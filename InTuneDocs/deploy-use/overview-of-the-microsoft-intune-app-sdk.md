---
title: "Microsoft Intune App SDK 概觀 | Microsoft Docs"
description: "Intune App SDK 適用於 iOS 和 Android 平台，並提供 Microsoft Intune 的行動應用程式管理功能。"
keywords: 
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ef1751bb-3a2f-4662-a922-38c076869eb3
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f46f13e9dbf03fa2b3e2ec7339cad927ea0b38e0
ms.openlocfilehash: 99f3aa3c8640dd41133584b3e1cb056dfd493efa
ms.lasthandoff: 12/20/2016


---

# <a name="overview-of-the-microsoft-intune-app-sdk"></a>Microsoft Intune App SDK 概觀

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune App SDK 適用於 iOS 和 Android 平台，並提供 Microsoft Intune 的行動應用程式管理功能。 此外，它會致力於減少開發人員必須進行的程式碼變更。

您會發現，您可以啟用大多數 SDK 功能，而不需要變更您的應用程式行為。 為了改進使用者和 IT 系統管理員體驗，您可以利用我們的 API，針對需要應用程式參與的功能自訂您的應用程式行為。

一旦您啟用應用程式，IT 系統管理員便可將原則部署至受 Intune 管理的應用程式，並利用這些功能來保護其公司資料。

## <a name="features"></a>功能
### <a name="control-users-ability-to-move-corporate-documents"></a>控制使用者移動公司文件的能力
IT 系統管理員可以控制受 Intune 管理的應用程式中公司文件的檔案重新配置。 例如，他們可以部署原則來停用檔案備份應用程式，以防止應用程式將公司資料備份到雲端。  

### <a name="configure-clipboard-restrictions"></a>設定剪貼簿限制
IT 系統管理員可以在受 Intune 管理的應用程式中設定 [剪貼簿] 行為。 例如，他們可以部署一個原則，讓使用者無法使用剪貼簿剪下或複製受 Intune 管理的應用程式並貼上至非管理的應用程式。

### <a name="enforce-encryption-on-saved-data"></a>強制加密已儲存的資料
IT 系統管理員可以強制執行原則，以確保應用程式儲存到裝置的資料會經過加密。

### <a name="remotely-wipe-corporate-data"></a>從遠端抹除公司資料
IT 系統管理員可以在取消註冊 Microsoft Intune 中的裝置時，從受 Intune 管理的應用程式遠端抹除公司資料。 這項功能是以身分識別為基礎，而且只會刪除與使用者之公司識別相關的檔案。 若要執行這項操作，此功能需要應用程式的參與。 應用程式可以根據使用者設定，指定應該進行抹除的身分識別。 如果沒有來自應用程式的這些指定的使用者設定，預設行為是抹除應用程式目錄，並通知使用者已移除公司資源存取權。

### <a name="enforce-the-use-of-a-managed-browser"></a>強制使用受管理的瀏覽器
IT 系統管理員可以在使用者開啟受 Intune 管理之應用程式中的連結時，強制使用受管理的瀏覽器。 當使用者使用受 Microsoft Intune 管理的瀏覽器時，它可協助確保在受 Intune 管理的應用程式網域內，保留出現在電子郵件中 (受 Intune 管理的郵件用戶端中) 的連結。

### <a name="enforce-a-pin-policy"></a>強制執行 PIN 原則
IT 系統管理員可以在受 Intune 管理的應用程式啟動時，強制執行 PIN 原則。 這項原則有助於確保向 Microsoft Intune 註冊其裝置的使用者是啟動應用程式的相同人員。 當使用者設定其 PIN 時，Intune App SDK 會使用 Azure Active Directory 依據裝置註冊認證來驗證認證。

### <a name="require-users-to-enter-credentials-before-they-can-start-apps"></a>要求使用者在啟動應用程式之前先輸入認證
IT 系統管理員可以要求使用者在啟動受 Intune 管理的應用程式之前先輸入其認證。 Intune App SDK 使用 Azure Active Directory 來提供單一登入體驗。 這表示認證一旦輸入，會重複用於後續的登入。 SDK 也支援驗證[與 Azure Active Directory 同盟](/active-directory/active-directory-aadconnect-federation-compatibility)的身分識別管理解決方案。

### <a name="check-device-health-and-compliance"></a>檢查裝置健全狀況和相容性
IT 系統管理員可以在使用者存取受 Intune 管理的應用程式之前，檢查裝置的健全狀況及其是否符合公司原則。 在 iOS 平台上，這項原則會檢查裝置是否已進行 JB 破解。 在 Android 平台上，這項原則會檢查裝置是否已進行 Root 破解。  

