---
title: "已註冊的裝置管理功能 | Microsoft Docs"
description: "閱讀本主題以了解 Intune 如何協助您管理您註冊的裝置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/12/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f23b3ee7-78da-4e53-9fc2-78e58401bcf9
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 364c7e1fe2bf17b0c804960c3ebaadb1cf4652a8
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Microsoft Intune 的已註冊裝置管理功能

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 可讓您向服務*註冊*某個範圍的裝置來管理這些裝置。 您可以自行註冊某些裝置類型，或者使用者可以使用「公司入口網站」應用程式進行註冊。 這也可讓它們執行例如瀏覽及安裝應用程式等作業，確保他們的裝置與公司原則相容，並連絡其 IT 支援人員。

本主題提供註冊裝置後取得之功能的完整清單。

管理、清查、應用程式部署、佈建，以及停用皆透過 Intune 管理主控台來處理。 使用者取得公司入口網站的存取權，以安裝應用程式、註冊及移除裝置，以及連絡其 IT 部門或技術服務人員。



## <a name="device-security-and-configuration"></a>裝置安全性和設定

|功能|詳細資料|詳細資訊|
|--------------|-----------|--------------------|
|設定原則<br><br>自訂原則| 可讓您管理組織中行動裝置上的許多設定及功能。 例如，您可以要求密碼、限制嘗試失敗次數、限制螢幕鎖定之前的時間、設定密碼到期，以及禁止先前用過的密碼。 您也可以控制使用的硬體和軟體功能，例如裝置相機或網頁瀏覽器。<br><br>當設定原則不含您所需要的設定時，可使用自訂原則。 針對 iOS 裝置，您可以匯入您從 Apple 設定程式工具匯出的設定。 針對其他裝置，您可以使用開放行動聯盟的統一資源識別項 /intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)<br />|
|遠端抹除、遠端鎖定和密碼重設|當裝置遺失或遭竊時，可以清除機密資料。 例如，您可以遠端鎖定裝置、將它還原為原廠設定，或只抹除公司資料。<br><br>您可以在使用者失去裝置存取權的情況下重設密碼、鎖定遺失或遭竊的裝置，甚至抹除遺失或遭竊裝置上的資料。|[透過遠端鎖定或密碼重設來協助保護您的裝置](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management)|
|資訊站模式|可讓您鎖定行動裝置的某些功能，例如螢幕擷取畫面及電源開關。 也可讓您限制裝置只能執行您指定的單一應用程式。|[Microsoft Intune 的 iOS 設定原則設定](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)|

## <a name="app-management"></a>應用程式管理

|功能|詳細資料|詳細資訊|
|--------------|-----------|--------------------|
|應用程式部署及管理|提供多種工具協助您管理行動應用程式的生命週期，包括安裝檔案及應用程式存放區、密切監視應用程式狀態及移除應用程式等應用程式部署工作。|[在 Microsoft Intune 中部署應用程式](/intune-classic/deploy-use/deploy-apps)|
|符合規定及不符合規定的應用程式|可讓您指定相容應用程式清單 /intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)|
|行動應用程式管理|對於所有使用 Intune 管理的裝置和未使用 Intune 管理的裝置，使用行動應用程式管理來設定應用程式的限制。 這可讓您藉由限制某些作業來提升公司資料的安全性，例如複製及貼上、從外部備份資料，以及在應用程式之間傳送資料。|[在 Microsoft Intune 主控台中設定和部署行動應用程式管理原則](/intune-classic/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)|
|iOS 行動裝置應用程式組態|使用行動裝置應用程式設定原則來為 iOS 應用程式提供使用者執行應用程式時可能需要的設定。 例如，應用程式可能需要使用者指定連接埠號碼或登入資訊。 這有助於簡化設定，並減少支援呼叫的數量。|[在 Microsoft Intune 中使用行動應用程式設定原則設定 iOS 應用程式](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)|
|iOS 行動裝置應用程式佈建設定檔|協助您將佈建設定檔部署至即將到期的 iOS 應用程式。 |[使用 iOS 行動佈建設定檔原則，以避免您的應用程式過期](/intune-classic/deploy-use/ios-mobile-app-provisioning-profiles)|
|受管理的瀏覽器|設定受管理的瀏覽器原則來控制裝置使用者可以瀏覽的網站。 此外也可將行動應用程式管理原則，套用到受管理的瀏覽器。|[搭配 Microsoft Intune 使用受管理的瀏覽器原則管理網際網路存取](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies)|
|Windows Hello 企業版|讓您與 Windows Hello 企業版整合，這是使用內部部署 Active Directory 或 Azure Active Directory 取代密碼、智慧卡或虛擬智慧卡來登入 Windows 10 的替代方法。|[使用 Microsoft Intune 控制裝置上的 Windows Hello 企業版設定](/intune-classic/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)|
|大量採購的應用程式|藉由從應用程式市集匯入授權資訊、追蹤您已經使用了多少個授權，並避免您安裝超過擁有數目的應用程式複本，來協助您管理透過大量採購方案購買的應用程式。|[使用 Microsoft Intune 管理大量購買的應用程式](/intune-classic/deploy-use/manage-volume-purchased-apps-in-microsoft-intune)|

## <a name="company-resource-access"></a>公司資源存取

|功能|詳細資料|詳細資訊|
|--------------|-----------|--------------------|
|憑證設定檔|建立及部署信任的憑證設定檔與簡單憑證註冊通訊協定 /intune-classic/deploy-use/secure-resource-access-with-certificate-profiles)|
|Wi-Fi 設定檔|將無線網路設定部署到您的使用者。 您可以藉由部署這些設定，盡可能減少使用者連線到公司網路所需的作業。|[Microsoft Intune 中的 Wi-Fi 連線](/intune-classic/deploy-use/wi-fi-connections-in-microsoft-intune)|
|電子郵件設定檔|建立電子郵件設定，並將其部署到裝置。 這代表使用者無須進行任何設定，就能從其個人裝置上存取公司的電子郵件。|[使用電子郵件設定檔與 Microsoft Intune 來設定公司電子郵件存取權](/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)|
|VPN 設定檔|將 VPN 設定部署至組織中的使用者及裝置。 透過部署這些設定，即可最小化連線到公司網路上資源所需的使用者工作。|[Microsoft Intune 中的 VPN 連線](/intune-classic/deploy-use/vpn-connections-in-microsoft-intune)|
|條件式存取原則|管理自未受 Intune 管理之裝置對 Microsoft Exchange 電子郵件及 SharePoint Online 的存取。|[使用 Microsoft Intune 限制電子郵件和 SharePoint 的存取](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)|

## <a name="inventory-and-reporting"></a>清查和報告

|功能|詳細資料|詳細資訊|
|--------------|-----------|--------------------|
|清查和報告|尋找您管理的裝置及裝置所用軟體的相關資訊。|[在 Microsoft Intune 透過清查了解您的裝置](/intune-classic/deploy-use/understand-your-devices-with-inventory-in-microsoft-intune)|

