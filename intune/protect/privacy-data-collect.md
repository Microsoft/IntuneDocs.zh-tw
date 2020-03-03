---
title: Intune 中的資料收集
titleSuffix: Microsoft Intune
description: 了解如何在 Intune 中收集個人資料。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1171740-936d-46a5-af37-f418bd6fa63e
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bd204271b9ae3e57e15a101647444913749f4109
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514229"
---
# <a name="data-collection-in-intune"></a>Intune 中的資料收集

當使用者使用 Intune 註冊其公司或個人裝置時，Intune 會收集並共用某些個人資料。 Intune 會從下列來源收集個人資料：

- 系統管理員在 Azure 入口網站中使用的 Intune。
- 終端使用者裝置 (當他們註冊進行 Intune 管理且處於使用期間)。
- 客戶在第三方服務的帳戶 (根據系統管理員的指示)。
- 診斷、效能及使用量資訊。

從這些來源中，Intune 會收集可分為下列三個類別的資訊：[識別](#identified-data)、[匿名化](#pseudonymized-data)和[彙總](#aggregated-data)。

> [!NOTE]
> 基於任何原因，我們不會將我們的服務所收集的任何資料銷售給任何協力廠商。

## <a name="identified-data"></a>識別資料

Intune 所收集的大多數個人資料是識別資料。 此資料會繫結至使用者、裝置或應用程式，這對管理的性質來說特常重要。 識別資料用來管理使用者的裝置和應用程式，以及佈建 Intune 服務。

Intune 所收集的識別資料可能包括但不限於： 

- 使用者資訊
  - 擁有者名稱/使用者顯示 (由 AzureUserID 所識別之使用者的 Azure 註冊名稱)
  - 使用者主體名稱或電子郵件位址
  - 協力廠商使用者識別 (例如 AppleID)
- 硬體清查資訊
  - 裝置名稱
  - 製造商
  - 作業系統
  - 序號
  - IMEI 編號
  - IP 位址
  - Wi-Fi Mac 地址
  - ICCID
  - 電話號碼
- 稽核記錄資訊，包括下列活動的相關資料
  - 管理
  - 建立
  - 更新 (編輯)
  - 刪除
  - 指派
  - 遠端工作
- 支援資訊
  - 連絡資訊 (姓名、電話號碼、電子郵件地址)
  - 與 Microsoft 支援服務、產品及/或客戶體驗小組成員以電子郵件傳送討論
- 存取控制資訊 (Intune 使用此資料來管理對管理角色的存取權，並透過[角色型存取控制](../fundamentals/role-based-access-control.md)之類的功能運作。
  - 靜態驗證器 (客戶密碼)
  - 憑證的隱私金鑰 
- 管理員和帳戶資訊
  - 管理使用者的名字和姓氏
  - 管理員使用者名稱
  - UPN (電子郵件)
  - 電話號碼
  - 帳戶擁有者的電子郵件地址
  - 每一位客戶 IT 管理員的 Active Directory 識別碼
  - 客戶帳單的付款方式資料
  - 訂用帳戶金鑰
- 應用程式清查，如
  - 應用程式名稱
  - 版本
  - 應用程式識別碼
  - 大小
  - 安裝位置
  - 只有在管理員標記為公司擁有的裝置時，或相容的應用程式功能已開啟時，才會收集應用程式清查資料。  
- 客戶協力廠商的租用戶識別碼，例如 Apple ID。 

## <a name="pseudonymized-data"></a>匿名化資料

匿名化資料與唯一識別碼建立關聯，通常是系統所產生的數字，無法自行識別個人，但是會用來傳遞企業服務給使用者。 

Intune 所收集的匿名化資料可能包括但不限於： 

- 診斷、效能及使用方式資料繫結至使用者及/或裝置
  - 使用功能的次數
  - 提供給功能的命令
  - 服務的回應時間
  - 安裝和其他程序的成功率
  - Intune 公司入口網站應用程式錯誤
  - 使用者和裝置識別碼
  - 用於參考、相互關聯、管理目的的識別碼 
- 裝置資料未繫結至裝置或使用者 (如果此資料繫結至裝置或使用者，Intune 會將它識別為資料)
  - Intune 裝置識別碼
  - Azure Active Directory 裝置識別碼
  - Intune 裝置管理識別碼
  - 租用戶識別碼
  - 帳戶識別碼
  - EAS 裝置識別碼
  - 平台特定識別碼
  - iOS/iPadOS 裝置的 AppleID
  - 適用於 Mac 裝置的 Mac 位址
  - 適用於 Windows 裝置的 Windows 識別碼
- 受控應用程式資訊
  - 受控應用用程式識別碼
  - 受控應用程式裝置標籤
  - Intune 裝置管理識別碼
  - Azure Active Directory 裝置識別碼
  - 加密金鑰

## <a name="aggregated-data"></a>彙總資料

彙總資料用來佈建及改善 Intune 服務。 

Intune 所收集的彙總資料可能包括但不限於： 

- 來自所有 Intune 租用戶的管理員使用方式資料 (例如，與管理員主控台互動時，選取管理員控制項)
- 租用戶帳戶資訊 (此資料可從 Intune 刀鋒視窗取得)
  - 已註冊的裝置或使用者數目
  - 識別的裝置平台數目  
  - 已安裝的裝置數目
  - installedDeviceCount：應用程式安裝所在的裝置數目。
  - notApplicableDeviceCount：應用程式不適用的裝置數目。
  - notInstalledDeviceCount：應用程式適用但未安裝的裝置數目。
  - pendingInstallDeviceCount：應用程式適用但安裝暫止中的裝置數目。

## <a name="next-steps"></a>後續步驟

深入了解 Intune 如何[儲存和處理](privacy-data-store-process.md)並[共用](privacy-data-secure-share.md)個人資料。 
