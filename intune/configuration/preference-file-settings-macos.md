---
title: 在 Microsoft Intune 中將喜好設定檔案設定新增至 macOS 裝置 - Azure | Microsoft Docs
titleSuffix: ''
description: 新增 xml 或 plist 檔案，其中包含您應用程式的重要資訊。 使用喜好設定檔案裝置設定檔來變更屬性清單檔中的金鑰資訊，並將其指派給您的 macOS 裝置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d226a5b8ee448b7b168a03fe6b8a1c63bc1be432
ms.sourcegitcommit: 8f56220e7cafc5bc43135940575a9acb5afde730
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827780"
---
# <a name="add-a-property-list-file-to-macos-devices-using-microsoft-intune"></a>使用 Microsoft Intune 將屬性清單檔案新增至 macOS 裝置

使用 Microsoft Intune，您可以為 macOS 裝置或 macOS 裝置上的應用程式新增屬性清單檔案（. plist）。

本功能適用於：

- 執行 10.7 和更新版本的 macOS 裝置

屬性清單檔案通常包含 macOS 應用程式的相關資訊。 如需詳細資訊，請參閱[關於資訊屬性清單](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html)檔案（Apple 的網站）和[自訂承載設定](https://support.apple.com/guide/mdm/custom-mdm9abbdbe7/1/web/1)。

本文列出並描述您可以新增至 macOS 裝置的不同屬性清單檔案設定。 作為行動裝置管理（MDM）解決方案的一部分，請使用這些設定來新增應用程式套件組合識別碼（`com.company.application`），並新增其 plist 檔案。

這些設定會新增至 Intune 裝置組態設定檔，然後指派或部署到您的 macOS 裝置。

## <a name="before-you-begin"></a>開始之前

[建立設定檔](device-profile-create.md)。

## <a name="what-you-need-to-know"></a>您必須知道的事項

- 這些設定不會經過驗證。 請務必先測試您的變更，再將設定檔指派給您的裝置。
- 如果您不確定如何輸入應用程式金鑰，請變更應用程式內的設定。 然後，使用[Xcode](https://developer.apple.com/xcode/)檢查應用程式的喜好設定檔案，以查看設定的設定方式。 Apple 建議您在匯入檔案之前，先使用 Xcode 移除無法管理的設定。
- 只有部分應用程式會使用受管理的喜好設定，而且可能不允許您管理所有設定。
- 請務必上傳以裝置通道設定為目標的屬性清單檔案，而不是使用者通道設定。 以整個裝置為目標的屬性清單檔案。

## <a name="preference-file"></a>喜好設定檔案

- **喜好設定功能變數名稱**：屬性清單檔案通常用於網頁瀏覽器（microsoft Edge）、 [Microsoft Defender Advanced 威脅防護](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac)及自訂應用程式。 當您建立喜好設定網域時，也會建立配套識別碼。 輸入套件組合識別碼，例如 `com.company.application`。 例如，輸入 `com.Contoso.applicationName`、`com.Microsoft.Edge` 或 `com.microsoft.wdav`。
- **屬性清單**檔案：選取與您的應用程式相關聯的屬性清單檔案。 請確定它是 `.plist` 或 `.xml` 檔案。 例如，上傳 `YourApp-Manifest.plist` 或 `YourApp-Manifest.xml` 檔案。
- 檔案**內容**：顯示內容清單檔案中的重要資訊。 如果您需要變更金鑰資訊，請在另一個編輯器中開啟清單檔案，然後在 Intune 中重新上傳該檔案。

請確定您的檔案格式正確。 檔案應該只有索引鍵值組，不應包裝在 `<dict>`、`<plist>`或 `<xml>` 標記中。 例如，您的屬性清單檔案應該類似下列檔案：

```xml
<key>SomeKey</key>
<string>someString</string>
<key>AnotherKey</key>
<false/>
...
```

選取 [確定]   > [建立]  儲存您的變更。 設定檔隨即建立，並顯示在設定檔清單中。

## <a name="next-steps"></a>後續步驟

設定檔已建立，但還不會執行任何動作。 接下來，[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

如需 Microsoft Edge 喜好設定檔的詳細資訊，請參閱[macOS 上的設定 Microsoft edge 原則設定](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac)。
