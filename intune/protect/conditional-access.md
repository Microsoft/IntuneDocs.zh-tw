---
title: Microsoft Intune 的條件式存取
titleSuffix: Microsoft Intune
description: 了解如何在 Microsoft Intune 中定義使用者、裝置和應用程式在存取公司資源之前必須符合的條件。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: cef8bcf74509d83b076b30a1ee7f2406e622b129
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722640"
---
# <a name="learn-about-conditional-access-and-intune"></a>了解條件式存取和 Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

條件式存取是指您可以控制允許連線到您電子郵件和公司資源的裝置與應用程式的方式。 在本主題中了解以裝置為基礎和以應用程式為基礎的條件式存取，並尋找搭配 Intune 使用條件式存取的常見案例。

Enterprise Mobility + Security (EMS) 的條件式存取不是一項獨立產品，它是參與屬於 EMS 之所有服務與產品的解決方案。 它提供更細微的存取控制來保障您公司資料的安全，同時為使用者提供體驗，讓他們能夠從任何裝置及從任何位置完成最佳工作成果。

您可以定義條件，依據位置、裝置、使用者狀態，以及應用程式的敏感程度，來限制對公司資料的存取。

> [!NOTE] 
> 條件式存取也可將其功能擴充至 [Office 365 服務](https://docs.microsoft.com/office365/enterprise/office-365-client-support-conditional-access) \(英文\)。

![條件式存取架構圖](./media/conditional-access/ca-diagram-1.png)

## <a name="use-conditional-access-with-intune"></a>搭配 Intune 使用條件式存取

條件式存取是 Azure Active Directory Premium 授權隨附的 Azure Active Directory 功能。 Intune 透過新增行動裝置合規姓與行動應用程式管理到解決方案以加強其功能。 

![使用 EMS 時的 Intune 和條件式存取](./media/conditional-access/intune-with-ca-1.png)

搭配 Intune 使用條件式存取的方式：

- **以裝置為基礎的條件式存取**

  - 適用於 Exchange 內部部署的條件式存取

  - 以網路存取控制為基礎的條件式存取

  - 以裝置風險為基礎的條件式存取

  - 適用於 Windows 電腦的條件式存取

    - 屬公司擁有

    - 攜帶您自己的裝置 (BYOD)

- **以應用程式為基礎的條件式存取**

## <a name="next-steps"></a>後續步驟

[搭配 Intune 使用條件式存取的常見方式](conditional-access-intune-common-ways-use.md)
