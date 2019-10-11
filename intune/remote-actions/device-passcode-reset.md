---
title: 使用 Microsoft Intune 重設裝置密碼 - Azure | Micrososft Docs
description: 使用您以 Intune 管理或監視之裝置上的移除密碼動作，移除或重設密碼。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 34aea5256ebb7d6577b4e77054dcca63d47bf317
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728581"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>在 Intune 中重設或移除裝置密碼

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文件將討論裝置層級密碼重設，以及 Android Enterprise (之前稱為 Android for Work 或 AfW) 裝置上的工作設定檔密碼重設。 由於需求各自不同，因此，請務必注意這兩者之間的差異。 裝置層級密碼重設會重設整部裝置的密碼。 工作設定檔密碼重設只會重設 Android Enterprise 裝置上的使用者工作設定檔。

## <a name="supported-platforms-for-device-level-passcode-reset"></a>支援裝置層級密碼重設的平台

| 平台 | 是否支援？ |
| ---- | ---- |
| 版本為 6.x 或更舊版本的 Android 裝置 | 是 |
| Kiosk 模式的 Android Enterprise 裝置 | 是 |
| iOS 裝置 | 是 |
| 已透過使用者註冊進行註冊的 iOS 裝置 | 否 |
| 已透過工作設定檔進行註冊的 Android 裝置 | 否 |
| 版本為 7.0 或更新版本的 Android 裝置 | 否 |
| macOS | 否 |
| Windows | 否 |

針對 Android 裝置，這表示只有在執行 6.x 或更舊版本的裝置或以 Kiosk 模式執行的 Android Enterprise 裝置上，才支援裝置層級密碼重設。 這是因為 Google 移除了裝置系統管理員授權應用程式內對 Android 7 裝置驗證碼/密碼重設的支援，這適用於所有 MDM 廠商。

## <a name="supported-platforms-for-android-enterprise-work-profile-passcode-reset"></a>支援 Android Enterprise 工作設定檔密碼重設的平台

| 平台 | 是否支援？ |
| ---- | ---- |
| 以工作設定檔註冊並執行 8.0 版及更新版本的 Android Enterprise 裝置 | 是 |
| 以工作設定檔註冊並執行 7.x 版及更舊版本的 Android Enterprise 裝置 | 否 |
| 執行 7.x 版及更舊版本的 Android 裝置 | 否 |

若要建立新的工作設定檔密碼，請使用 [重設密碼] 動作。 此動作會提示密碼重設，並僅針對工作設定檔建立新的暫時密碼。 

## <a name="reset-a-passcode"></a>重設密碼


1. 使用下列任一角色登入 [Azure 入口網站](https://portal.azure.com)：Azure Active Directory 全域管理員、Azure Active Directory Intune 服務管理員、技術服務人員或角色管理員。
2. 選取 [所有服務]  ，篩選 [Intune]  ，然後選取 [Microsoft Intune]  。
3. 選取 [裝置]  ，然後選取 [所有裝置]  。
4. 從您管理的裝置清單中選取裝置，再選擇 [...More] (...其他)  。 然後選擇 [Remove passcode] (移除密碼)  裝置遠端動作。

## <a name="reset-android-work-profile-passcodes"></a>重設 Android 工作設定檔密碼

以工作設定檔註冊的支援 Android Enterprise 裝置會收到新受控設定檔解除鎖定密碼，或終端使用者的受控設定檔查問。

針對執行 8.x 或更新版本並以工作設定檔註冊的 Android Enterprise 裝置，終端使用者在完成註冊之後，會立即收到啟用重設密碼的通知。 如果工作設定檔密碼為必要且已設定，就會顯示通知。 輸入其密碼之後，就會關閉通知。


## <a name="remove-ios-passcodes"></a>移除 iOS 密碼

請不要重設密碼，而是將它從 iOS 裝置中移除。 如果已設定密碼合規性政策，裝置會提示使用者在 [設定] 中設定新密碼。

## <a name="next-steps"></a>後續步驟

若要查看您剛採取的動作狀態，請在 [裝置]  中選擇 [裝置動作]  。
