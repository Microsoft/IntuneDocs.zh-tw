---
title: "Intune 資料倉儲 API 端點 | Microsoft Docs"
description: "參考主題描述 API URL 結構。"
keywords: "Intune 資料倉儲"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f36327f21fbb2f08906a7621b701a4e6c9deee03
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2017
---
# <a name="intune-data-warehouse-api-endpoint"></a>Intune 資料倉儲 API 端點

您可以搭配使用 Intune 資料倉儲 API 與具有特定角色型存取控制和 Azure AD 認證的帳戶。 您接著會使用 OAuth 2.0 向 Azure AD 授權 REST 用戶端。 最後，您會形成有意義的 URL 來呼叫資料倉儲資源。

[!INCLUDE[reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="authorization"></a>授權

Azure Active Directory (Azure AD) 採用 OAuth 2.0，可讓您授予 Azure AD 租用戶中之 Web 應用程式和 Web API 的存取權。 本指南與語言無關，並描述如何傳送和接收 HTTP 訊息，而不需要使用任何開放原始碼程式庫。 OAuth 2.0 規格的[第 4.1 節](https://tools.ietf.org/html/rfc6749#section-4.1)描述 OAuth 2.0 授權碼流程。

如需詳細資訊，請參閱[使用 OAuth 2.0 和 Azure Active Directory 授權存取 Web 應用程式](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)。

## <a name="api-url-structure"></a>API URL 結構

資料倉儲 API 端點會讀取每個集合的實體。 API 支援 **GET** HTTP 動詞，以及查詢選項子集。

Intune URL 使用下列格式：  
https://fef.{***location***}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{***entity-collection***}?api-version={***api-version***}

URL 包含下列元素：

| 元素 | 範例 | 描述 |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| 位置 | msua06 | 在 Azure 入口網站中檢視資料倉儲 API 刀鋒視窗，即可找到基底 URL。 |
| entity-collection | dates | OData 實體集合的名稱。 如需資料模型中集合和實體的詳細資訊，請參閱[資料模型](reports-ref-data-model.md)。 |
| api-version | beta | 版本是要存取之 API 的版本。 如需詳細資訊，請參閱[版本](#API-version-information)。 |


## <a name="api-version-information"></a>API 版本資訊

API 的目前版本為：`beta`。 

## <a name="odata-query-options"></a>OData 查詢選項

目前版本支援下列 OData 查詢參數：`$filter, $orderby, $select, $skip,` 和 `$top`。