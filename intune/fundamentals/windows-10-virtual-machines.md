---
title: 搭配 Microsoft Intune 使用 Windows 10 虛擬機器
titleSuffix: ''
description: 適用於搭配 Microsoft Intune 使用 Windows 10 虛擬機器的指導方針
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 486ca7eae1b1e8b016f44c735ec04a23145421a8
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124974"
---
# <a name="using-windows-10-virtual-machines-with-intune"></a>搭配 Intune 使用 Windows 10 虛擬機器

Intune 支援搭配特定限制管理執行 Windows 10 企業版的虛擬機器。 Intune 管理無須依賴也不會干擾相同虛擬機器上的 Windows 虛擬桌面管理。

搭配 Intune 管理 Windows 10 VM 時，請留意下列幾點：

## <a name="enrollment"></a>註冊
- 我們不建議搭配 Intune 管理隨選、工作階段主機虛擬機器。 必須在建立每個 VM 時註冊它。 此外，定期刪除 VM 將會在 Intune 中留下孤立的裝置記錄，直到將它們[清除](../remote-actions/devices-wipe.md#automatically-delete-devices-with-cleanup-rules)為止。 
- 不支援 Windows Autopilot 自我部署與白手套部署類型，因為其需要實體信賴平台模組 (TPM)。 
- 在只能使用 RDP 存取的 VM (例如裝載在 Azure 上的 VM) 上，不支援全新體驗 (OOBE) 註冊。 這些限制代表：
    - 不支援 Windows Autopilot 和商業 OOBE。
    - 不支援裝置內容原則的 [註冊狀態頁面] 選項。

## <a name="configuration"></a>設定
Intune 不支援任何利用信賴平台模組或硬體管理的設定，包括：
- [BitLocker 設定](../configuration/device-profiles.md#endpoint-protection)
- [裝置韌體設定介面設定](../configuration/device-profiles.md#device-firmware-configuration-interface)

## <a name="reporting"></a>報告
Intune 會自動偵測虛擬機器，並在 [裝置]   > [所有裝置]  > 選擇裝置 > [概觀]   > [型號]  欄位中，將它們回報為 [虛擬機器]。 

已解除配置的虛擬機器可能會導致不符合規範的裝置報告，因為它們無法[簽入 Intune 服務](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)。

## <a name="retirement"></a>淘汰
如果您只有 RDP 存取，請不要使用[抹除動作](../remote-actions/devices-wipe.md#wipe)。 抹除動作將會刪除虛擬機器的 RDP 設定，並防止您再次連線。


