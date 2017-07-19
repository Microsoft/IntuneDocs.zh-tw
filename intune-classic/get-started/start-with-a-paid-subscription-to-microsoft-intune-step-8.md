---
title: "啟用裝置註冊"
description: "設定 MDM 授權單位並啟用對 iOS、Windows、Android 和 Mac 裝置的註冊。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 64c6eb58246ac3ad232c1b8ee89d12a83e7e1784
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="enable-enrollment-for-mobile-devices"></a>啟用行動裝置的註冊

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主題描述 Intune 系統管理員如何啟用行動裝置註冊。 如需在手機上使用 Intune 的協助，請參閱 [Using managed devices to get work done](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions) (使用受管理的裝置完成工作)。

若要使用 Intune 設定行動裝置管理，您必須先設定*行動裝置管理授權單位*，以識別可管理與您帳戶相關聯之裝置的服務。 本指南假設您將使用 Intune 服務，而不是 System Center Configuration Manager。 一旦設定 MDM 授權單位之後，您就能啟用裝置平台的管理，並使用公司入口網站應用程式註冊您的裝置。

## <a name="enable-device-enrollment"></a>啟用裝置註冊

1. **讓 Intune 成為您的行動裝置管理授權單位** 在 [Intune 管理主控台][](https://manage.microsoft.com/) 中，選擇 [系統管理] > [行動裝置管理]，然後選擇 [工作] 下方的 [設定 MDM 授權單位]。  

2. 在 [MDM 授權單位] 對話方塊中，選擇 [是]。

    ![管理主控台。 將 mdm 設為 Intune](../media/intune-mdm-authority.png)

## <a name="choose-how-to-enroll-devices"></a>選擇註冊裝置的方式

Intune 可根據貴公司的需求，使用各種不同方式來管理裝置。 「攜帶您自己的裝置」(BYOD)、屬公司擁有的裝置、「選擇您自己的裝置」(CYOD)，以及 Kiosk 模式的裝置只是幾個可用的註冊案例。

請依照下列步驟來[選擇註冊裝置的方式](choose-how-to-enroll-devices1.md)。

## <a name="enable-mdm-for-your-device-platform"></a>針對您的裝置平台啟用 MDM
您必須針對 iOS、Mac 及 Android for Work 裝置啟用註冊，在平台提供者與您的 Intune 租用戶之間建立關聯性。 Windows 和 Android 裝置不需要額外的步驟，但針對 Windows 裝置，您可以藉由為使用者建立特殊的 DNS 登錄項目來簡化裝置註冊。

針對您想要管理的裝置平台啟用裝置註冊。 依您的平台而異，需要使用不同的需求：

- [iOS 和 macOS](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
- [Window 10 及 Windows Phone](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune)
- [Window 電腦](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune) (Intune 軟體用戶端)
- [Android for Work](/intune-classic/deploy-use/set-up-android-for-work)

註冊啟用之後，使用者可以將公司入口網站應用程式下載至其裝置，並完成裝置註冊程序。

### <a name="enable-company-owned-device-enrollment"></a>啟用屬公司擁有的裝置註冊
您也可以啟用各種不同的[屬公司擁有的裝置註冊](/intune-classic/deploy-use/manage-corporate-owned-devices)案例，包括：
- [Apple 裝置註冊方案](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)
- [Apple Configurator 設定助理註冊](/intune-classic/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)
- [Apple Configurator 直接註冊](/intune-classic/deploy-use/ios-direct-enrollment-in-microsoft-intune)
- [裝置註冊管理員](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

### <a name="next-steps"></a>後續步驟
恭喜！ 您剛完成 *Intune 快速入門指南*的最後一個步驟。 在您完成初始設定之後，您可以考慮啟用其他 MDM 功能。

>[!div class="step-by-step"]
>[&larr; **註冊裝置**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)     [**設定後的工作** &rarr;](.\post-configuration-tasks.md)  
