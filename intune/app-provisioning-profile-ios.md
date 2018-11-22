---
title: Microsoft Intune 中的 iOS 應用程式佈建設定檔
titlesuffix: ''
description: Intune 提供您一些工具，可讓您主動將新的佈建設定檔指派給具有即將到期應用程式的裝置。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6668848bcb381299417ca7a641e267c41f9a1e79
ms.sourcegitcommit: 6ff5df63a2fff291d7ac5fed9c51417fe808650d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52167383"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>使用 iOS 應用程式佈建設定檔以避免應用程式過期

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>簡介

指派至 iPhone 與 iPad 的 Apple iOS 企業營運應用程式，是使用包含的佈建設定檔與透過憑證簽署的程式碼所建置。 當該應用程式執行時，iOS 會確認該 iOS 應用程式的完整性，並強制執行由佈建設定檔定義的原則。 發生下列驗證︰

- **安裝檔案完整性** - iOS 會將應用程式詳細資料與企業簽署憑證的公開金鑰加以比較。 如果不同，應用程式內容可能已變更，且不允許執行該應用程式。
- **功能強制** - iOS 嘗試從包含在應用程式安裝檔 (.ipa) 中的企業佈建設定檔 (而非個別開發人員佈建設定檔) 強制執行應用程式功能。


您用來簽署應用程式的企業簽署憑證通常會持續三年。 不過佈建設定檔將會在一年後到期。 當憑證仍然有效時，Intune 會提供工具，您可主動將新的佈建設定檔指派至有應用程式即將到期的裝置。
憑證過期後，您必須使用新的憑證再次簽署應用程式，並使用新憑證的金鑰內嵌新的佈建設定檔。

身為系統管理員，您可以包含及排除安全性群組以指派 iOS 應用程式佈建設定。 例如，您可以將 iOS 應用程式佈建設定指派給「所有使用者」，但排除執行群組。

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>如何建立 iOS 行動應用程式佈建設定檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格上，選擇 [用戶端應用程式]。
1.  在 [用戶端應用程式] 工作負載中，選擇 [管理] > [iOS 應用程式佈建設定檔]。
2.  在設定檔清單窗格中，選擇 [建立設定檔]。
3. 在 [建立設定檔] 窗格中，設定下列值︰
    - **名稱** - 提供此行動佈建設定檔的名稱。
    - [描述] - 提供原則的描述 (選擇性)。
    - **上傳設定檔** - 選擇 [匯入]，然後選擇您從 Apple 開發人員網站下載的 Apple 行動組態設定檔檔案 (副檔名為 `.mobileprovision`)。
4. 完成之後，請選擇 [建立]。

## <a name="next-steps"></a>後續步驟

將設定檔指派給所需的 iOS 裝置。 如需詳細資訊，請使用[如何指派裝置設定檔](device-profile-assign.md)中的步驟。
