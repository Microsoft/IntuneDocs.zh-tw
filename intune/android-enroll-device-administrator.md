---
title: Microsoft Intune 中的 Android 裝置系統管理員註冊
titleSuffix: ''
description: 使用裝置系統管理員註冊，在 Intune 中註冊 Android 裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1dc495e6356a35215943415e03a46496a72bddf1
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071039"
---
# <a name="android-device-administrator-enrollment"></a>Android 裝置系統管理員註冊

Android 裝置系統管理員 (有時稱為「舊版」的 Android 管理，而且隨 Android 2.2 發行) 是一種管理 Android 裝置的方式。 不過，您現在可以在 [Android Enterprise](https://www.android.com/enterprise/management/) \(隨 Android 5.0 發行\) 中找到已改善的管理功能。 為了要移到現代化、更豐富且更安全的裝置管理，Google 在新的 Android 版本中減少了裝置系統管理員的支援。

因此，為了避免這種功能降低的情況，我們建議您不要使用下面所述的裝置系統管理員程序來註冊新裝置。

基於相同的理由，我們也建議您在裝置要更新為 Android 10 時，將裝置從裝置系統管理員管理中移轉。 

如需 Android 裝置系統管理員之 Intune 支援的詳細資訊，請參閱[注意事項](whats-new.md#decreasing-support-for-android-device-administrator)一節。

如果您仍決定讓使用者使用裝置系統管理員管理來註冊其 Android 裝置，請繼續閱讀下一節。  


> [!Note]  
> 混合式行動裝置管理 (混合式 MDM；使用 System Center Configuration Manager 主控台管理的 Intune) 不支援 Android 10 與更新版本，因為混合式 MDM 將在 2019 年 9 月 1 日終止服務。 如果您仍在使用混合式 MDM，您應該儘快移轉到 Intune 獨立部署。 若您需要移轉方面的協助，請連絡客戶支援。 如需詳細資訊，請參閱 [Move from Hybrid Mobile Device Management to Intune on Azure](https://aka.ms/hybrid_notification) (從混合式行動裝置管理移到 Azure 上的 Intune)。

如需 Google 的 Android Enterprise 功能的詳細資訊。請參閱下列文章：
- [Google 從裝置系統管理員移轉到 Android Enterprise 指南](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf) \(英文\)
- [Google 裝置系統管理員 API 過時因應措施文件](https://developers.google.com/android/work/device-admin-deprecation) \(英文\)


## <a name="set-up-device-administrator-enrollment"></a>設定 Android 裝置系統管理員註冊

Intune 預設允許使用裝置系統管理員功能來註冊 Android 裝置。

1. 若要準備管理行動裝置，您必須將行動裝置管理 (MDM) 授權單位設定為 **Microsoft Intune**。 請參閱[設定 MDM 授權單](mdm-authority-set.md)以取得相關指示。 此項目只會設定一次，也就是第一次為行動裝置管理設定 Intune 之時
2. [請告知使用者如何註冊其裝置](/intune-user-help/enroll-your-device-in-intune-android)。  

使用者註冊之後，您就可以開始管理其在 Intune 中的裝置，包括[指派合規性原則](compliance-policy-create-android.md)、[管理應用程式](app-management.md)等等。

如需其他使用者工作的資訊，請參閱下列文章：
- [使用 Microsoft Intune 之使用者體驗的相關資源](end-user-educate.md)
- [搭配 Intune 使用您的 Android 裝置](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)


## <a name="block-device-administrator-enrollment"></a>封鎖裝置系統管理員註冊
若要封鎖 Android 裝置系統管理員裝置，或僅禁止註冊個人擁有的 Android 裝置系統管理員裝置，請參閱[設定裝置類型限制](enrollment-restrictions-set.md)。



## <a name="next-steps"></a>後續步驟
- [指派合規性政策](compliance-policy-create-android.md)
- [管理應用程式](app-management.md)