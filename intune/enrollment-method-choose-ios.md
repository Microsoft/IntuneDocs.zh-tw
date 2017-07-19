---
title: "選擇 iOS 裝置在 Intune 中的註冊方式"
titleSuffix: Intune on Azure
description: "了解如何在 Microsoft Intune 中設定 iOS 裝置註冊。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 092f582cf30210858bd8cdd3879edfa873523ccb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="choose-how-to-enroll-ios-and-macos-devices"></a>選擇 iOS 和 macOS 裝置的註冊方式

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主題描述 IT 系統管理員可用來在 Intune 中啟用 iOS 裝置註冊的方法。

您可以使用下列資訊決定註冊 iOS 裝置時所要使用的方法。 下列所有方法皆可用於註冊公司擁有的裝置，但 BYOD 除外。

**必要條件：**需要 [Apple 推播通知服務憑證](apple-mdm-push-certificate-get.md)。

## <a name="user-owned-ios-devices-byod"></a>使用者擁有的 iOS 裝置 (BYOD)

使用者若要註冊個人 BYOD (攜帶您自己的裝置) 裝置，可以從 App Store 下載 iOS 版的公司入口網站應用程式，並依照應用程式中的註冊指示。 一經註冊之後，使用者就能連線到公司網路、加入網域或 Azure Active Directory 及存取公司資源。 若要啟用 BYOD，唯一需要的是 [Apple 推播通知服務憑證](apple-mdm-push-certificate-get.md)。 您也可以封鎖註冊個人擁有的 iOS 裝置。 如需指示，請參閱[設定裝置類型限制](enrollment-restrictions-set.md)。

## <a name="user-owned-macos-devices-byod"></a>使用者擁有的 macOS 裝置 (BYOD)

您可以啟用 macOS 裝置註冊。 若要啟用 macOS 註冊，唯一需要的是 [Apple 推播通知服務憑證](apple-mdm-push-certificate-get.md)。 如需詳細資訊，請參閱[註冊 macOS 裝置](./macos-enroll.md)

## <a name="enrollment-program-with-apple"></a>Apple 的註冊方案
Apple 提供包含裝置註冊和管理基礎結構的裝置購買方案。 透過這些方案之一購買的裝置，可以經由指派用於 Intune 管理的裝置序號來進行「無線」大量註冊。

- **裝置註冊方案 (DEM)** - Apple 針對組織和企業提供的裝置註冊方案。 如需詳細資訊，請參閱[使用裝置註冊方案註冊 iOS 裝置](device-enrollment-program-enroll-ios.md)。
- **Apple School Manager** - Apple 針對學校提供的裝置註冊方案。 如需詳細資訊，請參閱[使用 Apple School Manager 啟用 iOS 裝置註冊](apple-school-manager-set-up-ios.md)

## <a name="apple-configurator"></a>Apple Configurator

您可以透過匯出公司註冊設定檔，然後將 iOS 裝置連線到執行 Apple Configurator 的 Mac 來註冊那些行動裝置。 Apple Configurator 支援兩種註冊方式：

- **設定助理註冊**：將裝置重設為原廠設定值，並準備好裝置以供裝置的新使用者進行設定。 此方法需要系統管理員透過 USB 將 iOS 裝置連接到執行 Apple Configurator 的 Mac 電腦來預先設定註冊。 裝置接著將會交給其使用者，使用者在第一次啟動裝置時會執行設定助理。 此程序會利用使用者的工作或學校憑證來設定裝置及完成註冊程序。 如需詳細資訊，請參閱[使用設定輔助程式的 Apple Configurator 註冊 iOS 裝置](apple-configurator-setup-assistant-enroll-ios.md)。

- **直接註冊**：建立 Apple Configurator 相容的檔案以供裝置期間使用。 註冊的裝置不會恢復出廠預設值，與使用者之間也不會有任何關係。 若要註冊裝置，透過 USB 將 iOS 裝置連接到執行 Apple Configurator 的 Mac 電腦。 如需詳細資訊，請參閱[使用 Apple Configurator 和直接註冊來註冊 iOS 裝置](apple-configurator-direct-enroll-ios.md)。

## <a name="use-the-device-enrollment-program-dep"></a>使用裝置註冊方案 (DEP)

DEP 會以「無線」的方式將設定檔部署到透過 DEP 購買的裝置上。 當使用者在裝置第一次啟動時執行設定助理之際，該裝置就會在 Intune 中註冊。 如需詳細資訊，請參閱[使用裝置註冊方案註冊 iOS 裝置](device-enrollment-program-enroll-ios.md)。

## <a name="use-the-device-enrollment-manager-dem"></a>使用裝置註冊管理員 (DEM)
裝置註冊管理員是一個一般性使用者帳戶，最多可以註冊及管理 1,000 部裝置。 DEM 管理的裝置無法具有使用者親和性，因此裝置永遠不會有擁有者。 您可以將 DEM 權限授與 Intune 使用者，讓他們能夠使用這些功能。 DEM 使用者註冊的每一部裝置皆會佔用一份 Intune 授權。 如需詳細資訊，請參閱[使用裝置註冊管理員註冊 iOS 裝置](device-enrollment-manager-enroll.md)。
