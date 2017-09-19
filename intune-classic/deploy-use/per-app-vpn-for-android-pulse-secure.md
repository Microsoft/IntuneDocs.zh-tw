---
title: "Android 使用 Pulse Secure 的個別應用程式 VPN"
description: "您可以為 Intune 所管理的 Android 裝置建立個別應用程式 VPN 設定檔。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5dd8b1318acc035ed3fee410eea7ac5d08065844
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2017
---
# <a name="use-a-custom-policy-to-create-a-per-app-vpn-profile-for-android-devices"></a>使用自訂原則來建立 Android 裝置的個別應用程式 VPN 設定檔

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

您可以為 Intune 所管理的 Android 5.0 及更新版本裝置建立個別應用程式 VPN 設定檔。 首先，建立使用 Pulse Secure 或 Citrix 連線類型的 VPN 設定檔。 接著，建立將 VPN 設定檔與特定應用程式建立關聯的自訂設定原則。 

在您將原則部署至 Android 裝置或使用者群組後，使用者應啟動 Pulse Secure 或 Citrix VPN。 連線接著只允許來自指定應用程式的流量使用開放的 VPN 連線。

> [!NOTE]
>
> 此設定檔僅支援 Pulse Secure 和 Citrix 連線類型。


### <a name="step-1-create-a-vpn-profile"></a>步驟 1︰建立 VPN 設定檔

1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [原則] > [新增原則]。
2. 展開 [Android]，然後選擇 [VPN 設定檔 (Android 4 及更新版本)])，以選取新原則的範本。
3. 在範本中，針對 [連線類型]，選擇 [Pulse Secure] 或 [Citrix]。
4. 完成並儲存 VPN 設定檔。 如需 VPN 設定檔的詳細資訊，請參閱 [VPN 連線](../deploy-use/vpn-connections-in-microsoft-intune.md)。

> [!NOTE]
>
> 請記下您在建立 VPN 設定檔時指定的 [VPN 連線名稱 (顯示給使用者):] 值。 下一步中將需要此值。 例如，**MyAppVpnProfile**。

### <a name="step-2-create-a-custom-configuration-policy"></a>步驟 2：建立自訂設定原則

   1. 在 Intune 管理主控台中，請選擇 [原則] > [新增原則][Android] > [Android] > [自訂設定] > [建立原則]。
   2. 輸入原則的名稱。
   3. 在 [OMA-URI 設定] 下，選擇 [新增]。
   4. 輸入設定名稱。
   5. 針對 [資料類型]，請指定 [String]。
   6. 針對 [OMA-URI]，指定此字串：**./Vendor/MSFT/VPN/Profile/*Name*/PackageList**，其中 *Name* 是您在步驟 1 記下的 VPN 設定檔名稱。 在這個範例中，字串會是 **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**。
   7.   針對 [值]，建立與設定檔建立關聯的套件清單 (以分號區隔)。 例如，如果您想要 Excel 和 Google Chrome 瀏覽器使用 VPN 連線，請輸入**com.microsoft.office.excel;com.android.chrome**。

![Android 個別應用程式 VPN 自訂原則範例](./media/android_per_app_vpn_oma_uri.png)

#### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>將應用程式清單設定為封鎖清單或允許清單 (選用)
  使用 [BLACKLIST] 值，即可指定「不可」使用 VPN 連線的應用程式清單。 所有其他應用程式都會透過 VPN 進行連線。
或者，您可以使用 [WHITELIST] 值以指定應用程式清單，這些應用程式「可以」使用 VPN 連線。 不在清單上的應用程式不會透過 VPN 連線。
  1.    在 [OMA-URI] 設定下，選擇 [新增]。
  2.    輸入設定名稱。
  3.    針對 [資料類型]，請指定 [String]。
  4.    針對 [OMA-URI]，使用此字串：**./Vendor/MSFT/VPN/Profile/*Name*/Mode**，其中 *Name* 是您在步驟 1 記下的 VPN 設定檔名稱。 在這個範例中，字串會是 **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**。
  5.    針對 [值]，請輸入 [BLACKLIST] 或 [WHITELIST]。



### <a name="step-3-deploy-both-policies"></a>步驟 3︰兩個原則都部署

您必須將*兩個*原則部署至*相同的* Intune 群組。

1.  在 [原則] 工作區中，選取您要部署的原則，然後選擇 [管理部署]。
2.  在 [管理部署]  對話方塊中：
    -   **若要部署原則**，請選取您要部署原則的一或多個群組，然後選擇 [新增] > [確定]。
    -   **若要關閉對話方塊而不部署原則**，請選擇 [取消]。

在 [原則]  工作區的 [概觀]  頁面上，狀態摘要和警示可識別需要注意的原則問題。 狀態摘要還會顯示在 [儀表板] 工作區中。
