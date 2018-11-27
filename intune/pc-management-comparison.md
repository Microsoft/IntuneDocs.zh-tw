---
title: 比較 Windows 電腦管理選項
titlesuffix: Microsoft Intune
description: 使用 Apple 裝置註冊計劃 (DEP) 或 Apple Configurator 來註冊公司擁有的 iOS 裝置。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.openlocfilehash: a5c06844c253951dfe7d5998aa4e275a6281067f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184636"
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>比較作為電腦或行動裝置來管理 Windows 電腦

[!INCLUDE [classic-portal](includes/classic-portal.md)]

組織可以使用 Microsoft Intune 來管理 Windows 電腦，其方式包括使用行動裝置管理 (MDM) 作為行動裝置來管理，或使用 Intune 軟體用戶端作為電腦來管理。  Microsoft 建議客戶如有可能盡量使用 MDM 管理解決方案。 但是，為了協助您深入了解這些選項之間的差異，下圖對這兩個管理選項進行了比較。

|**功能 / 案例** |**將 Windows 作為電腦**<br>Intune 軟體用戶端 | **將 Windows 作為行動裝置**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**作業系統** |Windows 10、Windows 8+、Windows 7、Windows Vista | Windows 10+ |
|**Intune 入口網站支援** |[Silverlight 主控台](https://manage.microsoft.com)|[Azure 入口網站](https://portal.azure.com) |
|**條件式存取**|無法使用|可用 <br>[什麼是條件式存取？](conditional-access.md)|
|**大量註冊**|無法使用|可用 <br>[Windows 裝置的大量註冊](windows-bulk-enroll.md)|
|**裝置設定檔**|無法使用|可用 <br>[什麼是 Microsoft Intune 裝置設定檔？](device-profiles.md)|
|**無代理程式註冊**|無法使用 |可用<br>[註冊 Windows 裝置](windows-enroll.md)|
|**軟體更新管理**| Windows Updates 和 Microsoft 應用程式更新<br>[使用軟體更新讓 Windows 電腦維持最新狀態](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)|Windows 10 和 Microsoft 應用程式更新的商務用 Microsoft 市集<br> [設定商務用 Windows Update 的設定](windows-update-for-business-configure.md) |
|**軟體授權管理**|可用 <br>[管理 Windows 電腦軟體的授權合約](manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)|商務用 Microsoft 市集 (僅限 .appx 應用程式)<br>[管理您從商務用 Microsoft 網上商店購買的應用程式](windows-store-for-business.md)|
|**清查**|可用 <br>[檢視 Windows 電腦的硬體和軟體清查](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md)|可用 <br>[如何監視應用程式資訊](apps-monitor.md)<br>[什麼是裝置管理](device-management.md)|
|**Windows 防火牆原則**|可用 <br>[使用 Windows 防火牆原則協助保護 Windows 電腦](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) |可用 <br>[Windows Defender 防火牆](endpoint-protection-windows-10.md#windows-defender-firewall)|
|**反惡意程式碼防護**|Endpoint Protection<br>[使用 Endpoint Protection 協助保護 Windows 電腦](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)|Windows Defender<br>[啟用 Windows Defender](advanced-threat-protection.md)|
|**遠端協助** |TeamViewer<br>[對 Windows 電腦要求及提供遠端協助](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md)|TeamViewer<br> [使用 TeamViewer 來遠端管理 Intune 裝置](device-profile-android-teamviewer.md) |
|**應用程式部署** | 不適用於商務用 Microsoft 市集、<br>僅限 .exe、.appx 和多檔案 .msi<br>[為執行 Intune 軟體用戶端的 Windows 電腦新增應用程式](add-apps-for-windows-pcs-in-microsoft-intune.md)|適用於 Microsoft 市集應用程式及企業營運應用程式<br>[如何新增 Windows 市集應用程式](store-apps-windows.md)<br>[如何新增 Windows 企業營運 (LOB) 應用程式](lob-apps-windows.md)|
|**應用程式保護**|無法使用|可用 <br>[什麼是應用程式保護原則？](app-protection-policy.md)|
|**健康情況證明**|無法使用|可用|


### <a name="advantages-of-mdm-windows-pc-management"></a>MDM Windows 電腦管理的優點
使用最新行動裝置管理的 Windows 電腦管理具有下列優點：
- **延展性** - MDM 管理可隨著 Intune 雲端管理而延展。 Intune 軟體用戶端的上限為 7000 部電腦。
- **簡化** - 使用作業系統隨附的最新管理功能，而無需依賴於下載的軟體用戶端
- **一致性** - 您的 Windows 電腦可以像組織中的其他所有行動裝置一樣管理 <!-- - **Cloud optimization** - -->
