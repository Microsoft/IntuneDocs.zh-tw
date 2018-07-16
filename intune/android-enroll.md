---
title: 在 Intune 中註冊 Android 裝置
titlesuffix: Microsoft Intune
description: 了解如何在 Intune 中註冊 Android 裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f03c60c12bfd759c738de50d320787bf4b85f99d
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909179"
---
# <a name="enroll-android-devices"></a>註冊 Android 裝置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

您身為 Intune 系統管理員，可管理下列 Android 裝置：
- Android 裝置，包括 Samsung Knox Standard 裝置。
- Android 企業裝置，包括 [Android 工作設定檔裝置](#enable-enrollment-of-android-for-work-devices)和 Android kiosk 裝置。

Intune 的多使用者管理支援執行 Samsung Knox Standard 的裝置。 這表示使用者可以利用他們的 Azure AD 認證登入和登出裝置。 裝置不論是否處於使用狀態，都是集中管理。 當使用者登入時，他們可以存取應用程式，此外也可以將任何原則套用到這些應用程式。 當使用者登出時，會清除所有應用程式資料。

## <a name="prerequisite"></a>必要條件

若要準備管理行動裝置，您必須將行動裝置管理 (MDM) 授權單位設定為 **Microsoft Intune**。 請參閱[設定 MDM 授權單](mdm-authority-set.md)以取得相關指示。 此項目只會設定一次，也就是第一次為行動裝置管理設定 Intune 之時。

## <a name="set-up-android-enrollment"></a>設定 Android 註冊

根據預設，Intune 允許註冊 Android 和 Samsung Knox Standard 裝置。 滿足必要條件之後，系統管理員只需要[告訴他們的使用者如何註冊其裝置](/intune-user-help/enroll-your-device-in-intune-android.md)。

使用者註冊之後，您就可以開始管理其在 Intune 中的裝置，包括[指派合規性原則](compliance-policy-create-android.md)、[管理應用程式](app-management.md)等等。

如需其他使用者工作的資訊，請參閱下列文章：

- [使用 Microsoft Intune 之使用者體驗的相關資源](end-user-educate.md)
- [搭配 Intune 使用您的 Android 裝置](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

若要封鎖 Android 裝置，或者僅封鎖註冊個人擁有的 Android 裝置，請參閱[Set device type restrictions](enrollment-restrictions-set.md) (設定裝置類型限制)。

## <a name="set-up-android-enterprise-enrollment"></a>設定 Android 企業註冊

Android 企業是一組 Android 裝置功能與服務，可將個人應用程式與資料和包含公司應用程式與資料的公司設定檔分隔開來。 Android 企業裝置，包括工作設定檔裝置和 kiosk 裝置。 

若要設定 Android 企業裝置的註冊，您必須先[將 Android 企業連線至 Intune](connect-intune-android-enterprise.md)。 完成此步驟之後，您可以：

[設定 Android 工作設定檔註冊](android-work-profile-enroll.md)
[設定　Android kiosk 註冊](android-kiosk-enroll.md)

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>註冊 Samsung Knox 裝置時的使用者體驗
註冊 Samsung Knox 裝置時，有數個考量：
-   即使沒有任何原則要求 PIN，裝置仍然必須至少有一個四位數的 PIN，才能註冊。 如果裝置沒有 PIN，系統就會提示使用者建立一個 PIN。
-   Workplace Join 憑證 (WPJ) 沒有任何使用者互動。
-   系統會向使用者提示「服務註冊」資訊及應用程式所能執行的動作。
-   系統會向使用者提示「Knox 註冊」資訊及 Knox 所能執行的動作。
-   如果實施「加密原則」，使用者就必須設定一個六字元複雜密碼來作為裝置密碼。
-   沒有任何額外的使用者提示來安裝服務針對「公司資源存取」推播的憑證。
- 有些舊版 Knox 裝置會提示使用者提供用於「公司資源存取」的額外憑證。
- 如果 Samsung Mini 裝置因發生**找不到憑證**或**無法註冊裝置**錯誤而無法安裝 WPJ，請安裝最新的「Samsung 韌體更新」。
