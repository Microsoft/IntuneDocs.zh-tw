---
# required metadata

title: 新功能 | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 的新功能

## 2016 年 4 月
混合式客戶也支援這些功能 (Configuration Manager 與 Intune 整合)。
### 應用程式管理
- **MAM 使用者相容性。**
您現在可以檢視 Azure Active Directory (AAD) 租用戶中任一使用者的應用程式管理原則[狀態](monitor-mobile-app-management-policies-with-Microsoft-Intune.md)。 這包括：
   - 裝置
   - 裝置上的應用程式

   狀態值：

   已存回︰表示原則已部署至使用者，且已使用工作內容中的應用程式，並成功接收原則。

    未存回︰表示原則已部署至使用者，但是應用程式從那時起並未在工作內容中使用。


- **避免 Outlook 連絡人同步處理 (Android) 的 MAM 控制項。**
新的設定可供[行動應用程式管理](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)使用，而不需要裝置註冊。 此設定可讓您防止應用程式在 Android 裝置上將連絡人同步處理至原生通訊錄。 啟用此設定時，目標應用程式將不再能夠儲存連絡人到原生通訊錄。 停用此設定時，目標應用程式將能夠儲存連絡人到原生通訊錄。 當您[從遠端抹除裝置或應用程式](wipe-managed-company-app-data-with-Microsoft-Intune.md)時，將會移除所有已儲存至原生通訊錄的連絡人。 在 Android 裝置上的 Outlook 應用程式一開始支援這個新的設定。

### 裝置管理
- **公司擁有裝置的電話號碼識別。** 分類為「公司」的電話現在會在 (舉例而言) 您執行行動裝置清查報表時利用其完整電話號碼加以識別。 BYOD 電話號碼會持續以 **** 遮罩，僅顯示最後 4 位數。


### 公司入口網站更新
Android 公司入口網站應用程式 尚未在 Intune 中註冊其裝置，且沒有安裝正確憑證的使用者，將無法登入 Android 公司入口網站應用程式，而且會看到以下訊息，「您無法登入，因為您的裝置缺少必要的憑證」。 此訊息包含使用者可以點選以參閱安裝憑證的指示之「如何解決此問題」連結。

若要查看使用者需遵循才能解決此問題的步驟，請參閱[您的裝置缺少必要的憑證](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing) iOS 公司入口網站應用程式

支援已新增至下拉更新動作，以重新整理主畫面上的內容，其中包括列出的應用程式、列出的裝置，以及 IT 連絡人資訊。 下拉更新動作並未檢查相容性或原則資訊，而這可以透過選取目前裝置的磚並點選 [同步處理] 按鈕來完成。 Windows 10 Mobile 和 Windows Phone 8.1 公司入口網站應用程式

當使用者安裝企業營運應用程式時，就會看到改善的應用程式安裝體驗。

* 如果應用程式安裝花很長的時間，使用者可以手動同步處理他們的裝置，以強制同步處理程序繼續執行。 若要檢閱使用者指示，請參閱[以手動方式同步處理您的裝置，以加速應用程式安裝](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually) 公司入口網站
* 當 Windows 10 Mobile 和 Windows Phone 8.1 使用者安裝企業營運應用程式時，他們會看到下列新狀態，可提供其安裝狀態的更詳細資料︰

正在等待裝置同步處理 – 使用者已點選 [安裝]，而裝置會嘗試與 Intune 基礎結構同步處理。 安裝完成之前需要同步處理。

### 「正在等待裝置同步處理」的訊息也是一個連結，使用者可以點選以在同步處理程序花了較長的時間或已停止時，查看如何手動將他們的裝置與 Intune 同步處理的[指示](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually)。

**正在下載 – 正在處理使用者的下載要求，且裝置正在下載與安裝應用程式。** 新增這些狀態之前，如果應用程式安裝花了較長的時間，會讓使用者混淆，因為他們只看到「正在安裝」狀態，可能會在螢幕上維持時小數。 新增狀態表示，使用者現在就可以點選 [正在等待裝置同步處理] 連結，並遵循指示以強制同步處理程序繼續執行，而不是呼叫支援。 未來動態  裝置註冊管理員帳戶的變更。 為了改善效能和擴充，Intune 將不再於公司入口網站的 [我的裝置] 窗格中，顯示所有的裝置註冊管理員 (DEM) 裝置。  只有執行應用程式的本機裝置會顯示，只有在透過公司入口網站應用程式註冊時才會顯示。

DEM 使用者可在本機裝置上執行動作，但是其他已註冊裝置的遠端管理只能從 Intune 管理主控台執行。


## 此外，Intune 將會使用 DEM 帳戶取代 Apple 裝置註冊方案或 Apple configurator 工具。
這兩種註冊方法已經支援共用之 iOS 裝置的較少使用者註冊。



### 只有在共用裝置的較少使用者註冊無法使用時，才能使用 DEM 帳戶。
* [請參閱 [Cloud Platform roadmap (雲端平台藍圖)](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)，隨時關注 Intune 的最新發展](http://go.microsoft.com/fwlink/?LinkID=273882)


<!--HONumber=May16_HO2-->


