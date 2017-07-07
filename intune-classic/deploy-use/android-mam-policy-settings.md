---
title: "Android MAM 原則設定"
description: "本主題說明適用於 Android 裝置的行動裝置應用程式管理原則設定。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 785e36bb9354e02e4040b5cf2271cbf6f10c4041
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="android-app-protection-policy-settings-in-microsoft-intune"></a>Microsoft Intune 的 Android 應用程式保護原則設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

您可以在 Azure 入口網站的 [設定] 刀鋒視窗上，[設定](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)本主題所述的應用程式原則設定。
原則設定分為「資料重新配置」和「存取」設定兩類。 在本主題中，_**受原則管理的應用程式**_一詞是指已設定應用程式保護原則的應用程式。

##  <a name="data-relocation-settings"></a>資料重新配置設定

| 設定 | 如何使用 | 預設值 |
|------|------|------|
| **禁止 Android 備份** | 選擇 [是] 防止這個應用程式將工作或學校資料備份至 [Android Backup Service](https://developer.android.com/google/backup/index.html)。選擇 [否] 允許這個應用程式備份工作或學校資料。| 是 |
| **允許應用程式將資料傳送到其他應用程式** | 指定可以接收這個應用程式資料的應用程式： <ul><li> **受原則管理的應用程式**：只允許傳送至其他受原則管理的應用程式。</li> <li>**所有應用程式**：允許傳送到任何應用程式。 </li> <li>**無**：不允許將資料傳送到任何應用程式 (包括其他受原則管理的應用程式)。</li></ul> <p>有一些 Intune 可以允許資料傳輸至其中的豁免應用程式和服務。 如需應用程式和服務的完整清單，請參閱[資料傳輸豁免](#Data-transfer-exemptions)。| 所有應用程式 |
| **允許應用程式接收來自其他應用程式的資料** | 指定可將資料傳送至這個應用程式的應用程式： <ul><li>**受原則管理的應用程式**：只允許從其他受原則管理的應用程式傳送。</li><li>**所有應用程式**：允許從任何應用程式傳送資料。</li><li>**無**：不允許從任何應用程式 (包括其他受原則管理的應用程式) 傳送資料。 </li></ul> <p>有一些 Intune 可以允許從中進行資料傳輸的豁免應用程式和服務。 如需應用程式和服務的完整清單，請參閱[資料傳輸豁免](#Data-transfer-exemptions)。 | 所有應用程式 |
| **不可進行另存新檔** | 選擇 [是]，在這個應用程式中停用 [另存新檔] 選項。 如果您想要允許使用 [另存新檔]，請選擇 [否]。 <p><br>**選取要用於儲存公司資料的儲存體服務** <br>使用者可以儲存到幾個選取的服務 (商務用 OneDrive、SharePoint 和本機存放區)。 將會封鎖所有其他服務。</p> | 否 <br><br> 0 (已選取) |
| **限制與其他應用程式的剪下、複製和貼上** | 指定何時剪下、複製和貼上動作可與這個應用程式搭配使用。 從下列選項進行選擇： <ul><li>**封鎖**：不允許在這個應用程式與任何其他應用程式之間進行剪下、複製和貼上動作。</li><li>**受原則管理的應用程式**：允許在這個應用程式與其他受原則管理的應用程式之間進行剪下、複製和貼上動作。</li><li>**具有貼上的受原則管理的應用程式**：允許在這個應用程式與其他受原則管理的應用程式之間進行剪下或複製。 允許將資料從任何應用程式貼入這個應用程式。</li><li>**任何應用程式**：不限制與這個應用程式之間的剪下、複製和貼上。 | 任何應用程式 |
|**限制 Web 內容以顯示於受管理的瀏覽器中** | 選擇 [是]，強制在 Managed Browser 應用程式中開啟應用程式中的網頁連結。 <br><br> 針對未在 Intune 中註冊的裝置，受原則管理應用程式中的網頁連結只能在 Managed Browser 應用程式中開啟。 <br><br> 如果您使用 Intune 管理裝置，請參閱[透過 Microsoft Intune 使用受管理的瀏覽器原則管理網際網路存取](manage-internet-access-using-managed-browser-policies.md)。 | 否 |
| **加密應用程式資料** | 選擇 [是]，啟用這個應用程式中工作或學校資料的加密。 Intune 可搭配使用 OpenSSL 128 位元 AES 加密配置與 Android 金鑰儲存區系統，安全地加密應用程式資料。 資料會在檔案 I/O 工作期間，以同步方式加密。 裝置儲存空間上的內容將一律加密。 <br><br> 加密方法**未**經 FIPS 140-2 認證。  | 是 |
| **停用連絡人同步** | 選擇 [是]，防止應用程式將資料儲存至裝置上的原生「連絡人」應用程式。 如果您選擇 [否]，則應用程式可以將資料儲存至裝置上的原生「連絡人」應用程式。 <br><br>當您執行選擇性抹除以移除應用程式中的工作或學校資料時，會移除直接從應用程式同步到原生「連絡人」應用程式的連絡人。 無法清除從原生通訊錄同步處理到其他外部來源的任何連絡人。 目前這僅適用於 Microsoft Outlook 應用程式。 | 否 |
| **停用列印** | 選擇 [是]，防止應用程式列印工作或學校資料。 | 否 |

  >[!NOTE]
  >[加密應用程式資料] 設定的加密方法**未**經 FIPS 140-2 認證。


  ## <a name="data-transfer-exemptions"></a>資料傳輸豁免

  有一些 Intune 應用程式保護原則可以允許豁免應用程式和平台服務傳送和接收資料傳輸。 例如，Android 上所有啟用 Intune 的應用程式都必須能夠將資料傳輸至 Google 文字轉換語音並從中傳輸資料，因此可以大聲讀出您行動裝置螢幕中的文字。 這份清單可能隨時變更，並反映視為對安全產能有所幫助的服務和應用程式。

  ### <a name="full-exemptions"></a>完整豁免

  這些應用程式和服務完全可以接收和傳送 Intune 管理應用程式的資料傳輸。

  |應用程式/服務名稱 | 描述 |
  | ------ | ---- |
  | com.android.phone | 原生 Phone 應用程式
  | com.android.vending | Google Play 商店 |
  | com.android.documentsui | Android 文件選擇器|
  | com.google.android.webview | [WebView](https://developer.android.com/reference/android/webkit/WebView.html)，這是許多應用程式 (包括 Outlook) 的必要項目。 |
  | com.android.webview |[WebView](https://developer.android.com/reference/android/webkit/WebView.html)，這是許多應用程式 (包括 Outlook) 的必要項目。|
  | com.google.android.tts | Google 文字轉換語音 |
  | com.android.providers.settings | Android 系統設定 |
  | com.azure.authenticator | Azure Authenticator 應用程式，這是許多情況下成功驗證的必要項目。 |
  | com.microsoft.windowsintune.companyportal | Intune 公司入口網站|

  ### <a name="conditional-exemptions"></a>條件式豁免
  只有在特定情況下，這些應用程式和服務才能接收和傳送 Intune 管理應用程式的資料傳輸。

  |應用程式/服務名稱 | 描述 | 豁免條件|
  | ------ | ---- | --- |
  | com.android.chrome | Google Chrome 瀏覽器 | Chrome 用於 Android 7.0+ 上的一些 WebView 元件，而且絕不會隱藏，可供檢視。 不過，一律會限制送至應用程式的資料流程以及接收來自其中的資料流程。
  | com.skype.raider | Skype | Skype 應用程式只適用於導致通話的特定動作。 |
  | com.android.providers.media | Android 媒體內容提供者 | 只允許進行鈴聲選取動作的媒體內容提供者。 |
  | com.google.android.gms; com.google.android.gsf | Google Play Services 套件 | 這些套件允許用於 Google Cloud Messaging 動作 (例如推送通知)。 |



##  <a name="access-settings"></a>存取設定

| 設定 | 如何使用 | 預設值 |
|------|------|------|
| **需要 PIN 碼才可存取** | 選擇 [是]，需要 PIN 才能使用這個應用程式。 使用者第一次在工作或學校內容中執行應用程式時，系統會提示他們設定這個 PIN。 預設值 = [是]。<br><br> 進行下列 PIN 強度設定： <ul><li>**PIN 碼重設前的嘗試次數**：指定使用者必須嘗試順利輸入幾次其 PIN 後才能重設 PIN。 預設值 = **5**。</li><li> **允許簡單的 PIN**：選擇 [是]，允許使用者使用簡單的 PIN 序列 (例如 1234 或 1111)。 選擇 [否]，防止其使用簡單的序號。 預設值 = [是]。 </li><li> **PIN 長度**：指定 PIN 序列的最小位數。 預設值 = **4**。 </li><li> **允許指紋而非 PIN (Android 6.0+)**：選擇 [是]，讓使用者針對應用程式存取使用[指紋驗證](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication)，而非 PIN。 預設值 = [是]。</li></ul> 在 Android 裝置上，您可以讓使用者使用 [Android fingerprint authentication](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) (Android 指紋驗證) 而非 PIN 來證明其身分識別。 使用者嘗試使用自己的工作或學校帳戶來使用這個應用程式時，系統會提示他們提供自己的指紋識別，而不是輸入 PIN。 </li></ul>| 需要 PIN 碼：是 <br><br> PIN 碼重設嘗試次數：5 <br><br> 允許簡單的 PIN：是 <br><br> PIN 長度：4 <br><br> 允許指紋：是 |
| **需要公司認證才能存取** | 選擇 [是]，需要使用者使用工作或學校帳戶登入來進行應用程式存取，而不是輸入 PIN。 如果您設定為 [是]，則會覆寫 PIN 或 Touch ID 的需求。  | 否 |
| **封鎖在已進行 JB 或 Root 破解的裝置上執行受管理的應用程式** |選擇 [是]，防止在已進行 JB 或 Root 破解的裝置上執行這個應用程式。 使用者仍然可以繼續使用這個應用程式來執行個人工作，但必須使用不同的裝置來存取這個應用程式中的工作或學校資料。 | 是 |
| **重新檢查存取需求前等候時間 (分鐘)** | 進行以下設定： <ul><li>**逾時**︰這是重新檢查存取需求 (稍早定義於原則中) 前經過的分鐘數。 例如，當系統管理員開啟原則中的 PIN 時，若使用者開啟 MAM 應用程式，則必須輸入 PIN。 如果使用這項設定，使用者在 **30 分鐘** (預設值) 內都不需要在任何 MAM 應用程式上輸入 PIN。</li><li>**離線寬限期**：這是 MAM 應用程式可離線執行的分鐘數，指定經過多少時間 (分鐘) 之後即會重新檢查應用程式存取需求。 預設值 = **720** 分鐘 (12 小時)。 到期後，應用程式將會要求使用者驗證至 AAD，以便應用程式可以繼續執行。</li></ul>| 逾時：30 <br><br> 離線：720 |
| **離線間隔幾天後抹除 App 資料** | 在離線執行達到此天數 (由系統管理員定義) 之後，應用程式本身會執行選擇性抹除。 此選擇性抹除與系統管理員在 MAM 抹除工作流程中起始的抹除相同。 <br><br> | 90 天 |
| **封鎖螢幕擷取及 Android 助手 (Android 6.0+)** | 選擇 [是]，在使用這個應用程式時封鎖裝置的螢幕擷取和 [Android 助手] 功能。 選擇 [是]，也會在搭配使用這個應用程式與工作或學校帳戶時模糊應用程式切換器預覽影像。 | 否 |
| **當裝置 PIN 受到管理時，停用應用程式 PIN** | 選擇 [是] 以在已註冊裝置上偵測到裝置鎖定時停用應用程式 PIN。 | 否 |
