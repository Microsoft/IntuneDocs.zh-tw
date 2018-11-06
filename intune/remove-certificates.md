---
title: 在 Microsoft Intune 中移除 SCEP 或 PKCS 憑證 - Azure | Microsoft Docs
titleSuffix: ''
description: 系統管理員可以使用抹除或淘汰動作，自 Microsoft Intune 移除憑證。 在某些情況下，系統會自動移除憑證，例如取消註冊裝置或移除合規性政策。 在某些情況下，憑證會自動保留在裝置上，例如在 Intune 授權遺失或遭到移除時。 了解各自在 Android、Android Enterprise、iOS、macOS 和 Windows 裝置上的不同方式。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d4287322fd494c97cf24feb8cc16435a4405f2af
ms.sourcegitcommit: 7a649a5995600fb91817643e20a5565caedbb8f2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2018
ms.locfileid: "50150096"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>在 Microsoft Intune 中移除 SCEP 和 PKCS 憑證

在 Microsoft Intune 中，您可以將 SCEP 和 PKCS 憑證新增至裝置。 您也可以在[抹除](devices-wipe.md#wipe)或[淘汰](devices-wipe.md#retire)裝置時移除這些憑證。 在其他情況下，系統會自動移除憑證；還有某些情況是憑證會保留在裝置上。

本文列出一些常見的案例，以及對 PKCS 和 SCEP 憑證的影響。

> [!NOTE]
> 若要為正在從 Active Directory (AD) 或 Azure AD 中移除的使用者移除並撤銷憑證，請務必依序執行下列步驟：
>
>    1. 抹除或淘汰使用者的裝置
>    2. 從 AD 或 Azure AD 中移除使用者

## <a name="windows-devices"></a>Windows 裝置

#### <a name="scep-certificates"></a>SCEP 憑證

- 在下列情況中，系統會撤銷「並」移除 SCEP 憑證：

  - 終端使用者取消註冊
  - 系統管理員執行[抹除](devices-wipe.md#wipe)動作
  - 系統管理員執行[淘汰](devices-wipe.md#retire)動作
  - 從 Azure Active Directory (AD) 群組中移除裝置
  - 從群組指派中移除合規性原則
  - 從群組指派中移除組態設定檔

- 在下列情況中，系統會撤銷 SCEP 憑證：
  - 系統管理員變更或更新 SCEP 設定檔

- 在下列情況中，系統會移除根憑證：
  - 終端使用者取消註冊
  - 系統管理員執行[抹除](devices-wipe.md#wipe)動作
  - 系統管理員執行[淘汰](devices-wipe.md#retire)動作
  - 從群組指派中移除合規性原則

- 在下列情況中，SCEP 憑證會**保留**在裝置上 (未撤銷或移除憑證)：
  - 終端使用者遺失 Intune 授權
  - 系統管理員撤銷 Intune 授權
  - 系統管理員從 Azure AD 移除使用者或群組

#### <a name="pkcs-certificates"></a>PKCS 憑證

- 在下列情況中，系統會撤銷「並」移除 PKCS 憑證：

  - 終端使用者取消註冊
  - 系統管理員執行[抹除](devices-wipe.md#wipe)動作
  - 系統管理員執行[淘汰](devices-wipe.md#retire)動作

- 在下列情況中，系統會移除根憑證：
  - 終端使用者取消註冊
  - 系統管理員執行[抹除](devices-wipe.md#wipe)動作
  - 系統管理員執行[淘汰](devices-wipe.md#retire)動作

- 在下列情況中，PKCS 憑證會**保留**在裝置上 (未撤銷或移除憑證)：
  - 終端使用者遺失 Intune 授權
  - 系統管理員撤銷 Intune 授權
  - 系統管理員從 Azure AD 移除使用者或群組
  - 系統管理員變更或更新 PKCS 設定檔
  - 從群組指派中移除組態設定檔
  - 從群組指派中移除合規性原則 


## <a name="ios-devices"></a>iOS 裝置

#### <a name="scep-certificates"></a>SCEP 憑證

- 在下列情況中，系統會撤銷「並」移除 SCEP 憑證：

  - 終端使用者取消註冊
  - 系統管理員執行[抹除](devices-wipe.md#wipe)動作
  - 系統管理員執行[淘汰](devices-wipe.md#retire)動作
  - 從 Azure Active Directory (AD) 群組中移除裝置
  - 從群組指派中移除合規性原則
  - 從群組指派中移除組態設定檔

- 在下列情況中，系統會撤銷 SCEP 憑證：
  - 系統管理員變更或更新 SCEP 設定檔

- 在下列情況中，系統會移除根憑證：
  - 終端使用者取消註冊
  - 系統管理員執行[抹除](devices-wipe.md#wipe)動作
  - 系統管理員執行[淘汰](devices-wipe.md#retire)動作
  - 從群組指派中移除合規性原則

- 在下列情況中，SCEP 憑證會**保留**在裝置上 (未撤銷或移除憑證)：
  - 終端使用者遺失 Intune 授權
  - 系統管理員撤銷 Intune 授權
  - 系統管理員從 Azure AD 移除使用者或群組

#### <a name="pkcs-certificates"></a>PKCS 憑證

- 在下列情況中，系統會撤銷「並」移除 PKCS 憑證：

  - 終端使用者取消註冊
  - 系統管理員執行[抹除](devices-wipe.md#wipe)動作
  - 系統管理員執行[淘汰](devices-wipe.md#retire)動作

- 在下列情況中，系統會移除 PKCS 憑證：
  - 從群組指派中移除合規性原則
  - 從群組指派中移除組態設定檔
  
- 在下列情況中，系統會移除根憑證：
  - 終端使用者取消註冊
  - 系統管理員執行[抹除](devices-wipe.md#wipe)動作
  - 系統管理員執行[淘汰](devices-wipe.md#retire)動作

- 在下列情況中，PKCS 憑證會**保留**在裝置上 (未撤銷或移除憑證)：
  - 終端使用者遺失 Intune 授權
  - 系統管理員撤銷 Intune 授權
  - 系統管理員從 Azure AD 移除使用者或群組
  - 系統管理員變更或更新 PKCS 設定檔

## <a name="android--android-enterprise-devices"></a>Android 與 Android Enterprise 裝置

#### <a name="scep-certificates"></a>SCEP 憑證

- 在下列情況中，系統會撤銷「並」移除 SCEP 憑證：
  - 終端使用者取消註冊
  - 系統管理員執行[抹除](devices-wipe.md#wipe)動作

- 在下列情況中，系統會撤銷 SCEP 憑證：
  - 系統管理員執行[淘汰](devices-wipe.md#retire)動作
  - 從 Azure Active Directory (AD) 群組中移除裝置
  - 從群組指派中移除合規性原則
  - 從群組指派中移除組態設定檔
  - 系統管理員從 Azure Active Directory (AD) 移除使用者或群組
  - 系統管理員變更或更新 SCEP 設定檔

- 在下列情況中，系統會移除根憑證：
  - 終端使用者取消註冊
  - 系統管理員執行[抹除](devices-wipe.md#wipe)動作
  - 系統管理員執行[淘汰](devices-wipe.md#retire)動作

- 在下列情況中，SCEP 憑證會**保留**在裝置上 (未撤銷或移除憑證)：
  - 終端使用者遺失 Intune 授權
  - 系統管理員撤銷 Intune 授權
  - 系統管理員從 Azure AD 移除使用者或群組

#### <a name="pkcs-certificates"></a>PKCS 憑證

- 在下列情況中，系統會撤銷「並」移除 PKCS 憑證：

  - 終端使用者取消註冊
  - 系統管理員執行[抹除](devices-wipe.md#wipe)動作
  - 系統管理員執行[淘汰](devices-wipe.md#retire)動作

- 在下列情況中，系統會移除根憑證：
  - 終端使用者取消註冊
  - 系統管理員執行[抹除](devices-wipe.md#wipe)動作
  - 系統管理員執行[淘汰](devices-wipe.md#retire)動作

- 在下列情況中，PKCS 憑證會**保留**在裝置上 (未撤銷或移除憑證)：
  - 終端使用者遺失 Intune 授權
  - 系統管理員撤銷 Intune 授權
  - 系統管理員從 Azure AD 移除使用者或群組
  - 系統管理員變更或更新 PKCS 設定檔
  - 從群組指派中移除組態設定檔
  - 從群組指派中移除合規性原則 

## <a name="macos-certificates"></a>macOS 憑證

#### <a name="scep-certificates"></a>SCEP 憑證

- 在下列情況中，系統會撤銷「並」移除 SCEP 憑證：
  - 終端使用者取消註冊
  - 系統管理員執行[淘汰](devices-wipe.md#retire)動作
  - 從 Azure Active Directory (AD) 群組中移除裝置
  - 從群組指派中移除合規性原則
  - 從群組指派中移除組態設定檔

- 在下列情況中，系統會撤銷 SCEP 憑證：
  - 系統管理員變更或更新 SCEP 設定檔

- 在下列情況中，SCEP 憑證會**保留**在裝置上 (未撤銷或移除憑證)：
  - 終端使用者遺失 Intune 授權
  - 系統管理員撤銷 Intune 授權
  - 系統管理員從 Azure AD 移除使用者或群組

> [!NOTE]
> 不支援使用[抹除](devices-wipe.md#wipe)動作將 macOS 裝置恢復為出廠預設值。

#### <a name="pkcs-certificates"></a>PKCS 憑證

macOS 不支援 PKCS 憑證。

