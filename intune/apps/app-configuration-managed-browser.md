---
title: 使用受原則保護的瀏覽器管理公司 Web 存取
titleSuffix: Microsoft Intune
description: 使用由 Intune 指派、受原則保護的瀏覽器管理企業網頁瀏覽與 Web 資料傳輸。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 03b89225ee5691aea2653fb3ca19f99139a015aa
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181805"
---
# <a name="manage-web-access-using-a-microsoft-intune-policy-protected-browser"></a>使用 Microsoft Intune 的受原則保護瀏覽器來管理 Web 存取

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

使用受 Intune 原則保護的瀏覽器 (Microsoft Edge 或 Intune Managed Browser)，您可以確保存取公司網站的過程中隨時受到保護。  使用 Intune 設定時，受保護的瀏覽器可利用下列優勢：

- 應用程式保護原則
- 條件式存取
- 單一登入
- 應用程式組態設定
- Azure 應用程式 Proxy 整合

> [!IMPORTANT]
> 即將淘汰 Intune Managed Browser。 請使用 Microsoft Edge 來取得受保護的 Intune 瀏覽器體驗。 

## <a name="microsoft-edge-support"></a>Microsoft Edge 支援

您可以針對 iOS/iPadOS 與 Android 裝置上的企業案例使用 Microsoft Edge。 Microsoft Edge 支援與 Intune Managed Browser 相同的所有管理案例，並在終端使用者體驗中新增增強功能。 下列依據 Intune 原則啟用的 Microsoft Edge 企業功能包括：

- **雙重識別** - 使用者可以新增工作帳戶與個人帳戶以進行瀏覽。 系統會完整區隔兩個身分識別，類似於 Office 365 和 Outlook 中的架構與體驗。 Intune 系統管理員可以在工作帳戶內，針對受保護的瀏覽體驗設定所需原則。 
- **Intune 應用程式保護原則整合** - 系統管理員現在可以將應用程式保護原則的目標設為 Microsoft Edge，藉此控制下列功能：剪下、複製及貼上、防止擷取螢幕畫面，以及確保使用者選取的連結只會在其他受控應用程式中開啟。
- **Azure 應用程式 Proxy 整合** - 系統管理員可以控制對 SaaS 應用程式和 Web 應用程式的存取，協助確保無論使用者是從公司網路連線或從網際網路連線，瀏覽器型應用程式都只會在安全的 Microsoft Edge 瀏覽器中執行。 
- **受控我的最愛和首頁捷徑** - 為了方便存取，系統管理員可以設定 URL，以在終端使用者進入公司內容中時，顯示在 [我的最愛] 底下。 系統管理員可以設定首頁捷徑，就會在公司的使用者於 Microsoft Edge 中開啟新的頁面或新的索引標籤時，顯示為主要捷徑。

適用於 Microsoft Edge 的 Microsoft Intune 保護原則可協助保護您的組織資料和資源。 受 Intune 保護的 Microsoft Edge 能確保公司的資源無論是在原生安裝的應用程式內，或透過網頁瀏覽器存取時，都會受到保護。

## <a name="getting-started"></a>開始使用

Microsoft Edge 和 Intune Managed Browser 是網頁瀏覽器應用程式，您和您的終端使用者可從公共 App Store 下載，並在組織中使用。 

瀏覽器原則的作業系統需求：
- Android 4 及更新版本，或
- iOS/iPadOS 8.0 與更新版本。

較舊版本的 Android 與 iOS/iPadOS 能夠繼續使用 Managed Browser，但將無法安裝新版應用程式，而且可能無法存取所有應用程式功能。 建議您將這些裝置更新為受支援的作業系統版本。

>[!NOTE]
>Managed Browser 不支援安全通訊端層版本 3 (SSLv3) 密碼編譯通訊協定。


## <a name="application-protection-policies-for-protected-browsers"></a>受保護瀏覽器的應用程式保護原則

因為 Microsoft Edge 與 Managed Browser 已經和 Intune SDK 整合，所以您也可以將應用程式防護原則套用至這些應用程式，包括：
- 控制剪下、複製和貼上的運用。
- 防止擷取螢幕畫面。
- 確保只能在受控應用程式和瀏覽器中開啟公司連結。

如需詳細資料，請參閱[什麼是應用程式保護原則？](app-protection-policy.md)

您可以套用這些設定至：

- 向 Intune 註冊的裝置
- 向其他 MDM 產品註冊
- 未受管理的裝置

