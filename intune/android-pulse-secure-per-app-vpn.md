---
title: 自訂 Android 的個別應用程式 VPN 設定檔
titlesuffix: Microsoft Intune
description: 了解如何針對 Microsoft Intune 所管理的 Android 裝置建立個別應用程式 VPN 設定檔。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 75a4d6f91323992cf7aa2c8bae6db419b14d1942
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31831221"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>使用 Microsoft Intune 自訂設定檔來建立 Android 裝置的個別應用程式 VPN 設定檔

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

您可以為 Intune 所管理的 Android 5.0 及更新版本裝置建立個別應用程式 VPN 設定檔。 首先，建立使用 Pulse Secure 或 Citrix 連線類型的 VPN 設定檔。 接著，建立將 VPN 設定檔與特定應用程式建立關聯的自訂設定原則。

在您將原則指派給 Android 裝置或使用者群組之後，使用者應該啟動 Pulse Secure 或 Citrix VPN 用戶端。 接著，VPN 用戶端 就只會允許來自指定應用程式的流量使用開啟的 VPN 連線。

> [!NOTE]
>
> 此設定檔僅支援 Pulse Secure 和 Citrix 連線類型。


## <a name="step-1-create-a-vpn-profile"></a>步驟 1︰建立 VPN 設定檔


1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [裝置設定]。
2. 在 [裝置設定] 窗格的 [管理] 區段下，選擇 [設定檔]。
2. 在設定檔清單窗格中，選擇 [建立設定檔]。
3. 在 [建立設定檔] 窗格中，輸入 VPN 設定檔的 [名稱] 和 [描述]。
4. 從 [平台] 下拉式清單中選擇 [Android]。
5. 從 [設定檔類型] 下拉式清單中選擇 [VPN]。
3. 選擇 [設定]  >  [設定]，然後依照[如何設定 VPN 設定](vpn-settings-configure.md)及 [Android 裝置的 Intune VPN 設定](vpn-settings-android.md)中的設定來設定 VPN 設定檔。

請記下您在建立 VPN 設定檔時指定的 [連線名稱] 值。 下一個步驟將會需要這個名稱。 例如，**MyAppVpnProfile**。

## <a name="step-2-create-a-custom-configuration-policy"></a>步驟 2：建立自訂設定原則

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [裝置設定]。
2. 在 [裝置設定] 窗格的 [管理] 區段下，選擇 [設定檔]。
3. 在 [設定檔] 窗格中，按一下 [建立設定檔]。
4. 在 [建立設定檔] 窗格中，輸入自訂檔的 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中選擇 [Android]。
6. 從 [設定檔類型] 下拉式清單中選擇 [自訂]。
7. 選擇 [設定]  >  [設定]。
3. 在 [Custom OMA-URI Settings] (自訂 OMA-URI 設定) 窗格中，選擇 [新增]。
    - 輸入設定名稱。
    - 針對 [OMA-URI]，指定此字串：**./Vendor/MSFT/VPN/Profile/*Name*/PackageList**，其中 *Name* 是您在步驟 1 記下的 VPN 設定檔名稱。 在此範例中，此字串會是 **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**。
    - 針對 [資料類型]，請指定 [String]。
    - 針對 [值]，建立與設定檔建立關聯的套件清單 (以分號區隔)。 例如，如果您想要 Excel 和 Google Chrome 瀏覽器使用 VPN 連線，請輸入**com.microsoft.office.excel;com.android.chrome**。

![Android 個別應用程式 VPN 自訂原則範例](./media/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>將應用程式清單設定為封鎖清單或允許清單 (選用)
  使用 [BLACKLIST] 值，即可指定「不可」使用 VPN 連線的應用程式清單。 所有其他的應用程式都會透過 VPN 連線。
或者，您可以使用 [WHITELIST] 值以指定應用程式清單，這些應用程式「可以」使用 VPN 連線。 不在清單上的應用程式不會透過 VPN 連線。
  1.    在 [Custom OMA-URI Settings] (自訂 OMA-URI 設定) 窗格中，選擇 [新增]。
  2.    輸入設定名稱。
  3.    針對 [OMA-URI]，使用此字串：**./Vendor/MSFT/VPN/Profile/*Name*/Mode**，其中 *Name* 是您在步驟 1 記下的 VPN 設定檔名稱。 在這個範例中，字串會是 **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**。
  4.    針對 [資料類型]，請指定 [String]。
  5.    針對 [值]，請輸入 [BLACKLIST] 或 [WHITELIST]。



## <a name="step-3-assign-both-policies"></a>步驟 3︰指派這兩項原則

使用[如何指派裝置設定檔](device-profile-assign.md)中的指示，將兩個設定檔指派給必要的使用者或裝置。
