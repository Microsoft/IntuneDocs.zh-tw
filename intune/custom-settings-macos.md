---
title: 在 Microsoft Intune 中將自訂設定新增至 macOS 裝置 - Azure | Microsoft Docs
titleSuffix: ''
description: 從 Apple Configurator 或 Apple Profile Manager 工具匯出 macOS 設定，然後將這些設定匯入 Microsoft Intune。 這些設定可以建立、使用及控制 macOS 裝置上的自訂設定和功能。 此自訂設定檔可接著指派或散發到您組織中的 macOS 裝置，以建立基準或標準。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b8ce3317bf44e70a64851a0d325e8032d33bab8a
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566279"
---
# <a name="use-custom-settings-for-macos-devices-in-microsoft-intune"></a>在 Microsoft Intune 中使用 macOS 裝置的自訂設定

透過 Microsoft Intune，您可以使用「自訂設定檔」新增或建立 macOS 裝置的自訂設定。 自訂設定檔是 Intune 中的功能。 其設計目的是為了新增未內建在 Intune 的裝置設定和功能。

使用 macOS 裝置時，您可以透過兩種方式將自訂設定匯入 Intune：

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

您可以使用這些工具，將設定匯出至組態設定檔。 在 Intune 中，您可以匯入此檔案，然後將設定檔指派給您的 macOS 使用者和裝置。 一旦指派，將會散發這些設定，並同時為您組織中的 macOS 建立基準或標準。

本文示範如何建立 macOS 裝置的自訂設定檔。 其中也會提供有關使用 Apple Configurator 和 Apple Profile Manager 的一些指引。

## <a name="before-you-begin"></a>開始之前

- 使用 **Apple Configurator** 建立組態設定檔時，請確定您所匯出的設定與所使用裝置上的 macOS 版本相容。 如需解決不相容設定的資訊，請在 [Apple Developer](https://developer.apple.com/) (Apple 開發人員) 網站上搜尋 **Configuration Profile Reference** (組態設定檔參考) 和 **Mobile Device Management Protocol Reference** (行動裝置管理通訊協定參考)。

- 使用 **Apple Profile Manager** 時，請確定：

  - 在 Profile Manager 中啟用[行動裝置管理](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C)。
  - 在 Profile Manager 中新增 [macOS 裝置](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984)。
  - 在 Profile Manager 中新增裝置之後，請移至 [Under the Library] \(在程式庫下\) > [Devices] \(裝置\) > 選取您的裝置 > [Settings] \(設定\)。 輸入裝置的一般、安全性、隱私權、目錄和憑證設定。

    下載並儲存此檔案。 您將在 Intune 設定檔中輸入此檔案。 

  - 確定您從 Apple Profile Manager 匯出的設定與所使用裝置上的 macOS 版本相容。 如需解決不相容設定的資訊，請在 [Apple Developer](https://developer.apple.com/) (Apple 開發人員) 網站上搜尋 **Configuration Profile Reference** (組態設定檔參考) 和 **Mobile Device Management Protocol Reference** (行動裝置管理通訊協定參考)。

## <a name="create-the-profile"></a>建立設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入下列設定：

    - **名稱**：輸入設定檔的名稱，例如 `macos custom profile`。
    - **描述**：輸入設定檔的描述。
    - **平台**：選擇 [macOS]。
    - **設定檔類型**：選擇 [自訂]。

4. 在 [自訂設定] 中，輸入下列設定：

    - **自訂組態設定檔名稱**：輸入原則的名稱。 此名稱會在裝置上和 Intune 狀態中顯示。
    - **組態設定檔**：瀏覽至使用 Apple Configurator 或 Apple Profile Manager 所建立的組態設定檔。 您匯入的檔案會顯示在 [檔案內容] 區域中。

5. 選取 [確定] > [建立] 以建立 Intune 設定檔。 完成時，您的設定檔會顯示在 [裝置設定 - 設定檔] 清單中。

## <a name="next-steps"></a>後續步驟

設定檔已建立，但還不會執行任何動作。 接下來，請[指派此設定檔](device-profile-assign.md)。

了解如何[在 iOS 裝置上建立設定檔](custom-settings-ios.md)。
