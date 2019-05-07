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
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 34ce3f34dbf3c060438a6b30abc9345687cdaf47
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569489"
---
# <a name="whats-conditional-access"></a>什麼是條件式存取？

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

條件式存取是指您可以控制可連線到您電子郵件和公司資源的裝置與應用程式的方式。 在本主題中，深入了解以裝置和應用程式為基礎的條件式存取，並尋找搭配 Intune 使用條件式存取的常見案例。

Enterprise Mobility + Security (EMS) 的條件式存取不是一項獨立產品，它是參與屬於 EMS 之所有服務與產品的解決方案。 它提供更細微的存取控制來保障您公司資料的安全，同時為使用者提供體驗，讓他們能夠從任何裝置及從任何位置完成最佳工作成果。

您可以定義條件，依據位置、裝置、使用者狀態，以及應用程式的敏感程度，來限制對公司資料的存取。

> [!NOTE] 
> 條件式存取也可將其功能擴充至 [Office 365 服務](https://blogs.technet.microsoft.com/wbaer/2017/02/17/conditional-access-policies-with-sharepoint-online-and-onedrive-for-business/) \(英文\)。

![條件式存取架構圖](./media/ca-diagram-1.png)

## <a name="conditional-access-with-intune"></a>利用 Intune 的條件式存取

條件式存取是 Azure Active Directory Premium 授權中包含的 Azure Active Directory 功能。 Intune 透過新增行動裝置合規姓與行動應用程式管理到解決方案以加強其功能。 

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
