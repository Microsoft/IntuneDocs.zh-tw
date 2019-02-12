---
title: 升級至 Windows Holographic for Business
titleSuffix: Microsoft Intune
description: 了解如何將執行 Windows Holographic 的裝置升級至 Windows Holographic for Business
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: bfca0cb5b02fdf77fa9a0bab42af05fd04b5c140
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838881"
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>將執行 Windows Holographic 的裝置升級至 Windows Holographic for Business

Microsoft Intune 包含許多設定，可協助管理和保護您的裝置。 本文列出並描述可將 Windows 全像攝影版裝置升級至 Windows Holographic for Business 的設定。 這些設定會在 Intune 中推送或部署到裝置的升級組態設定檔中加以建立。

作為行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來升級您的 Windows 全像攝影版裝置。 至於 Microsoft HoloLens，您可購買 Commercial Suite，以取得升級所需的授權。 如需詳細資訊，請參閱[解除鎖定 Windows Holographic for Business 功能](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise)。

如需此功能的詳細資訊，請參閱[升級 Windows 10 版本或啟用 S 模式](edition-upgrade-configure-windows-10.md)。

## <a name="before-you-begin"></a>開始之前

[建立裝置組態設定檔](edition-upgrade-configure-windows-10.md#create-the-profile)。

## <a name="edition-upgrade"></a>版本升級

- **要升級的目標版本**：選取 [Windows 10 Holographic for Business]。
- **授權檔案**：瀏覽至提供給您的 XML 授權檔案並加以選取。

  ![輸入包含 Holographic for Business 授權資訊的 XML 檔案名稱](media/Holographic-edition-upgrade.png)
 
## <a name="next-steps"></a>後續步驟

雖然設定檔已建立，但它可能還不會執行任何動作。 請務必[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

您也可以針對 [Windows 10 及更新版本](edition-upgrade-windows-settings.md)裝置建立版本升級設定檔。
