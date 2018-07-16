---
title: 在 Intune 中註冊 Android 工作設定檔裝置
titlesuffix: Microsoft Intune
description: 了解如何在 Intune 中註冊 Android 工作設定檔裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 095985bad8f7e35a953383fcce8296716723b8bc
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909060"
---
# <a name="set-up-enrollment-of-android-work-profile-devices"></a>設定 Android 工作設定檔裝置的註冊

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 可協助您將應用程式和設定部署到 Android 工作設定檔裝置，以確保公司及個人資訊各自分開。 如需 Android 企業的特定詳細資料，請參閱 [Android 企業需求](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)。

若要設定 Android 工作設定檔管理，請遵循下列步驟：

1. [將 Intune 租用戶帳戶連線至 Android 企業帳戶](connect-intune-android-enterprise.md)。
2. 指定 Android 工作設定檔註冊設定。 [只有特定 Android 裝置才支援](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22) Android 工作設定檔。 支援 Android 工作設定檔的所有裝置也會支援傳統 Android 管理。 Intune 可讓您指定應如何從[註冊限制](enrollment-restrictions-set.md)管理支援 Android 工作設定檔的裝置。
    - **封鎖 (預設設定)**：所有 Android 裝置 (包括支援 Android 工作設定檔的裝置) 都會註冊為傳統 Android 裝置。
    - **允許**：所有支援 Android 工作設定檔的裝置都會註冊為 Android 工作設定檔裝置。 不支援 Android 工作設定檔的任何 Android 裝置會註冊為傳統 Android 裝置。
3. [請告知使用者如何註冊其裝置](/intune-user-help/enroll-your-device-in-intune-android.md)。


若要在 Android 工作設定檔中註冊裝置，但先前已將那些裝置註冊為一般 Android 裝置，則必須先取消註冊那些裝置，再予以重新註冊。

若要使用[裝置註冊管理員](device-enrollment-manager-enroll.md)帳戶註冊 Android 工作設定檔裝置，每個帳戶只能註冊 10 部裝置。

如需詳細資訊，請參閱 [Intune 傳送至 Google 的資料](data-intune-sends-to-google.md)。

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>在受控的 Google Play 商店中核准公司入口網站應用程式

為了確保使用者一律會存取最新版本的公司入口網站應用程式，您必須在受控 Google Play 商店中核准 Android 版的公司入口網站應用程式。 藉由核准它，您可確定每個使用者都會取得自動更新項目。 如果不核准，公司入口網站最後會過時，不能接收 Microsoft 發行的重要 Bug) 修正或新功能。

請遵循下列步驟核准 Intune 公司入口網站：

1.  在[受控 Google Play 商店](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal)中瀏覽到公司入口網站應用程式。
2.  以設定 Android 企業繫結的相同 Google 帳戶，登入受控 Google Play 商店。
3.  按一下 [核准]隨即開啟一個新的對話方塊。
4.  檢閱此對話方塊中的權限，然後按一下 [核准]。 您需要允許這些權限，才能讓公司入口網站應用程式管理裝置上的工作設定檔。
5.  選取 [Keep approved when app requests new permissions] (當應用程式要求新權限時，保留已核准的權限)，然後按一下 [儲存]。

## <a name="next-steps-for-android-work-profiles"></a>Android 工作設定檔的後續步驟
- [部署 Android 工作設定檔應用程式](store-apps-android.md)
- [新增 Android 工作設定檔設定原則](device-profiles.md)