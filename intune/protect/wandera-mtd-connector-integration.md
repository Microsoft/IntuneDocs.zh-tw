---
title: 設定 Wandera Mobile Threat Protection 與 Intune 的整合
titleSuffix: Intune on Azure
description: 如何搭配 Microsoft Intune 設定 Wandera Mobile Threat Protection 解決方案來控制行動裝置對公司資源的存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: f42acb38d84394a6b61fa16072de6320b84a67b5
ms.sourcegitcommit: 1a5b185acd27954b10b6d59409d82eb80fd71284
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72681300"
---
# <a name="integrate-wandera-mobile-threat-protection-with-intune"></a>將 Wandera Mobile Threat Protection 與 Intune 整合  

完成下列步驟以將 Wandera Mobile Threat Defense 解決方案與 Intune 整合。  

> [!NOTE]
> 此 Mobile Threat Defense 廠商不支援尚未註冊的裝置。

## <a name="before-you-begin"></a>開始之前  

開始執行將 Wandera 與 Intune 整合的程序之前，請確定您已備妥下列先決條件：
- Microsoft Intune 訂閱  
- 可授與下列權限的 Azure Active Directory 管理員認證：  
  - 登入及讀取使用者設定檔  
  - 以登入的使用者身分存取目錄  
  - 讀取目錄資料  
  - 將裝置資訊傳送至 Intune  

- Wandera 訂用帳戶：
  - 一或多個已獲得 EMM Connect 授權的 Wandera 帳戶  
  - 具有 Wandera 中超級系統管理員權限的帳戶  
 
### <a name="wandera-mobile-threat-defense-app-authorization"></a>Wandera Mobile Threat Defense 應用程式授權  

Wandera Mobile Threat Defense 應用程式授權程序：  
- 允許 Wandera Mobile Threat Defense 服務將裝置健康情況狀態相關資訊傳送回 Intune。  
- Wandera 會與 Azure AD 註冊群組成員資格同步，以填入其裝置的資料庫。  
- 允許 Wandera RADAR 系統管理入口網站使用 Azure AD 單一登入 (SSO)。  
- 允許 Wandera Mobile Threat Defense 應用程式使用 Azure AD SSO 來登入。  


## <a name="set-up-wandera-mobile-threat-defense-integration"></a>設定 Wandera Mobile Threat Defense 整合  
設定 *EMM Connect* for Wandera 需要您必須同時在 Intune 與 Wandera 主控台中完成的一次性設定程序。 設定程序大約會花費 15 分鐘的時間。 您可以在不需要與您的 Wandera 技術帳戶或支援代表協調的情況下完成設定。  

### <a name="enable-support-for-wandera-in-intune"></a>在 Intune 中啟用 Wandera 支援
1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並移至 [裝置合規性]   > [Mobile Threat Defense]  > 並選取 [新增]  。

2. 在 [新增連接器]  頁面上，使用下拉式清單，並選取 [Wandera]  。 然後選取 [建立]  。  

