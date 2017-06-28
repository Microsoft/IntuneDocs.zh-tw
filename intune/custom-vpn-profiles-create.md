---
title: "如何使用 Microsoft Intune 建立自訂 VPN 設定檔"
titleSuffix: Intune on Azure
description: "在 Intune 中使用自訂組態來建立 VPN 設定檔。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 11da0d31a9a00364a6105006c3e75b6bb6f2cb77
ms.contentlocale: zh-tw
ms.lasthandoff: 06/08/2017


---

# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>如何在 Microsoft Intune 中建立自訂 VPN 設定檔

## <a name="create-a-custom-configuration"></a>建立自訂組態
您可以使用 Intune 自訂設定原則來建立下列各項的 VPN 設定檔：

* 執行 Android 4 和更新版本的裝置
* 執行 Windows 8.1 和更新版本的已註冊裝置
* 執行 Windows Phone 8.1 和更新版本的裝置
* 執行 Windows 10 Desktop 的已註冊裝置 
* 執行 Windows 10 行動裝置版的裝置

標準 Intune VPN 原則未包含您想要使用的設定時，這類型的原則十分有用。

## <a name="to-create-a-custom-configuration-policy"></a>建立自訂設定原則：

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置設定]。
4. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
5. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
6. 在 [建立設定檔] 刀鋒視窗中，為 VPN 設定檔輸入 [名稱] 及 [描述]。
7. 從 [平台] 下拉式清單中，選取要套用 VPN 設定的裝置平台。 您目前可以為自訂裝置設定選擇下列平台之一︰
    - **Android**
    - **iOS** (使用您從 Apple Configurator 匯出的檔案進行設定)。
    - **macOS** (使用您從 Apple Configurator 匯出的檔案進行設定)。
    - **Windows Phone 8.1**
    - **Windows 10 及更新版本**
6. 從 [設定檔] 類型下拉式清單中選擇 [自訂]。
7. 在 [自訂 OMA URI 設定] 刀鋒視窗中，為您要指定的每個 URI 設定選擇 [新增]，以提供所要求的資訊，然後選擇 [確定]。 範例如下：

   ![VPN 設定檔自訂組態對話方塊](./media/Intune_Add_VPN_URI.png)

4.  輸入所有必要的 URI 設定之後，請選擇 [確定]，然後在 [建立設定檔] 刀鋒視窗中選擇 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。
若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。





