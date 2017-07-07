---
title: "設定 Windows 資訊保護 - Intune"
titleSuffix: Intune on Azure
description: "了解您可用於管理 Windows 資訊保護的相關 Intune 設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f233672c-7d9b-4554-af1f-92c001a1a3c5
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7ac59456dd2bc59a0a50eeab4e483dea2033c0fa
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-configure-windows-information-protection-in-microsoft-intune"></a>如何在 Microsoft Intune 中設定 Windows 資訊保護

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

隨著企業中員工擁有的裝置增加，透過不受企業控制的應用程式與服務 (像是電子郵件、社交媒體和公用雲端) 意外外洩資料的風險也隨之提高。 例如，員工從個人電子郵件帳戶傳送最新的工程圖片、將產品資訊複製並貼到推文中，或將進行中的銷售報表儲存到公用雲端存放裝置。

**Windows 資訊保護**有助於防範這類可能的資料外洩，而不會干擾員工的體驗。 它也能協助保護企業應用程式與資料，防止企業擁有的裝置和員工帶到公司的個人裝置意外外洩資料，而且不需要對您的環境或其他應用程式進行任何變更。

Intune 原則會管理受 Windows 資訊保護、企業網路位置、保護等級和加密設定所保護的應用程式清單。

>[!NOTE]
> 若要搭配使用 Windows 10 公司入口網站應用程式和 Windows 資訊保護，則您必須在 Windows 資訊保護的「豁免」模式下新增公司入口網站應用程式。 

### <a name="next-steps"></a>後續步驟
如需詳細資訊，請參閱[使用「Windows 資訊保護」保護您的企業資料](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)。
