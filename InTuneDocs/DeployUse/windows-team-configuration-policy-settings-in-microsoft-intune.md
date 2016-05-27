---
# required metadata

title: Microsoft Intune 的 Windows 團隊版組態原則設定 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 的 Windows 團隊版設定原則設定
使用 Microsoft Intune Windows 10 團隊版一般設定原則為已註冊的 Windows 10 團隊版裝置進行設定，例如 Microsoft Surface Hub。

|設定名稱|詳細資料|
|----------------|-----------|
|**可在室內有人時自動喚醒螢幕。**|可在裝置感應器偵測到室內有人時自動喚醒裝置。|
|**需要 PIN 碼以進行無線投影**|您必須先指定是否輸入 PIN 碼，才可以使用裝置的無線投影功能。|
|**設定裝置更新的維護期間**|設定可以進行裝置更新的間隔。 您可以設定間隔的開始時間和持續時間 (從 1 到 5 小時) 。|
|**啟用 Azure Operational Insights**|Azure Operational Insights 是 Microsoft Operations Manager 套件的一部分，可從 Windows 10 團隊版裝置收集、儲存和分析記錄檔資料。<br /><br />若要連接至 Azure Operational Insights，您必須指定 [工作場所 ID] 和 [工作場所金鑰].|
|**啟用 Miracast 無線投影**|如果您想要讓 Windows 10 團隊版裝置使用具有 Miracast 功能的裝置進行投影，請啟用此選項。<br /><br />如果您啟用此選項，請從 [選擇 Miracast 通道] 中選取用來投影內容的 Miracast 通道。|
|**選擇歡迎使用畫面上所顯示的會議資訊**|如果您啟用此選項，則可以選擇將顯示在 [歡迎使用] 畫面之 [會議] 磚上的資訊。 您可以：<br /><br />-   **僅顯示召集人和時間**<br />-   **顯示召集人、時間和主旨 (私人會議會隱藏主旨)**|
|**鎖定畫面背景影像 URL**|啟用此設定，以從您指定的 URL 顯示 Windows 10 團隊版裝置 [歡迎使用] 畫面上的自訂背景。<br /><br />影像必須是 PNG 格式，而且 URL 的開頭必須是 https://.|


### 請參閱
[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO1-->


