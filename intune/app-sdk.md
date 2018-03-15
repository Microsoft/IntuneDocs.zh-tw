---
title: "Intune App SDK 優點"
titlesuffix: Microsoft Intune
description: "Intune App SDK 適用於 iOS 和 Android 平台，並提供 Microsoft Intune 的行動應用程式管理功能。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ae22d3e718fd01330b81206921b6e9a23313a30f
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2018
---
# <a name="intune-app-sdk-overview"></a>Intune App SDK 概觀
Intune App SDK (適用於 iOS 和 Android) 可啟用應用程式的 Intune 應用程式保護原則。 它會盡力將應用程式開發人員所需的程式碼變更數量減到最少。 您會發現，您可以啟用大多數 SDK 功能，而不需要變更您的應用程式行為。 為了增強使用者和 IT 系統管理員體驗，您可以利用 API，針對需要應用程式參與的功能自訂您的應用程式行為。

啟用應用程式的應用程式保護原則之後，IT 系統管理員就可以部署這些原則，以保護他們在應用程式內的公司資料。

## <a name="app-protection-features"></a>應用程式保護功能

下列是可使用 SDK 所啟用的 Intune 應用程式保護功能範例。

### <a name="control-users-ability-to-move-corporate-files"></a>控制使用者移動公司檔案的能力
IT 系統管理員可以控制可在何處移動應用程式中的工作或學校資料。 例如，他們可以部署原則來停用應用程式將公司資料備份到雲端。

### <a name="configure-clipboard-restrictions"></a>設定剪貼簿限制
IT 系統管理員可以在受 Intune 管理的應用程式中設定 [剪貼簿] 行為。 例如，他們可以部署原則，來防止終端使用者從應用程式剪下或複製資料，並貼入未受管理的個人應用程式。

### <a name="enforce-encryption-on-saved-data"></a>強制加密已儲存的資料
IT 系統管理員可以強制執行原則，以確保應用程式儲存到裝置的資料會經過加密。

### <a name="remotely-wipe-corporate-data"></a>從遠端抹除公司資料
IT 系統管理員可以從受 Intune 管理的應用程式遠端抹除公司資料。 這項功能是以身分識別為基礎，而且只會刪除與使用者公司身分識別相關聯的檔案。 若要執行這項操作，此功能需要應用程式的參與。 應用程式可以根據使用者設定，指定應該進行抹除的身分識別。 如果沒有來自應用程式的這些指定的使用者設定，預設行為是抹除應用程式目錄，並通知使用者已移除存取權。

### <a name="enforce-the-use-of-a-managed-browser"></a>強制使用受管理的瀏覽器
IT 系統管理員可以強制使用 [Intune Managed Browser 應用程式](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies)開啟應用程式中的網頁連結。 此功能可確保出現在公司環境中的連結會保留在受 Intune 管理之應用程式的網域內。

### <a name="enforce-a-pin-policy"></a>強制執行 PIN 原則
IT 系統管理員可以要求終端使用者先輸入 PIN，才能存取應用程式中的公司資料。 這可確保使用應用程式的人員就是一開始使用其工作或學校帳戶登入的相同人員。 當終端使用者設定其 PIN 時，Intune App SDK 會使用 Azure Active Directory 依據已註冊的 Intune 帳戶來驗證終端使用者的認證。

### <a name="require-users-to-sign-in-with-work-or-school-account-for-app-access"></a>要求使用者使用工作或學校帳戶登入來存取應用程式
IT 系統管理員可以要求使用者使用其工作或學校帳戶登入來存取應用程式。 Intune App SDK 使用 Azure Active Directory 來提供單一登入體驗，其中認證一旦輸入，便可供後續登入重複使用。 我們也支援驗證與 Azure Active Directory 建立同盟的身分識別管理解決方案。

### <a name="check-device-health-and-compliance"></a>檢查裝置健全狀況和合規性
IT 系統管理員可以在終端使用者存取應用程式之前，檢查裝置的健全狀況以及其是否符合 Intune 原則。 在 iOS 上，這項原則會檢查裝置是否已進行 JB 破解。 在 Android 上，這項原則會檢查裝置是否已進行 Root 破解。

### <a name="multi-identity-support"></a>多重身分識別支援
多重身分識別支援是一種 SDK 功能，允許單一應用程式中可以共存受原則管理的帳戶 (公司) 和未受管理的帳戶 (個人)。

例如，許多使用者會在適用於 iOS 和 Android 的 Office 行動應用程式中，同時設定公司和個人電子郵件帳戶。 使用者使用其公司帳戶來存取資料時，IT 系統管理員必須確定將套用應用程式保護原則。 不過，當使用者存取個人電子郵件帳戶，該資料則不在 IT 系統管理員的控制範圍內。 Intune App SDK 藉由將應用程式保護原則的目標**僅**限於應用程式中的公司身分識別，來達成這項目的。

多重身分識別功能有助於解決組織在使用同時支援個人和工作帳戶的市集應用程式時，所遇到的資料保護問題。
 
### <a name="app-protection-without-device-enrollment"></a>無裝置註冊的應用程式保護

>[!IMPORTANT]
>Intune App Wrapping Tools、Intune App SDK for Android、Intune App SDK for iOS、SDK Xamarin Component 和 SDK Cordova Plugin 提供無裝置註冊的 Intune 應用程式保護。

許多個人裝置的使用者想要存取公司資料，但不想向行動裝置管理 (MDM) 提供者註冊其個人裝置。 因為 MDM 註冊需要裝置的通用控制權，所以使用者通常不太願意將其個人裝置的控制權提供給公司。

無裝置註冊的應用程式保護可讓 Microsoft Intune 服務將應用程式保護原則直接部署到應用程式，而不需要裝置管理通道來部署原則。
