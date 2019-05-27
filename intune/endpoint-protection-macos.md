---
title: 在 Microsoft Intune 中於 macOS 上新增 Endpoint Protection - Azure | Microsoft Docs
description: 在 macOS 裝置上，使用閘道管理員來判斷可安裝應用程式的位置，包括 Mac App Store。 此外，也使用 Microsoft Intune 來啟用或設定防火牆以允許特定應用程式、封鎖特定應用程式、使用隱形模式，甚至是封鎖特定類型的連入連線。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e050d188d4508225ef384fbf557e7724efacab18
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047729"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Intune 中的 macOS Endpoint Protection 設定

本文將說明您可以為執行 macOS 的裝置設定的 Endpoint Protection 設定。 這些設定包括這些裝置上的閘道管理員和防火牆設定，而且您可以使用 Microsoft Intune 中的裝置設定檔來設定它們。

## <a name="gatekeeper"></a>閘道管理員

- **允許從這些位置下載的應用程式**：依據應用程式的下載位置來限制應用程式。 用意是要保護裝置免於惡意程式碼危害，而只允許來自您所信任來源的應用程式。 您的允許選項： 
  - **Mac App Store**
  - **Mac App Store 和已識別的開發人員**
  - **任何位置**

- **使用者可覆寫閘道管理員**：防止使用者覆寫閘道管理員設定，並防止使用者透過按住 Control 鍵再按一下來安裝應用程式。 啟用時，使用者可以按住 Control 鍵再按一下任何應用程式來安裝該應用程式。

## <a name="firewall"></a>防火牆

使用防火牆來控制個別應用程式 (而非個別連接埠) 的連線。 使用個別應用程式設定可讓您更容易獲得防火牆保護的好處。 這還有助於防止不想要的應用程式控制為合法應用程式開啟的網路連接埠。

- **使用防火牆來根據每個應用程式控制連線，以防止裝置存取未經授權的網路。**
  - **防火牆**：啟用防火牆以設定您環境中處理連入連線的方式。
  - **連入連線**：除了基本網際網路服務所需的連線 (例如 DHCP、Bonjour 及 IPSec) 之外，封鎖所有連入連線。 此功能也會封鎖所有共用服務，例如「檔案共用」和「螢幕共用」。 如果您目前使用共用服務，請將此設定保持為 [未設定]。

- **允許或封鎖特定應用程式的連入連線**
  - **允許的應用程式**：選取明確允許接收連入連線的應用程式。
  - **封鎖的應用程式**：選取應封鎖連入連線的應用程式。
  - **隱形模式**：若要防止電腦回應探查要求，請啟用隱形模式。 電腦會繼續回應已授權應用程式的連入要求。 ICMP (ping) 等未預期的要求都會予以忽略。
