---
title: "什麼是應用程式管理 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰本主題可協助您了解 Microsoft Intune 管理應用程式的基本概念"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: d3be47257556e8bfa331cebf68baa43524690d1a
ms.lasthandoff: 02/16/2017


---

# <a name="what-is-microsoft-intune-app-management"></a>什麼是 Microsoft Intune 應用程式管理？


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


IT 系統管理員的任務之一可能需要確定您的使用者能否存取其工作所需的應用程式。 這可能是一項挑戰，因為︰
- 裝置平台及應用程式類型有千百種。
- 您可能需要管理公司裝置及使用者裝置上的應用程式。
- 您必須同時確保網路與資料的安全。 

此外，您也可能想要指派及管理未向 Intune 註冊之裝置上的應用程式。

Intune 提供各種功能協助您從您需要的裝置上取得所需的應用程式。

## <a name="app-management-capabilities-by-platform"></a>各種平台的應用程式管理功能

||||||
|-|-|-|-|-|
|&nbsp; |Android|iOS|Windows Phone 8.1|Windows 10|
|新增應用程式並指派給裝置與使用者|是|是|是|是|
|指派應用程式給未向 Intune 註冊的裝置|是|是|否|否|
|使用應用程式設定原則控制應用程式的啟動行為|否|是|否|否|
|使用應用程式保護原則保護應用程式中的公司資料|是|是|否|否<sup>1</sup>|
|只移除已安裝之應用程式中的公司資料 (應用程式選擇性抹除)|是|是|是|是|
|監視應用程式指派|是|是|是|是|
|指派及追蹤從應用程式市集中大量採購的應用程式|否|否|否|是|
|強制安裝在裝置上的應用程式 (必要)<sup>2</sup>|是|是|是|是|
|可從公司入口網站安裝在裝置上的選擇 (可用安裝)|是|是|是|是|
|安裝網路應用程式的捷徑 (網路美工圖案)|是|是|是|是|
|內部 (企業營運) 應用程式|是|是|否|否|
|市集應用程式|是|是|是|是|
|更新應用程式|是|是|是|是|

<sup>1</sup>您可以考慮使用 [Windows 資訊保護](/intune-azure/configure-devices/how-to-configure-windows-information-protection)來保護 Windows 10 裝置上的應用程式。

<sup>2</sup>僅適用於 Intune 管理的裝置。


## <a name="how-to-get-started"></a>如何開始

在**行動應用程式**工作負載中，您能存取的應用程式相關項目如下：

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 **Intune** 刀鋒視窗上選擇 [管理應用程式]。

    ![行動應用程式工作負載](./media/apps-workload.png)

### <a name="manage"></a>管理
- **應用程式** - 您可以在此新增、指派及監視您大部分的應用程式。 
    - [新增應用程式](add-apps.md)
    - [指派應用程式](deploy-apps.md)
    - [監視應用程式](monitor-apps.md)
- **授權的應用程式** - 檢視、部署及監視從應用程式市集中大量採購的應用程式。
    - [商務用 Windows 市集大量採購應用程式](wsfb-apps.md)
- **應用程式設定原則** - 應用程式設定原則可讓您提供使用者執行應用程式時可能需要的設定。 如需詳細資料，請參閱：
    - [應用程式設定原則](app-configuration-policies.md)
- **應用程式保護原則** - 可讓您建立設定與應用程式的關聯來協助保護其所使用的公司資料。 例如，您可以限制某應用程式與其他應用程式的通訊能力，或是要求使用者輸入 PIN 碼才能存取公司應用程式。
    - [應用程式保護原則](app-protection-policies.md)
- **應用程式選擇性抹除** - 只從您選取的裝置移除公司資料。
    - [應用程式選擇性抹除](app-selective-wipe.md)

### <a name="monitor"></a>監視
- **探索應用程式** - 顯示 Intune 指派並安裝在裝置上的所有應用程式。
- **應用程式安裝狀態** - 顯示您所建立之應用程式指派的狀態。
- **應用程式保護使用者狀態** - 顯示您選取之使用者的應用程式保護原則狀態。

如需詳細資訊，請參閱[監視應用程式](monitor-apps.md)

### <a name="setup"></a>Setup
<!--- **iOS VPP Tokens**
    - [iOS volume-purchased apps](ios-vpp-apps.md) --->
- **商務用 Windows 市集** - 設定對商務用 Windows 市集的整合。 執行此動作之後，可以將採購的應用程式同步到 Intune 並加以指派，以及追蹤授權使用狀況。 
    - [商務用 Windows 市集大量採購應用程式](wsfb-apps.md)
- **公司入口網站品牌** - 自訂公司入口網站顯示您公司的品牌。 
    - [公司入口網站設定](company-portal-app.md)

