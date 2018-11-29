---
title: Microsoft Intune 中的裝置管理功能
description: 閱讀本主題以了解 Intune 如何協助您管理您註冊的裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 22e184530dc0ae0e2bb636d3df8d5b45d8c4d0c7
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189484"
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Microsoft Intune 的已註冊裝置管理功能

Microsoft Intune 可讓您向服務*註冊*某個範圍的裝置來管理這些裝置。 您可以自行註冊某些裝置類型，或者使用者可以使用「公司入口網站」應用程式進行註冊。 註冊可以讓他們瀏覽及安裝應用程式、確認其裝置與公司原則相容，以及連絡其 IT 支援人員。

本文會完整列出您裝置註冊後所取得的功能。

管理、清查、應用程式部署、佈建及淘汰皆透過 Intune 入口網站處理。

使用者取得公司入口網站的存取權，以安裝應用程式、註冊及移除裝置，以及連絡其 IT 部門或技術服務人員。



## <a name="device-security-and-configuration"></a>裝置安全性和設定

|功能|詳細資料|詳細資訊|
|--------------|-----------|--------------------|
|設定原則<br><br>自訂原則| 可讓您管理組織中行動裝置上的許多設定及功能。 例如，您可以要求密碼、限制嘗試失敗次數、限制螢幕鎖定之前的時間、設定密碼到期，以及禁止先前用過的密碼。 您也可以控制使用的硬體和軟體功能，例如裝置相機或網頁瀏覽器。<br><br>當設定原則未包含您需要的設定時，請使用自訂原則。 針對 iOS 裝置，您可以匯入您從 Apple 設定程式工具匯出的設定。 針對其他裝置，您可以使用開放行動聯盟的統一資源識別項 (OMA URI) 設定來設定裝置上的設定與功能。|[使用 Microsoft Intune 原則管理裝置的設定及功能](device-compliance-get-started.md)|
|遠端抹除、遠端鎖定和密碼重設|當裝置遺失或遭竊時，可以清除機密資料。 例如，您可以遠端鎖定裝置、將它還原為原廠設定，或只抹除公司資料。<br><br>您可以在使用者失去裝置存取權的情況下重設密碼、鎖定遺失或遭竊的裝置，甚至抹除遺失或遭竊裝置上的資料。|透過[遠端鎖定](device-remote-lock.md)及[密碼重設](device-passcode-reset.md)來協助保護您的裝置|
|資訊站模式|可讓您鎖定行動裝置的某些功能，例如螢幕擷取畫面及電源開關。 也可讓您限制裝置只能執行您指定的單一應用程式。|[Microsoft Intune 的 iOS 設定原則設定](device-restrictions-ios.md)|

## <a name="app-management"></a>應用程式管理

|功能|詳細資料|詳細資訊|
|--------------|-----------|--------------------|
|應用程式部署及管理|提供多種工具協助您管理行動應用程式的生命週期，包括安裝檔案及應用程式存放區、密切監視應用程式狀態及移除應用程式等應用程式部署工作。|[在 Microsoft Intune 中部署應用程式](apps-deploy.md)|
|符合規定及不符合規定的應用程式|可讓您指定相容應用程式 (使用者可以安裝的應用程式) 及不相容應用程式 (使用者不得安裝) 的清單。|[Microsoft Intune 的 iOS 原則設定](device-restrictions-ios.md)|
|行動應用程式管理|對於所有使用 Intune 管理的裝置和未使用 Intune 管理的裝置，使用行動應用程式管理來設定應用程式的限制。 您可以藉由限制某些作業來提升公司資料的安全性，例如複製並貼上、從外部備份資料，以及在應用程式間傳輸資料。|[在 Microsoft Intune 主控台中設定和部署行動應用程式管理原則](app-wrapper-prepare-android.md)|
|iOS 行動裝置應用程式組態|使用行動裝置應用程式設定原則來為 iOS 應用程式提供使用者執行應用程式時可能需要的設定。 例如，應用程式可能需要使用者指定連接埠號碼或登入資訊。 您可以簡化應用程式設定，並減少連絡支援人員的次數。|[在 Microsoft Intune 中使用行動應用程式設定原則設定 iOS 應用程式](app-configuration-policies-use-ios.md)|
|iOS 行動裝置應用程式佈建設定檔|協助您將佈建設定檔部署至即將到期的 iOS 應用程式。 |[使用 iOS 行動佈建設定檔原則，以避免您的應用程式過期](app-provisioning-profile-ios.md)|
|受管理的瀏覽器|設定受管理的瀏覽器原則來控制裝置使用者可以瀏覽的網站。 此外也可將行動應用程式管理原則，套用到受管理的瀏覽器。|[搭配 Microsoft Intune 使用受管理的瀏覽器原則管理網際網路存取](app-configuration-managed-browser.md)|
|Windows Hello 企業版|讓您與 Windows Hello 企業版整合，這是使用內部部署 Active Directory 或 Azure Active Directory 取代密碼、智慧卡或虛擬智慧卡來登入 Windows 10 的替代方法。|[使用 Microsoft Intune 控制裝置上的 Windows Hello 企業版設定](windows-hello.md)|
|大量採購的應用程式|藉由從應用程式市集匯入授權資訊、追蹤您已經使用了多少個授權，並避免您安裝超過擁有數目的應用程式複本，來協助您管理透過大量採購方案購買的應用程式。|[使用 Microsoft Intune 管理大量購買的應用程式](vpp-apps.md)|

## <a name="company-resource-access"></a>公司資源存取

|功能|詳細資料|詳細資訊|
|--------------|-----------|--------------------|
|憑證設定檔|建立及部署信任的憑證設定檔與簡單憑證註冊通訊協定 (SCEP) 憑證，以用來保護及驗證 Wi-Fi、VPN 與電子郵件設定檔。|[使用 Microsoft Intune 中的憑證設定檔來保護資源存取](certificates-configure.md)|
|Wi-Fi 設定檔|將無線網路設定部署到您的使用者。 您可以藉由部署這些設定，盡可能減少使用者連線到公司網路所需的作業。|[Microsoft Intune 中的 Wi-Fi 連線](wi-fi-settings-configure.md)|
|電子郵件設定檔|建立電子郵件設定並部署至裝置，讓使用者可在個人裝置上存取公司電子郵件，而不需進行任何必要設定。|[使用電子郵件設定檔與 Microsoft Intune 來設定公司電子郵件存取權](email-settings-configure.md)|
|VPN 設定檔|將 VPN 設定部署至組織中的使用者及裝置。 透過部署這些設定，即可最小化連線到公司網路上資源所需的使用者工作。|[Microsoft Intune 中的 VPN 連線](device-profiles.md#vpn)|
|條件式存取原則|管理自未受 Intune 管理之裝置對 Microsoft Exchange 電子郵件及 SharePoint Online 的存取。|[使用 Microsoft Intune 限制電子郵件和 SharePoint 的存取](app-based-conditional-access-intune.md)|

## <a name="next-steps"></a>接下來的步驟

[See a list of devices that you can manage](device-management.md) (查看您可管理的裝置清單)。