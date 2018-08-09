---
title: Microsoft Intune 中 Windows 10 的 Kiosk 設定 - Azure | Microsoft Docs
description: 將您的 Windows 10 (及更新版本) 裝置設定為單一應用程式和多應用程式 kiosk，包括自訂 [開始] 功能表、新增應用程式、工作列及設定網頁瀏覽器。 此外，在 Microsoft Intune 中將 Windows Holographic for Business 裝置設定為多應用程式 kiosk。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6db58b1b1f19f789a2163f497c1f0da4c7c034a5
ms.sourcegitcommit: 5f6117b83f96f7d93dde3685c2ff2b67ae53740b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39481116"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Intune 中適用於 Windows 10 (和更新版本) 的 Kiosk 設定

Kiosk 設定檔可用來設定 Windows 10 裝置，以執行一個應用程式或執行多個應用程式。 當您建立 kiosk 設定檔時，還可以選擇是否顯示 [開始] 功能表、是否安裝網頁瀏覽器等。

## <a name="kiosk-settings"></a>Kiosk 設定

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入下列內容：

   - **名稱**：為新的設定檔輸入描述性名稱。
   - **描述**：輸入設定檔的描述。 這是選用項目，但建議使用。
   - **平台**：選取 [Windows 10 and later] \(Windows 10 及更新版本\)
   - **設定檔類型**：選取 [Kiosk (預覽)]
   
4. 選取 [Kiosk] > [新增]。
5. 為您的 Kiosk 輸入 [Kiosk 設定名稱]。 這個名稱可識別一組應用程式、這些應用程式在 [開始] 功能表中的配置，以及指派給此 Kiosk 設定的使用者。
6. 選取 [Kiosk 模式]。 [Kiosk 模式] 可識別原則支援的 Kiosk 模式類型。 這些選項包括：

    - **未設定** (預設)：原則不會啟用 kiosk 模式。
    - **單一全螢幕應用程式 Kiosk**：此設定可讓裝置以單一使用者帳戶執行，並將其鎖定到單一的通用 Windows 平台 (UWP) 應用程式。 因此當使用者登入時，會啟動特定的應用程式。 此模式也會限制使用者開啟新的應用程式或變更執行中的應用程式。
    - **多應用程式 Kiosk**：此設定檔可讓裝置執行多個通用 Windows 平台 (UWP) 應用程式或 Win32 應用程式。 您也可以將不同的應用程式指派給不同的使用者帳戶。 只有您新增的應用程式才可供使用者使用。 多應用程式 Kiosk (或固定用途裝置) 的優點是讓使用者只存取所需的應用程式，來為他們提供一個簡單明瞭的體驗。 此外，還可從其檢視中移除不需要的應用程式。

#### <a name="single-full-screen-app-kiosks"></a>單一全螢幕應用程式 Kiosk
輸入下列設定：

- **通用 Windows 平台 (UWP) 應用程式識別碼**：輸入 Kiosk 應用程式的 [應用程式使用者模型識別碼 (AUMID)]。 或選取使用[行動應用程式](apps-add.md)新增的現有受控應用程式。

    請參閱[尋找已安裝應用程式的應用程式使用者模型識別碼](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)。

- **使用者帳戶類型**：選項包括：

  - **自動登入**：針對在面對大眾的環境中且已啟用自動登入功能的 Kiosk，應該使用權限最低 (例如本機標準使用者帳戶) 的使用者。 若要設定 Azure Active Directory (AD) 帳戶以使用 kiosk 模式，請使用 `AzureAD\user@contoso.com` 格式。
  - **本機使用者帳戶**：輸入與 Kiosk 應用程式建立關聯的本機 (對裝置而言) 使用者帳戶或 Azure AD 帳戶登入。 針對已加入 Azure AD 網域的帳戶，請使用 `domain\username@tenant.org` 格式來輸入帳戶。

#### <a name="multi-app-kiosks"></a>多應用程式 kiosk
此模式下的應用程式可以在 [開始] 功能表中使用。 這些應用程式是使用者唯一能夠開啟的應用程式。 

[多應用程式 kiosk](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune) 使用會列出所允許應用程式及其他設定的 kiosk 設定。

輸入下列設定：

