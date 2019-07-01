---
title: 在 Microsoft Intune 中管理 Android Enterprise 工作設定檔裝置
titleSuffix: ''
description: 使用 Microsoft Intune 管理 Android Enterprise 工作設定檔裝置可為使用個人 Android 裝置工作的使用者提供額外管理功能與隱私權。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2cc3c960-1fdd-47ca-a693-420d47b403de
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6f59ff42f7707ace92442bf37ddac9679e36448f
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "67045879"
---
# <a name="manage-android-work-profile-devices-with-intune"></a>使用 Intune 管理 Android 工作設定檔裝置

Android Enterprise 提供一組註冊選項，為使用者提供最新且最安全的功能。 使用 Android Enterprise 工作設定檔註冊，可允許一組功能和服務，將個人應用程式與資料和公司應用程式與資料分隔開來。 使用者以 Android 裝置進行工作時，它也提供額外的管理功能與隱私控管。 

## <a name="supported-devices"></a>支援的裝置

Android Enterprise 管理功能仰賴一些新版 Android 作業系統的功能。 對於不支援 Android Enterprise 的裝置來說，仍可使用傳統 Android 管理功能。 如需詳細資訊，請參閱 [Android Enterprise 需求](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)。

## <a name="onboarding"></a>入門訓練

註冊 Android Enterprise 工作設定檔裝置之前，必須先完成一些上線步驟。 下列步驟可建立 Intune 租用戶與受控 Google Play 之間的連線。 如需詳細資訊，請參閱[啟用 Android Enterprise 工作設定檔裝置的註冊](android-work-profile-enroll.md)。

## <a name="work-profile-management"></a>工作設定檔管理

當您使用 Intune 來管理 Android Enterprise 工作設定檔裝置時，並非管理整部裝置。 管理功能只對註冊期間建立於裝置上的公司設定檔有影響。 任何部署到具備 Intune 之裝置的應用程式，都會安裝在公司設定檔中。 工作設定檔中的應用程式圖示與裝置上的個人應用程式不同。 裝置上 Android 企業部分以外的所有 Android 應用程式及資料仍屬於個人範疇，由終端使用者自行控制。 使用者可以將其選擇的任何應用程式安裝到裝置的個人部分。 系統管理員可以管理及監視範圍設定為工作設定檔的應用程式和動作。

Intune 提供一系列您可以在 Android 工作設定檔裝置上設定的內建一般設定。 如需詳細資訊，請參閱 [Android 工作設定檔裝置原則設定](compliance-policy-create-android-for-work.md)。

## <a name="app-publishing-and-distribution"></a>發行與散發應用程式

受控 Google Play 服務是 Android Enterprise 應用程式發佈及管理中不可或缺的一部分。 在公司設定檔中，部署到 Android Enterprise 工作設定檔裝置的所有應用程式，皆來自於受控 Google Play 服務。 若要管理和部署 Play Store 店中的應用程式，您可使用貴公司的系統管理員認證登入 Google Play 網站以進行 Google 管理。 您可以核准用來進行 Android Enterprise 部署的應用程式，使其出現在裝置的工作設定檔中。 這些應用程式接著會同步到 Intune 主控台，然後就能使用 Intune 部署及管理它們。 您組織所開發的企業營運 (LOB) 應用程式，必須使用 Google 的 Android 應用程式發佈主控台，才能發佈到受控 Google Play。 企業營運應用程式必須在 Android 應用程式發行主控台中設定，以限制對您組織的存取。

應用程式可以在不與使用者互動且也不要求使用者允許**來自不明來源的安裝**情況下進行安裝。 若要瀏覽及安裝選擇性或可用的應用程式，使用者可以瀏覽其裝置上的 Play for Work 商店。 如需詳細資訊，請參閱[使用 Intune 將應用程式指派給 Android Enterprise 工作設定檔裝置](apps-add-android-for-work.md)。

## <a name="app-configuration"></a>應用程式組態

Android Enterprise 提供部署應用程式設定值到支援這些值之應用程式所需的基礎結構。 為工作應用程式指定設定值，可確保使用者第一次啟動應用程式時，就是使用正確設定的值。 應用程式設定支援需要應用程式開發人員在建立其 Android 應用程式時，特別將其設定成支援受管理的值。 若要執行此作業，可以使用 Intune 指定及套用這些組態設定。 如需詳細資訊，請參閱[為受控 Android 裝置新增應用程式設定原則](app-configuration-policies-use-android.md)。

