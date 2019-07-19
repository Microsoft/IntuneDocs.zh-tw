---
title: 使用 Intune 管理適用於 iOS 和 Android 的 Microsoft Edge
titleSuffix: ''
description: 使用 Microsoft Edge 的 Intune 應用程式保護原則，以確保一律使用就地保護公司網站的存取。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bc18ba2210719cbebe77cd5b37024be4bb7b0d3e
ms.sourcegitcommit: a01f0f3070932e3be44a4f545d4de11d715381ea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2019
ms.locfileid: "68287225"
---
# <a name="manage-web-access-by-using-microsoft-edge-with-microsoft-intune"></a>透過搭配 Microsoft Intune 使用 Microsoft Edge 來管理 Web 存取

搭配 Microsoft Edge 使用 Intune 應用程式保護原則，可協助確保一律會使用就地保護措施來存取公司網站。 提供以下依據 Intune 原則啟用的 Microsoft Edge 企業功能：

- **雙重識別。** 使用者可以新增工作帳戶與個人帳戶以進行瀏覽。 系統會完整區隔兩個身分識別，類似於 Office 365 和 Outlook 中的架構與體驗。 Intune 系統管理員可以在公司帳戶內，針對受保護的瀏覽體驗設定所需原則。
- **Intune 應用程式保護原則整合。** 因為 Microsoft Edge 已與 Intune SDK 整合，所以您可以透過應用程式保護原則來防止資料遺失。 這些功能包括控制剪下、複製與貼上、防止螢幕擷取，以及確保使用者選取的連結只在其他受管理用程式中開啟。
- **Azure 應用程式 Proxy 整合。** 您可以控制針對軟體即服務 (SaaS) 應用程式和 Web 應用程式的存取。 這能協助確保瀏覽器型應用程式都只會在安全的 Microsoft Edge 瀏覽器中執行，無論使用者是從公司網路連線或從網際網路連線。
- **應用程式設定。** 您可以利用應用程式組態設定來加強組織的安全性狀態，並為使用者設定容易使用的功能。 例如，您可以定義書籤、首頁捷徑、允許或封鎖的網站，以及 Azure Active Directory (Azure AD) 應用程式 Proxy。

適用於 Microsoft Edge 的 Microsoft Intune 保護原則可協助保護您的組織資料和資源。 使用這些原則來搭配 Microsoft Edge 能確保公司資源無論是在原生安裝的應用程式內，或透過網頁瀏覽器存取時，都會受到保護。

## <a name="getting-started"></a>開始使用

您和您的終端使用者可以從公用應用程式存放區下載 Microsoft Edge，以便用於您的組織中。 瀏覽器原則的作業系統需求為下列其中之一：
- Android 4 及更新版本
- iOS 8.0 和更新版本

## <a name="application-protection-policies-for-microsoft-edge"></a>Microsoft Edge 的應用程式保護原則

因為 Microsoft Edge 已與 Intune SDK 整合，所以您可以將應用程式保護原則套用至它們上方。

您可以套用這些設定至：
- 向 Intune 註冊的裝置。
- 向其他行動裝置管理產品註冊的裝置。
- 非受控裝置。

如果 Microsoft Edge 未以 Intune 原則設定目標，使用者便無法使用它來存取來自其他受 Intune 管理的應用程式 (例如 Office 應用程式) 的資料。 

## <a name="conditional-access-for-microsoft-edge"></a>Microsoft Edge 的條件式存取

您可以利用 Azure AD 條件式存取將使用者重新導向，讓他們只能透過 Microsoft Edge 來存取公司內容。 這會將行動瀏覽器針對已連線至 Azure AD 之 Web 應用程式的存取方式，限制為被原則保護的 Microsoft Edge。 這會封鎖來自任何其他未被保護之瀏覽器的存取，例如 Safari 或 Chrome。 您可以將條件式存取套用至 Azure 資源，例如 Exchange Online 和 SharePoint Online、Microsoft 365 系統管理中心，甚至是已透過 [Azure AD 應用程式 Proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) \(部分機器翻譯\) 對外部使用者公開的內部部署網站。