>[!NOTE]
>如果使用者從應用程式市集安裝 Managed Browser，且 Intune 並沒有管理它，可以將它作為基本網頁瀏覽器使用，並透過 Microsoft MyApps 網站支援單一登入。 系統會將使用者直接帶往 MyApps 網站，他們可以在該網站看到其所有已佈建的 SaaS 應用程式。
由於 Managed Browser 或 Microsoft Edge 未受 Intune 管理，所以無法存取來自其他 Intune 受控的應用程式資料。 


## <a name="conditional-access-for-protected-browsers"></a>受保護瀏覽器的條件式存取

Managed Browser 現在是進行條件式存取的經過核准用戶端應用程式。 這表示您可以限制行動瀏覽器對 Azure AD 已連線 Web 應用程式的存取，而在這些 Web 應用程式中，使用者只能使用 Managed Browser，並封鎖存取任何其他未受保護的瀏覽器 (如 Safari 或 Chrome)。 這項保護可以套用至 Azure 資源，例如 Exchange Online 和 SharePoint Online、Microsoft 365 系統管理中心，甚至是已透過 [Azure AD 應用程式 Proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) 對外部使用者公開的內部部署網站。 

若要限制 Azure AD 已連線 Web 應用程式在行動平台上使用 Intune Managed Browser，您可以建立條件式存取原則要求使用經過核准的用戶端應用程式。 

> [!TIP]  
> 條件式存取是一項 Azure Active Directory (Azure AD) 技術。 從 *Intune* 存取的條件式存取節點，與從 *Azure AD* 存取的節點相同。  

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [條件式存取]   > [新增原則]  。
3. 新增原則的 [名稱]  。 
4. 在 [指派]  區段中，選取 [條件]   > [用戶端應用程式]  。 隨即顯示 [用戶端應用程式]  窗格。
5. 按一下 [設定]  下的 [是]  ，將原則套用至特定用戶端應用程式。
6. 確認已選取 **Browser** 作為用戶端應用程式。

    ![Azure AD - Managed Browser - 選取用戶端應用程式](./media/app-configuration-managed-browser/managed-browser-conditional-access-02.png)

    > [!NOTE]
    > 如果您想要限制哪些原生應用程式 (非瀏覽器應用程式) 可以存取這些雲端應用程式，則也可以選取 [行動裝置 App 及桌面用戶端]  。

7. 按一下 [完成]   > [完成]  。
8. 在 [指派]  區段中，選取 [使用者和群組]  ，然後選擇您想要指派此原則的使用者或群組。 按一下 [完成]  以關閉窗格。
9. 在 [指派]  區段中，選取 [雲端應用程式或動作]  以選擇要使用此原則保護的應用程式。 按一下 [完成]  以關閉窗格。
10. 選取窗格之 [存取控制]  區段中的 [授與]  。 
11. 按一下 [授與存取]  ，然後按一下 [需要經過核准的用戶端應用程式]  。 
12. 按一下 [授與]  窗格上的 [選取]  。 此原則必須指派給您只想要讓 Intune Managed Browser 應用程式存取的雲端應用程式。

    ![Azure AD - Managed Browser 條件式存取原則](./media/app-configuration-managed-browser/managed-browser-conditional-access-01.png)



設定上述原則之後，會強制使用者使用 Intune Managed Browser 存取您使用此原則保護的 Azure AD 已連線 Web 應用程式。 在此情況下，如果使用者嘗試使用非受控瀏覽器，則會注意到必須改為使用 Intune Managed Browser。

Managed Browser 不支援傳統「條件式存取」原則。 如需詳細資訊，請參閱[移轉 Azure 入口網站中的傳統原則](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration)。

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>在受原則保護瀏覽器中單一登入與 Azure AD 連線的 Web 應用程式

iOS/iPadOS 與 Android 上的 Microsoft Edge 與 Intune Managed Browser 能以 SSO 方式連線到與 Azure AD 連線的所有 Web 應用程式 (SaaS 與內部部署)。 當 Microsoft Authenticator 應用程式存在於 iOS/iPadOS 上，或 Intune 公司入口網站應用程式存在於 Android 上時，受原則保護之瀏覽器的使用者便能存取與 Azure AD 連線的 Web 應用程式，而無須重新輸入認證。

