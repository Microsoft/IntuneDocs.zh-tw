---
title: 使用 Microsoft Intune 建立 macOS 核心擴充裝置設定檔-Azure |Microsoft Docs
titleSuffix: ''
description: 新增或建立 macOS 裝置設定檔, 然後將核心延伸模組設定為允許使用者覆寫、新增小組識別碼, 以及 Microsoft Intune 中的組合和小組識別碼。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: eca4692189af9272d3d1fc427b4eba638d8b5b27
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882977"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>在 Intune 中新增 macOS 核心延伸模組

在 macOS 裝置上, 您可以在核心層級新增功能。 這些功能可存取一般程式無法存取的 OS 部分。 您的組織可能會有應用程式、裝置功能等等中未提供的特定需求或需求。 

若要新增一律允許在您的裝置上載入的核心延伸模組, 請在 Microsoft Intune 中新增「核心延伸模組」 (KEXT), 然後將這些擴充功能部署到您的裝置。

例如, 您的病毒掃描程式會掃描您的裝置是否有惡意內容。 您可以在 Intune 中將此病毒掃描程式的核心延伸模組新增為允許的核心延伸模組。 然後, 將擴充功能「指派」至您的 macOS 裝置。

有了這項功能, 系統管理員可以讓使用者覆寫核心擴充功能、新增小組識別碼, 以及在 Intune 中新增特定的核心延伸模組。

本功能適用於：

- macOS 10.13.2 與更新版本

若要使用這項功能, 裝置必須:

- 使用 Apple 的裝置註冊計劃 (DEP) 在 Intune 中註冊。 [自動註冊 macOS 裝置](device-enrollment-program-enroll-macos.md)有詳細資訊。

  或

- 已在 Intune 中註冊「使用者核准的註冊」 (Apple 的條款)。 [準備 MacOS High 中核心延伸模組的變更](https://support.apple.com/en-us/HT208019)(開啟 Apple 的網站) 有詳細資訊。

Intune 會使用「組態設定檔」來依據貴組織的需求建立和自訂這些設定。 在設定檔中新增這些功能之後，您接著可以將設定推送貨部署到您組織中的 macOS 裝置。

本文說明如何使用 Intune 中的核心擴充功能來建立裝置設定檔。

> [!TIP]
> 如需有關核心擴充功能的詳細資訊, 請參閱[核心延伸模組總覽](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html)(開啟 Apple 的網站)。

## <a name="what-you-need-to-know"></a>您必須知道的事項

- 可新增未簽署的舊版核心延伸模組。
- 請務必輸入核心延伸模組的正確 [小組識別碼] 和 [套件組合識別碼]。 Intune 不會驗證您輸入的值。 如果您輸入錯誤的資訊, 此延伸模組將無法在裝置上使用。

> [!NOTE]
> Apple 已發行有關簽署和 notarization 所有軟體的資訊。 在 macOS 10.14.5 和更新版本上, 透過 Intune 部署的核心延伸模組不需要符合 Apple 的 notarization 原則。
>
> 如需此 notarization 原則及任何更新或變更的相關資訊, 請參閱下列資源:
>
> - [在散發之前 Notarizing 您的應用程式](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution)(開啟 Apple 的網站) 
> - [準備 MacOS High 中核心延伸模組的變更](https://support.apple.com/en-us/HT208019)(開啟 Apple 的網站)

## <a name="create-the-profile"></a>建立設定檔

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
3. 輸入下列內容：

    - **名稱**：為新的設定檔輸入描述性名稱。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取 [macOS] 
    - **配置檔案類型**: 選取 [**擴充**功能]。
    - **設定**：輸入您要設定的設定。 如需所有設定的清單及其用途，請參閱：

        - [macOS](kernel-extensions-settings-macos.md)

4. 當您完成時，請選取 [確定]   > [建立]  儲存變更。

設定檔隨即建立，並顯示在清單中。 請確認會[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

## <a name="next-steps"></a>後續步驟

建立設定檔之後，就可以指派它。 接下來，[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
