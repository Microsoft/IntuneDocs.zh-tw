---
title: "在 Intune 中註冊 macOS 裝置 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解如何在 Intune Azure 預覽版中註冊 macOS 裝置。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 1/3/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba2affcdbcdfcd690d671c7b20f9d1e14a74f764
ms.openlocfilehash: 171175689adca027181f3da4d05222117de97e13


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>在 Intune Azure 預覽版中註冊 macOS 裝置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

您身為 Intune 系統管理員，可管理 macOS 裝置。 根據預設，使用者可利用 Azure 入口網站來註冊其 macOS 裝置。 您只需要告訴使用者前往[公司入口網站](http://portal.manage.microsoft.com)以及註冊其 macOS 裝置即可。 

## <a name="prerequisites"></a>必要條件

請於設定 macOS 裝置註冊之前，先完成下列必要條件︰

- [設定網域](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [設定 MDM 授權單位](set-mdm-authority.md)
- [建立群組](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [設定公司入口網站](/intune-azure/manage-apps/company-portal-app.md)
- 指派 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)中的使用者授權
- [取得 Apple MDM Push Certificate](get-an-apple-mdm-push-certificate.md)

## <a name="set-up-macos-enrollment"></a>設定 macOS 註冊

根據預設，Intune 已設定為允許註冊 macOS 裝置。 

若要查看允許或封鎖 macOS 裝置註冊的設定，請前往 Azure 入口網站中的 Intune 刀鋒視窗，然後選擇 [註冊][註冊限制] > 。 

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>告知使用者如何註冊其裝置才可存取公司資源

如需取得使用者註冊指示，請參閱[在 Intune 註冊 macOS 裝置](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-macos)。 註冊程序會告知使用者，他們能獲得什麼，以及 IT 系統管理員可以和無法在其裝置上看到什麼。

如需其他使用者工作的資訊，請參閱下列文章：

- [使用 Microsoft Intune 之使用者體驗的相關資源](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [搭配 Intune 使用 iOS 或 macOS 裝置](https://docs.microsoft.com/intune/enduser/using-your-ios-or-mac-os-x-device-with-intune)


<!--HONumber=Feb17_HO1-->


