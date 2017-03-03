---
title: "註冊裝置 - 裝置註冊管理員 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版：使用裝置註冊管理員帳戶，於 Intune 中註冊裝置。 "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: 78eca605a277c1e0fc750900ece028d8f2c7c5b2
ms.lasthandoff: 02/15/2017

---

# <a name="enroll-devices-using-device-enrollment-manager"></a>使用裝置註冊管理員註冊裝置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

組織可以搭配使用 Intune 與單一使用者帳戶來管理大量的行動裝置。 *裝置註冊管理員* (DEM) 帳戶是特殊的使用者帳戶，最多可以註冊 1,000 部裝置。 將現有的使用者加入 DEM 帳戶，能夠賦予他們特殊的 DEM 功能。 每個已註冊的裝置會使用單一授權。 建議您將透過此帳戶註冊的裝置做為共用裝置使用，而不是做為個人 ("BYOD") 裝置使用。  

使用者必須存在於 Azure 入口網站才能新增為裝置註冊管理員。 為了取得最佳安全性，DEM 使用者不應該同時為 Intune 管理員。

>[!NOTE]
>DEM 註冊方法不可與其他這些註冊方法一併使用︰[Apple Configurator 設定助理](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)[Apple Configurator 直接註冊](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md)或[裝置註冊方案](enroll-ios-devices-using-device-enrollment-program.md)。 

## <a name="example-of-a-device-enrollment-manager-scenario"></a>裝置註冊管理員案例範例

餐廳想要提供 50 部銷售點平板電腦給其服務生，和訂單監視器給廚房員工。 那些員工永遠不會需要存取公司資料或以使用者身分登入。 Intune 管理員會建立裝置註冊管理員帳戶，並將餐廳管理者新增至 DEM 帳戶，提供該管理者 DEM 功能。 管理者現在可以使用 DEM 認證來註冊 50 部平板電腦裝置。

只有 Intune 主控台中的使用者才能是裝置註冊管理員。 裝置註冊管理員使用者不能是 Intune 系統管理員。

DEM 使用者可以︰

-   在 Intune 中最多註冊 1000 部裝置。
-   登入公司入口網站以取得公司應用程式。
-   藉由將特定角色的應用程式部署到平板電腦來設定公司資料的存取權。

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>以 DEM 帳戶註冊裝置的限制

使用裝置註冊管理員帳戶所註冊的裝置具有下列限制︰

  - 沒有特定的裝置「使用者」。 因此不會有電子郵件或公司資料的存取權。 不過，仍可使用 VPN 等為裝置應用程式提供資料的存取權。

  - 因為這些都是個別使用者案例，所以沒有條件式存取。

  - DEM 使用者無法使用公司入口網站在裝置本身取消註冊 DEM 註冊的裝置。 Intune 管理員有這項功能，但 DEM 使用者沒有。

  - 只有本機裝置會出現在公司入口網站應用程式或網站中。
 
  - 因為進行應用程式管理需要每位使用者的 Apple ID，因此使用者無法使用 Apple 大量採購計劃 (VPP) 應用程式。
 
  - (僅限 iOS) 如果使用 DEM 註冊 iOS 裝置，您就無法使用 Apple Configurator 或 Apple 裝置註冊方案 (DEP) 來註冊裝置。


> [!NOTE]
> 若要將公司應用程式部署到受裝置註冊管理員管理的裝置，請以 [必要安裝] 將公司入口網站應用程式部署到裝置註冊管理員的使用者帳戶。
> 為了改善效能，在 DEM 裝置上檢視公司入口網站應用程式只會顯示本機裝置。 只能從 Intune 管理主控台遠端管理其他 DEM 裝置。


## <a name="add-a-device-enrollment-manager"></a>新增裝置註冊管理員

1.  在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2.  在 Intune 刀鋒視窗上，選擇 [註冊裝置]，然後選擇 [裝置註冊管理員]。

3.  選取 [新增]。

4.  在 [新增使用者] 刀鋒視窗中，輸入 DEM 使用者的使用者主體名稱，然後選取 [新增]。 DEM 隨即會新增至 DEM 使用者清單。

## <a name="remove-a-device-enrollment-manager"></a>移除裝置註冊管理員

移除裝置註冊管理員並不會影響已註冊的裝置。 移除裝置註冊管理員時：

-   從 DEM 使用者清單中移除使用者，並不會影響已註冊的裝置，且可繼續完整管理已註冊的裝置。

-   移除的裝置註冊管理員帳戶認證仍持續有效。

-   移除裝置註冊管理員依然無法抹除或淘汰裝置。

-   除非達到 Intune 系統管理員所設定的每台裝置上限，否則移除的裝置註冊管理員無法註冊其他裝置。

**移除裝置註冊管理員**

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 Intune 刀鋒視窗上，選擇 [註冊裝置]，然後選擇 [裝置註冊管理員]。

3. 在 [裝置註冊管理員] 刀鋒視窗上，於 DEM 使用者上按一下滑鼠右鍵，然後選取 [移除]。

## <a name="view-the-properties-of-a-device-enrollment-manager"></a>檢視裝置註冊管理員的內容

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 Intune 刀鋒視窗上，選擇 [註冊裝置]，然後選擇 [裝置註冊管理員]。

3. 在 [裝置註冊管理員] 刀鋒視窗上，於 DEM 使用者上按一下滑鼠右鍵，然後選取 [內容]。

