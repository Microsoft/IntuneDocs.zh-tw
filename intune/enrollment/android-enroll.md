---
title: 在 Intune 中註冊 Android 裝置
titleSuffix: Microsoft Intune
description: 了解如何在 Intune 中註冊 Android 裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 7/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a9de31ce7a08edcb7dddc6a65a061c1883021e4
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723589"
---
# <a name="enroll-android-devices"></a>註冊 Android 裝置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

身為 Intune 管理員，您可以下列方式註冊 Android 裝置：
- Android Enterprise (提供一組註冊選項，為使用者提供最新且最安全的功能)：
    - [**Android Enterprise 工作設定檔**](android-work-profile-enroll.md)：適用於獲授與存取公司資料之權限的個人裝置。 系統管理員可以管理公司帳戶、應用程式和資料。 裝置上的個人資料會與公司資料分開保存，系統管理員不會控制個人設定或資料。 
    - [**Android Enterprise 專用**](android-kiosk-enroll.md)：適用於屬公司擁有的單一使用裝置，例如數位招牌，票證列印或庫存管理。 系統管理員會針對一組有限的應用程式和 Web 連結鎖定裝置使用。 它也會防止使用者新增其他應用程式，或在裝置上採取其他動作。
    - [**Android Enterprise 完全受控**](android-fully-managed-enroll.md)：適用於屬公司擁有的單一使用者裝置，專門用於公司和非個人用途。 系統管理員可以管理整部裝置，並強制讓工作設定檔無法使用原則控制項。 
- [**Android 裝置系統管理員**](android-enroll-device-administrator.md)，包括 Samsung Knox Standard 裝置和 [Zebra 裝置](../configuration/android-zebra-mx-overview.md)。 

## <a name="prerequisites"></a>必要條件

若要準備管理行動裝置，您必須將行動裝置管理 (MDM) 授權單位設定為 **Microsoft Intune**。 請參閱[設定 MDM 授權單](../fundamentals/mdm-authority-set.md)以取得相關指示。 此項目只會設定一次，也就是第一次為行動裝置管理設定 Intune 之時。

針對斑馬技術公司 (Zebra Technologies) 製造的裝置，您可能需要根據特定裝置的功能，授與公司入口網站額外的權限。 [Zebra 裝置上的行動性延伸模組](../configuration/android-zebra-mx-overview.md)有更多詳細資料。

針對 Samsung Knox Standard 裝置，有[更多必要條件](android-samsung-knox-mobile-enroll.md)。

## <a name="next-steps"></a>後續步驟

- [設定 Android Enterprise 工作設定檔註冊](android-work-profile-enroll.md)
- [設定 Android Enterprise 專用裝置註冊](android-kiosk-enroll.md)
- [設定 Android Enterprise 完全受控註冊](android-fully-managed-enroll.md)
- [設定 Android 裝置系統管理員註冊](android-enroll-device-administrator.md)

