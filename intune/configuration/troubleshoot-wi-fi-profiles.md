---
title: 檢閱 Microsoft Intune 中的 Wi-Fi 裝置設定檔記錄並進行疑難排解 - Azure | Microsoft Docs
description: 了解 Microsoft Intune 中 Android、iOS 和 Windows 裝置上的 Wi-Fi 裝置組態設定檔問題，並進行疑難排解。 檢閱記錄，並查看一些常見的問題和可能的解決方式。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 70f471e7f4db7ddce89d8956474822375c684944
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547970"
---
# <a name="troubleshoot-wi-fi-device-configuration-profiles-in-microsoft-intune"></a>針對 Microsoft Intune 中的 Wi-Fi 裝置組態設定檔進行疑難排解

在 Intune 中，您可以建立裝置組態設定檔，其中包括 WiFi 網路的連線設定。 使用這些設定，將使用者的 Android、iOS 和 Windows 裝置連線到組織網路。

本文說明將 Wi-Fi 設定檔成功套用於裝置後的樣子。 它也包括記錄資訊、常見問題等等。 使用本文來協助您針對 Wi-Fi 設定檔進行疑難排解。

如需 Intune 中 Wi-Fi 設定檔的詳細資訊，請參閱[在裝置上新增和使用 Wi-Fi 設定](wi-fi-settings-configure.md)。

## <a name="before-you-begin"></a>開始之前

本文中的範例會使用適用於 Intune 設定檔的 SCEP 憑證驗證。 它也假設受信任的根和 SCEP 設定檔可在裝置上正確運作。

## <a name="android"></a>Android

在本節中，我們會逐步解說在 Android 裝置上安裝組態設定檔時的終端使用者體驗。

### <a name="end-user-experience-example"></a>終端使用者體驗範例

此情節使用 Nokia 6.1 裝置。 在裝置上安裝 Wi-Fi 設定檔之前，請先安裝受信任的根和 SCEP 設定檔。

1. 終端使用者會收到安裝受信任的根憑證設定檔的通知：

    > [!div class="mx-imgBorder"]
    > ![在 Android 上安裝受信任的根憑證設定檔的公司入口網站應用程式通知範例](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-trusted-root.png)

