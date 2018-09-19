---
title: iOS 應用程式保護原則設定
titlesuffix: Microsoft Intune
description: 本主題描述 iOS 裝置的應用程式保護原則設定。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0f8b08f2-504c-4b38-bea2-b8a4ef0526b8
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bc38ae71a26081696574ff3fe854f86ebac663ce
ms.sourcegitcommit: 8fdddb684ecf5eabf071907168413bcd89a2f702
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44141655"
---
#  <a name="ios-app-protection-policy-settings"></a>iOS 應用程式保護原則設定
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

您可以為 Azure 入口網站的 [新增原則] > [設定] 刀鋒視窗上的應用程式保護原則，[設定](app-protection-policies.md)本主題中所述的原則設定。

原則設定分為「資料重新配置」和「存取」設定兩類。 在本主題中 [受原則管理的應用程式] 一詞是指設有應用程式保護原則的應用程式。

##  <a name="data-relocation-settings"></a>資料重新配置設定

| 設定 | 如何使用 | 預設值 |
|------|------|------|
| **禁止 iTunes 和 iCloud 備份** | 選擇 [是]，防止這個應用程式將工作或學校資料備份至 iTunes 和 iCloud。 選擇 [否]，允許這個應用程式將工作或學校資料備份至 iTunes 和 iCloud。| 是 |
| **允許應用程式將資料傳送到其他應用程式** | 指定可以接收這個應用程式資料的應用程式： <ul><li> **受原則管理的應用程式**：只允許傳送至其他受原則管理的應用程式。</li> <li>**所有應用程式**：允許傳送到任何應用程式。 </li> <li>**無**：不允許將資料傳送到任何應用程式 (包括其他受原則管理的應用程式)。</li></ul>如果您將此設定設為 [受原則管理的應用程式]，則可以設定 [Filter Open-In/Share Dialog to only policy managed apps?] \(將開啟方式/共用對話方塊只篩選出受原則管理的應用程式嗎？\) 設定。 選擇 [是] 只在 Apple 的 [Open-In/Share] \(開啟方式/共用\) 對話方塊中顯示受控應用程式，以取得可搭配 iOS 上檔案/文件使用的應用程式。 **這也會停用 iOS 內的 [儲存到檔案] 選項** 選擇 [否] 以顯示裝置上可用來在 [Open-In/Share] \(開啟方式/共用\) 對話方塊中開啟檔案/文件的所有應用程式。 傳送至非受控應用程式的受控資料仍會予以加密。 <br><br>**注意：** 若要設定 [Open-In/Share] \(開啟方式/共用\) 對話方塊的篩選，則同時需要作為檔案/文件來源的應用程式，以及可開啟此檔案/文件來使用 Intune SDK for iOS 8.1.1 (含) 以上版本的應用程式。 預設值 = [否]。 <br><br> 此外，如果您將此設定設為 [受原則管理的應用程式] 或 [無]，則會封鎖 Spotlight 搜尋在應用程式中搜尋資料的 iOS 9 功能。 <p><p>此原則也會影響 Web 內容的行為。 如果此原則設定為 [封鎖]，使用者將無法開啟通往任何瀏覽器的 HTTP 連結，包括 Managed Browser。 此外，如果此原則設定為 [僅受原則管理]，HTTP 連結只能在 Managed Browser 中開啟。 <p> 有一些 Intune 可預設允許資料傳送至其中的豁免應用程式和服務。 此外，如果您需要允許資料傳送至不支援 Intune 應用程式的應用程式，您可以建立您自己的豁免設定。 請參閱[資料轉送豁免](#data-transfer-exemptions)以取得詳細資訊。 | 所有應用程式 |
| **允許應用程式接收來自其他應用程式的資料** | 指定可將資料傳送至這個應用程式的應用程式： <ul><li>**受原則管理的應用程式**：只允許從其他受原則管理的應用程式傳送。</li><li>**所有應用程式**：允許從任何應用程式傳送資料。</li><li>**無**：不允許從任何應用程式 (包括其他受原則管理的應用程式) 傳送資料。</li></ul> 有一些 Intune 可以允許從中進行資料傳輸的豁免應用程式和服務。 如需應用程式和服務的完整清單，請參閱[資料傳輸豁免](#data-transfer-exemptions)。 在未註冊的 iOS 裝置上，啟用多重身分識別 MAM 的應用程式會忽略此原則，並允許所有內送資料。 | 所有應用程式 |
| **不可進行另存新檔** | 選擇 [是]，在這個應用程式中停用 [另存新檔] 選項。 如果您想要允許使用 [另存新檔]，請選擇 [否]。 <p><br>**選取要用於儲存公司資料的儲存體服務** <br>使用者可以儲存到幾個選取的服務 (商務用 OneDrive、SharePoint 和本機存放區)。 將會封鎖所有其他服務。</p> | 否 <br><br> 0 (已選取) |
| **限制與其他應用程式的剪下、複製和貼上** | 指定何時剪下、複製和貼上動作可與這個應用程式搭配使用。 從下列選項進行選擇： <ul><li>**封鎖**：不允許在這個應用程式與任何其他應用程式之間進行剪下、複製和貼上動作。</li><li>**受原則管理的應用程式**：允許在這個應用程式與其他受原則管理的應用程式之間進行剪下、複製和貼上動作。</li><li>**具有貼上的受原則管理的應用程式**：允許在這個應用程式與其他受原則管理的應用程式之間進行剪下或複製。 允許將資料從任何應用程式貼入這個應用程式。</li><li>**任何應用程式**：不限制與這個應用程式之間的剪下、複製和貼上。 | 任何應用程式 |
|**限制 Web 內容以顯示於受管理的瀏覽器中** | 選擇 [是]，強制在 Managed Browser 應用程式中開啟應用程式中的網頁連結。 <br><br> 針對未在 Intune 中註冊的裝置，受原則管理應用程式中的網頁連結只能在 Managed Browser 應用程式中開啟。 <br><br> 如果您使用 Intune 管理裝置，請參閱[透過 Microsoft Intune 使用受管理的瀏覽器原則管理網際網路存取](app-configuration-managed-browser.md)。 <br><br> 適用於行動裝置 (iOS 和 Android) 的 Microsoft Edge 瀏覽器支援 Intune 應用程式保護原則。 使用其公司 Azure AD 帳戶登入 Edge 瀏覽器應用程式的使用者，將會受到 Intune 的保護。 Edge 瀏覽器可整合 MAM SDK，並支援其所有的資料保護原則，但會防止：<ul><li>**另存新檔**：Edge 瀏覽器不允許使用者將直接的應用程式內連線新增至雲端儲存體提供者 (例如 OneDrive)，而且不允許使用者將檔案下載至本機檔案系統。</li><li>**連絡人同步**：Edge 瀏覽器不會儲存至原生連絡人清單。</li></ul>Edge 瀏覽器會利用 Intune 原則的自動註冊。 這表示當裝置上的另一個 Microsoft 應用程式正由 Intune 原則管理時，Edge 瀏覽器會自動檢查是否有以 Edge 應用程式為目標的原則。 Intune 原則的自動註冊是由 MAM SDK 處理，因此無需任何應用程式參與。 | 否 |
| **加密應用程式資料** | 針對受原則管理的應用程式，使用 iOS 所提供的裝置層級加密配置來加密待用資料。 需要 PIN 時，會根據應用程式保護原則中的設定來加密資料。 <br><br> 前往[這裡](https://support.apple.com/HT202739)的正式 Apple 文件，來查看哪些 iOS 加密模組已經 FIPS 140-2 認證或擱置 FIPS 140-2 認證。 <br><br> 指定何時加密這個應用程式中的工作或學校資料。 從下列選項進行選擇： <ul><li>**是**：當裝置已鎖定且有 Intune 的應用程式層級加密保護時，與此原則相關的所有應用程式資料都會受到加密。 當您啟用此設定時，使用者可能必須設定並使用 PIN 才能存取其裝置。  如果不需要裝置 PIN 和加密，將不會開啟應用程式，而且會出現下列訊息提示使用者設定 PIN：「您的組織要求您先啟用裝置 PIN，才能存取此應用程式」。</li><li>**否**：Intune 不會強制加密。 | 是|
| **停用連絡人同步** | 選擇 [是]，防止應用程式將資料儲存至裝置上的原生「連絡人」應用程式。 如果您選擇 [否]，則應用程式可以將資料儲存至裝置上的原生「連絡人」應用程式。 <br><br>當您執行選擇性抹除以移除應用程式中的工作或學校資料時，會移除直接從應用程式同步到原生「連絡人」應用程式的連絡人。 無法清除從原生通訊錄同步處理到其他外部來源的任何連絡人。 目前這僅適用於 Microsoft Outlook 應用程式。 | 否 |
| **停用列印** | 選擇 [是]，防止應用程式列印工作或學校資料。 | 否 |
| **封鎖協力廠商鍵盤** | 選擇 [是] 以防止在受控應用程式中使用協力廠商鍵盤。 <br><br>啟用此設定時，使用者會收到一次性訊息，指出已封鎖使用協力廠商鍵盤。 當使用者第一次與需要使用鍵盤的組織資料互動時，就會顯示此訊息。 使用受控應用程式時，只能使用標準 iOS 鍵盤，其他鍵盤選項都會停用。 此設定不會影響在非受控應用程式中使用協力廠商鍵盤。 | 否 |

> [!NOTE]
> 沒有資料重新配置設定可以控制 iOS 裝置上的 Apple 受管理「開啟於」功能。 若要使用管理 Apple「開啟於」，請參閱[使用 Microsoft Intune 管理 iOS 應用程式之間的資料傳輸](data-transfer-between-apps-manage-ios.md)。

## <a name="data-transfer-exemptions"></a>資料傳輸豁免

在特定情況下，有一些 Intune 應用程式保護原則可以允許豁免應用程式和平台服務傳送和接收資料傳輸。 這份清單可能隨時變更，並反映視為對安全產能有所幫助的服務和應用程式。

| 應用程式/服務名稱 | 說明 |
| ---- | --- |
|<code>tel; telprompt</code> | 原生 Phone 應用程式 |
| <code>skype</code> | Skype |
| <code>app-settings</code> | 裝置設定 |
| <code>itms; itmss; itms-apps; itms-appss; itms-services</code> | App Store |
| <code>calshow</code> | 原生行事曆 |


## <a name="access-settings"></a>存取設定

| 設定 | 如何使用 | 預設值 |
|------|------|------|
| **需要 PIN 碼才可存取** | 選擇 [是]，需要 PIN 才能使用這個應用程式。 使用者第一次在工作或學校內容中執行應用程式時，系統會提示他們設定這個 PIN。 線上或離線工作時都會套用 PIN。 預設值 = [是]。<br><br> 進行下列 PIN 強度設定： <ul><li>**選取類型**：先設定數值或密碼類型的 PIN 需求，再存取已套用應用程式保護原則的應用程式。 數值需求只有數字，密碼則至少要以 1 個字母**或**至少要以 1 個特殊字元定義。 <br><br> **注意：** 若要設定密碼類型，應用程式需要有 Intune SDK 版本 7.1.12 或更新版本。 數值類型沒有 Intune SDK 版本限制。 允許的特殊字元包括 iOS 英文鍵盤上的特殊字元和符號。 預設值 = **數值**。<br><br></li><li>**PIN 碼重設前的嘗試次數**：指定使用者必須嘗試順利輸入幾次其 PIN 後才能重設 PIN。 此原則設定格式支援正整數。 預設值 = **5**。<br><br></li><li> **允許簡單的 PIN**：選擇 [是]，允許使用者使用簡單的 PIN 序列，例如 1234、1111、abcd 或 aaaa。 選擇 [否]，防止其使用簡單的序號。 <br><br>**注意**：如果已設定密碼類型 PIN，而且 [允許簡單的 PIN] 設定為 [是]，那麼使用者的 PIN 中需要至少 1 個字母**或**至少 1 個特殊字元。 如果已設定密碼類型 PIN，而且 [允許簡單的 PIN] 設定為 [否]，那麼使用者的 PIN 中需要至少 1 個數字**和** 1 個字母**以及**至少 1 個特殊字元。 預設值 = [是]。 <br><br></li><li>**PIN 長度**：指定 PIN 序列的最小位數。 預設值 = **4**。 <br><br></li><li> **允許指紋而非 PIN (iOS 8.0+)**：選擇 [是]，讓使用者對應用程式存取使用 [Touch ID](https://support.apple.com/HT201371)，而非 PIN。 預設值 = [是]。<br><br></li><li> **允許臉部辨識而非 PIN (iOS 11+)**：選擇 [是]，以允許使用者使用 [Face ID](https://support.apple.com/HT208109) 而非 PIN 存取應用程式。 <br><br>**注意：** 若要設定臉部辨識，應用程式需要有 Intune SDK 7.1.19 版或更新版本。 預設值 = [是]。 當使用者透過其公司帳戶存取應用程式時，系統會提示使用者提供臉部識別碼。<br><br></li><li> **在裝置 PIN 受控時，停用應用程式 PIN**：選擇 [是] 以便於設定好公司入口網站的已註冊裝置上偵測到裝置鎖定時，停用應用程式 PIN。<br><br> **注意：** 應用程式需要 Intune SDK 7.0.1 版或更新版本。 預設值 = [否]。</li></ul> 在 iOS 裝置上，您可以讓使用者使用 [Touch ID](https://support.apple.com/HT201371) 或 [Face ID](https://support.apple.com/HT208109)而非 PIN 來證明其身分識別。 Intune 使用 [LocalAuthentication](https://developer.apple.com/documentation/localauthentication/) API 來驗證使用 Touch ID 和 Face ID 的使用者。 若要深入了解 Touch ID 和 Face ID，請參閱 [iOS 安全性指南](https://www.apple.com/business/docs/iOS_Security_Guide.pdf)。 使用者嘗試透過其公司或學校帳戶使用此應用程式時，系統會提示他們提供自己的指紋識別或臉部識別，而不是輸入 PIN。 啟用此設定時，App 切換預覽影像會在使用工作或學校帳戶時變得很模糊。 </li></ul><!-- <br><br>You can require a PIN expiration for targeted iOS apps. You can configure the PIN requirement and expiration date in days through the Azure portal. When required, a user will be required to set and use a new PIN before getting access to an iOS app. Only iOS apps that have app protection enabled with the Intune App SDK will support this feature.-->| 存取需要 PIN 碼：是 <br><br> 選取類型：數值 <br><br> PIN 碼重設嘗試次數：5 <br><br> 允許簡單的 PIN：是 <br><br> PIN 長度：4 <br><br> 允許指紋：是 <br><br> 允許臉部辨識：是 <br><br> 停用應用程式 PIN：否 |
| **需要公司認證才能存取** | 選擇 [是]，需要使用者使用工作或學校帳戶登入來進行應用程式存取，而不是輸入 PIN。 如果您將此設定為 [是]，並且已開啟 PIN 或生物識別登入提示 ，則將會顯示公司認證以及 PIN 或生物識別登入提示 。 | 否 |
| **封鎖在已進行 JB 或 Root 破解的裝置上執行受管理的應用程式** |  選擇 [是]，防止在已進行 JB 或 Root 破解的裝置上執行這個應用程式。 使用者仍然可以繼續使用這個應用程式來執行個人工作，但必須使用不同的裝置來存取這個應用程式中的工作或學校資料。 | 是 |
| **重新檢查存取需求前等候時間 (分鐘)** | 進行以下設定： <ul><li>**逾時**︰這是重新檢查存取需求 (稍早定義於原則中) 前經過的分鐘數。 例如，若管理員在原則中開啟「PIN」及「封鎖已 Root 破解的裝置」，當使用者開啟受控於 Intune 的裝置時，就必須輸入 PIN 並在未 Root 破解的裝置上使用應用程式。 如果使用此設定，使用者在另外 **30 分鐘** (預設值) 內都不需要在任何受控於 Intune 的應用程式上輸入 PIN 或接受另一次 Root 偵測檢查。  <br><br>**注意：** 在 iOS 上，**相同發行者**的所有受 Intune 管理的應用程式會共用一組 PIN。 當裝置上的應用程式離開前景時，特定 PIN 的 PIN 計時器就會重設。 在此設定中定義的逾時持續時間內，使用者不需要在任何共用 PIN 並受 Intune 管理的應用程式上輸入 PIN。 此原則設定格式支援正整數。<br><br></li><li>**離線寬限期**：這是 MAM 應用程式可以離線執行的分鐘數。 指定經過多少時間 (分鐘) 之後即會重新檢查應用程式存取需求。 預設值 = **720** 分鐘 (12 小時)。 這段期間過後，該應用程式會封鎖對公司或學校資料的存取要求，直到有可用的網路連線為止。 此原則設定格式支援正整數。</li></ul>| 逾時：30 <br><br> 離線：720 |
| **離線間隔幾天後抹除 App 資料** | 在離線執行達到此天數 (由系統管理員定義) 之後，應用程式需要使用者連線到網路並重新驗證。 如果使用者成功驗證，就可以繼續存取其資料，而且會重設離線間隔。  如果使用者無法驗證，應用程式會執行使用者帳戶和資料的選擇性抹除。  如需使用選擇性抹除會移除哪些資料的詳細資訊，請參閱[如何只抹除 Intune 管理之應用程式中的公司資料](https://docs.microsoft.com/intune/apps-selective-wipe)。 此原則設定格式支援正整數。 <br> | 90 天 |
| **需要最低的 iOS 作業系統** | 選擇 [是] 以要求使用此應用程式的最低 iOS 作業系統。 如果裝置上的 iOS 版本不符合需求，將會封鎖使用者進行存取。 <br><br> **注意：** 應用程式需要 Intune SDK 7.0.1 版或更新版本。 | 否 |
| **需要最低的 iOS 作業系統 (僅警告)** | 選擇 [是] 以要求使用此應用程式的最低 iOS 作業系統。 如果裝置上的 iOS 版本不符合需求，使用者將會看見通知。 此通知可以關閉。 <br><br> **注意：** 應用程式需要 Intune SDK 7.0.1 版或更新版本。 | 否 |
| **需要最低的應用程式版本** | 選擇 [是] 以要求使用應用程式的最低應用程式版本。 如果裝置上的應用程式版本不符合需求，會封鎖使用者進行存取。<br><br>因為應用程式之間通常會有不同的版本控制配置，所以請建立包含一個針對單一應用程式之最低應用程式版本的原則 (例如，Outlook 版本原則)。 <br><br> 此原則設定格式支援 major.minor、major.minor.build、major.minor.build.revision。 <br><br> **注意：** 應用程式需要 Intune SDK 7.0.1 版或更新版本。 | 否 | 
| **需要最低的應用程式版本 (僅警告)** | 選擇 [是] 以建議使用此應用程式的最低應用程式版本。 如果裝置上的應用程式版本不符合需求，使用者會看見通知。 此通知可以關閉。<br><br>因為應用程式之間通常會有不同的版本控制配置，所以請建立包含一個針對單一應用程式之最低應用程式版本的原則 (例如，Outlook 版本原則)。 <br><br> 此原則設定格式支援 major.minor、major.minor.build、major.minor.build.revision。 <br><br> **注意：** 應用程式需要 Intune SDK 7.0.1 版或更新版本。 | 否 | 
| **需要最低的 Intune 應用程式保護原則 SDK 版本** | 選擇 [是] 以要求在應用程式上使用的最低 Intune 應用程式保護原則 SDK 版本。 如果應用程式的 Intune 應用程式保護原則 SDK 版本不符合需求，會封鎖使用者進行存取。 <br> <br> 若要深入了解 Intune 應用程式保護原則 SDK，請參閱 [Intune App SDK 概觀](app-sdk.md)。 <br><br> 此原則設定格式支援 major.minor、major.minor.build、major.minor.build.revision。 <br><br> **注意：** 應用程式需要 Intune SDK 7.0.1 版或更新版本。 | 否 |

> [!NOTE]
> 若要深入了解在同一應用程式和使用者集合的 [存取] 區段中設定的多個 Intune 應用程式保護設定如何在 iOS 上運作，請參閱 [Intune MAM 常見問題集](https://docs.microsoft.com/en-us/intune/mam-faq#app-experience-on-ios)與[在 Intune 中使用應用程式防護原則的存取動作選擇性地抹除資料](app-protection-policies-access-actions.md)。

##  <a name="add-ins-for-outlook-app"></a>Outlook 應用程式增益集

Outlook 最近為 iOS 版 Outlook 推出了增益集，可讓您將熱門應用程式與電子郵件用戶端整合。 Web、Windows、Mac 和 iOS 版的 Outlook，皆提供 Outlook 增益集。 Intune SDK 和 Intune 應用程式保護原則不包含管理 Outlook 增益集的支援，但還有其他方法可以限制其使用。 因為增益集透過 Microsoft Exchange 進行管理，所以除非使用者的 Exchange 對使用者關閉了增益集，否則，使用者將可在 Outlook 與未受管理的增益集應用程式之間，共用資料與郵件。

若想要停止讓使用者無法存取及安裝 Outlook 增益集 (如此會影響所有 Outlook 用戶端)，請務必在 Exchange 系統管理中心對角色進行下列變更︰

- 為避免使用者安裝 Office 市集增益集，請移除使用者的「我的市集」角色。
- 為避免使用者側載增益集，請移除使用者的「我的自訂應用程式」角色。
- 為避免使用者安裝所有增益集，請移除使用者的「我的自訂應用程式」與「我的市集」角色。

這些指示適用於 Office 365、Exchange 2016、Exchange 2013 (跨 Web、Windows、Mac 與行動裝置上的 Outlook)。

- 深入了解[適用於 Outlook 的增益集](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx)。
- 深入了解 [How to specify the administrators and users who can install and manage add-ins for Outlook app](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx) (如何指定可安裝及管理 Outlook 應用程式增益集的系統管理員與使用者)。

##  <a name="linkedin-account-connections-for-microsoft-apps"></a>Microsoft 應用程式的 LinkedIn 帳戶連線

LinkedIn 帳戶連線讓使用者在某些 Microsoft 應用程式內看到公用 LinkedIn 設定檔資訊。 根據預設，您的使用者可以選擇連線 LinkedIn 和 Microsoft 工作或學校帳戶，來查看額外的 LinkedIn 設定檔資訊。 

> [!NOTE]
> LinkedIn 整合目前無法用於美國政府客戶，以及 裝載於澳洲、加拿大、中國、法國、德國、印度、韓國、英國、日本和南非的組織的 Exchange Online 信箱。

Intune SDK 和 Intune 應用程式保護原則不包含管理 LinkedIn 帳戶連線的支援，但還有其他方法可以管理它們。 您可以停用整個組織的 LinkedIn 帳戶連線，或是您可以針對組織中的選取使用者群組啟用 LinkedIn 帳戶連線。 這些設定會影響跨所有平台 (Web、行動裝置和桌面) 上的 Office 365 應用程式之間的 LinkedIn 連線。 您可以：

- 在 Azure 入口網站為租用戶啟用或停用 LinkedIn 帳戶連線。 
- 使用群組原則為組織的 Office 2016 應用程式啟用或停用 LinkedIn 帳戶連線。

如果已為租用戶啟用 LinkedIn 整合，則當您組織中的使用者連線 LinkedIn 和 Microsoft 工作或學校帳戶時，他們有兩個選項： 

- 他們可以提供在這兩個帳戶之間共用資料的權限。 這表示他們會提供權限讓 LinkedIn 帳戶與 Microsoft 工作或學校帳戶共用資料，以及讓 Microsoft 工作或學校帳戶與其 LinkedIn 帳戶共用資料。 與 LinkedIn 共用的資料會離開連線服務。 
- 他們只能提供從 LinkedIn 帳戶共用資料到 Microsoft 工作及學校帳戶的權限

如果使用者同意在帳戶之間共用資料，如同 Office 增益集一樣，LinkedIn 整合會使用現有的 Microsoft Graph API。 LinkedIn 整合只會使用可供 Office 增益集使用的 API 子集，並支援各種排除項目。


|Microsoft Graph 權限  |說明  |
|---------|---------|
|[人員](https://developer.microsoft.com/en-us/graph/docs/concepts/permissions_reference#people-permissions)的讀取權限     |可讓應用程式讀取與登入與使用者相關的人員評分清單。 清單可以包括本機連絡人、來自社交網路或貴組織目錄的連絡人，以及最近連絡過 (例如電子郵件與 Skype) 的人員。         |
|[行事曆](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdeveloper.microsoft.com%2Fen-us%2Fgraph%2Fdocs%2Fconcepts%2Fpermissions_reference%23calendars-permissions&data=04%7C01%7CCem.Aykan%40microsoft.com%7C59705402acc347cdf0d908d5b1d82d53%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636610464378331622%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwifQ%3D%3D%7C-1&sdata=fABkrlIxqggnB%2Bc%2BR%2BbFpuenhSg7OHfBhWcbv3ahmAU%3D&reserved=0)的讀取權限     |允許應用程式讀取使用者行事曆中的事件。 包含登入使用者行事曆中的會議、其時間、位置及出席者。         |
|[使用者設定檔](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdeveloper.microsoft.com%2Fen-us%2Fgraph%2Fdocs%2Fconcepts%2Fpermissions_reference%23user-permissions&data=04%7C01%7CCem.Aykan%40microsoft.com%7C59705402acc347cdf0d908d5b1d82d53%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636610464378341626%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwifQ%3D%3D%7C-1&sdata=RcnVIpntjyR4TXafOYTV0SffZuZWpshQQWY0e2VkkXg%3D&reserved=0)的讀取權限     |允許使用者登入應用程式，以及允許應用程式讀取登入之使用者的設定檔。 它也允許應用程式讀取登入之使用者的基本公司資訊。         |
|Subscriptions     |未提供此範圍且尚未使用。 它包含使用者組織提供給 Microsoft 應用程式和服務 (例如 Office 365) 的訂閱。         |
|深入資訊     |未提供此範圍且尚未使用。 它包含根據 Microsoft 服務的使用，與登入的使用者帳戶建立關聯的興趣。         |

### <a name="learn-more"></a>深入了解

- 深入了解 [LinkedIn information and features in your Microsoft apps](https://go.microsoft.com/fwlink/?linkid=850740) (Microsoft 應用程式中的 LinkedIn 資訊與功能)。
- 在 [Office 365 藍圖頁面](https://products.office.com/en-US/business/office-365-roadmap?filters=%26freeformsearch=linkedin#abc)上深入了解 LinkedIn 帳戶連線版本。 
- 深入了解 [Microsoft 應用程式和服務的 LinkedIn 帳戶連線](https://docs.microsoft.com/en-us/azure/active-directory/linkedin-integration)。
- 如需在使用者的 LinkedIn 與 Microsoft 工作或學校帳戶之間共用之資料的詳細資訊，請參閱 [LinkedIn in Microsoft applications at your work or school](https://www.linkedin.com/help/linkedin/answer/84077) (工作或學校之 Microsoft 應用程式中的 LinkedIn)。