- **新增 Win32 應用程式**：Win32 應用程式是傳統型應用程式。 輸入 [應用程式名稱] 以及 [識別碼]。 在裝置方面，[識別碼] 是可執行檔的完整路徑名稱。
- **新增受控應用程式**：選取使用 [Intune 中的行動應用程式](apps-add.md)新增的現有受控應用程式。
- **依 AUMID 新增應用程式**：輸入[應用程式的 AUMID](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (UWP 應用程式)。
- **工作列**：選擇是要 [啟用] (顯示) 工作列，還是要讓它在 kiosk 上保持 [未設定] (隱藏) 狀態。
- **[開始] 功能表配置**：輸入描述應用程式在 [開始] 功能表上如何顯示 (包括應用程式的順序) 的 XML 檔案。 [自訂與匯出 [開始] 配置](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout)提供一些指引和範例 XML。

  [建立可執行多個應用程式的 Windows 10 kiosk](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file) 提供有關使用及建立 XML 檔案的更多詳細資料。

- **使用者帳戶類型**：新增一或多個能夠使用您新增之應用程式的使用者帳戶。 當該帳戶登入時，只有設定中所定義的應用程式可供使用。 帳戶可以是與 Kiosk 應用程式建立關聯的裝置本機帳戶或 Azure AD 帳戶登入。

    針對在面對大眾的環境中且已啟用自動登入功能的 Kiosk，應該使用權限最低 (例如本機標準使用者帳戶) 的使用者類型。 若要設定 Azure Active Directory (AD) 帳戶以使用 kiosk 模式，請使用 `domain\user@tenant.com` 格式。

## <a name="kiosk-web-browser-settings"></a>Kiosk 網頁瀏覽器設定

這些設定會控制 Kiosk 上的網頁瀏覽器應用程式。 請確定您已使用[行動應用程式](apps-add.md)將網頁瀏覽器應用程式部署到 Kiosk 裝置。

1. 輸入下列設定：

    - **預設的首頁 URL**：輸入瀏覽器開啟或重新啟動時，Kiosk 瀏覽器將開啟的預設 URL。

    - **首頁按鈕**：顯示 ([允許]) 或隱藏 ([未設定]) kiosk 瀏覽器的首頁按鈕。 根據預設，未設定該按鈕。

    - **導覽按鈕**：顯示 ([允許]) 或隱藏 ([未設定]) 向前和向後按鈕。 根據預設，未設定這些導覽按鈕。

    - **結束工作階段按鈕**：顯示 ([允許]) 或隱藏 ([未設定]) 結束工作階段按鈕。 顯示時，使用者可選取按鈕，而應用程式會提示結束工作階段。 確認時，瀏覽器會清除所有瀏覽資料 (Cookie、快取等)，並巡覽回預設 URL。 根據預設，未設定該按鈕。 

    - **使用者超出閒置時間限制時重新整理瀏覽器**：輸入工作階段閒置時間量 (分鐘)，在該時間之後 Kiosk 瀏覽器會以全新狀態重新啟動。 值為整數的 1-1440 分鐘。 根據預設，此值是空的或空白，這表示沒有閒置逾時。

    - **封鎖的網站**：封鎖的網站 URL (支援萬用字元) 清單。 使用此設定可防止瀏覽器開啟特定網站。 您也可以 [匯入] 包含清單的 .csv 檔案。 或者，建立包含您所新增之網站的 .csv 檔案 ([匯出])。

    - **網站例外狀況**：封鎖的網站 URL (支援萬用字元) 的例外狀況清單。 使用此設定可允許瀏覽器開啟特定網站。 這些例外狀況是封鎖的 URL 的子集。 如果 URL 位於封鎖的網站清單和網站例外狀況清單中，則例外狀況會生效。

    您也可以 [匯入] 包含清單的 .csv 檔案。 或者，建立包含您所新增之網站的 .csv 檔案 ([匯出])。

2. 按一下 [確定] 以儲存您的變更。

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

在 Windows Holographic for Business 裝置上，您可以設定這些裝置在單一應用程式 kiosk 模式或多應用程式 kiosk 模式中執行。 

#### <a name="single-full-screen-app-kiosks"></a>單一全螢幕應用程式 Kiosk
輸入下列設定：

- **通用 Windows 平台 (UWP) 應用程式識別碼**：輸入 Kiosk 應用程式的 [應用程式使用者模型識別碼 (AUMID)]。 或選取使用[行動應用程式](apps-add.md)新增的現有受控應用程式。

    請參閱 [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (尋找已安裝應用程式的應用程式使用者模型識別碼) 以取得識別碼。

- **使用者帳戶類型**：選取 [本機使用者帳戶] 以輸入本機 (對裝置而言) 使用者帳戶，或與 kiosk 應用程式相關聯的 Microsoft 帳戶 (MSA) 帳戶登入。 Windows Holographic for Business 不支援 [自動登入] 使用者帳戶類型。

#### <a name="multi-app-kiosks"></a>多應用程式 kiosk
此模式下的應用程式可以在 [開始] 功能表中使用。 這些應用程式是使用者唯一能夠開啟的應用程式。

輸入下列設定：

- **新增受控應用程式**：選取使用 [Intune 中的行動應用程式](apps-add.md)新增的現有受控應用程式。
- **依 AUMID 新增應用程式**：輸入[應用程式的 AUMID](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (UWP 應用程式)。
- **[開始] 功能表配置**：輸入描述應用程式在 [開始] 功能表上如何顯示 (包括應用程式的順序) 的 XML 檔案。 [自訂與匯出 [開始] 配置](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens)提供一些指引，並包含 Windows Holographic for Business 裝置的特定 XML 檔案。
- **使用者帳戶類型**：新增一或多個能夠使用您新增之應用程式的使用者帳戶。 支援的選項包括： 
  - **HoloLens 訪客**：訪客帳戶是來賓帳戶，不需要任何使用者認證或驗證，如 [shared PC mode concepts](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts) (共用電腦模式概念) 中所述。
  - **Azure AD 使用者**：需要使用者認證才能登入裝置。 請使用 `domain\user@tenant.com` 格式。
  - **本機使用者帳戶**：需要使用者認證才能登入裝置。 

當該帳戶登入時，只有設定中所定義的應用程式可供使用。

## <a name="next-steps"></a>接下來的步驟
[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