2. 下一個通知會提示您安裝 SCEP 憑證設定檔：

    > [!div class="mx-imgBorder"]
    > ![在 Android 上安裝 SCEP 憑證設定檔的公司入口網站應用程式通知範例](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-scep-certificate.png)

    > [!TIP]
    > 使用裝置管理員管理的 Android 裝置時，可能會列出多個憑證。 撤銷或移除憑證設定檔時，憑證會保留在裝置上。 在此情節中，請選取最新的憑證。 這通常是清單中顯示的最後一個憑證。
    >
    > 這種情況不會發生在 Android Enterprise 和 Samsung Knox 裝置上。 如需詳細資訊，請參閱[管理 Android 工作設定檔裝置](../enrollment/android-enterprise-overview.md)和[移除 SCEP 和 PKCS 憑證](../protect/remove-certificates.md#android-knox-devices)。

3. 接下來，使用者會收到安裝 Wi-Fi 設定檔的通知：

    > [!div class="mx-imgBorder"]
    > ![在 Android 上安裝 SCEP 憑證設定檔的公司入口網站應用程式通知範例](./media/troubleshoot-wi-fi-profiles/android-end-user-install-wifi-profile.png)

4. 完成時，Wi-Fi 連線會顯示為已儲存的網路：

    > [!div class="mx-imgBorder"]
    > ![Wi-Fi 連線會顯示為已儲存的網路](./media/troubleshoot-wi-fi-profiles/android-end-user-saved-networks.png)

### <a name="review-company-portal-app-logs"></a>檢閱公司入口網站應用程式記錄

在 Android 上，**Omadmlog .log** 檔會詳細說明 Wi-Fi 設定檔安裝在裝置上時的活動。 您最多可以有五個 Omadmlog 記錄檔。 請務必取得上次同步處理的時間戳記，因為它會協助您尋找相關的記錄項目。

在下列範例中，使用 [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) 讀取記錄檔，並搜尋 "wifimgr"：

> [!div class="mx-imgBorder"]
> ![Wi-Fi 連線會顯示為已儲存的網路](./media/troubleshoot-wi-fi-profiles/android-cmtrace-filter-wifimgr.png)

下列記錄會顯示您的搜尋結果，並顯示成功套用的 Wi-Fi 設定檔：

```log
2019-08-01T19:22:46.7340000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.7490000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:46.8100000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:46.8209999    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.8240000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected ca certificate with alias: 'user:205xxxxx.0' and thumbprint '<thumbprint>'.
2019-08-01T19:22:47.0990000    VERB    com.microsoft.omadm.platforms.android.certmgr.CertificateChainBuilder    15118    04142    Complete certificate chain built with Complete certs.
2019-08-01T19:22:47.1010000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    1 cert(s) matched criteria: User<ID>[i:<ID>,17CECEA1D337FAA7D167AD83A8CC7A8FCBF9xxxx;eku:1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2]
2019-08-01T19:22:47.1090000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    0 cert(s) excluded by criteria:
2019-08-01T19:22:47.1110000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected client cert with alias 'User<ID>' and requestId 'ModelName=<ModelName>%2FLogicalName_<LogicalName>;Hash=-912418295'.
2019-08-01T19:22:47.4120000    VERB    com.microsoft.omadm.Services    15118    04142    Successfully applied, enabled and saved wifi profile '<profile ID>'
2019-08-01T19:22:47.4240000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.4910000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.4970000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5080000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.5820000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.5900000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5910000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04142    Applied profile <profile ID>

```

## <a name="ios"></a>iOS

在裝置上安裝 Wi-Fi 設定檔之後，它會顯示在 [管理設定檔]  中：

> [!div class="mx-imgBorder"]
> ![iOS 裝置上的管理設定檔](./media/troubleshoot-wi-fi-profiles/ios-management-profile.png)

> [!div class="mx-imgBorder"]
> ![Wi-Fi 連線會在 iOS 裝置上顯示為 Wi-Fi 網路](./media/troubleshoot-wi-fi-profiles/ios-wifi-connection-in-management-profile.png)

### <a name="review-the-ios-console-and-device-logs"></a>檢閱 iOS 主控台和裝置記錄

在 iOS 裝置上，公司入口網站應用程式記錄不包含 Wi-Fi 設定檔的相關資訊。 若要查看 Wi-Fi 設定檔的安裝詳細資料，請使用主控台/裝置記錄：

1. 將 iOS 裝置連線到 Mac。 移至 [應用程式]   > [公用程式]  ，然後開啟主控台應用程式。
2. 在 [動作]  底下，選取 [包含資訊訊息]  和 [包含偵錯訊息]  ：

    > [!div class="mx-imgBorder"]
    > ![iOS 主控台應用程式中的 [包含資訊訊息] 和 [包含偵錯訊息]](./media/troubleshoot-wi-fi-profiles/ios-console-app-include-info-messages-debug-messages.png)

3. 重現情節，並將記錄儲存至文字檔：

    1. 選取目前畫面上的所有訊息：[編輯]   > [全選]  。
    2. 複製訊息：[編輯]   > [複製]  。
    3. 在文字編輯器中貼上記錄資料，然後儲存檔案。

4. 搜尋儲存的記錄檔，以查看詳細資訊。 當設定檔成功安裝時，您的輸出看起來會類似下列記錄：

    ```log
    Line 390870: debug    11:19:58.994815 -0400    profiled    Adding dependent www.windowsintune.com.wifi.Contoso to parent Microsoft.Profiles.MDM in domain ManagingProfileToManagedProfile to system\
    Line 390872: debug    11:19:58.995210 -0400    profiled    Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.wifi.Contoso in domain ManagedProfileToManagingProfile to system\
    Line 392346: default    11:19:59.360460 -0400    profiled    Profile \'93www.windowsintune.com.wifi.Contoso\'94 installed.\
    ```

## <a name="windows"></a>Windows

在裝置上安裝 Wi-Fi 設定檔後，移至 [設定]   > [帳戶]   > [存取公司或學校資源]  。 選取您的帳戶 > [資訊]  ：

> [!div class="mx-imgBorder"]
> ![存取公司或學校資源，並選取 Windows 裝置上的資訊](./media/troubleshoot-wi-fi-profiles/windows-access-work-school-info.png)

在 **Microsoft 管理的區域**中，會顯示 [WiFi]  ：

> [!div class="mx-imgBorder"]
> ![在 Microsoft 管理的區域中，會看到 Windows 列出了 WiFi](./media/troubleshoot-wi-fi-profiles/windows-wifi-areas-managed-by-microsoft.png)

若要查看 Wi-Fi 連線，請移至 [設定]   > [網路與網際網路]    > [Wi-Fi]  ：

> [!div class="mx-imgBorder"]
> ![在 Windows 上，將 Wi-Fi 連線視為設定中的已知網路](./media/troubleshoot-wi-fi-profiles/windows-wifi-connection-known-networks.png)

### <a name="review-event-viewer-logs"></a>檢閱事件檢視器記錄

在 Windows 裝置上，Wi-Fi 設定檔的詳細資料會記錄在事件檢視器中：

1. 開啟 [事件檢視器]  應用程式。
2. 在 [檢視]  功能表上，選取 [顯示分析和偵錯記錄]  。
3. 展開 [應用程式及服務記錄檔]   > [Microsoft]   > [Windows]   > [DeviceManagement-Enterprise-Diagnostic-Provider]   > [管理員] 

您的輸出應類似以下記錄：

```log
Log Name:      Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
Source:        Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider
Date:          8/7/2019 8:01:41 PM
Event ID:      1506
Task Category: (1)
Level:         Information
Keywords:      (2)
User:          SYSTEM
Computer:      <Computer Name>
Description:
WiFiConfigurationServiceProvider: Node set value, type: (0x4), Result: (The operation completed successfully.).
```

## <a name="common-issues"></a>常見問題

### <a name="issue-1-the-wi-fi-profile-isnt-deployed-to-the-device"></a>問題 1：Wi-Fi 設定檔未部署至裝置

- 確認 Wi-Fi 設定檔已指派給正確的群組：

    1. 在 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)內，選取 [裝置]   > [組態設定檔]  。
    2. 選取您的設定檔 > [指派]  。 確認選取的群組正確。
    3. 在 [端點管理員] 中，選取 [疑難排解 + 支援]  。 檢閱 [指派]  資訊。

