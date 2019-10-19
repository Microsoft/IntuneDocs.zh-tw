---
title: 舊版 Intune 電腦用戶端及 Azure 上的 Intune
description: 在 Azure 上使用 Intune 來管理貴組織的 Windows 裝置時的考量。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.assetid: 1f104923-12df-453c-9c20-942ef65a0945
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5ab1be3d34d52e824d1ff06124e28206fb7b07a1
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72510181"
---
# <a name="intune-on-azure-console-and-legacy-intune-pc-client"></a>Azure 上的 Intune 主控台及舊版 Intune 電腦用戶端

Intune 使用以 Azure 為基礎的 SaaS 應用程式服務架構。 Azure 在規模、容量和效能方面提供了重要改良。 這可在 Azure 入口網站中提供更強的 Intune 系統管理員體驗及最佳化的工作流程。 

在 Azure 上使用 Intune 來管理貴組織的 Windows 裝置時，請考量下列各點：

## <a name="manage-windows-10-devices-by-using-mdm"></a>使用 MDM 管理 Windows 10 裝置

我們建議您改為使用[行動裝置管理 (MDM) 來管理 Windows 10 裝置](../configuration/device-restrictions-windows-10.md)，而不是使用舊版 Intune 電腦用戶端。 Azure 入口網站上的 Intune 提供了使用 MDM 管理 Windows 10 的能力。 Windows 10 MDM 提供了許多新的管理和安全性功能，這些功能在舊版 Intune 電腦用戶端中不提供。

## <a name="legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>舊版電腦用戶端功能只在 Silverlight 主控台中提供

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune 電腦用戶端管理工作流程使用 [ Silverlight 型 Intune 系統管理主控台](https://manage.microsoft.com/)，其具有下列結果：

- 針對使用 Intune 電腦用戶端的所有非群組管理工作，您必須使用 Silverlight 主控台。
- 在管理群組時，您必須[在 Azure 入口網站上使用 Intune](https://portal.azure.com/)。 因為 Intune 現在會使用 Azure AD 群組而非舊版 Intune 群組，因此有這項要求。 

由於切換到 Azure AD 群組，Silverlight 主控台儀表板檢視中的「以群組為基礎」篩選已稍微變更。 若要在更新的 Silverlight UI 中進行篩選，請遵循下列步驟：

1. 選取檢視。
2. 在 [篩選]  方塊中，輸入您要據以篩選的群組名稱，然後按 Enter。 這會篩選清單檢視，只顯示該特定群組中的裝置。

   ![篩選下拉式清單輸入，並選取 [無]](./media/intune-legacy-pc-client/image01.png)


## <a name="continue-to-manage-windows-7-by-using-intune-pc-client"></a>繼續使用 Intune 電腦用戶端管理 Windows 7

針對無法使用 MDM 管理的 Windows 7，我們會僅在 Silverlight 主控台中繼續支援現有的 Intune 電腦用戶端功能。 當您升級到 Windows 10 時，請考慮移轉至 MDM 管理。

## <a name="mdm-capabilities"></a>MDM 功能

有關電腦用戶端和 MDM 功能之間的詳細比較，請參閱[比較作為電腦或行動裝置來管理 Windows 電腦](pc-management-comparison.md)。 MDM 更新將繼續為註冊 MDM 的 Windows 10 裝置帶來新的管理功能，包含評估 Win 32 應用程式的選項。 查看[新增功能](whats-new.md)，了解服務最新版本的新增功能。

## <a name="switch-from-pc-client-to-mdm"></a>從電腦用戶端切換到 MDM

要從使用 Intune 電腦用戶端管理 Windows 10 裝置切換到使用 MDM 進行管理，請遵循下列步驟：

1. 在 Silverlight 主控台中，執行 [選擇性抹除]  將裝置從電腦用戶端取消註冊。
  ![Warning 快顯，並選取 [選擇性抹除裝置] 選項按鈕 ](./media/intune-legacy-pc-client/image02.png)
2. 使用 [MDM (和/或 Azure AD Join)](../enrollment/windows-enroll.md) 重新註冊該裝置。

## <a name="next-steps"></a>後續步驟
[註冊 Windows 裝置](../enrollment/windows-enroll.md)
