---
title: 設定 Lookout 與 Microsoft Intune 的整合
titleSuffix: Microsoft Intune
description: 了解如何整合 Intune 與 Lookout Mobile Threat Defense (作為 Mobile Threat Defense 解決方案)，來控制行動裝置對貴公司資源的存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be2e9371288961d0afdf7ad6e8cfec8f734087f6
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529924"
---
# <a name="set-up-lookout-mobile-endpoint-security-integration-with-intune"></a>設定與 Intune 的 Lookout Mobile Endpoint Security 整合
透過符合[必要條件](lookout-mobile-threat-defense-connector.md#prerequisites)的環境，您可以將 Lookout Mobile Endpoint Security 與 Intune 整合。 本文的資訊將引導您設定整合，並設定 Lookout 中的重要設定以便與 Intune 搭配使用。  

> [!IMPORTANT]
> 尚未與 Azure AD 租用戶建立關聯的現有 Lookout Mobile Endpoint Security 租用戶無法用來整合 Azure AD 與 Intune。 請與 Lookout 支援部門連絡，以建立新的 Lookout Mobile Endpoint Security 租用戶。 請使用新的租用戶來連接 Azure AD 使用者。

## <a name="collect-azure-ad-information"></a>收集 Azure AD 資訊  
若要將 Lookout 與 Intune 整合，您需將 Lookout Mobility Endpoint Security 租用戶關聯至 Azure Active Directory (AD) 訂用帳戶。

若要讓您的 Lookout Mobile Endpoint Security 訂用帳戶與 Intune 整合，您需將下列資訊提供給 Lookout 支援 (enterprisesupport@lookout.com)：  

- **Azure AD 租用戶目錄識別碼**  

- 適用於具備**完整** Lookout Mobile Endpoint Security (MES) 主控台存取權之群組的 **Azure AD 群組物件識別碼**。  
  您會在 Azure AD 中建立此使用者群組，以包含具備可登入 **Lookout 主控台**之「完整權限」  的使用者。 使用者必須是此群組的成員或選擇性的「限制存取」  群組，才能登入 Lookout 主控台。 

- 適用於具備**限制** Lookout MES 主控台存取權「(選擇性群組)」  之群組的 **Azure AD 群組物件識別碼**。 
  您會在 Azure AD 中建立此選擇性使用者群組，以包含不應有權存取 Lookout 主控台中數個與設定和註冊相關模組的使用者。 相反地，這些使用者均具備 Lookout 主控台中**安全性原則**模組的唯讀存取權。 使用者必須是此選擇性群組或必要「完整權限」  群組的成員，才能登入 Lookout 主控台。

 > [!TIP] 
 > 如需權限的詳細資訊，請參閱 Lookout 網站上的[這篇文章](https://personal.support.lookout.com/hc/articles/114094105653)。

### <a name="collect-information-from-azure-ad"></a>收集來自 Azure AD 的資訊 

1. 使用全域管理員帳戶登入 [Azure 入口網站](https://portal.azure.com)。

2. 移至 [Azure Active Directory]   > [屬性]  ，然後找出您的**目錄識別碼**。 使用 [複製]  按鈕來複製目錄識別碼，並儲存於文字檔中。

   ![Azure AD 屬性](./media/lookout-mtd-connector-integration/azure-ad-properties.png)  

3. 接下來，針對您用來為 Azure AD 使用者授與 Lookout 主控台存取權的帳戶尋找 Azure AD 群組識別碼。 一個群組適用於「完整權限」  ，而第二個適用於「限制存取」  的群組是選擇性的。 取得每個帳戶的「物件識別碼」  ：  
   1. 移至 [Azure Active Directory]   > [群組]  以開啟 [群組 - 所有群組]  窗格。  

   2. 選取您建立來取得「完整權限」  的群組以開啟其 [概觀]  窗格。  

   3. 使用 [複製]  按鈕來複製物件識別碼，並儲存於文字檔中。  

   4. 如果您使用該群組，請重複執行「限制存取」  群組的流程。  

      ![Azure AD 物件識別碼](./media/lookout-mtd-connector-integration/azure-ad-group-id.png)  

   收集此資訊之後，請連絡 Lookout 支援 (電子郵件︰enterprisesupport@lookout.com)。 Lookout 支援將與您的主要連絡人合作來登錄您的訂用帳戶，並使用您提供的資訊來建立 Lookout Enterprise 帳戶。  

## <a name="configure-your-lookout-subscription"></a>設定 Lookout 訂用帳戶  
當 Lookout 支援建立您的 Lookout Enterprise 帳戶之後，Lookout 支援會傳送電子郵件給貴公司的主要連絡人，其中提供登入 URL 的連結： https://aad.lookout.com/les?action=consent 。 

### <a name="initial-sign-in"></a>初始登入  
首次登入 Lookout MES 主控台會顯示同意頁面 (https://aad.lookout.com/les?action=consent) 。 Azure AD 全域管理員只需登入並**接受**。 後續登入不會要求使用者具備這個等級的 Azure AD 權限。 

 隨即顯示同意頁面。 選擇 [接受]  以完成註冊。 
   ![首次登入 Lookout 主控台的頁面螢幕擷取畫面](./media/lookout-mtd-connector-integration/lookout_mtp_initial_login.png)

當您接受並同意之後，即會將您重新導向至 Lookout 主控台。

完成初始登入並同意之後，即會將從 https://aad.lookout.com 登入的使用者重新導向至 MES 主控台。 如果還未授與同意，則所有登入嘗試都會產生不正確的登入錯誤。

### <a name="configure-the-intune-connector"></a>設定 Intune 連接器  
下列程序假設您先前已在 Azure AD 中建立使用者群組來測試 Lookout 部署。 最佳做法是從一小組使用者開始，讓您的 Lookout 與 Intune 管理員能夠熟悉產品整合。 當他們熟悉之後，您就能將該註冊擴展至其他使用者群組。

1. 登入 [Lookout MES 主控台](https://aad.lookout.com)並移至 [系統]   > [連接器]  ，然後選取 [新增連接器]  。  選取 [Intune]  。

   ![在 [連接器] 索引標籤上選取 [Intune] 選項的 Lookout 主控台影像](./media/lookout-mtd-connector-integration/lookout_mtp_setup-intune-connector.png)

2. 在 [Microsoft Intune]  窗格上，選取 [連線設定]  並指定 [活動訊號頻率]  (以分鐘為單位)。 

   ![已設定 [活動訊號頻率] 的 [連線設定] 索引標籤影像](./media/lookout-mtd-connector-integration/lookout-mtp-connection-settings.png)

3. 選取 [註冊管理]  ，然後針對 [使用下列 Azure AD 安全性群組來識別應在 Lookout for Work 中註冊的裝置]  ，指定要與 Lookout 搭配使用之 Azure AD 群組的*群組名稱*，然後選取 [儲存變更]  。

    ![Intune 連接器註冊頁面的螢幕擷取畫面](./media/lookout-mtd-connector-integration/lookout-mtp-enrollment.png)  

   **關於您使用的群組**：
   - 最佳做法是從 Azure AD 安全性群組開始，此群組包含少數用來測試 Lookout 整合的使用者。
   - **群組名稱**會區分大小寫，如 Azure 入口網站中安全性群組的 [屬性]  中所示。  
   - 您針對**註冊管理**指定的群組會定義一組將向 Lookout 註冊裝置的使用者。 如果使用者隸屬於某個註冊群組，即會在 Lookout MES 中註冊他們在 Azure AD 中的裝置且可加以啟用。 當使用者首次在支援的裝置上開啟 *Lookout for Work* 應用程式時，系統會提示他們啟用它。

4. 選取 [狀態同步處理]  ，並確保已將 [裝置狀態]  和 [威脅狀態]  設定為 [開啟]  。  這兩者要同時存在，Lookout 與 Intune 的整合才能正常運作。  

5. 選取 [錯誤管理]  、指定應收到錯誤報表的電子郵件地址，然後選取 [儲存變更]  。
 
   ![Intune 連接器之 [錯誤管理] 頁面的螢幕擷取畫面](./media/lookout-mtd-connector-integration/lookout-mtp-connector-error-notifications.png)

6. 選取 [建立連接器]  以完成連接器設定。 稍後，當您對結果感到滿意時，即可將註冊擴展到其他使用者群組。

## <a name="configure-intune-to-use-lookout-as-a-mobile-threat-defense-provider"></a>設定 Intune 以使用 Lookout 作為 Mobile Threat Defense 提供者
當您設定 Lookout MES 之後，必須在 Intune 中設定與 Lookout 的連線。  

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。

2. 移至 [裝置合規性]   > [Mobile Threat Defense]  ，然後選取 [新增]  。

3. 在 [新增連接器]  窗格上使用下拉式清單，然後選取 [Lookout for Work]  。  

4. 選取 [建立]  。 當連接器建立與 Lookout MES 的聯繫之後，[連接器設定]  就會變成可用狀態。

5. 將 [為 iOS 裝置啟用應用程式同步]  設定為 [開啟]  。 

6. 選取 [儲存]  以完成設定。  Intune 和 Lookout MES 現已整合且可供使用。


## <a name="additional-settings-in-the-lookout-mes-console"></a>Lookout MES 主控台中的其他設定
以下是您可以在 Lookout MES 主控台中設定的其他設定。  

### <a name="configure-enrollment-settings"></a>設定註冊設定
在 Lookout MES 主控台中，選取 [系統]   > [管理註冊]   > [註冊設定]  。  

- 針對 [已中斷連線狀態]  ，指定在將未連線的裝置標示為已中斷連線之前的天數。  

  已中斷連線的裝置會視為不相容，而且根據 Intune 條件式存取原則，將無法存取您的公司應用程式。 您可以指定 1 到 90 天之間的值。

  ![Lookout [系統] 模組上的 [註冊設定]](./media/lookout-mtd-connector-integration/lookout-console-enrollment-settings.png)

### <a name="configure-email-notifications"></a>設定電子郵件通知
若要接收威脅的電子郵件警示，請使用應收到通知的使用者帳戶登入 [Lookout MES 主控台](https://aad.lookout.com)。  

- 移至 [喜好設定]  ，接著將您想要到收的通知設定為 [開啟]  ，然後**儲存**所做的變更。  

- 如果您不想再收到電子郵件通知，請將通知設定為 [關閉]  ，然後儲存變更。

  ![顯示使用者帳戶喜好設定頁面的螢幕擷取畫面](./media/lookout-mtd-connector-integration/lookout-mtp-email-notifications.png)



## <a name="configure-threat-classifications"></a>設定威脅分類  
Lookout Mobile Endpoint Security 會將各種類型的行動裝置威脅進行分類。 Lookout 威脅分類具有相關聯的預設風險層級。 隨時都能變更風險層級，以符合貴公司的需求。

如需威脅層級分類，以及如何管理與其關聯之風險層級的相關資訊，請參閱 [Lookout 威脅參考](https://enterprise.support.lookout.com/hc/articles/360011812974)。

>[!IMPORTANT]
> 風險層級對於 Mobile Endpoint Security 而言很重要，因為 Intune 整合會在執行階段，根據這些風險層級來計算裝置合規性。  
> 
> Intune 管理員可在原則中設定規則，以判斷裝置的現行威脅最低層級為何 (**高**、**中**或**低**) 時，要將其識別為不相容。 Lookout Mobile Endpoint Security 中的威脅分類原則會直接在 Intune 中驅動裝置合規性計算。  

## <a name="monitor-enrollment"></a>監視註冊
完成設定之後，Lookout Mobile Endpoint Security 就會開始輪詢 Azure AD，以找出對應至指定註冊群組的裝置。  您可以移至 Lookout MES 主控台中的 [裝置]  來尋找已註冊裝置的相關資訊。  
- 裝置的初始狀態為 [擱置]  。  
- 在裝置上安裝、開啟及啟用 *Lookout for Work* 應用程式之後，裝置狀態即會更新。

如需如何將 *Lookout for Work* 應用程式部署到裝置的詳細資料，請參閱[使用 Intune 新增 Lookout for Work 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)。

## <a name="next-steps"></a>後續步驟

[設定 Lookout 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)
