---
title: "選擇在 Intune 中註冊 Windows 裝置的方式"
titleSuffix: Intune on Azure
description: "了解如何在 Microsoft Intune 中設定 Windows 裝置註冊。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8bae9bd48493f20bb4abb94290013f27a6a75dd6
ms.sourcegitcommit: 10e3ab2aeb79a1fb2243bef2748ccc003fdd4cc7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2017
---
# <a name="enroll-ios-devices-in-intune"></a>在 Intune 中註冊 iOS 裝置

Intune 啟用 iPad 和 iPhone 的行動裝置管理 (MDM)，讓使用者存取公司的電子郵件和應用程式。

身為 Intune 管理員，您可以啟用 iOS 裝置註冊。 您可以允許使用者註冊個人擁有的裝置，又稱為「攜帶您自己的裝置」(BYOD) 註冊。 您也可以啟用公司擁有的裝置註冊。

## <a name="prerequisites-for-ios-enrollment"></a>iOS 註冊的必要條件
啟用 iOS 裝置之前，請先完成下列步驟：
- [設定 Intune](setup-steps.md) - 這些步驟會設定您的 Intune 基礎結構。 裝置註冊特別要求您[設定 MDM 授權單位](mdm-authority-set.md)。
- [取得 Apple MDM Push certificate](apple-mdm-push-certificate-get.md) - Apple 需要憑證才能管理 iOS 和 macOS 裝置。

## <a name="user-owned-ios-devices-byod"></a>使用者擁有的 iOS 裝置 (BYOD)

您可以讓使用者註冊其個人的裝置讓 Intune 管理，這稱為「攜帶您自己的裝置」或 BYOD。 當您完成必要條件及指派使用者授權之後，使用者即可從 App Store 下載 iOS 公司入口網站應用程式，並遵循應用程式中的註冊指示進行。

## <a name="company-owned-ios-devices"></a>公司擁有的 iOS 裝置
針對為使用者購買裝置的組織來說，Intune 可支援下列 iOS 公司擁有裝置的註冊方法：

- Apple 的裝置註冊計劃 (DEP)
- Apple School Manager
- Apple Configurator 設定助理註冊
- Apple Configurator 直接註冊

您也可以使用[裝置註冊管理員](device-enrollment-manager-enroll.md)帳戶，來註冊公司擁有的 iOS 裝置。

## <a name="device-enrollment-program"></a>裝置註冊方案
組織可以透過 Apple 的裝置註冊計劃 (DEP) 購買 iOS 裝置。 DEP 可以讓您在「線上」部署註冊設定檔，將裝置納入管理。 深入了解[裝置註冊計劃](device-enrollment-program-enroll-ios.md)。

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager 是針對學校提供的裝置採購暨註冊方案。 就像 DEP，您可以部署設定檔以註冊管理的裝置。 深入了解 [Apple School Manager](apple-school-manager-set-up-ios.md)。

## <a name="apple-configurator"></a>Apple Configurator
您可以使用 Apple Configurator 在 Mac 電腦上註冊 iOS 裝置。 若要準備裝置，請以 USB 連接它們並安裝註冊設定檔。 使用 Apple Configurator 註冊裝置的方法共有兩種：
- 設定助理註冊 - 將裝置重設為原廠設定，並將裝置備妥可執行設定助理，以及為裝置的新使用者安裝公司原則。
- 直接註冊 - 不會將裝置重設為原廠設定，並使用預先定義的原則來註冊裝置。 這個方法適用於無使用者親和性的裝置。

深入了解 [Apple Configurator 註冊](apple-configurator-setup-assistant-enroll-ios.md)。
