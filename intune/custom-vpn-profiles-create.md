---
title: "如何使用 Microsoft Intune 建立自訂 VPN 設定檔"
titleSuffix: 
description: "在 Intune 中使用自訂設定來建立 VPN 設定檔。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ec9b959d086051985287a62f7d10fe8d4cbad7e9
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>如何在 Microsoft Intune 中建立自訂 VPN 設定檔

您可以使用 Intune 自訂設定原則來建立下列平台的 VPN 設定檔：

* Android 4 及更新版本
* 執行 Windows 8.1 和更新版本的已註冊裝置
* Windows Phone 8.1 和更新版本
* 執行 Windows 10 Desktop 的已註冊裝置 
* Windows 10 Mobile

標準 Intune VPN 原則沒有您想要使用的設定時，則此類型的原則十分有用。

## <a name="to-create-a-custom-configuration-policy"></a>建立自訂設定原則：

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [裝置設定]。
2. 在 [裝置設定] 窗格的 [管理] 區段下，選擇 [設定檔]。
5. 在 [設定檔] 窗格中，選擇 [建立設定檔]。
6. 在 [建立設定檔] 窗格中，輸入 VPN 設定檔的 [名稱] 和 [描述]。
7. 從 [平台] 下拉式清單中，選取要套用 VPN 設定的裝置平台。 您目前可以為自訂裝置設定選擇下列平台之一︰
    - **Android**
    - **Android for Work**
    - **iOS** (使用您從 Apple Configurator 匯出的檔案進行設定)。
    - **macOS** (使用您從 Apple Configurator 匯出的檔案進行設定)。
    - **Windows Phone 8.1**
    - **Windows 8.1 及更新版本**
    - **Windows 10 及更新版本**
6. 從 [設定檔] 類型下拉式清單中選擇 [自訂]。
7. 在 [Custom OMA-URI Settings] (自訂 OMA-URI 設定) 窗格中，為您要指定的每個 URI 設定選擇 [新增]，以提供所要求的資訊，然後選擇 [確定]。 範例如下：

   ![VPN 設定檔自訂設定對話方塊](./media/Intune_Add_VPN_URI.png)

4.  輸入所有必要的 URI 設定之後，請選擇 [確定]，然後在 [建立設定檔] 窗格中選擇 [建立]。

設定檔隨即建立，並出現在 [設定檔清單] 窗格上。
若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。




