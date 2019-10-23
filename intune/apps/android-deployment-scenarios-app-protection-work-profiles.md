---
title: Microsoft Intune 中的應用程式保護原則與工作設定檔 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中決定針對個人或 BYOD Android 企業裝置使用應用程式保護原則或工作設定檔時，了解兩者的差異及優缺點。 比較無註冊應用程式防護原則 (APP-WE) 和 Android 企業工作設定檔之間的差異，以及所提供的功能。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a2c71e04cf842fda7b16fb8ad4a05668ccbfaa84
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507594"
---
# <a name="application-protection-policies-and-work-profiles-on-android-enterprise-devices-in-intune"></a>Intune 中 Android 企業裝置上的應用程式保護原則與工作設定檔

在許多組織中，系統管理員皆須面對保護不同裝置上的資源與資料的挑戰。 其中一個挑戰，便是保護具備個人 Android 企業裝置，也稱為攜帶您自己的裝置 (BYOD) 之使用者的資源。 Microsoft Intune 針對攜帶您自己的裝置 (BYOD) 支援兩個 Android 部署案例：

- 無註冊應用程式防護原則 (APP-WE)
- Android 企業工作設定檔

APP-WE 和 Android 工作設定檔部署案例皆包含下列對 BYOD 環境極為重要的關鍵功能：

1. **保護及隔離受組織管理的資料**：這兩個解決方案皆會針對受組織管理的資料強制持行資料外洩防護 (DLP) 來保護組織資料。 這些保護會防止受保護資料意外外洩，例如使用者不小心將它共用到個人應用程式或帳戶。 它們也能確保存取該資料的裝置處於健康良好且未被入侵的狀態。

2. **使用者隱私權**：APP-WE 和 Android 企業工作設定檔會將裝置上的使用者資料，與由行動裝置管理 (MDM) 系統管理員所管理的資料隔離開來。 在這兩個案例中，IT 系統管理員都會強制執行原則，例如針對受組織管理的應用程式或身分識別強制僅限 PIN 的驗證。 IT 系統管理員並無法讀取、存取或清除使用者所有或其所控制的資料。

針對 BYOD 部署選擇 APP-WE 或 Android 企業工作設定檔，應取決於您的要求和商務需求。 此文章的目標是提供指導方針以協助您做出決定。

## <a name="about-intune-app-protection-policies"></a>關於 Intune 應用程式保護原則

Intune 應用程式保護原則 (APP) 是以使用者為目標的資料保護原則。 該原則會在應用程式層級上套用資料外洩防護。 Intune APP 會要求應用程式開發人員在其所建立的應用程式上啟用 APP 功能。

個別的 Android 應用程式會以幾種方式啟用 APP：

1. **原生整合到 Microsoft 第一方應用程式**：適用於 Android 的 Microsoft Office 應用程式，以及數個其他 Microsoft 應用程式已內建 Intune APP。 這些 Office 應用程式 (例如 Word、OneDrive、Outlook 等) 並不需要進行額外自訂來套用原則。 使用者可以直接從 Google Play 商店安裝這些應用程式。

2. **由開發人員使用 Intune SDK 整合到應用程式組建**：應用程式開發人員可以將 Intune SDK 整合到其原始程式碼中，並重新編譯其應用程式以支援 Intune APP 原則功能。

3. **使用 Intune App Wrapping Tool 進行包裝**：某些客戶會在未存取原始程式碼的情況下編譯 Android 應用程式 (.APK 檔案)。 若沒有原始程式碼，開發人員便無法與 Intune SDK 整合。 若沒有 SDK，他們便無法針對 APP 原則啟用其應用程式。 開發人員必須修改或重新撰寫應用程式的程式碼，以支援 APP 原則。

    為了協助達成這點，Intune 針對現有 Android 應用程式 (APK) 提供 **App Wrapping Tool** 工具，並建立能辨識 APP 原則的應用程式。

    如需此工具的詳細資訊，請參閱[針對應用程式防護原則準備企業營運應用程式](../developer/apps-prepare-mobile-application-management.md)。

