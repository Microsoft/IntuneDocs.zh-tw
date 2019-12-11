---
title: Microsoft Intune 所管理裝置的註冊選項
titleSuffix: ''
description: 系統管理員可針對 Microsoft Intune 所管理裝置來設定的註冊選項清單。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: cf4ad6d4-423f-4826-ab8d-6eb7a7cfb559
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b8c502bd42d3290bd03c0ce954d55de3073c3f2d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503209"
---
# <a name="enrollment-options-for-devices-managed-by-intune"></a>Intune 所管理裝置的註冊選項

身為 Intune 管理員，您可以設定裝置註冊，協助使用者並啟用 Intune 的功能。  Intune 包含下列註冊選項：

## <a name="terms-and-conditions"></a>條款及條件

您可以要求使用者必須先接受公司的條款及條件，然後才能使用公司入口網站來註冊他們的裝置並存取資源 (例如公司應用程式和電子郵件)。 條款及條件的設定是選擇性的。 深入了解[條款及條件](terms-and-conditions-create.md)。

## <a name="enrollment-restrictions"></a>註冊限制

您可以選擇限制裝置註冊的條件：
- 裝置平台
- 每位使用者的裝置數目
- 封鎖個人裝置

深入了解[註冊限制](enrollment-restrictions-set.md)。

## <a name="enable-apple-device-enrollment"></a>啟用 Apple 裝置註冊

需有 MDM Push Certificate 才能註冊 iOS 和 Mac 裝置。 深入了解 [MDM Push Certificates](apple-mdm-push-certificate-get.md)。

## <a name="corporate-identifiers"></a>公司識別碼

您可以列出國際行動設備識別碼 (IMEI) 編號及序號，以識別公司擁有的裝置。 深入了解[公司識別碼](corporate-identifiers-add.md)。
## <a name="multi-factor-authentication"></a>[Multi-Factor Authentication]

您可以要求使用者在註冊裝置時使用其他驗證方法，例如電話、PIN 或生物特徵辨識資料。 深入了解[多重要素驗證](multi-factor-authentication.md)。

## <a name="device-enrollment-manager"></a>裝置註冊管理員
指派使用者擔任裝置註冊管理員。  DEM 使用者可以使用單一使用者帳戶來註冊大量的行動裝置。 裝置註冊管理員 (DEM) 帳戶最多可以註冊 1,000 部裝置。 深入了解[裝置註冊管理員](device-enrollment-manager-enroll.md)。

## <a name="device-categories"></a>裝置類別

您可以根據您定義的類別，使用裝置類別自動新增裝置。 將裝置依群組分門別類，可以更輕鬆地管理這些裝置。 深入了解[裝置類別](device-group-mapping.md)。
