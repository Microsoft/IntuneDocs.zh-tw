---
title: Microsoft Intune 中的已知問題 - Azure | Microsoft Docs
description: 閱讀有關 Microsoft Intune 的已知問題。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 08/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 421eea460ee7c00b79a63a014291a8abb88ddaea
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347792"
---
# <a name="known-issues-in-microsoft-intune"></a>Microsoft Intune 的已知問題


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

您可以使用本文來了解 Microsoft Intune 中的任何已知問題。

若要回報此處未列的 Bug，可[提出支援要求](get-support.md)。

如果您想要要求在 Intune 中新增功能，請考慮在 [Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console)網站上提出報告。

## <a name="migration"></a>移轉

### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal"></a>匯出 Azure 傳統入口網站合規性政策，在 Intune Azure 入口網站中重新建立這些原則

將會取代在 Azure 傳統入口網站中建立的合規性政策。 您可檢閱及刪除任何現有的合規性政策，但無法加以更新。 若需要將任一合規性政策移轉至目前的 Intune Azure 入口網站，可以用逗號分隔的檔案 (.csv 檔案) 匯出政策。 然後，使用檔案中的詳細資料，在 Intune Azure 入口網站中，重新建立這些政策。

> [!IMPORTANT]
> Azure 傳統入口網站淘汰之後，您將無法再存取或檢視合規性政策。 因此，請務必在淘汰 Azure 傳統入口網站之前，先匯出您的政策，然後於 Azure 入口網站中重新建立它們。

### <a name="intune-legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Intune 舊版電腦用戶端功能只在 Silverlight 主控台提供

