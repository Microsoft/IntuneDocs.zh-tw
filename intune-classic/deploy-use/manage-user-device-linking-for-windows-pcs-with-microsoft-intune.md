---
title: 管理 Windows 電腦的使用者裝置連結
description: 如何將使用者連結到受 Intune 管理的 Windows 電腦。
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 53c99d63-c312-442a-8a71-de1b10fcd39b
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 751355c34fc18cd9a1ededd498724d4652fc1368
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="manage-user-device-linking-for-windows-pcs"></a>管理 Windows 電腦的使用者裝置連結

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

本主題中的資訊僅適用於使用 Intune 軟體用戶端作為電腦所管理的 Windows 桌上型電腦。 

將軟體部署給使用者之前，您必須先將使用者連結到電腦。 您可以將一位使用者連結到多部電腦，但每一部電腦只能連結到一位使用者。 使用者會自動連結到他們在 Intune 中使用公司入口網站註冊的任何電腦。

將使用者連結到電腦：

1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [群組] &gt; [所有裝置]\ (或包含您想要連結至使用者之電腦的其他群組)。

2. 選取您想要連結使用者的電腦，然後選擇 [連結使用者]。

   [連結使用者] 對話方塊會顯示可用使用者清單，列出使用者的顯示名稱、使用者識別碼，以及每個使用者目前連結的電腦數目。 如果使用者已經連結到選取的電腦，該使用者的名稱和使用者識別碼便會顯示在 [目前使用者] 下方。 如果電腦未連結到任何使用者，[目前使用者] 下方將會出現 [沒有使用者]。

3. 請執行下列其中一項動作：

   - 若要讓電腦與目前的使用者保持連結 (如有)，請選擇 [取消]。

   - 若要移除與目前使用者的連結 (如果有的話)，請選擇 [移除連結]<strong>**&gt; [確定]**</strong>。

   - 若要將電腦連結到新的使用者，請在 [所有使用者] 清單中選取使用者。 請確認使用者資料是否正確，然後選擇 [確定]。

> [!TIP]
> 如果您想要限制終端使用者將自己連結到電腦的能力，請啟用 [Microsoft Intune 代理程式設定] 原則中的 [限制使用者將自己連結到電腦的能力] 選項。

### <a name="see-also"></a>另請參閱

[使用 Intune 軟體用戶端執行的一般 Windows 電腦管理工作](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)