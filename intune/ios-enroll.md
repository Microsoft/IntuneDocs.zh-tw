---
title: "選擇在 Intune 中註冊 Windows 裝置的方式"
titleSuffix: Intune on Azure
description: "了解如何在 Microsoft Intune 中設定 Windows 裝置註冊。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 61bdbc7ca68995e23295cf099ce73dfdcaeba37c
ms.sourcegitcommit: 5eb209ae48173ddfdbbab131f12f3ac3498dcd87
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2017
---
# <a name="enroll-ios-devices-in-intune"></a>在 Intune 中註冊 iOS 裝置

Intune 啟用 iPad 和 iPhone 的行動裝置管理 (MDM)，讓使用者存取公司的電子郵件和應用程式。

身為 Intune 管理員，您可以啟用 iOS 裝置註冊。 您可以允許使用者註冊個人擁有的裝置，又稱為「攜帶您自己的裝置」(BYOD) 註冊。 您也可以啟用公司擁有的裝置註冊。

## <a name="prerequisites-for-ios-enrollment"></a>iOS 註冊的必要條件
啟用 iOS 裝置之前，請先完成下列步驟：
- [設定 Intune](setup-steps.md) - 這些步驟會設定您的 Intune 基礎結構。 裝置註冊特別要求您[設定 MDM 授權單位](mdm-authority-set.md)。
- [取得 Apple MDM Push certificate](apple-mdm-push-certificate-get.md) - Apple 需要憑證才能管理 iOS 和 macOS 裝置。

完成這些必要條件之後，使用者就可以安裝公司入口網站應用程式來註冊其個人的 iOS 裝置，或者管理員可以設定公司擁有的 iOS 裝置管理。 管理員也可以指派可以單一管理帳戶註冊許多裝置的[裝置註冊管理員](device-enrollment-manager-enroll.md)。 Intune 支援下列 iOS 公司擁有的裝置註冊方法：

## <a name="device-enrollment-program"></a>裝置註冊方案
組織可以透過 Apple 的裝置註冊計劃 (DEP) 購買 iOS 裝置。 DEP 可以讓您在「線上」部署註冊設定檔，將裝置納入管理。 深入了解[裝置註冊計劃](device-enrollment-program-enroll-ios.md)。

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager 是針對學校提供的裝置採購暨註冊方案。 就像 DEP，您可以部署設定檔以註冊管理的裝置。 深入了解 [Apple School Manager](apple-school-manager-set-up-ios.md)。

## <a name="apple-configurator"></a>Apple Configurator
您可以使用 Apple Configurator 在 Mac 電腦上註冊 iOS 裝置。 若要準備裝置，請以 USB 連接它們並安裝註冊設定檔。 使用 Apple Configurator 註冊裝置的方法共有兩種：
- 設定助理註冊 - 將裝置重設為原廠設定，並將裝置備妥可執行設定助理，以及為裝置的新使用者安裝公司原則。
- 直接註冊 - 不會將裝置重設為原廠設定，並使用預先定義的原則來註冊裝置。 這個方法適用於無使用者親和性的裝置。

深入了解 [Apple Configurator 註冊](apple-configurator-setup-assistant-enroll-ios.md)。
