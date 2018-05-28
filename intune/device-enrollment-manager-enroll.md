---
title: 使用裝置註冊管理員帳戶註冊裝置
titlesuffix: Microsoft Intune
description: 使用裝置註冊管理員帳戶，在 Intune 中註冊裝置。 "
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a32eb1d65710bf09d61c0846a8d949d5cd99ed2
ms.sourcegitcommit: 91802e78cd5014d20a828ca25a54a381d452f0f8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="enroll-devices-by-using-a-device-enrollment-manager-account"></a>使用裝置註冊管理員帳戶註冊裝置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

組織可以搭配使用 Intune 與單一使用者帳戶來管理大量的行動裝置。 *裝置註冊管理員* (DEM) 帳戶是特殊的使用者帳戶，最多可以註冊 1,000 部裝置。 將現有的使用者加入 DEM 帳戶，能夠賦予他們特殊的 DEM 功能。 每個已註冊的裝置會使用單一授權。 建議您將透過此帳戶註冊的裝置做為共用裝置使用，而不是做為個人 ("BYOD") 裝置使用。  

使用者必須存在於 [Azure 入口網站](https://portal.azure.com)才能新增為裝置註冊管理員。 為了取得最佳安全性，DEM 使用者不應該同時為 Intune 管理員。

>[!NOTE]
>DEM 註冊方法不可與其他這些註冊方法一併使用︰[Apple Configurator 搭配設定助理](apple-configurator-setup-assistant-enroll-ios.md)、[Apple Configurator 搭配直接註冊](apple-configurator-direct-enroll-ios.md)、[Apple School Manager (ASM)](apple-school-manager-set-up-ios.md) 或[裝置註冊計劃 (DEP)](device-enrollment-program-enroll-ios.md)。

## <a name="example-of-a-device-enrollment-manager-scenario"></a>裝置註冊管理員案例範例

餐廳想要提供 50 部銷售點平板電腦給其服務生，和訂單監視器給廚房員工。 那些員工永遠不會需要存取公司資料或以使用者身分登入。 Intune 管理員會建立裝置註冊管理員帳戶，並將餐廳管理者新增至 DEM 帳戶。 管理者現在擁有 DEM 功能。 管理者現在可以使用 DEM 認證來註冊 50 部平板電腦裝置。

只有 [Azure 入口網站](https://portal.azure.com)中的使用者才能是裝置註冊管理員。 裝置註冊管理員使用者不能是 Intune 系統管理員。

DEM 使用者可以︰

-   在 Intune 中最多註冊 1000 部裝置
-   登入公司入口網站以取得公司應用程式
-   藉由將特定角色的應用程式部署到平板電腦來設定公司資料的存取權

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>以 DEM 帳戶註冊裝置的限制

使用裝置註冊管理員帳戶所註冊的裝置具有下列限制︰

  - 不具每位使用者的存取權。 因為裝置並未指派使用者，所以裝置沒有任何電子郵件或公司資料存取權。 但仍可使用 VPN 設定等來為裝置應用程式提供資料的存取權。
  - DEM 使用者無法使用公司入口網站在裝置本身取消註冊 DEM 註冊的裝置。 Intune 管理員可以取消註冊。
  - 只有本機裝置會出現在公司入口網站應用程式或網站中。
  - 使用者無法將 Apple「大量採購方案」(VPP) 應用程式與使用者授權搭配使用，因為進行應用程式管理需要個別使用者的 Apple ID。
  - (僅限 iOS) 如果您使用 DEM 註冊 iOS 裝置，就無法使用 Apple Configurator、Apple 裝置註冊計劃 (DEP) 或 Apple School Manager (ASM) 來註冊裝置。
  - (僅限 Android) 可以單一 DEM 帳戶註冊的 Android for Work 裝置有數量限制。 每個 DEM 帳戶最多可以註冊 10 部 Android 工作設定檔裝置。 這項限制不適用於舊版的 Android 註冊。
  - 裝置如果具有裝置授權，便可以安裝 VPP 應用程式。
  - 每部裝置都需要裝置授權。 深入了解[使用者和裝置授權](licenses-assign.md#how-user-and-device-licenses-affect-access-to-services)。


> [!NOTE]
> 您可以將公司應用程式部署到裝置註冊管理員管理的裝置。 請將公司入口網站應用程式以**必要安裝**部署到裝置註冊管理員的使用者帳戶。
> 為了改善效能，在 DEM 裝置上檢視公司入口網站應用程式只會顯示本機裝置。 只能從 Intune 管理主控台遠端管理其他 DEM 裝置。


## <a name="add-a-device-enrollment-manager"></a>新增裝置註冊管理員

1.  在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [裝置註冊管理員]。

2.  選取 [新增]。

3.  在 [新增使用者] 刀鋒視窗中，輸入 DEM 使用者的使用者主體名稱，然後選取 [新增]。 DEM 隨即會新增至 DEM 使用者清單。

## <a name="permissions-for-dem"></a>DEM 的權限

需要具備全域或 Intune 服務管理員 Azure AD 角色，才能在管理入口網站中執行與 DEM 註冊相關的工作。 儘管 RBAC 權限列於且適用於自訂使用者角色之下，但也需要有這些角色才能查看所有 DEM 使用者。 未指派全域管理員或 Intune 服務管理員角色，但具備裝置註冊管理員角色之讀取權限的使用者，只能看到他們所建立的 DEM 使用者。 支援這些功能的 RBAC 角色將會在未來宣布。

若未針對使用者指派全域管理員或 Intune 服務管理員角色，但他們具備已針對所指派之裝置註冊管理員角色啟用的讀取權限，則將只能看到他們所建立的 DEM 使用者。

## <a name="remove-a-device-enrollment-manager"></a>移除裝置註冊管理員

移除裝置註冊管理員並不會影響已註冊的裝置。 移除裝置註冊管理員時：

-   已註冊的裝置不會受到影響，仍可全面管理。
-   移除的裝置註冊管理員帳戶認證仍持續有效。
-   移除裝置註冊管理員依然無法抹除或淘汰裝置。
-   已移除的裝置註冊管理員可註冊的裝置數目，不得超過 Intune 管理員所設定的每位使用者限制。

**移除裝置註冊管理員**

1. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊]，然後選擇 [裝置註冊管理員]。
2. 在 [裝置註冊管理員] 刀鋒視窗上，依序選取 DEM 使用者和 [刪除]。

## <a name="view-the-properties-of-a-device-enrollment-manager"></a>檢視裝置註冊管理員的內容

1. 在 [Azure 入口網站](https://portal.azure.com)中，選擇 [裝置註冊]，然後選擇 [裝置註冊管理員]。
2. 在 [裝置註冊管理員] 刀鋒視窗上，於 DEM 使用者上按一下滑鼠右鍵，然後選取 [內容]。
