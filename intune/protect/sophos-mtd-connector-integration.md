---
title: 設定 Sophos Mobile 與 Intune 的整合
titleSuffix: Intune on Azure
description: 如何設定 Sophos Mobile 解決方案與 Microsoft Intune 的整合，來控制行動裝置對公司資源的存取。
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
ms.openlocfilehash: aad6268606dfcf69c304bb5c5b270c8c4795e4b2
ms.sourcegitcommit: 1a5b185acd27954b10b6d59409d82eb80fd71284
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72681291"
---
# <a name="integrate-sophos-mobile-with-intune"></a>整合 Sophos Mobile 與 Intune  

完成下列步驟以整合 Sophos Mobile Threat Defense 解決方案與 Intune。  

> [!NOTE]
> 此 Mobile Threat Defense 廠商不支援尚未註冊的裝置。

## <a name="before-you-begin"></a>開始之前  

開始整合 Sophos Mobile 與 Intune 前，請先確定您有下列項目：  
- Microsoft Intune 訂閱  
- 可授與下列權限的 Azure Active Directory 管理員認證：  
  - 登入及讀取使用者設定檔  
  - 以登入的使用者身分存取目錄  
  - 讀取目錄資料  
  - 將裝置資訊傳送至 Intune  
- 可存取 Sophos Mobile 管理主控台的系統管理員認證。  


### <a name="sophos-mobile-app-authorization"></a>Sophos Mobile 應用程式授權  
  
Sophos Mobile 應用程式授權程序如下：  
- 允許 Sophos Mobile 服務將裝置健康狀態的相關資訊傳送回 Intune。  
- 將 Sophos Mobile 與 Azure AD 註冊群組成員資格同步，以填入其裝置的資料庫。  
- 允許 Sophos Mobile 管理主控台使用 Azure AD 單一登入 (SSO)。  
- 允許 Sophos Mobile 應用程式使用 Azure AD SSO 登入。  


## <a name="to-set-up-sophos-mobile-integration"></a>設定 Sophos Mobile 整合  

1. 登入 [Azure 入口網站]( https://portal.azure.com/)，前往 [Intune]   > 裝置合規性   > Mobile Threat Defense  > 並選取 [新增]  。  
2. 在 [新增連接器]  頁面上，使用下拉式清單，並選取 [Sophos]  。 然後選取 [建立]  。  
3. 選取的連結 [開啟 Sophos 系統管理員主控台]  。  
4. 使用 Sophos 認證登入 [Sophos 系統管理員主控台](https://central.sophos.com/)。  
5. 前往 行動裝置   > 設定   > 設定   > Sophos 設定  。  
6. 在 [Sophos 設定]  頁面上，選取 [Intune MTD]  索引標籤。  
   ![Sophos 設定](./media/sophos-mtd-connector-integration/sophos-setup.png) 
 
7. 選取 [繫結]  ，然後選取 [是]  。 Sophos 會連線到 Intune，並要求您登入自己的 Intune 訂用帳戶。 
8. 在 Microsoft Intune 驗證視窗中，輸入您的 Intune 認證，並 [接受]  *Sophos Mobile Thread Defense* 的權限要求。  
   ![Intune 驗證](./media/sophos-mtd-connector-integration/intune-authentication.png)

9. 在 [Sophos 設定]  頁面上，選取 [儲存]  以完成 Intune 的設定：  
   ![儲存 Sophos 設定](./media/sophos-mtd-connector-integration/save-sophos-configuration.png)  

1. 出現 [Successful Integration] \(成功整合\)  訊息時，整合即完成。  
1. 現在已可在 Intune 主控台中使用 Sophos。  


## <a name="next-steps"></a>後續步驟  
[設定 Sophos 用戶端應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)
