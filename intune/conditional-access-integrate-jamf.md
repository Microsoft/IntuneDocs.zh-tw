---
title: 將 Jamf Pro 與 Microsoft Intune 整合以符合規範 | Microsoft Intune
description: 使用 Azure Active Directory 條件式存取搭配 Microsoft Intune 合規性政策來協助保護受 Jamf 管理的裝置。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa2fe73c0dab855f43daf71e9564f17490fa6366
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55846990"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>將 Jamf Pro 與 Intune 整合以取得合規性

適用於：Azure 入口網站中的 Intune

如果貴組織使用 [Jamf Pro](https://www.jamf.com) 來管理終端使用者的 Mac，您可以使用 Microsoft Intune 合規性政策搭配 Azure Active Directory 條件式存取，來確保您組織中的裝置能符合規範。

## <a name="prerequisites"></a>必要條件

您需要下列項目以搭配 Jamf Pro 設定條件式存取：

- Jamf Pro 10.1.0 或更新版本
- [macOS 版公司入口網站應用程式](https://aka.ms/macoscompanyportal)
- 具有 OS X 10.11 Yosemite 或更新版本的 macOS 裝置

## <a name="connecting-intune-to-jamf-pro"></a>將 Intune 連線到 Jamf Pro

若要將 Intune 連線到 Jamf Pro，您可以：

1. 在 Azure 中建立新的應用程式
2. 使 Intune 與 Jamf Pro 整合
3. 在 Jamf Pro 中設定條件式存取

## <a name="create-an-application-in-azure-active-directory"></a>在 Azure Active Directory 中建立應用程式

1. 在 [Azure 入口網站](https://portal.azure.com)中，移至 [Azure Active Directory] > [應用程式註冊]。
2. 選取 [+新增應用程式註冊]。
3. 輸入**顯示名稱**，例如 **Jamf 條件式存取**。
4. 選取 [Web 應用程式 / API]。
5. 使用 Jamf Pro 執行個體 URL 指定 [登入 URL]。
6. 選取 [建立]。 應用程式會隨即建立，且入口網站會顯示應用程式詳細資料。
7. 為新的應用程式儲存一份**應用程式識別碼**複本。 您會在稍後的程序中指定此識別碼。 接下來，選取 [設定]，然後移至 [API 存取] > [金鑰]。
8. 在 [金鑰] 窗格上，指定 [描述]、[到期日] 前等待的時間，然後選取 [儲存] 以產生應用程式金鑰 (值)。

   > [!IMPORTANT]
   > 應用程式金鑰在此程序期間只會顯示一次。 請務必將它儲存在您可以輕鬆擷取的地方。

8. 在應用程式的 [設定] 窗格上，巡覽至 [API 存取] > [必要權限]。 選取任何現有的權限，然後按一下 [刪除] 並刪除所有權限。 當您新增權限時，必須刪除現有的權限，應用程式只有在具有單一必要權限時才能正常運作。  
9. 若要指派新權限，請選取 [+新增] > [選取 API] > [Microsoft Intune API]，然後按一下 [選取]。
10. 在 [啟用存取] 窗格上，選取 [傳送裝置屬性到 Microsoft Intune]，然後依序按一下 [選取] 和 [完成]。
11. 在 [必要權限] 窗格上，選取 [授與權限]，然後選取 [是] 將必要權限套用至應用程式。

    > [!NOTE]
    > 如果應用程式金鑰到期，您必須在 Microsoft Azure 中建立新的應用程式金鑰，然後更新 Jamf Pro 中的條件式存取資料。 Azure 允許您同時啟用舊金鑰與新金鑰，以避免服務中斷。

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>使 Intune 與 Jamf Pro 整合

1. 在 [Azure 入口網站](https://portal.azure.com)中，移至 [Microsoft Intune] > [裝置相容性] > [夥伴裝置管理]。
2. 將您在先前程序期間儲存的應用程式識別碼貼上至 [Jamf Azure Active Directory 應用程式識別碼] 欄位，以啟用適用於 Jamf 的相容性連接器。
3. 選取 [儲存]。

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>在 Jamf Pro 中設定 Microsoft Intune 整合

1. 在 Jamf Pro 中，瀏覽至 [全域管理] > [條件式存取]。 按一下 [Microsoft Intune 整合] 索引標籤上的 [編輯] 按鈕。
2. 選取 [啟用 Microsoft Intune 整合] 核取方塊。
3. 提供您 Azure 租用戶的相關必要資訊，包括 [位置]、[網域名稱]，以及您在先前步驟中儲存的 [應用程式識別碼] 和 [應用程式金鑰]。
4. 選取 [儲存]。 Jamf Pro 會測試您的設定，並確認是否成功。

## <a name="set-up-compliance-policies-and-register-devices"></a>設定合規性原則並註冊裝置

設定 Intune 和 Jamf 之間的整合後，您需要[將合規性政策套用至 Jamf 受控裝置](conditional-access-assign-jamf.md)。



## <a name="next-steps"></a>後續步驟

- [將合規性原則套用至受 Jamf 管理的裝置](conditional-access-assign-jamf.md)
- [Jamf 傳送至 Intune 的資料](data-jamf-sends-to-intune.md)
