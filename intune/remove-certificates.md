---
title: 在 Microsoft Intune 中移除 SCEP 或 PKCS 憑證 - Azure | Microsoft Docs
titleSuffix: ''
description: 系統管理員可以使用抹除或淘汰動作，自 Microsoft Intune 移除憑證。 在某些情況下，系統會自動移除憑證，例如取消註冊裝置或移除合規性政策。 在某些情況下，憑證會自動保留在裝置上，例如在 Intune 授權遺失或遭到移除時。 了解各自在 Android、Android Enterprise、iOS、macOS 和 Windows 裝置上的不同方式。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: lacranda
ms.openlocfilehash: e5d6bf546a67ef36107aa566de299397959190e3
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2019
ms.locfileid: "68374671"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>在 Microsoft Intune 中移除 SCEP 和 PKCS 憑證

在 Microsoft Intune 中，您可以使用簡單憑證註冊通訊協定 (SCEP) 與公開金鑰加密標準 (PKCS) 憑證設定檔將憑證新增到裝置。

您可以在[抹除](devices-wipe.md#wipe)或[淘汰](devices-wipe.md#retire)裝置時移除這些憑證。 在一些情況下，系統會自動移除憑證；還有一些情況是憑證會保留在裝置上。 本文列出一些常見的案例，以及對 PKCS 和 SCEP 憑證的影響。

> [!NOTE]
> 若要為正在從內部部署 Active Directory 或 Azure Active Directory (Azure AD) 中移除的使用者移除並撤銷憑證，請依序執行下列步驟：
>
> 1. 抹除或淘汰使用者的裝置。
> 2. 從內部部署 Active Directory 或 Azure AD 中移除使用者。

## <a name="manually-deleted-certificates"></a>手動刪除憑證

手動刪除憑證這種案例是會套用到所有平台與 SCEP 或 PKCS 憑證設定檔所佈建的憑證。 例如，使用者可能會在裝置仍由憑證原則作為目標時從裝置刪除憑證。

在此案例中，刪除憑證之後，下次裝置聯繫 Intune 時會被判定為不符合規範，因為它缺少預期的憑證。 Intune 接著會簽發新憑證以讓裝置重新符合規範。 系統會自動還原憑證，您不需要執行任何額外動作。

## <a name="windows-devices"></a>Windows 裝置

### <a name="scep-certificates"></a>SCEP 憑證

在下列情況中，系統會撤銷「並」  移除 SCEP 憑證：

- 使用者取消註冊。
- 系統管理員執行[抹除](devices-wipe.md#wipe)動作。
- 系統管理員執行[淘汰](devices-wipe.md#retire)動作。
- 從 Azure AD 群組中移除裝置。
- 從群組指派中移除憑證設定檔。

在下列情況中，系統會撤銷 SCEP 憑證：
- 系統管理員變更或更新 SCEP 設定檔。

在下列情況中，系統會移除根憑證：
- 使用者取消註冊。
- 系統管理員執行[抹除](devices-wipe.md#wipe)動作。
- 系統管理員執行[淘汰](devices-wipe.md#retire)動作。

在下列情況中，SCEP 憑證會*保留*在裝置上 (未撤銷或移除憑證)：
- 使用者遺失 Intune 授權。
- 系統管理員撤銷 Intune 授權。
- 系統管理員從 Azure AD 移除使用者或群組。

### <a name="pkcs-certificates"></a>PKCS 憑證

在下列情況中，系統會撤銷「並」  移除 PKCS 憑證：

- 使用者取消註冊。
- 系統管理員執行[抹除](devices-wipe.md#wipe)動作。
- 系統管理員執行[淘汰](devices-wipe.md#retire)動作。

在下列情況中，系統會移除根憑證：
- 使用者取消註冊。
- 系統管理員執行[抹除](devices-wipe.md#wipe)動作。
- 系統管理員執行[淘汰](devices-wipe.md#retire)動作。

在下列情況中，PKCS 憑證會*保留*在裝置上 (未撤銷或移除憑證)：
- 使用者遺失 Intune 授權。
- 系統管理員撤銷 Intune 授權。
- 系統管理員從 Azure AD 移除使用者或群組。
- 系統管理員變更或更新 PKCS 設定檔。
- 從群組指派中移除憑證設定檔。


## <a name="ios-devices"></a>iOS 裝置

### <a name="scep-certificates"></a>SCEP 憑證

在下列情況中，系統會撤銷「並」  移除 SCEP 憑證：

- 使用者取消註冊。
- 系統管理員執行[抹除](devices-wipe.md#wipe)動作。
- 系統管理員執行[淘汰](devices-wipe.md#retire)動作。
- 從 Azure AD 群組中移除裝置。
- 從群組指派中移除憑證設定檔。

在下列情況中，系統會撤銷 SCEP 憑證：
- 系統管理員變更或更新 SCEP 設定檔。

在下列情況中，系統會移除根憑證：
- 使用者取消註冊。
- 系統管理員執行[抹除](devices-wipe.md#wipe)動作。
- 系統管理員執行[淘汰](devices-wipe.md#retire)動作。

在下列情況中，SCEP 憑證會*保留*在裝置上 (未撤銷或移除憑證)：
- 使用者遺失 Intune 授權。
- 系統管理員撤銷 Intune 授權。
- 系統管理員從 Azure AD 移除使用者或群組。

### <a name="pkcs-certificates"></a>PKCS 憑證

在下列情況中，系統會撤銷「並」  移除 PKCS 憑證：

- 使用者取消註冊。
- 系統管理員執行[抹除](devices-wipe.md#wipe)動作。
- 系統管理員執行[淘汰](devices-wipe.md#retire)動作。

在下列情況中，系統會移除 PKCS 憑證：
- 從群組指派中移除憑證設定檔。

在下列情況中，系統會移除根憑證：
- 使用者取消註冊。
- 系統管理員執行[抹除](devices-wipe.md#wipe)動作。
- 系統管理員執行[淘汰](devices-wipe.md#retire)動作。

在下列情況中，PKCS 憑證會*保留*在裝置上 (未撤銷或移除憑證)：
- 使用者遺失 Intune 授權。
- 系統管理員撤銷 Intune 授權。
- 系統管理員從 Azure AD 移除使用者或群組。
- 系統管理員變更或更新 PKCS 設定檔。

## <a name="android-knox-devices"></a>Android KNOX 裝置

### <a name="scep-certificates"></a>SCEP 憑證

在下列情況中，系統會撤銷「並」  移除 SCEP 憑證：
- 使用者取消註冊。
- 系統管理員執行[抹除](devices-wipe.md#wipe)動作。

在下列情況中，系統會撤銷 SCEP 憑證：
- 系統管理員執行[淘汰](devices-wipe.md#retire)動作。
- 從 Azure AD 群組中移除裝置。
- 從群組指派中移除憑證設定檔。
- 系統管理員從 Azure AD 移除使用者或群組。
- 系統管理員變更或更新 SCEP 設定檔。

在下列情況中，系統會移除根憑證：
- 使用者取消註冊。
- 系統管理員執行[抹除](devices-wipe.md#wipe)動作。
- 系統管理員執行[淘汰](devices-wipe.md#retire)動作。

在下列情況中，SCEP 憑證會*保留*在裝置上 (未撤銷或移除憑證)：
- 使用者遺失 Intune 授權。
- 系統管理員撤銷 Intune 授權。
- 系統管理員從 Azure AD 移除使用者或群組。

### <a name="pkcs-certificates"></a>PKCS 憑證

在下列情況中，系統會撤銷「並」  移除 PKCS 憑證：

- 使用者取消註冊。
- 系統管理員執行[抹除](devices-wipe.md#wipe)動作。
- 系統管理員執行[淘汰](devices-wipe.md#retire)動作。

在下列情況中，系統會移除根憑證：
- 使用者取消註冊。
- 系統管理員執行[抹除](devices-wipe.md#wipe)動作。
- 系統管理員執行[淘汰](devices-wipe.md#retire)動作。

在下列情況中，PKCS 憑證會*保留*在裝置上 (未撤銷或移除憑證)：
- 使用者遺失 Intune 授權。
- 系統管理員撤銷 Intune 授權。
- 系統管理員從 Azure AD 移除使用者或群組。
- 系統管理員變更或更新 PKCS 設定檔。
- 從群組指派中移除憑證設定檔。


> [!NOTE]
> 上述案例不會驗證 Android for Work 裝置。
> Android 舊版裝置 (任何非 Samsung、非工作設定檔裝置) 不會啟用憑證移除功能。

## <a name="macos-certificates"></a>macOS 憑證

### <a name="scep-certificates"></a>SCEP 憑證

在下列情況中，系統會撤銷「並」  移除 SCEP 憑證：
- 使用者取消註冊。
- 系統管理員執行[淘汰](devices-wipe.md#retire)動作。
- 從 Azure AD 群組中移除裝置。
- 從群組指派中移除憑證設定檔。

在下列情況中，系統會撤銷 SCEP 憑證：
- 系統管理員變更或更新 SCEP 設定檔。

在下列情況中，SCEP 憑證會*保留*在裝置上 (未撤銷或移除憑證)：
- 使用者遺失 Intune 授權。
- 系統管理員撤銷 Intune 授權。
- 系統管理員從 Azure AD 移除使用者或群組。

> [!NOTE]
> 不支援使用[抹除](devices-wipe.md#wipe)動作將 macOS 裝置恢復為出廠預設值。

### <a name="pkcs-certificates"></a>PKCS 憑證

macOS 不支援 PKCS 憑證。

