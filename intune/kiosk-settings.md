---
title: Microsoft Intune 中 Windows 10 的 Kiosk 設定 - Azure | Microsoft Docs
description: 將您的 Windows 10 (及更新版本) 裝置設定為單一應用程式和多應用程式 kiosk，包括自訂 [開始] 功能表、新增應用程式、工作列及設定網頁瀏覽器。 此外，在 Microsoft Intune 中將 Windows Holographic for Business 裝置設定為多應用程式 kiosk。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 59e2ab4635c8488b99781ac123aacd0854967dc8
ms.sourcegitcommit: c3ac9e5f6240223cb5dfed8b44c7425066d6ea86
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49380026"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Intune 中適用於 Windows 10 (和更新版本) 的 Kiosk 設定

在 Windows 10 裝置上，您可以使用 Intune 來執行這些裝置作為 kiosk。 Kiosk 可以執行一或多個應用程式。 您也可以顯示和自訂 [開始] 功能表、新增不同的應用程式 (包括 Win32 應用程式)、將特定首頁新增至網頁瀏覽器，以及執行更多作業。 

請使用本文中的步驟，在 Intune 中建立單一應用程式 kiosk 或多應用程式 kiosk。

Intune 針對每部裝置支援一個 kiosk 設定檔。 如果您需要在單一裝置上有多個 kiosk 設定檔，則可以使用[自訂 OMA-URI](custom-settings-windows-10.md)。

## <a name="kiosk-settings"></a>Kiosk 設定

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入下列內容：

   - **名稱**：為新的設定檔輸入描述性名稱。
   - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
   - **平台**：選取 [Windows 10 and later] \(Windows 10 及更新版本\)
   - **設定檔類型**：選取 [Kiosk (預覽)]

4. 選取 [kiosk 模式]。 [Kiosk 模式] 可識別原則支援的 Kiosk 模式類型。 這些選項包括：

    - **未設定** (預設)：原則不會啟用 kiosk 模式。
    - **單一應用程式、全螢幕 kiosk**：裝置以單一使用者帳戶執行，並將其鎖定到單一市集應用程式。 因此當使用者登入時，會啟動特定的應用程式。 此模式也會限制使用者開啟新的應用程式或變更執行中的應用程式。
    - **多應用程式 kiosk**：裝置藉由使用應用程式使用者模型識別碼 (AUMID) 來執行多個市集應用程式、Win32 應用程式或現成的 Windows 應用程式。 只有您新增的應用程式才可在裝置上使用。

        多應用程式 Kiosk (或固定用途裝置) 的優點是讓使用者只存取所需的應用程式，來為他們提供一個簡單明瞭的體驗。 此外，還可從其檢視中移除不需要的應用程式。

## <a name="single-full-screen-app-kiosks"></a>單一全螢幕應用程式 Kiosk
當您選擇單一應用程式 kiosk 模式時，請輸入下列設定：

- **使用者登入類型**：您新增的應用程式會以您所輸入使用者帳戶身分執行。 選項包括：

  - **自動登入 (Windows 10 1803 版和更新版本)**：對外環境中的 kiosk 不需要使用者登入，其與來賓帳戶類似。 這項設定使用 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)。
  - **本機使用者帳戶**：輸入本機 (對裝置而言) 使用者帳戶。 您輸入的帳戶可用來登入 kiosk。

- **應用程式類型**：選取 [市集應用程式]。

- **要以 kiosk 模式執行的應用程式**：選擇 [新增市集應用程式]，然後從清單中選取應用程式。

    目前未列出任何應用程式？ 請使用[用戶端應用程式](apps-add.md)中的步驟新增一些應用程式。

    按一下 [確定] 以儲存您的變更。

