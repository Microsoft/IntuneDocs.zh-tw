---
title: "使用國際行動設備識別碼 (IMEI) 編碼來指定公司擁有的裝置 | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 398d93d4e2317d00a2f9d5f89966aaec3b942504
ms.openlocfilehash: af4b87eb8082ee5ff11cd2d42b788ad17b334bcb


---

# 使用國際行動設備識別碼 (IMEI) 編碼來指定公司擁有的裝置
Microsoft Intune 可讓系統管理員為具有 IMEI 編號的行動裝置平台匯入國際行動設備識別碼 (IMEI) 編碼，協助找出公司擁有的行動裝置。 只要在 Intune 註冊，即可在 **[群組]** > **[概觀]** > **[所有裝置]** > **公司預先註冊的裝置]** > **依 IMEI (所有平台)]** 下方檢視已匯入 IMEI 編號的裝置。

1. 在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，選擇 **[群組]** &gt; **[所有裝置]** &gt; **[所有公司預先註冊的裝置]** &gt;**[依 IMEI (所有平台)]**，然後選擇 **[新增裝置]**。 您可以使用下列兩種方式新增裝置：

    -   **上傳包含序號的 CSV 檔案** - 建立以逗號分隔值的清單，並在其中包含兩個不含標頭的資料行，且限制每個 CSV 檔案最多可有 5000 部裝置或 5 MB。

        |||
        |-|-|
        |&lt;IMEI #1&gt;|&lt;裝置 #1 詳細資料&gt;|
        |&lt;IMEI #2&gt;|&lt;裝置 #2 詳細資料&gt;|
        在文字編輯器中檢視此 .csv 檔案時，其外觀大致如下：

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **手動新增裝置詳細資料** - 輸入最多五部裝置的 IMEI 編碼和裝置詳細資料。

   *詳細資料*是供系統管理之用，因此您可以識別與裝置相關聯的 IMEI 編碼。 這項資訊不會傳送至裝置，但會出現在 Intune 主控台中。

2.   選擇 **[下一步]**。
3.  在 [檢閱裝置] 窗格上，您可以確認匯入的裝置 IMEI 編碼。 您也可以決定是否覆寫正重新匯入之 IMEI 編碼的 [詳細資料]。 您可以取消核取 [覆寫] 核取方塊，以保留目前詳細資料。 選擇 **[完成]** 匯入 IMEI 編碼。
4.  新增的 IMEI 編碼和描述會新增至 [依 IMEI (所有平台)] 清單。

具有該 IMEI 編碼的裝置註冊時 (通常是使用者安裝公司入口網站應用程式並完成已註冊的程序時)，裝置將會標記為 [屬公司擁有]，並在 [IMEI 裝置] 群組中顯示為已註冊。



<!--HONumber=Jul16_HO1-->


