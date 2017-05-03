---
title: "在 Intune 中註冊 Android 裝置"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何在 Intune Azure 預覽版中註冊 Android 裝置。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: b2cbabea781840df0a2a283f803dc76520590aba
ms.lasthandoff: 04/19/2017


---

# <a name="enroll-android-devices"></a>註冊 Android 裝置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune 可讓您管理 Android 裝置，包括 Samsung Knox Standard 裝置。 若要啟用裝置管理，您的使用者必須註冊其裝置，方法是下載從 Google Play 取得的 Intune 公司入口網站應用程式，然後開啟應用程式，並遵循提示進行註冊。 管理 Android 裝置之後，您可以[建立合規性原則](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android)、[管理應用程式](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-management)等。

Intune 的多使用者管理現在支援執行 Samsung KNOX Standard 的裝置。 這代表使用者可以使用其 Azure AD 認證登入和登出裝置，而且該裝置不論是否正在使用，都會集中管理。 當終端使用者登入時，他們可以存取應用程式，此外也可以將任何原則套用到這些應用程式。 當使用者登出時，會清除所有應用程式資料。

## <a name="prerequisite"></a>必要條件

您必須將 MDM 授權單位設定為 **Microsoft Intune**準備管理行動裝置。 請參閱[設定 MDM 授權單](set-mdm-authority.md)以取得相關指示。 此項目只會設定一次，也就是第一次為行動裝置管理設定 Intune 之時，因此您有可能已經設定過此項目。

## <a name="set-up-android-enrollment"></a>設定 Android 註冊

根據預設，Intune 已允許註冊 Android 和 Samsung Knox Standard 裝置。

若要封鎖 Android 裝置，或者僅封鎖註冊個人擁有的 Android 裝置，請參閱[Set device type restrictions](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-type-restrictions) (設定裝置類型限制)。

若要設定使用者能夠註冊的裝置數上限，請參閱 [Set device limit restrictions](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-limit-restrictions) (設定裝置限制)。

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>告知使用者如何註冊其裝置才可存取公司資源

您需要告訴使用者移至 Google Play 來下載 Intune 公司入口網站應用程式，然後開啟應用程式，並遵循提示以註冊其裝置。 應用程式會引導使用者進行註冊程序，即說明使用者能獲得什麼，以及 IT 系統管理員可以和無法在其裝置上看到什麼。

您也可以將線上註冊步驟的連結傳送給他們︰[在 Intune 註冊 Android 裝置](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android)。

如需其他使用者工作的資訊，請參閱下列文章：

- [使用 Microsoft Intune 之使用者體驗的相關資源](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)
- [在 Intune 上使用您的 Android 裝置](https://docs.microsoft.com/intune/enduser/using-your-android-device-with-intune)

