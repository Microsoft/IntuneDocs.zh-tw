---
title: Google 傳送至 Intune 的資料
titleSuffix: Microsoft Intune
description: Google 傳送至 Intune 的資料清單。
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
ms.assetid: c379c8db-788a-454e-9098-665ea3bc7b56
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 914ce3aa15099b7692d524dbfa368f99f0d092e8
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504483"
---
# <a name="data-google-sends-to-intune"></a>Google 傳送至 Intune 的資料

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

在裝置上啟用 Android 企業裝置管理時，Microsoft Intune 會建立與 Google 的連線並在 Intune 和 Google 之間共享使用者和裝置資訊。 您必須先建立 Google 帳戶，Microsoft Intune 才能建立連線。

下表列出裝置上啟用裝置管理時，Google 傳送至 Intune 的資料清單：


| Google 傳送至 Intune 的資料 | 詳細資料 | 用途 | 範例 |
|:---:|:---:|:---:|:---:|
| 企業資料 | Google 中的客戶企業識別碼。 | 連結 Intune 與 Google 之間的客戶資訊。 | **enterpriseId** 範例：LC04eik8a6。<br>**名稱**。 設定 Android 企業時，所輸入的系統管理員名稱。 範例：Joe Smith。<br>**系統管理員電子郵件**。 YourAdmin@gmail.com 設定 Android 企業時會用到。 |
| 應用程式資料 | 受控 Play Store 應用程式的資料。 | 將應用程式指定為使用者或裝置可用的或必要的應用程式。 | **應用程式名稱**範例：Contoso 倉儲庫存應用程式。<br>**代表應用程式的唯一識別碼**範例： app:com.Contoso.Warehouse.InventoryTracking |
| 服務帳戶 | 內部唯一的 Google 服務帳戶，用於特定的客戶來電。 | 用來代替客戶呼叫 Google (以檢視應用程式、裝置以及其他等等) | **名稱**範例：InternalAccount@InternalService.com。<br>**金鑰**範例：ServiceAccountPassword |


若要停止使用 Android 企業裝置管理搭配 Microsoft Intune 並刪除資料，您必須同時停用 Microsoft Intune 的 Android 企業裝置管理並刪除您的 Google 帳戶。 關於如何執行帳戶管理請參閱 Google 帳戶。


