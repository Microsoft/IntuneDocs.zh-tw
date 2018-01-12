---
title: "在 Intune 中註冊 macOS 裝置"
titlesuffix: Azure portal
description: "了解如何在 Intune 中註冊 macOS 裝置。"
keywords: 
author: ErikjeMS
ms.author: erikje
nmanager: angrobe
ms.date: 10/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3d1382e85b9ce58cd65380a799ca8eb4da98b84c
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2018
---
# <a name="enroll-macos-devices-in-intune"></a>在 Intune 中註冊 macOS 裝置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 可讓您管理 macOS 裝置。 若要啟用裝置管理，您的使用者必須前往[公司入口網站](http://portal.manage.microsoft.com)，並遵循提示以註冊其裝置。 管理 macOS 裝置之後，您可以[建立 macOS 裝置的自訂設定](custom-settings-macos.md)。 即將推出更多功能。

## <a name="prerequisites"></a>必要條件

請於設定 macOS 裝置註冊之前，先完成下列必要條件︰

- [設定網域](custom-domain-name-configure.md)
- [設定 MDM 授權單位](mdm-authority-set.md)
- [建立群組](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [設定公司入口網站](company-portal-app.md)
- 指派 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)中的使用者授權
- [取得 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)

## <a name="set-up-macos-enrollment"></a>設定 macOS 註冊

根據預設，Intune 已允許註冊 macOS 裝置。

若要封鎖註冊 macOS 裝置，請參閱 [Set device type restrictions](enrollment-restrictions-set.md) (設定裝置類型限制)。

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>告知使用者如何註冊其裝置才可存取公司資源

告訴使用者前往[公司入口網站](http://portal.manage.microsoft.com)，並遵循提示以註冊其裝置。 您也可以將線上註冊步驟的連結傳送給他們︰[在 Intune 註冊 macOS 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)。

如需其他使用者工作的資訊，請參閱下列文章：

- [使用 Microsoft Intune 之使用者體驗的相關資源](end-user-educate.md)
- [搭配 Intune 使用 iOS 或 macOS 裝置](https://docs.microsoft.com/intune-user-help/using-your-ios-or-mac-os-x-device-with-intune)
