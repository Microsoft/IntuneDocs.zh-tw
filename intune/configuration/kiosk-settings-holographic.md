---
title: Microsoft Intune 中 Windows Holographic for Business 的 Kiosk 設定 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，將您的 Windows Holographic for Business 裝置設定為單一應用程式和多應用程式 kiosk、自訂開始功能表、新增應用程式、顯示工作列，以及設定網頁瀏覽器。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e555c62030cede57e98e34034367831c298c0ced
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72492410"
---
# <a name="windows-holographic-for-business-device-settings-to-run-as-a-kiosk-in-intune"></a>Intune 中 Kiosk 執行模式的 Windows Holographic for Business 裝置設定

在 Windows Holographic for Business 裝置上，您可以設定這些裝置在單一應用程式 kiosk 模式或多應用程式 kiosk 模式中執行。 Windows Holographic for Business 不支援某些功能。

本文列出並說明您可以在 Windows Holographic for Business 裝置 上控制的各種不同設定。 作為行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來設定讓您的 Windows Holographic for Business 裝置以 kiosk 模式執行。

身為 Intune 系統管理員，您可以建立這些設定並將其指派給您的裝置。

若要深入了解 Intune 中的 Windows kiosk 功能，請參閱[設定 Kiosk 設定](kiosk-settings.md)。

## <a name="before-you-begin"></a>開始之前

[建立設定檔](kiosk-settings.md#create-the-profile)。

## <a name="single-full-screen-app-kiosks"></a>單一全螢幕應用程式 Kiosk

當您選擇單一應用程式 kiosk 模式時，請輸入下列設定：

- **使用者登入類型**：選取 [本機使用者帳戶]  以輸入本機 (對裝置而言) 使用者帳戶，或與 kiosk 應用程式建立關聯的 Microsoft 帳戶 (MSA)。 Windows Holographic for Business 不支援 [自動登入]  使用者帳戶類型。

- **應用程式類型**：選取 [市集應用程式]  。

- **要以 kiosk 模式執行的應用程式**：選擇 [新增市集應用程式]  ，然後從清單中選取應用程式。

    目前未列出任何應用程式？ 請使用[用戶端應用程式](../apps/apps-add.md)中的步驟新增一些應用程式。

    按一下 [確定]  以儲存您的變更。

## <a name="multi-app-kiosks"></a>多應用程式 kiosk

此模式下的應用程式可以在 [開始] 功能表中使用。 這些應用程式是使用者唯一能夠開啟的應用程式。 當您選擇多應用程式 kiosk 模式時，請輸入下列設定：

- **以 S 模式的 Windows 10 裝置為目標**：選擇 [否]  。 Windows Holographic for Business 不支援 S 模式。

- **使用者登入類型**：新增一或多個可使用所新增應用程式的使用者帳戶。 選項包括： 

  - **自動登入**：不支援 Windows Holographic for Business。
  - **本機使用者帳戶**：[新增]  本機 (對裝置而言) 使用者帳戶。 您輸入的帳戶可用來登入 kiosk。
  - **Azure AD 使用者或群組 (Windows 10 1803 版和更新版本)** ：需要使用者認證才能登入裝置。 選取 [新增]  以從清單中選擇 Azure AD 使用者或群組。 您可以選取多個使用者和群組。 選擇 [選取]  以儲存您的變更。
  - **HoloLens 訪客**：訪客帳戶是來賓帳戶，不需要任何使用者認證或驗證，如 [shared PC mode concepts](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts) (共用電腦模式概念) 中所述。

- **應用程式**：新增要在 kiosk 裝置上執行的應用程式。 請記住，您可以新增數個應用程式。

  - **新增商店應用程式**：選取您新增或部署到 Intune 作為[用戶端應用程式](../apps/apps-add.md)（包括 LOB 應用程式）的現有應用程式。 如果您沒有列出任何應用程式，Intune 會支援您[新增至 intune](../apps/store-apps-windows.md)的許多[應用程式類型](../apps/apps-add.md)。
  - **新增 Win32 應用程式**：不支援Windows Holographic for Business。
  - **依 AUMID 新增**：使用此選項可新增現成的 Windows 應用程式。 輸入下列內容： 

    - **應用程式名稱**：必要。 輸入應用程式的名稱。
    - **應用程式使用者模型識別碼 (AUMID)** ：必要。 輸入 Windows 應用程式的應用程式使用者模型識別碼 (AUMID)。 若要取得此識別碼，請參閱 [find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (尋找已安裝應用程式的應用程式使用者模型識別碼)。
    - **磚大小**：必要。 針對應用程式磚大小，選擇 [小]、[中]、[寬] 或 [大]。

- **Kiosk 瀏覽器設定**：不支援Windows Holographic for Business。

- **使用其他開始畫面版面配置**：選擇 [是]  以輸入描述應用程式在 [開始] 功能表上如何顯示 (包括應用程式的順序) 的 XML 檔案。 如果您需要在 [開始] 功能表中有更多自訂項目，請使用此選項。 [自訂與匯出 [開始] 配置](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens)提供一些指引，並包含 Windows Holographic for Business 裝置的特定 XML 檔案。

- **Windows 工作列**：不支援 Windows Holographic for Business。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

您也可以為 [Android](device-restrictions-android.md#kiosk)、[Android 企業](device-restrictions-android-for-work.md#dedicated-device-settings)及 [Windows 10 和更新版本](kiosk-settings-windows.md) 裝置建立 kiosk 設定檔。
