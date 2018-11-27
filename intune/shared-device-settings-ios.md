---
title: 適用於 iOS 的 Microsoft Intune 共用裝置組態設定
titlesuffix: ''
description: 了解您可以用來在 iOS 裝置鎖定畫面上顯示資訊的 Microsoft Intune 設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 638b4b3ebc83917faae0d34ec407b8ad47b4a4fb
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183378"
---
# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>在 iOS 裝置鎖定畫面上顯示訊息的共用裝置組態設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文將說明可以用來在 iOS 裝置鎖定畫面上顯示資訊的 Microsoft Intune 設定。

共用裝置組態設定可讓您指定登入視窗與鎖定畫面上所顯示的選擇性文字。 例如，您可以輸入「若遺失，請送回」訊息和「資產標籤資訊」。 

>[!IMPORTANT]
> 執行 iOS 9.3 和更新版本的受監督裝置支援這項功能。

## <a name="create-shared-device-settings"></a>建立共用的裝置設定

1. 從 [Azure 入口網站中的 Intune](https://portal.azure.com)，巡覽至 [[裝置設定] 區域中的 [裝置功能]](device-features-configure.md)。 
1. 在 [裝置功能] 窗格中，選擇 [Shared Device Configuration (supervised only)] (共用裝置設定 (僅限受監督))。
2. 在 [Shared Device Configuration (supervised only)] (共用裝置設定 (僅限受監督)) 窗格中，設定下列設定：
    - **資產標籤資訊**：輸入裝置資產標籤的相關資訊。 例如：「由 Contoso 公司所擁有」。您輸入的資訊會套用至您指派此設定檔的所有裝置上。
    - **鎖定畫面註腳** - 如果裝置遺失或遭竊，輸入可能有助於取回裝置的備註。 例如：「如果拾獲，請撥打 (號碼)」。
3. 完成之後，選擇 [確定] 直到您返回 [建立設定檔] 窗格，然後選擇 [建立]。 


## <a name="next-steps"></a>接下來的步驟

您現在可以將裝置設定檔指派給您選擇的群組。 如需詳細資料，請參閱[如何指派裝置設定檔](device-profile-assign.md)。
