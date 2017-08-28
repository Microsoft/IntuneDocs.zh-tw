---
title: "Azure 上 Microsoft Intune 的已知問題"
titleSuffix: Intune on Azure
description: "閱讀 Intune 的相關已知問題"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5a9b7f69cded9258efb6c8a897e0c026f3228a6b
ms.sourcegitcommit: c248b5a15894f0ade23bad4644c3b7035a9fcce8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2017
---
# <a name="known-issues-in-microsoft-intune"></a>Microsoft Intune 的已知問題


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


您可以使用本主題了解 Microsoft Intune 的任何已知問題。

若要回報此處未列的 Bug，可[提出支援要求](get-support.md)。

若要要求在 Intune 中新增功能，請考慮前往我們的 [Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console) 網站填寫報告。

## <a name="migration"></a>移轉

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>由 Intune 在移轉期間所建立的群組，可能會影響其他 Microsoft 產品的功能

當您從傳統 Intune 移轉到 Azure 入口網站時，您可能會看到名為 **All Users - b0b08746-4dbe-4a37-9adf-9e7652c0b421** 的新群組。 此群組包含 Azure Active Directory 中的所有使用者，而非只有 Intune 授權的使用者。 如果您預期有某些不屬於任何群組的現有或新使用者，此使用方式可能會對其他 Microsoft 產品造成問題。

### <a name="secondary-migration-required-for-select-capabilities"></a>需進行次要移轉以選取功能

必須先移轉 2017 年 1 月之前建立的 Intune 帳戶，才能在 Azure 入口網站中使用下列功能：

- 公司裝置註冊設定檔
- Apple 裝置註冊方案
- 依 iOS 序號預先宣告公司裝置
- 裝置註冊管理員帳戶
- Apple 大量採購方案

因為無法從傳統 Intune (Silverlight) 主控台和 Azure 入口網站管理這些功能，所以移轉會：
- 在傳統主控台中停用它們
- 在 Azure 入口網站中啟用它們  

在 2017 年 9 月 11 之後，會將這些功能的移轉合併至「主要移轉至 Azure」。 如果您的帳戶已經移轉成使用 Azure 入口網站，則此次要移轉會在 2017 年 9 月 11 日與 22 日之間發生。 而開始移轉您的帳戶之後，將會在同一天完成。 移轉最多可能需要 6 個小時，而且是從在 Intune 傳統主控台中停用這些功能開始算起。

如果您現在於 Azure 入口網站中管理這些 Intune 功能，請注意以下幾點：

#### <a name="removes-default-corporate-device-enrollment-profiles-in-apple-dep"></a>移除 Apple DEP 中的預設公司裝置註冊設定檔
Azure 入口網站不支援 Apple 裝置註冊計劃 (DEP) 裝置的「預設」公司裝置註冊設定檔。 傳統 Intune (Silverlight) 主控台中提供此功能，但已停止提供，以避免不慎指派這類設定檔。 在 Azure 入口網站中進行 DEP 序號同步處理時，不會指派任何公司裝置註冊設定檔。 使用裝置之前，必須先指派註冊設定檔。

#### <a name="apple-dep-token-restored-with-migration"></a>移轉時還原的 Apple DEP 權杖

如果您刪除傳統 Intune (Silverlight) 入口網站中的 Apple 裝置註冊計畫權杖，且未將新的權杖上傳至 Azure 入口網站，則會在您移轉時於 Azure 入口網站中還原原始權杖。 若要移除這個權杖並避免 DEP 註冊，請刪除 Azure 入口網站中的權杖。

### <a name="status-blades-for-migrated-policies-do-not-work"></a>用於移轉原則的「狀態」刀鋒視窗無法運作

您無法在 Azure 入口網站中，檢視從傳統入口網站移轉之原則的狀態資訊。 但是，您可以在傳統入口網站中繼續檢視這些原則的報表。 若要檢視移轉之設定原則的狀態資訊，請在 Azure 入口網站中重新建立它們。

