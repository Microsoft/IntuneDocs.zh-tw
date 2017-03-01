---
title: "Microsoft Intune 中的裝置設定檔是什麼？"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解 Intune 裝置設定檔，以及這些設定檔如何協助管理及保護您公司裝置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: eb48265e4655117976c9847b1f5bee712f0c2e3c
ms.lasthandoff: 02/18/2017


---

# <a name="what-are-microsoft-intune-device-profiles"></a>什麼是 Microsoft Intune 裝置設定檔？

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

使用 Microsoft Intune 的**設定裝置**工作負載可以管理您管理之所有裝置的設定及功能。 您大部分會使用此工作負載來建立裝置設定檔，讓您管理和控制所管理裝置上的各種不同功能。

當您開啟此工作負載時，會顯示下列選項︰

- **概觀** - 此頁面提供狀態及報表，可協助您監視您指派給使用者及裝置的裝置設定。
- **管理設定檔** - 您可以在此區段中建立裝置組態設定檔。 您可以在下方找到您能建立之所有設定檔類型的清單。
- **設定憑證授權單位** - 此工作流程會逐步引導您執行設定憑證所需的步驟。 若要使用 Intune 的憑證設定檔，必須執行此動作。

## <a name="getting-started"></a>開始使用

建立裝置設定檔的工作流程與所有設定檔的建立工作流程類似。 如需如何建立設定檔的資訊，請參閱[如何建立 Microsoft Intune 的裝置組態設定檔](/intune-azure/configure-devices/how-to-create-device-profiles)。 另外也請閱讀建立每種設定檔類型設定的特有資訊。

您可以管理您裝置上的下列功能︰

## <a name="device-restrictions"></a>裝置限制
裝置限制可讓您控制各種類別中，您所管理的各種設定及功能，包括安全性、瀏覽器、硬體及資料共用設定。 例如，您可以建立裝置限制設定檔，禁止 iOS 裝置的使用者存取裝置相機 。
如需詳細資訊，請參閱[如何設定裝置限制設定](how-to-configure-device-restrictions.md) 支援︰Android、iOS、macOS、Windows 10 及 Windows 10 Team。

## <a name="email"></a>電子郵件
電子郵件設定檔可讓您建立、部署及監視您管理之裝置上的 Exchange ActiveSync 電子郵件設定。 藉由部署這些設定，您可以確保一致性、減少支援來電，以及讓使用者無須任何設定，就能從其個人裝置存取公司的電子郵件。
如需詳細資訊，請參閱[如何設定電子郵件設定](how-to-configure-email-settings.md) 支援︰支援︰Android、iOS、Windows Phone 8.1 及 Windows 10。

## <a name="wi-fi"></a>Wi-Fi
使用 Wi-Fi 設定檔將無線網路設定部署給組織中的使用者與裝置。 若您部署 Wi-Fi 設定檔，您的使用者不需要自行設定即可存取您公司的 Wi-Fi。
如需詳細資訊，請參閱[如何設定 Wi-Fi 設定](how-to-configure-wi-fi-settings.md) 支援︰ Android、iOS、macOS 及 Windows 8.1 (僅限匯入)。

## <a name="vpn"></a>VPN
虛擬私人網路 (VPN) 為您的使用者提供安全的公司網路遠端存取。 裝置使用 VPN 連線設定檔來啟動與 VPN 伺服器的連線。 使用 VPN 設定檔將 VPN 設定部署給組織中的使用者及裝置，讓他們可以輕鬆安全地連線到網路。
如需詳細資訊，請參閱[如何設定 VPN 設定](how-to-configure-vpn-settings.md)。
支援︰Android、iOS、macOS、Windows Phone 8.1、Windows 8.1 及 Windows 10。

## <a name="certificates"></a>憑證
此設定檔類型可讓您設定信任的憑證、SCEP 憑證及 PKCS 憑證指派給裝置，以及用於驗證 Wi-Fi、VPN 及電子郵件設定檔。
如需詳細資訊，請參閱[如何設定憑證](how-to-configure-certificates.md) 支援︰Android、iOS、Windows Phone 8.1、Windows 8.1 及 Windows 10。

## <a name="edition-upgrade"></a>版本升級
此設定檔類型可讓您自動將執行某些特定版本 Windows 10 的裝置升級為更新版本。如需詳細資訊，請參閱[如何設定 Windows 10 版本升級](how-to-configure-windows-10-edition-upgrade.md) 支援︰僅限 Windows 10。

## <a name="windows-information-protection"></a>Windows 資訊保護
Windows 資訊保護可協助防範資料流失，但不會干擾員工的操作。 它也能協助保護企業應用程式與資料，防止企業擁有的裝置和員工帶到公司的個人裝置意外外洩資料，而且不需要對您的環境或其他應用程式進行任何變更。
如需詳細資訊，請參閱[如何設定 Windows 資訊保護](how-to-configure-windows-information-protection.md) 支援︰僅限 Windows 10。

## <a name="custom"></a>自訂
自訂設定可讓您指派不屬於 Intune 內建設定的裝置設定。 例如在 Android 裝置上，您可以指定 OMA-URI 值來設定裝置。 對於 iOS 裝置，您可以匯入您在 Apple Configurator 中建立的設定檔。
如需詳細資訊，請參閱[如何設定自訂設定](how-to-configure-custom-settings.md) 支援︰ Android、iOS、macOS 及 Windows 8.1。

