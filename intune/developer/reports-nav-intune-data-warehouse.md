---
title: Intune 資料倉儲 API
titleSuffix: Microsoft Intune
description: 您可以使用 Intune 資料倉儲 API 來建置報表，以深入了解您的企業行動環境。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 701D6CE9-43F6-4A29-8E84-E2B59931C635
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0345bf2246a7bf579b4b46d118d7889442001c30
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733422"
---
# <a name="microsoft-intune-data-warehouse-api"></a>Microsoft Intune 資料倉儲 API

Intune 資料倉儲 API 可讓您存取電腦可讀格式的 Intune 資料，以用於您慣用的分析工具。 您可以使用 API 來建置報表，以深入了解您的企業行動環境。 API 使用 OData 通訊協定，其遵循下列項目的標準模式：

- 要求與回應標頭
- 狀態碼
- HTTP 方法
- URL 慣例
- 媒體類型
- 裝載格式
- 查詢選項

OData (開放式資料通訊協定) 是一種 Organization for the Advancement of Structured Information Standards (OASIS) 標準，可定義用於建置和使用 RESTful API 的最佳做法。 Intune 資料倉儲會使用 OData 版本 4.0。

本參考章節概述端點、所支援 HTTP 方法、傳回裝載格式，以及 Intune 資料倉儲資料模型的文件。

> [!Important]  
> 您可以使用搶鮮版 (Beta) 來試用最新資料倉儲功能。 若要使用搶鮮版 (Beta)，URL 必須包含查詢參數 `api-version=beta`。 搶鮮版 (Beta) 會先提供功能，再將它們正式推出為支援的服務。 Intune 新增功能時，搶鮮版 (Beta) 可能會變更行為和資料合約。 與搶鮮版 (Beta) 相依的任何自訂程式碼或報告工具都可能會中斷進行中更新。 <!--If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

## <a name="odata-custom-client"></a>OData 自訂用戶端

您可以透過 RESTful 端點存取 Intune 資料倉儲資料模型。 若要存取您的資料，您的用戶端必須使用 OAuth 2.0 向 Azure Active Directory (Azure AD) 進行授權。 您可以先在 Azure 中設定 Web 應用程式和用戶端應用程式，並授與用戶端的權限。 您的本機用戶端將取得授權，接著可以與資料倉儲端點進行通訊。

如需詳細資訊，請參閱[使用 REST 用戶端從資料倉儲 API 取得資料](reports-proc-data-rest.md)。

> [!Note]  
> 您可以存取 Github 上的 [GitHub Intune 資料倉儲儲存機制](https://github.com/Microsoft/Intune-Data-Warehouse)以取得程式碼範例。

## <a name="interacting-with-the-api"></a>與 API 互動

API 需要使用 Azure AD 進行授權。 Azure AD 使用 OAuth 2.0。 授權之後，您可以使用 HTTP GET 動詞並連絡公開的實體集合，以從 API 取得資料。 如需詳細資料，請參閱：

- [授權](../reports-api-url.md)
- [API URL 結構](../reports-api-url.md)

## <a name="intune-data-warehouse-data-model"></a>Intune 資料倉儲資料模型

OData 會定義抽象資料模型和通訊協定，可讓任何資料來源所公開的任何用戶端存取資訊。 資料模型文件主題包含 Intune 資料倉儲資料模型中命名空間、實體和傳回物件的說明。 如需詳細資訊，請參閱[資料倉儲資料模型](reports-ref-data-model.md)。

## <a name="next-steps"></a>後續步驟

藉由閱讀 [Azure AD 的驗證案例](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)，深入了解使用 Azure AD。

在 [odata.org](https://www.odata.org) 尋找 OData 資源。
  
檢閱 [OData 第 4.0 版] (https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html) 的 OData 第 4.0 版標準  
