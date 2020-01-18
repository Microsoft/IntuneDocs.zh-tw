---
title: 開發中 - Microsoft Intune
titleSuffix: ''
description: 正在開發的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/07/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 01ea2f75d166e5cc6aef4b890dba5722a74c1f61
ms.sourcegitcommit: 8f56220e7cafc5bc43135940575a9acb5afde730
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827814"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>Microsoft Intune 正在開發的項目 - 2020 年 1 月

為了協助您整備及規劃，此頁面會列出正在開發，但尚未發行的 Intune UI 更新及功能。 除了此頁面上的資訊： 

- 若我們預期您將需要在變更前先行採取動作，我們會在 Office 訊息中心發佈輔助性貼文。
- 當功能進入生產環境時，不論是預覽或正式推出，功能描述都會從這個頁面移至[新](whats-new.md)功能。
- 此頁面和[新增功能](whats-new.md)頁面會定期更新。 請回來查看其他更新。
- 請參閱 [Microsoft 365 藍圖](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)以取得策略性交付與時間表。

> [!NOTE]
> 此頁面會反映我們在未來版本中目前對 Intune 功能的期望。 日期和個別功能可能會變更。 此頁面不會描述開發中的所有功能。

**RSS 摘要**：將下列 URL 複製並貼上至您的摘要讀取器中，以了解此頁面何時更新：`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>應用程式管理

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>在 Windows 上顯示公司入口網站應用程式的通知<!-- 1808082  -->
我們會更新 Windows 裝置上的公司入口網站應用程式，以向使用者顯示快顯通知，即使應用程式關閉也是一樣。 只有在安裝狀態為 [已完成] 或 [失敗] 時，更新才會顯示可用應用程式的通知。 公司入口網站應用程式不會顯示必要應用程式的通知。 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>顯示公司入口網站應用程式的安裝狀態訊息<!-- 2514416  -->
公司入口網站應用程式會向終端使用者顯示額外的應用程式安裝狀態訊息。 下列條件將適用于新的 Win32 相依性功能：
- 應用程式無法啟動。 不符合系統管理員所定義的相依性。

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276-idready---"></a>在 iOS 裝置上將 web 剪輯的目標重定為 Microsoft Edge<!-- 5455276 idready -->
在 iOS 裝置上作為固定 web 應用程式的 web 剪輯必須更新。 如果需要在受保護的瀏覽器中開啟，新部署的 web 剪輯會在 Microsoft Edge 中開啟，而不是 Intune Managed Browser。 您必須重新置放既有的 web 剪輯，以確保它們在 Microsoft Edge 中開啟，而不是 Managed Browser。 

### <a name="user-experience-change-when-adding-apps-to-intune---4705829-idready---"></a>將應用程式新增至 Intune 時的使用者體驗變更<!-- 4705829 idready -->
透過 Intune 新增應用程式時，您會看到新的使用者體驗。 此體驗會提供您先前使用的相同設定和詳細資料，但新的體驗會遵循類似 wizard 的程式，再將應用程式新增至 Intune。 此新體驗也會在新增應用程式之前提供審查頁面。 從 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，選取 [應用程式]   > [所有應用程式]   > [新增]  。 如需詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](~/apps/apps-add.md)。

#### <a name="require-win32-apps-to-restart----3136567--"></a>需要 Win32 應用程式重新開機 <!-- 3136567-->
您可以要求 Win32 應用程式必須在成功安裝後重新開機。 此外，您也可以選擇必須重新開機之前的時間量（寬限期）。

<!-- ***********************************************-->
## <a name="device-configuration"></a>裝置設定

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>將自動 proxy 設定新增至 Android Enterprise 工作設定檔的 Wi-fi 設定檔<!-- 4490822 idready -->
在 Android Enterprise 工作設定檔裝置上，您可以建立 Wi-fi 設定檔。 當您選擇 Wi-fi 企業類型時，您也可以輸入在 Wi-fi 網路上使用的可延伸驗證通訊協定（EAP）類型。

在未來的更新中，當您選擇企業類型時，您將能夠輸入自動 proxy 設定，包括 proxy 伺服器 URL，例如 `proxy.contoso.com`。

若要查看您可以設定的目前 Wi-fi 設定，請前往 Microsoft Intune 中的 [為[執行 Android 企業和 android kiosk 的裝置新增 wi-fi 設定](../configuration/wi-fi-settings-android-enterprise.md)]。

適用於：
- Android Enterprise 工作設定檔

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>適用于 macOS 裝置的有線網路裝置設定設定檔<!-- 3508686  -->
將會提供新的 macOS 裝置設定設定檔 **，以設定**有線網路（**裝置**設定 > **配置**檔 >  > 為平臺 >**有線網路** **設定設定檔**類型）。 使用此功能來建立 802.1 x 設定檔以管理有線網路，並將這些有線網路部署至您的 macOS 裝置。

適用於：
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>具有 IKEv2 VPN 連線的 VPN 設定檔可以搭配 iOS 裝置使用 always on <!-- 1947932 idready -->
在 iOS 裝置上，您可以建立使用 IKEv2 連線的 VPN 設定檔（**裝置**設定 > **配置**檔 > **建立**設定檔 > **iOS/iPadOS**用於平臺 > **VPN**以進行配置檔案類型）。 在未來的更新中，您可以使用 IKEv2 設定「永遠開啟」。 當設定時，IKEv2 VPN 設定檔會自動連線，並保持連接（或快速重新連接） VPN。 即使在網路之間移動或重新開機裝置，它仍會保持連線。

在 iOS 上，always on VPN 僅限於 IKEv2 設定檔。

若要查看您目前可以設定的 IKEv2 設定，請前往[在 Microsoft Intune 中於 iOS 裝置上新增 VPN 設定](../configuration/vpn-settings-ios.md#ikev2-settings)。

適用於：
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>改善在 iOS 和 macOS 裝置上建立設定設定檔時的使用者介面體驗<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
當您建立 iOS 或 macOS 裝置的設定檔時，將會更新 [端點管理] 系統管理中心的體驗。 這項變更會影響下列裝置設定設定檔（**裝置** ** > 設定設定檔 > ** **建立**適用于平臺的設定檔 > **iOS**或**macOS** ）：

- Custom： iOS、macOS
- 裝置功能： iOS、macOS
- 裝置限制：iOS、macOS
- 端點保護：macOS
- 延伸模組： macOS
- 喜好設定檔案： macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>改善在 Android Enterprise 裝置上建立 OEMConfig 設定設定檔時的使用者介面體驗<!-- 5568645 idready  -->
當您建立或編輯 Android 企業裝置的 OEMConfig 設定檔時，會更新端點管理系統管理中心的體驗。 更新的體驗將會提供您一眼就設定的設定摘要。 此變更會影響 OEMConfig 裝置設定設定檔  （裝置 ** > 設定設定檔，**  > 為配置檔案類型**建立配置**檔 > **Android Enterprise**的平臺 > **OEMConfig** 。

本功能適用於：
- Android 企業 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>裝置註冊

### <a name="block-android-enrollments-by-device-manufacturer--5197392-idready--"></a>封鎖裝置製造商的 Android 註冊<!--5197392 idready-->
您將能夠根據裝置的製造商來封鎖裝置的註冊。 這適用于 Android 裝置系統管理員和 Android Enterprise 工作設定檔裝置。 若要查看註冊限制，請移至[Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)> **裝置** > **註冊限制**。



<!-- ***********************************************-->
## <a name="device-management"></a>裝置管理


### <a name="new-information-in-device-details---4471759-5604099----"></a>裝置詳細資料中的新資訊<!-- 4471759 5604099  -->
下列資訊會新增至裝置的 **[總覽**] 頁面：
- 記憶體容量（裝置上的實體記憶體數量）
- 儲存體容量（裝置上的實體儲存體數量） 
- CPU 處理器類型和速度
- RAM 和處理器資料

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>角色型存取控制

### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-idready--"></a>新的 Intune 內建角色端點安全性管理員<!--4253397 idready-->
將會提供新的 Intune 內建角色：「端點安全性管理員」。 這個新角色可讓系統管理員完整存取 Intune 中的端點管理員節點，以及僅供存取其他區域。 角色是 Azure AD 的「安全性系統管理員」角色的擴充。 如果您目前只有全域管理員做為角色，則不需要進行任何變更。 如果您使用角色，而您想要端點安全性管理員所提供的資料細微性，請在可用時指派該角色。 如需內建角色的詳細資訊，請參閱[角色型存取控制](role-based-access-control.md)。

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Intune 角色使用者介面變更即將推出<!--5801612 idready-->
[Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)系統管理中心的使用者介面 > **租使用者管理** > **角色**將會變更為更方便使用且直覺化的設計。 這種體驗會提供您現在所使用的相同設定和詳細資料，但新的體驗會採用類似 wizard 的進程。


<!-- ***********************************************-->
## <a name="security"></a>安全性

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Android COBO 裝置上的衍生認證支援<!--4839592-->
您將能夠在 Android Enterprise 完全受控裝置上使用衍生的認證。 將包含支援來抓取 Entrust Datacard、調解和 DISA Purebred 的衍生認證。 您將能夠使用衍生的認證來進行應用程式驗證、Wi-fi、VPN 或 S/MIME 簽署及/或使用支援的應用程式加密。 

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。


