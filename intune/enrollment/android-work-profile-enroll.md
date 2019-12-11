---
title: 在 Intune 中註冊 Android Enterprise 工作設定檔裝置
titleSuffix: Microsoft Intune
description: 了解如何在 Intune 中註冊 Android Enterprise 工作設定檔裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4339f98ed133c3426faee8bd4b18024fd2648606
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503344"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>設定 Android Enterprise 工作設定檔裝置的註冊

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 可協助您將應用程式和設定部署到 Android Enterprise 工作設定檔裝置，以確保公司及個人資訊各自分開。 如需 Android Enterprise 的特定詳細資料，請參閱 [Android Enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Android Enterprise 需求)。

若要設定 Android Enterprise 工作設定檔管理，請遵循下列步驟：

1. [將 Intune 租用戶帳戶連線至 Android Enterprise 帳戶](connect-intune-android-enterprise.md)。
2. 指定 Android Enterprise 工作設定檔註冊設定。 [只有特定 Android 裝置才支援](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22) Android Enterprise 工作設定檔。 支援 Android Enterprise 工作設定檔的所有裝置，也支援 Android 裝置系統管理員管理。 Intune 可讓您指定應如何從[註冊限制](enrollment-restrictions-set.md)管理支援 Android Enterprise 工作設定檔的裝置。
    - **封鎖**：除非 Android 裝置系統管理員註冊也遭到封鎖，否則，所有 Android 裝置 (包括支援 Android Enterprise 工作設定檔的裝置) 都將註冊為 Android 裝置系統管理員裝置。 
    - **允許 (預設設定)** ：所有支援 Android Enterprise 工作設定檔的裝置都會註冊為 Android Enterprise 工作設定檔裝置。 除非 Android 裝置系統管理員註冊遭到封鎖，否則，所有不支援 Android Enterprise 工作設定檔的 Android 裝置都會註冊為 Android 裝置系統管理員裝置。 
> [!NOTE]
> 自 2019 年 7 月起，新租用戶的預設設定為 [允許]  。 所有先前的租用戶都將體驗不對其註冊限制進行任何變更，而且將看到他們在註冊限制中所設定的任何原則。 對於不曾進行任何註冊限制變更的先前租用戶，[封鎖]  仍將是 Android Enterprise 工作設定檔的預設值。

3. [請告知使用者如何註冊其裝置](/intune-user-help/create-a-work-profile-and-enroll-your-device-in-intune-android)。  

如果您要使用 Android Enterprise 工作設定檔來註冊裝置，但先前已向 Android 裝置系統管理員註冊那些裝置，則必須先將那些裝置取消註冊，再予以重新註冊。
> [!NOTE]
> 身為系統管理員，您可以使用 [淘汰]  功能，從遠端完成此作業。 從 [所有裝置]  刀鋒視窗中選取裝置之後，即可在 [動作] 功能表中找到此功能。

若要使用[裝置註冊管理員](device-enrollment-manager-enroll.md)帳戶註冊 Android Enterprise 工作設定檔裝置，每個帳戶只能註冊 10 部裝置。

如需詳細資訊，請參閱 [Intune 傳送至 Google 的資料](../protect/data-intune-sends-to-google.md)。

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Android Enterprise 工作設定檔的後續步驟
- [部署 Android Enterprise 工作設定檔應用程式](../apps/apps-add-android-for-work.md)
- [新增 Android Enterprise 工作設定檔設定原則](../configuration/device-profiles.md)

## <a name="see-also"></a>請參閱

[在 Microsoft Intune 中對 Android Enterprise 裝置進行設定及疑難排解](https://support.microsoft.com/help/4476974)
