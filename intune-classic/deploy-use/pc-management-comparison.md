---
title: "比較 Windows 電腦管理選項"
description: "使用 Apple 裝置註冊方案 (DEP) 或 Apple Configurator 來註冊公司擁有的 iOS 裝置"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8f6de91724db10ef64e2c1fd6eee6101c6eac79a
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2018
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>比較作為電腦或行動裝置來管理 Windows 電腦

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

組織可以使用 Microsoft Intune 來管理 Windows 電腦，其方式包括使用行動裝置管理 (MDM) 作為行動裝置來管理，或使用 Intune 軟體用戶端作為電腦來管理。  Microsoft 建議客戶如有可能盡量使用 MDM 管理解決方案。 但是，為了協助您深入了解這些選項之間的差異，下圖對這兩個管理選項進行了比較。

|**功能 / 案例** |**將 Windows 作為電腦**<br>Intune 軟體用戶端 | **將 Windows 作為行動裝置**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**作業系統** |Windows 10、Windows 8+、Windows 7、Windows Vista | Windows 10+ |
|**Intune 入口網站支援** |[Silverlight 主控台](https://manage.microsoft.com)|[Azure 入口網站](https://portal.azure.com) |
|**條件式存取**|無法使用|可用 <br>[什麼是條件式存取？](https://docs.microsoft.com/intune-azure/conditional-access/what-is-conditional-access)|
|**大量註冊**|無法使用|可用 <br>[Windows 裝置的大量註冊](https://docs.microsoft.com/intune-azure/enroll-devices/bulk-enroll-windows)|
|**裝置設定檔**|無法使用|可用 <br>[什麼是 Microsoft Intune 裝置設定檔？](https://docs.microsoft.com/intune-azure/configure-devices/what-are-device-profiles)|
|**無代理程式註冊**|無法使用 |可用<br>[註冊 Windows 裝置](https://docs.microsoft.com/intune-azure/enroll-devices/enroll-windows-devices)|
|**軟體更新管理**| Windows Updates 和 Microsoft 應用程式更新<br>[使用軟體更新讓 Windows 電腦維持最新狀態](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)|Windows 10 和 Microsoft 應用程式更新的商務用 Microsoft 市集<br> [設定商務用 Windows Update 的設定](https://docs.microsoft.com/intune-azure/configure-devices/how-to-configure-windows-update-for-business) |
|**軟體授權管理**|可用 <br>[管理 Windows 電腦軟體的授權合約](https://docs.microsoft.com/intune/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)|商務用 Microsoft 市集 (僅限 .appx 應用程式)<br>[管理您從商務用 Microsoft 網上商店購買的應用程式](https://docs.microsoft.com/intune-azure/manage-apps/wsfb-apps)|
|**清查**|可用 <br>[檢視 Windows 電腦的硬體和軟體清查](https://docs.microsoft.com/intune/deploy-use/view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune)|可用 <br>[如何監視應用程式資訊](https://docs.microsoft.com/intune/apps-monitor)<br>[什麼是裝置管理](https://docs.microsoft.com/intune/device-management)|
|**Windows 防火牆原則**|可用 <br>[使用 Windows 防火牆原則協助保護 Windows 電腦](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune) |無法使用|
|**反惡意程式碼防護**|Endpoint Protection<br>[使用 Endpoint Protection 協助保護 Windows 電腦](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)|Windows Defender<br>[Windows Defender 設定](https://docs.microsoft.com/intune-azure/configure-devices/custom-for-windows-10#windows-defender-settings)|
|**遠端協助** |TeamViewer<br>[對 Windows 電腦要求及提供遠端協助](https://docs.microsoft.com/intune/deploy-use/request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune)|無法使用 |
|**應用程式部署** | 不適用於商務用 Microsoft 市集、<br>僅限 .exe、.appx 和多檔案 .msi<br>[為執行 Intune 軟體用戶端的 Windows 電腦新增應用程式](https://docs.microsoft.com/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)|適用於 Microsoft 市集應用程式及企業營運應用程式<br>[如何新增 Windows 市集應用程式](https://docs.microsoft.com/intune/store-apps-windows)<br>[如何新增 Windows 企業營運 (LOB) 應用程式](https://docs.microsoft.com/intune/lob-apps-windows)|
|**應用程式保護**|無法使用|可用 <br>[什麼是應用程式保護原則？](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-protection-policy)|
|**健康情況證明**|無法使用|可用|


### <a name="advantages-of-mdm-windows-pc-management"></a>MDM Windows 電腦管理的優點
使用最新行動裝置管理的 Windows 電腦管理具有下列優點：
- **延展性** - MDM 管理可隨著 Intune 雲端管理而延展。 Intune 軟體用戶端的上限為 7000 部電腦。
- **簡化** - 使用作業系統隨附的最新管理功能，而無需依賴於下載的軟體用戶端
- **一致性** - 您的 Windows 電腦可以像組織中的其他所有行動裝置一樣管理
<!-- - **Cloud optimization** - -->
