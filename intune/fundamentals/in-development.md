---
title: 開發中 - Microsoft Intune
titleSuffix: ''
description: 正在開發的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04b284a62076122cec70b6b455151a0377470521
ms.sourcegitcommit: 16a9109b4028589c17695d41271ca4fee8b1d697
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74540727"
---
# <a name="in-development-for-microsoft-intune---december-2019"></a>Microsoft Intune 正在開發的項目 - 2019 年 12 月

為了協助您整備及規劃，此頁面會列出正在開發，但尚未發行的 Intune UI 更新及功能。 除了此頁面上的資訊：

- 若我們預期您將需要在變更前先行採取動作，我們會在 Office 訊息中心發佈輔助性貼文。
- 當功能進入生產環境時，不論是預覽或正式推出，功能描述都會從這個頁面移至[新](whats-new.md)功能。
- 此頁面和[新增功能](whats-new.md)頁面會定期更新。 請回來查看其他更新。
- 請參閱 [Microsoft 365 藍圖](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)以取得策略性交付與時間表。

> [!NOTE]
> 此頁面會反映我們在未來版本中目前對 Intune 功能的期望。 日期和個別功能可能會變更。 此頁面不會描述開發中的所有功能。

**RSS 摘要**：將下列 URL 複製並貼上至您的摘要讀取器中，以了解此頁面何時更新：`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>應用程式管理

### <a name="ios-user-licensed-vpp-apps---5619268-idready---"></a>iOS 使用者授權的 VPP 應用程式<!-- 5619268 idready -->
對於使用者註冊 iOS 裝置，使用者將不會再看到部署為 [可用] 的裝置授權 VPP 應用程式。 不過，終端使用者將會繼續查看公司入口網站內所有使用者授權的 VPP 應用程式。 如需與 VPP 應用程式相關的詳細資訊，請參閱[如何使用 Microsoft Intune 管理透過 Apple 大量採購方案購買的 iOS 和 macOS 應用程式](~/apps/vpp-apps-ios.md)。

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745-idready---"></a>從記憶體加密的 macOS 裝置取出個人修復金鑰<!-- 4851745 idready -->
使用者將能夠使用 iOS 公司入口網站應用程式來取出其個人修復金鑰（FileVault 金鑰）。 具有個人修復金鑰的裝置必須向 Intune 註冊，並透過 Intune 以 FileVault 加密。 使用 iOS 公司入口網站應用程式，使用者可以開啟 Safari web view 並取出其個人的修復金鑰。 在 Intune 中，選取 **裝置** > 已*加密且已註冊的 MacOS 裝置* > **取得修復金鑰**。 如需 FileVault 的詳細資訊，請參閱[FileVault encryption For macOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos)。

### <a name="microsoft-app-icons-update--4677605--"></a>Microsoft 應用程式圖示更新<!--4677605-->
應用程式保護原則和應用程式設定原則的應用程式目標窗格中，用於 Microsoft 應用程式的圖示將會更新。

### <a name="smime-support-for-microsoft-outlook-mobile---2669398----"></a>Microsoft Outlook Mobile 的 S/MIME 支援<!-- 2669398  -->
Intune 將支援提供可與 iOS 和 Android 上的 Outlook Mobile 搭配使用的 S/MIME 簽署和加密憑證。 如需相關資訊，請參閱[iOS 裝置的電子郵件設定](~/configuration/email-settings-ios.md)和[Android 裝置的電子郵件設定](~/configuration/email-settings-android.md)。

### <a name="custom-settings-support-for-macos-applications---4736278----"></a>MacOS 應用程式的自訂設定支援<!-- 4736278  -->
Intune 將支援自訂設定，可讓您將特定的索引鍵和值新增至現有的喜好設定屬性清單（. plist）檔案，以設定 macOS 應用程式和裝置。 並非所有應用程式都支援受控喜好設定，而在某些情況下，只能管理特定的設定。 這些設定只會透過裝置通道進行部署。 您應該只上傳以裝置通道設定為目標的屬性清單檔案或 .xml 檔案。

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>在 Windows 上顯示公司入口網站應用程式的通知<!-- 1808082  -->
我們會更新 Windows 裝置上的公司入口網站應用程式，以向使用者顯示快顯通知，即使應用程式關閉也是一樣。 只有在安裝狀態為 [已完成] 或 [失敗] 時，更新才會顯示可用應用程式的通知。 公司入口網站應用程式不會顯示必要應用程式的通知。

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>顯示公司入口網站應用程式的安裝狀態訊息<!-- 2514416  -->
公司入口網站應用程式會向終端使用者顯示額外的應用程式安裝狀態訊息。 下列條件將適用于新的 Win32 相依性功能：
- 應用程式無法啟動。 不符合系統管理員所定義的相依性。

### <a name="configure-app-notification-content-for-organization-accounts---2576686---"></a>設定組織帳戶的代理程式更新內容<!-- 2576686 -->
Android 和 iOS 裝置上的 Intune 應用程式可讓您控制組織帳戶的代理程式更新內容。 這項功能將需要應用程式的支援，而且可能無法供所有啟用應用程式的應用程式使用。 如需有關應用程式的詳細資訊，請參閱[什麼是應用程式保護原則？](../apps/app-protection-policy.md)

<!-- ***********************************************-->
## <a name="device-configuration"></a>裝置設定

### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998-idready---"></a>禁止使用者在 Android Enterprise 裝置擁有者裝置上的受控金鑰儲存區中設定憑證認證<!-- 3311998 idready -->
在 Android Enterprise 裝置擁有者裝置上，將會有新的設定，可封鎖使用者在受控金鑰存放區中設定其憑證認證（**裝置**設定 > **配置**檔 > **建立設定檔** > **Android Enterprise** for platform >**裝置擁有者，僅 >** 配置檔案類型 >**使用者 + 帳戶**）的裝置限制。

若要查看目前的設定，請前往[使用 Intune 允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。

適用於：
- Android Enterprise 裝置擁有者，包括專用且完全受控的裝置

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686-idready---"></a>適用于 macOS 裝置的有線網路裝置設定設定檔<!-- 3508686 idready -->
在 macOS 裝置上，未來的更新將會包含新的裝置設定設定檔，其會設定有線網路（**裝置**設定 > **配置**檔 > 為平臺 >**有線網路**配置檔案類型）**建立設定檔** > **macOS** 。 使用此功能來建立 802.1 x 設定檔以管理有線網路，並將這些有線網路部署至您的 macOS 裝置。

適用於：
- macOS

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>將自動 proxy 設定新增至 Android Enterprise 工作設定檔的 Wi-fi 設定檔<!-- 4490822 idready -->
在 Android Enterprise 工作設定檔裝置上，您可以建立 Wi-fi 設定檔。 當您選擇 Wi-fi 企業類型時，您也可以輸入在 Wi-fi 網路上使用的可延伸驗證通訊協定（EAP）類型。

在未來的更新中，當您選擇企業類型時，您將能夠輸入自動 proxy 設定，包括 proxy 伺服器 URL，例如 `proxy.contoso.com`。

若要查看您可以設定的目前 Wi-fi 設定，請前往 Microsoft Intune 中的 [為[執行 Android 企業和 android kiosk 的裝置新增 wi-fi 設定](../configuration/wi-fi-settings-android-enterprise.md)]。

適用於：
- Android Enterprise 工作設定檔

### <a name="enable-network-access-control-nac-with-cisco-anyconnect-vpn-on-ios-devices---4860111-idready---"></a>在 iOS 裝置上使用 Cisco AnyConnect VPN 啟用網路存取控制（NAC）<!-- 4860111 idready -->
在 iOS 裝置上，您可以建立 VPN 設定檔，並使用不同的連線類型，包括 Cisco AnyConnect （**裝置**設定 > **設定檔** > **為平臺**> **VPN** **建立 > 配置**檔案類型 > **Cisco AnyConnect** for connection type）。 

在未來的更新中，您將能夠啟用具有 Cisco AnyConnect 的網路存取控制（NAC）。 若要使用此功能：

1. 在[Cisco Identity Services 引擎系統管理員指南](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)中，使用將**MICROSOFT INTUNE 設定為 MDM 伺服器**中的步驟，在 Azure 中設定 Cisco IDENTITY Services 引擎（ISE）。
2. 在 Intune 裝置設定檔中，選取 [**啟用網路存取控制（NAC）** ] 設定。

若要查看所有可用的 VPN 設定，請移至[在 iOS 裝置上設定 VPN 設定](../configuration/vpn-settings-ios.md)。

適用於：
- iOS

### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578-idready---"></a>已在您的 iOS、iPadOS 和 macOS 裝置上更新應用程式和網站的單一登入體驗<!-- 4999578 idready -->
Intune 正在為 iOS、iPadOS 和 macOS 裝置新增更多單一登入設定。 目前，您可以在 Intune 中設定認證 SSO 應用程式延伸模組和 Apple 內建 Kerberos 延伸模組。 在未來的更新中，您將能夠設定由貴組織或由您的身分識別提供者所撰寫的重新導向 SSO 應用程式延伸模組。 

使用這些設定，針對使用新式驗證方法（例如 OAuth 和 SAML2）的應用程式和網站，設定順暢的單一登入體驗。 

若要查看您可以設定的 SSO 應用程式延伸模組設定，請移至[macOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension)上的 [IOS 和 sso] 上的 [ [sso](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) ]。

適用於：
- iOS/iPadOS
- macOS

### <a name="require-use-of-approved-keyboards-on-android--4761794-idready---"></a>需要在 Android 上使用已核准的鍵盤<!--4761794 IDready -->
您可以指定可在受控 Android 應用程式中使用的已核准鍵盤清單。 在受管理的應用程式中，系統會提示使用者切換到已安裝在其裝置上的其中一個已核准鍵盤，或視需要將其導向至 Google Play 商店以下載和設定其中一個已核准的鍵盤。 使用者只能在受管理的應用程式中編輯文字欄位（如果其現用鍵盤是其中一個已核准的鍵盤）。

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices---3246388----"></a>在 Windows 10 和更新版本的裝置上搭配使用 PKCS 憑證與 Wi-fi 設定檔<!-- 3246388  -->
目前，您可以使用 SCEP 憑證來驗證 Windows Wi-fi 設定檔（**裝置**設定 > **設定檔** > **建立設定檔** > **Windows 10 和更新版本**（適用于平臺 > 的**wi-fi）** 配置檔案類型 > **Enterprise** > **EAP 類型**）。 您將可以搭配 Windows Wi-fi 設定檔使用 PKCS 憑證。 這項功能可讓使用者使用您租使用者中新的或現有的 PKCS 憑證設定檔來驗證 Wi-fi 設定檔。 

如需有關 Wi-fi 設定檔的詳細資訊，請參閱[在 Intune 中新增適用于 Windows 10 和更新版本裝置的 wi-fi 設定](../configuration/wi-fi-settings-windows.md)。

適用於：
- Windows 10 及更新版本

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824----"></a>在 iOS 裝置上建立電子郵件裝置設定檔時的新 ExchangeActiveSync 設定<!-- 4892824  --> 
在 iOS/iPadOS 裝置上，您可以在裝置設定檔中設定電子郵件連線能力（**裝置**設定 > **配置**檔 > 為平臺 >**電子郵件** **建立設定檔** > **iOS/iPadOS**適用于配置檔案類型）。 

將會提供新的 ExchangeActiveSync 設定，包括：
- 選擇要同步（或封鎖同步處理）的服務，例如電子郵件、行事曆和連絡人。
- 允許（或封鎖）使用者在其裝置上變更這些服務的同步設定。 

若要查看目前的設定，請移至[Intune 中 iOS 裝置的電子郵件設定檔設定](../configuration/email-settings-ios.md)。

適用於：
- iOS 13.0 與更新版本
- iPadOS 13.0 和更新版本

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices---5353228----"></a>防止使用者將個人 Google 帳戶新增至 Android Enterprise 裝置擁有者和專用裝置<!-- 5353228  -->
您將能夠防止使用者在 Android 企業裝置擁有者和專用裝置上建立個人 Google 帳戶（**裝置**設定 > **設定檔** > **建立設定檔** > **Android Enterprise** **僅限平臺 > 裝置擁有者 >** 配置檔案類型 >**使用者和帳戶設定**）的裝置限制。

若要查看您目前可以設定的設定，請參閱[使用 Intune 來允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。

適用於：
- Android Enterprise 裝置擁有者
- Android Enterprise 專用裝置

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile---5468501----"></a>IOS 裝置限制設定檔中已移除 Siri 命令的伺服器端記錄設定<!-- 5468501  -->
在 iOS 裝置上，您可以建立裝置限制設定檔，以設定 Siri 命令的伺服器端記錄（**裝置**設定 > **配置**檔 > 為平臺**建立設定檔** > **iOS/iPadOS**> 配置檔案類型 >**內建應用程式**）的**裝置限制**。 將會移除**Siri 命令的伺服器端記錄**設定。

此設定將會從 Intune 管理主控台移除。 即使已設定此設定的現有原則會繼續顯示設定，此設定對裝置沒有任何作用。 如果您想要從現有的原則中移除設定，請移至原則、進行次要編輯、儲存，然後將更新原則。

若要查看您可以設定的設定，請參閱[使用 Intune 透過 iOS 與 iPadOS 裝置設定來允許或限制功能](../configuration/device-restrictions-ios.md)。

適用於：
- iOS

<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
<!--## Device management-->


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>監視和疑難排解

### <a name="centralized-audit-logs--5603185-5697164--"></a>集中式審核記錄<!--5603185, 5697164-->
新的集中式審核記錄體驗會將所有類別的審核記錄收集到單一頁面中。 You'l 能夠篩選記錄檔，以取得您要尋找的資料。 若要查看 audit 記錄，請移至 [**租使用者管理**] > [ **audit logs**]。 如需詳細資訊，請參閱[Intune 中的 Audit 記錄即將進行的變更](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Upcoming-change-to-Audit-logs-in-Intune/ba-p/1015858)。

<!-- ***********************************************-->
<!--## Role-based access control-->


<!-- ***********************************************-->

## <a name="security"></a>安全性

### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529-idready---"></a>使用 PKCS 憑證設定檔搭配憑證來布建裝置<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529 IDready -->
您將能夠使用 PKCS 憑證設定檔，將憑證發行至裝置，並在我們目前的使用者憑證支援上擴充。 以裝置為基礎的憑證將支援 Android、iOS 和 Windows 平臺，並可用於 Wi-fi 和 VPN 設定檔。

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。


