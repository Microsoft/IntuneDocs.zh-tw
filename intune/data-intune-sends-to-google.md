---
title: Intune 傳送至 Google 的資料
titleSuffix: Microsoft Intune
description: Intune 傳送至 Google 的資料清單。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 78fef57849b8742bb10ece1717234af5cce3f4ba
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="data-intune-sends-to-google"></a>Intune 傳送至 Google 的資料

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

在裝置上啟用 Android 裝置管理時，Microsoft Intune 會建立與 Google 的連線並與 Google 共用使用者和裝置資訊。 您必須先建立 Google 帳戶，Microsoft Intune 才能建立連線。

下表列出裝置上啟用裝置管理時，Microsoft Intune 傳送至 Google 的資料：


| 傳送至 Google 的資料 | 詳細資料 | 用途 | 範例 |
|:---:|:---:|:---:|:---:|
| EnterpriseId | 將 Gmail 帳戶繫結至 Intune 時，在 Google 產生。 | 用來在 Intune 與 Google 之間進行通訊的主要識別碼。  此通訊包括設定原則、管理裝置，以及繫結/解除繫結 Android 企業與 Intune。 | 唯一識別項、範例格式：LC04eik8a6 |
| 原則本文 | 儲存新的應用程式或設定原則時，在 Intune 產生。 | 將原則套用至裝置。 | 這是應用程式或設定原則所有已設定的設定集合。 這可能包含客戶資訊，如果有提供為原則的一部分，例如網路名稱、應用程式名稱，以及應用程式特定設定。 |
| 裝置資料 | 工作設定檔的裝置案例以在 Google 中註冊開始。 受管理裝置的裝置案例以在 Google 中註冊開始。 | 各種動作的裝置資料資訊會在 Intune 與 Google 之間傳送，例如套用原則、管理裝置和一般性的報表作業。 | **代表裝置名稱的唯一識別碼。** 範例：enterprises/LC04ebru7b/devices/3592d971168f9ae4<br>**代表使用者名稱的唯一識別碼。** 範例：Enterprises/LC04ebru7b/users/116838519924207449711<br>**裝置狀態。** 範例：作用中、已停用、佈建中。<br>**性狀態。** 範例：設定不受支援、遺漏必要的應用程式<br>**軟體資訊。** 範例：軟體版本及修補程式等級。<br>**網路資訊。** 範例：IMEI、MEID、WifiMacAddress<br>**裝置設定。** 範例：加密層級和裝置是否允許未知應用程式的資訊。<br> 如需 JSON 訊息的範例，請參閱下方內容。 |
| newPassword | 在 Intune 產生。 | 重設裝置密碼。 | 代表新密碼的字串。 |
| Google 使用者 | Google | 管理工作設定檔 (BYOD) 案例的工作設定檔。 | 代表連結的 Gmail 帳戶的唯一識別碼。 範例：114223373813435875042 |
| 應用程式資料 | 儲存應用程式原則時，在 Intune 產生。 |  | 應用程式名稱字串。 範例：app:com.microsoft.windowsintune.companyportal |
| 企業服務帳戶 | Intune 要求時在 Google 產生。 | 用於針對涉及此客戶的交易在 Intune 與 Google 之間進行驗證。 | 有幾個部分：<br> **企業識別碼**：先前記載。<br>**UPN**：產生的 UPN，用於代表客戶的驗證。<br>範例： w49d77900526190e26708c31c9e8a0@pfwp-commicrosoftonedfmdm2.google.com.iam.gserviceaccount.com<br>**索引鍵**：Base64 編碼的 Blob，用於驗證要求，在服務中會加密儲存，但以下是 Blob 的外觀：<br> 代表客戶索引碼的唯一識別碼<br>範例：a70d4d53eefbd781ce7ad6a6495c65eb15e74f1f |

**裝置資料範例**

以下是來自 Google 的範例 JSON 裝置訊息：



```
'{
  "name": "enterprises/LC02dhxx1r/devices/3195483be017acdc",
  "userId": "114223373813435875042",
  "adminType": "DEVICE_OWNER",
  "state": "ACTIVE",
  "appliedState": "ACTIVE",
  "policyCompliant": true,
  "enrollmentTime": "2017-10-06T15:17:41.702Z",
  "lastStatusReportTime": "2017-10-06T15:18:10.325Z",
  "lastPolicyComplianceReportTime": "2017-10-06T15:18:11.665Z",
  "lastPolicySyncTime": "2017-10-06T15:18:07.852Z",
  "appliedPolicyVersion": "2",
  "apiLevel": 26,
  "enrollmentTokenData": "brew 30 day token",
  "enrollmentTokenId": "yXdtW0_0L7c7Yo9DtRhEfPi3PcMqTorF3V1bTAw_eRs",
  "softwareInfo": {
    "androidVersion": "8.0.0",
    "cloudDpcVersionCode": 55314,
    "cloudDpcVersionName": "bv00553-rc14",
    "androidBuildNumber": "OPR4.170623.009",
    "deviceKernelVersion": "3.10.73-ga51b1600b7f8",
    "bootloaderVersion": "BHZ21c",
    "androidBuildTime": "2017-08-28T18:57:48Z",
    "securityPatchLevel": "2017-10-05",
    "androidBuildType": "user",
    "buildUser": "android-build"
  },
  "hardwareInfo": {
    "brand": "google",
    "hardware": "bullhead",
    "deviceBasebandVersion": "M8994F-2.6.39.3.03",
    "manufacturer": "LGE",
    "serialNumber": "01ed07873b3c20cd",
    "model": "Nexus 5X",
    "batteryShutdownTemperatures": [60.0],
    "batteryThrottlingTemperatures": [-3.4028235E38],
    "cpuShutdownTemperatures": [115.0, 115.0, 115.0, 115.0, 115.0, 115.0],
    "cpuThrottlingTemperatures": [60.0, 60.0, 60.0, 60.0, 60.0, 60.0],
    "gpuShutdownTemperatures": [-3.4028235E38],
    "gpuThrottlingTemperatures": [-3.4028235E38],
    "skinShutdownTemperatures": [-3.4028235E38],
    "skinThrottlingTemperatures": [37.0]
  },
  "displays": [{
    "name": "Built-in Screen",
    "refreshRate": 60,
    "state": "ON",
    "width": 1080,
    "height": 1920,
    "density": 420
  }],
  "appliedPolicyName": "enterprises/LC02dhxx1r/policies/default",
  "networkInfo": {
    "imei": "353626070676775",
    "wifiMacAddress": "02:00:00:00:00:00"
  },
  "memoryInfo": {
    "totalRam": "1902936064",
    "totalInternalStorage": "3169611776"
  },
  "memoryEvents": [{
    "eventType": "EXTERNAL_STORAGE_DETECTED",
    "createTime": "2017-10-06T15:18:09.959Z",
    "byteCount": "26720919552"
  }],
  "powerManagementEvents": [{
    "eventType": "BATTERY_LEVEL_COLLECTED",
    "createTime": "2017-10-06T15:18:09.939Z",
    "batteryLevel": 95.0
  }],
  "userName": "enterprises/LC02dhxx1r/users/114223373813435875042",
  "enrollmentTokenName": "enterprises/LC02dhxx1r/enrollmentTokens/yXdtW0_0L7c7Yo9DtRhEfPi3PcMqTorF3V1bTAw_eRs"
}'
```

若要停止使用 Android 裝置管理搭配 Microsoft Intune 並刪除資料，您必須同時停用 Microsoft Intune 的 Android 裝置管理並刪除您的 Google 帳戶。 關於如何執行帳戶管理請參閱 Google 帳戶。