- 在 [端點管理員] 中，選取 [疑難排解 + 支援]  。 藉由檢查 [上次簽入]  時間，確認裝置可以與 Intune 同步處理。

- 如果 Wi-Fi 設定檔已連結至受信任的根和 SCEP 設定檔，請確認這兩個設定檔都已部署至裝置。 Wi-Fi 設定檔相依於這些設定檔。

- 在 Windows 10 和更新版本的裝置上，檢閱 MDM 診斷資訊記錄：

  1. 移至 [設定]   > [帳戶]   > [存取公司或學校資源]  。
  2. 選取您的工作或學校帳戶 > [資訊]  。
  3. 在 [設定]  頁面底部，選取 [建立報表]  。
  4. 隨即開啟一個視窗，其中顯示記錄檔的路徑。 選取 [匯出]  。
  5. 移至 `\Users\Public\Documents\MDMDiagnostics` 路徑，並查看報表：

      > [!div class="mx-imgBorder"]
      > ![顯示 Windows 10 裝置上 WiFi 設定檔設定的 MDM 診斷資訊範例](./media/troubleshoot-wi-fi-profiles/windows-mdm-diagnostic-info.png)

  > [!TIP]
  > 如需詳細資訊，請參閱[診斷 Windows 10 中的 MDM 失敗](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) \(部分機器翻譯\)。

