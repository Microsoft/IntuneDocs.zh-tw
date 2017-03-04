---
title: "將 IMEI 識別碼新增至 Intune"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何將公司識別碼 (IMEI 號碼) 新增到 Microsoft Intune。 "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 0d7c8eedbdad917a43d43d2e79ead5663e8e2871
ms.lasthandoff: 02/18/2017

---

# <a name="add-corporate-identifiers"></a>新增公司識別碼

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

您可以建立一份國際行動設備識別碼 (IMEI) 號碼來識別您公司的裝置。 這些裝置不一定已經註冊，所以狀態可能是「已註冊」或「未連線」。 「未連線」表示裝置從未簽入 Intune 服務。

建立此清單時，請建立內含兩個資料行，但不含標題的逗點分隔值 (.csv) 清單。 在左資料行中新增 IMEI 識別碼，在右資料行中新增詳細資料。 清單目前最多可容納 500 個資料列。

在文字編輯器中，.csv 的外觀類似如下：

01 234567 890123,device details</br>
02 234567 890123,device details

**新增公司識別碼的 .csv 清單**

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 Intune 刀鋒視窗上選擇 [註冊裝置]，然後選擇 [公司裝置識別碼]。

3. 若要匯入的檔案內含會覆寫現有詳細資料的新詳細資料，請選取 [覆寫現有識別碼的詳細資料]，以新的詳細資料取代現有的詳細資料。

4. 瀏覽至 IMEI CSV 檔案，然後選取 [新增]。

**刪除公司識別碼的 .csv 清單**

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 Intune 刀鋒視窗上選擇 [註冊裝置]，然後選擇 [公司裝置識別碼]。

3. 選擇 [刪除]。

