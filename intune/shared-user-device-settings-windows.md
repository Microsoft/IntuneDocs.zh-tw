---
title: Windows 10 共用裝置設定 - Microsoft Intune - Azure | Microsoft Docs
description: 在 Microsoft Intune 中新增和使用 Windows 10 來設定多位使用者共用或使用的裝置。 查看他們在裝置上進行的所有設定清單，包括 Microsoft Surface。 在裝置組態設定檔中控制來賓帳戶、管理帳戶和刪除非使用中的帳戶、允許或防止儲存至本機儲存體、設定電源和睡眠選項、選擇何時安裝更新，以及在教育環境中使用裝置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 707bb84df55fa202e3dc5241e3d7212039b17b3b
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55841737"
---
# <a name="windows-10-and-later-settings-to-manage-shared-devices-using-intune"></a>使用 Intune 管理共用裝置的 Windows 10 及更新版本設定

Windows 10 及更新版本裝置 (例如 Microsoft Surface) 可供許多使用者使用。 擁有多位使用者的裝置稱為共用裝置，且是行動裝置管理 (MDM) 解決方案的一部分。

使用 Microsoft Intune，終端使用者可以透過來賓帳戶來登入這些共用裝置。 當他們使用裝置時，只能存取您允許的功能。 身為 Intune 系統管理員，您可以為共用的 Windows 10 裝置設定存取權、選擇何時刪除帳戶、控制電源管理設定，以及執行其他作業。

本文列出並描述您可以在 Windows 10 (及更新版本) 裝置組態設定檔中使用的設定。 在 Intune 中建立設定檔之後，您可以將設定檔部署或指派給您組織中的裝置群組。 您也可以將此設定檔指派給具有混合裝置類型和 OS 版本的裝置群組。

如需這項 Intune 功能的詳細資訊，請參閱[控制共用電腦或多重使用者裝置上的存取權、帳戶和電源功能](shared-user-device-settings.md)。 如需 Windows CSP 的詳細資訊，請參閱 [SharedPC CSP](https://docs.microsoft.com/windows/client-management/mdm/sharedpc-csp)。

## <a name="before-your-begin"></a>開始之前

[建立設定檔](shared-user-device-settings.md)。

## <a name="shared-multi-user-device-settings"></a>共用的多重使用者裝置設定

- **共用電腦模式**：選擇 [啟用] 可開啟共用電腦模式。 在此模式中，一次只能有一位使用者登入裝置。 在第一位使用者登出之前，其他使用者無法登入。[未設定] (預設) 會保留這項設定不受 Intune 管理，且不會推送任何原則來控制裝置上的這項設定。
- **來賓帳戶**：在登入畫面上選擇建立來賓選項。 來賓帳戶不需要任何使用者認證或驗證。 這項設定會在每次使用時建立新的本機帳戶。 選項包括：
  - **來賓**：在本機裝置上建立來賓帳戶。
  - **網域**：在 Azure Active Directory (AD) 中建立來賓帳戶。
  - **來賓和網域**：在本機裝置和 Azure Active Directory (AD) 中建立來賓帳戶。
- **帳戶管理**：設定為 [啟用] 可自動刪除來賓所建立的本機帳戶，以及 AD 和 Azure AD 中的帳戶。 當使用者登出裝置或系統維護執行時，就會刪除這些帳戶。 啟用時，亦請設定：
  - **帳戶刪除**：選擇何時刪除帳戶：[At storage space threshold] \(達到儲存空間閾值\)、[At storage space threshold and inactive threshold] \(達到儲存空間閾值和非使用中閾值\) 或 [Immediately after log-out] \(登出後立即\)。另請輸入：
    - **開始刪除閾值 (%)**：輸入磁碟空間百分比 (0-100)。 當總磁碟/儲存空間低於您輸入的值時，則會刪除快取的帳戶。 它會繼續刪除帳戶以回收磁碟空間。 非使用中時間最長的帳戶會最先遭到刪除。
    - **停止刪除閾值 (%)**：輸入磁碟空間百分比 (0-100)。 當總磁碟/儲存空間達到您輸入的值時，則會停止刪除。

  設定為 [停用] 可保留來賓所建立的本機、AD 和 Azure AD 帳戶。

- **本機儲存體**：選擇 [啟用] 可防止使用者在裝置的硬碟中儲存和檢視檔案。 選擇 [停用] 可讓使用者使用檔案總管在本機查看和儲存檔案。 [未設定] (預設) 會保留這項設定不受 Intune 管理，且不會推送任何原則來控制裝置上的這項設定。
- **電源原則**：當設定為 [啟用] 時，使用者無法關閉休眠功能、無法覆寫所有睡眠動作 (例如關閉筆記電腦螢幕)，且無法變更電源設定。 當設定為 [停用] 時，使用者可以讓裝置休眠、關閉筆記電腦螢幕讓裝置睡眠，以及變更電源設定。 [未設定] (預設) 會保留這項設定不受 Intune 管理，且不會推送任何原則來控制裝置上的這項設定。
- **睡眠逾時 (秒)**：輸入裝置進入睡眠模式前閒置的秒數 (0-100)。 如果您未設定時間，裝置會在 60 分鐘後進入睡眠狀態。
- **當電腦喚醒時登入**：設定為 [啟用] 可要求使用者在裝置從睡眠模式喚醒時使用密碼登入。 選擇 [停用] 可讓使用者不需要輸入其使用者名稱和密碼。 [未設定] (預設) 會保留這項設定不受 Intune 管理，且不會推送任何原則來控制裝置上的這項設定。
- **維護開始時間 (從午夜開始以分鐘計)**：以分鐘 (0-1440) 為單位，輸入自動維護工作 (例如 Windows Update) 執行的時間。 預設開始時間是午夜或零 (`0`) 分鐘。 若要變更開始時間，請輸入從午夜開始以分鐘計的開始時間。 例如，如果您想要從上午 2 點開始進行維護，請輸入 `120`。 如果您想要從下午 8 點開始進行維護，請輸入 `1200`。
- **教育原則**：選擇 [啟用] 可使用針對學校用裝置建議的設定，這些設定的限制較嚴格。 選擇 [停用] 則不會使用預設和建議的教育原則。 [未設定] (預設) 會保留這項設定不受 Intune 管理，且不會推送任何原則來控制裝置上的這項設定。

  如需教育原則功能的詳細資訊，請參閱 [Windows 10 configuration recommendations for education customers](https://docs.microsoft.com/education/windows/configure-windows-for-education) (適用於教育客戶的 Windows 10 設定建議)。

## <a name="next-steps"></a>後續步驟

- [指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
- 請參閱 [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) 的設定。
