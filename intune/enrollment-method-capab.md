---
title: 適用於 Windows 裝置的 Intune 功能 (依註冊方法列出)
titlesuffix: Microsoft Intune
description: 了解每種註冊方法針對 Windows 裝置所支援的功能。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c9e440aef7f434cbe675506fd6f22a9bd26b2c31
ms.sourcegitcommit: 528d2bc70bfd25803a2d9f0fe9372c8a5f5e7dad
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446815"
---
# <a name="capabilities-by-enrollment-method-for-windows-devices"></a>適用於 Windows 裝置的功能 (依註冊方法列出)
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 可讓您管理員工的裝置與應用程式，以及員工存取公司資料的方式。 裝置必須先在 Intune 服務中註冊。 有數種方法可以註冊員工裝置。 每種方法都有不同的最佳做法和功能，如下表所示。

## <a name="best-practices-by-enrollment-method"></a>最佳做法 (依註冊方法列出)
| **最佳做法** | **[Azure AD 加入](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD 加入 (使用 Autopilot)](enrollment-autopilot.md)** |**[大量](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **GPO** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|常用於教育目的|![X](media/xmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|裝置可用作共用裝置|![X](media/xmark.png)|![X](media/xmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|個人裝置必須存取公司資源|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![核取記號](media/checkmark.png)|![X](media/xmark.png)|
|應用程式自助服務|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>功能 (依註冊方法列出)

| **功能** | **[Azure AD 加入](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD 加入 (使用 Autopilot)](enrollment-autopilot.md)** |**[大量](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **GPO** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|條件式存取                                      |![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|
|使用者與裝置建立關聯                    |![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|
|需要 Azure AD Premium                               |![X](media/xmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![核取記號](media/checkmark.png)|
|裝置可以評估 CA 所保護的資源             |![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![X](media/xmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|
|使用者不得為其裝置的系統管理員               |![X](media/xmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|能夠設定裝置設定體驗        |![X](media/xmark.png)|![核取記號](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|能夠在不需要使用者互動的情況下註冊裝置      |![X](media/xmark.png)|![X](media/xmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![X](media/xmark.png)|![核取記號](media/checkmark.png)|
|能夠執行 PowerShell 指令碼                       |![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)| 
|支援在 AD 網域加入之後自動註冊      |![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![核取記號](media/checkmark.png)|
|支援在混合式 Azure AD 加入之後自動註冊|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![核取記號](media/checkmark.png)|
|支援在 Azure AD 加入之後自動註冊       |![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![核取記號](media/checkmark.png)|![X](media/xmark.png)|

## <a name="next-steps"></a>接下來的步驟

[註冊選項](enrollment-options.md)

