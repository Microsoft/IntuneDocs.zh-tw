---
title: JAMF Pro 傳送至 Intune 的資料
titleSuffix: Microsoft Intune
description: 當您整合 Jamf Pro 以使用 Intune 管理 Mac 時，請檢閱 Jamf Pro 傳送給 Microsoft Intune 的資料清單。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86f2f47322e668815d1ff37ce6c2de1e4d6cdc16
ms.sourcegitcommit: 99b74d7849fbfc8f5cf99cba33e858eeb9f537aa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68670906"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Jamf Pro 傳送至 Intune 的資料

當您搭配 Intune 使用 [Jamf Pro](https://www.jamf.com) 來管理終端使用者的 Mac 時，Jamf Pro 會擷取受控 macOS 裝置的清查資訊。 Jamf Pro 會將下列資訊回報給 Intune：

* 裝置 Azure AD 識別碼
* JAMF 清查狀態 (過去 24 小時內使用 Jamf Pro 簽入之電腦的清查狀態)
* 作業系統版本
* 使用者 Azure AD 識別碼
* 已加密 (FileVault 2)
* 閘道管理員狀態
* 密碼：字元集數目下限
* 密碼到期 (天數)
* 密碼類型：簡單、英數字元，或不明
* 避免自動登入
* 必要的密碼長度
* 密碼：避免重複使用的舊密碼數目
* 系統完整性保護
* 上次簽入時間
* 架構類型
* 可用的 RAM 插槽
* 電池容量
* 開機 ROM
* 匯流排速度
* 快取大小
* 裝置名稱
* 加入網域
* Jamf 識別碼
* MAC 位址
* 品牌
* 型號
* 型號識別碼
* NIC 速度
* 核心數目
* 處理器數目
* OS
* 平台
* 處理器速度
* 處理器類型
* 次要 MAC 位址
* 序號
* SMC 版本
* RAM 總計
* UDID
* 使用者電子郵件


您可以在 [所有裝置]  檢視中選取 [刪除]  ，以從 Intune 主控台移除 Jamf 受控裝置。 選取多個裝置，並按一下 [刪除]  ，即可啟用刪除大量裝置。

在 Jamf Pro 文件中取得如何[移除 Jamf 受控裝置](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)的相關資訊。您也可以透過 [Jamf 支援](https://www.jamf.com/support/)提出支援票證，以取得其他支援。 

