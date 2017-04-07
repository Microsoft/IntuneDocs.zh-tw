---
title: "將 IMEI 識別碼新增至 Intune"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何將公司識別碼 (IMEI 號碼) 新增到 Microsoft Intune。 "
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 4ebd74c77145464574a1fed878ec4dbc2eb3c271
ms.openlocfilehash: 7bb8168c442a3340e8c185f1908acd9be15cab05
ms.lasthandoff: 04/05/2017

---

# <a name="add-corporate-identifiers"></a>新增公司識別碼

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

身為 IT 系統管理員，您可以建立並匯入列出國際行動設備識別 (IMEI) 號碼以識別公司所擁有裝置的逗號分隔值 (.csv) 檔案。 基於系統管理目的，每個 IMEI 號碼均可含有清單中指定的詳細資料。

當您上傳公司 iOS 裝置的序號時，它們必須與公司註冊設定檔搭配。 接著，必須使用 Apple 的裝置註冊計劃 (DEP) 或 Apple Configurator 來註冊裝置，以使它們顯示為公司所擁有。 

## <a name="create-a-csv-file"></a>建立 .csv 檔案
建立此清單時，請建立內含兩個資料行，但不含標題的逗點分隔值 (.csv) 清單。 在左資料行中新增 IMEI 識別碼，在右資料行中新增詳細資料。 詳細資料限制為 128 個字元。 目前的限制是每個 .csv 檔案 500 個資料列。

**上傳內含序號的 .csv 檔案** - 建立只有兩個資料行而沒有標題的逗點分隔值 (.csv) 清單，並限制清單只可包含 5000 部裝置，或每個.csv 檔案不得超過 5 MB。

|||
|-|-|
|&lt;IMEI #1&gt;|&lt;裝置 #1 詳細資料&gt;|
|&lt;IMEI #2&gt;|&lt;裝置 #2 詳細資料&gt;|

    This .csv file when viewed in a text editor appears as:

    ```
    01 234567 890123,device details
    02 234567 890123,device details
    ```

**新增公司識別碼的 .csv 清單**

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 Intune 刀鋒視窗上選擇 [註冊裝置]，然後選擇 [公司裝置識別碼]。

3. 若要匯入的檔案內含會覆寫現有詳細資料的新詳細資料，請選取 [覆寫現有識別碼的詳細資料]，以新的詳細資料取代現有的詳細資料。

4. 瀏覽至 IMEI CSV 檔案，然後選取 [新增]。

> [!IMPORTANT]
> 某些 Android 裝置有多個 IMEI 編號。 Intune 一部裝置清查一個 IMEI 編號。 如果您匯入的 IMEI 編號不是 Intune 清查過的 IMEI，則該裝置會分類為個人裝置，而不是公司擁有的裝置。 如果某部裝置匯入多個 IMEI 編號，則註冊狀態會將未經清查的編號顯示為**未知**。

匯入之後，這些裝置不一定已經註冊，所以狀態可能是「已註冊」或「未連線」。 「未連線」表示裝置從未與 Intune 服務通訊。

## <a name="delete-a-csv-list"></a>刪除 .csv 清單

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 Intune 刀鋒視窗上選擇 [註冊裝置]，然後選擇 [公司裝置識別碼]。

3. 選擇 [刪除]。

如需國際行動設備識別碼的詳細規格，請參閱 [3GGPP TS 23.003 (英文)](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729)。