SSO 要求您的裝置必須由 iOS/iPadOS 上的 Microsoft Authenticator 應用程式註冊，或是由 Android 上的 Intune 公司入口網站註冊。 如果另一個應用程式尚未註冊具有 Authenticator 應用程式或 Intune 公司入口網站的使用者裝置，則這些使用者在受原則保護瀏覽器中巡覽至與 Azure AD 連線的 Web 應用程式時，系統會提示他們註冊其裝置。 使用 Intune 所管理的帳戶註冊裝置之後，該帳戶也已啟用 Azure AD 已連線 Web 應用程式的 SSO。 

> [!NOTE]
> 裝置註冊是使用 Azure AD 服務的簡單簽入。 它不需要完整裝置註冊，而且不表示將裝置上的任何其他權限授與 IT。

## <a name="create-a-protected-browser-app-configuration"></a>建立受保護的瀏覽器應用程式設定

>[!IMPORTANT]
>如要套用應用程式設定，使用者的受保護瀏覽器或裝置上的另一個應用程式必須已受 [Intune 應用程式防護原則]( ../app-protection-policy.md)管理

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [應用程式設定原則]   > [新增]   > [受管理的應用程式]  。
3. 在 [建立應用程式設定原則]  窗格的 [基本]  頁面上，輸入應用程式組態設定的 [名稱]  和選擇性 [描述]  。
4. 選擇 [選取公用應用程式]  ，然後選擇適用於 iOS/iPadOS、Android 或兩者的 [Managed Browser]  和/或 [Edge]  。
5. 按一下 [選取]  以返回 [建立應用程式設定原則]  窗格。
6. 按一下 [下一步]  以顯示 [設定]  頁面。
7. 在 [設定]  頁面上，您可以定義金鑰和值組以提供應用程式設定。 請使用本文稍後的各個章節，來了解您可以定義的不同金鑰和值組。
8. 按一下 [下一步]  以顯示 [指派]  頁面，然後按一下 [選取要包含的群組]  和/或 [選取要排除的群組]  。
9. 按一下 [下一步]  以顯示 [檢閱 + 建立]  頁面。
10. 在您檢閱應用程式設定原則之後，請按一下 [建立]  。

新設定會隨即建立，然後顯示在 [應用程式設定原則]  窗格上。


## <a name="assign-the-configuration-settings-you-created"></a>指派您建立的組態設定

您可以將設定指派給使用者的 Azure AD 群組。 如果該使用者已經安裝目標受保護的瀏覽器應用程式，則此應用程式是由您指定的設定管理。

1. 在 Intune 行動應用程式管理儀表板的 [應用程式]  窗格上，選擇 [應用程式設定原則]  。
2. 從應用程式設定清單，選取您要指派的設定。
3. 在下一個窗格上，選擇 [指派]  。
4. 在 [指派]  窗格上，選取您要指派應用程式設定的 Azure AD 群組，然後選擇 [確定]  。

## <a name="how-to-set-microsoft-edge-as-the-protected-browser-for-your-organization"></a>如何針對貴組織將 Microsoft Edge 設定為受保護的瀏覽器

此設定可讓您設定是否要將使用者導向至 Microsoft Edge 或 Intune Managed Browser，前提假設這兩個瀏覽器都會以應用程式保護原則設為目標。 **此應用程式設定原則設定應以開啟網頁連結的 Intune 受控應用程式為目標。** 

如果將此設定設為 "True"：

- 當使用者從以此設定為目標的 Intune 受控應用程式中開啟連結時，即會將其導向至 Microsoft Edge。 
- 如果他們還沒有此應用程式，系統就會提示他們從商店下載 Microsoft Edge，而不論他們是否已下載 Intune Managed Browser。

如果將此設定設為 "False"：

- 如果您的使用者**同時**下載了 Managed Browser 和 Microsoft Edge，將啟動 Managed Browser。 
- 如果您的使用者下載了 Managed Browser **或** Microsoft Edge **其中之一**，則將啟動該瀏覽器應用程式。 
- 如果您的使用者並未下載任一個瀏覽器應用程式，系統就會提示他們下載 Managed Browser。

使用上述程序來建立 Microsoft Edge 應用程式設定。 在選取 [設定]  窗格上的 [組態設定]  時 (步驟 9)，提供下列金鑰和值組：

| 機碼                              |  值   |
|----------------------------------|----------|
| **com.microsoft.intune.useEdge** | **true** |

> [!NOTE]
> 在管理 Microsoft Edge 的應用程式保護原則和應用程式設定中指定的相關聯應用程式中，請確定已設定下列資料保護原則設定：
> - 將組織資料傳送至其他應用程式：**受原則管理的應用程式**
> - 限制使用其他應用程式的 Web 內容傳輸：**受原則管理的瀏覽器**

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>如何設定受保護瀏覽器的應用程式 Proxy 設定

