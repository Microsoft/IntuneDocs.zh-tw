---
title: 針對 Windows 10 裝置將記錄傳送給公司支援人員 | Microsoft Docs
description: 在 Intune 中註冊 Windows 10 1511 裝置
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 038747fb-5b52-47c4-a2b6-f9218da4cfe1
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9e88fa55391ace4f8a86416412489ca055083503
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502044"
---
# <a name="send-logs-to-your-company-support-from-the-settings-app-for-windows-10"></a>針對 Windows 10 將記錄從設定應用程式傳送給公司支援人員

使用 [設定] 應用程式為 Windows 10 公司入口網站進行疑難排解。 如果您在 Windows 10 裝置上使用應用程式時遇到問題，可以傳送電子郵件給支援小組來尋求協助。 發生在 [公司入口網站] 應用程式中的事件和錯誤會儲存在您裝置上名為「診斷記錄」  的特殊文件中。 其中可能包含關於錯誤的其他見解，匯出時會對支援小組很有用。

1. 若要開啟 [設定]  應用程式，請移至 [開始]  功能表 > [設定]  。 您也可以在搜尋列中搜尋「設定」  。
2. 移至 [帳戶]   > [存取公司或學校資源]  。
3. 選取 [匯出您的管理記錄檔]  。

   ![「存取公司或學校資源畫面」，其中 [相關設定] 標題下顯示 [匯出] 選項。](./media/w10-export-logs.png)

4. 記錄檔會儲存在 **C:\Users\Public\Public Documents\MDMDiagnostics**。 將建立兩個檔案：一個是記錄檔本身，另一個是可讓您的系統管理員在不同程式 (例如 Microsoft Excel) 中檢閱記錄檔的特殊文件。 將這兩個檔案附加到電子郵件並將該電子郵件傳送給您的系統管理員。如果您要執行此動作多次，只需從您建立記錄檔的日期選擇檔案即可。 

您可能也需要傳送[公司入口網站應用程式中的記錄](send-logs-to-your-it-admin-cp-windows.md)，更進一步地協助公司支援人員嘗試將他們可能發現的任何問題進行疑難排解。 

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。
