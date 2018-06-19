---
title: 開啟 Windows Defender | Microsoft Docs
description: 了解如何開啟 Windows Defender 來存取公司資源。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/08/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d16dd2de-3ed5-474f-a04b-36dcd350162c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: shburbid
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 9190282edb8d356d7d43a634d10991a4b4c19c16
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31018493"
---
# <a name="turn-on-windows-defender-to-access-company-resources"></a>開啟 Windows Defender 來存取公司資源

您的工作單位或學校想要確保裝置存取資源時的安全性。 有幾種方式可使用 Windows 的內建保護 [Windows Defender](https://www.microsoft.com/safety/pc-security/windows-defender.aspx)，來抵禦惡意軟體。

您可能需要變更一些 Windows Defender 的設定，修正任何存取問題。 這些步驟可能需要您前往電腦上幾個不同的地方。

## <a name="turn-on-windows-defender"></a>開啟 Windows Defender

1. 開啟 [開始] 中的 [控制台]。
2. 開啟 [系統管理工具] > [編輯群組原則]。 這會在新視窗中開啟 [本機群組原則編輯器]。
3. 開啟 [電腦設定] > [系統管理範本] > [Windows 元件] > [Windows Defender 防毒軟體]。 [關閉 Windows Defender 防毒軟體] 設定位在其他設定的資料夾下。 
4. 開啟 [關閉 Windows Defender 防毒軟體] 並確定它設為 [停用] 或 [未設定]。

## <a name="turn-on-real-time-protection"></a>開啟即時保護

請前往 [開始] 並搜尋 [Windows Defender 資訊安全中心]，檢查並確定已開啟 [即時保護]。 選取 [病毒與威脅防護設定] 並確認 [即時保護] 和 [雲端提供的保護] 都切換成 [開啟]。 如未顯示這些選項，請執行下列作業啟用它們：

1. 開啟 [開始] 中的 [控制台]。
2. 開啟 [系統管理工具] > [編輯群組原則]。 這會在新視窗中開啟 [本機群組原則編輯器]。
3. 開啟 [電腦設定] > [系統管理範本] > [Windows 元件] >  [Windows Defender 資訊安全中心] > [病毒與威脅防護]。
4. 開啟 [Virus and threat protection area] (病毒與威脅防護區) 設定，並將它設為 [停用]。

## <a name="update-your-antivirus-definitions"></a>更新您的防毒定義

請前往 [開始] 並搜尋 [Windows Defender 資訊安全中心]，檢查並確定防毒定義為最新狀態。 選取 [防護更新] 和 [檢查更新] 來確定您的裝置有最新的病毒防護。 如果這個選項沒有出現，請遵循[開啟即時保護](turn-on-defender-windows.md#turn-on-real-time-protection)中的步驟

是否仍需要協助？ 請連絡您公司的支援人員。 如需其連絡資訊，請查看[公司入口網站](https://portal.manage.microsoft.com#HelpDeskDialog)。