若要查看已啟用 APP 的應用程式清單，請參閱[具有一組豐富行動應用程式保護原則的受控應用程式](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。

## <a name="deployment-scenarios"></a>部署案例

本節會描述 APP-WE 和 Android 企業工作設定檔部署案例的重要特性。

### <a name="app-we"></a>APP-WE

APP-WE (無註冊應用程式防護原則) 部署會在應用程式 (而非裝置) 上定義原則。 在此案例中，裝置通常不是由 MDM 授權單位 (例如 Intune) 所註冊或管理。 為了保護應用程式及組織資料的存取權，系統管理員會使用可由 APP 管理的應用程式，並將資料保護原則套用到這些應用程式上。

本功能適用於：

- Android 4.4 及更新版本

> [!TIP]
> 如需詳細資訊，請參閱[什麼是應用程式保護原則？](app-protection-policy.md)。

APP-WE 案例適用於想在其裝置上保持較少組織使用量，且不想要註冊 MDM 的使用者。 身為系統管理員，您仍然需要保護您的資料。 這些裝置並未受控。 因此常見的 MDM 工作和功能 (例如 WiFi、裝置 VPN 及憑證管理) 並非此部署案例的一部分。

### <a name="android-enterprise-work-profiles"></a>Android 企業工作設定檔

工作設定檔是核心 Android 企業部署案例，也是唯一以 BYOD 使用情況為目標的案例。 工作設定檔是在 Android OS 層級建立的個別分割區，並可由 Intune 管理。

本功能適用於：

- 具有 Google 行動服務的 Android 5.0 及更新版本裝置

工作設定檔包含下列功能：

- **傳統 MDM 功能**：關鍵的 MDM 功能 (例如使用受控的 Google Play 進行應用程式生命週期管理) 皆可用於任何 Android 企業案例中。 受控的 Google Play 能提供豐富的體驗，以在沒有任何使用者介入的情況下安裝及更新應用程式。 IT 也可以將應用程式組態設定推送到組織應用程式。 它也不需要使用者允許從不明來源進行安裝。 其他常見的 MDM 活動 (例如部署憑證、設定 WiFi/VPN 及設定密碼) 皆可搭配工作設定檔使用。

- **工作設定檔界線上的 DLP**：和 APP-WE 相同，IT 也可以強制執行資料保護原則。 使用工作設定檔時，DLP 原則會在工作設定檔層級 (而非應用程式層級) 上強制執行。 例如，複製/貼上保護會由套用至應用程式的 APP 設定來強制執行，或是由工作設定檔強制執行。 當應用程式被部署到工作設定檔時，系統管理員可以在 APP 層級關閉此原則，來暫停針對該工作設定檔的複製/貼上保護。

## <a name="tips-to-optimize-the-work-profile-experience"></a>將工作設定檔體驗最佳化的提示

### <a name="when-to-use-app-within-work-profiles"></a>在工作設定檔內使用 APP 的時機

Intune APP 和工作設定檔為互補的技術，並可以一起或分開使用。 就架構而言，這兩個解決方案會在不同的層級上強制執行原則：APP 為個別應用程式層級，工作設定檔則為設定檔層級。 將受 APP 原則管理的應用程式部署到工作設定檔中的應用程式，是個有效且被支援的案例。 使用 APP、工作設定檔，或是這兩者的組合，會取決於您的 DLP 需求。

您可以在其中一個設定檔無法滿足您組織的資料保護需求時，透過工作設定檔和 APP 互補的特性取得額外的涵蓋範圍。 例如，工作設定檔沒有提供原生控制項來限制應用程式儲存到未受信任的雲端儲存空間。 APP 則包含此功能。 您也可能認為單獨由工作設定檔所提供的 DLP 已經足夠，並選擇不使用 APP。 或者您可能需要由這兩者的組合所提供的保護。

### <a name="suppress-app-policy-for-work-profiles"></a>針對工作設定檔隱藏 APP 原則

您可能會需要支援具備多個裝置 (處於 APP-WE 案例的非受控裝置，以及具有工作設定檔的受控裝置) 的個別使用者。

例如，您要求使用者在開啟公司應用程式時輸入 PIN。 根據裝置的不同，PIN 功能可能會由 APP 或工作設定檔負責處理。 針對 APP-WE 裝置，PIN 啟動行為是由 APP 強制執行。 針對工作設定檔裝置，您可以使用由 OS 所強制執行的裝置或工作設定檔 PIN。 若要達成此案例，請設定 APP 設定，來使它們「不會在」  應用程式被部署到工作設定檔時套用。 如果您不這麼設定，裝置會提示使用者輸入 PIN，然後系統在 APP 層時又會再一次提示使用者輸入 PIN。

### <a name="control-multi-identity-behavior-in-work-profiles"></a>在工作設定檔中控制多重身分識別行為

Office 應用程式 (例如 Outlook 和 OneDrive) 具有「多重身分識別」行為。 在應用程式的其中一個執行個體中，使用者可以新增針對多個不同帳戶或雲端儲存空間的連線。 在應用程式內，從這些位置所擷取的資料可能會被分散或合併。 此外，使用者可以在個人身分識別 (user@outlook.com) 和組織身分識別 (user@contoso.com) 之間進行環境切換。

使用工作設定檔時，您應該停用此多重身分識別行為。 當您停用它時，工作設定檔中應用程式的徽章執行個體只能由組織身分識別來設定。 請使用 [允許的帳戶] 應用程式組態設定來支援 Office Android 應用程式。

如需詳細資訊，請參閱[針對 iOS 和 Android 應用程式組態設定部署 Outlook](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune) \(機器翻譯\)。

## <a name="when-to-use-intune-app"></a>使用 Intune APP 的時機

在數個企業行動力案例中，使用 Intune APP 是最佳建議。

### <a name="older-devices-running-android-44-51-are-being-used"></a>使用執行 Android 4.4-5.1 的較舊裝置

正式來說，具有 Google 行動服務的所有 Android 5.0 或更新版本裝置都能支援工作設定檔，並能夠以該方式來管理。 不過，某些來自部分 OEM 的 Android 5.0 和 5.1 裝置並不支援工作設定檔。

如果使用不支援工作設定檔的版本，若要針對裝置上的組織資料使用 DLP，您必須使用 Intune APP 功能。

### <a name="no-mdm-no-enrollment-google-services-are-unavailable"></a>不要 MDM、不要註冊、無法使用 Google 服務

基於不同的原因，某些客戶並不願意接受任何形式的裝置管理 (包括工作設定檔管理)：

- 法律和責任原因
- 為確保使用者體驗的一致性
- Android 裝置環境具有高度異質的特性
- 沒有連線到 Google 服務的能力，這是進行工作設定檔管理的先決條件。

例如，客戶若位於中國，或是具有位於中國的使用者，將無法使用 Android 裝置管理，因為 Google 服務在該地區已被封鎖。 在此情況下，請使用 Intune APP 來取得 DLP 功能。

## <a name="summary"></a>[摘要]

透過使用 Intune，您的 Android BYOD 計畫將能使用 APP-WE 和 Android 企業工作設定檔。 選擇使用 APP-WE 或工作設定檔，將取決於您的商務和使用情況需求。 整體來說，如果您在受控裝置上需要進行 MDM 活動 (例如憑證部署、應用程式推送等)，請使用工作設定檔。 如果您不想要或無法管理裝置，且僅使用 Intune 已啟用 APP 的應用程式，請使用 APP-WE。

## <a name="next-steps"></a>後續步驟
[開始使用應用程式保護原則](app-protection-policy.md)，或是[註冊您的裝置](../enrollment/android-enroll.md)。
