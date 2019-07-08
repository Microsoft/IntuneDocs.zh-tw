---
title: 尋找 Microsoft Intune 裝置的主要使用者。
titleSuffix: ''
description: 尋找 Intune 裝置的主要使用者 (或使用者裝置親和性)。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 21f62ad44d992d1f4adbb1945bdba02e526d9138
ms.sourcegitcommit: 2db7dc2baea0c159f70338e6a0529acc89580773
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67500641"
---
# <a name="find-the-primary-user-of-an-intune-device"></a>尋找 Intune 裝置的主要使用者

主要使用者 (也就是使用者裝置親和性) 是每個 Intune 裝置的屬性。 您可以為 Intune 裝置指派零或一位主要使用者。 若未指派任何主要使用者，即會將裝置稱為「共用裝置」。

## <a name="how-to-find-a-devices-primary-user"></a>如何尋找裝置的主要使用者

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選擇 [裝置]  > 選擇裝置。
3. 在 [概觀]  頁面上，選擇 [查看更多]  ，您將會看到列出的主要使用者。

## <a name="what-is-the-primary-user"></a>什麼是主要使用者？
主要使用者屬性可在下列位置，用來將授權的 Intune 使用者對應至其裝置：
- 公司入口網站應用程式
- 終端使用者網站
- IT 專業人員體驗，例如對 Azure 入口網站中的頁面進行疑難排解。 這些頁面會使用主要使用者，將使用者帳戶對應至裝置。    

### <a name="company-portal-app"></a>公司入口網站應用程式
公司入口網站應用程式預期登入公司入口網站的使用者帳戶為該裝置的主要使用者。 如果已將另一位使用者指派為主要使用者，公司入口網站就會顯示一則警告：

「已經將此裝置指派給貴組織中的其他人。 請洽詢公司支援人員，以了解如何成為主要裝置使用者。 您可以繼續使用公司入口網站，但功能將會受到限制。」

若未為 Intune 裝置指派任何主要使用者，則公司入口網站應用程式會將它偵測為共用裝置。 共用裝置可以視覺方式來識別，其會在裝置圖格上顯示「共用」標籤。 在此模式中，公司入口網站仍可用來要求並安裝可用的應用程式。 不過，無法使用自助動作 (重設/重新命名/淘汰)。  

若要顯示於共用裝置上的公司入口網站中，必須將可用的應用程式指派給使用者群組。 系統會根據 IT 系統管理員設定應用程式的方式，將其安裝於系統內容或使用者內容中。 如需應用程式內容的詳細資訊，請參閱[在 Windows 10 裝置上安裝應用程式](apps-windows-10-app-deploy.md#installing-apps-on-windows-10-devices)。 需要有公司入口網站版本 10.3.4651.0 或更新版本，才能使用此功能。


## <a name="who-is-assigned-as-the-primary-user"></a>要將哪位人員指派為主要使用者？
Intune 會在註冊期間或之後，自動將主要使用者新增至裝置。 註冊方法會判斷何時要將主要使用者新增至裝置。

| 平台 | 註冊方法 | 已指派主要使用者 | 已指派主要使用者 |
| ---- | ---- | ---- | ---- |
| Windows | 新增公司或學校 (使用者導向) | 正在註冊使用者 | 註冊期間 |   
| Windows | 新式應用程式登入 (使用者導向) | 正在註冊使用者 | 註冊期間 | 
| Windows | 只在 MDM 中註冊 (使用者導向) | 正在註冊使用者 | 註冊期間 | 
| Windows | Azure AD Join (全新體驗) | 正在註冊使用者 | 註冊期間 | 
| Windows | Azure AD Join (Autopilot 全新體驗) | 正在註冊使用者 | 註冊期間 | 
| Windows | 只在 MDM 中註冊 | 正在註冊使用者 | 註冊期間 | 
| Windows | 混合式 AADJ + 自動註冊 GPO | 第一位使用者登入 Windows | 當第一位使用者登入 Windows 時| 
| Windows | 共同管理 | 第一位使用者登入 Windows | 當第一位使用者登入 Windows 時 | 
| Windows | Azure AD Join (大量註冊權杖) | 無 | 不適用 | 
| Windows | Azure AD Join (Autopilot 自我部署模式) | 無 | 不適用 | 
| 跨平台 | 透過公司入口網站應用程式的使用者導向註冊 | 正在註冊使用者 | 註冊期間 |
| 跨平台 | 裝置註冊管理員 (DEM) | 正在註冊 DEM 使用者 | 註冊期間 |
| iOS、macOS | Apple 自動裝置註冊 (具有使用者親和性的 DEP) | 正在註冊使用者 | 註冊期間 |
| iOS、macOS | Apple 自動裝置註冊 (不具使用者親和性的 DEP) | 無 | 不適用 |
| Android | Android 公司擁有的專用裝置 | 無 | 不適用 |

## <a name="primary-user-and-azure-ad-device-owner"></a>主要使用者和 Azure AD 裝置擁有者
在某些情況下，Intune 主要使用者可能不同於 Azure AD 裝置的 [擁有者]  屬性 (可在 [裝置]   > [Azure AD 裝置]  下方檢視)。 Azure AD 裝置擁有者會在裝置註冊期間新增至 Azure Active Directory。

## <a name="next-steps"></a>後續步驟
[管理您的 Intune 裝置](device-management.md)。
