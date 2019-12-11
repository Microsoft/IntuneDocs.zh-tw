---
title: Windows 10 升級和 Microsoft Intune 中的 S 模式設定 - Azure | Microsoft Docs
description: 查看所有設定的清單以及它們在裝置上升級 Windows 10 版本時的用途，或者在 Microsoft Intune 中使用裝置組態設定檔，在裝置上啟用 S 模式。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 75878e2110e9d855c2a0f78c0e7a1112f883872e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72489651"
---
# <a name="windows-10-and-newer-device-settings-to-upgrade-editions-or-enable-s-mode-in-intune"></a>升級版本或在 Intune 中啟用 S 模式的 Windows 10 (和更新版本) 裝置設定

Microsoft Intune 包含許多設定，可協助管理和保護您的裝置。 本文列出並描述升級版本或在 Windows 10 裝置上啟用 S 模式的設定。 這些設定會在 Intune 中推送或部署到裝置的升級組態設定檔中加以建立。

作為行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來控制您 Windows 10 裝置的版本和 S 模式選項。

如需此功能的詳細資訊，請參閱[升級 Windows 10 版本或啟用 S 模式](edition-upgrade-configure-windows-10.md)。

## <a name="before-you-begin"></a>開始之前

[建立設定檔](edition-upgrade-configure-windows-10.md#create-the-profile)。

## <a name="edition-upgrade"></a>版本升級

- **要升級到的版本**：選取您要升級到的 Windows 10 版本。 由此原則設為目標的裝置會升級至您選擇的版本。
- **產品金鑰**：輸入您從 Microsoft 收到的產品金鑰。 建立包含產品金鑰的原則之後，即無法更新金鑰，且會基於安全性考量而隱藏。 若要變更產品金鑰，請再次輸入完整金鑰。
- **授權檔案**：針對**商務用 Windows 10 全像攝影版**或 **Windows 10 行動裝置版**，選擇 [瀏覽]  來選取您從 Microsoft 收到的授權檔案。 這個授權檔案包含您要升級裝置之目標版本的授權資訊。

## <a name="mode-switch"></a>模式切換

- **沒有設定**：S 模式裝置會保持在 S 模式。 終端使用者可以將裝置切換移出 S 模式。
- **Keep in S mode** \(保持在 S 模式\)：防止終端使用者將裝置切換移出 S 模式。
- **Switch** \(切換\)：將裝置切換移出 S 模式。

## <a name="next-steps"></a>後續步驟

雖然設定檔已建立，但它可能還不會執行任何動作。 請務必[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

您也可以針對 [Windows Holographic for Business](holographic-upgrade.md) 裝置建立版本升級設定檔。
