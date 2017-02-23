---
title: "將 IMEI 識別碼新增至 Intune | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解如何將公司識別碼 (IMEI 號碼) 新增到 Microsoft Intune。 "
keywords: 
author: staciebarker
ms.author: stabark
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: e134a6e3ff143dacce1d70ef0ab44ade0722ed57

---

# <a name="add-corporate-identifiers"></a>新增公司識別碼

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

您可以建立一份國際行動設備識別碼 (IMEI) 號碼來識別您公司的裝置。 這些裝置不一定已經註冊，所以狀態可能是「已註冊」或「未連線」。 「未連線」表示裝置從未簽入 Intune 服務。

建立此清單時，請建立內含兩個資料行，但不含標題的逗點分隔值 (.csv) 清單。 在左資料行中新增 IMEI 識別碼，在右資料行中新增詳細資料。 清單目前最多可容納 500 個資料列。

在文字編輯器中，.csv 的外觀類似如下：

01 234567 890123,device details</br>
02 234567 890123,device details

**新增公司識別碼的 .csv 清單**

1. 在 Azure 入口網站中，選擇 [更多服務]，再於文字方塊中輸入 **Intune**，然後選擇 [其他]  >  [Intune]。

2. 在 Intune 刀鋒視窗上選擇 [註冊裝置]，然後選擇 [公司裝置識別碼]。

3. 若要匯入的檔案內含會覆寫現有詳細資料的新詳細資料，請選取 [覆寫現有識別碼的詳細資料]，以新的詳細資料取代現有的詳細資料。

4. 瀏覽至 IMEI CSV 檔案，然後選取 [新增]。

**刪除公司識別碼的 .csv 清單**

1. 在 Intune 刀鋒視窗上選擇 [註冊裝置]，然後選擇 [公司裝置識別碼]。

2. 選擇 [刪除]。



<!--HONumber=Feb17_HO1-->


