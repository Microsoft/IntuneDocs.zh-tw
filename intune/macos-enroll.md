---
title: 設定 macOS 裝置的註冊
titlesuffix: Microsoft Intune
description: 了解如何在 Intune 中設定 macOS 裝置的註冊。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c1fb846dc65ee14315edf7b9ba15e0e24998a3a2
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2018
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>在 Intune 中設定 macOS 裝置的註冊

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

## <a name="user-owned-ios-devices-byod"></a>使用者擁有的 iOS 裝置 (BYOD)

您可以讓使用者註冊其個人的裝置讓 Intune 管理，這稱為「攜帶您自己的裝置」或 BYOD。 當您完成必要條件及指派使用者授權之後，使用者即可從 App Store 下載 macOS 公司入口網站應用程式，並遵循應用程式中的註冊指示進行。

## <a name="company-owned-ios-devices"></a>公司擁有的 iOS 裝置
針對為使用者購買裝置的組織來說，Intune 可支援使用[裝置註冊管理員](device-enrollment-manager-enroll.md)帳戶來註冊公司擁有裝置 macOS 裝置。

## <a name="set-up-macos-enrollment"></a>設定 macOS 註冊

根據預設，Intune 已允許註冊 macOS 裝置。

若要封鎖註冊 macOS 裝置，請參閱 [Set device type restrictions](enrollment-restrictions-set.md) (設定裝置類型限制)。

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>告知使用者如何註冊其裝置才可存取公司資源

告訴使用者前往[公司入口網站](https://portal.manage.microsoft.com)，並遵循提示以註冊其裝置。 您也可以將線上註冊步驟的連結傳送給他們︰[在 Intune 註冊 macOS 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)。

如需其他使用者工作的資訊，請參閱下列文章：

- [使用 Microsoft Intune 之使用者體驗的相關資源](end-user-educate.md)
- [使用具有 Intune 的 macOS 裝置](/intune-user-help/using-your-macos-device-with-intune)

## <a name="enroll-virtual-macos-machines-for-testing"></a>註冊虛擬 macOS 機器進行測試

> [!NOTE]
> 只支援 macOS 虛擬機器進行測試。 您不應該使用 macOS 虛擬機器作為終端使用者的實際執行裝置。 

您可以使用 Parallels Desktop 或 VMware Fusion 註冊 macOS 虛擬機器進行測試。 

針對 Parallels Desktop，您需要設定虛擬機器的硬體型號和序號，讓 Intune 可以進行辨識。 遵循 Parallels 的[設定硬體型號](http://kb.parallels.com/123594)和[序號](http://kb.parallels.com/123455)指示，設定必要的設定來進行測試。 建議您比對執行虛擬機器之裝置的硬體型號與您所建立之虛擬機器的硬體型號。 您可以在 **Apple 功能表** > [關於此 Mac][系統報表] >  > [模型識別碼] 中找到這個硬體型號。 

針對 VMware Fusion，您需要[編輯 .vmx 檔案](https://kb.vmware.com/s/article/1014782)，設定虛擬機器的硬體型號和序號。 建議您比對執行虛擬機器之裝置的硬體型號與您所建立之虛擬機器的硬體型號。 您可以在 **Apple 功能表** > [關於此 Mac][系統報表] >  > [模型識別碼] 中找到這個硬體型號。 
