---
title: "適用於 iOS 裝置的 Intune AirPlay 設定"
titlesuffix: Azure portal
description: "了解如何使用 Intune，以協助將 iOS 裝置自動連線到相容 AirPlay 的裝置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 03ecd2de215ff5b825dc8240d0b4f1bb77891d46
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2017
---
# <a name="intune-airplay-settings-for-ios-devices"></a>適用於 iOS 裝置的 Intune AirPlay 設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用這些設定來協助將您管理的 iOS 裝置連線到網路中相容 AirPlay 的裝置 (例如 Apple TV)。
有了這項功能，您可以：

- **設定裝置和密碼清單** - 讓使用者自動連線至範圍內的 AirPlay 裝置。 使用 AirPlay 裝置的名稱與密碼佈建它們，讓它們在連線時不需要再提供名稱與密碼。
- **設定允許的目的地**：設定 AirPlay 裝置的清單 (依據裝置識別碼)。 使用者只能看到和連線到您列出的裝置 (僅限受監督的裝置)。

## <a name="get-started"></a>開始使用

1. 在 [裝置功能] 刀鋒視窗上選擇 [AirPlay]。
2. 在 [AirPlay] 刀鋒視窗上，選擇下列一或兩個動作：

## <a name="configure-a-device-and-password-list"></a>設定裝置和密碼清單

1. 在 [密碼] 刀鋒視窗上，輸入 AirPlay 裝置的 [裝置名稱] 和 [密碼]，例如 **Contoso Apple TV**。
2. 輸入裝置詳細資料之後，按一下 [新增]。 裝置會顯示在 [裝置名稱] 清單中。
3. 繼續新增裝置。 完成之後，請選擇 [確定]。


## <a name="configure-allowed-destinations"></a>設定允許的目的地

1. 在 [允許的目的地 (僅限受監督)] 刀鋒視窗上，輸入 AirPlay 裝置的 [裝置識別碼]，例如 52:46:CD:51:83:4C。
2. 輸入裝置識別碼之後，按一下 [新增]。 識別碼會顯示在 [裝置識別碼] 清單中。
3. 繼續新增裝置。 完成之後，請選擇 [確定]。

您也可以從逗號分隔值 (csv) 檔案匯入裝置和密碼，以及允許的目的地。


## <a name="next-steps"></a>後續步驟

您現在可以將裝置設定檔指派給您選擇的群組。 如需詳細資料，請參閱[如何指派裝置設定檔](device-profile-assign.md)。

