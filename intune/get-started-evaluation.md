---
title: "開始使用 Intune"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ef58e46118a0a44609abba5de4986b5a1526a151
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2017
---
# <a name="what-is-microsoft-intune"></a>什麼是 Microsoft Intune？

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

![Azure 入口網站中的 Microsoft Intune](./media/generic-intune-azure.png)

Microsoft Intune 是其中一項 Azure 最新服務。 它提供工具來管理貴組織[定期更新](whats-new.md)的行動裝置、電腦與應用程式。 除了從現代 Azure 主控台，Intune 也可讓您使用傳統主控台。 傳統主控台是 Intune 的第一個版本，您仍然可以到那裡[使用 Intune 軟體用戶端管理 Windows 電腦](/intune-classic/deploy-use/pc-management-comparison.md)。 傳統入口網站以 Silverlight 為基礎所建立，適用於少量工作。 其他的一切，包括行動裝置和應用程式管理，是在 Azure 入口網站完成。 使用者入門指南會引導您完成想要成功在 Azure 入口網站中使用 Intune 時，需要完成的基本工作。

![說明及支援刀鋒視窗，位於 Intune 左側資訊看板中的動作清單底部。](./media/intune-azure-help-support-closeup.png)

## <a name="what-does-intune-in-the-azure-portal-provide"></a>Azure 入口網站中的 Intune 提供什麼？

Azure 入口網站中的 Intune 提供您：

* 所有 [Enterprise Mobility + Security (EMS) (EMS) 元](https://docs.microsoft.com/enterprise-mobility-security)元件全部整合在同一主控台內
* HTML 型主控台，以 Web 標準為基礎而建立，支援[現代網頁瀏覽器](supported-devices-browsers.md)
* [Azure Active Directory 群組](groups-get-started.md)可為所有 Azure 應用程式提供相容性
* 透過 [Microsoft Graph API](intune-graph-apis.md) 的自動化

## <a name="prerequisites"></a>必要條件

開始之前，您必須啟用 Intune 系統管理員和租用戶帳戶。 您可以在[這裡](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)註冊那些帳戶。 目前的訂閱者也可以在您的即時租用戶中完成這些活動。 請確定您只有使用測試裝置！

您也需要確定您是全域系統管理員，為貴組織完成本指南中的所有工作。
