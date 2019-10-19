---
title: 在 Microsoft Intune 中設定 macOS 裝置的 VPN 設定 - Azure | Microsoft Docs
description: 新增或建立虛擬私人網路（VPN）設定檔，包括連線詳細資料、分割通道、具有識別碼、索引鍵和值組的自訂 VPN 設定、具有設定腳本的 proxy 設定、IP 或 FQDN 位址，以及中的 TCP 埠在執行 macOS 的裝置上 Microsoft Intune。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 044b35b34a9a5b01537e82dcfddca74a284ebdcc
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72491003"
---
# <a name="add-vpn-settings-on-macos-devices-in-microsoft-intune"></a>在 Microsoft Intune 中設定 macOS 裝置上的 VPN 設定

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文說明可用於設定執行 macOS 之裝置上 VPN 連線的 Intune 設定。

下列清單中的值並非全部都能設定，須取決於您選擇的設定。

## <a name="before-you-begin"></a>開始之前

[建立裝置組態設定檔](vpn-settings-configure.md)。

> [!NOTE]
> 這些設定適用于所有的註冊類型。 如需註冊類型的詳細資訊，請參閱[macOS 註冊](../enrollment/macos-enroll.md)。

## <a name="base-vpn-settings"></a>基本 VPN 設定

**連線名稱**：輸入此連線的名稱。 終端使用者瀏覽其裝置的可用 VPN 連線清單時，使用者會看到此名稱。
- **IP 位址或 FQDN**：提供裝置所連線之 VPN 伺服器的 IP 位址或完整網域名稱。 範例：**192.168.1.1**、**vpn.contoso.com**。
- **驗證方法**從下列方式中選擇裝置向 VPN 伺服器進行驗證的方式︰
  - **憑證**：從 [驗證憑證]  下選擇先前建立用於驗證連線的 SCEP 或 PKCS 憑證設定檔。 如需憑證設定檔的詳細資訊，請參閱[如何設定憑證](../protect/certificates-configure.md)。
  - **使用者名稱和密碼**：使用者必須提供使用者名稱和密碼才能登入 VPN 伺服器。
- **連線類型**：從下列廠商清單中選取 VPN 連線類型︰
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **自訂 VPN**
- **分割通道**：[啟用]  或 [停用]  此選項可讓裝置依據流量決定所要使用的連線。 例如，旅館中的使用者使用 VPN 連線存取工作檔案，但使用旅館的標準網路進行一般的網頁瀏覽。

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](../apps/apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>自訂 VPN 設定

若選取 [自訂 VPN]  ，請進一步設定如下：

- **Vpn 識別碼**：輸入您所使用之 vpn 應用程式的識別碼。 此識別碼是由您的 VPN 提供者所提供。
- **輸入自訂 VPN 屬性的機碼值組**：新增或匯入 [機碼]  和 [值]  來自訂您的 VPN 連線。 這些值通常由 VPN 提供者提供。

## <a name="proxy-settings"></a>Proxy 設定

- **自動設定指令碼**：使用檔案設定 Proxy 伺服器。 輸入包含設定檔的 [Proxy 伺服器 URL]  。 例如，輸入 `http://proxy.contoso.com`。
- **位址**：輸入 Proxy 伺服器位址 (例如 IP 位址)。
- **連接埠號碼**：輸入與 Proxy 伺服器相關聯的連接埠號碼。

## <a name="next-steps"></a>後續步驟

設定檔已建立，但還不會執行任何動作。 接下來，[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

在[android](vpn-settings-android.md)、 [android Enterprise](vpn-settings-android-enterprise.md)、 [iOS](vpn-settings-ios.md)和[Windows 10](vpn-settings-windows-10.md)裝置上設定 VPN 設定。
