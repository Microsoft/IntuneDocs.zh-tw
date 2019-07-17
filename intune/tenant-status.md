---
title: Microsoft Intune 租用戶狀態頁面
titleSuffix: Microsoft Intune
description: 使用 Intune 的 [租用戶狀態] 頁面，不需要離開 Intune 入口網站即可檢視重要的租用戶詳細資料
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 946d46baf17a5ffdd4b567adca32b651cacb72bb
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882231"
---
# <a name="intune-tenant-status-page"></a>Intune 租用戶狀態頁面
[租用戶狀態] 頁面是您可以檢視最新租用戶重要詳細資料的集中式中樞。 這些詳細資料包括授權可用性和使用、連接器狀態，以及 Intune 服務的相關重要通訊。  

若要檢視儀表板，請在 Azure 入口網站中，移至 [Intune] > [租用戶狀態]  。  [租用戶狀態] 會顯示於 [說明及支援]  群組下。  

此頁面分成四個區域：

## <a name="tenant-details"></a>租用戶詳細資料
租用戶詳細資料提供您租用戶的相關概覽資訊。 您可以檢視租用戶名稱和位置、MDM 授權單位，以及租用戶服務版本號碼。 服務版本號碼是一個連結，它會開啟 Microsoft Docs 上＜Intune 的新功能＞  一文。您可在＜新功能＞  中，閱讀 Intune 服務的最新功能和更新資訊。  

此區段也提供您可用授權及指派給使用者的數目等基本資訊。 但不會顯示裝置的授權。

## <a name="connector-status"></a>連接器狀態
連接器狀態是您一次檢視 Intune 中所有可用連接器狀態的位置。  

連接器包括：
- **您設定的外部服務連線**。 例如，「Apple 大量採購方案」  服務或 *Windows Autopilot* 服務。  這種連接器類型的狀態取決於上次成功同步處理時間。
- **連線到外部非受控服務所需的憑證或認證**，例如 *Apple Push Notification Service* (APNS) 憑證。 這種連接器類型之狀態取決於憑證或認證的到期時間戳記。  

根據預設，顯示畫面最多會顯示五個連接器。 您可以選取 [查看所有連接器]  展開此清單，以檢視所有可用的連接器，包括您尚未設定使用的連接器。  

狀況不良的連接器一律會顯示在清單頂端。 接著是具有警告的連接器，然後是狀況良好的連接器清單。 您尚未設定的連接器會最後出現。

若任何一種類型有多個連接器，則狀態會是所有相同連接器的摘要。 系統會使用狀況最不良的任何一個連接器狀態作為群組的健全狀況。  

**連接器狀態：**
- **狀況不良：**
  - 憑證或認證已過期
  - 上次同步處理為三天或更多天前
- **警告：**
  - 憑證或認證將在七天內過期
  - 上次同步處理為多天前
- **狀況良好：**
  - 憑證或認證在未來七天內不會過期
  - 上次同步處理為不到一天前  

當您從清單中選取連接器時，入口網站會顯示與建立或設定該連接器相關的入口網站頁面。  例如，當您選取 [VPP 到期日]  連接器時，[iOS 大量採購方案權杖]  頁面會隨即開啟，您可以在這裡檢視有關該連接器的更多詳細資料。 您可以接著建立新的設定，或編輯和修正現有設定的問題。  

## <a name="intune-service-health"></a>Intune 服務健全狀況  
您可以檢視作用中事件和諮詢的詳細資料，而不必巡覽至 Microsoft 365 服務健全狀況儀表板或訊息中心，這兩者都位於 [Microsoft 365 系統管理中心](https://admin.microsoft.com)。 只會顯示已注意到會影響您租用戶的事件。  

當您選取事件時，事件的詳細資料會直接顯示在 [租用戶狀態] 頁面中。 若要檢視過去的諮詢和事件，請選取 [查看過去的事件/諮詢]  。 Microsoft 365 系統管理中心會隨即開啟，然後您可以檢視租用戶過去 30 天的諮詢和事件。  

若要檢視「Intune 服務健全狀況」  的資訊，您的帳戶必須在 Azure Active Directory 或 Microsoft 365 系統管理中心具有 [全域管理員]  或 [服務管理員]  角色。 若要指派這些權限，請使用全域管理員權限登入 [Microsoft 365 系統管理中心](https://admin.microsoft.com)。 選取 [使用者] > [作用中使用者]  ，然後選取需要存取的帳戶。 針對 [角色] 選取 [編輯]  ，選取 [服務管理員]  或 [全域管理員]  ，然後**儲存**您的編輯以指派權限。  

您只能透過 Microsoft 365 系統管理中心設定 Intune 服務健全狀況的通訊喜好設定。

## <a name="intune-news"></a>Intune 新聞  
檢視來自 Intune 服務小組的資訊通訊，而不必巡覽至 Office 訊息中心。 這些通訊包括 Intune 服務最近發生變更，或即將為您租用戶所進行變更的相關訊息。  

預設會顯示最後 10 則作用中訊息。 若要檢視較舊的訊息，請選取 [查看過去的訊息]  ，以在 Microsoft 365 系統管理中心開啟 [訊息中心]  。  

若要檢視 Intune 新聞的資訊，您的帳戶必須在 Azure Active Directory 中具有 [全域管理員]  或 [服務管理員]  角色，或在 Microsoft 365 系統管理中心具有 [訊息中心讀者]  角色。  若要指派此權限，請使用系統管理員權限登入 [Microsoft 365 系統管理中心](https://admin.microsoft.com)。 選取 [使用者] > [作用中使用者]  ，然後選取需要存取的帳戶。 針對 [角色]  選取 [編輯]  ，選取 [Teams 通訊管理員]  ，然後**儲存**您的編輯以指派權限。  

您只能透過 Microsoft 365 系統管理中心設定 Intune 新聞的通訊喜好設定。
