---
title: 使用 Microsoft Edge 與 Microsoft Intune 管理 Web 存取
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
ms.openlocfilehash: 1ad8a3298a801b07e021b84bd5eea9c91f01f1a2
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044889"
---
# <a name="manage-web-access-using-microsoft-edge-with-microsoft-intune"></a>使用 Microsoft Edge 與 Microsoft Intune 管理 Web 存取

使用 Microsoft Edge 的 Intune 應用程式保護原則，可以確保一律使用就地保護公司網站的存取。 提供以下依據 Intune 原則啟用的 Microsoft Edge 企業功能。 這些企業功能包括：

1.  **雙重識別** - 使用者可以新增工作帳戶與個人帳戶以進行瀏覽。 系統會完整區隔兩個身分識別，類似於 Office 365 和 Outlook 中的架構與體驗。 Intune 系統管理員可以在工作帳戶內，針對受保護的瀏覽體驗設定所需原則。
2.  **Intune 應用程式保護原則整合** – 因為 Microsoft Edge 與 Intune SDK 整合，所以您可以設定應用程式保護原則的目標，以確保資料外洩防護。 這些功能包括控制剪下、複製與貼上、防止螢幕擷取，以及確保使用者選取的連結只在其他受管理用程式中開啟。
3.  **Azure 應用程式 Proxy 整合** – 您可以控制對 SaaS 應用程式和 Web 應用程式的存取，協助確保無論使用者是從公司網路連線或從網際網路連線，瀏覽器型應用程式都只會在安全的 Microsoft Edge 瀏覽器中執行。
4.  **應用程式設定** – 您可以利用應用程式組態設定，來加強組織的安全性狀態，並為終端使用者設定容易使用的功能。 例如，您可以定義書籤、首頁捷徑、允許/封鎖的網站、Azure 應用程式 Proxy 和更多功能。
適用於 Microsoft Edge 的 Microsoft Intune 保護原則可協助保護您的組織資料和資源。 使用這些原則來搭配 Microsoft Edge 能確保公司資源無論是在原生安裝的應用程式內，或透過網頁瀏覽器存取時，都會受到保護。

## <a name="getting-started"></a>開始使用

您和您的終端使用者可以從公用應用程式存放區下載 Microsoft Edge，以便用於您的組織中。 瀏覽器原則的作業系統需求：
- Android 4 及更新版本，或
- iOS 8.0 和更新版本

## <a name="application-protection-policies-for-microsoft-edge"></a>Microsoft Edge 的應用程式保護原則

因為 Microsoft Edge 與 Intune SDK 整合，所以您可以將應用程式保護原則套用至這些應用程式，包括：
- 控制剪下、複製和貼上的運用。
- 防止擷取螢幕畫面。
- 確保只能在受控應用程式和瀏覽器中開啟公司連結。

如需詳細資料，請參閱＜什麼是應用程式保護原則？＞
您可以套用這些設定至：
- 向 Intune 註冊的裝置
- 向其他 MDM 產品註冊
- 未受管理的裝置

如果 Microsoft Edge 未以 Intune 原則設定目標，則使用者無法使用它從其他受 Intune 管理的應用程式 (例如 Office 應用程式) 存取資料。 

## <a name="conditional-access-for-microsoft-edge"></a>Microsoft Edge 的條件式存取

您可以利用 Azure AD 條件式存取將使用者重新導向為只能透過 Microsoft Edge 來存取公司內容。 這會將行動瀏覽器對 Azure AD 已連線 Web 應用程式的存取限制為受原則保護的 Microsoft Edge，且會封鎖從任何其他未受保護的瀏覽器 (如 Safari 或 Chrome) 進行存取。 條件式存取可以套用至 Azure 資源，例如 Exchange Online 和 SharePoint Online、Microsoft 365 系統管理中心，甚至是已透過 [Azure AD 應用程式 Proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) \(部分機器翻譯\) 對外部使用者公開的內部部署網站。

