---
title: Android 應用程式防護原則設定 | Microsoft Intune
titlesuffix: Microsoft Intune
description: 本主題說明 Android 裝置的應用程式防護原則設定。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9e9ef9f5-1215-4df1-b690-6b21a5a631f8
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 8505560527a8ea1b5d75eef5f7c3423d6a2d6a7d
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53817393"
---
# <a name="android-app-protection-policy-settings-in-microsoft-intune"></a>Microsoft Intune 的 Android 應用程式保護原則設定
本文描述 Android 裝置的應用程式防護原則設定。 您可以在 Azure 入口網站的 [設定] 刀鋒視窗上，為應用程式防護原則[設定](app-protection-policies.md)所述的原則設定。
原則設定有兩個類別：「資料保護設定」和「存取設定」。 在本文中「受原則管理的應用程式」一詞是指設有應用程式保護原則的應用程式。

##  <a name="data-protection-settings"></a>資料保護設定

| 設定 | 如何使用 | 預設值 |
|------|------|------|
| **禁止 Android 備份** | 選取 [是]，防止此應用程式將公司或學校資料備份至 [Android 備份服務](https://developer.android.com/google/backup/index.html)。<br><br> 選取 [否]，允許此應用程式備份公司或學校資料。| 是 |
| **允許應用程式將資料傳送到其他應用程式** | 指定可以接收這個應用程式資料的應用程式： <ul><li> **受原則管理的應用程式**：只允許傳送至其他受原則管理的應用程式。</li> <li>**所有應用程式**：允許傳送到任何應用程式。 </li> <li>**無**：不允許將資料傳送到任何應用程式 (包括其他受原則管理的應用程式)。</li></ul> <p>有一些 Intune 可預設允許資料傳送至其中的豁免應用程式和服務。 此外，如果您需要允許資料傳送至不支援 Intune 應用程式的應用程式，您可以建立您自己的豁免設定。 請參閱[資料傳輸豁免](#Data-transfer-exemptions)以取得詳細資訊。<p>此原則也適用於 Android 應用程式連結。  一般 Web 連結則是由 [限制與其他應用程式的 Web 內容傳輸] 原則設定所管理。<p>**注意︰** Intune 目前不支援 Android Instant Apps 功能。 Intune 會封鎖與應用程式之間的任何資料連接。  如需 [Android Instant Apps](https://developer.android.com/topic/instant-apps/index.html) 的詳細資訊，請參閱 Android 開發人員文件。</p>| 所有應用程式 |
| **允許應用程式接收來自其他應用程式的資料** | 指定可將資料傳送至這個應用程式的應用程式： <ul><li>**受原則管理的應用程式**：只允許從其他受原則管理的應用程式傳送。</li><li>**所有應用程式**：不允許從任何應用程式傳送資料。</li><li>**無**：不允許從任何應用程式 (包括其他受原則管理的應用程式) 傳送資料。 </li></ul> <p>有一些 Intune 可以允許從中進行資料傳輸的豁免應用程式和服務。 如需應用程式和服務的完整清單，請參閱[資料傳輸豁免](#Data-transfer-exemptions)。 | 所有應用程式 |
| **不可進行另存新檔** | 選擇 [是]，在這個應用程式中停用 [另存新檔] 選項。 如果您想要允許使用 [另存新檔]，請選擇 [否]。 **注意︰** Microsoft Excel、OneNote、PowerPoint 和 Word 支援此設定。 協力廠商和 LOB 應用程式也可能支援此設定。 <p>**選取要用於儲存公司資料的儲存體服務** <br>使用者可以儲存到幾個選取的服務 (商務用 OneDrive、SharePoint 和本機存放區)。 將會封鎖所有其他服務。</p> | 否<p>&nbsp;</p><p>&nbsp;</p>0 (已選取) |
| **限制與其他應用程式的剪下、複製和貼上** | 指定何時剪下、複製和貼上動作可與這個應用程式搭配使用。 從下列選項進行選擇： <ul><li>**封鎖**：不允許在這個應用程式與任何其他應用程式之間進行剪下、複製和貼上動作。</li><li>**受原則管理的應用程式**：允許在這個應用程式與其他受原則管理的應用程式之間進行剪下、複製和貼上動作。</li><li>**具有貼上的受原則管理的應用程式**：允許在這個應用程式與其他受原則管理的應用程式之間進行剪下或複製。 允許將資料從任何應用程式貼入這個應用程式。</li><li>**任何應用程式**：不限制與這個應用程式之間的剪下、複製和貼上。 | 任何應用程式 |
|**限制與其他應用程式的 Web 傳輸** | 指定如何從原則受控的應用程式開啟 Web 內容 (HTTP/HTTPS 連結)。 從下列選項進行選擇：<ul><li>**受原則管理的瀏覽器**：只允許在原則受控的瀏覽器中開啟 Web 內容。</li><li>**任何應用程式**：允許任何應用程式中的 Web 連結 </li></ul><br><br> 如果您使用 Intune 管理裝置，請參閱[透過 Microsoft Intune 使用受控的瀏覽器原則管理網際網路存取](app-configuration-managed-browser.md)。<br><br>**原則受控的瀏覽器**<br>如果您部署多個原則受控的瀏覽器，則只會啟動其中一個。  啟動順序依序為 Intune Managed Browser 和 Microsoft Edge。  在 Android 上，如果未安裝 Intune Managed Browser 或 Microsoft Edge，您的終端使用者可以從支援 HTTP/HTTPS 連結的其他原則受控應用程式中進行選擇。<p>如果原則受控的瀏覽器為必要但尚未安裝，則會提示您的終端使用者安裝 Intune Managed Browser。<p>如果原則受控的瀏覽器為必要，則 Android 應用程式連結是由 [允許應用程式將資料傳送至其他應用程式] 原則設定所管理。<p>**Intune 裝置註冊**<br>如果您使用 Intune 來管理裝置，請參閱＜透過 Microsoft Intune 使用受控瀏覽器原則管理網際網路存取＞。 <p>**原則受控的 Microsoft Edge**<br>適用於行動裝置 (iOS 和 Android) 的 Microsoft Edge 瀏覽器支援 Intune 應用程式保護原則。 使用其公司 Azure AD 帳戶登入 Microsoft Edge 瀏覽器應用程式的使用者，將會受到 Intune 的保護。 Microsoft Edge 瀏覽器可整合 MAM SDK，並支援其所有的資料保護原則，但會防止：<br><ul><li>**另存新檔**：Microsoft Edge 瀏覽器不允許使用者將直接的應用程式內連線新增至雲端儲存體提供者 (例如 OneDrive)。</li><li>**連絡人同步**：Microsoft Edge 瀏覽器不會儲存至原生連絡人清單。</li></ul><br>**注意**：<br>應用程式 SDK 無法判斷目標應用程式是否為瀏覽器。 在 Android 裝置上，允許支援 HTTP/HTTPS 意圖的其他受控瀏覽器應用程式。 | 任何應用程式 |
| **加密應用程式資料** | 選擇 [是]，啟用這個應用程式中工作或學校資料的加密。 Intune 可搭配使用 OpenSSL 256 位元 AES 加密配置與 Android 金鑰儲存區系統，安全地加密應用程式資料。 資料會在檔案 I/O 工作期間，以同步方式加密。 裝置儲存空間上的內容將一律加密。 SDK 將繼續提供 128 位元金鑰的支援，以取得與使用較舊 SDK 版本之內容和應用程式的相容性。 <br><br> 加密方法**未**經 FIPS 140-2 認證。  | 是 |
| **在裝置加密已啟用時停用應用程式加密** | 選擇 [是]，在註冊的裝置上偵測到裝置加密時停用內部應用程式的應用程式加密。 <br><br>**注意︰** Intune 只能偵測已註冊 Intune MDM 的裝置。 外部應用程式儲存空間仍會加密，以確保未受管理的應用程式無法加以存取。 | 是 |
| **停用連絡人同步** | 選擇 [是]，防止應用程式將資料儲存至裝置上的原生「連絡人」應用程式。 如果您選擇 [否]，則應用程式可以將資料儲存至裝置上的原生「連絡人」應用程式。 <br><br>當您執行選擇性抹除以移除應用程式中的工作或學校資料時，會移除直接從應用程式同步到原生「連絡人」應用程式的連絡人。 無法清除從原生通訊錄同步處理到其他外部來源的任何連絡人。 目前這僅適用於 Microsoft Outlook 應用程式。 | 否 |
| **停用列印** | 選擇 [是]，防止應用程式列印工作或學校資料。 | 否 |

  >[!NOTE]
  >[加密應用程式資料] 設定的加密方法**未**經 FIPS 140-2 認證。

  ## <a name="data-transfer-exemptions"></a>資料傳輸豁免

  有一些 Intune 應用程式保護原則可以允許豁免應用程式和平台服務傳送和接收資料傳輸。 例如，Android 上所有 Intune 受控應用程式都必須能夠將資料傳輸至 Google 文字轉換語音並從中傳輸資料，因此可以大聲讀出您行動裝置螢幕中的文字。 這份清單可能隨時變更，並反映視為對安全產能有所幫助的服務和應用程式。

  ### <a name="full-exemptions"></a>完整豁免

  這些應用程式和服務完全可以接收和傳送 Intune 管理應用程式的資料傳輸。

  |應用程式/服務名稱 | 說明 |
  | ------ | ---- |
  | com.android.phone | 原生 Phone 應用程式
  | com.android.vending | Google Play 商店 |
  | com.android.documentsui | Android 文件選擇器|
  | com.google.android.webview | [WebView](https://developer.android.com/reference/android/webkit/WebView.html)，這是許多應用程式 (包括 Outlook) 的必要項目。 |
  | com.android.webview |[WebView](https://developer.android.com/reference/android/webkit/WebView.html)，這是許多應用程式 (包括 Outlook) 的必要項目。|
  | com.google.android.tts | Google 文字轉換語音 |
  | com.android.providers.settings | Android 系統設定 |
  | com.android.settings | Android 系統設定 |
  | com.azure.authenticator | Azure Authenticator 應用程式，這是許多情況下成功驗證的必要項目。 |
  | com.microsoft.windowsintune.companyportal | Intune 公司入口網站|

  ### <a name="conditional-exemptions"></a>條件式豁免
  只有在特定情況下，這些應用程式和服務才能接收和傳送 Intune 管理應用程式的資料傳輸。

  |應用程式/服務名稱 | 說明 | 豁免條件|
  | ------ | ---- | --- |
  | com.android.chrome | Google Chrome 瀏覽器 | Chrome 用於 Android 7.0+ 上的一些 WebView 元件，而且絕不會隱藏，可供檢視。 不過，一律會限制送至應用程式的資料流程以及接收來自其中的資料流程。  |
  | com.skype.raider | Skype | Skype 應用程式只適用於導致通話的特定動作。 |
  | com.android.providers.media | Android 媒體內容提供者 | 只允許進行鈴聲選取動作的媒體內容提供者。 |
  | com.google.android.gms; com.google.android.gsf | Google Play Services 套件 | 這些套件允許用於 Google Cloud Messaging 動作 (例如推送通知)。 |

如需詳細資訊，請參閱[應用程式的資料傳輸原則例外狀況](app-protection-policies-exception.md)。

##  <a name="access-settings"></a>存取設定

| 設定 | 如何使用 |  
|------|------| 
| **需要 PIN 碼才可存取** | 選取 [是]，需要 PIN 才能使用此應用程式。 使用者第一次在工作或學校內容中執行應用程式時，系統會提示他們設定這個 PIN。 <br><br> 預設值 = [是]。<br><br> 進行下列 PIN 強度設定： <br> <ul><li>**選取類型：** 先設定數值或密碼類型的 PIN 需求，再存取已套用應用程式保護原則的應用程式。 數值需求只有數字，密碼則至少要以 1 個字母**或**至少要以 1 個特殊字元定義。 <br><br> 預設值 = **數值**<br><br> **注意︰** 允許的特殊字元包括 Android 英文鍵盤上的特殊字元和符號。</li></ul>  <ul><li>**PIN 重設之前的嘗試次數：** 指定使用者必須重設之前，使用者必須成功輸入 PIN 的嘗試次數。 <br><br> 預設值 = **5** </li> <br> <li> **允許簡單的 PIN：** 選取 [是] 以允許使用者使用簡單的 PIN 序列 (例如 *1234*、*1111*、*abcd* 或 *aaaa*)。 選取 [否]，防止其使用簡單的序列。 <br><br>預設值 = [是] <br><br>**注意︰** 如果已設定密碼類型 PIN，而且 [允許簡單的 PIN] 已設定為 [是]，則使用者的 PIN 中需要至少有一個字母**或**至少一個特殊字元。 如果已設定密碼類型 PIN，而且 [允許簡單的 PIN] 已設定為 [否]，則使用者的 PIN 中需要至少一個數字**和**一個字母**和**至少一個特殊字元。* </li> <br> <li>  **PIN 長度：** 指定 PIN 序列的最小位數。 <br><br>預設值 = **4** </li> <br> <li> **允許指紋而非 PIN (Android 6.0+)：** 選取 [是] 以允許使用者針對應用程式存取使用[指紋驗證](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) \(英文\) 而非 PIN。 <br><br>預設值 = [是] <br><br>**注意︰** 此功能支援 Android 裝置上的生物特徵辨識通用控制項。 「不支援」OEM 特定的生物特徵辨識設定，例如 * Samsung。*。* <br><br>在 Android 上，您可以讓使用者使用 [Android 指紋驗證](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication)而非 PIN 來證明其身分識別。 使用者嘗試使用自己的公司或學校帳戶來使用這個應用程式時，系統會提示他們提供自己的指紋識別，而不是輸入 PIN。 <br><br> Android 工作設定檔必須註冊個別指紋，才能強制執行**允許指紋而非 PIN** 原則。 此原則僅針對 Android 工作設定檔中安裝的原則管理應用程式生效。 藉著在公司入口網站中註冊而建立 Android 工作設定檔之後，個別指紋必須在裝置上註冊。 如需使用 Android 工作設定檔的工作設定檔指紋詳細資訊，請參閱[鎖定您的工作資料夾](https://support.google.com/work/android/answer/7029958)。| 
| **需要公司認證才能存取** | 選擇 [是]，需要使用者使用工作或學校帳戶登入來進行應用程式存取，而不是輸入 PIN。 當設定為 [是] 且已開啟 PIN 或生物識別登入提示時，會顯示公司認證以及 PIN 或生物識別登入提示。 <br><br>預設值 = 否 |
| **重新檢查存取需求前等候時間 (分鐘)** | 進行下列設定： <ul><li>**逾時**︰這是重新檢查存取需求 (稍早定義於原則中) 前經過的分鐘數。 例如，若管理員在原則中開啟 PIN 及「封鎖已 Root 破解的裝置」，則當使用者開啟 Intune 受控應用程式時，就必須輸入 PIN 並在未 Root 破解的裝置上使用應用程式。 當使用這項設定時，使用者在等於設定值的時段內都不需要在任何 Intune 受控應用程式上輸入 PIN 或接受另一次 Root 偵測檢查。  <br><br>此原則設定格式支援正整數。 <br><br> 預設值 = **30 分鐘** <br><br> **注意︰** 在 Android 上，PIN 會在所有 Intune 受控應用程式間共用。 當裝置上的應用程式離開前景時，PIN 計時器就會重設。 在此設定中所定義的逾時持續時間內，使用者不需要在任何共用 PIN 的 Intune 受控應用程式上輸入 PIN。* <br><br></li> |
| **封鎖螢幕擷取及 Android 助手** | 選取 [是]，在使用這個應用程式時封鎖裝置的螢幕擷取和 [Android 助手] 功能。 選擇 [是]，也會在搭配使用這個應用程式與工作或學校帳戶時模糊應用程式切換器預覽影像。 <br><br>預設值 = 否 |


> [!NOTE]  
> 若要深入了解在同一應用程式和使用者集合的 [存取] 區段中設定的多個 Intune 應用程式保護設定如何在 Android 上運作，請參閱 [Intune MAM 常見問題集](mam-faq.md)與[在 Intune 中使用應用程式防護原則的存取動作選擇性地抹除資料](app-protection-policies-access-actions.md)。


## <a name="conditional-launch"></a>條件式啟動
設定條件式啟動設定，以設定您存取保護原則的登入安全性需求。 

根據預設，有數個設定會提供預先設定的值和動作。 您可以刪除某些設定，例如「最低 OS 版本」。 您也可以從 [選取一個] 下拉式清單中選取其他設定。 

| 設定 | 如何使用 |  
|---------|------------| 
| **PIN 嘗試次數上限** | 指定在執行已設定動作之前，使用者必須成功輸入 PIN 的嘗試次數。 此原則設定格式支援正整數。 「動作」包括： <br><ul><li>**重設 PIN** - 使用者必須重設其 PIN。</li></ul> <ul><li>**抹除資料** - 與應用程式建立關聯的使用者帳戶會從裝置抹除。  </li></ul> </li></ul> 預設值 = **5** |
| **離線寬限期** | MAM 應用程式可以離線執行的分鐘數。 指定經過多少時間 (分鐘) 之後即會重新檢查應用程式存取需求。 「動作」包括： <br><ul><li>**封鎖存取 (分鐘)**：MAM 應用程式可以離線執行的分鐘數。 指定經過多少時間 (分鐘) 之後即會重新檢查應用程式存取需求。 在這段期間過後，應用程式必須進行 Azure Active Directory (Azure AD) 的使用者驗證，如此應用程式才能繼續執行。 <br><br>此原則設定格式支援正整數。 <br><br>預設值 = **720** 分鐘 (12 小時) </li></ul> <ul><li>**抹除資料 (天)** - 在離線執行達到此天數 (由系統管理員定義) 之後，應用程式需要使用者連線到網路並重新驗證。 如果使用者成功驗證，就可以繼續存取其資料，而且會重設離線間隔。  如果使用者無法驗證，應用程式會執行使用者帳戶和資料的選擇性抹除。 如需詳細資訊，請參閱[如何僅抹除 Intune 受控應用程式中的公司資料](https://docs.microsoft.com/intune/apps-selective-wipe)。</li></ul> 此原則設定格式支援正整數。 <br><br>  預設值 = **90 天** </li></ul>  此項目可以出現多次，每個執行個體支援不同的動作。 |   
| **已越獄或 Root 破解的裝置** |這項設定沒有可設定的值。 「動作」包括： <br><ul><li>**封鎖存取** - 防止在已越獄或 Root 破解的裝置上執行此應用程式。 使用者仍然可以繼續使用這個應用程式來執行個人工作，但必須使用不同裝置來存取這個應用程式中的工作或學校資料。</li></ul> <ul><li>**抹除資料** - 與應用程式建立關聯的使用者帳戶會從裝置抹除。  </li></ul> |
| **最低 OS 版本** | 指定要求使用此應用程式的最低 Android 作業系統。 「動作」包括： <br><ul><li>**警告** - 如果裝置上的 Android 版本不符合需求，使用者將會看見通知。 此通知可以關閉。  </li></ul> <ul><li>**封鎖存取** - 如果裝置上的 Android 版本不符合需求，將會禁止使用者存取。</li></ul> <ul><li>**抹除資料** - 與應用程式建立關聯的使用者帳戶會從裝置抹除。  </li></ul> </li></ul>此原則設定格式支援 major.minor、major.minor.build、major.minor.build.revision。 |
| **最低應用程式版本** | 指定作業系統最小值。 「動作」包括： <br><ul><li>**警告** - 如果裝置上的應用程式版本不符合需求，使用者會看見通知。 此通知可以關閉。</li></ul> <ul><li>**封鎖存取** - 如果裝置上的應用程式版本不符合需求，會封鎖使用者進行存取。 </li></ul> <ul><li>**抹除資料** - 與應用程式建立關聯的使用者帳戶會從裝置抹除。 </li></ul> </li></ul> 因為應用程式之間通常會有不同的版本控制配置，所以請建立包含一個針對單一應用程式之最低應用程式版本的原則 (例如，「Outlook 版本原則」)。<br><br> 此項目可以出現多次，每個執行個體支援不同的動作。<br><br> 此原則設定格式支援 major.minor、major.minor.build、major.minor.build.revision。|
| **最低修補程式版本** | 要求裝置具有由 Google 發行的最低 Android 安全性修補程式。  <br><ul><li>**警告** - 如果裝置上的 Android 版本不符合需求，使用者將會看見通知。 此通知可以關閉。  </li></ul> <ul><li>**封鎖存取** - 如果裝置上的 Android 版本不符合需求，將會禁止使用者存取。</li></ul> <ul><li>**抹除資料** - 與應用程式建立關聯的使用者帳戶會從裝置抹除。  </li></ul></li></ul> 此原則設定支援 *YYYY-MM-DD* 的日期格式。 |
| **裝置製造商** | 指定使用此應用程式所需的裝置製造商。 「動作」包括： <br><ul><li>**允許指定 (封鎖非指定)** - 僅有符合指定製造商的裝置可以使用應用程式。 會封鎖所有其他裝置。 </li></ul> <ul><li>**允許指定 (抹除非指定)** - 與應用程式建立關聯的使用者帳戶會從裝置抹除。 </li></ul> |