3. 在 Mobile Threat Defense 窗格上，從連接器清單選取 **Wandera** MTD 連接器以開啟 [編輯連接器]  窗格。 選取 [Open the Wandera admin console] \(開啟 Wandera 系統管理主控台\)  以開啟 [RADAR](https://radar.wandera.com/login) 這個 Wandera 系統管理主控台，然後登入。 

4. 在 Wandera 主控台中，移至 [設定]   > [EMM Integration] \(EMM 整合\)  ，然後選取 [EMM Connect]  索引標籤。使用 [EMM Vendor] \(EMM 廠商\)  下拉式清單，並選取 [Microsoft Intune]  。

   ![選取 Intune](./media/wandera-mtd-connector-integration/set-up-intune-in-radar.png)

5. 選取 [授與權限]  以開啟與 Intune 入口網站的連線。 使用您的 Intune 系統管理員認證登入，選取該核取方塊並**接受**權限要求。  

   ![接受權限](./media/wandera-mtd-connector-integration/permissions.png) 

6. Wandera 會完成連線並讓您返回 RADAR 系統管理主控台。 視需要重複程序以**授與**額外設定存取權。  

   ![整合與權限](./media/wandera-mtd-connector-integration/integrations-and-permissions.png) 

7. 在 RADAR 主控台中，複製出現在 [EMM Label] \(EMM 標籤\)  下的 **SyncOnly** 群組名稱。 您將使用此名稱來設定 Intune 中的群組以與 Wandera 同步。

   ![同步處理群組](./media/wandera-mtd-connector-integration/sync-group-name.png) 

8. 返回 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 主控台，並編輯 Wandera MTD 連接器。 將可用切換參數設定為 [開啟]  ，然後**儲存** 設定。  

   ![啟用 Wandera](./media/wandera-mtd-connector-integration/enable-wandera.png) 

Intune 與 Wandera 現在已連結。  

## <a name="configure-the-wandera-applications-and-synchronization-group"></a>設定 Wandera 應用程式與同步群組  
若要部署 Wandera，您將為您使用的平台 (iOS 與 Android) 新增 Wandera 行動裝置應用程式到 Intune，然後將它們指派給特定群組以進行同步，亦即 *SyncOnly* 群組。 

以下各節與程序會引導您完成此程序。

如需有關從 Wandera 執行此程序的詳細資訊，請登入 Wandera [RADAR](https://radar.wandera.com/login)。 移至 [設定]   > [EMM Integration] \(EMM 整合\)  ，選取 [App Push] \(應用程式推播\)  索引標籤，然後選取 [Microsoft Intune]  。 [應用程式推播] 索引標籤會使用 Intune 特定指示來更新。  

### <a name="add-the-wandera-apps"></a>新增 Wandera 應用程式  
在 Intune 中建立用戶端應用程式以部署 Wandera app 應用程式到 Android 與 iOS 裝置。 請參閱[新增 MTD 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)以了解 Wandera 應用程式的特定程序與自訂詳細資料。  

建立應用程式之後，返回這裡以建立同步群組並指派應用程式。  


### <a name="create-the-synchronization-group-and-assign-the-apps"></a>建立同步群組並指派應用程式

1. 從 Wandera RADAR 取得 [EMM Label] \(EMM 標籤\)  下出現的 **SyncOnly** 群組名稱。 您可能已在步驟 7 中[在 Intune 中啟用 Wandera 支援](#enable-support-for-wandera-in-intune)時儲存此名稱。 使用此名稱作為 Intune 中 Wandera 同步的群組名稱。  

2. 在 Intune 主控台中，移至 [群組]  並選取 [新增群組]  。 指定下列設定以設定將由 Wandera 使用的同步群組：
   - **群組類型**：**安全性**
   - **群組名稱**：指定您從 Wandera RADAR 系統管理主控台擷取的 **SyncOnly** 名稱。

   ![設定同步群組](./media/wandera-mtd-connector-integration/configure-sync-group.png)

3. 選取 [成員]  並指派包括您要搭配 Wandera 使用之 Android 與 iOS 裝置的群組。

4. 選取 [建立]  以儲存群組。

如需詳細資訊，請參閱[部署應用程式](../apps/apps-deploy.md)

### <a name="assign-the-wandera-apps-to-the-synchronization-group"></a>指派 Wandera 應用程式到同步群組  
針對您為 iOS 與 Android 建立的 Wandera 應用程式重複下列程序。

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並移至 [用戶端應用程式]   > [應用程式]  ，然後選取 Wandera 應用程式。  

2. 選取 [指派]  ，然後選取 [新增群組]  。  

3. 在 [新增群組]  窗格上，針對 [指派類型]  選取 [必要]  。

4. 選取 [包含的群組]  ，然後選取 [選取要納入的群組]  。 指定您為 Wandera 同步建立的群組，然後按一下 [選取]   > [確定]   > [確定]  。 選取 [儲存]  以完成群組指派。  
 

## <a name="next-steps"></a>後續步驟  
既然您已設定整合，您可以開始設定原則、設定進階條件式存取，以及在 Wandera 系統主控台中檢視報告。 若要深入了解如何管理及設定 Wandera，請參閱 Wandera 文件中的[支援中心開始使用指南](https://radar.wandera.com/?return_to=https://wandera.force.com/Customer/s/getting-started) \(英文\)。  
 
