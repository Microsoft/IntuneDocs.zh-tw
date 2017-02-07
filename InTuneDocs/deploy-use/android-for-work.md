---
title: "關於 Android for Work | Microsoft Docs"
description: "使用 Intune 管理 Android for Work 可為使用 Android 裝置工作的使用者，提供額外的管理功能與隱私權。"
keywords: 
author: nathbarn
manager: angrobe
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aa0002d9-f5a0-466e-98ac-3970cb77e3a2
translationtype: Human Translation
ms.sourcegitcommit: d28902223352cefecb62b2226a2eef8775de0953
ms.openlocfilehash: 28994238d2874a0b6c64e188db04b09439d841bc


---

# <a name="manage-android-for-work-devices-with-intune"></a>使用 Intune 管理 Android for Work 裝置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Android for Work 是一組 Android 裝置功能及服務。 這些功能及服務可以為使用 Android 裝置工作的使用者，提供額外的管理功能與隱私權。 Intune 可協助您將應用程式及公司資源部署到 Android for Work 裝置，以確保工作及個人資訊各自分開。 部署成功之後，裝置存取的應用程式及只會提供給裝置上的 Android for Work 環境使用。

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

## <a name="supported-devices"></a>支援的裝置

因為許多管理功能必須依賴較新版 Android 作業系統的功能，所以 Android for Work 需要較新版的 Android 硬體。 目前只有執行 Android 5.0 Lollipop 及更新版本及支援工作設定檔的裝置支援 Android for Work。 對於不具 Android for Work 原生支援的裝置，仍可使用一般常用的 Android 管理功能。 深入了解 [Android for Work requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Android for Work 的需求)。

## <a name="onboarding"></a>入門訓練