若要限制 Azure AD 已連線 Web 應用程式在 iOS 和 Android 上使用 Microsoft Edge，請遵循下列步驟：
1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在 Intune 節點下，選取 [條件式存取]   > [新原則]  。
3. 接下來，選取刀鋒視窗之 [存取控制]  區段中的 [授與]  。
4. 按一下 [需要經過核准的用戶端應用程式]  。
5. 按一下 [授與]  刀鋒視窗上的 [選取]  。 此原則必須指派給您只想要讓 Intune Managed Browser 應用程式存取的雲端應用程式。

    ![條件式存取原則 - 授與](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. 在 [指派] 區段中，選取 [條件] > [用戶端應用程式]。 隨即顯示 [用戶端應用程式] 刀鋒視窗。
7. 按一下 [設定] 下的 [是]，將原則套用至特定用戶端應用程式。
8. 確認已選取 [瀏覽器] 作為用戶端應用程式。

    ![條件式存取原則 - 選取用戶端應用程式](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > 如果您想要限制哪些原生應用程式 (非瀏覽器應用程式) 可以存取這些雲端應用程式，則也可以選取 [行動裝置 App 及桌面用戶端]  。

9. 在 [指派]  區段中，選取 [使用者和群組]  ，然後選擇您想要指派此原則的使用者或群組。

    > [!NOTE]
    > 您也必須使用 Intune 應用程式防護原則瞄準使用者，才能讓使用者接收到應用程式設定原則。 如需建立 Intune 應用程式防護原則詳細資訊，請參閱[什麼是應用程式防護原則？](app-protection-policy.md)

10. 在 [指派]  區段中，選取 [雲端應用程式]  選擇要使用此原則保護的應用程式。

設定上述原則之後，會強制使用者使用 Microsoft Edge 存取您使用此原則保護的 Azure AD 已連線 Web 應用程式。 在此情況下，如果使用者嘗試使用非受控瀏覽器，則會看到他們必須改為使用 Microsoft Edge 的訊息。

> [!TIP]
> 條件式存取是一項 Azure Active Directory (Azure AD) 技術。 從 Intune 存取之條件式存取節點與從 Azure AD 存取的節點相同。

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>在受原則保護瀏覽器中單一登入與 Azure AD 連線的 Web 應用程式

iOS 和 Android 上的 Microsoft Edge 可利用與所有和 Azure AD 已連線 Web 應用程式 (SaaS 和內部部署) 的 SSO。 SSO 可讓使用者透過 Microsoft Edge 存取 Azure AD 已連線 Web 應用程式，而不必重新輸入其認證。

SSO 要求裝置必須註冊 iOS 裝置的 Microsoft Authenticator 應用程式或 Android 上 Intune 公司入口網站應用程式。 使用者具有 Authenticator 應用程式或 Intune 公司入口網站時，如果他們的裝置尚未註冊，則這些使用者在受原則保護瀏覽器中巡覽至與 Azure AD 已連線 Web 應用程式時，系統會提示他們註冊其裝置。 使用 Intune 所管理的使用者帳戶註冊裝置之後，該帳戶也已啟用 Azure AD 已連線 Web 應用程式的 SSO。

> [!NOTE]
> 裝置註冊是使用 Azure AD 服務的簡單簽入。 它不需要完整裝置註冊，而且不表示將裝置上的任何其他權限授與 IT。

## <a name="create-a-protected-browser-app-configuration"></a>建立受保護的瀏覽器應用程式設定

如要套用應用程式設定，使用者的受保護瀏覽器或裝置上的另一個應用程式必須已受 [Intune 應用程式保護原則](app-protection-policy.md)管理。

建立受保護的瀏覽器應用程式設定會使用下列步驟：

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [用戶端應用程式]   > [應用程式設定原則]   > [新增]  。
3. 在 [新增設定原則]  刀鋒視窗上，輸入應用程式組態設定的 [名稱]  和選擇性 [描述]  。
4. 針對 [裝置註冊]  類型請選擇 [受管理的應用程式]  。
5. 選擇 [Select the required apps] (選取必要的應用程式)  ，然後在 [目標 App]  刀鋒視窗上，選擇適用於 iOS、Android 或兩者的 **Managed Browser** 或 **Edge**。
6. 選擇 [確定]  返回 [新增設定原則]  刀鋒視窗。
7. 選擇 [組態設定]  。 在 [設定]  刀鋒視窗上，您可以定義金鑰和值組來為 Microsoft Edge 提供設定。 請使用本文稍後的各個章節，來了解您可以定義的不同金鑰和值組。

    > [!NOTE]
    > Microsoft Edge 使用與 Managed Browser 相同的金鑰和值組。 

8.  完成之後，請按一下 [確定]  。
9.  在 [新增設定原則]  刀鋒視窗上，選擇 [新增]  。<br>
    會隨即建立新設定，然後顯示在 [應用程式設定]  刀鋒視窗上。

## <a name="assign-the-configuration-settings-you-created"></a>指派您建立的組態設定 

您可以將設定指派給使用者的 Azure AD 群組。 如果該使用者已經安裝目標受保護的瀏覽器應用程式，則此應用程式是由您指定的設定管理。

1. 在 Intune 行動應用程式管理儀表板的 [用戶端應用程式]  刀鋒視窗上，選擇 [應用程式設定原則]  。
2. 從應用程式設定清單，選取您要指派的設定。
3. 在下一個刀鋒視窗上，選擇 [指派]  。
4. 在 [指派]  刀鋒視窗上，選取您要指派應用程式設定的 Azure AD 群組，然後選擇 [確定]  。

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>如何設定受保護瀏覽器的應用程式 Proxy 設定

Microsoft Edge 及 [Azure AD 應用程式 Proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) 可以一起使用，讓使用者在他們的行動裝置上存取內部網路網站。 

以下是一些 AD 應用程式 Proxy 啟用的案例範例： 

- 使用者正在使用受 Intune 保護的 Outlook 行動應用程式。 然後他們按一下電子郵件中的內部網路網站連結，Microsoft Edge 則辨識此內部網路網站已透過應用程式 Proxy 向使用者公開。 使用者會透過應用程式 Proxy 自動進行路由傳送，在到達內部網路網站之前，使用任何適用的 Multi-Factor Authentication 和條件式存取來進行驗證。 使用者現在能夠甚至是在其行動裝置上存取內部網路網站，且 Outlook 中的連結會如預期運作。
- 使用者在其 iOS 或 Android 裝置上開啟 Microsoft Edge。 如果 Microsoft Edge 受到 Intune 保護，且已啟用應用程式 Proxy，則使用者可以使用他們慣用的內部 URL 巡覽至內部網路網站。 Microsoft Edge 會辨識此內部網路網站已透過應用程式 Proxy 向使用者公開，且使用者會自動透過應用程式 Proxy 傳送，在到達內部網路網站之前先通過驗證。 

### <a name="before-you-start"></a>開始之前

- 透過 Azure AD 應用程式 Proxy 設定內部應用程式。
    - 若要設定應用程式 Proxy 並發佈應用程式，請參閱[安裝程式文件](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)。
- Microsoft Edge 應用程式必須已指派 [Intune 應用程式保護原則](app-protection-policy.md)。

> [!NOTE]
> 更新的應用程式 Proxy 重新導向資料，最多可能需要 24 小時才會在 Managed Browser 和 Microsoft Edge 中生效。

#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>步驟 1：從 Outlook 啟用自動重新導向到受保護的瀏覽器
Outlook 必須設定啟用以下設定的應用程式保護原則：**與受原則管理的瀏覽器共用 Web 內容**。

![應用程式保護原則 - 與受原則管理的瀏覽器共用 Web 內容](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>步驟 2：設定應用程式組態設定，以啟用應用程式 Proxy
使用下列金鑰/值組設定目標 Microsoft Edge，以針對 Microsoft Edge 啟用應用程式 Proxy：

|    金鑰    |    值    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

如需如何前後使用 Microsoft Edge 與 Azure AD 應用程式 Proxy 緊密 (並受保護) 存取內部部署 Web 應用程式的詳細資訊，請參閱 Enterprise Mobility + Security 部落格文章：[建議搭配使用：Intune 和 Azure Active Directory 合作以改善使用者存取](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) \(英文\)。 此部落格文章參考 Intune Managed Browser，但內容也適用於 Microsoft Edge。

## <a name="how-to-configure-a-homepage-shortcut-for-microsoft-edge"></a>如何設定適用於 Microsoft Edge 的首頁捷徑

此設定允許您設定適用於 Microsoft Edge 的首頁捷徑。  在 Microsoft Edge 中開啟新索引標籤時，您設定的首頁捷徑會成為搜尋列下方第一個圖示。 使用者在其受控內容中將無法編輯或刪除這個捷徑。 首頁捷徑會顯示您組織的名稱，以區分該捷徑。 

使用下列金鑰/值組來設定首頁捷徑：

|    金鑰    |    值    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    指定有效的 URL。 基於安全性考量，會封鎖不正確的 URL。<br>範例：  `<https://www.bing.com`>
    |

## <a name="how-to-configure-managed-bookmarks-for-microsoft-edge"></a>如何設定 Microsoft Edge 的受控書籤

為了方便存取，您可以設定想讓使用者在使用 Microsoft Edge 時的可用書籤。 以下是一些詳細資料：

- 使用者在使用 Microsoft Edge 的企業模式時，才會看到這些書籤。 
- 使用者無法刪除或修改這些書籤。
- 這些書籤會顯示在清單頂端。 使用者建立的所有書籤都會顯示在這些書籤下方。
- 如果您已啟用 App Proxy 重新導向，即可使用 App Proxy Web 應用程式的內部或外部 URL 來新增這些 Web 應用程式。

您可以使用下列金鑰/值組來設定受控書籤：

|    金鑰    |    值    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    此設定值是書籤清單。 每個書籤的組成都是書籤標題加書籤 URL。 請使用 `|` 字元分隔標題和 URL。      **範例：**<br>`Microsoft Bing|https://www.bing.com`<p>若要設定多個書籤，請以雙引號字元 `||` 分隔每組配對。<p>**範例：**<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="how-to-display-myapps-within-microsoft-edge-bookmarks"></a>如何在 Microsoft Edge 書籤中顯示 MyApps

根據預設，您的使用者將會在 Microsoft Edge 書籤的資料夾中，看到設定給他們的 MyApps 網站。 將會使用您的組織名稱標示資料夾。

|    金鑰    |    值    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **True** 會在 Microsoft Edge 書籤中顯示 MyApps。<p>**False** 會在 Microsoft Edge 中隱藏 MyApps。    |

## <a name="how-to-specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>如何為 Microsoft Edge 指定允許或封鎖的網站清單
您可以使用應用程式設定來定義當使用者使用他們的工作設定檔時，可以存取哪些網站。 如果您使用允許清單時，您的使用者將只能存取您已明確列出的網站。 如果您使用封鎖的清單時，您的使用者將能夠存取所有的站台，除了您明確封鎖的站台。 您只應該使用允許或封鎖清單，不能兩者都使用。 如果兩者都以裝置為目標，將適用允許的清單。  

您可以使用下列金鑰/值組，為 Microsoft Edge 設定允許或封鎖的網站清單。 如需有效 URL 格式的詳細資訊，請繼續閱讀。 

|    金鑰    |    值    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    從下列選項進行選擇：<p>1.指定允許的 URL (僅允許這些 URL；不能存取其他站台)：<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2.指定封鎖的 URL (可以存取所有其他網站)：<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    金鑰的相對應值為 URL 清單。 您可以以單一值的方式，輸入想要允許或封鎖的所有 URL，並使用垂直線 `|` 字元分隔。<p>**範例：**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>適用於允許和封鎖網站清單的 URL 格式 
您可以使用各種不同 URL 格式來建置您的允許/封鎖網站清單。 下表會詳細說明這些允許的模式。 在開始之前有一些注意事項： 
- 確定您在清單中輸入 UTL 時，已在所有 URL 中加上 **http** 或 **https** 的前置詞。
- 您可以根據下列許可模式清單中的規則，來使用萬用字元符號 (*)。
- 您可以在位址中指定連接埠號碼。 如不指定連接埠號碼，會使用下列值：
    - 針對 http 使用連接埠 80
    - 針對 https 使用連接埠 443
- **不**支援對連接埠號碼使用萬用字元。 例如，不支援 `http://www.contoso.com:*` 和 `http://www.contoso.com:*/`。

    |    URL    |    詳細資料    |    相符項    |    不符合    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    比對單一頁面    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    比對單一頁面    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/&#42;`   |    比對所有以 `www.contoso.com` 開頭的 URL    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    比對 `contoso.com` 下的所有子網域    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`    |
    |    `http://www.contoso.com/images`    |    比對單一資料夾    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    使用連接埠號碼來比對單一頁面    |    http://www.contoso.com:80    |         |
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
    - `http://www.contoso.com:*`
    - `http://www.contoso.com: /*`
  
## <a name="defining-behavior-when-users-try-to-access-a-blocked-site"></a>定義當使用者嘗試存取已封鎖網站時的行為

由於 Microsoft Edge 中內建了雙重身分識別模型，您可以為終端使用者啟用 Intune Managed Browser 所無法達成且更有彈性的體驗。 當使用者在 Microsoft Edge 叫用已封鎖的網站時，會可以提示他們在其個人內容開啟連結，而不是其工作內容，這樣可讓他們維持受到保護，同時維持公司資源安全。 例如，如果使用者透過其 Outlook 收到新聞文章的連結，他們將能夠在其個人的內容或 [InPrivate] 索引標籤中開啟連結，而不是不允許新聞網站的工作內容。 根據預設，會允許這些轉換。

使用下列金鑰/值組來設定是否允許這些軟轉換：

|    金鑰    |    值    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    [True]  允許 Microsoft Edge 將使用者轉換至其個人內容以開啟封鎖的網站<p>[封鎖]  會防止 Microsoft Edge 轉換使用者，而使用者將只會看到一則訊息，指出他們正在嘗試存取的網站遭到封鎖。    |

## <a name="directing-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>將使用者導向 Microsoft Edge，而不是 Intune Managed Browser 

Intune Managed Browser 和 Microsoft Edge 現在都可以用來作為受原則保護的瀏覽器。 為了確保您的使用者會被導向使用正確瀏覽器應用程式，請用下列組態設定來設定所有 Intune 受控應用程式 (例如 Outlook 和 OneDrive) 的目標：

|    金鑰    |    值    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    值 `true` 將會引導使用者使用 Microsoft Edge。<p>值 `false` 將會引導使用者使用 Intune Managed Browser。    |

如果未設定此應用程式設定值，則下列邏輯會定義哪一個瀏覽器將用來開啟公司的連結。

在 Android 上：
- 如果使用者已在其裝置中下載 Intune Managed Browser 和 Microsoft Edge，將會開啟前者。 
- 如果裝置上僅下載 Microsoft Edge 且已經透過 Intune 原則設定為目標應用程式，則會開啟 Microsoft Edge。
- 如果裝置上只有 Managed Browser 且已經透過 Intune 原則設定為目標應用程式，則會開啟 Managed Browser。

在 iOS 上，針對已整合 Intune SDK for iOS v. 9.0.9+ 的應用程式：
- 如果裝置上同時有 Managed Browser 和 Microsoft Edge，則會啟動 Intune Managed Browser。  
- 如果裝置上只有 Microsoft Edge 且已經透過 Intune 原則設定為目標應用程式，則會啟動 Microsoft Edge。
- 如果裝置上只有 Managed Browser 且已經透過 Intune 原則設定為目標應用程式，則為 Managed Browser。

## <a name="using-microsoft-edge-on-ios-to-access-managed-app-logs"></a>在 iOS 上使用 Microsoft Edge 來存取受控應用程式記錄檔 

在其 iOS 裝置上安裝了 Microsoft Edge 的終端使用者，可以檢視所有 Microsoft 所發佈應用程式的管理狀態。 他們可以傳送記錄檔用於疑難排解其受管理的 iOS 應用程式。
1. 在您的 iOS 裝置上開啟 Microsoft Edge。
2. 網址方塊中的類型 `about:intunehelp`。 
3. 疑難排解模式會從 Microsoft Edge 中啟動。

如需儲存在應用程式記錄中的設定清單，請參閱[在 Managed Browser 中檢閱應用程式保護記錄](app-protection-policy-settings-log.md)。

若要了解如何在 Android 裝置上檢視記錄檔，請參閱[透過電子郵件將記錄檔傳送給 IT 系統管理員](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android)。 

## <a name="security-and-privacy-for-microsoft-edge"></a>Microsoft Edge 的安全性和隱私權

Microsoft Edge 的其他安全性和隱私權考量：

- Microsoft Edge 不會使用在其裝置上使用者為原生瀏覽器設定的設定，因為 Microsoft Edge 無法存取這些設定。
- 如果您已在與 Microsoft Edge 建立關聯的應用程式防護原則中設定 [需要簡單的 PIN 以進行存取]  或 [需要公司認證以進行存取]  選項，且使用者選取驗證頁面上的說明連結，使用者即可以瀏覽任何網際網路網站，不論其是否已新增至原則的封鎖清單中。
- Microsoft Edge 可以在直接存取網站時，只封鎖網站的存取。 使用中繼服務 (例如翻譯服務) 存取網站時，不封鎖存取。
- 若要允許驗證並存取 Intune 文件，請從允許或封鎖清單設定中排除 * **.microsoft.com**。 一律允許。
關閉使用量資料。Microsoft 會自動收集有關 Managed Browser 效能和使用的匿名資料，以改善 Microsoft 產品和服務。 使用者可以在裝置上使用 **[使用方式資料]** 設定以關閉資料收集。 您無法控制這項資料的收集。 在 iOS 裝置上，無法開啟使用者利用過期或未受信任的憑證瀏覽的網站。

## <a name="next-steps"></a>後續步驟

- [什麼是應用程式保護原則？](app-protection-policy.md) 
