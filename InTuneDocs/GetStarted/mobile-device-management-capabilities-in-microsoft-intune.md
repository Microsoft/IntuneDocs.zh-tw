---
# required metadata

title: Microsoft Intune 的行動裝置管理功能 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f23b3ee7-78da-4e53-9fc2-78e58401bcf9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
# Microsoft Intune 的行動裝置管理功能

Microsoft Intune 可讓您向服務註冊某個範圍的裝置來管理這些裝置。 使用者接著可以使用公司入口網站來執行各種作業，例如註冊其裝置、瀏覽及安裝應用程式、確定他們的裝置與公司原則相容，及連絡其 IT 支援。
本主題提供註冊裝置提供之功能的完整清單。

管理、清查、應用程式部署、佈建，以及停用皆透過 Intune 管理主控台來處理。 使用者存取公司入口網站來安裝應用程式、註冊及移除裝置，以及協助連絡其 IT 部門或技術服務人員。



## 裝置安全性和設定

|功能|詳細資料|詳細資訊|
|--------------|-----------|--------------------|
|設定原則<br><br>自訂原則|行動裝置設定原則可讓您管理組織中行動裝置上的許多設定及功能。 例如，您可以要求密碼、限制嘗試失敗次數、限制螢幕鎖定之前的分鐘數、設定密碼到期，以及禁止先前用過的密碼。 您也可以控制使用的硬體和軟體功能，例如裝置攝影機或網頁瀏覽器<br><br>當設定原則不含您所需要的設定時，可使用自訂原則。 對於 iOS 裝置，您可以匯入您從 Apple 設定程式工具匯出的設定。 對於其他裝置，您可以使用 OMA URI 設定來設定裝置上的設定與功能。|[透過 Microsoft Intune 原則管理裝置上的設定和功能](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)<br />|
|遠端抹除、遠端鎖定和密碼重設|當裝置遺失或遭竊時，可以清除敏感資料。 例如，您可以遠端鎖定裝置、將它還原為原廠設定，或只抹除公司資料。<br>您可以在使用者失去裝置存取權的情況下重設密碼、鎖定遺失或遭竊的裝置，甚至抹除遺失或遭竊裝置上的資料。|[使用遠端鎖定和密碼重設來協助保護您的裝置](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune)和[從 Intune 管理淘汰裝置](/intune/deploy-use/retire-devices-from-microsoft-intune-management)|
|資訊站模式|可讓您鎖定行動裝置的某些功能，例如螢幕擷取畫面及電源開關。 也可讓您限制裝置只能執行您指定的單一應用程式。|[Microsoft Intune 的 iOS 組態原則設定](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|

## 應用程式管理

|功能|詳細資料|詳細資訊|
|--------------|-----------|--------------------|
|應用程式部署及管理|提供多種工具協助您管理行動應用程式的生命週期，包括安裝檔案及應用程式存放區、密切監視應用程式狀態及移除應用程式等應用程式部署工作。|[在 Microsoft Intune 中部署應用程式](/intune/deploy-use/deploy-apps)|
|符合規定及不符合規定的應用程式|可讓您指定相容應用程式 (使用者可以安裝的應用程式) 及不相容應用程式 (使用者不得安裝) 的清單。|[Microsoft Intune 的 iOS 原則設定](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|
|行動應用程式管理|對您使用 Intune 管理的裝置和未由 Intune 管理的裝置，使用行動應用程式管理來設定應用程式的限制。 這可讓您藉由限制某些作業來提升公司資料的安全性，例如複製及貼上、從外部備份資料，以及在應用程式之間傳送資料。|[在 Microsoft Intune 主控台中設定及部署行動應用程式管理原則](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)<br><br>[使用 Microsoft Intune 建立及部署行動應用程式管理原則](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)<br /><br />[準備將 iOS 應用程式交由 Microsoft Intune App Wrapping Tool 進行行動應用程式管理](/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)<br /><br />[準備 Android 應用程式以使用 Microsoft Intune 應用程式包裝工具進行行動應用程式管理](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)|
|行動裝置應用程式組態|使用行動裝置應用程式組態原則來為 iOS 應用程式提供使用者執行應用程式時可能需要的設定。 例如，應用程式可能需要使用者指定登入資訊的連接埠號碼。 這有助於簡化組態，並減少服務台電話數量。|[在 Microsoft Intune 中使用行動裝置應用程式組態原則設定 iOS 應用程式](/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)|
|受管理的瀏覽器|為使用者部署受管理的瀏覽器之後，可以設定受管理的瀏覽器原則來控制他們所能造訪的網站。 此外也可將行動應用程式管理原則，套用到受管理的瀏覽器。|[透過 Microsoft Intune 使用受管理的瀏覽器原則管理網際網路存取](/intune/deploy-use/manage-internet-access-using-managed-browser-policies)|
|Microsoft Passport|Intune 可讓您與 Microsoft Passport for Work 整合，這是使用 Active Directory 或 Azure Active Directory 帳戶取代密碼、智慧卡或虛擬智慧卡來登入 Windows 10 的替代方法。|[使用 Microsoft Intune 控制裝置上的 Microsoft Passport 設定](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)|

## 公司資源存取

|功能|詳細資料|詳細資訊|
|--------------|-----------|--------------------|
|憑證設定檔|建立及部署信任的憑證設定檔與簡單憑證註冊通訊協定 (SCEP) 憑證，以用來保護及驗證 Wi-Fi、VPN 與電子郵件設定檔。|[使用 Microsoft Intune 中的憑證設定檔來保護資源存取](/intune/deploy-use/secure-resource-access-with-certificate-profiles)|
|Wi-Fi 設定檔|將無線網路設定部署到您的使用者。 您可以藉由部署這些設定，盡可能減少使用者連線到公司網路所需的作業。|[Microsoft Intune 中的 Wi-Fi 連線](/intune/deploy-use/wi-fi-connections-in-microsoft-intune)|
|電子郵件設定檔|建立電子郵件設定，並將其部署到裝置。 如此一來，使用者無須進行任何設定，就能從其個人裝置上存取公司的電子郵件。|[使用電子郵件設定檔與 Microsoft Intune 來設定公司電子郵件存取權](/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)|
|VPN 設定檔|將 VPN 設定部署給組織中的使用者及裝置。 透過部署這些設定，即可最小化連線到公司網路上資源所需的使用者工作。|[Microsoft Intune 中的 VPN 連線](/intune/deploy-use/vpn-connections-in-microsoft-intune)|
|條件式存取原則|管理自未由 Intune 管理的裝置對 Microsoft Exchange 電子郵件及 SharePoint Online 的存取。|[使用 Microsoft Intune 限制電子郵件和 SharePoint 的存取](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)|

## 清查和報告

|功能|詳細資料|詳細資訊|
|--------------|-----------|--------------------|
|清查和報告|尋找您管理的裝置及裝置所用軟體的相關資訊。<br /><br />您可以透過數種方式篩選這些報表 (例如裝置平台)，以及裝置是否與公司標準相容。|[透過報表來了解 Microsoft Intune 作業](/intune/understand-explore/understand-microsoft-intune-operations-by-using-reports)|

### 請參閱
[Microsoft Intune 的 Windows 電腦管理功能](/intune/understand-explore/windows-pc-management-capabilities-in-microsoft-intune)


<!--HONumber=May16_HO1-->


