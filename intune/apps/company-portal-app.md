---
title: 如何設定公司入口網站應用程式
titleSuffix: Microsoft Intune
description: 了解如何將公司自有商標套用到 Intune 公司入口網站應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dd48eea5ee09562590844e11ac372480c892a7af
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585016"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>如何設定 Microsoft Intune 公司入口網站應用程式

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

使用者可以從 Microsoft Intune 公司入口網站存取公司資料及執行一般工作，例如註冊裝置、安裝應用程式，以及尋找向 IT 部門尋求協助的資訊。 此外，公司入口網站應用程式可讓使用者安全地存取公司資源。 公司入口網站應用程式提供數個不同的頁面，例如 [首頁]、[應用程式]、[應用程式詳細資料]、[裝置] 和 [裝置詳細資料]。 若要在公司入口網站中快速尋找應用程式，您可以在 [應用程式] 頁面上篩選應用程式。

> [!IMPORTANT]
> 若要支援 Google 的 Firebase 雲訊息傳遞 (FCM)，您必須將 Android 公司入口網站應用程式更新到最新的版本。 如需詳細資訊，請參閱新功能 - [將您的 Android 公司入口網站應用程式更新到最新的版本](../fundamentals/whats-new.md#update-your-android-company-portal-app-to-the-latest-version-)。

> [!Tip]
> 當您自訂公司入口網站時，這些組態會同時套用到公司入口網站和公司入口網站應用程式。 請注意，使用者必須或指派 Intune 授權，才能存取「公司入口網站」網站。

您可以透過自訂公司入口網站，協助為終端使用者提供熟悉且實用的體驗。 若要這樣做，請在 Intune 入口網站中，選取 [用戶端應用程式]   > [商標和自訂]  ，然後進行必要設定。

當使用者從公司入口網站安裝 iOS 應用程式時，他們將會收到提示。 當 iOS 應用程式連結至 App Store、連結至大量採購方案 (VPP)，或連結至企業營運 (LOB) 應用程式時，就會發生這種情況。 提示可讓使用者接受此動作，或允許應用程式的管理。 提示將顯示您的公司名稱，或者，當您的公司名稱無法使用時，將顯示**公司入口網站**。 

> [!Note]
> 如果您使用 Azure Government，應用程式記錄檔會提供給終端使用者，用來決定當他們在起始程序取得問題說明時如何進行共用。 不過，如果您未使用 Azure Government，當使用者在起始程序取得問題說明時，Windows 10 版公司入口網站會將應用程式記錄檔直接傳送給 Microsoft。 應用程式記錄檔傳送給 Microsoft 可以更輕鬆地進行疑難排解並解決問題。 

## <a name="company-information-and-privacy-statement"></a>公司資訊和隱私權聲明
公司名稱顯示為公司入口網站標題。 當使用者按一下隱私權連結時，會顯示隱私權聲明。

| 欄位名稱 | 長度上限 | 詳細資訊 |
|---|---|---|
|**公司名稱**| 40 | 這個名稱會顯示為公司入口網站的標題，並以文字形式在 Intune 使用者體驗期間顯示。 |
| **隱私權聲明 URL** |     79     | 您可以指定自己的公司隱私權聲明，在使用者從公司入口網站按一下隱私權連結時會顯示該聲明。 您必須以 `<https://www.contoso.com>` 格式輸入有效的 URL。 |

> [!NOTE]
> 我們依循 Microsoft 和 Apple 原則，不會基於任何原因將服務所收集的任何資料提供給任何協力廠商。

## <a name="support-information"></a>支援資訊
輸入貴公司的支援資訊，為您的員工提供 Intune 相關問題的連絡人。

|欄位名稱|長度上限|詳細資訊|
|---|---|---|
|**連絡人姓名** | 40 | 此姓名會顯示在 [說明及支援]  頁面上。 |
|**電話號碼** | 20 | 此連絡人電話號碼會顯示在 [說明及支援]  頁面上，讓員工能夠連絡您以尋求支援。 |
|**電子郵件地址**| 40 | 此連絡人地址會顯示在 [說明及支援]  頁面上。 您必須輸入有效的電子郵件地址，格式為 `alias@domainname.com`。 |
|**網站名稱**| 40 | 這是支援網站的 URL 所顯示的易記名稱。 若您只指定支援網站 URL 而未指定易記名稱，則會在公司入口網站的 [說明及支援]  頁面上顯示 [移至 IT 部門網站]。 |
|**網站 URL**| 150 | 如果想讓使用者參考您的支援網站，請在這裡指定 URL。 URL 的格式必須為 `https://www.contoso.com`。 如果您未指定 URL，公司入口網站的 [說明及支援]  頁面上將不會顯示支援網站的任何內容。 |
| **其他資訊**| 120 | 顯示在 [說明及支援]  頁面上。 |


## <a name="company-identity-branding-customization"></a>公司識別商標自訂
您可以使用公司標誌、公司名稱、佈景主題色彩和背景自訂您的公司入口網站。

### <a name="theme-color-and-logo-in-the-company-portal"></a>公司入口網站的佈景主題色彩和標誌
將佈景主題色彩套用到公司入口網站。 選取標準色彩，或針對自訂色彩輸入六位數的十六進位碼。

|欄位名稱|詳細資訊|
|---|---|
|**選取標準色彩或輸入六位數的十六進位代碼**| 選擇 [標準]  以視覺方式選取色彩。 選擇 [自訂]  根據十六進位代碼值選取特定色彩。|
|**選擇佈景主題色彩**| 選取要套用到公司入口網站的佈景主題色彩。 您可以從標準色彩中選擇，或輸入特定的十六進位碼。 |
|**顯示**| 選取要顯示**公司標誌和名稱**、**僅限公司標誌**或**僅限公司名稱**。 |
|**上傳您公司的標誌**|您可以上傳公司的標誌，以顯示在您的公司入口網站中。 請注意，文字色彩會自動選擇，以達最佳的對比效果。 您可以上傳透明背景的標誌以達到最佳外觀效果。<p><ul><li>影像大小上限：400 像素 x 400 像素</li><li>檔案大小上限：750KB</li><li>檔案類型：PNG、JPG 或 JPEG</li></ul>|

上傳標誌之後，預覽區會以佈景主題色彩顯示標誌。 如果您選擇顯示公司名稱，它就會在公司入口網站中以黑色或白色顯示，而且會根據您的佈景主題色彩自動選擇，以達最佳的對比效果。 畫面上的預覽區不會顯示公司名稱。 

### <a name="logo-to-use-on-white-or-light-backgrounds"></a>要在白色或淺色背景中使用的標誌
選擇在白色或淺色背景中看起來最佳的標誌。

|欄位名稱|詳細資訊|
|---|---|
|**上傳您的標誌**| 如果您已選擇要顯示公司標誌，就可以使用這個選項。 您可以上傳透明背景的標誌以達到最佳外觀效果。<p><ul><li>影像大小上限：400 像素 x 400 像素</li><li>檔案大小上限：750KB</li><li>檔案類型：PNG、JPG 或 JPEG</li></ul>|

### <a name="brand-image-for-company-portal"></a>公司入口網站的品牌影像

顯示反映您公司品牌的品牌影像。 儲存變更之後，可以選擇刀鋒視窗頂端的 [在 Intune Web 入口網路中預覽您的設定]  來查看您的設定。 請注意，您只能在 iOS 裝置上預覽品牌影像，而無法在 Intune Web 入口網站中進行預覽。 

|欄位名稱|詳細資訊|
|---|---|
|**上傳您的品牌影像**| 此選項可讓您顯示品牌形象。 在 iOS 公司入口網站中，它會顯示為使用者設定檔頁面上的背景影像。<p><ul><li>建議影像寬度：大於 1125 像素 (必須至少為 650 像素)</li><li>影像大小上限：1.3 MB</li><li>檔案類型：PNG、JPG 或 JPEG</li></ul>|

正確的品牌影像可讓公司品牌留下強烈印象，因而加強使用者對公司入口網站的信任。 以下是您擷取、選擇及最佳化公司入口網站影像時可能想要考慮的一些祕訣。 

- 連絡您的行銷或美術部門。 他們可能已有一組經核准的品牌影像。 他們也可協助您視需要最佳化影像。 

- 請同時考慮橫向和直向構圖。 影像在焦點周圍應該有足夠的背景。 影像可能會因裝置大小、方向與平台而有不同的裁剪方式。 

- 避免使用一般內建影像。 影像應該反映您公司的品牌，而且對您的使用者並不陌生。 如果您沒有影像，與其使用對使用者不具任何意義的一般影像，不如不要使用影像。 

- 移除不必要的中繼資料。 影像檔可能隨附中繼資料，例如相機設定檔、地理位置、標題、字幕等。 請使用影像最佳化工具去除這項資訊來維護品質，同時符合檔案大小限制。 

當 Intune 中的品牌影像新增或變更時，使用者可能不會在 iOS 裝置上看到變更，直到「公司入口網站」已在啟動時發現變更，然後重新啟動以顯示品牌影像。 

### <a name="brand-image-examples"></a>品牌影像範例

下列影像顯示範例 iPad 品牌影像：

![範例 iPhone 品牌影像的螢幕擷取畫面](./media/company-portal-app/company-portal-app-03.png)

下列影像顯示範例 iPhone 品牌影像：

![範例 iPad 品牌影像的螢幕擷取畫面](./media/company-portal-app/company-portal-app-02.png)

## <a name="privacy-statement-customization"></a>隱私權聲明自訂

您可以在受控 iOS 裝置上自訂要針對貴組織顯示的隱私權聲明。 此訊息會列出貴組織無法在受控 iOS 裝置上查看或執行的項目。

在[公司入口網站自訂]   > [裝置管理與隱私權訊息]  底下，您可以：

- 接受 [預設]  以使用顯示的清單，或
- 選擇 [自訂]  ，以自訂貴組織無法在受控 iOS 裝置上查看或執行的項目。 您可以使用 [Markdown](https://daringfireball.net/projects/markdown/) \(英文\) 來加入項目符號、粗體、斜體和連結。

## <a name="company-portal-derived-credentials-for-ios-devices"></a>適用於 iOS 裝置的公司入口網站衍生認證
Intune 支援個人識別驗證 (PIV) 和一般存取卡 (CAC) 衍生認證，與認證提供者 DISA Purebred、Entrust Datacard 和 Intercede 合作。 終端使用者將會完成其 iOS 裝置註冊後的其他步驟，以在公司入口網站應用程式中驗證其身分識別。 系統會先為您的租使用者設定認證提供者，並針對使用者或裝置將使用衍生認證的設定檔設為目標，以啟用衍生認證。

> [!NOTE]
> 使用者會根據您透過 Intune 指定的連結，看到衍生認證的相關指示。

如需 iOS 裝置之衍生認證的詳細資訊，請參閱[在 Microsoft Intune 中使用衍生認證](~/protect/derived-credentials.md)。

## <a name="windows-company-portal-keyboard-shortcuts"></a>Windows 公司入口網站鍵盤快速鍵

終端使用者可以在 Windows 公司入口網站中使用鍵盤快速鍵觸發導覽、應用程式與裝置動作。

您可以在 Windows 公司入口網站應用程式中使用下列鍵盤快速鍵。

| 區域 | 說明 | 鍵盤快速鍵 |
|:------------------:|:--------------:|:-----------------:|
| 導覽功能表 | 導覽 | Alt+M |
|  | 首頁 | Alt+H |
|  | 所有應用程式 | Alt+A |
|  | 已安裝的應用程式 | Alt+I |
|  | 傳送意見反應 | Alt+F |
|  | 我的設定檔 | Alt+U |
|  | 設定 | Alt+T |
| 首頁 - 裝置磚 | 重新命名 | F2 |
|  | 移除 | Ctrl+D 或 Delete |
|  | 檢查存取權 | Ctrl+M 或 F9 |
| 裝置詳細資訊 | 重新命名 | F2 |
|  | 移除 | Ctrl+D 或 Delete |
|  | 檢查存取權 | Ctrl+M 或 F9 |
| 應用程式詳細資料 | 安裝 | Ctrl+I |
| 裝置 | 可用 | Ctrl+D |

使用者也能夠在 Windows「公司入口網站」應用程式中看到可用的捷徑。

![Windows 公司入口網站中可用捷徑的螢幕擷取畫面](./media/company-portal-app/company-portal-app-01.png)

## <a name="user-self-service-device-actions-from-the-company-portal"></a>來自公司入口網站的使用者自助裝置動作

使用者可以透過公司入口網站應用程式或網站，在其本機裝置或遠端裝置上執行動作。 使用者可以執行的動作會根據裝置平台和設定而有所不同。 在所有情況下，只有裝置的主要使用者能夠執行遠端裝置動作。
- **淘汰**：從 Intune 管理移除裝置。 在公司入口網站應用程式和網站中，這會顯示為 [移除]  。
- **抹除**：此動作會起始裝置重設。 在公司入口網站中，這會顯示為 [重設]  ，或者，在 iOS 公司入口網站應用程式中，顯示為 [恢復出廠預設值]  。
- **重新命名**：此動作會變更使用者可以在公司入口網站中看到的裝置名稱。 它不會變更本機裝置名稱，只會變更公司入口網站中的清單。
- **同步處理**：此動作會使用 Intune 服務來起始裝置簽入。 這會在公司入口網站中顯示為 [檢查狀態]  。
- **遠端鎖定**：這會鎖定裝置，需要 PIN 才能將其解除鎖定。
- **重設密碼**：此動作會用來重設裝置密碼。 在 iOS 裝置上，將會移除密碼，而終端使用者將需在設定中輸入新密碼。 在支援的 Android 裝置上，Intune 會產生新密碼，並暫時顯示於公司入口網站中。
- **金鑰復原**：此動作是用來針對已加密的 macOS 裝置從「公司入口網站」網站復原個人復原金鑰。 

### <a name="self-service-actions"></a>自助動作

某些平台和設定不允許自助裝置動作。 下表提供自助動作的進一步詳細資料：

|  | Windows 10<sup>(3)</sup> | iOS/iPadOS<sup>(3)</sup> | MacOS<sup>(3)</sup><sup>(5)</sup> | Android<sup>(3)</sup> |
|----------------------|--------------------------|-------------------|-----------------------------------|-------------------------|
| 淘汰 | 可用<sup>(1)</sup> | 可用<sup>(8)</sup> | 可用 | 可用<sup>(7)</sup> |
| 抹除 | 可用 | 可用 | NA | 可用<sup>(7)</sup> |
| 重新命名<sup>(4)</sup> | 可用 | 可用<sup>(8)</sup> | 可用 | 可用 |
| 同步 | 可用 | 可用 | 可用 | 可用 |
| 遠端鎖定 | 僅限 Windows Phone | 可用 | 可用 | 可用 |
| 重設密碼 | 僅限 Windows Phone | 可用 | NA | 可用<sup>(6)</sup> |
| 金鑰修復 | NA | NA | 可用<sup>(2)</sup> | NA |
| 深色模式 | NA | 可用 | NA | NA |

<sup>(1)</sup> 在已加入 Azure AD 的 Windows 裝置上，一律會封鎖**淘汰**。<br>
<sup>(2)</sup> 只有透過 Web 入口網站才能使用 MacOS 的**金鑰復原**。<br>
<sup>(3)</sup> 如果使用裝置註冊管理員註冊，則會停用所有遠端動作。<br>
<sup>(4)</sup> **重新命名**只會變更公司入口網站應用程式或網站中的裝置名稱，而非裝置上的裝置名稱。<br>
<sup>(5)</sup> MacOS 裝置上無法使用**遠端抹除**。<br>
<sup>(6)</sup> 在某些 Android 和 Android Enterprise 設定上不支援**密碼重設**。 如需詳細資訊，請參閱[在 Intune 中重設或移除裝置密碼](../remote-actions/device-passcode-reset.md)。<br>
<sup>(7)</sup> **淘汰**和**抹除**不適用於 Android Enterprise 裝置擁有者案例 (COPE、COBO、COSU)。<br> 
<sup>(8)</sup> **淘汰** (移除裝置) 和**重新命名**適用於所有類型的註冊。 使用者註冊不支援其他動作。<br> 

## <a name="next-steps"></a>後續步驟

- [使用 Microsoft Intune 手動新增 Windows 10 公司入口網站應用程式](company-portal-app.md)
