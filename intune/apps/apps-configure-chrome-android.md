---
title: 使用 Intune 設定適用於 Android 裝置的 Google Chrome
titleSuffix: Microsoft Intune
description: 將 Intune 設定原則與適用於 Android 裝置的 Google Chrome 搭配使用。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: c02ea34417073091e2f2841b363edfb9966ce558
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2019
ms.locfileid: "75205899"
---
# <a name="configure-google-chrome-for-android-devices-using-intune"></a>使用 Intune 設定適用於 Android 裝置的 Google Chrome 

您可以使用 Intune 應用程式設定原則來設定適用於 Android 裝置的 Google Chrome。 應用程式的設定可以自動套用。 例如，您可以特別設定您想要封鎖或允許的書籤和 URL。

## <a name="prerequisites"></a>先決條件

- 使用者的 Android Enterprise 裝置必須在 Intune 中註冊。 如需詳細資訊，請參閱[設定 Android Enterprise 工作設定檔裝置的註冊](~/enrollment/android-work-profile-enroll.md)。
- Google Chrome 會新增為受控 Google Play 應用程式。 如需受控 Google Play 的相關詳細資訊，請參閱[將您的 Intune 帳戶連結到受控 Google Play 帳戶](~/enrollment/connect-intune-android-enterprise.md)。

## <a name="add-the-google-chrome-app-to-intune"></a>將 Google Chrome 應用程式新增至 Intune

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [所有應用程式]   > [新增]  ，然後新增 [受控的 Google Play]  應用程式。
3. 移至 [受控 Google Play]，使用 **Google Chrome** 進行搜尋並核准。

    ![搜尋及核准 Google Chrome](~/apps/media/apps-configure-chrome-android/search.png)

4. 將 Google Chrome 作為必要的應用程式類型指派給使用者群組。 當裝置註冊到 Intune 時，將會自動部署 Google Chrome。

如需將受控 Google Play 應用程式新增至 Intune 的其他相關詳細資料，請參閱[受控 Google Play 商店應用程式](~/apps/apps-add-android-for-work.md#managed-google-play-store-apps)。

## <a name="add-app-configuration-for-managed-ae-devices"></a>新增受控 AE 裝置的應用程式設定

1. 從 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，選取 [應用程式]   > [應用程式設定原則]   > [新增]   > [受控裝置]  。
2. 使用下列詳細資料：
    - **名稱** - 在 Azure 入口網站中顯示的設定檔名稱。
    - **描述** - 在 Azure 入口網站中顯示的設定檔描述。
    - [裝置註冊類型]  - 此設定會設定為 [受控裝置]  。
    - **平台** - 選取 [Android]  。

    ![新增 Google Chrome 設定原則](~/apps/media/apps-configure-chrome-android/add-policy.png)

3. 按一下 [相關聯的應用程式]  ，以顯示 [相關聯的應用程式]  窗格。 尋找並選取 **Google Chrome**。 此清單包含[您已經使用 Intune 核准並同步處理的受控 Google Play 應用程式](~/apps/apps-add-android-for-work.md)。

    ![在 [相關聯的應用程式] 底下選取 [Google Chrome]](~/apps/media/apps-configure-chrome-android/associated-app.png)

4. 按一下 [組態設定]  ，選取 [使用組態設計工具]  ，然後按一下 [新增]  以選取設定金鑰。

    ![新增 [使用組態設計工具]](~/apps/media/apps-configure-chrome-android/configuration.png)

    以下是一般設定的範例：
    - **封鎖存取 URL 清單**：`["*"]`
    - **允許存取 URL 清單**：`["baidu.com", "youtube.com", "chromium.org", "chrome://*"]`
    - **受控書籤**：`[{"toplevel_name": "My managed bookmarks folder"  },  {"url": "baidu.com",   "name": "Baidu"},  {"url": "youtube.com", "name": "Youtube"},  {"name": "Chrome links",  "children": [{"url": "chromium.org", "name": "Chromium"},    {"url": "dev.chromium.org", "name": "Chromium Developers"}]}]`
    - **Incognito 模式可用性**：`Incognito mode disabled`

    使用組態設計工具新增組態設定之後，它們就會在表格中列出。 

    ![一般設定](~/apps/media/apps-configure-chrome-android/common-settings.png)

    上面的設定會建立書籤，並封鎖對所有 URL 的存取，`baidu.com`、`yahoo.com`、`chromium.org` 與 `chrome://` 除外。

5. 按一下 [確定]  與 [新增]  ，將您的設定原則新增至 Intune。
6. 將此設定原則指派給使用者群組。 如需詳細資訊，請參閱[使用 Microsoft Intune 將應用程式指派給群組](~/apps/apps-deploy.md)。 

## <a name="verify-the-device-settings"></a>確認裝置設定

Android 裝置向 Android Enterprise 註冊之後，具有公事包圖示的受控 Google Chrome 應用程式將自動部署。
 
   <img alt="Managed Google Chrome with the portfolio icon" src="~/apps/media/apps-configure-chrome-android/chrome-icon.png" width="350">

啟動 Google Chrome，您就會發現已套用設定。

   書籤：<br>
   <img alt="Bookmarks" src="~/apps/media/apps-configure-chrome-android/bookmarks.png" width="350">

   封鎖的 URL：<br>
   <img alt="Blocked URL" src="~/apps/media/apps-configure-chrome-android/blocked-url.png" width="350">

   允許 URL：<br>
   <img alt="Allow URL" src="~/apps/media/apps-configure-chrome-android/allowed-url.png" width="350">

   無痕索引標籤：<br>
   <img alt="Incognito tab" src="~/apps/media/apps-configure-chrome-android/incognito-tab.png" width="350">

## <a name="troubleshooting"></a>疑難排解

1. 請檢查 Intune 入口網站來監視原則部署狀態。

    ![監視原則部署狀態](~/apps/media/apps-configure-chrome-android/monitor-status.png)

2. 啟動 Google Chrome 並造訪 **chrome://policy**。 我們可以確認是否已成功套用設定。

    ![確認已成功套用設定](~/apps/media/apps-configure-chrome-android/confirm.png)

## <a name="additional-information"></a>其他資訊

- [為受控的 Android Enterprise 裝置新增應用程式設定原則](~/app-configuration-policies-use-android.md)
- [Chrome Enterprise 原則清單](https://cloud.google.com/docs/chrome-enterprise/policies/) \(英文\)

## <a name="next-steps"></a>後續步驟

- 如需 Android Enterprise 完全受控裝置的詳細資訊，請參閱[設定 Android Enterprise 完全受控裝置的 Intune 註冊](~/enrollment/android-fully-managed-enroll.md)。
