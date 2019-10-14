---
title: Microsoft Intune 的應用程式設定原則
titleSuffix: ''
description: 了解在 Microsoft Intune 中如何於 iOS 或 Android 裝置上使用應用程式設定原則。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08017be16e4257ef0bd7bfb775197feaa20baf75
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940367"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Microsoft Intune 的應用程式設定原則

應用程式設定原則可讓您在終端使用者執行應用程式之前，將組態設定指派給已指派給終端使用者的原則來去除應用程式設定問題。 在終端使用者裝置上設定應用程式時，這些設定會自動提供，使用者不需要採取動作。 每個應用程式的組態設定均為唯一。 

您可以建立及使用應用程式設定原則，以提供 iOS 或 Android 應用程式的組態設定。 這些組態設定允許使用應用程式設定及管理來自訂應用程式。 每當應用程式檢查是否有設定原則設定時 (通常是應用程式第一次執行時)，便會使用這些設定。 

例如，應用程式組態設定可能需要您指定下列任何詳細資料：

- 自訂連接埠號碼
- 語言設定
- 安全性設定
- 公司標誌等品牌設定

如果終端使用者改為輸入這些設定，則他們可能會以不正確的方式執行此動作。 應用程式設定原則可為整個企業提供一致性，並減少終端使用者嘗試自行設定時撥給技術服務人員的電話數量。 藉由使用應用程式設定原則，可更加輕鬆且快速地採用新應用程式。

應用程式開發人員最終會決定可用的設定參數。 您應檢閱應用程式廠商的文件以查看應用程式是否支援設定，同時也查看可用的設定。 Intune 會針對某些應用程式填入可用的組態設定。 

