---
title: 在 Azure 上使用 Intune 管理 Windows 裝置時的考量
description: 在 Azure 上使用 Intune 來管理貴組織的 Windows 裝置時的考量。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 71effb587bfb82ecae18afda67b05fffd2127052
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="intune-on-azure-console-and-legacy-intune-pc-client"></a>Azure 主控台上的 Intune 和電腦用戶端上的舊版 Intune

Intune 最近移至 Azure 型 SaaS 應用程式服務架構。 Azure 在規模、容量和效能方面提供了重要改良。 這項轉換也會在 Azure 入口網站中提供增強型的 Intune 系統管理體驗和最佳化的工作流程。 

在 Azure 上使用 Intune 來管理貴組織的 Windows 裝置時，請考量下列各點：

## <a name="legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>舊版電腦用戶端功能只在 Silverlight 主控台中提供

Intune 電腦用戶端管理工作流程使用 [ Silverlight 型 Intune 系統管理主控台](https://manage.microsoft.com/)，其具有下列結果：

- 針對使用 Intune 電腦用戶端的所有非群組管理工作，您必須使用 Silverlight 主控台。
- 在管理群組時，您必須[在 Azure 入口網站上使用 Intune](https://portal.azure.com/)。 因為 Intune 現在會使用 Azure AD 群組而非舊版 Intune 群組，因此有這項要求。 

由於切換到 Azure AD 群組，Silverlight 主控台儀表板檢視中的「以群組為基礎」篩選已稍微變更。 若要在更新的 Silverlight UI 中進行篩選，請遵循下列步驟：

1. 選取檢視。
2. 在 [篩選] 方塊中，輸入您要據以篩選的群組名稱，然後按 Enter。 這會篩選清單檢視，只顯示該特定群組中的裝置。

   ![](media/intune_on_azure/image01.png)

## <a name="manage-windows-10-devices-by-using-mdm"></a>使用 MDM 管理 Windows 10 裝置

我們建議您改為使用[行動裝置管理 (MDM) 來管理 Windows 10 裝置](https://docs.microsoft.com/intune/device-restrictions-windows-10)，而不是使用舊版 Intune 電腦用戶端。 Azure 入口網站上的 Intune 提供了使用 MDM 管理 Windows 10 的能力。 Windows 10 MDM 提供了許多新的管理和安全性功能，這些功能在舊版 Intune 電腦用戶端中不提供。

## <a name="continue-to-manage-windows-7-by-using-intune-pc-client"></a>繼續使用 Intune 電腦用戶端管理 Windows 7

針對無法使用 MDM 管理的 Windows 7，我們會僅在 Silverlight 主控台中繼續支援現有的 Intune 電腦用戶端功能。 當您升級到 Windows 10 時，請考慮移轉至 MDM 管理。

## <a name="mdm-capabilities"></a>MDM 功能

有關電腦用戶端和 MDM 功能之間的詳細比較，請參閱[比較作為電腦或行動裝置來管理 Windows 電腦](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison)。 MDM 更新將繼續為註冊 MDM 的 Windows 10 裝置帶來新的管理功能，包含評估 Win 32 應用程式的選項。 查看[新增功能](https://docs.microsoft.com/intune/whats-new)，了解服務最新版本的新增功能。

## <a name="switch-from-pc-client-to-mdm"></a>從電腦用戶端切換到 MDM

要從使用 Intune 電腦用戶端管理 Windows 10 裝置切換到使用 MDM 進行管理，請遵循下列步驟：

1. 在 Silverlight 主控台中，執行 [選擇性抹除] 將裝置從電腦用戶端取消註冊。
  ![](media/intune_on_azure/image02.png)
2. 使用 [MDM (和/或 Azure AD Join)](https://docs.microsoft.com/intune/windows-enroll) 重新註冊該裝置。 

## <a name="next-steps"></a>接下來的步驟
[註冊 Windows 裝置](https://docs.microsoft.com/intune/windows-enroll)

 
