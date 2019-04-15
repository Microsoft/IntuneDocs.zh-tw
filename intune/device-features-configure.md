---
title: 使用 Microsoft Intune 建立 iOS 或 macOS 裝置設定檔 - Azure | Micrososft Docs
description: 新增或建立 iOS 或 macOS 裝置設定檔，然後在 Microsoft Intune 中設定 AirPrint 的設定、主畫面配置、應用程式通知、共用裝置、單一登入，以及網路內容篩選器設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5ae03a4155fa2d170648548bb9a08b570f49c673
ms.sourcegitcommit: 25e17a1d002ee1faa49bb89648eb59373528539f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "59566616"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>在 Intune 中新增 iOS 或 macOS 裝置功能設定

Intune 包含許多可協助系統管理員控制 iOS 和 macOS 裝置的功能和設定。 例如，系統管理員可以：

- 允許使用者存取您網路中的 AirPrint 印表機
- 將應用程式與資料夾新增至主畫面，包括新增頁面
- 選擇是否要顯示應用程式通知及如何顯示
- 設定鎖定畫面以顯示一則訊息或資產標記，特別適用於共用裝置
- 為使用者提供在應用程式之間共用認證的安全單一登入體驗
- 篩選使用成人內容語言的網站，並允許或封鎖特定網站

這些功能均適用於 Intune，而且可由系統管理員加以設定。 Intune 會使用「組態設定檔」，基於您組織的需求來建立和自訂這些設定。 在設定檔中新增這些功能之後，接著可將設定檔推送或部署至組織中的 iOS 和 macOS 裝置。

本文示範如何建立裝置組態設定檔。 您也可以查看適用於 [iOS](ios-device-features-settings.md) 和 [macOS](macos-device-features-settings.md) 裝置的所有可用設定。

## <a name="create-a-device-profile"></a>建立裝置設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務] > 篩選 [Intune] > 選取 [Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入下列內容：

    - **名稱**：為新的設定檔輸入描述性名稱。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取您的平台：
        - **iOS**
        - **macOS**
    - **設定檔類型**：選取 [裝置功能]。
    - **設定**：輸入您要設定的設定。 如需所有設定的清單及其功用，請參閱：

        - [iOS](ios-device-features-settings.md)
        - [macOS](macos-device-features-settings.md)

4. 當您完成時，請選取 [確定]，然後選擇 [建立] 儲存變更。

設定檔隨即建立並顯示於清單中。 請確認會[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

## <a name="next-steps"></a>後續步驟

建立設定檔之後，就可以指派它。 接下來，[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

檢視適用於 [iOS](ios-device-features-settings.md) 和 [macOS](macos-device-features-settings.md) 裝置的所有裝置功能設定。
