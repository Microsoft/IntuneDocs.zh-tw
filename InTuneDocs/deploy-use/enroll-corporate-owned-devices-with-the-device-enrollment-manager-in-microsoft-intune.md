---
title: "使用裝置註冊管理員進行註冊 | Microsoft Docs"
description: "裝置註冊管理員 (DEM) 帳戶可以透過單一使用者帳戶來管理大量共用且由公司所有的行動裝置。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/29/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: ea57a51f2855dea416ad4a76e657e1846ffe41f1
ms.lasthandoff: 04/24/2017


---


# <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune"></a>使用 Microsoft Intune 中的裝置註冊管理員註冊公司所擁有的裝置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

組織可以搭配使用 Intune 與單一使用者帳戶來管理大量的行動裝置。 *裝置註冊管理員* (DEM) 帳戶是特殊的使用者帳戶，最多可以註冊 1,000 部裝置。 將現有的使用者加入 DEM 帳戶，能夠賦予他們特殊的 DEM 功能。 每個已註冊的裝置會使用單一授權。 建議您將透過此帳戶註冊的裝置作為共用裝置使用 (即無使用者親和性)，而不是作為個人 ("BYOD") 裝置使用。  

使用者必須存在於 Azure 入口網站才能新增為裝置註冊管理員。 為了取得最佳安全性，DEM 使用者不應該同時為 Intune 管理員。

>[!NOTE]
>DEM 註冊方法不能與 [Apple Configurator 設定助理](ios-setup-assistant-enrollment-in-microsoft-intune.md)或[直接註冊](ios-direct-enrollment-in-microsoft-intune.md)，或是 [DEP 註冊方法](ios-device-enrollment-program-in-microsoft-intune.md)一起使用。

## <a name="example-of-a-device-enrollment-manager-scenario"></a>裝置註冊管理員案例範例

餐廳想要提供 50 部銷售點平板電腦給其服務生，和訂單監視器給廚房員工。 那些員工永遠不會需要存取公司資料或以使用者身分登入。 Intune 管理員會建立裝置註冊管理員帳戶，並將餐廳管理者新增至 DEM 帳戶，提供該管理者 DEM 功能。 管理者現在可以使用 DEM 認證來註冊 50 部平板電腦裝置。

只有 Intune 主控台中的使用者才能是裝置註冊管理員。 裝置註冊管理員使用者不能是 Intune 系統管理員。

DEM 使用者可以︰

-   在 Intune 中最多註冊 1000 部裝置
-   使用公司入口網站應用程式以取得公司應用程式
-   藉由將特定角色的應用程式部署到平板電腦來設定公司資料的存取權

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

1.  請確定您要新增至 DEM 帳戶的使用者已經存在。 如果需要新增使用者，請登入 [Office 365 入口網站](https://go.microsoft.com/fwlink/p/?LinkId=698854)，並遵循[個別或大量將使用者新增至 Office 365](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec) 中的步驟。

2.  使用您的系統管理員認證登入 [Microsoft Intune 管理主控台](https://manage.microsoft.com)。

3.  在瀏覽窗格中選擇 [系統管理]，並移至 [系統管理員管理]，然後選取 [裝置註冊管理員]。 [裝置註冊管理員] 頁面隨即開啟。

4.  選擇 [Add… (新增...)]。 [新增裝置註冊管理員]  對話方塊隨即開啟。

5.  輸入 Intune 帳戶的 [使用者識別碼]，然後選擇 [確定]。

    DEM 使用者現在可以在公司入口網站中，運用使用者用於 BYOD 案例中的同一程序來註冊行動裝置。 管理員使用者可以在最多 1000 部裝置上安裝公司入口網站應用程式，並使用其 DEM 認證註冊裝置。 如需每個平台的使用者註冊步驟，請參閱︰

  - [在 Intune 註冊 iOS 裝置](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-ios)
  - [在 Intune 註冊 macOS 裝置](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-macos)
  - [在 Intune 註冊 Android 裝置](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android)
  - [在 Intune 註冊 Windows 裝置](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows)

## <a name="delete-a-device-enrollment-manager-from-intune"></a>從 Intune 刪除裝置註冊管理員

1.  使用您的系統管理員認證登入 [Microsoft Intune 管理入口網站](https://manage.microsoft.com)。

2.  在瀏覽窗格中選擇 [系統管理]，並移至 [系統管理員管理]，然後選取 [裝置註冊管理員]。 [裝置註冊管理員] 頁面隨即開啟。

3.  選取想要刪除的裝置註冊管理員 [使用者]，然後選擇 [刪除]。 此使用者將不會從 Intune 中刪除，且此使用者所管理的裝置仍會在 Intune 中維持已註冊狀態。 刪除裝置註冊管理員可防止該使用者在 Intune 中註冊更多裝置。

4.  選擇 [是] 以確認您要刪除裝置註冊管理員。

刪除裝置註冊管理員對已註冊的裝置沒有影響。 刪除裝置註冊管理員之後：

-   已註冊的裝置不會受到影響。

-   仍可全面管理已註冊的裝置。

-   刪除的裝置註冊管理員帳戶認證仍能繼續用於登入公司入口網站來存取應用程式。

-   刪除的裝置註冊管理員帳戶認證仍然無法抹除或淘汰裝置。

-   刪除的裝置註冊管理員帳戶與已註冊裝置之間的關聯性仍然存在，但不能再註冊其他裝置。