Azure 入口網站上的 Intune 提供了使用 Windows MDM 註冊管理 Windows 10 的能力。 如需詳細資訊，請參閱 [Azure 主控台上的 Intune 和電腦用戶端上的舊版 Intune](https://docs.microsoft.com/intune-classic/deploy-use/intune-on-azure)。

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>由 Intune 在移轉期間所建立的群組，可能會影響其他 Microsoft 產品的功能

當您從 Intune 移轉到 Azure 入口網站時，可能會看到名為 **All Users - b0b08746-4dbe-4a37-9adf-9e7652c0b421** 的新群組。 此群組包含 Azure Active Directory 中的所有使用者，而非只有 Intune 授權的使用者。 如果您預期有某些不屬於任何群組的現有或新使用者，此使用方式可能會對其他 Microsoft 產品造成問題。

### <a name="status-blades-for-migrated-policies-do-not-work"></a>用於移轉原則的「狀態」刀鋒視窗無法運作

您無法在 Azure 入口網站中，檢視從 Azure 傳統入口網站移轉之原則的狀態資訊。 但是，您可以在傳統入口網站中繼續檢視這些原則的報表。 若要檢視移轉之設定原則的狀態資訊，請在 Azure 入口網站中重新建立它們。

## <a name="apps"></a>應用程式


### <a name="multiple-app-install-prompts-for-certain-vpp-apps"></a>特定 VPP 應用程式的多個應用程式安裝提示
您可能會看到終端使用者裝置上已安裝之特定 VPP 應用程式的多個應用程式安裝提示。 如果您將已上傳至 Intune Azure 入口網站之 VPP 權杖的 [Automatic app updates] \(自動應用程式更新\) 選項設定為 [開啟]，就會發生此問題。    

若要解決此問題，您可以停用 VPP 權杖的 [Automatic app updates] \(自動應用程式更新\) 選項。 若要執行這項作業，請在 Azure 入口網站中，開啟 Microsoft Intune。 從 Intune 選取 [用戶端應用程式] >  [iOS VPP 權杖]。 接下來，選取已部署受影響應用程式的 VPP 權杖，然後選取 [編輯] > [Automatic app updates] \(自動應用程式更新\) > [關閉] > [儲存]。 或者，您可以停止將受影響的應用程式部署為 VPP 應用程式，這將會停止提示。    

這是目前版本中的已知問題。 我們將在未來推出修正程式來解決此問題。 實作修正程式之後，您的使用者就不會再看到多個應用程式安裝提示。

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>iOS 大量採購應用程式僅適用於預設的 Intune 租用戶語言
iOS 大量採購應用程式只能針對與您的 Intune 帳戶相同的國碼/地區碼顯示，並且予以指派。 Intune 只會同步其 iTunes 地區設定與 Intune 租用戶帳戶國碼/地區碼相同的應用程式。 例如，如果您購買僅於美國市集中提供的應用程式，但您的 Intune 帳戶是德文，Intune 就不會顯示該應用程式。

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>上傳多份相同的 iOS 大量採購方案
請勿針對相同的 VPP 權杖多次按一下 [上傳] 按鈕。 這會導致上傳重複的 VPP 權杖，並針對相同的 VPP 權杖多次進行應用程式同步處理。

### <a name="some-managed-browser-traffic-not-routed-through-azure-app-proxy----2463492---"></a>部分 Managed Browser 流量未透過 Azure 應用程式 Proxy 進行路由傳送 <!-- 2463492 -->
Managed Browser 和應用程式 Proxy 整合存在一個已知問題，即某些第三流量 (例如 javascript 或 AJAX 呼叫) 不會透過 Azure 應用程式 Proxy 進行路由傳送。 這是目前版本中的已知問題。  

<!-- ## Groups -->

## <a name="device-configuration"></a>裝置設定

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>您無法為某些裝置儲存「Windows 資訊保護」原則

對於沒有在 Intune 註冊的裝置，您只能在「Windows 資訊保護」原則設定的 [公司識別] 欄位中指定一個主要網域。
如果您新增了其他網域 (使用 [進階設定] > [網路周圍] > [新增受保護網域])，則將無法儲存原則。 您看到的錯誤訊息很快就會變得更為準確。

### <a name="cisco-anyconnect-and-cisco-legacy-anyconnect-vpn-client-support---ios"></a>Cisco AnyConnect 和 Cisco Legacy AnyConnect VPN 用戶端支援 - iOS

在 iOS 裝置上，網路存取控制 (NAC) 整合不適用於新的 Cisco AnyConnect 用戶端。 我們正與 Cisco 合作來提供 NAC 整合。

[在 Intune 中建立 VPN 設定檔](vpn-settings-ios.md)提供 Cisco AnyConnect 和 Cisco Legacy AnyConnect 用戶端更詳細的資訊。

### <a name="using-the-numeric-password-type-with-macos-sierra-devices"></a>搭配 macOS Sierra 裝置使用數值密碼類型

目前，如果您在 macOS Sierra 裝置的裝置限制設定檔中依序選取 [數值] > [必要的密碼類型]，它會強制為 [英數字元]。 如果您想要搭配這些裝置使用數值密碼，請不要設定這項設定。
未來的 macOS 版本可能會更正這個問題。

如需這些設定的詳細資訊，請參閱 [Microsoft Intune 中的 macOS 裝置限制設定](device-restrictions-macos.md)。

## <a name="compliance"></a>合規性

### <a name="compliance-policies-from-intune-do-not-show-up-in-new-console"></a>Intune 的合規性原則不會顯示於新的主控台中

您在傳統入口網站中所建立的合規性原則都會移轉，但並不會顯示於 Azure 入口網站中，因為 Azure 入口網站的設計改變了。 您在傳統 Intune 傳統入口網站所建立的合規性原則仍然會強制執行，但您必須在傳統入口網站中檢視及編輯這些原則。

除此之外，您在 Azure 入口網站中所建立的新合規性原則不會顯示於傳統入口網站中。

如需詳細資訊，請參閱[什麼是裝置合規性](device-compliance.md)。

<!-- ## Enrollment -->


## <a name="data-protection"></a>資料保護

### <a name="ios-app-protection-policies"></a>iOS 應用程式保護原則

您可以定義 [iOS 應用程式保護原則](app-protection-policy-settings-ios.md)，在透過行動應用程式管理 (MAM) 進行管理而不需要註冊的裝置上供使用者使用。 由於暫時性的錯誤，您只能為僅一個小數位數、而非多個小數位數的 iOS 版本定義這些原則。 可為 iOS 10.3 設定，不能為 iOS 10.3.1 的最低版本設定。 即將推出的 iOS SDK 更新會解決此問題。


## <a name="administration-and-accounts"></a>管理與帳戶

全域管理員 (也稱為租用戶管理員) 無須個別的 Intune 或 Enterprise Mobility Suite (EMS) 授權，也可以繼續執行日常的管理工作。 但是，若要使用服務，例如註冊自己的裝置、公司裝置或使用 Intune 公司入口網站，他們就需要有 Intune 或 EMS 授權。

<!-- ## Additional items -->