- **Kiosk 瀏覽器設定**：這些設定會控制 kiosk 上的網頁瀏覽器應用程式。 請確定您從 Microsoft Store 取得 [Kiosk 瀏覽器應用程式](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP)、將其新增至 Intune 作為[用戶端應用程式](apps-add.md)，然後將應用程式指派給 kiosk 裝置。

  輸入下列設定：

  - **預設的首頁 URL**：輸入 kiosk 瀏覽器開啟或重新啟動時所顯示的預設 URL。 例如，輸入 `http://bing.com` 或 `http://www.contoso.com`。

  - **首頁按鈕**：[顯示] 或 [隱藏] kiosk 瀏覽器的首頁按鈕。 預設不會顯示此按鈕。

  - **導覽按鈕**：[顯示] 或 [隱藏] 向前和向後按鈕。 預設不會顯示導覽按鈕。

  - **結束工作階段按鈕**：[顯示] 或 [隱藏] 結束工作階段按鈕。 顯示時，使用者可選取按鈕，而應用程式會提示結束工作階段。 確認時，瀏覽器會清除所有瀏覽資料 (Cookie、快取等)，然後開啟預設 URL。 預設不會顯示此按鈕。

  - **在閒置時間後重新整理瀏覽器**：輸入閒置時間量 (1-1440 分鐘)，在該時間之後 kiosk 瀏覽器會以全新狀態重新啟動。 閒置時間是自使用者上次互動之後所經過的分鐘數。 根據預設，此值是空的或空白，這表示沒有任何閒置逾時。

  - **允許的網站**：使用此設定可允許開啟特定網站。 換句話說，使用此功能可在裝置上限制或防止網站。 例如，您可以允許開啟位於 `http://contoso.com*` 的所有網站。 預設會允許所有網站。

    若要允許特定網站，請上傳包含允許網站清單的 .csv 檔案。 如果您未新增 .csv 檔案，則會允許所有網站。 Intune 支援以 * (星號) 作為萬用字元。

  按一下 [確定] 以儲存您的變更。

## <a name="multi-app-kiosks"></a>多應用程式 kiosk

此模式下的應用程式可以在 [開始] 功能表中使用。 這些應用程式是使用者唯一能夠開啟的應用程式。

當您選擇多應用程式 kiosk 模式時，請輸入下列設定：

- **以 S 模式的 Windows 10 裝置為目標**：選擇 [是] 以允許 kiosk 設定檔中的市集應用程式和 AUMID 應用程式 (Win32 應用程式除外)。 選擇 [否] 以允許 kiosk 設定檔中的市集應用程式、Win32 應用程式和 AUMID 應用程式。 當您選擇 [否] 時，此 kiosk 設定檔不會部署到 S 模式裝置。

- **使用者登入類型**：您新增的應用程式會以您所輸入使用者帳戶身分執行。 選項包括：

  - **自動登入 (Windows 10 1803 版和更新版本)**：對外環境中的 kiosk 不需要使用者登入，其與來賓帳戶類似。 這項設定使用 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)。
  - **本機使用者帳戶**：[新增] 本機 (對裝置而言) 使用者帳戶。 您輸入的帳戶可用來登入 kiosk。
  - **Azure AD 使用者或群組 (Windows 10 1803 版和更新版本)**：選取 [新增] 以從清單中選擇 Azure AD 使用者或群組。 您可以選取多個使用者和群組。 選擇 [選取] 以儲存您的變更。
  - **HoloLens 訪客**：訪客帳戶是來賓帳戶，不需要任何使用者認證或驗證，如 [shared PC mode concepts](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts) (共用電腦模式概念) 中所述。