> [!NOTE]
> 在受控的 Google Play 商店中，支援設定的應用程式將會標示為：
> 
> ![已設定應用程式的螢幕擷取畫面](./media/app-configuration-policies-overview/configured-app.png)
>
> 使用受控裝置作為 Android 裝置的註冊類型時，您只會看到來自[受控 Google Play 商店](https://play.google.com/work) (而不是 [Google Play 商店](https://play.google.com/store/apps)) 的應用程式。 受控 Google Play 商店 (也稱為 Android for Work (AfW)) 和 Android Enterprise 是工作設定檔中的應用程式，其中包含支援應用程式設定的應用程式版本。

您可以使用[包含與排除指派的組合](apps-inc-exl-assignments.md)，將應用程式設定原則指派給一群終端使用者和裝置。 新增應用程式設定原則後，就可以設定指派應用程式設定原則。 當您設定原則指派時，您可以選擇包含與排除要套用原則的終端使用者[群組](../fundamentals/groups-add.md)。 當您選擇要包含一或多個群組時，您可以選擇選取要包含特定群組或選取內建群組。 內建群組包括 [所有使用者]  、[所有裝置]  和 [所有使用者及所有裝置]  。

您有兩個選項來使用 Intune 的應用程式設定原則：
- **受控裝置** - Intune 以行動裝置管理 (MDM) 提供者身分管理裝置。 應用程式必須設計為支援應用程式設定。
- **受控應用程式** - 已開發用於整合 Intune App SDK 的應用程式。 這就是不需註冊的行動應用程式管理 ([MAM-WE](app-management.md#mobile-application-management-mam-basics))。 您也可以包裝應用程式以實作並支援 Intune App SDK。 如需此包裝應用程式的詳細資訊，請參閱[針對應用程式防護原則準備企業營運應用程式](../developer/apps-prepare-mobile-application-management.md)。

    > [!NOTE]
    > Intune 受控應用程式會在與 Intune 應用程式防護原則一起部署時，以 30 分鐘的間隔簽入 Intune 應用程式設定原則狀態。 如果未將 Intune 應用程式防護原則指派給使用者，則 Intune 應用程式設定原則簽入間隔會設為 720 分鐘。

## <a name="apps-that-support-app-configuration"></a>支援應用程式設定的應用程式

### <a name="managed-devices"></a>受管理的裝置
您可以針對支援應用程式設定的應用程式，使用應用程式設定原則。 若要在 Intune 中支援應用程式設定，則應用程式的編寫方式，必須支援使用由 OS 所定義的應用程式設定。 請諮詢您的應用程式廠商，以取得他們所支援的應用程式設定金鑰的詳細資料。

### <a name="managed-apps"></a>受管理的應用程式
將 [Intune App SDK](../developer/app-sdk.md) 併入應用程式，或在使用 [Intune App Wrapping Tool](../developer/apps-prepare-mobile-application-management.md) 開發應用程式之後包裝應用程式，就可以準備好企業營運應用程式。 Intune App SDK 會盡力將應用程式開發人員所需的程式碼變更數量減到最少。 如需詳細資訊，請參閱 [Intune App SDK 概觀](../developer/app-sdk.md)。 如需 Intune App SDK 與 Intune 應用程式包裝工具之間的比較，請參閱[準備應用程式保護原則的企業營運應用程式](../developer/apps-prepare-mobile-application-management.md#feature-comparison)。

選取 [受控應用程式]  作為 [裝置註冊類型]  具體上是指未在裝置管理中註冊之裝置上由 Intune 設定原則所設定的應用程式，而**受控裝置**適用於透過 MDM 通道部署的應用程式，因此由 Intune 管理。 請根據這些描述來選取適當的選擇。 

![裝置註冊類型](./media/app-configuration-policies-overview/device-enrollment-type.png)

> [!NOTE]
> 針對多重身分識別應用程式 (例如 Microsoft Outlook)，可以考慮使用者喜好設定。 例如，焦點收件匣會遵循使用者設定，而不會變更設定。 其他參數可讓您控制使用者是否可以變更設定。 如需詳細資訊，請參閱 [Deploying Outlook for iOS and Android app configuration settings](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune) (針對 iOS 和 Android 應用程式組態設定部署 Outlook)。

## <a name="validate-the-applied-app-configuration-policy"></a>驗證已套用的應用程式設定原則

您可以使用下列三種方法來驗證應用程式設定原則：

   1. 在裝置上可見。 目標應用程式是否展現出應用程式設定原則中所套用的行為？
   2. 透過診斷記錄 (請參閱下面的＜診斷記錄＞一節)。
   3. 在 Intune 入口網站中。 原則的 [監視]  區段可以提供相關的狀態：

      ![裝置安裝狀態的第一個螢幕擷取畫面](./media/app-configuration-policies-overview/device-install-status-1.png)

      ![裝置安裝狀態的第二個螢幕擷取畫面](./media/app-configuration-policies-overview/device-install-status-2.png)

      此外，在畫面左側的 [Intune]   -> [裝置]   -> [所有裝置]  下方，[應用程式設定]  選項會顯示所有指派的原則及其狀態：

      ![應用程式設定的螢幕擷取畫面](./media/app-configuration-policies-overview/app-configuration.png)

## <a name="diagnostic-logs"></a>診斷記錄

### <a name="ios-configuration-on-unmanaged-devices"></a>非受控裝置上的 iOS 設定

您可以在非受控裝置上，使用 [Intune 診斷記錄]  針對受控應用程式設定驗證 iOS 設定。

1. 如果尚未在裝置上安裝，請從 App Store 下載並安裝 **Intune Managed Browser**。 如需詳細資訊，請參閱[受 Microsoft Intune 保護的應用程式](apps-supported-intune-apps.md)。
2. 啟動 **Intune Managed Browser** 並從導覽列中選取 [關於]   > [intunehelp]  。
3. 按一下 [開始使用]  。
4. 按一下 [共用記錄]  。
5. 使用您選擇的電子郵件應用程式傳送記錄給您自己，方便您在自己的電腦上檢視。 
6. 使用您的文字檔檢視器檢閱 **IntuneMAMDiagnostics.txt** 檔案。
7. 搜尋 `ApplicationConfiguration`。 結果看起來像這樣：

    ``` JSON
        {
            (
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.BlockListURLs";
                    Value = "https://www.aol.com";
                },
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.bookmarks";
                    Value = "Outlook Web|https://outlook.office.com||Bing|https://www.bing.com";
                }
            );
        },
        {
            ApplicationConfiguration =             
            (
                {
                Name = IntuneMAMUPN;
                Value = "CMARScrubbedM:13c45c42712a47a1739577e5c92b5bc86c3b44fd9a27aeec3f32857f69ddef79cbb988a92f8241af6df8b3ced7d5ce06e2d23c33639ddc2ca8ad8d9947385f8a";
                },
                {
                Name = "com.microsoft.outlook.Mail.NotificationsEnabled";
                Value = false;
                }
            );
        }
    ```

您的應用程式設定詳細資料應與為您的租用戶所設定的應用程式設定原則相符。 

![目標應用程式設定](./media/app-configuration-policies-overview/targeted-app-configuration-3.png)

### <a name="ios-configuration-on-managed-devices"></a>受控裝置上的 iOS 設定

您可以在受控裝置上，使用 [Intune 診斷記錄]  針對受控應用程式設定驗證 iOS 設定。

1. 如果尚未在裝置上安裝，請從 App Store 下載並安裝 **Intune Managed Browser**。 如需詳細資訊，請參閱[受 Microsoft Intune 保護的應用程式](apps-supported-intune-apps.md)。
2. 啟動 **Intune Managed Browser** 並從導覽列中選取 [關於]   > [intunehelp]  。
3. 按一下 [開始使用]  。
4. 按一下 [共用記錄]  。
5. 使用您選擇的電子郵件應用程式傳送記錄給您自己，方便您在自己的電腦上檢視。 
6. 使用您的文字檔檢視器檢閱 **IntuneMAMDiagnostics.txt** 檔案。
7. 搜尋 `AppConfig`。 您的結果應該與您為租用戶所設定的應用程式設定原則相符。

### <a name="android-configuration-on-managed-devices"></a>受控裝置上的 Android 設定

您可以在受控裝置上，使用 [Intune 診斷記錄]  針對受控應用程式設定驗證 iOS 設定。

若要收集 Android 裝置的記錄，您或終端使用者必須透過 USB 連線 (或裝置上的**檔案總管**同等功能) 從裝置下載記錄。 步驟如下：

1. 使用 USB 纜線將 Android 裝置連接到您的電腦。
2. 在電腦上尋找有裝置名稱的目錄。 在該目錄中，尋找 `Android Device\Phone\Android\data\com.microsoft.windowsintune.companyportal`。
3. 在 `com.microsoft.windowsintune.companyportal` 資料夾中，開啟 [檔案] 資料夾並開啟 `OMADMLog_0`。
3. 搜尋 `AppConfigHelper` 以尋找應用程式設定相關訊息。 結果看起來將會類似下列的資料區塊畫面：

    `2019-06-17T20:09:29.1970000       INFO   AppConfigHelper     10888  02256  Returning app config JSON [{"ApplicationConfiguration":[{"Name":"com.microsoft.intune.mam.managedbrowser.BlockListURLs","Value":"https:\/\/www.aol.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.bookmarks","Value":"Outlook Web|https:\/\/outlook.office.com||Bing|https:\/\/www.bing.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.homepage","Value":"https:\/\/www.arstechnica.com"}]},{"ApplicationConfiguration":[{"Name":"IntuneMAMUPN","Value":"AdeleV@M365x935807.OnMicrosoft.com"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled","Value":"false"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled.UserChangeAllowed","Value":"false"}]}] for user User-875363642`
    
## <a name="graph-api-support-for-app-configuration"></a>應用程式設定的圖形 API 支援

您可以使用圖形 API 來完成應用程式設定工作。 如需詳細資料，請參閱 [Graph API Reference MAM Targeted Config](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create) (以圖形 API 參考 MAM 為目標的設定)。

## <a name="troubleshooting"></a>疑難排解

### <a name="using-logs-to-show-a-configuration-parameter"></a>使用記錄來顯示設定參數
當記錄顯示已確認要套用但似乎無法運作的設定參數時，應用程式開發人員在實作設定時可能發生了問題。 請先連絡該應用程式的開發人員或檢查其知識庫，您可能就不必撥打 Microsoft 支援電話。 如果在應用程式中處理設定的方式存在問題，則必須在該應用程式的未來更新版本中加以解決。

## <a name="next-steps"></a>後續步驟

### <a name="managed-devices"></a>受管理的裝置

- 了解如何在 iOS 裝置上使用應用程式設定。  請參閱[為受控 iOS 裝置新增應用程式設定原則](app-configuration-policies-use-ios.md)。
- 了解如何在 Android 裝置上使用應用程式設定。  請參閱[為受管理的 Android 裝置新增應用程式設定原則](app-configuration-policies-use-android.md)。

### <a name="managed-apps"></a>受管理的應用程式

- 了解如何在受管理的應用程式上使用應用程式設定。 請參閱[在不註冊裝置的情況下新增受管理應用程式的應用程式設定原則](app-configuration-policies-managed-app.md)。
