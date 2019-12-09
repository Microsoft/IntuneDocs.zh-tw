---
title: 探索到的應用程式
titleSuffix: Microsoft Intune
description: 了解 Intune 在裝置上所找到已偵測應用程式的詳細資料。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: eff4ccdc8b40da4d72394001b88446653ff71bd0
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564252"
---
# <a name="intune-discovered-apps"></a>Intune 探索到的應用程式

Intune **探索到的應用程式**是 Intune 在您租用戶中已註冊裝置上所偵測到應用程式清單。 該清單可作為您租用戶的軟體清查。 **探索到的應用程式**其報表不同於[應用程式安裝](apps-monitor.md)報表。 針對個人裝置，Intune 一律不會收集非受控應用程式的資訊。 在公司裝置上，會針對此報表收集所有應用程式 (不論是否為受控應用程式)。 以下是與預期行為對應的資料表。 一般而言，報表會從註冊後開始每 7 天重新整理一次 (而不是針對整個租用戶每週重新整理)。 此重新整理期間的唯一例外狀況是，透過 Win32 應用程式 Intune 管理延伸模組所收集的應用程式資訊會每 24 小時收集一次。

## <a name="monitor-discovered-apps-with-intune"></a>使用 Intune 來監視探索到的應用程式

Intune 提供在您的租用戶中已註冊 Intune 之裝置上偵測到之應用程式的彙總清單。

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [監視]   > [探索到的應用程式]  。

>[!NOTE]
>您可以從 [探索到的應用程式]  窗格中選取 [匯出]  ，將探索到的應用程式清單匯出至 .csv 檔案。
>
>針對探索到的 Win32 應用程式，目前沒有彙總計數。 此類型的資料只能以每個裝置為基礎來檢視。

Intune 也會提供在您的租用戶中個別裝置上探索到的應用程式清單。

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [所有裝置]  。
3. 選取一個裝置。
4. 若要檢視針對此裝置探索到的應用程式，請在 [監視器]  區段中選取 [探索到的應用程式]  。

## <a name="details-of-discovered-apps"></a>探索到的應用程式詳細資料

下列清單提供應用程式平台類型、針對個人裝置監視的應用程式、針對公司裝置監視的應用程式，以及重新整理週期。 如需 Intune 所支援應用程式類型的詳細資訊，請參閱 [Microsoft Intune 中的應用程式類型](apps-add.md#app-types-in-microsoft-intune)。

| 平台 | 針對個人擁有的裝置 | 針對公司擁有的裝置 | 重新整理週期 |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Windows 10 (Win32 應用程式) 注意：[需要裝置上的 Intune 管理延伸模組](intune-management-extension.md) | 不適用 | 在新增移除程式清單中找到的所有 Win32 應用程式 | 裝置註冊後每 24 小時 |
| Windows 10 (現代化應用程式) | 僅限受控的現代化應用程式 | 安裝於裝置上的所有應用程式 | 裝置註冊後每 7 天 |
| Windows 8.1 | 僅限受管理的應用程式 | 僅限受管理的應用程式 | 裝置註冊後每 7 天 |
| Windows Phone 8 | 僅限受管理的應用程式 | 僅限受管理的應用程式 | 裝置註冊後每 7 天 |
| Windows RT | 僅限受管理的應用程式 | 僅限受管理的應用程式 | 裝置註冊後每 7 天 |
| iOS | 僅限受管理的應用程式 | 安裝在裝置上的所有應用程式 | 裝置註冊後每 7 天 |
| macOS | 安裝在裝置上的所有應用程式 | 安裝在裝置上的所有應用程式 | 裝置註冊後每 7 天 |
| Android | 僅限受管理的應用程式 | 安裝在裝置上的所有應用程式 | 裝置註冊後每 7 天 |
| Android 企業 | 僅限受管理的應用程式 | 僅限在工作設定檔中安裝的應用程式 | 裝置註冊後每 7 天 |

> [!NOTE]
> Windows 10 已加入混合式 Azure AD 的裝置 (如 Configuration Manager 的應用程式管理工作負載中所示) 目前不會根據上述排程，透過 Intune 管理擴充功能 (IME) 來收集應用程式清查。 若要減緩此問題，應將 Configuration Manager 中的應用程式管理工作負載切換至 Intune，以便將 IME 安裝於裝置上 (Win32 清查和 PowerShell 部署都需要 IME)。 請注意，此行為的任何變更或更新，都會在[開發中](../fundamentals/in-development.md)和/或[新功能](../fundamentals/whats-new.md)中公告。

已探索的應用程式數目可能不符合應用程式安裝狀態計數。 不一致的可能性包括：

- 已安裝受控應用程式的目標變更可能會導致狀態窗格中的安裝計數減少，但仍然會在已偵測的應用程式中回報。
- 由於可能的使用者或裝置重疊，租用戶中相同應用程式的目標多執行個體將會導致不同的計數。 應用程式的每個執行個體都會計算重複的使用者，但已探索的應用程式將會有重複的計數。
- 已探索的應用程式與應用程式狀態是在不同的時間間隔收集，這會導致應用程式計數不一致。

## <a name="next-steps"></a>後續步驟

- [Microsoft Intune 中的應用程式類型](apps-add.md#app-types-in-microsoft-intune)
- [使用 Microsoft Intune 監視應用程式資訊和指派](apps-monitor.md)
