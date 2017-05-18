---
title: "應用程式佈建設定檔 | Microsoft Docs"
description: "Intune 提供工具，讓您可主動將新的佈建設定檔原則部署至有應用程式即將到期的裝置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 86fbe736-7bdb-4f5e-ae21-13c91eb2462c
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: db76786da0428b0e064f2091089653244d90ee2a
ms.lasthandoff: 12/30/2016


---

# <a name="use-ios-mobile-provisioning-profile-policies-to-prevent-your-apps-from-expiring"></a>使用 iOS 行動佈建設定檔原則，以避免您的應用程式過期

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

部署至 iPhone 與 iPad 的 Apple iOS 企業營運應用程式，是使用包含的佈建設定檔與透過憑證簽署的程式碼所建置。 當該應用程式執行時，iOS 會確認該 iOS 應用程式的完整性，並強制執行由佈建設定檔定義的原則。 發生下列驗證︰

- **安裝檔案完整性** - iOS 會將應用程式詳細資料與企業簽署憑證的公開金鑰加以比較。 如果不同，應用程式內容可能已變更，且將不允許執行該應用程式。
- **功能強制** - iOS 嘗試從包含在應用程式安裝檔 (.ipa) 中的企業佈建設定檔 (而非個別開發人員佈建設定檔) 強制執行應用程式功能。


您用來簽署應用程式的企業簽署憑證通常會持續三年。 不過佈建設定檔將會在一年後到期。 當憑證仍然有效時，Intune 會提供工具，您可主動將新的佈建設定檔原則部署至有應用程式即將到期的裝置。
憑證過期後，您必須使用新的憑證再次簽署應用程式，並使用新憑證的金鑰內嵌新的佈建設定檔。



## <a name="how-to-find-out-when-a-line-of-business-app-will-expire"></a>如何找出企業營運應用程式的到期時間

1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [應用程式] > [應用程式]。
2. 在應用程式清單中，查看 [到期日] 欄，以查看應用程式的到期日。 您也可以將 [篩選] 下拉式清單設定為 [已過期/即將過期]，來僅查看您必須採取動作的應用程式。

## <a name="how-to-create-an-ios-mobile-provisioning-profile-policy"></a>如何建立 iOS 行動佈建設定檔原則


1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [原則] > [概觀] > [新增原則]。
2. 在 **[建立新的原則對話方塊]** 方塊中，選擇 **[iOS]**  >  **[行動佈建設定檔原則]**，然後選擇 **[建立原則]**。
3. 在 [一般] 頁面，設定以下的值：
    - [名稱] - 提供此行動佈建設定檔原則的名稱。
    - [描述] - 提供原則的描述 (選擇性)。
    - **[組態設定檔]** - 按一下 **[匯入]**，然後選擇您從 Apple 開發人員網站下載的 Apple 行動組態設定檔檔案 (副檔名為 **.mobileprovision**)。
4. 完成之後，請選擇 [儲存原則]。
5. 現在，將原則部署到所需的 iOS 裝置。 如需詳細資訊，請參閱[使用 Microsoft Intune 原則管理裝置上的設定與功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