註冊 Android for Work 裝置之前，必須先完成一些上架步驟。 下列步驟會在您的 Intune 租用戶與 Android for Work 應用程式散發及管理程序隨附的 Google Play for Work 之間建立連線。 深入了解[啟用 Android for Work 裝置的註冊](https://docs.microsoft.com/intune/deploy-use/set-up-android-for-work)。

## <a name="work-profile-management"></a>工作設定檔管理

當您使用 Intune 管理 Android for Work 裝置時，並非管理整部裝置。 管理功能只對註冊時所建立的工作設定檔有影響。 任何部署到使用 Intune 之裝置上的應用程式，都是工作設定檔的一部分。 工作設定檔中的應用程式圖示會顯示為橙色公事包。 這在區分裝置上的個人應用程式與公司應用程式。 裝置上 Android for Work 以外的 Android 應用程式及資料仍屬於個人範疇，由使用者自行控制。 使用者可以選擇任何應用程式安裝到裝置的個人部分；系統管理員則能管理及監視屬於工作設定檔的各項動作。

## <a name="app-publishing-and-distribution"></a>發行與散發應用程式

Google Play for Work 服務屬於應用程式散發及管理的一部分。 工作設定檔中所有部署到 Android for Work 裝置的應用程式皆來自 Play for Work。 若要管理及部署 Play Store 中的應用程式，必須以 Intune 系統管理員登入 Play for Work 網站，然後為您的 Intune 租用戶核准應用程式。 這些應用程式會同步到 Intune 主控台，以便於 Intune 進行部署及管理。 您組織所開發的企業營運 (LOB) 應用程式，必須使用 Google 的 Android 應用程式發行主控台，才能發行到 Play for Work。 企業營運應用程式必須在 Android 應用程式發行主控台中設定，以限制對您組織的存取。

應用程式安裝時不會與使用者互動，而且也不會要求使用者允許**來自未知來源的安裝**。 若要瀏覽及安裝選擇性或可用的應用程式，使用者可以瀏覽其裝置上的 Play Store。 深入了解[如何使用 Intune 將應用程式部署至 Android for Work 裝置](https://docs.microsoft.com/intune/deploy-use/android-for-work-apps)。

## <a name="app-configuration"></a>應用程式組態

Android for Work 提供部署應用程式設定值到支援這些值之應用程式所需的基礎結構。 為工作應用程式指定設定值，可確保使用者第一次啟動應用程式時，就是使用正確設定的值。 應用程式設定支援需要應用程式開發人員在建立其 Android 應用程式時，特別將其設定成支援受管理的值。 若要執行此作業，可以使用 Intune 指定及套用這些組態設定。 深入了解 [Android for Work 應用程式的組態設定](afw-app-configuration-policy.md)。

## <a name="email-configuration"></a>電子郵件組態

Android for Work 不提供預設電子郵件應用程式，也不會像 iOS 般地提供原生的電子郵件設定檔物件。 但是電子郵件組態可藉由將應用程式組態設定套用到支援這些設定的應用程式來加以設定。 在 Play Store 中，Gmail 及 Nine Work 這兩個 Exchange ActiveSync (EAS) 用戶端應用程式支援 Android for Work 應用程式組態。

Intune 提供 Gmail 及 Nine Work 應用程式的組態範本。 其他支援應用程式組態設定檔的電子郵件應用程式可以透過行動裝置應用程式設定原則加以設定。

若是對 Android for Work 裝置使用 EAS 條件式存取，必須使用 Gmail 或 Nine Work 電子郵件應用程式。 此外也支援 Android 版的 Microsoft Outlook 應用程式，或其他任何經由 ADAL 使用新式驗證的電子郵件應用程式。 深入了解[公司電子郵件的電子郵件設定檔](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)。

## <a name="mobile-app-management-policies"></a>行動應用程式管理原則

工作設定檔與個人設定檔可全面支援行動裝置應用程式管理 (MAM) 中所啟用套用到應用程式的限制原則。 您可以在 Android 應用程式發行主控台 (https://play.google.com/apps/publish) 中發行企業營運應用程式。 此主控台提供可以讓您將應用程式設為不對組織公開的選項。 深入了解[相容性原則設定](afw-compliance-policy-settings-in-microsoft-intune.md)。 如需詳細資訊，請參閱[行動裝置應用程式管理原則](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)。

## <a name="vpn-profiles"></a>VPN 設定檔

VPN 支援類似於 Android VPN 設定檔， 會提供相同的 VPN 提供者與基本設定選項。 這兩者的主要差異在於：

1.  **工作設定檔範圍內的 VPN** - VPN 連線的範圍僅限於部署到工作設定檔的應用程式。 只有受 Android for Work 管理的應用程式可以使用此 VPN 連線。 裝置上的個人應用程式無法使用受管理的 VPN 連線。

2.  **應用程式專用的 VPN** - 若 VPN 提供者支援應用程式專用的 VPN 組態，並提供功能讓您透過 Android for Work 應用程式組態設定檔設定個別應用程式的 VPN，就能在 Intune 中設定應用程式專用的 VPN。 您可以連絡 VPN 提供者，確定其是否支援此功能。 深入了解 [VPN 連線設定檔](vpn-connections-in-microsoft-intune.md)。

## <a name="certificate-profiles"></a>憑證設定檔

傳統 Android 管理同樣能使用的憑證設定檔組態選項，也能在 Android for Work 裝置上使用。 Android for Work 提供增強的憑證管理 API。 增強的憑證管理提供下列功能：

1.  確保使用者的憑證部署採用無訊息模式而且無縫執行。

2.  確保當裝置從 Intune 撤回並移除了設定檔之後，會完全移除部署的憑證。

3.  提供經過改良的傳訊功能，可以通知使用者其 IT 部門已透過管理服務部署及設定憑證。

深入了解[憑證設定檔](secure-resource-access-with-certificate-profiles.md)。

## <a name="wi-fi-profiles"></a>Wi-Fi 設定檔

確保當裝置從 Intune 撤回並移除了工作設定檔之後，會移除 Android for Work 管理的 Wi-Fi 設定檔。 深入了解 [Wi-Fi 設定檔](wi-fi-connections-in-microsoft-intune.md)。

## <a name="next-steps"></a>後續步驟
[啟用 Android for Work 裝置的註冊](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-android-for-work)
[如何使用 Intune 將應用程式部署至 Android for Work 裝置](https://docs.microsoft.com/en-us/intune/deploy-use/android-for-work-apps)



<!--HONumber=Jan17_HO5-->


