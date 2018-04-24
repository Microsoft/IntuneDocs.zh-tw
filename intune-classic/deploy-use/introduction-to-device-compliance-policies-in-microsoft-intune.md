---
title: 裝置相容性原則
description: 本主題說明什麼是裝置合規性政策，及其運作方式。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4c9c93d29ddee6d01e057c01a44c81950b857213
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="device-compliance-policies-in-microsoft-intune"></a>Microsoft Intune 的裝置相容性原則

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="what-is-a-compliance-policy"></a>什麼是合規性政策？
為協助保護公司資料，您必須確認用來存取公司應用程式及資料的裝置符合特定規則。 這些規則可能包括使用 PIN 來存取裝置，以及為裝置中儲存的資料加密。 這樣一組規則稱為合規性原則。

## <a name="how-should-i-use-compliance-policies"></a>應該如何使用合規性政策？
您可以搭配條件式存取原則使用合規性原則，只允許符合合規性原則規則的裝置存取電子郵件和其他服務。 若要了解如何搭配使用這兩個原則，請閱讀[限制存取電子郵件和 O365 服務](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)文章。

您也可以使用與條件式存取無關的合規性政策。 單獨使用合規性原則時，將會評估目標裝置，並回報其合規狀態。 例如，您可能想要報告有關未加密的裝置數目，或哪些裝置已進行破解或刷機。 不過，單獨使用合規性原則時，對公司資源沒有存取限制。

您可以將合規性政策部署到使用者。 將合規性政策部署到使用者時，即會檢查使用者裝置的相容性。
若要深入了解行動裝置在部署原則之後需要多長的時間才能取得原則，請參閱[管理裝置上的設定和功能](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#frequently-asked-questions-about-intune-policies)。

下表列出合規性原則所支援的裝置類型。 此表也描述如何在搭配條件式存取原則使用合規性原則時，管理不符合規範的設定。

-----------------------------

|原則設定| Windows 8.1 及更新版本| Windows Phone 8.1 和更新版本| iOS 8.0 和更新版本|Android 4.0 及更新版本<br/>Samsung Knox Standard 4.0 及更新版本|
|-----|----|----|----|----|
|**PIN 或密碼設定** |已修復|已修復|已修復|已隔離|
|**裝置加密**|不適用|已修復|已修復 (藉由設定 PIN 碼)|已隔離|
|**已越獄或 Root 的裝置**|不適用|不適用|隔離 (非設定)|隔離 (非設定)|
|**電子郵件設定檔**|不適用|不適用|已隔離|不適用|
|**最低 OS 版本**|已隔離|已隔離|已隔離|已隔離|
|**最高 OS 版本**|已隔離|已隔離|已隔離|已隔離|
|**Windows 健康情況證明**|已隔離：Windows 10 和 Windows 10 行動裝置版<br /><br />不適用：Windows 8.1|不適用|不適用|不適用|

------------------------------

**已補救** = 裝置作業系統強制符合規範。 (例如，強制使用者設定 PIN。)

**已隔離** = 裝置作業系統不強制符合規範。 (例如，Android 裝置不強制使用者為裝置加密。)裝置不相容時，會採取下列動作︰

-   如果對使用者套用了條件式存取原則，裝置會遭到封鎖。

-   公司入口網站會通知使用者任何合規性問題的相關事項。

## <a name="next-steps"></a>接下來的步驟
[建立裝置合規性原則](create-a-device-compliance-policy-in-microsoft-intune.md)

[部署和監視裝置合規性原則](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### <a name="see-also"></a>另請參閱
[限制存取電子郵件和 O365 服務](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
