---
title: Microsoft Intune 中 Windows 10 的 Kiosk 設定 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中將您的 Windows 10 (和更新版本) 裝置設定為單一應用程式和多應用程式 Kiosk、自訂 [開始] 功能表、新增應用程式、顯示工作列，以及設定網頁瀏覽器。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/11/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a80e4cf4e68235ef9e88943a8b62121e0cfb6623
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66046965"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>在 Intune 中讓 Windows 10 和更新版本的裝置以 Kiosk 形式執行

在 Windows 10 和更新版本的裝置上，您可以設定讓這些裝置以單一應用程式 Kiosk 模式或多應用程式 Kiosk 模式執行。

本文列出並描述您可以在 Windows 10 及更新版本裝置上控制的各種不同設定。 作為行動裝置管理 (MDM) 解決方案的一部分，使用這些設定來設定讓 Windows 10 和更新版本的裝置以 Kiosk 模式執行。

身為 Intune 系統管理員，您可以建立這些設定並將其指派給您的裝置。

若要深入了解 Intune 中的 Windows kiosk 功能，請參閱[設定 Kiosk 設定](kiosk-settings.md)。

## <a name="before-you-begin"></a>開始之前

- [建立設定檔](kiosk-settings.md#create-the-profile)。

- 此 kiosk 設定檔直接與您使用 [Microsoft Edge kiosk 設定](device-restrictions-windows-10.md#microsoft-edge-browser)建立的裝置限制設定檔相關。 總括來說：

  1. 建立此 kiosk 設定檔以在 kiosk 模式下執行裝置。
  2. 建立[裝置限制設定檔](device-restrictions-windows-10.md#microsoft-edge-browser)，並設定 Microsoft Edge 中允許的特定功能及設定。

> [!IMPORTANT] 
> 請務必將此 kiosk 設定檔指派給與您 [Microsoft Edge 設定檔](device-restrictions-windows-10.md#microsoft-edge-browser)相同的裝置。

## <a name="single-full-screen-app-kiosks"></a>單一全螢幕應用程式 Kiosk

僅在裝置執行一個應用程式。

- **選取 kiosk 模式**：選擇 [單一應用程式、全螢幕 kiosk]  。

- **使用者登入類型**：您新增的應用程式會以您所輸入使用者帳戶身分執行。 選項包括：

  - **自動登入 (Windows 10 1803 版和更新版本)** ：用於對外環境中不需要使用者登入的 Kiosk，其與來賓帳戶類似。 這項設定使用 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)。
  - **本機使用者帳戶**：輸入本機 (對裝置而言) 使用者帳戶。 您輸入的帳戶會登入 kiosk。

- **應用程式類型**：選取應用程式類型。 選項包括：

  - **新增 Microsoft Edge 瀏覽器**：選取 [Microsoft Edge 瀏覽器]  ，然後選擇 [Edge kiosk 模式類型]  ：

    - **數位/互動式告示板**：以全螢幕開啟 URL，並僅顯示該網站上的內容。 [設定數位告示板](https://docs.microsoft.com/windows/configuration/setup-digital-signage)提供此功能的詳細資訊。
    - **公開瀏覽 (InPrivate)** ：執行 Microsoft Edge 的受限多重索引標籤版本。 使用者可以公開瀏覽，或結束其瀏覽工作階段。

    如需這些選項的詳細資訊，請參閱[部署 Microsoft Edge kiosk 模式](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types)。

    > [!NOTE]
    > 此設定可啟用裝置上的 Microsoft Edge 瀏覽器。 若要設定特定於 Microsoft Edge 的設定，請建立裝置組態設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10]  平台 > [裝置限制]   >  [Microsoft Edge 瀏覽器]  )。 [Microsoft Edge 瀏覽器](device-restrictions-windows-10.md#microsoft-edge-browser)會列出並描述可用的設定。

    按一下 [確定]  以儲存您的變更。

  - **新增 kiosk 瀏覽器**：選取 [Kiosk 瀏覽器設定]  。 這些設定會控制 Kiosk 上的網頁瀏覽器應用程式。 請確定您從 Microsoft Store 取得 [Kiosk 瀏覽器應用程式](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP)、將其新增至 Intune 作為[用戶端應用程式](apps-add.md)，然後將應用程式指派給 kiosk 裝置。

    輸入下列設定：

    - **預設的首頁 URL**：輸入 kiosk 瀏覽器開啟或重新啟動時所顯示的預設 URL。 例如，輸入 `http://bing.com` 或 `http://www.contoso.com`。

    - **首頁按鈕**：[顯示]  或 [隱藏]  kiosk 瀏覽器的首頁按鈕。 預設不會顯示此按鈕。

    - **導覽按鈕**：[顯示]  或 [隱藏]  向前和向後按鈕。 預設不會顯示導覽按鈕。

    - **結束工作階段按鈕**：[顯示]  或 [隱藏]  結束工作階段按鈕。 顯示時，使用者可選取按鈕，而應用程式會提示結束工作階段。 確認時，瀏覽器會清除所有瀏覽資料 (Cookie、快取等)，然後開啟預設 URL。 預設不會顯示此按鈕。

    - **在閒置時間後重新整理瀏覽器**：輸入閒置時間量 (1-1440 分鐘)，在該時間之後 kiosk 瀏覽器會以全新狀態重新啟動。 閒置時間是自使用者上次互動之後所經過的分鐘數。 根據預設，此值是空的或空白，這表示沒有任何閒置逾時。

    - **允許的網站**：使用此設定可允許開啟特定網站。 換句話說，使用此功能可在裝置上限制或防止網站。 例如，您可以允許開啟位於 `http://contoso.com*` 的所有網站。 預設會允許所有網站。

      若要允許特定網站，請上傳包含不同行上所允許網站清單的檔案。 如果您未新增檔案，則會允許所有網站。 Intune 支援以 `*` (星號) 作為萬用字元。

      範例檔案應類以下列清單：

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`  

    按一下 [確定]  以儲存您的變更。

  - **新增市集應用程式**：選取 [新增市集應用程式]  然後從清單中選取應用程式。

    目前未列出任何應用程式？ 請使用[用戶端應用程式](apps-add.md)中的步驟新增一些應用程式。

  按一下 [確定]  以儲存您的變更。

## <a name="multi-app-kiosks"></a>多應用程式 kiosk

此模式下的應用程式可以在 [開始] 功能表中使用。 這些應用程式是使用者唯一能夠開啟的應用程式。 如果應用程式對另一個應用程式具有相依性，則兩者都必須包含在允許的應用程式清單中。 例如，Internet Explorer 64 位元相依於 Internet Explorer 32 位元，因此您必須允許 "C:\Program Files\internet explorer\iexplore.exe" 和 “C:\Program Files (x86)\Internet Explorer\iexplore.exe”。 

- **選取 kiosk 模式**：選擇 [多應用程式 kiosk]  。

- **以 S 模式的 Windows 10 裝置為目標**：
  - **是**：允許 Kiosk 設定檔中的市集應用程式和 AUMID 應用程式 (Win32 應用程式除外)。
  - **否**：允許 Kiosk 設定檔中的市集應用程式、Win32 應用程式和 AUMID 應用程式。 此 kiosk 設定檔不會部署到 S 模式裝置。

- **使用者登入類型**：您新增的應用程式會以您所輸入使用者帳戶身分執行。 選項包括：

  - **自動登入 (Windows 10 1803 版和更新版本)** ：用於對外環境中不需要使用者登入的 Kiosk，其與來賓帳戶類似。 這項設定使用 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)。
  - **本機使用者帳戶**：[新增]  本機 (對裝置而言) 使用者帳戶。 您輸入的帳戶會登入 kiosk。
  - **Azure AD 使用者或群組 (Windows 10 1803 版和更新版本)** ：選取 [新增]  以從清單中選擇 Azure AD 使用者或群組。 您可以選取多個使用者和群組。 選擇 [選取]  以儲存您的變更。
  - **HoloLens 訪客**：訪客帳戶是來賓帳戶，不需要任何使用者認證或驗證，如 [shared PC mode concepts](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts) (共用電腦模式概念) 中所述。

- **瀏覽器和應用程式**：新增要在 Kiosk 裝置上執行的應用程式。 請記住，您可以新增數個應用程式。

  - **瀏覽器**

    - **新增 Microsoft Edge**：Microsoft Edge 會新增至應用程式方格，所有的應用程式都可以在此 kiosk 上執行。 選擇 [Microsoft Edge kiosk 模式類型]  ：

      - **標準模式 (完整版 Microsoft Edge)** ：執行具備所有瀏覽功能的完整版 Microsoft Edge。 使用者資料和狀態會在工作階段之間儲存。
      - **公開瀏覽 (InPrivate)** ：執行 Microsoft Edge InPrivate 的多重索引標籤版本，為在全螢幕模式中執行之 kiosk 提供量身打造的體驗。

      如需這些選項的詳細資訊，請參閱[部署 Microsoft Edge kiosk 模式](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types)。

      > [!NOTE]
      > 此設定可啟用裝置上的 Microsoft Edge 瀏覽器。 若要設定特定於 Microsoft Edge 的設定，請建立裝置組態設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10]  平台 > [裝置限制]   >  [Microsoft Edge 瀏覽器]  )。 [Microsoft Edge 瀏覽器](device-restrictions-windows-10.md#microsoft-edge-browser)會列出並描述可用的設定。

      按一下 [確定]  以儲存您的變更。

    - **新增 Kiosk 瀏覽器**：這些設定會控制 Kiosk 上的網頁瀏覽器應用程式。 請確定您使用[用戶端應用程式](apps-add.md)將網頁瀏覽器應用程式部署到 kiosk 裝置。

      輸入下列設定：

      - **預設的首頁 URL**：輸入 kiosk 瀏覽器開啟或重新啟動時所顯示的預設 URL。 例如，輸入 `http://bing.com` 或 `http://www.contoso.com`。

      - **首頁按鈕**：[顯示]  或 [隱藏]  kiosk 瀏覽器的首頁按鈕。 預設不會顯示此按鈕。

      - **導覽按鈕**：[顯示]  或 [隱藏]  向前和向後按鈕。 預設不會顯示導覽按鈕。

      - **結束工作階段按鈕**：[顯示]  或 [隱藏]  結束工作階段按鈕。 顯示時，使用者可選取按鈕，而應用程式會提示結束工作階段。 確認時，瀏覽器會清除所有瀏覽資料 (Cookie、快取等)，然後開啟預設 URL。 預設不會顯示此按鈕。

      - **在閒置時間後重新整理瀏覽器**：輸入閒置時間量 (1-1440 分鐘)，在該時間之後 kiosk 瀏覽器會以全新狀態重新啟動。 閒置時間是自使用者上次互動之後所經過的分鐘數。 根據預設，此值是空的或空白，這表示沒有任何閒置逾時。

      - **允許的網站**：使用此設定可允許開啟特定網站。 換句話說，使用此功能可在裝置上限制或防止網站。 例如，您可以允許開啟位於 `contoso.com*` 的所有網站。 預設會允許所有網站。

        若要允許特定網站，請上傳包含允許網站清單的 .csv 檔案。 如果您未新增 .csv 檔案，則會允許所有網站。

      按一下 [確定]  以儲存您的變更。

  - **應用程式**

    - **新增市集應用程式**：從商務用 Microsoft Store 新增應用程式。 如果目前未列出任何應用程式，則您可以取得應用程式，然後[將其新增至 Intune](store-apps-windows.md)。 例如，您可以新增 Kiosk 瀏覽器、Excel、OneNote 等。

      按一下 [確定]  以儲存您的變更。

    - **新增 Win32 應用程式**：Win32 應用程式是傳統型應用程式，例如 Visual Studio Code 或 Google Chrome。 輸入下列內容：

      - **應用程式名稱**：必要。 輸入應用程式的名稱。
      - **本機路徑**：必要。 輸入可執行檔的路徑，例如 `C:\Program Files (x86)\Microsoft VS Code\Code.exe` 或 `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`。
      - **應用程式使用者模型識別碼 (AUMID)** ：輸入 Win32 應用程式的應用程式使用者模型識別碼 (AUMID)。 此設定可決定桌面上磚的開始畫面版面配置。 若要取得此識別碼，請參閱 [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps)。

      按一下 [確定]  以儲存您的變更。

    - **依 AUMID 新增**：使用此選項可新增現成的 Windows 應用程式，例如 [記事本] 或 [小算盤]。 輸入下列內容：

      - **應用程式名稱**：必要。 輸入應用程式的名稱。
      - **應用程式使用者模型識別碼 (AUMID)** ：必要。 輸入 Windows 應用程式的應用程式使用者模型識別碼 (AUMID)。 若要取得此識別碼，請參閱 [find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (尋找已安裝應用程式的應用程式使用者模型識別碼)。

      按一下 [確定]  以儲存您的變更。

    - **自動啟動**：選擇性。 選擇使用者登入時自動啟動的應用程式。 只有一個應用程式可以自動啟動。
    - **磚大小**：必要。 針對應用程式磚大小，選擇 [小]、[中]、[寬] 或 [大]。

  > [!TIP]
  > 新增所有應用程式之後，您可以按一下並拖曳清單中的應用程式來變更顯示順序。  

- **使用其他開始畫面版面配置**：選擇 [是]  以輸入描述應用程式在 [開始] 功能表上如何顯示 (包括應用程式的順序) 的 XML 檔案。 如果您需要在 [開始] 功能表中有更多自訂項目，請使用此選項。 [自訂與匯出 [開始] 配置](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout)提供一些指引和範例 XML。

- **Windows 工作列**：選擇 [顯示]  或 [隱藏]  工作列。 預設不會顯示此工作列。 圖示 (例如 Wi-Fi 圖示) 會顯示，但使用者無法變更設定。

- **允許下載資料夾的存取權**：選擇 [是]  以允許使用者存取 Windows 檔案總管中的 [下載] 資料夾。 根據預設，已停用對 [下載] 資料夾的存取權。 這項功能通常用於讓終端使用者存取從瀏覽器下載的項目。

按一下 [確定]  以儲存您的變更。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

您也可以為 [Android](device-restrictions-android.md#kiosk)、[Android 企業](device-restrictions-android-for-work.md#dedicated-device-settings)及 [Windows Holographic for Business](kiosk-settings-holographic.md) 裝置建立 Kiosk 設定檔。
