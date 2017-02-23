---
title: "在 Intune 中註冊 Android 裝置 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解如何在 Intune Azure 預覽版中註冊 Android 裝置。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: edd6303f3bb05dfff758cbb7d4bd08e21f083998


---

# <a name="enroll-android-devices"></a>註冊 Android 裝置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

身為 Intune 系統管理員，您可以從公司入口網站啟用 Android 裝置的管理，包括 Samsung Knox Standard 裝置。 使用者接著可以使用 Google Play 提供的公司入口網站應用程式來註冊其裝置。

## <a name="prerequisite"></a>必要條件

您必須將 MDM 授權單位設定為 **Microsoft Intune**準備管理行動裝置。 請參閱[設定 MDM 授權單](set-mdm-authority.md)以取得相關指示。 此項目只會設定一次，也就是第一次為行動裝置管理設定 Intune 之時，因此您有可能已經設定過此項目。 

## <a name="set-up-android-enrollment"></a>設定 Android 註冊

根據預設，Intune 會設定為允許註冊 Android 與 Samsung Knox Standard 裝置。 

若要看允許或封鎖註冊 Android 裝置的設定，請前往 Azure 入口網站中的 Intune 刀鋒視窗頁面，然後選擇 [註冊]  >  [註冊限制]。 

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>告知使用者如何註冊其裝置才可存取公司資源

如需使用者註冊指示，請參閱[在 Intune 註冊 Android 裝置](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android)。 註冊程序會告知使用者，他們能獲得什麼，以及 IT 系統管理員可以和無法在其裝置上看到什麼。

如需其他使用者工作的資訊，請參閱下列文章：

- [使用 Microsoft Intune 之使用者體驗的相關資源](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [在 Intune 上使用您的 Android 裝置](https://docs.microsoft.com/intune/enduser/using-your-android-device-with-intune)


<!--HONumber=Feb17_HO1-->


