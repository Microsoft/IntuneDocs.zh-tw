---
title: "設定訂用帳戶使用 Lookout MTP | Microsoft Intune"
description: "本主題提供有關如何設定 Lookout MTP 的詳細資訊。"
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba2196ff03975df1f8969e1522f7af459343694d
ms.openlocfilehash: 530a34c7c75a4fa73cbb62873e2d28883b91b57e


---

# 設定訂用帳戶使用 Lookout 行動裝置威脅保護
為了準備使用 Lookout MTP 服務所需的訂用帳戶，Lookout 支援部門 (enterprisesupport@lookout.com) 需要您的下列 Azure Active Directory (Azure AD) 訂用帳戶相關資訊。 

* **Azure AD 租用戶識別碼**
* 可**完整存取** Lookout MTP 主控台的 **Azure AD 群組物件識別碼**
* 可**限制存取** Lookout MTP 主控台的 **Azure AD 群組物件識別碼** (選擇性)

請使用下一節的內容，來收集您需要提供給 Lookout 支援團隊的資訊。  

## 取得您的 Azure AD 資訊
### Azure AD 租用戶識別碼
登入 [Azure AD 管理入口網站](https://manage.windowsazure.com)，然後選取您的訂用帳戶。 

![顯示租用戶名稱之 Azure AD 頁面的螢幕擷取畫面](../media/mtp/aad_tenant_name.png) 當您選擇訂用帳戶的名稱時，產生的 URL 會包含訂用帳戶 ID。  如果您在尋找訂用帳戶 ID 時發生任何問題，可參閱這篇 [Microsoft 支援文章](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US)以取得尋找訂用帳戶 ID 的提示。   
### 取得您的 Azure AD 群組識別碼
Lookout MTP 主控台支援 2 個存取層級：  
* **完整存取**︰Azure AD 系統管理員可以建立擁有「完整存取」權限的使用者群組，並選擇性地建立擁有「限制存取」權限的使用者群組。  只有這些群組中的使用者才能夠登入 **Lookout MTP 主控台**。
* **限制存取**︰此群組中的使用者無法存取 Lookout MTP 主控台的幾項設定及註冊相關模組，但可唯讀存取 Lookout MTP 主控台的 [安全性原則] 模組。  

如需權限的詳細資訊，請參閱 Lookout 網站上的[這篇文章](https://personal.support.lookout.com/hc/en-us/articles/114094105653)。

在 **Azure AD 管理主控台**中，您可以在群組的 [屬性] 頁面上找到**群組物件識別碼**。

![醒目提示 [群組識別碼] 欄位之 [屬性] 頁面的螢幕擷取畫面](../media/mtp/aad_group_object_id.png)

收集到這項資訊之後，請連絡 Lookout 支援部門 (電子郵件：enterprisesupport@lookout.com)。

Lookout 支援部門會與您的主要連絡人合作，一同登入您的訂用帳戶，並使用您收集的資訊來建立 Lookout MTP 企業帳戶。


## 設定訂用帳戶使用 Lookout MTP
### 步驟 1︰設定您的 MTP
一旦 Lookout 支援部門建立好您的 Lookout MTP 企業帳戶之後，您即可登入 Lookout MTP 主控台。   來自 Lookout 的電子郵件會傳送給您公司的主要連絡人，並提供下列登入 URL 的連結：https://aad.lookout.com/les?action=consent

第一次登入 Lookout MTP 主控台時，您必須使用具有 Azure AD 全域管理員角色的使用者帳戶，因為 Lookout MTP 需要此帳戶才能註冊您的 Azure AD 租用戶。   後續登入即不會要求使用者具備此 Azure AD 權限等級。  第一次登入時，會顯示同意頁面。 選擇 [接受] 以完成註冊。

![Lookout MTP 主控台之第一次登入頁面的螢幕擷取畫面](../media/mtp/lookout_mtp_initial_login.png) 一旦您接受並同意，系統會將您重新導向至 Lookout MTP 主控台。 初始註冊之後，即可透過下列 URL 進行後續登入：https://aad.lookout.com

如果您遇到登入問題，請參閱[疑難排解文章](https://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration)。

接下來的步驟將概述要在 [Lookout MTP 主控台](https://aad.lookout.com)中完成 Lookout MTP 設定的必備工作。

### 步驟 2︰設定 Intune 連接器

1.  在 Lookout MTP 主控台中，移至 [系統] 模組，選擇 [連接器] 索引標籤，然後選取 [Intune]。

  ![開啟 [連接器] 索引標籤並醒目提示 [Intune] 選項之 Lookout MTP 主控台的螢幕擷取畫面](../media/mtp/lookout_mtp_setup-intune-connector.png)

2.  在 [連線設定] 選項中，設定 [活動訊號頻率] (以分鐘為單位)。  您的 Intune 連接器已就緒。  

  ![顯示已設定 [活動訊號頻率] 之 [連線設定] 索引標籤的螢幕擷取畫面](../media/mtp/lookout-mtp-connection-settings.png)

### 步驟 3︰設定註冊群組
在 [Enrollment Management] (註冊管理) 選項中，定義應向 Lookout 註冊其裝置的一組使用者。 最佳做法是從小型的使用者群組開始，以測試並熟悉整合的運作方式。  一旦您滿意測試結果，即可擴充註冊更多使用者群組。

若要開始使用註冊群組，請先定義適合作為要在 Lookout MTP 中註冊之第一組使用者的 Azure AD 安全性群組。 在 Azure 中建立群組之後，請在 Lookout MTP 主控台中，移至 [Enrollment Management] (註冊管理) 選項，然後新增 Azure AD 安全性群組的 [顯示名稱] 以進行註冊。

如果使用者隸屬於某個註冊群組，且他們擁有的任何裝置已受 Azure AD 識別及支援，即會向 Lookout MTP 註冊這些裝置並可在其中啟用。  當使用者第一次在其支援的裝置上開啟 Lookout for Work 應用程式時，Lookout MTP 即會啟用該裝置。
![Intune 連接器註冊頁面的螢幕擷取畫面](../media/mtp/lookout-mtp-enrollment.png)

針對檢查新裝置的時間遞增量，最佳做法是使用預設的 5 分鐘。

>[!IMPORTANT]
> 顯示名稱區分大小寫。  使用 [顯示名稱]，如 Azure 入口網站中之安全性群組的 [屬性] 頁面所示。 請注意在下圖之安全性群組的 [屬性] 頁面中，[顯示名稱] 採用駝峰式命名法。  不過，此標題會全部以小寫顯示，而且不應用來輸入 Lookout MTP 主控台。
>![Azure 入口網站中 Azure Active Directory 服務之 [屬性] 頁面的螢幕擷取畫面](../media/mtp/aad-group-display-name.png)

目前版本有下列限制：  
* 不會對群組顯示名稱進行任何驗證。  請務必使用 Azure 入口網站中所示的 [顯示名稱] 欄位值，來表示 Azure AD 安全性群組。
* 目前不支援在群組中建立其他群組。  指定的 Azure AD 安全性群組只能包含使用者，不應包含任何巢狀群組。


### 步驟 4︰設定狀態同步處理
在 [State Sync] (狀態同步處理) 選項中，指定應傳送至 Intune 的資料類型。  目前，您必須同時啟用裝置狀態和威脅狀態，Lookout 與 Intune 的整合才能正常運作。  預設會啟用這些狀態。
### 步驟 5︰設定錯誤報告電子郵件收件者資訊
在 [Error Management] (錯誤管理) 選項中，輸入應接收錯誤報告的電子郵件地址。

![Intune 連接器之 [錯誤管理] 頁面的螢幕擷取畫面](../media/mtp/lookout-mtp-connector-error-notifications.png)

### 步驟 6：設定電子郵件通知
若要接收威脅的電子郵件警示，請使用要用來接收通知的使用者帳戶登入 [Lookout MTP 主控台](https://aad.lookout.com)。 在 [系統] 模組的 [喜好設定] 索引標籤上，選擇所需的通知，並設定為 [開啟]。 儲存您的變更。

![顯示使用者帳戶之 [喜好設定] 頁面的螢幕擷取畫面](../media/mtp/lookout-mtp-email-notifications.png) 如果您不想再收到電子郵件通知，請將通知設定為 [關閉]，然後儲存變更。
### 步驟 7︰設定威脅分類
Lookout MTP 會將各種類型的行動裝置威脅進行分類。 [Lookout MTP 威脅分類](http://personal.support.lookout.com/hc/en-us/articles/114094130693)具有相關聯的預設風險層級。 您可以隨時變更這些層級，以符合您公司的需求。

![顯示威脅和分類之原則頁面的螢幕擷取畫面](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> 這裡指定的風險層級對於 MTP 而言很重要，因為 Intune 整合會根據這些風險層級，在執行階段計算裝置相容性。 換句話說，Intune 系統管理員可在原則中設定規則，以判斷當裝置具有何種實際威脅底限 (高、中或低等級) 時，要將其識別為不相容。 MTP 中的威脅分類原則會直接在 Intune 中驅動裝置相容性計算。

## 監控註冊
完成設定之後，Lookout MTP 就會開始輪詢 Azure AD，找出對應至指定註冊群組的裝置。  您可以在 [裝置] 模組中找到已註冊裝置的相關資訊。  裝置的初始狀態會顯示為 [擱置中]。  在裝置上安裝、開啟及啟用 Lookout for Work 應用程式之後，裝置狀態將會變更。  如需如何取得發送至裝置之 Lookout for Work 應用程式的詳細資訊，請參閱[設定及部署 Lookout for Work 應用程式](configure-and-deploy-lookout-for-work-apps.md)主題。
## 後續步驟
[在 Intune 中啟用 Lookout MTP 連線](enable-lookout-mtp-connection-in-intune.md)



<!--HONumber=Sep16_HO3-->


