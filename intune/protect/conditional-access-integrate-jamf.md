---
title: 將 Jamf Pro 與 Microsoft Intune 整合以符合規範
titleSuffix: Microsoft Intune
description: 搭配 Azure Active Directory 條件式存取使用 Microsoft Intune 合規性政策，來協助整合及保護 Jamf 受控裝置。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 39d687c8c9b75182ba0e7d4020c6b840c753a231
ms.sourcegitcommit: a4c7339ec9ff5b1b846cb3cca887cf91b5cd4baa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627653"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>將 Jamf Pro 與 Intune 整合以取得合規性

適用於：Azure 入口網站中的 Intune

如果貴組織使用 [Jamf Pro](https://www.jamf.com) \(英文\) 來管理 Mac 裝置，您可以搭配 Azure Active Directory (Azure AD) 條件式存取使用 Microsoft Intune 合規性政策，來確保組織中的裝置符合規範，然後才能使用那些裝置存取公司資源。 此文章將協助您設定 Jamf 與 Intune 的整合。

當 Jamf Pro 與 Intune 整合時，您可以透過 Azure AD，從 macOS 裝置與 Intune 同步處理清查資料。 Intune 的合規性引擎接著會分析清查資料來產生報告。 Intune 的分析結合了裝置使用者 Azure AD 身分識別的相關情報，透過條件式存取來推動強制執行。 符合條件式存取原則規範的裝置可存取受保護的公司資源。

設定整合之後，您將接著在由 Jamf 管理的裝置上[設定 Jamf 和 Intune 以強制遵循條件式存取的規範](conditional-access-assign-jamf.md)。  


## <a name="prerequisites"></a>必要條件

### <a name="products-and-services"></a>產品與服務
您需要下列項目以搭配 Jamf Pro 設定條件式存取：

- Jamf Pro 10.1.0 或更新版本
- [macOS 版公司入口網站應用程式](https://aka.ms/macoscompanyportal)
- 具有 OS X 10.11 Yosemite 或更新版本的 macOS 裝置

### <a name="network-ports"></a>網路連接埠
<!-- source: https://support.microsoft.com/en-us/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune -->
Jamf 和 Intune 必須能夠存取下列連接埠，才能正確整合： 
- **Intune**：連接埠 443
- **Apple**：連接埠 2195、2196 和 5223 (將通知推播至 Intune)
- **Jamf**：連接埠 80 和 5223

若要讓 APNS 能夠在網路上正確運作，您也必須啟用連出連線，並從下列位址重新導向：
- 來自所用戶端的 Apple 17.0.0.0/8 區塊 (在 TCP 連接埠 5223 與 443)。   
- 來自 Jamf Pro 伺服器的連接埠 2195 與 2196。  

如需有關這些連接埠的詳細資訊，請參閱下列文章：  
- [Intune 網路設定需求與頻寬](../fundamentals/network-bandwidth-use.md)。
- jamf.com 上 [Jamf Pro 使用的網路連接埠](https://www.jamf.com/jamf-nation/articles/34/network-ports-used-by-jamf-pro) \(英文\)。
- support.apple.com 網站上的 [Apple 軟體產品使用的 TCP 和 UDP 連接埠](https://support.apple.com/HT202944)


## <a name="connect-intune-to-jamf-pro"></a>將 Intune 連線到 Jamf Pro

將 Intune 連線到 Jamf Pro：

1. 在 Azure 中建立新的應用程式。
2. 使 Intune 與 Jamf Pro 整合。
3. 在 Jamf Pro 中設定條件式存取。

## <a name="create-an-application-in-azure-active-directory"></a>在 Azure Active Directory 中建立應用程式

1. 在 [Azure 入口網站](https://portal.azure.com)中，移至 [Azure Active Directory]   > [應用程式註冊]  ，然後選取 [新增註冊]  。 

2. 在 [註冊應用程式]  頁面上，指定下列詳細資料：
   - 在 [名稱]  區段中，輸入有意義的應用程式名稱，例如 **Jamf 條件式存取**。
   - 針對 [支援的帳戶類型]  區段，選取 [任何組織目錄中的帳戶]  。 
   - 針對 [重新導向 URI]  保留 Web 的預設值，然後為您的 Jamf Pro 執行個體指定 URL。  

3. 選取 [註冊]  以建立應用程式，並開啟新應用程式的 [概觀]  頁面。  

4. 在應用程式的 [概觀]  頁面上，複製 [應用程式 (用戶端) 識別碼]  值，並加以記錄以供稍後使用。 您將需要在後續程序中用到此值。  

5. 選取 [管理]  下方的 [憑證及祕密]  。 選取 [新增用戶端密碼]  按鈕。 在 [描述]  中輸入值、針對 [到期]  選取任意選項，然後選擇 [新增]  。

   > [!IMPORTANT]  
   > 離開此頁面之前，複製用戶端密碼的值，並加以記錄以供稍後使用。 您將需要在後續程序中用到此值。 此值無法在未重新建立應用程式註冊的情況下再次使用。  

6. 選取 [管理]  下方的 [API 權限]  。 選取現有的權限，然後選取 [移除權限]  以刪除那些權限。 由於您將新增權限，因此必須先刪除所有的現有權限，而應用程式只有在具備單一必要權限時才能正常運作。  

7. 若要指派新的權限，請選取 [新增權限]  。 在 [要求 API 權限]  頁面上，選取 [Intune]  ，然後選取 [應用程式權限]  。 只選取 **update_device_attributes** 的核取方塊。  

   選取 [新增權限]  以儲存此設定。  

8. 在 [API 權限]  頁面上，選取 [代表 _\<您的租用戶>_ 授與管理員同意]  ，然後選取 [是]  。  成功註冊應用程式之後，API 權限應如下所示：![順利取得權限](./media/conditional-access-integrate-jamf/sucessfull-app-registration.png)

   Azure AD 中的應用程式註冊程序已完成。


    > [!NOTE]
    > 如果用戶端密碼到期，您必須在 Azure 中建立新的用戶端密碼，然後更新 Jamf Pro 中的條件式存取資料。 Azure 允許您同時啟用舊祕密與新金鑰，以避免服務中斷。

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>使 Intune 與 Jamf Pro 整合

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，然後移至 [Microsoft Intune]   > [裝置相容性]   > [夥伴裝置管理]  。

2. 將您在先前程序期間儲存的應用程式識別碼貼上至 [Jamf Azure Active Directory 應用程式識別碼]  欄位，以啟用適用於 Jamf 的相容性連接器。

3. 選取 [儲存]  。

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>在 Jamf Pro 中設定 Microsoft Intune 整合

1. 在 Jamf Pro 中，瀏覽至 [全域管理]   > [條件式存取]  。 按一下 [macOS Intune 整合]  索引標籤上的 [編輯]  按鈕。

2. 選取 [啟用 macOS 的 Intune 整合]  核取方塊。

3. 提供關於您 Azure 租用戶的必要資訊，包括 [位置]  、[網域名稱]  、[應用程式識別碼]  ，以及您在 Azure AD 中建立應用程式時所儲存的 [用戶端密碼]  的值。  

4. 選取 [儲存]  。 Jamf Pro 會測試您的設定，並確認是否成功。

## <a name="set-up-compliance-policies-and-register-devices"></a>設定合規性原則並註冊裝置

設定 Intune 和 Jamf 之間的整合後，您需要[將合規性政策套用至 Jamf 受控裝置](conditional-access-assign-jamf.md)。


## <a name="disconnect-jamf-pro-and-intune"></a>中斷 Jamf Pro 和 Intune 的連線 

如果您不再使用 Jamf Pro 來管理組織中的 Mac，而且想要讓使用者受 Intune 管理，您必須移除 Jamf Pro 與 Intune 之間的連線。 使用 Jamf Pro 主控台來移除連線。 

1. 在 Jamf Pro 中，移至 [全域管理]   > [條件式存取]  。 在 [macOS Intune 整合]  索引標籤上，選取 [編輯]  。
2. 清除 [啟用 macOS 的 Intune 整合]  核取方塊。
3. 選取 [儲存]  。 Jamf Pro 會將您的設定傳送至 Intune，並終止整合。
4. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。 移至 [Microsoft Intune]   > [裝置合規性]   > [夥伴裝置管理]  ，確認狀態為目前為 [已終止]  。 

   > [!NOTE]
   > 您組織的 Mac 裝置將會在主控台中顯示的日期 (3 個月) 移除。 

## <a name="next-steps"></a>後續步驟

- [將合規性原則套用至受 Jamf 管理的裝置](conditional-access-assign-jamf.md)
- [Jamf 傳送至 Intune 的資料](data-jamf-sends-to-intune.md)
