---
title: 使用 StageNow 登入 Microsoft Intune-Azure 中的色彩 Android 裝置 |Microsoft Docs
description: 使用 Microsoft Intune 的 Android 裝置上使用 StageNow 時，請參閱常見問題與解決方案。 也了解如何取得記錄檔，並了解如何讀取為成功或錯誤記錄檔的範例。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36476820805c00cefafcd9f64dd2f08a014762c0
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490536"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>疑難排解，並在 Microsoft Intune 中的色彩 Android 裝置上看到潛在問題

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

在 Microsoft Intune，您可以使用[色彩行動擴充程式 (MX) 來管理 Android 色彩裝置](android-zebra-mx-overview.md)。 使用色彩的裝置，您 StageNow 管理設定，在建立設定檔，並將它們上傳至 Intune。 Intune 會使用 StageNow 應用程式，以在裝置上套用設定。 StageNow 應用程式也會建立詳細的記錄檔，可用來疑難排解在裝置上。

本功能適用於：

- Android

比方說，您可以建立設定檔中設定裝置的 StageNow。 當您建立 StageNow 設定檔時，最後一個步驟為測試設定檔，就會產生檔案。 您使用此檔案 StageNow 應用程式在裝置上。

在另一個範例中，您可以在 StageNow，建立設定檔，並加以測試。 在 Intune 中，您可以新增 StageNow 設定檔中，並將其指派給您的色彩裝置。 檢查時指派的設定檔的狀態，設定檔會顯示的高階狀態。

在這兩種情況中，您可以取得更多詳細資料從 StageNow 記錄檔，並在每次 StageNow 設定檔適用於儲存在裝置上。

一些問題無關的 StageNow 設定檔的內容，而且不反映在記錄檔。

本文示範如何讀取 StageNow 記錄，並列出其他潛在的問題，就不會反映在記錄中的色彩裝置。

[使用及管理色彩行動延伸模組使用的色彩裝置](android-zebra-mx-overview.md)有這項功能的詳細資訊。

## <a name="get-the-logs"></a>取得記錄檔

### <a name="use-the-stagenow-app-on-the-device"></a>在裝置上使用 StageNow 應用程式
當您測試設定檔中，而不是使用您電腦上使用直接 StageNow[部署設定檔的 Intune](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow)，StageNow 應用程式在裝置上的儲存從已測試的記錄。 若要取得記錄檔，請使用**詳細 （...）** StageNow 應用程式在裝置上的選項。

### <a name="get-logs-using-android-debug-bridge"></a>取得使用 Android Debug Bridge 的記錄檔
若要使用 Intune 已部署的設定檔之後，請取得記錄檔，將裝置連接到的電腦[Android Debug Bridge (adb)](https://developer.android.com/studio/command-line/adb) （開啟 Android 的網站）。

在裝置上，記錄會儲存在 `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>取得電子郵件中的記錄檔
若要使用 Intune 已部署的設定檔之後，請取得記錄檔，使用者可以傳送電子郵件您在裝置上使用的電子郵件應用程式的記錄檔。 色彩在裝置上，開啟 公司入口網站應用程式，並[記錄檔傳送](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android)。 使用傳送記錄檔功能也會建立 PowerLift 事件識別碼，您可以參考如果連絡 Microsoft 支援服務。

## <a name="read-the-logs"></a>讀取記錄檔

檢視記錄檔時，卻發生錯誤時，您會看到`<characteristic-error>`標記。 錯誤詳細資料會寫入`<parm-error>`標記 >`desc`屬性。

## <a name="error-types"></a>錯誤類型

色彩的裝置包括不同的錯誤報告層級：

- 裝置不支援 CSP。 比方說，裝置不是行動電話通訊的裝置，而沒有行動電話通訊的管理員。
- MX 或 OSX 版本不相符。 每個 CSP 已建立版本。 如需完整的支援矩陣，請參閱 <<c0> [ 色彩的文件](http://techdocs.zebra.com/mx/)（開啟色彩的網站）。
- 裝置會回報另一個問題或錯誤。

## <a name="examples"></a>範例

例如，您會有下列的輸入設定檔：

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

在記錄中的 XML 是與輸入相同的。 此比對輸出表示已成功套用至裝置未出現任何錯誤的設定檔：

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

在另一個範例中，您會有下列輸入：

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

記錄檔會顯示錯誤，因為它包含`<characteristic-error>`標記。 在此案例中，設定檔會嘗試安裝 Android 套件 (APK) 不存在指定的路徑中：

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

## <a name="other-potential-issues-with-zebra-devices"></a>色彩裝置與其他潛在的問題

此區段會列出其他可能的問題，您可能會看到使用色彩裝置與裝置系統管理員時。 StageNow 記錄檔中未回報這些問題。

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView 已過期

當較舊的裝置登入使用公司入口網站應用程式時，使用者可能會看到訊息指出 System WebView 元件已過期，而且必須升級。 如果裝置具有 Google Play 安裝，將它連線到網際網路，並檢查更新。 如果裝置沒有 Google Play 安裝、 取得更新的版本的元件，並將它套用到裝置。 或者，您也可以更新至最新的裝置作業系統公布的色彩。

### <a name="management-actions-take-a-long-time"></a>管理動作需要很長的時間

如果 Google Play 服務無法使用，有些工作會需要 8 小時的時間才能完成。 [限制的 Intune 公司入口網站應用程式，適用於 Android](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) （開啟另一個 Microsoft 網站上） 可能是不錯的資源。

### <a name="device-spoofing-suspected-shows-in-intune"></a>在 Intune 中會顯示 「 裝置詐騙可疑 」

此錯誤表示 Intune 懷疑自己的模型和製造商為色彩裝置回報非-色彩 Android 裝置。

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>公司入口網站應用程式已超過最小必要版本

Intune 可能更新公司入口網站應用程式的最小必要的版本。 如果裝置未安裝 Google Play，公司入口網站應用程式不會自動更新。 如果所需要的最低版本為比已安裝的版本還新，公司入口網站應用程式會停止運作。 最新的公司入口網站應用程式使用的更新[色彩裝置上的側載](android-zebra-mx-overview.md#sideload-the-company-portal-app)。

## <a name="next-steps"></a>後續步驟

[色彩討論區](https://developer.zebra.com/community/home/discussions)（開啟色彩的網站）

[使用及管理在 Intune 中的色彩行動延伸模組使用的色彩裝置](android-zebra-mx-overview.md)