Microsoft Edge 與 Intune Managed Browser 和 [Azure AD 應用程式 Proxy]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) \(部分機器翻譯\) 可以一起使用，以支援 iOS/iPadOS 和 Android 裝置使用者的下列案例：

- 使用者下載並登入 Microsoft Outlook 應用程式。 自動套用 Intune 應用程式保護原則。 它們會加密已儲存的資料，並阻擋使用者將公司檔案傳輸至裝置上未受管理的應用程式或位置。 當使用者接著在 Outlook 中按一下內部網路網站的連結時，您可以指定用受保護的瀏覽器應用程式開啟該連結，不用其他瀏覽器。 受保護的瀏覽器可辨識此內部網路網站是透過應用程式 Proxy 向使用者公開。 使用者會透過應用程式 Proxy 自動進行路由傳送，在到達內部網路網站之前，使用任何適用的多重要素驗證和條件式存取進行驗證。 使用者以前從遠端找不到這個網站，現在不但可以存取，Outlook 中的連結也一如預期般運作。
- 遠端使用者開啟受保護的瀏覽器應用程式，並瀏覽至使用內部 URL 的內部網路網站。 受保護的瀏覽器可辨識此內部網路網站是透過應用程式 Proxy 向使用者公開。 使用者會透過應用程式 Proxy 自動進行路由傳送，在到達內部網路網站之前，使用任何適用的多重要素驗證和條件式存取進行驗證。 使用者以前從遠端找不到這個網站，但現在可以存取。

### <a name="before-you-start"></a>在您開始使用 Intune 之前

