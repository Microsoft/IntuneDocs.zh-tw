---
title: "針對 Windows 10 裝置將記錄傳送給公司支援人員 | Microsoft Docs"
description: "在 Intune 中註冊 Windows 10 1511 裝置"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 038747fb-5b52-47c4-a2b6-f9218da4cfe1
searchScope: User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: f36b623f78a640cfe1900dc0d1564cbf2fbfbf6f
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2017
---
# <a name="send-logs-to-your-company-support-from-the-settings-app-for-windows-10"></a>針對 Windows 10 將記錄從設定應用程式傳送給公司支援人員

如果您在使用公司所管理的 Windows 10 裝置時出現錯誤，則可以使用電子郵件將資訊傳送給公司支援人員，以協助他們針對問題進行疑難排解。 這項資訊會保留在裝置中名為 _diagnostic log_ 的特殊文件中。

1.  開啟 Windows [設定] 應用程式，方法是前往 [開始] 功能表，然後選取 [設定] 按鈕。 您也可以在搜尋列中搜尋「設定」。
2.  移至 [帳戶] > [存取公司或學校資源]。
3.  選取 [匯出您的管理記錄檔]。

  ![「存取公司或學校資源畫面」，其中 [相關設定] 標題下顯示 [匯出] 選項。](./media/w10-export-logs.png)

4. 記錄檔會儲存在 **C:\Users\Public\Public Documents\MDMDiagnostics**。 將建立兩個檔案：一個是記錄檔本身，另一個是可讓您的系統管理員在不同程式 (例如 Microsoft Excel) 中檢閱記錄檔的特殊文件。 將這兩個檔案附加到電子郵件並將該電子郵件傳送給您的系統管理員。如果您要執行此動作多次，只需從您建立記錄檔的日期選擇檔案即可。 

您可能也需要傳送[公司入口網站應用程式中的記錄](send-logs-to-your-it-admin-cp-windows.md)，更進一步地協助公司支援人員嘗試將他們可能發現的任何問題進行疑難排解。 

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://portal.manage.microsoft.com#HelpDeskDialog)。
