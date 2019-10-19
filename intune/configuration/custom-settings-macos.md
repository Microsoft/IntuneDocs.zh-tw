---
title: 在 Microsoft Intune 中將自訂設定新增至 macOS 裝置 - Azure | Microsoft Docs
titleSuffix: ''
description: 從 Apple Configurator 或 Apple Profile Manager 工具匯出 macOS 設定，然後將這些設定匯入 Microsoft Intune。 這些設定可以建立、使用及控制 macOS 裝置上的自訂設定和功能。 此自訂設定檔可接著指派或散發到您組織中的 macOS 裝置，以建立基準或標準。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c24c120b033a4db0162e985ef185932dd931eda
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506916"
---
# <a name="use-custom-settings-for-macos-devices-in-microsoft-intune"></a>在 Microsoft Intune 中使用 macOS 裝置的自訂設定

透過 Microsoft Intune，您可以使用「自訂設定檔」新增或建立 macOS 裝置的自訂設定。 自訂設定檔是 Intune 中的功能。 其設計目的是為了新增未內建在 Intune 的裝置設定和功能。

使用 macOS 裝置時，您可以透過兩種方式將自訂設定匯入 Intune：

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

您可以使用這些工具，將設定匯出至組態設定檔。 在 Intune 中，您可以匯入此檔案，然後將設定檔指派給您的 macOS 使用者和裝置。 指派之後，就會散發設定。 他們也會在您的組織中建立 macOS 的基準或標準。

本文提供使用 Apple 設定和 Apple Profile Manager 的一些指引，並說明您可以設定的屬性。

## <a name="before-you-begin"></a>開始之前

[建立設定檔](device-profile-create.md)。

## <a name="what-you-need-to-know"></a>您必須知道的事項

- 使用 **Apple Configurator** 建立組態設定檔時，請確定您所匯出的設定與裝置上的 macOS 版本相容。 如需解決不相容設定的資訊，請在 [Apple Developer](https://developer.apple.com/) (Apple 開發人員) 網站上搜尋 **Configuration Profile Reference** (組態設定檔參考) 和 **Mobile Device Management Protocol Reference** (行動裝置管理通訊協定參考)。

- 使用 **Apple Profile Manager** 時，請確定：

  - 在 Profile Manager 中啟用[行動裝置管理](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C)。
  - 在 Profile Manager 中新增 [macOS 裝置](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984)。
  - 在 Profile Manager 中新增裝置之後，請移至 [Under the Library] \(在程式庫下\)   > [Devices] \(裝置\)  > 選取您的裝置 > [Settings] \(設定\)  。 輸入裝置的一般、安全性、隱私權、目錄和憑證設定。

    下載並儲存此檔案。 您將在 Intune 設定檔中輸入此檔案。 

  - 確定您從 Apple Profile Manager 匯出的設定與裝置上的 macOS 版本相容。 如需解決不相容設定的資訊，請在 [Apple Developer](https://developer.apple.com/) (Apple 開發人員) 網站上搜尋 **Configuration Profile Reference** (組態設定檔參考) 和 **Mobile Device Management Protocol Reference** (行動裝置管理通訊協定參考)。

## <a name="custom-configuration-profile-settings"></a>自訂組態設定檔設定

- **自訂組態設定檔名稱**：輸入原則的名稱。 此名稱會在裝置上和 Intune 狀態中顯示。
- **組態設定檔**：瀏覽至使用 Apple Configurator 或 Apple Profile Manager 所建立的組態設定檔。 您匯入的檔案會顯示在 [檔案內容]  區域中。

  您也可以將裝置權杖新增至您的 `.mobileconfig` 檔案。 裝置權杖是用來新增裝置特定資訊。 例如，若要顯示序號，請輸入 `{{serialnumber}}`。 在裝置上，顯示的文字類似于 `123456789ABC`，這對每個裝置而言都是唯一的。 輸入變數時，請務必使用大括弧 `{{ }}`。 [應用程式設定權杖](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)包含可以使用的變數清單。 您也可以使用 `deviceid` 或任何其他的裝置特定值。

  > [!NOTE]
  > 變數不會在 UI 中進行驗證，而且會區分大小寫。 因此，您可能會看到儲存之設定檔含有不正確的輸入。 例如，如果您輸入 `{{DeviceID}}` 而不是 `{{deviceid}}`，則會顯示常值字串而不是裝置的唯一識別碼。 請務必輸入正確的資訊。

選取 [確定]   > [建立]  儲存您的變更。 設定檔隨即建立，並顯示在設定檔清單中。

## <a name="next-steps"></a>後續步驟

設定檔已建立，但還不會執行任何動作。 接下來，請[指派此設定檔](device-profile-assign.md)。

了解如何[在 iOS 裝置上建立設定檔](../custom-settings-ios.md)。
