---
title: "Windows 團隊版設定原則設定"
description: "使用 Microsoft Intune **Windows 10 團隊版一般設定原則** 為已註冊的 Windows 10 團隊版裝置進行設定，例如 Microsoft Surface Hub。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d8d0ec02fccd7aff391d794f4db4c5c2db03c4dd
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2017
---
# <a name="windows-team-configuration-policy-settings-in-microsoft-intune"></a>Microsoft Intune 的 Windows 團隊版設定原則設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用 Microsoft Intune **Windows 10 團隊版一般設定原則**為已註冊的 Windows 10 團隊版裝置進行設定，例如 Microsoft Surface Hub。

|設定名稱|詳細資料|
|----------------|-----------|
|**可在室內有人時自動喚醒螢幕**|可在裝置感應器偵測到室內有人時自動喚醒裝置。|
|**需要 PIN 碼以進行無線投影**|您必須先指定是否輸入 PIN 碼，才可以使用裝置的無線投影功能。|
|**設定裝置更新的維護時段**|設定可以進行裝置更新的間隔。 您可以設定間隔的開始時間和持續時間 (從 1 到 5 小時) 。|
|**啟用 Azure Operational Insights**|Azure Operational Insights，Microsoft Operations Manager 套件組合會收集、儲存及分析來自 Windows 10 團隊版的記錄檔資料。<br /><br />若要連線到 Azure Operational Insights，您必須指定 [工作區識別碼] 和 [工作區金鑰]。|
|**啟用 Miracast 無線投影**|如果您想要讓 Windows 10 團隊版裝置使用支援 Miracast 的裝置來投影，請啟用此選項。<br /><br />如果啟用此選項，請從 [選擇 Miracast 頻道] 選取用來投影的 Miracast 頻道。|
|**選擇要顯示在歡迎畫面上的會議資訊**|如果您啟用此選項，則可以選擇將顯示在 [歡迎使用] 畫面之 [會議] 磚上的資訊。 您可以：<br /><br />-   **僅顯示召集人和時間**<br />-   **顯示召集人、時間和主旨 (不會顯示私人會議的主旨)**|
|**鎖定畫面背景圖片 URL**|啟用此設定以在 Windows 10 團隊版裝置的 [歡迎] 畫面顯示來自指定 URL 的自訂背景。<br /><br />影像必須是 PNG 格式，而且 URL 的開頭必須是 **https://**。|


### <a name="see-also"></a>另請參閱
[使用 Microsoft Intune 原則管理裝置的設定及功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