- 在 Android 裝置上，如果裝置上未安裝受信任的根和 SCEP 設定檔，您會在公司入口網站應用程式 Omadmlog 檔中看到下列項目：

  ``` log
  2019-08-01T19:18:13.5120000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04105    Skipping Wifi profile <profile ID> because it is pending certificates.
  ```

  - 當受信任的根和 SCEP 設定檔位於 Android 裝置上且符合規範時，Wi-Fi 設定檔可能不在裝置上。 當來自公司入口網站應用程式的 **CertificateSelector** 提供者找不到符合指定準則的憑證時，就會發生此問題。 特定準則可能在憑證範本或 SCEP 設定檔中。

    如果找不到相符的憑證，就不會安裝裝置上的憑證。 因為沒有正確的憑證，所以不會套用 Wi-Fi 設定檔。 在此情節中，您會在公司入口網站應用程式 Omadmlog 檔中看到下列項目：

    ` Skipping Wifi profile <profile ID> because it is pending certificates.`

    下列範例記錄顯示已排除的憑證，因為已指定 [任何目的]  擴充金鑰使用方法 (EKU) 準則。 但是，指派給裝置的憑證沒有該 EKU：

    ```log
    2018-11-27T21:10:37.6390000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID1> and requestId <requestID1> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID2> and requestId <requestID2> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    0 cert(s) matched criteria:
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    2 cert(s) excluded by criteria:
    2018-11-27T21:10:37.6400000    INFO       com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager       14210                00948     Skipping Wifi profile <profile ID> because it is pending certificates.
    ```

    下列範例顯示輸入了 [任何目的]  EKU 的 SCEP 設定檔。 但是，它不會在憑證授權單位 (CA) 的憑證範本中輸入。 若要修正此問題，請將 [任何目的]  選項新增至憑證範本。 或者，從 SCEP 設定檔移除 [任何目的]  選項。

    > [!div class="mx-imgBorder"]
    > ![在 Android 上，將 [任何目的] 新增至憑證授權單位上的憑證範本](./media/troubleshoot-wi-fi-profiles/android-add-any-purpose-eku.png)

    > [!div class="mx-imgBorder"]
    > ![在 Android 上，將 [任何目的] 新增至 Intune 中的 SCEP 憑證組態設定檔](./media/troubleshoot-wi-fi-profiles/android-any-purpose-scep-device-config-profile.png)

  - 確認完整憑證鏈中的所有必要憑證都在 Android 裝置上。 否則，Wi-Fi 設定檔無法安裝在裝置上。 如需詳細資訊，請參閱[遺漏的中繼憑證授權單位](https://developer.android.com/training/articles/security-ssl#MissingCa) (會開啟 Android 的網站)。
  - 使用關鍵字篩選 Omadmlog 以尋找資訊，例如在 Wi-Fi 設定檔中使用的憑證，以及設定檔是否成功套用。

    例如，使用 [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) 讀取記錄。 使用搜尋字串來篩選 "wifimgr"：

    > [!div class="mx-imgBorder"]
    > ![篩選 CMTrace 以尋找 Android 裝置上的 WiFiMgr 組態設定檔](./media/troubleshoot-wi-fi-profiles/cmtrace-filter-wifimgr.png)

    輸出看起來類似下列記錄：

    > [!div class="mx-imgBorder"]
    > ![顯示已成功在裝置上套用 WiFi Intune 組態設定檔的 CMTrace 記錄輸出範例](./media/troubleshoot-wi-fi-profiles/cmtrace-sample-log-output.png)

    如果您在記錄中看到錯誤，請複製錯誤的時間戳記，並取消篩選記錄。 然後，使用 [尋找] 選項搭配時間戳記，以查看錯誤發生前的情況。

### <a name="issue-2-the-wi-fi-profile-is-deployed-to-the-device-but-the-device-cant-connect-to-the-network"></a>問題 2：Wi-Fi 設定檔已部署至裝置，但裝置無法連線到網路

通常，此問題是由 Intune 以外的東西所造成。 下列工作可協助您了解並針對連線問題進行疑難排解：

- 使用 Wi-Fi 設定檔中具有相同準則的憑證，以手動方式連線到網路。

  如果您可以連線，請查看手動連線中的憑證屬性。 然後，使用相同的憑證屬性來更新 Intune Wi-Fi 設定檔。
- 連線錯誤通常會記錄在 Radius 伺服器記錄中。 例如，它應該會顯示裝置是否嘗試使用 Wi-Fi 設定檔進行連線。

## <a name="need-more-help"></a>需要其他協助

- 使用 [Intune 使用者論壇](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc) \(英文\) 或[取得 Microsoft 支援](../fundamentals/get-support.md)。

- 如需 Microsoft Intune 中 Wi-Fi 設定檔的詳細資訊，請參閱下列文章：

  - 針對執行 [Android](wi-fi-settings-android.md)、[iOS](wi-fi-settings-ios.md) 和 [Windows 10 與更新版本](wi-fi-settings-windows.md)的裝置新增 Wi-Fi 設定。
  - [支援提示 - 如何在 Intune 中為 SCEP 憑證部署設定 NDES](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-How-to-configure-NDES-for-SCEP-certificate/ba-p/455125)
  - 針對 [SCEP 憑證設定檔部署](https://support.microsoft.com/help/4526725/troubleshooting-scep-profile-deployment-to-android-devices-in-intune)和 [NDES 設定](https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune)進行疑難排解。

- 如需最新消息、資訊和技術秘訣，請參閱官方部落格：
  - [Microsoft Intune 支援小組部落格](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess) \(英文\)
  - [Microsoft Enterprise Mobility 與安全性小組部落格](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity) \(英文\)

## <a name="next-steps"></a>後續步驟

[監視您的設定檔](device-profile-monitor.md)。
