---
title: Microsoft Intune 的條件式存取
titleSuffix: Microsoft Intune
description: 了解如何在 Microsoft Intune 中定義使用者、裝置和應用程式為了存取公司資源所須符合的條件。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 179d135ee8e216495cd7435bf38d8087e5c990e8
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188284"
---
# <a name="learn-about-conditional-access-and-intune"></a>了解條件式存取和 Intune

使用條件式存取，您就能夠控制可連線到電子郵件和公司資源的裝置和應用程式。 

Enterprise Mobility + Security (EMS) 不是獨立產品。 這是 EMS 所屬全部服務和產品的部分解決方案。 條件式存取提供更細緻的存取控制，以保障公司資料的安全，同時讓使用者體驗可在任何裝置與地點來最佳地完成工作。

您可以定義條件，依據位置、裝置、使用者狀態，以及應用程式的敏感程度，來限制對公司資料的存取。

> [!NOTE]
> 條件式存取也可將其功能擴充至 [Office 365 服務](https://docs.microsoft.com/office365/enterprise/office-365-client-support-conditional-access) \(英文\)。

![條件式存取圖表](./media/conditional-access/ca-diagram-1.png)

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