若要限制已連線至 Azure AD 的 Web 應用程式在 iOS 和 Android 上只能使用 Microsoft Edge：
1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在 Intune 節點下，選取 [條件式存取]   > [新原則]  。
3. 選取刀鋒視窗之 [存取控制]  區段中的 [授與]  。
4. 選取 [需要經過核准的用戶端應用程式]  。
5. 選擇 [授與]  刀鋒視窗上的 [選取]  。 此原則必須指派給您只想要讓 Intune Managed Browser 應用程式存取的雲端應用程式。

    ![條件式存取原則 - [授與] 的螢幕擷取畫面](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. 在 [指派] 區段中，選取 [條件]   > [用戶端應用程式]  。 [用戶端應用程式]  刀鋒視窗隨即顯示。
7. 在 [設定]  下，選取 [是]  來將原則套用至特定用戶端應用程式。
8. 確認已選取 **Browser** 作為用戶端應用程式。

    ![條件式存取原則 - [選取用戶端應用程式] 的螢幕擷取畫面](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > 如果您想要限制哪些原生應用程式 (非瀏覽器應用程式) 可以存取這些雲端應用程式，則也可以選取 [行動裝置 App 及桌面用戶端]  。

9. 在 [指派]  區段中，選取 [使用者和群組]  ，然後選擇您要指派此原則的使用者或群組。

    > [!NOTE]
    > 您也必須使用 Intune 應用程式防護原則瞄準使用者，才能讓使用者接收到應用程式設定原則。 如需建立 Intune 應用程式防護原則詳細資訊，請參閱[什麼是應用程式防護原則？](app-protection-policy.md)。

10. 在 [指派]  區段中，選取 [雲端應用程式]  選擇要使用此原則保護的應用程式。

設定上述原則之後，系統會強制使用者使用 Microsoft Edge 來存取您使用此原則保護、已連線至 Azure AD 的 Web 應用程式。 在此情況下，如果使用者嘗試使用非受控瀏覽器，便會收到他們必須改為使用 Microsoft Edge 的訊息。

> [!TIP]
> 條件式存取是 Azure AD 技術。 從 Intune 存取之條件式存取節點與從 Azure AD 存取的節點相同。

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>在被原則保護的瀏覽器中針對已連線至 Azure AD 的 Web 應用程式使用單一登入

iOS 和 Android 上的 Microsoft Edge 可以針對所有已連線至 Azure AD 的 Web 應用程式 (SaaS 和內部部署) 利用單一登入 (SSO)。 SSO 可讓使用者透過 Microsoft Edge 存取已連線至 Azure AD 的 Web 應用程式，而不必重新輸入其認證。

SSO 要求裝置必須註冊 iOS 裝置的 Microsoft Authenticator 應用程式或 Android 上 Intune 公司入口網站應用程式。 當使用者具備上述其中一項時，系統會在他們在被原則保護的瀏覽器中移至已連線至 Azure AD 的 Web 應用程式時通知他們註冊其裝置。 (這只會在其裝置尚未註冊時發生。)使用 Intune 所管理的使用者帳戶註冊裝置之後，該帳戶將會針對已連線至 Azure AD 的 Web 應用程式啟用 SSO。

> [!NOTE]
> 裝置註冊是使用 Azure AD 服務的簡單簽入。 它不需要完整裝置註冊，且不會在該裝置上授與 IT 人員額外的權限。

## <a name="create-a-protected-browser-app-configuration"></a>建立受保護的瀏覽器應用程式設定

如要套用應用程式設定，使用者被保護的瀏覽器或裝置上的另一個應用程式必須已由 [Intune 應用程式保護原則](app-protection-policy.md)所管理。

針對 Microsoft Edge 建立應用程式設定：

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [用戶端應用程式]   > [應用程式設定原則]   > [新增]  。
3. 在 [新增設定原則]  刀鋒視窗上，輸入應用程式組態設定的 [名稱]  和選擇性 [描述]  。
4. 針對 [裝置註冊]  類型請選擇 [受管理的應用程式]  。
5. 選擇 [選取必要的應用程式]  。 然後在 [目標應用程式]  刀鋒視窗上，選擇適用於 iOS、Adroid 或兩者的 [Managed Browser]  或 [Edge]  。
6. 選取 [確定]  以返回 [新增設定原則]  刀鋒視窗。
7. 選取 [組態設定]  。 在 [設定]  刀鋒視窗上，您可以定義金鑰和值組來為 Microsoft Edge 提供設定。 請使用本文稍後的各個章節，來了解您可以定義的不同金鑰和值組。

    > [!NOTE]
    > Microsoft Edge 使用與 Managed Browser 相同的金鑰和值組。 

8. 完成之後，請選取 [確定]  。
9. 在 [新增設定原則]  刀鋒視窗上，選擇 [新增]  。<br>
    會隨即建立新設定，然後顯示在 [應用程式設定]  刀鋒視窗上。

## <a name="assign-the-configuration-settings-you-created"></a>指派您建立的組態設定 

您可以將設定指派給 Azure AD 中的使用者群組。 如果該使用者已經安裝目標受保護的瀏覽器應用程式，則此應用程式是由您指定的設定管理。

1. 在 Intune 行動應用程式管理儀表板的 [用戶端應用程式]  刀鋒視窗上，選取 [應用程式設定原則]  。
2. 從應用程式設定清單，選取您要指派的設定。
3. 在下一個刀鋒視窗上，選取 [指派]  。
4. 在 [指派]  刀鋒視窗上，選取您要指派應用程式設定的 Azure AD 群組，然後選取 [確定]  。

## <a name="direct-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>將使用者導向 Microsoft Edge，而不是 Intune Managed Browser 

Intune Managed Browser 和 Microsoft Edge 都可以用來作為被原則保護的瀏覽器。 為了確保您的使用者會被引導為使用正確的瀏覽器應用程式，請用下列組態設定來設定所有由 Intune 所管理之應用程式 (例如 Outlook、OneDrive 與 SharePoint) 的目標：

|    金鑰    |    值    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    值 `true` 將會引導您的使用者下載並使用 Microsoft Edge。<br>值 `false` 將會允許您的使用者使用 Intune Managed Browser。    |

如果**未**設定此應用程式設定值，則下列邏輯會定義哪一個瀏覽器將用來開啟公司連結。

在 Android 上：
- 如果使用者已在其裝置中下載 Intune Managed Browser 和 Microsoft Edge，則會開啟 Intune Managed Browser。 
- 如果裝置上僅下載 Microsoft Edge 且已經透過 Intune 原則設定為目標應用程式，則會開啟 Microsoft Edge。
- 如果裝置上只有 Managed Browser 且已經透過 Intune 原則設定為目標應用程式，則會啟動 Managed Browser。

在 iOS 上，針對已整合 Intune SDK for iOS v. 9.0.9+ 的應用程式：
- 如果裝置上同時有 Managed Browser 和 Microsoft Edge，則會啟動 Intune Managed Browser。  
- 如果裝置上只有 Microsoft Edge 且已經透過 Intune 原則設定為目標應用程式，則會啟動 Microsoft Edge。
- 如果裝置上只有 Managed Browser 且已經透過 Intune 原則設定為目標應用程式，則會啟動 Managed Browser。

## <a name="configure-application-proxy-settings-for-microsoft-edge"></a>針對 Microsoft Edge 設定應用程式 Proxy 設定

Microsoft Edge 及 [Azure AD 應用程式 Proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) \(部分機器翻譯\) 可以一起使用，來讓使用者在他們的行動裝置上存取內部網路網站。 

以下是一些 Azure AD 應用程式 Proxy 能夠提供的案例範例： 

- 使用者正在使用受 Intune 保護的 Outlook 行動應用程式。 然後他們按一下電子郵件中的內部網路網站連結，Microsoft Edge 則辨識此內部網路網站已透過應用程式 Proxy 向使用者公開。 使用者會透過應用程式 Proxy 自動進行路由傳送，在到達內部網路網站之前，使用任何適用的多重要素驗證和條件式存取來進行驗證。 使用者現在能夠存取內部網路網站 (甚至是在其行動裝置上)，且 Outlook 中的連結會如預期運作。
- 使用者在其 iOS 或 Android 裝置上開啟 Microsoft Edge。 如果 Microsoft Edge 是被 Intune 保護，且已啟用應用程式 Proxy，則使用者可以使用他們慣用的內部 URL 來移至內部網路網站。 Microsoft Edge 會辨識此內部網路網站是透過應用程式 Proxy 向使用者公開。 系統會自動透過應用程式 Proxy 路由使用者，以在抵達內部網路網站之前進行驗證。 

### <a name="before-you-start"></a>開始之前

- 透過 Azure AD 應用程式 Proxy 設定內部應用程式。
  - 若要設定應用程式 Proxy 並發佈應用程式，請參閱[安裝程式文件](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)。
- Microsoft Edge 應用程式必須已指派 [Intune 應用程式保護原則](app-protection-policy.md)。

> [!NOTE]
> 更新的應用程式 Proxy 重新導向資料，最多可能需要 24 小時才會在 Managed Browser 和 Microsoft Edge 中生效。

#### <a name="step-1-enable-automatic-redirection-to-microsoft-edge-from-outlook"></a>步驟 1：從 Outlook 啟用針對 Microsoft Edge 的自動重新導向
搭配能啟用 [使用原則受控瀏覽器共用 Web 內容]  設定的應用程式保護原則來設定 Outlook。

![應用程式保護原則 - [使用原則受控瀏覽器共用 Web 內容] 的螢幕擷取畫面](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>步驟 2：設定應用程式組態設定，以啟用應用程式 Proxy
使用下列金鑰/值組將 Microsoft Edge 設定為目標，以針對 Microsoft Edge 啟用應用程式 Proxy：

|    金鑰    |    值    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

如需如何前後使用 Microsoft Edge 與 Azure AD 應用程式 Proxy 來緊密 (且被保護) 地存取內部部署 Web 應用程式的詳細資訊，請參閱[建議搭配使用：Intune 和 Azure Active Directory 合作以改善使用者存取](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) \(英文\)。 此部落格文章參考 Intune Managed Browser，但內容也適用於 Microsoft Edge。

## <a name="configure-a-homepage-shortcut-for-microsoft-edge"></a>設定適用於 Microsoft Edge 的首頁捷徑

此設定允許您設定適用於 Microsoft Edge 的首頁捷徑。 當使用者在 Microsoft Edge 中開啟新索引標籤時，您設定的首頁捷徑會成為搜尋列下方第一個圖示。 使用者在其受控內容中無法編輯或刪除這個捷徑。 首頁捷徑會顯示您組織的名稱，以區分該捷徑。 

使用下列金鑰/值組來設定首頁捷徑：

|    金鑰    |    值    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    指定有效的 URL。 基於安全性考量，會封鎖不正確的 URL。<br>**範例：**  <`https://www.bing.com`>
    |

## <a name="configure-managed-bookmarks-for-microsoft-edge"></a>設定 Microsoft Edge 的受控書籤

為了方便存取，您可以設定想讓使用者在使用 Microsoft Edge 時的可用書籤。 

以下是一些詳細資料：

- 使用者在使用 Microsoft Edge 的企業模式時，才會看到這些書籤。 
- 使用者無法刪除或修改這些書籤。
- 這些書籤會顯示在清單頂端。 使用者所建立的書籤都會顯示在這些書籤下方。
- 如果您已啟用應用程式 Proxy 重新導向，即可使用應用程式 Proxy Web 應用程式的內部或外部 URL 來新增這些應用程式 Proxy Web 應用程式。

您可以使用下列金鑰/值組來設定受控書籤：

|    金鑰    |    值    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    此設定值是書籤清單。 每個書籤都是由書籤標題和書籤 URL 所組成。 請使用 `|` 字元來分隔標題和 URL。      範例：<br>`Microsoft Bing|https://www.bing.com`<br>若要設定多個書籤，請以雙引號字元 `||` 分隔每組配對。<p>範例：<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="display-myapps-within-microsoft-edge-bookmarks"></a>在 Microsoft Edge 書籤內顯示 MyApps

根據預設，您的使用者將會看見在 Microsoft Edge 書籤的資料夾內針對他們所設定的 MyApps 網站。 該資料夾將會以您組織的名稱來標示。

|    金鑰    |    值    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **True** 會在 Microsoft Edge 書籤中顯示 MyApps。<p>**False** 會在 Microsoft Edge 中隱藏 MyApps。    |

## <a name="specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>針對 Microsoft Edge 指定允許或封鎖的網站清單
您可以使用應用程式設定來定義當使用者使用他們的工作設定檔時，可以存取哪些網站。 如果您使用允許清單，您的使用者將只能存取您明確列出的網站。 如果您使用封鎖的清單，您的使用者將能夠存取您明確封鎖的網站以外的所有網站。 您只應該強制允許或封鎖清單，而不應該同時使用兩者。 如果您同時強制兩者，系統只會採用允許清單。  

請使用下列金鑰/值組來針對 Microsoft Edge 設定允許或封鎖的網站清單。 

|    金鑰    |    值    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    從下列選項進行選擇：<p>1.指定允許的 URL (僅允許這些 URL；不能存取其他站台)：<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2.指定封鎖的 URL (可以存取所有其他網站)：<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    金鑰的相對應值為 URL 清單。 您可以以單一值的方式，輸入想要允許或封鎖的所有 URL，並使用垂直線 `|` 字元分隔。<br>**範例：**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>適用於允許和封鎖網站清單的 URL 格式 
您可以使用各種不同 URL 格式來建置您的允許/封鎖網站清單。 下表會詳細說明這些允許的模式。 在開始之前有一些注意事項： 
- 確定您在清單中輸入 UTL 時，已在所有 URL 中加上 **http** 或 **https** 的前置詞。
- 您可以根據下列許可模式清單中的規則，來使用萬用字元符號 (\*)。
- 萬用字元只能比對主機名稱的整個元件 (以句點分隔) 或路徑的整個部分 (以正斜線分隔)。 例如，**不**支援 `http://*contoso.com`。
- 您可以在位址中指定連接埠號碼。 如不指定連接埠號碼，會使用下列值：
  - 針對 http 使用連接埠 80
  - 針對 https 使用連接埠 443
- **不**支援對連接埠號碼使用萬用字元。 例如，不支援 `http://www.contoso.com:*` 和 `http://www.contoso.com:*/`。 

    |    URL    |    詳細資料    |    相符項    |    不符合    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    比對單一頁面    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    比對單一頁面    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/*;`   |    比對所有以 `www.contoso.com` 開頭的 URL    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    比對 `contoso.com` 下的所有子網域    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`    |    `http://*contoso.com/*`    |    比對所有結尾為 `contoso.com/` 的子網域    |    `http://news-contoso.com`<br>`http://news-contoso.com.com/daily`    |    `http://news-contoso.host.com`    |
    `http://www.contoso.com/images`    |    比對單一資料夾    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    使用連接埠號碼來比對單一頁面    |    `http://www.contoso.com:80`    |         |
    |    `https://www.contoso.com`    |    比對單一且安全的頁面    |    `https://www.contoso.com`    |    `http://www.contoso.com`    |
    |    `http://www.contoso.com/images/*`    |    符合單一資料夾及所有子資料夾    |    `www.contoso.com/images/dogs`<br>`www.contoso.com/images/cats`    |    `www.contoso.com/videos`    |
  
- 以下是一些您無法指定的輸入範例：
  - `*.com`
  - `*.contoso/*`
  - `www.contoso.com/*images`
  - `www.contoso.com/*images*pigs`
  - `www.contoso.com/page*`
  - IP 位址
  - `https://*`
  - `http://*`
  - `https://*contoso.com`
  - `http://www.contoso.com:*`
  - `http://www.contoso.com: /*`

## <a name="define-behavior-when-users-try-to-access-a-blocked-site"></a>定義當使用者嘗試存取被封鎖網站時的行為

由於 Microsoft Edge 中已內建雙重身分識別模型，您可以為使用者啟用 Intune Managed Browser 無法達成且更有彈性的體驗。 當使用者在 Microsoft Edge 中造訪被封鎖的網站時，您可以提示他們在其個人內容 (而非工作內容) 中開啟該連結。 這可讓他們持續被保護，同時也能確保企業資源的安全。 例如，如果使用者在 Outlook 中收到某篇新聞文章的連結，他們可以在其個人內容或 InPrivate 索引標籤中開啟該連結。其工作內容並不允許新聞網站。 根據預設，會允許這些轉換。

使用下列金鑰/值組來設定是否允許這些軟轉換：

|    金鑰    |    值    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **True** 會允許 Microsoft Edge 將使用者轉換至其個人內容以開啟被封鎖的網站。<p>**Block** 會防止 Microsoft Edge 轉換使用者。 使用者只會看見說明他們嘗試存取的網站已被封鎖的訊息。    |

## <a name="use-microsoft-edge-on-ios-to-access-managed-app-logs"></a>在 iOS 上使用 Microsoft Edge 來存取受控應用程式記錄檔 

在其 iOS 裝置上安裝 Microsoft Edge 的使用者，可以檢視由 Microsoft 所發行之所有應用程式的管理狀態。 他們可以傳送記錄檔用於疑難排解其受管理的 iOS 應用程式。 以下說明做法：
1. 在您的 iOS 裝置上開啟 Microsoft Edge。
2. 網址方塊中的類型 `about:intunehelp`。 
3. Microsoft Edge 會啟動疑難排解模式。

如需儲存在應用程式記錄中的設定清單，請參閱[在 Managed Browser 中檢閱應用程式保護記錄](app-protection-policy-settings-log.md)。

若要了解如何在 Android 裝置上檢視記錄檔，請參閱[透過電子郵件將記錄檔傳送給 IT 系統管理員](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android)。 

## <a name="security-and-privacy-for-microsoft-edge"></a>Microsoft Edge 的安全性和隱私權

以下是 Microsoft Edge 的其他安全性和隱私權考量：

- Microsoft Edge 不會使用使用者在其裝置上針對原生瀏覽器所設定的設定，因為 Microsoft Edge 並無法存取這些設定。
- 您可以在與 Microsoft Edge 相關聯的應用程式保護原則中設定 [需要簡單的 PIN 碼才能存取]  或 [需要公司認證才能存取]  選項。 如果使用者選取驗證頁面上的說明連結，他們便可以瀏覽任何網際網路網站，無論那些網站是否被加入原則中的已封鎖清單。
- Microsoft Edge 可以在直接存取網站時，只封鎖網站的存取。 它不會在使用者使用中繼服務 (例如翻譯服務) 來存取網站時封鎖存取。
- 若要允許驗證並存取 Intune 文件，請從允許或封鎖清單設定中排除 * **.microsoft.com**。 它一律會被允許。
- 使用者可以關閉資料收集。 Microsoft 會自動收集有關 Managed Browser 效能和使用的匿名資料，以改善 Microsoft 產品和服務。 使用者可以在裝置上使用 **[使用方式資料]** 設定以關閉資料收集。 您無法控制此資料的收集。 在 iOS 裝置上，使用者將無法開啟具有過期或未受信任憑證的網站。

## <a name="next-steps"></a>後續步驟

- [什麼是應用程式保護原則？](app-protection-policy.md) 
