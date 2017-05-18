---
title: "應用程式生命週期概觀 | Microsoft Docs"
description: "深入了解從新增 Intune 管理的應用程式，到它們最終淘汰的生命週期。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: c3394663b234ada70f724b750dfdffc8369cb203
ms.lasthandoff: 12/30/2016


---

# <a name="overview-of-the-app-lifecycle"></a>應用程式生命週期的概觀

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

加入應用程式並進行其他階段時即開始 Intune 應用程式生命週期，直到您將應用程式移除。

![應用程式生命週期](./media/app-lifecycle.png "Intune 應用程式生命週期")

## <a name="add"></a>新增

應用程式部署的第一個步驟是將您想要管理和部署的應用程式加入 Intune 。 雖然您可以使用許多不同的應用程式類型，但基本程序都相同。 使用 Intune，您可以同時為[註冊的裝置](add-apps-for-mobile-devices-in-microsoft-intune.md)和[使用 Intune 用戶端軟體管理的 Windows 電腦](add-apps-for-windows-pcs-in-microsoft-intune.md)新增應用程式。

## <a name="deploy"></a>部署

在您將應用程式加入 Intune 之後，您可以接著[將它部署到您管理的裝置](deploy-apps.md)。 Intune 讓此程序非常簡易，並且在部署應用程式之後，您可以從 Intune 管理主控台[監視部署成功](monitor-apps-in-microsoft-intune.md)。 此外，在某些應用程式市集中，例如 [Apple](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md) 和 [Windows](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md) 應用程式市集，您可以為公司大量購買應用程式授權。 Intune 可以與這些市集同步處理資料，讓您可以直接從 Intune 管理主控台中部署和追蹤這些類型應用程式的授權使用情況。

## <a name="configure"></a>設定

隨著應用程式生命週期，會定期發佈新版本的應用程式。 Intune 提供工具，可輕鬆地[更新您已部署為新版本的應用程式](update-apps-using-microsoft-intune.md)。 此外，您可以設定某些應用程式的額外功能，例如︰
- [iOS 應用程式設定原則](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md)提供執行應用程式時所使用之相容 iOS 應用程式的設定。 例如，應用程式可能需要特定的商標設定或伺服器的名稱才能連接。
- [受管理的瀏覽器原則](manage-internet-access-using-managed-browser-policies.md)可協助您設定 Intune 受管理瀏覽器的設定，其會取代預設的裝置瀏覽器，並可讓您限制使用者可以瀏覽的網站。

## <a name="protect"></a>保護

Intune 提供您許多方法來協助保護您的應用程式中的資料。 主要方法如下︰
- [條件式存取](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)根據您指定之條件，控制電子郵件及其他服務的存取權。 條件包括裝置類型或遵循您部署的[裝置相容性原則](introduction-to-device-compliance-policies-in-microsoft-intune.md)。
- [行動應用程式管理 (MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md) 適用於個別的應用程式，可協助保護他們使用的公司資料。 例如，您可以限制在未受管理的應用程式與您管理的應用程式之間複製資料，或是可以防止應用程式在已進行 JB 或 Root 破解的裝置上執行。

## <a name="retire"></a>淘汰

最後，您部署的應用程式很可能會過時，因此必須移除。 Intune 可讓您輕鬆地[從服務淘汰應用程式](retire-apps-using-microsoft-intune.md)。

