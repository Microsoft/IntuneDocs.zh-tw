---
title: 自訂 Android 的個別應用程式 VPN 設定檔
titleSuffix: Microsoft Intune
description: 了解如何針對 Microsoft Intune 所管理的 Android 裝置建立個別應用程式 VPN 設定檔。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3683d2aeada791c6ec827e915e02365a336e6045
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059666"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>使用 Microsoft Intune 自訂設定檔來建立 Android 裝置的個別應用程式 VPN 設定檔

[!INCLUDE[azure_portal](../includes/azure_portal.md)]

您可以為 Intune 所管理的 Android 5.0 及更新版本裝置建立個別應用程式 VPN 設定檔。 首先，建立使用 Pulse Secure 或 Citrix 連線類型的 VPN 設定檔。 接著，建立將 VPN 設定檔與特定應用程式建立關聯的自訂設定原則。

在您將原則指派給 Android 裝置或使用者群組之後，使用者應該啟動 Pulse Secure 或 Citrix VPN 用戶端。 接著，VPN 用戶端 就只會允許來自指定應用程式的流量使用開啟的 VPN 連線。

> [!NOTE]
>
> 此設定檔僅支援 Pulse Secure 和 Citrix 連線類型。

## <a name="step-1-create-a-vpn-profile"></a>步驟 1：建立 VPN 設定檔

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
3. 輸入下列內容：

    - **名稱**：為設定檔輸入描述性名稱。 命名您的設定檔，以方便之後能輕鬆識別。 例如，良好設定檔名稱為**適用於整家公司的 Android 各個應用程式 VPN 設定檔**。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取 [Android]  。
    - **設定檔類型**：選取 [VPN]  。

4. 選擇 [設定]   >  [設定]  ，然後依照[如何設定 VPN 設定](vpn-settings-configure.md)及 [Android 裝置的 Intune VPN 設定](vpn-settings-android.md)中的設定來設定 VPN 設定檔。

請記下您在建立 VPN 設定檔時指定的 [連線名稱]  值。 下一個步驟將會需要這個名稱。 例如，**MyAppVpnProfile**。

## <a name="step-2-create-a-custom-configuration-policy"></a>步驟 2：建立自訂設定原則

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
3. 輸入下列內容：

    - **名稱**：為自訂設定檔輸入描述性名稱。 命名您的設定檔，以方便之後能輕鬆識別。 例如，良好設定檔名稱為**適用於整家公司的自訂 OMA-URI Android VPN 設定檔**。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取 [Android]  。
    - **設定檔類型**：選取 [自訂]  。

4. 選擇 [設定]   >  [設定]  。
5. 在 [Custom OMA-URI Settings] (自訂 OMA-URI 設定)  窗格中，選擇 [新增]  。
    - **名稱**：輸入設定的名稱。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **OMA-URI**：輸入 `./Vendor/MSFT/VPN/Profile/*Name*/PackageList`，其中 *Name* 是您在步驟 1 記下的連線名稱。 在此範例中，字串是 `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList`。
    - **資料類型**：輸入**字串**。
    - **值**：輸入要與設定檔建立關聯的套件清單 (以分號區隔)。 例如，如果想要 Excel 和 Google Chrome 瀏覽器使用 VPN 連線，請輸入 `com.microsoft.office.excel;com.android.chrome`。

![Android 個別應用程式 VPN 自訂原則範例](./media/android-pulse-secure-per-app-vpn/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>將應用程式清單設定為封鎖清單或允許清單 (選用)

使用 **BLACKLIST** 值，即可輸入「不可」  使用 VPN 連線的應用程式清單。 所有其他的應用程式都會透過 VPN 連線。 或者，您可以使用 **WHITELIST** 值以指定應用程式清單，這些應用程式「可以」  使用 VPN 連線。 不在清單上的應用程式不會透過 VPN 連線。

1. 在 [Custom OMA-URI Settings] (自訂 OMA-URI 設定)  窗格中，選擇 [新增]  。
2. 輸入設定名稱。
3. 在 [OMA-URI]  中，輸入 `./Vendor/MSFT/VPN/Profile/*Name*/Mode`，其中 *Name* 是您在步驟 1 記下的 VPN 設定檔名稱。 在我們的範例中，字串是 `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode`。
4. 在 [資料類型]  中，輸入**字串**。
5. 在 [值]  中，輸入 **BLACKLIST** 或 **WHITELIST**。

## <a name="step-3-assign-both-policies"></a>步驟 3：指派這兩項原則

[指派這兩個裝置設定檔](device-profile-assign.md)給所需的使用者或裝置。