- **應用程式**：新增要在 kiosk 裝置上執行的應用程式。 請記住，您可以新增數個應用程式。

  - **新增市集應用程式**：從商務用 Microsoft Store 新增應用程式。 如果目前未列出任何應用程式，則您可以取得應用程式，然後[將其新增至 Intune](store-apps-windows.md)。 例如，您可以新增 Kiosk 瀏覽器、Excel、OneNote 等。

  - **新增 Win32 應用程式**：Win32 應用程式是傳統型應用程式，例如 Visual Studio Code 或 Google Chrome。 輸入下列內容：

    - **應用程式名稱**：必要。 輸入應用程式的名稱。
    - **本機路徑**：必要。 輸入可執行檔的路徑，例如 `C:\Program Files (x86)\Microsoft VS Code\Code.exe` 或 `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`。
    - **應用程式使用者模型識別碼 (AUMID)**：選擇性。 輸入 Win32 應用程式的應用程式使用者模型識別碼 (AUMID)。 此設定可決定桌面上磚的開始畫面版面配置。 若要取得此識別碼，請參閱 [find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (尋找已安裝應用程式的應用程式使用者模型識別碼)。
    - **磚大小**：必要。 針對應用程式磚大小，選擇 [小]、[中]、[寬] 或 [大]。
  
  - **依 AUMID 新增**：使用此選項可新增現成的 Windows 應用程式，例如 [記事本] 或 [小算盤]。 輸入下列內容： 

    - **應用程式名稱**：必要。 輸入應用程式的名稱。
    - **應用程式使用者模型識別碼 (AUMID)**：必要。 輸入 Windows 應用程式的應用程式使用者模型識別碼 (AUMID)。 若要取得此識別碼，請參閱 [find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (尋找已安裝應用程式的應用程式使用者模型識別碼)。
    - **磚大小**：必要。 針對應用程式磚大小，選擇 [小]、[中]、[寬] 或 [大]。

  > [!TIP]
  > 新增所有應用程式之後，您可以按一下並拖曳清單中的應用程式來變更顯示順序。  

  按一下 [確定] 以儲存您的變更。

- **Kiosk 瀏覽器設定**：這些設定會控制 kiosk 上的網頁瀏覽器應用程式。 請確定您使用[用戶端應用程式](apps-add.md)將網頁瀏覽器應用程式部署到 kiosk 裝置。

  輸入下列設定：

  - **預設的首頁 URL**：輸入 kiosk 瀏覽器開啟或重新啟動時所顯示的預設 URL。 例如，輸入 `http://bing.com` 或 `http://www.contoso.com`。

  - **首頁按鈕**：[顯示] 或 [隱藏] kiosk 瀏覽器的首頁按鈕。 預設不會顯示此按鈕。

  - **導覽按鈕**：[顯示] 或 [隱藏] 向前和向後按鈕。 預設不會顯示導覽按鈕。

  - **結束工作階段按鈕**：[顯示] 或 [隱藏] 結束工作階段按鈕。 顯示時，使用者可選取按鈕，而應用程式會提示結束工作階段。 確認時，瀏覽器會清除所有瀏覽資料 (Cookie、快取等)，然後開啟預設 URL。 預設不會顯示此按鈕。

  - **在閒置時間後重新整理瀏覽器**：輸入閒置時間量 (1-1440 分鐘)，在該時間之後 kiosk 瀏覽器會以全新狀態重新啟動。 閒置時間是自使用者上次互動之後所經過的分鐘數。 根據預設，此值是空的或空白，這表示沒有任何閒置逾時。

  - **允許的網站**：使用此設定可允許開啟特定網站。 換句話說，使用此功能可在裝置上限制或防止網站。 例如，您可以允許開啟位於 `contoso.com*` 的所有網站。 預設會允許所有網站。

    若要允許特定網站，請上傳包含允許網站清單的 .csv 檔案。 如果您未新增 .csv 檔案，則會允許所有網站。

  按一下 [確定] 以儲存您的變更。

- **使用其他開始畫面版面配置**：選擇 [是] 以輸入描述應用程式在 [開始] 功能表上如何顯示 (包括應用程式的順序) 的 XML 檔案。 如果您需要在 [開始] 功能表中有更多自訂項目，請使用此選項。 [自訂與匯出 [開始] 配置](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout)提供一些指引和範例 XML。

- **Windows 工作列**：選擇 [顯示] 或 [隱藏] 工作列。 預設不會顯示此工作列。

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

在 Windows Holographic for Business 裝置上，您可以設定這些裝置在單一應用程式 kiosk 模式或多應用程式 kiosk 模式中執行。 Windows Holographic for Business 不支援某些功能。

#### <a name="single-full-screen-app-kiosks"></a>單一全螢幕應用程式 Kiosk
當您選擇單一應用程式 kiosk 模式時，請輸入下列設定：

- **使用者登入類型**：選取 [本機使用者帳戶] 以輸入本機 (對裝置而言) 使用者帳戶，或與 kiosk 應用程式建立關聯的 Microsoft 帳戶 (MSA)。 Windows Holographic for Business 不支援 [自動登入] 使用者帳戶類型。

- **應用程式類型**：選取 [市集應用程式]。

- **要以 kiosk 模式執行的應用程式**：選擇 [新增市集應用程式]，然後從清單中選取應用程式。

    目前未列出任何應用程式？ 請使用[用戶端應用程式](apps-add.md)中的步驟新增一些應用程式。

    按一下 [確定] 以儲存您的變更。

#### <a name="multi-app-kiosks"></a>多應用程式 kiosk
此模式下的應用程式可以在 [開始] 功能表中使用。 這些應用程式是使用者唯一能夠開啟的應用程式。 當您選擇多應用程式 kiosk 模式時，請輸入下列設定：

- **以 S 模式的 Windows 10 裝置為目標**：選擇 [否]。 Windows Holographic for Business 不支援 S 模式。

- **使用者登入類型**：新增一或多個可使用所新增應用程式的使用者帳戶。 選項包括： 

  - **自動登入**：不支援 Windows Holographic for Business。
  - **本機使用者帳戶**：[新增] 本機 (對裝置而言) 使用者帳戶。 您輸入的帳戶可用來登入 kiosk。
  - **Azure AD 使用者或群組 (Windows 10 1803 版和更新版本)**：需要使用者認證才能登入裝置。 選取 [新增] 以從清單中選擇 Azure AD 使用者或群組。 您可以選取多個使用者和群組。 選擇 [選取] 以儲存您的變更。
  - **HoloLens 訪客**：訪客帳戶是來賓帳戶，不需要任何使用者認證或驗證，如 [shared PC mode concepts](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts) (共用電腦模式概念) 中所述。

- **應用程式**：新增要在 kiosk 裝置上執行的應用程式。 請記住，您可以新增數個應用程式。

  - **新增市集應用程式**：選取您使用[用戶端應用程式](apps-add.md)新增的現有應用程式。 如果目前未列出任何應用程式，則您可以取得應用程式，然後[將其新增至 Intune](store-apps-windows.md)。
  - **新增 Win32 應用程式**：不支援Windows Holographic for Business。
  - **依 AUMID 新增**：使用此選項可新增現成的 Windows 應用程式。 輸入下列內容： 

    - **應用程式名稱**：必要。 輸入應用程式的名稱。
    - **應用程式使用者模型識別碼 (AUMID)**：必要。 輸入 Windows 應用程式的應用程式使用者模型識別碼 (AUMID)。 若要取得此識別碼，請參閱 [find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (尋找已安裝應用程式的應用程式使用者模型識別碼)。
    - **磚大小**：必要。 針對應用程式磚大小，選擇 [小]、[中]、[寬] 或 [大]。

- **Kiosk 瀏覽器設定**：不支援Windows Holographic for Business。

- **使用其他開始畫面版面配置**：選擇 [是] 以輸入描述應用程式在 [開始] 功能表上如何顯示 (包括應用程式的順序) 的 XML 檔案。 如果您需要在 [開始] 功能表中有更多自訂項目，請使用此選項。 [自訂與匯出 [開始] 配置](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens)提供一些指引，並包含 Windows Holographic for Business 裝置的特定 XML 檔案。

- **Windows 工作列**：不支援 Windows Holographic for Business。



## <a name="next-steps"></a>接下來的步驟
[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
