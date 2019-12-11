---
title: Intune 傳送至 Google 的資料
titleSuffix: Microsoft Intune
description: Intune 傳送至 Google 的資料清單。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f6ab8a4e8e46373a536949c13ceaebb267f34cd
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504463"
---
# <a name="data-intune-sends-to-google"></a>Intune 傳送至 Google 的資料

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

在裝置上啟用 Android 企業裝置管理時，Microsoft Intune 會建立與 Google 的連線並與 Google 共用使用者和裝置資訊。 您必須先建立 Google 帳戶，Microsoft Intune 才能建立連線。

下表列出裝置上啟用裝置管理時，Microsoft Intune 傳送至 Google 的資料：


| 傳送至 Google 的資料 | 詳細資料 | 用途 | 範例 |
|:---:|:---:|:---:|:---:|
| EnterpriseId | 將 Gmail 帳戶繫結至 Intune 時，在 Google 產生。 | 用來在 Intune 與 Google 之間進行通訊的主要識別碼。  此通訊包括設定原則、管理裝置，以及繫結/解除繫結 Android 企業與 Intune。 | 唯一識別碼，範例格式：LC04eik8a6 |
| 原則本文 | 儲存新的應用程式或設定原則時，在 Intune 產生。 | 將原則套用至裝置。 | 這是應用程式或設定原則所有已設定的設定集合。 這可能包含客戶資訊，如果有提供為原則的一部分，例如網路名稱、應用程式名稱，以及應用程式特定設定。 |
| 裝置資料 | 工作設定檔的裝置案例以在 Google 中註冊開始。 受管理裝置的裝置案例以在 Google 中註冊開始。 | 各種動作的裝置資料資訊會在 Intune 與 Google 之間傳送，例如套用原則、管理裝置和一般性的報表作業。 | **代表裝置名稱的唯一識別碼。** 範例：enterprises/LC04ebru7b/devices/3592d971168f9ae4<br>**代表使用者名稱的唯一識別碼。** 範例：Enterprises/LC04ebru7b/users/116838519924207449711<br>**裝置狀態。** 範例：使用中、已停用、佈建中。<br>**性狀態。** 範例：不支援設定、遺漏必要的應用程式<br>**軟體資訊。** 範例：軟體版本及修補程式等級。<br>**網路資訊。** 範例：IMEI、MEID、WifiMacAddress<br>**裝置設定。** 範例：加密層級和裝置是否允許使用未知應用程式的資訊。<br> 如需 JSON 訊息的範例，請參閱下方內容。 |
| newPassword | 在 Intune 產生。 | 重設裝置密碼。 | 代表新密碼的字串。 |
| Google 使用者 | Google | 管理工作設定檔 (BYOD) 案例的工作設定檔。 | 代表連結的 Gmail 帳戶的唯一識別碼。 範例：114223373813435875042 |
| 應用程式資料 | 儲存應用程式原則時，在 Intune 產生。 |  | 應用程式名稱字串。 範例：app:com.microsoft.windowsintune.companyportal |
| 企業服務帳戶 | Intune 要求時在 Google 產生。 | 用於針對涉及此客戶的交易在 Intune 與 Google 之間進行驗證。 | 有幾個部分：<br> **企業識別碼**：先前記載。<br>**UPN**：產生的 UPN，用於代表客戶的驗證。<br>範例： w49d77900526190e26708c31c9e8a0@pfwp-commicrosoftonedfmdm2.google.com.iam.gserviceaccount.com<br>**索引鍵**：以 Base64 編碼的 blob，用於驗證要求、加密後儲存在服務中，但 blob 看起來會像這樣：<br> 代表客戶索引碼的唯一識別碼<br>範例：a70d4d53eefbd781ce7ad6a6495c65eb15e74f1f |


若要停止使用 Android 企業裝置管理搭配 Microsoft Intune 並刪除資料，您必須同時停用 Microsoft Intune 的 Android 企業裝置管理並刪除您的 Google 帳戶。 關於如何執行帳戶管理請參閱 Google 帳戶。


