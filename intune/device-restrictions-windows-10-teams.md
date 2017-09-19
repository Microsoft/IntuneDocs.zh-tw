---
title: "Windows 10 團隊版的 Intune 裝置限制"
titlesuffix: Azure portal
description: "了解適用於 Windows 10 團隊版裝置的裝置限制。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 677c41a2-5344-4c52-85f0-809dce3a5d5b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f0826b57656a756cf0a9f57a4b02b734a23b2919
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2017
---
# <a name="windows-10-team-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中 Windows 10 團隊版裝置限制設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


## <a name="apps-and-experience"></a>應用程式及體驗

- **有人在房間時喚醒螢幕** - 可在裝置感應器偵測到室內有人時自動喚醒裝置。
- **歡迎使用畫面上所顯示的會議資訊** - 啟用此選項可選擇顯示在 [歡迎使用] 畫面之 [會議]磚上的資訊。 您可以：
    - **僅顯示召集人和時間**
    - **顯示召集人、時間和主旨 (不會顯示私人會議的主旨)**
- **歡迎使用畫面背景影像 URL** -啟用此設定以在 Windows 10 團隊版裝置的 [歡迎] 畫面顯示來自指定 URL 的自訂背景。<br>影像必須是 PNG 格式，而且 URL 的開頭必須是 **https://**。

## <a name="azure-operational-insights"></a>Azure Operational Insights

- **Azure Operational Insights** - Azure Operational Insights 這個 Microsoft Operations Manager 套件組件會收集、儲存及分析來自 Windows 10 團隊版的記錄檔資料。
若要連線到 Azure Operational Insights，您必須指定 [工作區識別碼] 和 [工作區金鑰]。

## <a name="maintenance"></a>維護

- **更新的維護期間** - 設定可以進行裝置更新的範圍。 您可以設定間隔的 [開始時間] 和 [持續時間 (小時)] (從 1 到 5 小時) 。

## <a name="wireless-projection"></a>無線投影

- **無線投影的 PIN** - 指定您是否必須輸入 PIN，才可使用該裝置的無線投影功能。
- **Miracast 無線投影** - 如果您想要讓 Windows 10 團隊版裝置使用支援 Miracast 的裝置來投影，請選取此選項。
- **Miracast 無線投影通道** - 選擇用來建立連線的 Miracast 通道。


## <a name="next-steps"></a>後續步驟

使用[如何設定裝置限制設定](device-restrictions-configure.md)中的資訊進行儲存，並將設定檔指派給使用者和裝置。
