---
title: 建立 macOS 核心延伸模組的裝置設定檔與 Microsoft Intune-Azure |Microsoft Docs
titleSuffix: ''
description: 新增或建立 macOS 裝置設定檔，然後再設定核心延伸模組，若要允許使用者覆寫，請在 Microsoft Intune 中新增小組識別碼和套件組合 」 和 「 小組識別碼。
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
ms.openlocfilehash: fd2e03c09cb2bed49ee7607283bf63e2c3ae67da
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403902"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>在 Intune 中新增 macOS 核心延伸模組

MacOS 裝置上，您可以在核心層級加入功能。 這些功能存取規則的程式無法存取 OS 的部分。 您的組織可能有特定需求或無法在應用程式、 裝置功能等等的需求。 

若要加入核心延伸模組一律允許載入您的裝置上，新增 「 核心延伸模組 」 (KEXT) 在 Microsoft Intune，然後將這些擴充功能部署到您的裝置。

例如，您會有病毒掃描程式掃描您的裝置，惡意內容。 您可以加入這個的病毒掃描程式的核心延伸模組，以在 Intune 中允許的核心延伸。 然後，「 指派 」 擴充功能到您的 macOS 裝置。

使用此功能，系統管理員可以允許使用者覆寫核心延伸模組、 加入小組識別碼，以及在 Intune 中新增特定的核心延伸模組。

本功能適用於：

- macOS 10.13.2 與更新版本

若要使用這項功能，裝置必須：

- 使用 Apple 裝置註冊方案 (DEP) 的 Intune 中註冊。 [自動註冊 macOS 裝置](device-enrollment-program-enroll-macos.md)有詳細資訊。

  或

- 在 Intune 中註冊與 「 已核准的使用者註冊 」 （Apple 詞彙）。 [準備在 macOS High Sierra 中的核心延伸模組的變更](https://support.apple.com/en-us/HT208019)（開啟 Apple 的網站） 有更多的資訊。

Intune 會使用「組態設定檔」來依據貴組織的需求建立和自訂這些設定。 在設定檔中新增這些功能之後，您接著可以將設定推送貨部署到您組織中的 macOS 裝置。

這篇文章會示範如何建立裝置組態的設定檔，在 Intune 中使用核心延伸模組。

> [!TIP]
> 如需有關核心延伸模組的詳細資訊，請參閱[核心延伸模組概觀](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html)（開啟 Apple 的網站）。

## <a name="what-you-need-to-know"></a>您必須知道的事項

- 您可以新增不帶正負號的舊版核心延伸模組。
- 請務必輸入適當的團隊識別碼和套件組合的核心延伸模組的識別碼。 Intune 不會驗證您輸入的值。 如果您輸入錯誤的資訊，擴充功能不會在裝置上運作。

> [!NOTE]
> Apple 發行簽章和 notarization 所有軟體的相關資訊。 在 macOS 10.14.5 上及更新版本中，透過 Intune 部署的延伸模組不需要符合 Apple 的 notarization 原則的核心。
>
> 如需此 notarization 原則，以及任何更新或變更的資訊，請參閱下列資源：
>
>  - [Notarizing 之前發佈的應用程式](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution)（開啟 Apple 的網站） 
>  - [準備在 macOS High Sierra 中的核心延伸模組的變更](https://support.apple.com/en-us/HT208019)（開啟 Apple 的網站）

## <a name="create-the-profile"></a>建立設定檔

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
3. 輸入下列內容：

    - **名稱**：為新的設定檔輸入描述性名稱。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取 [macOS] 
    - **設定檔類型**： 選取 **延伸模組**。
    - **設定**：輸入您要設定的設定。 如需所有設定的清單及其用途，請參閱：

        - [macOS](kernel-extensions-settings-macos.md)

4. 當您完成時，請選取 [確定]   > [建立]  儲存變更。

設定檔隨即建立，並顯示在清單中。 請確認會[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

## <a name="next-steps"></a>後續步驟

建立設定檔之後，就可以指派它。 接下來，[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
