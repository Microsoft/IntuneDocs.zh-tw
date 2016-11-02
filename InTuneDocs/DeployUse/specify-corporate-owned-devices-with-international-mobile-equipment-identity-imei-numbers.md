---
title: "指定 IMEI 編號 | Microsoft Intune"
description: "Microsoft Intune 允許系統管理員匯入行動裝置平台的 IMEI 編號，從而找出公司所擁有的行動裝置"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c6b01a5efc0f60622b95623fd91f192c267ff766
ms.openlocfilehash: 9bd2b4bb676e23712c0a668161b81c4e352bce87


---

# 使用國際行動設備識別碼 (IMEI) 編碼來指定公司擁有的裝置
Microsoft Intune 允許系統管理員使用 IMEI 編號匯入行動裝置平台的 IMEI 編號的國際行動設備識別碼 (IMEI) 編號，從而找出公司擁有的行動裝置。 當裝置在 Intune 中註冊之後，您可以在 [群組]  >  [概觀]  >  [所有裝置] 下檢視 IMEI 編號已經匯入的裝置。 [裝置群組] 會在列出 IMEI 編號已經匯入的裝置時，會在 [擁有權] 資料行中將其標示為**公司**。

1. 在 [Microsoft Intune](http://manage.microsoft.com) 管理主控台中，選擇 [群組] &gt; [所有裝置] &gt; [所有公司預先註冊的裝置] &gt;[依 IMEI (所有平台)]，然後選擇 [新增裝置]。 您可以使用下列兩種方式新增裝置：

    -   **上傳內含序號的 .csv 檔案** - 建立只有兩個資料行而沒有標題的逗點分隔值 (.csv) 清單，並限制清單只可包含 5000 部裝置，或每個.csv 檔案不得超過 5 MB。

        |||
        |-|-|
        |&lt;IMEI #1&gt;|&lt;裝置 #1 詳細資料&gt;|
        |&lt;IMEI #2&gt;|&lt;裝置 #2 詳細資料&gt;|
        在文字編輯器中檢視此 .csv 檔案時，其外觀大致如下：

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **手動新增裝置的詳細資料** - 輸入 IMEI 編號與裝置詳細資料，最多不得超過五部裝置。

   *詳細資料*供系統管理之用，因此您可以指定裝置所關聯的 IMEI 編碼。 這項資訊不會傳送到裝置，但會出現在 Intune 主控台中。

2.   選擇 **[下一步]**。
3.  在 [檢閱裝置] 窗格上，確認匯入之裝置的 IMEI 編碼。 您也可以決定是否要覆寫要重新匯入之 IMEI 編號的**詳細資料**。 您可以取消核取 [覆寫] 核取方塊，以保留目前的詳細資料。 選擇 **[完成]** 匯入 IMEI 編碼。
4.  匯入的 IMEI 編號與描述會新增到 [依 IMEI (所有平台)] 清單中。

當具有 IMEI 編號的裝置註冊到 Intune (通常會在使用者安裝公司入口網站應用程式，並完成註冊程序之後) 時，裝置將其標示公司擁有，並在**IMEI 裝置**群組中將其顯示為已註冊。



<!--HONumber=Oct16_HO3-->


