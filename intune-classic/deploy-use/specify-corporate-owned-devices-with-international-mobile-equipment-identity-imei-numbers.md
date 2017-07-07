---
title: "指定 IMEI 編號"
description: "Microsoft Intune 允許系統管理員匯入行動裝置平台的 IMEI 編號，從而找出公司所擁有的行動裝置"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d1ecc65dac893740b152aa743e6b32c5de5a3ec9
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers"></a>使用國際行動設備識別碼 (IMEI) 編碼來指定公司擁有的裝置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 允許系統管理員使用 IMEI 編號匯入行動裝置平台的 IMEI 編號的國際行動設備識別碼 (IMEI) 編號，從而找出公司擁有的行動裝置。 當裝置在 Intune 中註冊之後，您可以在 [群組]  >  [概觀]  >  [所有裝置] 下檢視 IMEI 編號已經匯入的裝置。 [裝置群組] 會在列出 IMEI 編號已經匯入的裝置時，會在 [擁有權] 資料行中將其標示為**公司**。

1. 在 [Microsoft Intune](https://manage.microsoft.com) 管理主控台中，選擇 [群組] &gt; [所有裝置] &gt; [所有公司預先註冊的裝置] &gt;[依 IMEI (所有平台)]，然後選擇 [新增裝置]。 您可以使用下列兩種方式新增裝置：

    -   **上傳內含序號的 .csv 檔案** - 建立只有兩個資料行而沒有標題的逗點分隔值 (.csv) 清單，並限制清單只可包含 5000 部裝置，或每個.csv 檔案不得超過 5 MB。 詳細資料欄位的長度限制為 128 個字元。 

        |||
        |-|-|
        |&lt;IMEI #1&gt;|&lt;裝置 #1 詳細資料&gt;|
        |&lt;IMEI #2&gt;|&lt;裝置 #2 詳細資料&gt;|
        在文字編輯器中檢視此 .csv 檔案時，其外觀大致如下：

        ```
        01234567890123,device details
        02234567890123,device details
        ```

    -   **手動新增裝置的詳細資料** - 輸入 IMEI 編號與裝置詳細資料，最多不得超過 15 部裝置。

   [詳細資料] 欄位供系統管理之用。 您可以指定詳細資料，以協助識別屬公司擁有的裝置清單中依硬體識別碼列出的裝置。 這項資訊不會傳送到裝置，但會出現在 Intune 主控台中。

2.   選擇 **[下一步]**。
3.  在 [檢閱裝置] 窗格上，確認匯入之裝置的 IMEI 編碼。 您也可以決定是否要覆寫要重新匯入之 IMEI 編號的**詳細資料**。 您可以取消核取 [覆寫] 核取方塊，以保留目前的詳細資料。 選擇 **[完成]** 匯入 IMEI 編碼。
4.  匯入的 IMEI 編號與描述會新增到 [依 IMEI (所有平台)] 清單中。

> [!IMPORTANT]
> 如果您要匯入 Android 裝置的 IMEI 編號，請注意有些 Android 裝置可以有多個 IMEI 編號。 如果您匯入的 IMEI 編號不是裝置向 Intune 回報的 IMEI，則會將該裝置分類為個人裝置，而不是公司擁有的裝置。

當具有 IMEI 編號的裝置註冊到 Intune (通常會在使用者安裝公司入口網站應用程式，並完成註冊程序之後) 時，裝置將其標示公司擁有，並在**IMEI 裝置**群組中將其顯示為已註冊。

>[!NOTE]
> 當貴組織在不久的將來移轉到新的 Azure 入口網站後，您會看到這項功能的變更。 在現有的 Intune 系統管理員主控台中，管理員可以接受已上傳之 CSV 的相關詳細資料，並覆寫個別硬體識別碼的現有詳細資料。 在新的 Azure 入口網站中，您將可以自動覆寫所有硬體識別碼的詳細資料，或略過所有現有識別項的新詳細資料。

如需國際行動設備識別碼的詳細規格，請參閱 [3GGPP TS 23.003 (英文)](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729)。