## <a name="apps"></a>應用程式

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>iOS 大量採購應用程式僅適用於預設的 Intune 租用戶語言
iOS 大量採購應用程式只能針對與您的 Intune 帳戶相同的國碼/地區碼顯示，並且予以指派。 Intune 只會同步處理其 iTunes 地區設定與 Intune 租用戶帳戶國碼/地區碼相同的應用程式。 例如，如果您購買僅於美國市集中提供的應用程式，但您的 Intune 帳戶是德文，則 Intune 不會顯示該應用程式。

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>上傳多份相同的 iOS 大量採購方案
請勿針對相同的 VPP 權杖多次按一下 [上傳] 按鈕。 這會導致上傳重複的 VPP 權杖，並針對相同的 VPP 權杖多次進行應用程式同步處理。

<!-- ## Groups -->

## <a name="device-configuration"></a>裝置設定

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>您無法為某些裝置儲存「Windows 資訊保護」原則

對於沒有在 Intune 註冊的裝置，您只能在「Windows 資訊保護」原則設定的 [公司識別] 欄位中指定一個主要網域。
如果您新增了其他網域 (使用 [進階設定] > [網路周圍] > [新增受保護網域])，則將無法儲存原則。 您看到的錯誤訊息很快就會變得更為準確。

### <a name="cisco-anyconnect-vpn-client-support"></a>Cisco AnyConnect VPN 用戶端支援

Cisco AnyConnect VPN 用戶端的最新版本 (4.0.07072) 目前無法與 Intune 相容。
未來的 Intune 更新將會包含與這個 VPN 用戶端版本的相容性。 在此之前，建議您不要更新 Cisco AnyConnect VPN 用戶端，並繼續使用現有的版本。

### <a name="using-the-numeric-password-type-with-macos-sierra-devices"></a>搭配 macOS Sierra 裝置使用數值密碼類型

目前，如果您在 macOS Sierra 裝置的裝置限制設定檔中依序選取 [數值] > [必要的密碼類型]，它會強制為 [英數字元]。 如果您想要搭配這些裝置使用數值密碼，請不要設定這項設定。
未來的 macOS 版本可能會更正這個問題。

如需這些設定的詳細資訊，請參閱 [Microsoft Intune 中的 macOS 裝置限制設定](device-restrictions-macos.md)。

## <a name="compliance"></a>合規性

### <a name="compliance-policies-from-intune-do-not-show-up-in-new-console"></a>Intune 的合規性原則不會顯示於新的主控台中

您在傳統入口網站中所建立的合規性原則都會移轉，但並不會顯示於 Azure 入口網站中，因為 Azure 入口網站的設計改變了。 您在傳統 Intune 入口網站中所建立的合規性原則仍然會強制執行，但您必須在傳統 Intune 入口網站中檢視及編輯它們。
除此之外，您在 Azure 入口網站中所建立的新合規性原則不會顯示於傳統 Intune 入口網站中。

如需詳細資訊，請參閱[什麼是裝置合規性](device-compliance.md)。

<!-- ## Enrollment -->


## <a name="data-protection"></a>資料保護

### <a name="ios-app-protection-policies"></a>iOS 應用程式保護原則

您可以定義 [iOS 應用程式保護原則](app-protection-policy-settings-ios.md)，在透過行動應用程式管理 (MAM) 進行管理而不需要註冊的裝置上供使用者使用。 由於暫時性的錯誤，您只能為僅一個小數位數、而非多個小數位數的 iOS 版本定義這些原則。 可為 iOS 10.3 設定，不能為 iOS 10.3.1 的最低版本設定。 即將推出的 iOS SDK 更新會解決此問題。


## <a name="administration-and-accounts"></a>管理與帳戶

全域管理員 (也稱為租用戶管理員) 無須個別的 Intune 或 Enterprise Mobility Suite (EMS) 授權，也可以繼續執行日常的管理工作。 但是，若要使用服務，例如註冊自己的裝置、公司裝置或使用 Intune 公司入口網站，他們就需要有 Intune 或 EMS 授權。

<!-- ## Additional items -->
