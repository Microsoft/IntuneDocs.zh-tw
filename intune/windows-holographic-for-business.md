---
title: 使用 Microsoft Intune 來管理 Windows 全像攝影版裝置 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 時，您可以在執行 Windows Holographic for Business 的裝置上完成各種不同的工作，包括設定公司入口網站、建立合規性原則、自訂 OMA-URI 設定、部署應用程式、將裝置分類成群組、建立設定檔、限制裝置、啟用軟體更新、設定條款和條件、設定 VPN 和 Wi-Fi 設定，以及使用「Hello 企業版」。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 18f86580fc4c80fade7aeaa9678e9d8edac9a53e
ms.sourcegitcommit: b57be56524ddb5026fab94f7638dc516ed118325
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="customize-devices-running-windows-holographic-with-intune"></a>使用 Intune 來自訂執行 Windows 全像攝影版的裝置

Microsoft Intune 支援執行 Windows Holographic for Business 的裝置，例如 [Microsoft HoloLens](https://docs.microsoft.com/en-us/hololens/)。

若要使用 Microsoft Intune 來管理執行「Windows 全像攝影版」的裝置，您必須建立「版本升級」設定檔。 此升級設定檔會將裝置從「Windows 全像攝影版」升級至 Windows Holographic for Business。 至於 Microsoft HoloLens，您則可購買 Commercial Suite，以取得升級所需的授權。 如需詳細資訊，請參閱[將執行 Windows Holographic 的裝置升級到 Windows Holographic for Business](holographic-upgrade.md)。

若要協助管理和自訂執行 Windows Holographic for Business 的裝置，您可以使用本文中的工作。 例如，您可以管理軟體更新、設定 VPN 設定等。

## <a name="azure-active-directory"></a>Azure Active Directory

Azure Active Directory (AD) 是一項絕佳的資源，可協助您管理及控制執行 Windows Holographic for Business 的裝置。 使用 Intune 和 Azure AD 時，您可以： 

- **[設定已新增至 Azure Active Directory 的裝置](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-setup)**：您可以在 Azure Active Directory (AD) 中新增工作用的 Windows 10 裝置，包括執行 Windows Holographic for Business 的裝置。 這項功能可讓 Azure AD 控制裝置。 它可以協助確保使用者會透過符合安全性與合規性標準的裝置，來存取公司資源。

  [Azure AD 的裝置管理簡介](https://docs.microsoft.com/azure/active-directory/device-management-introduction)提供更多詳細資料。

- **[Windows 裝置的大量註冊](windows-bulk-enroll.md)**：身為系統管理員，您可以將大量的新 Windows 裝置加入 Azure Active Directory (AD) 和 Intune。 這項功能稱為大量註冊，其會使用佈建套件來執行作業。 這些套件會將執行 Windows Holographic for Business 的裝置加入您的 Azure AD 租用戶，並在 Intune 中註冊。

## <a name="company-portal"></a>公司入口網站
**[設定公司入口網站應用程式](company-portal-app.md)**

Intune 包括公司入口網站，使用者會在此網站存取公司資料、註冊裝置、安裝應用程式、連絡您的 IT 部門等。 您可以針對執行 Windows Holographic for Business 的裝置自訂公司入口網站應用程式。

## <a name="compliance-policy"></a>相容性原則
**[建立裝置合規性原則](compliance-policy-create-windows.md)**

合規性原則係指裝置必須符合才能符合規範的規則和設定。 您可以使用這些原則搭配條件式存取，讓不符合規範的裝置無法存取公司資源。 在 Intune 中，您可以建立合規性原則來允許或封鎖執行 Windows Holographic for Business 之裝置的存取權。 例如，您可以建立要求啟用 Bitlocker 的原則。

另請參閱**[開始使用合規性原則](device-compliance-get-started.md)**。

## <a name="deploy-and-manage-apps"></a>部署和管理 App
**[將應用程式新增至 Intune](apps-add.md)**

使用 Intune 時，您可以將應用程式新增至執行 Windows Holographic for Business 的裝置。 有許多方式可以部署應用程式，包括：

- [新增 Microsoft Store 應用程式](store-apps-windows.md)
- [新增您建立的應用程式](lob-apps-windows.md)
- [將應用程式指派給群組](apps-deploy.md)

Microsoft Intune 可以將通用 Windows 應用程式部署到執行 Windows Holographic for Business 的 Microsoft HoloLens 裝置。 您可以在 Intune Azure 入口網站直接上傳應用程式，或從 Microsoft Store for Business 部署它們。 如需相關領域的詳細資訊，請參閱下列各節：
- 若要使用 Intune Azure 入口網站來部署企業營運應用程式 (LOB) 應用程式，請參閱[如何將 Windows 企業營運應用程式新增至 Microsoft Intune](lob-apps-windows.md)。
- 若要使用 Microsoft Store for Business 來部署應用程式，請參閱[利用 Microsoft Intune 來管理您從 Microsoft Store for Business 購買的應用程式](windows-store-for-business.md)。 
- 若要了解如何使用 Microsoft Intune 來管理應用程式，請參閱[什麼是利用 Microsoft Intune 管理應用程式](app-management.md)。
- 若要深入了解開發 Microsoft HoloLens 的應用程式，請參閱 [Microsoft HoloLens 的混合現實應用程式](https://www.microsoft.com/hololens/apps)。 

> [!NOTE]
> 執行 Windows 10 Holographic for Business 1607 的 HoloLens 裝置不支援 Microsoft Store for Business 線上授權的應用程式。 若要進一步了解，請參閱[將應用程式安裝到 HoloLens 上](https://docs.microsoft.com/en-us/hololens/hololens-install-apps)。

## <a name="device-actions"></a>裝置動作
Intune 具有一些內建動作，可讓 IT 系統管理員執行不同的工作，不論是在本機裝置上進行，或在 Azure 入口網站中使用 Intune 遠端進行均可。 使用者也可以從 Intune 公司入口網站，對使用 Intune 註冊的個人擁有裝置發出遠端命令。

下列動作適用於執行 Windows Holographic for Business 的裝置： 

- **[原廠重設](devices-wipe.md#factory-reset)**：**原廠重設**動作會從 Intune 移除裝置，並將裝置還原為出廠預設值。 您可以在提供裝置給新的使用者之前或裝置遺失或遭竊時，使用此動作。

- **[移除公司資料](devices-wipe.md#remove-company-data)**：**移除公司資料**動作會從 Intune 移除裝置，並移除受控的應用程式資料、設定及 Intune 指派的電子郵件設定檔。 使用者的個人資料仍會保留在裝置上。

- **[同步處理裝置以取得最新的原則和動作](device-sync.md)**：**同步**動作會強制裝置立即使用 Intune 簽入。 當裝置簽入時，會立即接收所有擱置動作或已指派的原則。 這項功能可協助您驗證已指派的原則並對其進行疑難排解，而不用等到下次排程的簽入才進行。

**[什麼是 Microsoft Intune 裝置管理？](device-management.md)** 是一篇很好的資源，可讓您了解如何使用 Azure 入口網站管理裝置。 

## <a name="device-categories-and-groups"></a>裝置類別和群組
**[將裝置分類成群組](device-group-mapping.md)**

使用 Intune 時，您可以建立裝置類別，以根據您建立的類別 (例如「銷售」、「會計」、「人力資源」等) 自動將裝置新增至群組。 用意是讓您可以更輕鬆地管理執行 Windows Holographic for Business 的裝置。

## <a name="device-configuration-profiles"></a>裝置組態設定檔 
**[開始使用組態設定檔](device-profiles.md)和[建立您自己的設定檔](device-profile-create.md)**

Intune 包含您可以在組織內不同裝置上啟用或停用的設定及功能。 可使用設定檔來管理這些設定和功能。 例如，您可以建立在執行 Windows Holographic for Business 的裝置上啟用 Cortana 或使用 Windows Defender Smart Screen 的設定檔。

在您的設定檔中，您可以使用 OMA-URI 來自訂一些設定、建立裝置限制，以及設定虛擬私人網路 (VPN) 和 Wi-Fi。

#### <a name="custom-device-settingscustom-settings-windows-holographicmd"></a>[自訂裝置設定](custom-settings-windows-holographic.md)

若要設定 OMA-URI (開放行動通訊聯盟統一資源識別項) 設定，您可以在 Intune 中建立自訂設定檔。 請使用 OMA-URI 設定來控制您 Windows Holographic for Business 裝置上的各種不同功能，例如啟用 VPN 或檢查 Microsoft Update 上是否有更新。

#### <a name="device-restrictionsdevice-restrictions-windows-holographicmd"></a>[裝置限制](device-restrictions-windows-holographic.md)

裝置限制可讓您控制裝置上的各種不同設定和功能，包括要求密碼、從 [Microsoft Store](https://www.microsoft.com/store/apps/windows?icid=CNavAppsWindowsApps) 安裝應用程式、啟用藍芽等。 這些限制會建立在 Intune 設定檔中。 您可以將此設定檔套用至多個執行 Windows Holographic for Business 的裝置。

#### <a name="configure-vpnvpn-settings-configuremd"></a>[設定 VPN](vpn-settings-configure.md)

虛擬私人網路 (VPN) 為您的使用者提供安全的公司網路遠端存取。 在 Intune 中，您可以建立 VPN 設定檔來包含執行 Windows Holographic for Business 之裝置的特定設定。 例如，您可以建立 VPN 設定檔，讓所有 Windows Holographic for Business 裝置都能使用 Citrix VPN 作為連線類型。

#### <a name="configure-wi-fiwi-fi-settings-configuremd"></a>[設定 Wi-Fi](wi-fi-settings-configure.md)

您也可以在 Intune 中建立 Wi-Fi 設定檔，以將無線網路設定指派給 Windows Holographic for Business 裝置。 當您指派 Wi-Fi 設定檔時，使用者無須進行任何網路設定，即可取得公司網路存取權。 例如，您可以建立 Windows Holographic for Business 裝置專用的 Wi-Fi 網路。

## <a name="software-updates"></a>軟體更新
**[管理軟體更新](windows-update-for-business-configure.md)**

Intune 包含一項適用於 Windows 10 裝置的功能，稱為更新通道。 這些更新通道包含一組決定了更新安裝方式的設定。 例如，您可以建立一個維護期間來安裝更新，或選擇在安裝更新後重新啟動。 您可以將更新通道套用至多個執行 Windows Holographic for Business 的裝置。

## <a name="terms-and-conditions"></a>條款及條件
**[設定公司的使用者存取條款及條件](terms-and-conditions-create.md)**

您可以要求使用者必須先接受公司的條款及條件，才能註冊裝置及存取公司應用程式 (包括電子郵件)。 在 Intune 中，您可以定義如何在公司入口網站中顯示條款及條件，也可以將這些條款及條件指派給執行 Windows Holographic for Business 的裝置。

## <a name="windows-hello-for-business"></a>Windows Hello 企業版
**[使用 Windows Hello 企業版](windows-hello.md)**

「Hello 企業版」是一種替代的登入方法，可使用 Azure Active Directory 帳戶來取代密碼、智慧卡或虛擬智慧卡。 使用「Hello 企業版」時，您的 Windows Holographic for Business 裝置可以使用 PIN (由您設定長度下限) 來登入。
