---
title: 在 Intune 中註冊 Android 裝置
titlesuffix: Microsoft Intune
description: 了解如何在 Intune 中註冊 Android 裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 3d86afec4e501533ab0048e866969a5bf73c2c57
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2019
ms.locfileid: "54387055"
---
# <a name="enroll-android-devices"></a>註冊 Android 裝置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

您身為 Intune 系統管理員，可管理下列 Android 裝置：
- Android 裝置，包括 Samsung Knox Standard 裝置。
- Android 企業裝置，包括：
    - **Android 工作設定檔裝置**：個人裝置獲授與存取公司資料的權限。 系統管理員可以管理公司帳戶、應用程式和資料。 裝置上的個人資料會與公司資料分開保存，系統管理員不會控制個人設定或資料。 
    - **Android 專用裝置**：屬公司擁有的單一使用裝置，例如數位招牌，票證列印或庫存管理。 系統管理員會針對一組有限的應用程式和 Web 連結鎖定裝置使用。 它也會防止使用者新增其他應用程式，或在裝置上採取其他動作。
    - **Android 完全受控裝置**：公司擁有的單一使用者裝置，專門用於公司和非個人用途。 系統管理員可以管理整部裝置，並強制讓工作設定檔無法使用原則控制項。 

## <a name="prerequisite"></a>必要條件

若要準備管理行動裝置，您必須將行動裝置管理 (MDM) 授權單位設定為 **Microsoft Intune**。 請參閱[設定 MDM 授權單](mdm-authority-set.md)以取得相關指示。 此項目只會設定一次，也就是第一次為行動裝置管理設定 Intune 之時。

## <a name="set-up-android-enrollment"></a>設定 Android 註冊

根據預設，Intune 允許註冊 Android 和 Samsung Knox Standard 裝置。 滿足必要條件之後，系統管理員只需要[告訴他們的使用者如何註冊其裝置](/intune-user-help/enroll-your-device-in-intune-android)。

使用者註冊之後，您就可以開始管理其在 Intune 中的裝置，包括[指派合規性原則](compliance-policy-create-android.md)、[管理應用程式](app-management.md)等等。

如需其他使用者工作的資訊，請參閱下列文章：

- [使用 Microsoft Intune 之使用者體驗的相關資源](end-user-educate.md)
- [搭配 Intune 使用您的 Android 裝置](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

若要封鎖 Android 裝置，或者僅封鎖註冊個人擁有的 Android 裝置，請參閱[Set device type restrictions](enrollment-restrictions-set.md) (設定裝置類型限制)。

## <a name="set-up-android-enterprise-enrollment"></a>設定 Android 企業註冊

Android 企業是一組 Android 裝置功能與服務，可將個人應用程式與資料和包含公司應用程式與資料的公司設定檔分隔開來。 Android 企業裝置，包括工作設定檔裝置和完全受控裝置，以及專用裝置。 

- [設定 Android 工作設定檔註冊](android-work-profile-enroll.md)
- [設定 Android 專用裝置註冊](android-kiosk-enroll.md)
- [設定 Android 完全受控註冊](android-fully-managed-enroll.md)

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>註冊 Samsung Knox 裝置時的使用者體驗

Intune 支援 Samsung Knox Standard 裝置進行多使用者管理。 這表示使用者可以利用他們的 Azure AD 認證登入和登出裝置。 裝置不論是否處於使用狀態，都是集中管理。 當使用者登入時，他們可以存取應用程式，此外也可以將任何原則套用到這些應用程式。 當使用者登出時，就會清除所有應用程式資料。

註冊 Samsung Knox 裝置時，有數個考量：
-   即使沒有任何原則要求 PIN，裝置仍然必須至少有一個四位數的 PIN，才能註冊。 如果裝置沒有 PIN，系統就會提示使用者建立一個 PIN。
-   Workplace Join 憑證 (WPJ) 沒有任何使用者互動。
-   系統會向使用者提示「服務註冊」資訊及應用程式所能執行的動作。
-   系統會向使用者提示「Knox 註冊」資訊及 Knox 所能執行的動作。
-   如果實施「加密原則」，使用者就必須設定一個六字元複雜密碼來作為裝置密碼。
-   沒有任何額外的使用者提示來安裝服務針對「公司資源存取」推播的憑證。
- 有些舊版 Knox 裝置會提示使用者提供用於「公司資源存取」的額外憑證。
- 如果 Samsung Mini 裝置因發生**找不到憑證**或**無法註冊裝置**錯誤而無法安裝 WPJ，請安裝最新的「Samsung 韌體更新」。

## <a name="next-steps"></a>後續步驟

- [設定 Android 工作設定檔註冊](android-work-profile-enroll.md)
- [設定 Android 專用裝置註冊](android-kiosk-enroll.md)
- [設定 Android 完全受控註冊](android-fully-managed-enroll.md)
