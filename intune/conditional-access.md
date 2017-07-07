---
title: "利用 Intune 的條件式存取"
titleSuffix: Intune on Azure
description: "了解如何在 Microsoft Intune 中定義使用者與裝置在存取公司資源之前必須符合的條件。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d3e6b720eeed65c81e5f3a4dbf06890ea8fd09ce
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="whats-conditional-access"></a>什麼是條件式存取？

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主題會先說明適用於 Enterprise Mobility + Security (EMS) 的條件式存取，接著說明使用 Intune 時的條件式存取常見案例。

Enterprise Mobility + Security (EMS) 的條件式存取不是一項獨立產品，它是參與屬於 EMS 之所有服務與產品的解決方案。 它提供更細微的存取控制來保障您公司資料的安全，同時為使用者提供體驗，讓他們能夠從任何裝置及從任何位置完成最佳工作成果。

您可以定義條件，依據位置、裝置、使用者狀態，以及應用程式的敏感程度，來限制對公司資料的存取。

> [!NOTE] 
> 條件式存取也可將其功能擴充至 [Office 365 服務](https://blogs.technet.microsoft.com/wbaer/2017/02/17/conditional-access-policies-with-sharepoint-online-and-onedrive-for-business/) \(英文\)。

![條件式存取架構圖](./media/ca-diagram-1.png)

## <a name="conditional-access-with-intune"></a>利用 Intune 的條件式存取

Intune 會新增行動裝置合規性和行動應用程式管理功能，以支援 EMS 條件式存取解決方案。

![使用 EMS 時的 Intune 和條件式存取](./media/intune-with-ca-1.png)

透過 Intune 使用條件式存取的方式：

-   **裝置型條件式存取**

    -   Exchange 內部部署的條件式存取

    -   以網路存取控制為依據的條件式存取

    -   以裝置風險為依據的條件式存取

    -   Windows 電腦的條件式存取

        -   屬公司擁有

        -   攜帶您自己的裝置 (BYOD)

-   **以應用程式為基礎的條件式存取**

## <a name="next-steps"></a>後續步驟

[透過 Intune 使用條件式存取的常見方式](conditional-access-intune-common-ways-use.md)