## <a name="email-configuration"></a>電子郵件組態

Android Enterprise 不提供預設電子郵件應用程式，也不會像 iOS 般地提供原生的電子郵件設定檔物件。 但是電子郵件組態可藉由將應用程式組態設定套用到支援這些設定的應用程式來加以設定。 在 Play Store 中，Gmail 及 Nine Work 這兩個 Exchange ActiveSync (EAS) 用戶端應用程式支援使用 Android Enterprise 應用程式設定進行設定。

Intune 會在將 Gmail 及 Nine Work 應用程式當成工作應用程式管理時，提供它們適用的組態範本。 其他支援應用程式組態設定檔的電子郵件應用程式可以透過行動裝置應用程式設定原則加以設定。

如果您針對 Android Enterprise 工作設定檔裝置使用 Exchange ActiveSync 條件式存取，請考慮使用 Gmail 或 Nine Work 電子郵件應用程式。 此外也支援 Android 版的 Microsoft Outlook 應用程式，或其他任何經由 ADAL 使用新式驗證的電子郵件應用程式。 如需詳細資訊，請參閱[如何在 Microsoft Intune 中設定電子郵件設定](email-settings-configure.md)。

## <a name="app-protection-policies"></a>應用程式防護原則

在工作設定檔和個人設定檔中完全支援已套用的應用程式保護原則。 您可以在 Android 應用程式發行主控台 (https://play.google.com/apps/publish ) 中發行企業營運應用程式。 此主控台提供可以讓您將應用程式設為不對組織公開的選項。 如需詳細資訊，請參閱[在 Intune 中為 Android Enterprise 工作設定檔裝置新增裝置合規性政策](compliance-policy-create-android-for-work.md)。 如需應用程式防護原則的一般資訊，請參閱[什麼是應用程式防護原則？](app-protection-policy.md)

## <a name="vpn-profiles"></a>VPN 設定檔

VPN 支援類似於 Android VPN 設定檔， Android Enterprise 管理的可用相同 VPN 提供者與基本設定選項有兩個不同之處：

-  **設定檔範圍內的 VPN** – VPN 連線受限在只有部署到公司設定檔的應用程式。 只有受 Android Enterprise 管理的應用程式才可使用此 VPN 連線。 裝置上的個人應用程式無法使用受管理的 VPN 連線。 如需詳細資訊，請參閱 [Android Enterprise VPN 設定](vpn-settings-android.md#android-enterprise-vpn-settings)。

-  **應用程式專屬 VPN** – 若 VPN 提供者支援下列項目，就能在 Intune 中設定應用程式特定的 VPN：
    - 應用程式特定 VPN 的組態
    - 透過 Android Enterprise 應用程式組態設定檔來設定個別應用程式 VPN 的功能。
    如需詳細資訊，請參閱[使用 Microsoft Intune 自訂設定檔來建立 Android 裝置的個別應用程式 VPN 設定檔](android-pulse-secure-per-app-vpn.md)。

## <a name="certificate-profiles"></a>憑證設定檔

Android 管理可使用的相同憑證設定檔設定選項，在 Android Enterprise 工作設定檔裝置上也可使用。 Android Enterprise 提供增強的憑證管理 API。 增強的憑證管理提供下列功能：

-  確保使用者的憑證部署採用無訊息模式而且無縫執行。
-  確保當裝置從 Intune 淘汰並移除工作設定檔之後，會移除部署的憑證。
-  提供經過改良的傳訊功能，可以通知使用者其 IT 部門已透過管理服務部署及設定憑證。

如需詳細資訊，請參閱[在 Microsoft Intune 中設定裝置的憑證設定檔](certificates-configure.md)。

## <a name="wi-fi-profiles"></a>Wi-Fi 設定檔

當裝置從 Intune 淘汰並刪除公司設定檔之後，會移除 Android Enterprise 所管理的 Wi-Fi 設定檔。 如需詳細資訊，請參閱[如何在 Microsoft Intune 中設定 Wi-Fi 設定](wi-fi-settings-configure.md)。

## <a name="next-steps"></a>後續步驟
- [註冊 Android 裝置](android-enroll.md)
- [使用 Intune 將應用程式指派給 Android Enterprise 工作設定檔裝置](apps-add-android-for-work.md)