- 透過 Azure AD 應用程式 Proxy 設定內部應用程式。
  - 若要設定應用程式 Proxy 並發佈應用程式，請參閱[安裝程式文件](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)。 
  - [使用者必須指派給](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-add-on-premises-application#add-a-user-for-testing)要進行重新導向的企業應用程式。 即使已將應用程式設為通道模式以進行預先驗證，並且已在應用程式 Proxy 設定中關閉使用者指派需求，也必須這麼做。
- 您至少必須使用 Managed Browser 應用程式 1.2.0 版本。
- Managed Browser 或 Microsoft Edge 應用程式的使用者已將 [Intune 應用程式防護原則](app-protection-policy.md)指派給應用程式。

    > [!NOTE]
    > 更新的應用程式 Proxy 重新導向資料，最多可能需要 24 小時才會在 Managed Browser 和 Microsoft Edge 中生效。


#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>步驟 1：從 Outlook 啟用自動重新導向到受保護的瀏覽器
Outlook 必須設定啟用以下設定的應用程式保護原則：**限制 Web 內容只在 Managed Browser 中顯示**。

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-protected-browser"></a>步驟 2：指派已針對受保護的瀏覽器指派的應用程式設定原則
此程序會設定 Managed Browser 或 Microsoft Edge 應用程式來使用應用程式 Proxy 重新導向。 

開啟原則組態設定中的 [Edge]  索引標籤，然後針對應用程式 Proxy 重新導向值選取 [啟用]  。 啟用此設定將可讓使用者存取公司連結和透過 Azure 應用程式 Proxy 發佈的內部部署 Web 應用程式。

如需如何前後使用 Managed Browser、Microsoft Edge 與 Azure AD 應用程式 Proxy 緊密 (並受保護) 存取內部部署 Web 應用程式的詳細資訊，請參閱 Enterprise Mobility + Security 部落格文章：[建議搭配使用：Intune 和 Azure Active Directory 合作以改善使用者存取](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) \(英文\)。

## <a name="how-to-configure-the-homepage-for-a-protected-browser"></a>如何未受保護的瀏覽器設定首頁

此設定可讓您設定使用者啟動受保護的瀏覽器或建立新索引標時會看到的首頁。 
- 此設定會在 Managed Browser 中顯示該網頁。  Edge 會改為顯示首頁捷徑。
- 首頁捷徑圖示會顯示為搜尋控制項下方的圖示。  無法編輯或刪除它。
- 首頁捷徑會顯示您組織的名稱，以區分該捷徑。  它一律會顯示為第一個圖示。

使用程序來建立 Managed Browser 或 Microsoft Edge 應用程式設定，提供下列金鑰和值組：

|                                機碼                                |                                                           值                                                            |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.homepage</strong> | 指定有效的 URL。 基於安全性考量，會封鎖不正確的 URL。<br>範例：`https://www.bing.com` |

## <a name="how-to-configure-bookmarks-for-a-protected-browser"></a>如何設定受保護瀏覽器的書籤

此設定可讓您設定一組書籤，供 Microsoft Edge 或 Managed Browser 的使用者使用。

- 使用者無法刪除或修改這些書籤
- 這些書籤會顯示在清單頂端。 使用者建立的所有書籤都會顯示在這些書籤下方。
- 如果您已啟用 App Proxy 重新導向，即可使用 App Proxy Web 應用程式的內部或外部 URL 來新增這些 Web 應用程式。

使用程序來建立 Managed Browser 或 Microsoft Edge 應用程式設定，提供下列金鑰和值組：

|                                機碼                                 |                                                                                                                                                                                                                                                         值                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.bookmarks</strong> | 此設定值是一份書籤。 每個書籤的組成都是書籤標題加書籤 URL。 請使用 <strong>&#124;</strong> 字元分隔標題和 URL。<br><br>範例：<br> <code>Microsoft Bing&#124;https://www.bing.com</code><br><br>若要設定多個書籤，請以雙引號字元 <strong>&#124;&#124;</strong> 分隔每組配對。<br><br>範例：<br> <code>Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com</code> |

## <a name="how-to-specify-allowed-and-blocked-urls-for-a-protected-browser"></a>如何為受保護的瀏覽器指定允許與封鎖的 URL

使用程序來建立 Managed Browser 或 Microsoft Edge 應用程式設定，提供下列金鑰和值組：

|機碼|值|
|-|-|
|從下列選項進行選擇：<br><ul><li>指定允許的 URL (僅允許這些 URL；不能存取其他站台)：<br> **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br></li><li>指定封鎖的 URL (可以存取所有其他網站)：<br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**</li></ul>|金鑰的相對應值為 URL 清單。 您可以以單一值的方式，輸入想要允許或封鎖的所有 URL，並使用縱線 **&#124;** 字元分隔。<br><br>範例：<br><br><code>URL1&#124;URL2&#124;URL3</code><br><code>http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com</code>|

>[!IMPORTANT]
>請勿同時指定這兩個金鑰。 如果兩個金鑰都以同一使用者為目標，會使用允許金鑰，因為它是最嚴格的選項。
>此外，請確定未封鎖重要的網頁，例如您的公司網站。

### <a name="url-format-for-allowed-and-blocked-urls"></a>適用於允許和封鎖 URL 的 URL 格式
使用下列資訊，來了解您在允許和封鎖清單中指定 URL 時可使用的允許格式與萬用字元：

- 您可以根據下列許可模式清單中的規則，來使用萬用字元符號 ( **&#42;** )：

- 確定您在清單中輸入 UTL 時，已在所有 URL 中加上 **http** 或 **https** 的前置詞。

- 您可以在位址中指定連接埠號碼。 如不指定連接埠號碼，會使用下列值：

  - 針對 http 使用連接埠 80

  - 針對 https 使用連接埠 443

  不支援對連接埠號碼使用萬用字元。 例如，不支援 `http://www.contoso.com:;` 和 `http://www.contoso.com: /;`。

- 使用下表來了解您在指定 URL 時可使用的允許模式：

|                  URL                  |                     詳細資料                      |                                                相符項                                                |                                不符合                                 |
|---------------------------------------|--------------------------------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
|        `http://www.contoso.com`         |              比對單一頁面               |                                            `www.contoso.com`                                            |  `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`contoso.com`/   |
|          `http://contoso.com`           |              比對單一頁面               |                                             `contoso.com/`                                              | `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com` |
|    `http://www.contoso.com/&#42;`     | 比對所有以 `www.contoso.com` 開頭的 URL |      `www.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com/videos/tvshows`      |              `host.contoso.com`<br /><br />`host.contoso.com/images`              |
|    `http://*.contoso.com/*`     |     比對 contoso.com 下的所有子網域     | `developer.contoso.com/resources`<br /><br />`news.contoso.com/images`<br /><br />`news.contoso.com/videos` |                               `contoso.host.com`                                |
|     `http://www.contoso.com/images`     |             比對單一資料夾              |                                        `www.contoso.com/images`                                         |                          `www.contoso.com/images/dogs`                          |
|       `http://www.contoso.com:80`       |  使用連接埠號碼來比對單一頁面   |                                       `http://www.contoso.com:80`                                       |                                                                               |
|        `https://www.contoso.com`        |          比對單一且安全的頁面           |                                        `https://www.contoso.com`                                        |                            `http://www.contoso.com`                             |
| `http://www.contoso.com/images/&#42;` |    符合單一資料夾及所有子資料夾    |                  `www.contoso.com/images/dogs`<br /><br />`www.contoso.com/images/cats`                   |                            `www.contoso.com/videos`                             |

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
  
## <a name="soft-transitions-from-work-to-personal-accounts"></a>從工作到個人帳戶的平順轉換

Microsoft Edge 行動企業體驗的基石是雙重身分識別模型，這表示 Microsoft Edge 同時支援工作和個人身分識別。 與 Office 365 和 Outlook 應用程式一樣，此雙重身分識別模型讓終端使用者可以使用 Microsoft Edge 來滿足所有瀏覽需求，並根據系統管理員定義的內容原則，輕鬆地在這兩種體驗之間切換。 瀏覽個人內容不會受到影響，而公司資訊會完全保留於 Microsoft Edge 的工作內容中。 

此模型的好處之一是，當使用者嘗試開啟貴組織不允許的網站連結 (例如報紙文章等) 時，他們能夠在自己的個人內容中進行此操作，這會與他們的工作內容完全分開。 這些平順轉換預設為啟用。 

使用程序來建立 Managed Browser 或 Microsoft Edge 應用程式設定，提供下列金鑰和值組：

| 機碼                                                                | 值                                                 |
|--------------------------------------------------------------------|-------------------------------------------------------|
| **com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock** | **False** 會封鎖這些平順轉換的發生 |

## <a name="how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios"></a>如何在 iOS 上使用受管理的瀏覽器存取受管理應用程式的記錄檔

在其 iOS/iPadOS 裝置上安裝 Managed Browser 的使用者，可以檢視 Microsoft 所發行之所有應用程式的管理狀態。 他們可以傳送用來對其受控 iOS/iPadOS 應用程式進行疑難排解的記錄檔。

1. 開啟 iOS/iPadOS [設定]  。
2. 選取受管理的**瀏覽器**應用程式設定。
3. 切換 [啟用 Intune 診斷]  在疑難排解模式中設定瀏覽器。
4. 開啟受管理的**瀏覽器**。 按一下 [檢視 Intune 應用程式狀態]  查看個別的應用程式原則設定。
5. 按 [開始使用]  和 [共用記錄]  或 [將記錄傳送給 Microsoft]  ，將疑難排解記錄檔傳送給您的 IT 系統管理員或 Microsoft。

您也可以從應用程式內，在疑難排解模式中開啟瀏覽器。

1. 開啟受管理的瀏覽器。
2. 網址方塊中的類型 `about:intunehelp`。
瀏覽器啟動疑難排解模式。

如需儲存在應用程式記錄中的設定清單，請參閱[在 Managed Browser 中檢閱應用程式保護記錄](app-protection-policy-settings-log.md)。

## <a name="security-and-privacy-for-the-managed-browser"></a>Managed Browser 的安全性與隱私權

- Managed Browser 不會使用使用者在其裝置上針對內建瀏覽器所做的設定。 Managed Browser 無法存取這些設定。

- 如果您已在與 Managed Browser 建立關聯的應用程式防護原則中設定 [需要簡單的 PIN 以進行存取]  或 [需要公司認證以進行存取]  選項，而且使用者選取了驗證頁面上的說明連結，他們就可以瀏覽任何的網際網路網站，而不論其是否已加入原則的封鎖清單中。

- Managed Browser 只有在它們直接存取網站時，才能封鎖對網站的存取。 使用中繼服務 (例如翻譯服務) 存取網站時，不封鎖存取。

- 若要允許驗證並存取 Intune 文件，請從允許或封鎖清單設定中排除 **&#42;.microsoft.com**。 一律允許。

### <a name="turn-off-usage-data"></a>關閉使用量資料
Microsoft 會自動收集有關 Managed Browser 效能和使用的匿名資料，以改善 Microsoft 產品和服務。 使用者可以在裝置上使用 **[使用方式資料]** 設定以關閉資料收集。 您無法控制這項資料的收集。

- 在 iOS/iPadOS 裝置上，使用者無法開啟具有過期或未受信任憑證的網站。

## <a name="next-steps"></a>後續步驟

- [什麼是應用程式保護原則？](app-protection-policy.md) 
