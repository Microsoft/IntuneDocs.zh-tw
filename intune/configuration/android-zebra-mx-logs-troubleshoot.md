---
title: 在 Microsoft Intune 中的 Android Zebra 裝置上使用 StageNow 記錄-Azure |Microsoft Docs
description: 請參閱在 Android 裝置上搭配 Microsoft Intune 使用 StageNow 時的常見問題和解決方法。 同時瞭解如何取得記錄檔，並查看如何讀取記錄檔中是否有成功或錯誤的範例。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 324550836cd8e7c8ea2786d15618d5f5010a043f
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735242"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>在 Microsoft Intune 中疑難排解及查看 Android Zebra 裝置上的潛在問題

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

在 Microsoft Intune 中，您可以使用[Zebra 行動延伸模組（MX）來管理 Android Zebra 裝置](android-zebra-mx-overview.md)。 使用 Zebra 裝置時，您會在 StageNow 中建立設定檔以管理設定，並將其上傳至 Intune。 Intune 會使用 StageNow 應用程式，將設定套用到裝置上。 StageNow 應用程式也會在用來進行疑難排解的裝置上建立詳細的記錄檔。

本功能適用於：

- Android

例如，您可以在 StageNow 中建立設定檔來設定裝置。 當您建立 StageNow 設定檔時，最後一個步驟會產生檔案供您測試組態檔。 您會在裝置上使用此檔案搭配 StageNow 應用程式。

在另一個範例中，您會在 StageNow 中建立設定檔，並加以測試。 在 Intune 中，您會新增 StageNow 設定檔，然後將它指派給您的 Zebra 裝置。 檢查所指派設定檔的狀態時，設定檔會顯示高階狀態。

在這兩種情況下，您都可以從 StageNow 記錄檔取得更多詳細資料，每次套用 StageNow 設定檔時，該檔案就會儲存在裝置上。

有些問題與 StageNow 設定檔的內容無關，而且不會反映在記錄中。

本文說明如何讀取 StageNow 記錄，並列出可能不會反映在記錄檔中的其他 Zebra 裝置潛在問題。

[使用和管理具有 Zebra 行動性延伸模組的 Zebra 裝置](android-zebra-mx-overview.md)具有此功能的詳細資訊。

## <a name="get-the-logs"></a>取得記錄

### <a name="use-the-stagenow-app-on-the-device"></a>在裝置上使用 StageNow 應用程式
當您在中使用電腦上的 StageNow 直接測試組態檔時，裝置上的 StageNow 應用程式會儲存測試的記錄，而不是使用[Intune 來部署設定檔](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow)。 若要取得記錄檔，請在裝置上的 StageNow 應用程式中使用 [**更多（...）** ] 選項。

### <a name="get-logs-using-android-debug-bridge"></a>使用 Android Debug Bridge 取得記錄
若要在使用 Intune 部署設定檔之後取得記錄，請將裝置連線到具有[Android Debug Bridge （adb）](https://developer.android.com/studio/command-line/adb)的電腦（開啟 Android 的網站）。

在裝置上，記錄會儲存在 `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>從電子郵件取得記錄
若要在使用 Intune 部署設定檔之後取得記錄，終端使用者可以使用裝置上的電子郵件應用程式，以電子郵件傳送記錄給您。 在 Zebra 裝置上，開啟公司入口網站應用程式，然後[傳送記錄](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android)。 使用 [傳送記錄] 功能也會建立 PowerLift 事件識別碼，如果您聯繫 Microsoft 支援服務，就可以參考此識別碼。

## <a name="read-the-logs"></a>讀取記錄

查看記錄檔時，每當您看到 `<characteristic-error>` 標記時，就會發生錯誤。 錯誤詳細資料會寫入 `<parm-error>` 標記 > `desc` 屬性。

## <a name="error-types"></a>錯誤類型

Zebra 裝置包含不同的錯誤報表層級：

- 裝置不支援 CSP。 例如，裝置不是行動電話通訊裝置，也沒有行動電話管理員。
- MX 或 OSX 版本不相符。 每個 CSP 的版本都是。 如需完整的支援矩陣，請參閱[Zebra 的檔](http://techdocs.zebra.com/mx/)（開啟 Zebra 的網站）。
- 裝置會報告另一個問題或錯誤。

## <a name="examples"></a>範例

例如，您有下列輸入設定檔：

```xml
<wap-provisioningdoc>
    <characteristic type="Clock">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

在記錄檔中，XML 與輸入相同。 這種相符的輸出表示設定檔已成功套用至裝置，且沒有錯誤：

```xml
<wap-provisioningdoc>
    <characteristic type="Clock" version="6.0">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

在另一個範例中，您有下列輸入：

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2" >
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic type="AppMgr" version="4.2" >
        <parm name="Action" value="Install"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic>
</wap-provisioningdoc>
```

記錄檔會顯示錯誤，因為它包含 @no__t 0 標記。 在此案例中，設定檔嘗試安裝的 Android 套件（APK）不存在於指定的路徑中：

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2">
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic-error type="AppMgr" version="5.1" desc="missing">
        <parm-error name="Action" value="Install" desc="apk doesnot exist in the path"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic-error>
</wap-provisioningdoc>
```

## <a name="other-potential-issues-with-zebra-devices"></a>Zebra 裝置的其他潛在問題

本節列出當您使用裝置系統管理員的 Zebra 裝置時，可能會看到的其他可能問題。 這些問題不會在 StageNow 記錄中回報。

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView 已過期

當較舊的裝置使用公司入口網站應用程式登入時，使用者可能會看到一則訊息，指出系統 Web 工作元件已過期，而且需要升級。 如果裝置已安裝 Google Play，請將它連線到網際網路，然後檢查是否有更新。 如果裝置未安裝 Google Play，請取得元件的更新版本，並將其套用至裝置。 或者，更新為 Zebra 所發行的最新裝置作業系統。

### <a name="management-actions-take-a-long-time"></a>管理動作需要很長的時間

如果 Google Play 服務無法使用，某些工作最多需要8小時才能完成。 [Android Intune 公司入口網站應用程式的限制](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china)（開啟另一個 Microsoft 網站）可能是很好的資源。

### <a name="device-spoofing-suspected-shows-in-intune"></a>Intune 中顯示「可疑的裝置詐騙」

此錯誤表示 Intune 懷疑非 Zebra 的 Android 裝置會將其型號和製造商報告為 Zebra 裝置。

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>公司入口網站應用程式比所需的最低版本還舊

Intune 可能會更新公司入口網站應用程式的最小必要版本。 如果 Google Play 未安裝在裝置上，公司入口網站應用程式就不會自動更新。 如果所需的最低版本比安裝的版本更新，則公司入口網站應用程式會停止運作。 使用[Zebra 裝置上](android-zebra-mx-overview.md#sideload-the-company-portal-app)的側載，更新至最新的公司入口網站應用程式。

## <a name="next-steps"></a>後續步驟

[Zebra 討論](https://developer.zebra.com/community/home/discussions)區（開啟 Zebra 的網站）

[在 Intune 中使用 Zebra 行動性延伸模組使用及管理 Zebra 裝置](android-zebra-mx-overview.md)
