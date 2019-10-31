---
title: Microsoft Intune 的應用程式生命週期概觀
description: 深入了解 Microsoft Intune 中的受控應用程式生命週期。 應用程式生命週期包括新增、部署、設定、保護及淘汰應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: apps; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 53425b56985cbafb4033b11df54597959c0b0d59
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72499716"
---
# <a name="overview-of-the-app-lifecycle-in-microsoft-intune"></a>Microsoft Intune 中的應用程式生命週期概觀

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

新增應用程式並進行其他階段時即開始 Microsoft Intune 應用程式生命週期，直到您將應用程式移除。 了解這些階段，您將具有在 Intune 中開始使用應用程式管理所需的詳細資料。

![](./media/app-lifecycle/app-lifecycle.png "Intune 應用程式生命週期")應用程式生命週期 - 新增、部署、設定、保護和淘汰。

## <a name="add"></a>新增

應用程式部署的第一個步驟是將您想要管理和指派的應用程式加入 Intune。 雖然您可以使用許多不同的應用程式類型，但基本程序都相同。 使用 Intune，您可以新增不同的應用程式類型，包括在內部撰寫的應用程式 (企業營運)、來自市集的應用程式、內建的應用程式，以及網路上的應用程式。 如需這些之中每一種應用程式類型的詳細資訊，請參閱[如何將應用程式新增至 Microsoft Intune](apps-add.md)。 

## <a name="deploy"></a>部署

在您將應用程式新增到 Intune 之後，可以接著[將它指派給使用者和您管理的裝置](apps-deploy.md)。 Intune 讓此程序非常簡易，並且在部署應用程式之後，您可以從 Azure 入口網站內的 Intune [監視部署成功](apps-monitor.md)。 此外，在某些應用程式市集中，例如 [Apple](vpp-apps-ios.md) 和 [Windows](windows-store-for-business.md) 應用程式市集，您可以為公司大量購買應用程式授權。 Intune 可以與這些市集同步處理資料，讓您可以直接從 Intune 管理主控台中部署和追蹤這些類型應用程式的授權使用情況。

## <a name="configure"></a>設定

隨著應用程式生命週期，會定期發佈新版本的應用程式。 Intune 提供工具，可輕鬆地[更新您已部署為新版本的應用程式](apps-add.md)。 此外，您可以設定某些應用程式的額外功能，例如︰
- [iOS 應用程式設定原則](app-configuration-policies-use-ios.md)提供執行應用程式時所使用之相容 iOS 應用程式的設定。 例如，應用程式可能需要特定品牌設定或它必須連線之伺服器的名稱。
- [受管理的瀏覽器原則](app-configuration-managed-browser.md)可協助您設定 Intune 受管理瀏覽器的設定，其會取代預設的裝置瀏覽器，並可讓您限制使用者可以瀏覽的網站。

## <a name="protect"></a>保護

Intune 提供您許多方法來協助保護您的應用程式中的資料。 主要方法如下︰
- [條件式存取](../protect/conditional-access.md)，它會根據您指定的條件來控制電子郵件及其他服務的存取權。 條件包括裝置類型或遵循您部署的[裝置相容性原則](../protect/device-compliance-get-started.md)。
- [應用程式保護原則](app-protection-policy.md)適用於個別的應用程式，可協助保護它們使用的公司資料。 例如，您可以限制在未受管理的應用程式與您管理的應用程式之間複製資料，或是可以防止應用程式在已進行 JB 或 Root 破解的裝置上執行。

## <a name="retire"></a>淘汰

最後，您部署的應用程式很可能會過時，因此必須移除。 Intune 可讓您輕鬆地[從服務淘汰應用程式](../remote-actions/device-management.md)。

## <a name="next-steps"></a>後續步驟

- 深入了解 [Microsoft Intune 應用程式管理](app-management.md)
