---
title: "使用 App Wrapping Tool 包裝 iOS 應用程式 | Microsoft Intune"
description: "使用本主題中的資訊，深入了解如何在不需修改應用程式本身程式碼的情況下，包裝您的 iOS 應用程式。 準備應用程式，以便您可以套用行動裝置應用程式管理原則。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c67a5042fd177a4c5bd897092e84281db0977f5e
ms.openlocfilehash: 2c187b61b8fe25b2870d0cbc62f8352494583fc2


---

# 準備將 iOS 應用程式交由 Intune App Wrapping Tool 進行行動應用程式管理
使用 **Microsoft Intune App Wrapping Tool for iOS** 修改內部 iOS 應用程式的行為，讓您限制應用程式的功能，而不需變更應用程式本身的程式碼。

此工具是 Mac OS 命令列應用程式，它會建立應用程式的「包裝函式」。 處理應用程式後，您便可以使用您設定的 Intune [行動應用程式管理原則](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)變更應用程式功能。

若要下載此工具，請參閱 [Microsoft Intune App Wrapping Tool for iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios)。



## 步驟 1： 滿足使用應用程式包裝工具的必要條件
請參閱[這篇部落格文章](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)以深入了解必要條件及其設定方法。

|需求|詳細資訊|
|---------------|--------------------------------|
|支援的作業系統和工具組|您必須在執行 OS X 10.8.5 或更新版本的 macOS 電腦上執行應用程式包裝工具，其中此電腦已安裝 XCode 工具組第 5 版或更新版本。|
|簽署憑證和佈建設定檔|您必須擁有 Apple 簽署憑證和佈建設定檔。 請參閱 [Apple 開發人員文件](https://developer.apple.com/)。|
|使用 App Wrapping Tool 處理應用程式|應用程式必須由您的公司或獨立軟體廠商 (ISV) 所開發並簽署。 您無法使用此工具來處理來自 Apple Store 的應用程式。 應用程式必須針對 iOS 8.0 或更新版本撰寫。 應用程式必須也採用位置獨立可執行檔 (PIE) 格式。 如需有關 PIE 格式的詳細資訊，請參閱您的 Apple 開發人員文件。 最後，應用程式必須有副檔名 **.app**，或 **.ipa** 格式。|
|包裝工具無法處理的應用程式|加密的應用程式、未簽署的應用程式和具有擴充檔案屬性的應用程式。|
|設定您的應用程式權利|您必須設定權利，將非一般授與的其他權限和功能提供給應用程式，再包裝應用程式。 如需指示，請參閱[設定應用程式權利](#setting-app-entitlements)。|

## 步驟 2： 安裝應用程式包裝工具

1.  從裝載在 [GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) 的 **Microsoft Intune App Wrapping Tool for iOS** 存放庫，將應用程式包裝工具檔案下載到 Mac 作業系統電腦本機。

2.  按兩下 **Microsoft Intune App Wrapping Tool for iOS.dmg** 安裝檔案。 終端使用者授權合約 (EULA) 視窗隨即出現。 請仔細閱讀文件。

3. 選擇 [同意] 接受 EULA，將封裝掛接到您的電腦。

4.  開啟 **IntuneMAMPackager** 封裝，將檔案儲存到 macOS 電腦的本機資料夾。 您現在已準備好執行應用程式包裝工具。

## 步驟 3： 執行應用程式包裝工具
* 在 macOS 電腦上開啟終端機視窗，瀏覽至您儲存應用程式包裝工具檔案的資料夾。 可執行檔工具名為 **IntuneMAMPackager**，位於 **IntuneMAMPackager/Contents/MacOS**。 您必須執行命令，如下所示︰

    ```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioning profile paths>]

    ```

    > [!NOTE]
    > 某些參數是選擇性的，如下表所示。

    **範例：** 下列範例命令會在名為 **MyApp.ipa**的應用程式上執行 App Wrapping Tool。 已指定佈建設定檔和 SHA-1 雜湊。 處理的應用程式已建立，名為 **MyApp_Wrapped.ipa**，儲存在使用者的 [桌面] 資料夾中。

    ```
    ./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB  -v true
    ```
    您可以使用下列命令列屬性搭配應用程式包裝工具：

    |屬性|使用方法|
  |------------|--------------------|
  |**-i**|`<Path of the input native iOS application file>`。 檔案結尾必須是 .app 或 .ipa。 |
  |**-o**|`<Path of the wrapped output application>` |
  |**-p**|`<Path of your provisioning profile for iOS apps>`|
  |**-c**|`<SHA1 hash of the signing certificate>`|
    |-h|顯示應用程式包裝工具可用命令列屬性的詳細使用資訊。|
  |-v|(可省略但很實用) 輸出到主控台的詳細資訊訊息。|
  |-e | (可省略) 使用此旗標讓應用程式包裝工具在處理應用程式時，移除遺失的權利。 如需詳細資料，請參閱＜設定應用程式權利＞一節。|
  |-xe| (可省略) 列印應用程式 iOS 延伸模組的相關資訊，以及使用這些功能所需的權利。 如需詳細資料，請參閱＜設定應用程式權利＞一節。 |
  |-x| (可省略) `<An array of paths to extension provisioning profiles>`。 如果您的應用程式需要延伸模組佈建設定檔，請使用此選項。|
  |-f |(可省略) `<Path to a plist file specifying arguments.>` 如果您選擇使用 plist 範本指定其餘的 IntuneMAMPackager 屬性：-i、-o、-p 等等，請在 [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) 檔案的前面使用此旗標。如需詳細資料，請參閱＜使用 plist 輸入引數＞一節。 |
  |-b|(可省略) 如果希望包裝的輸出應用程式和輸入應用程式有相同的套件組合版本，請使用 -b 不加引數 (不建議使用)。 <br/><br/> 如果希望包裝的應用程式有自訂的 CFBundleVersion，請使用 `-b <custom bundle version>`。 如果選擇指定自訂的 CFBundleVersion，建議您以最不明顯的元件累增原生應用程式的 CFBundleVersion，例如， 1.0.0 -> 1.0.1. |


###使用 plist 輸入引數
您可將所有命令引數放入 [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) 檔案，即可輕鬆執行應用程式包裝工具。 Plist 是一種類似 XML 的檔案格式，我們可以用它以表單介面輸入命令列引數。

在 **IntuneMAMPackager/Contents/MacOS** 資料夾中，使用文字編輯器或 Xcode 開啟空白的 plist 範本 `Parameters.plist`。 針對下列金鑰輸入您的引數︰

| Plist 金鑰 |  預設值| 附註 |
|------------------|--------------|-----|
| 輸入應用程式封裝路徑  |empty| 與 -i 相同。 |
| 輸出應用程式封裝路徑 |empty| 與 -o 相同。|
| 佈建設定檔路徑 |empty| 與 -p 相同。 |
| SHA-1 憑證雜湊 |empty| 與 -c 相同。 |
| 啟用詳細資訊 |false| 與 -v 相同。 |
| 移除遺失的權利 | false| 與 -c 相同。|
| 避免預設的組建 |false | 相當於使用 -b 不加引數。 |
|組建字串覆寫 | empty| 已包裝的輸出應用程式的自訂 CFBundleVersion |
|延伸模組佈建設定檔路徑 | empty| 應用程式的延伸模組佈建設定檔陣列。
  

最後，將 plist 當成單獨的引數執行 IntuneMAMPackager︰

```
./IntuneMAMPackager –f Parameters.plist
```

* 處理完成後即會顯示**應用程式已成功地包裝**訊息。

    如果發生錯誤，請參閱[錯誤訊息](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#error-messages)以取得協助。

*   已包裝的應用程式會儲存在您先前指定的輸出資料夾。 您現在可以將應用程式上傳到 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]，然後將它與行動應用程式管理原則相關聯。

    > [!IMPORTANT]
    > 上傳已包裝的應用程式時，如果較舊的 (包裝或原生) 版本已部署到 Intune，您可以嘗試更新舊版應用程式。 如果發生錯誤，請將應用程式上傳為新的應用程式，並刪除舊版。

    您現在可以將應用程式部署到您的 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 群組，而且應用程式現在將使用您指定的應用程式限制在裝置上執行。

## 錯誤訊息和記錄檔
使用下列資訊對您使用 App Wrapping Tool 時所遇到的問題進行疑難排解。

### 錯誤訊息
如果應用程式包裝工具無法成功完成，主控台中即會顯示下列其中一則錯誤訊息：

|錯誤訊息|詳細資訊|
|-----------------|--------------------|
|您必須指定有效的 iOS 佈建設定檔。|您的佈建設定檔可能無效。 請檢查以確定您有裝置的正確權限，且您的設定檔正確地將目標鎖定在開發或散發。 您的佈建設定檔也可能過期。|
|請指定有效的輸入應用程式名稱。|請確定您指定的輸入應用程式名稱正確。|
|請指定輸出應用程式的有效路徑。|請確定您指定的輸出應用程式路徑已存在且正確。|
|請指定有效的輸入佈建設定檔。|請確定您提供有效的佈建設定檔名稱和副檔名。 您的佈建設定檔可能缺少權利，或是您可能未包含 **-p** 命令列選項。|
|找不到您指定的輸入應用程式。 請指定有效的輸入應用程式名稱和路徑。|請確定您的輸入應用程式路徑有效且已存在。 請確定輸入應用程式存在於該位置。|
|找不到您指定的輸入佈建設定檔。 請指定有效的輸入佈建設定檔。|請確定輸入佈建檔案的路徑有效，且您指定的檔案已存在。|
|找不到您指定的輸出應用程式資料夾。 請指定輸出應用程式的有效路徑。|請確定您指定的輸出路徑有效且已存在。|
|輸出應用程式沒有 .ipa 副檔名。|應用程式包裝工具只接受具有 **.app** 和 **.ipa** 副檔名的應用程式。 請確定您的輸出檔案具有有效的副檔名。|
|指定了無效的簽章憑證。 請指定有效的 Apple 簽章憑證。|請確定您已經從 Apple 開發人員入口網站下載正確的簽章憑證。 您的憑證可能已過期，或可能缺少公用或私用金鑰。 如果您的 Apple 憑證和佈建設定檔可用來在 Xcode 中正確地簽署應用程式，它們便適用於應用程式包裝工具。|
|您指定的輸入應用程式無效。 請指定有效的應用程式。|請確定您具有已經編譯為 .app 或 .ipa 檔案的有效 iOS 應用程式。|
|您指定的輸入應用程式已加密。 請指定有效的未加密應用程式。|應用程式包裝工具不支援加密的應用程式。 請提供未加密的應用程式。|
|您指定的輸入應用程式不是位置獨立可執行檔 (PIE) 格式。 請指定有效的 PIE 格式應用程式。|位置獨立可執行檔 (PIE) 應用程式可以在執行時於隨機記憶體位址載入，這可以具備安全性好處。 如需詳細資訊，請參閱 Apple 開發人員文件。|
|您指定的輸入應用程式已經包裝。 請指定有效的未包裝應用程式。|您無法處理此工具已經處理過的應用程式。 如果您想要再次處理應用程式，請使用原始版本的應用程式來執行此工具。|
|您指定的輸入應用程式未簽署。 請指定有效的已簽署應用程式。|應用程式包裝工具需要已簽署的應用程式。 請參閱您的開發人員文件，了解如何簽署已包裝的應用程式。|
|您指定的輸入應用程式必須為 .ipa 或 .app 格式。|應用程式包裝工具只接受 .app 和 .ipa 副檔名。 請確定您的輸入檔副檔名有效，且已經編譯為 .app 或 .ipa 檔案。|
|您指定的輸入應用程式已包裝，且是最新的原則範本版本。|應用程式包裝工具不會使用最新的原則範本版本重新包裝現有的已包裝應用程式。|
|警告：未指定 SHA1 憑證雜湊。 請確定您的已包裝應用程式已經簽署，然後再部署。|請確定在 **–c** 命令列旗標後指定有效的 SHA1 雜湊。 |

### 應用程式包裝工具的記錄檔
使用應用程式包裝工具包裝的應用程式，會產生寫入到 iOS 用戶端裝置主控台的記錄檔。 當您的應用程式有問題並需要診斷問題是否與應用程式包裝工具相關時，這項資訊很有用。 若要得到此資訊，請使用下列步驟：

1.  藉由執行應用程式來重現問題。

2.  遵照 [偵錯已部署的 iOS 應用程式](https://developer.apple.com/library/ios/qa/qa1747/_index.html)的 Apple 指示收集主控台輸出。

3.  在主控台輸入下列指令碼，篩選應用程式限制輸出的已儲存記錄：

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    您可以將篩選過的記錄檔提交給 Microsoft。

    > [!NOTE]
    > 在記錄檔中，項目「組建版本」表示 Xcode 的組建版本。

    已包裝的應用程式也會提供使用者選項，在應用程式當機之後，直接從裝置透過電子郵件傳送記錄檔。 使用者可以將記錄檔傳送給您檢查，並視需要轉寄給 Microsoft。


### 憑證、佈建設定檔和驗證需求

您必須符合應用程式包裝工具的一些需求，它才能發揮完整的功能。

|需求|詳細資料|
|---------------|-----------|
|佈建設定檔|**請確定佈建設定檔有效後再加以納入**。 應用程式包裝工具在處理 iOS 應用程式時，不會檢查佈建設定檔是否已過期。 如果指定了過期的佈建設定檔，應用程式包裝工具會包含過期的佈建設定檔，而您將不會知道有問題，直到在 iOS 裝置上安裝應用程式失敗。|
|憑證|**請先確認憑證有效再加以指定**。 工具在處理 iOS 應用程式時，不會檢查憑證是否已過期。 如果提供已過期憑證的雜湊，則工具會處理並簽署應用程式，但它無法在裝置上安裝。<br /><br />**請確定為簽署封裝應用程式所提供的憑證，在佈建設定檔中有相符的項目**。 工具不會驗證針對為簽署包裝應用程式所提供的憑證，佈建設定檔是否有相符的項目。|
|驗證|裝置必須有 PIN，加密才能運作。 在已部署包裝應用程式的裝置上，若觸碰裝置上的狀態列，即會要求使用者向 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 重新驗證。 包裝應用程式中的預設原則為「重新啟動時驗證」。 iOS 透過結束應用程式然後加以重新啟動 來處理任何外部通知 (例如通話)。


## 設定應用程式權利
包裝應用程式之前，您可以授與**權利**，將超過應用程式一般可執行的其他權限和功能提供給應用程式。  **權利檔案**還可在程式碼簽署期間，用於指定應用程式內的特殊權限 (例如共用金鑰鏈的存取權)。 應用程式開發期間會在 Xcode 內啟用特定應用程式服務，稱為**功能**。 啟用後，您的權利檔案中會反映這些功能。 如需權利和功能的詳細資訊，請參閱 iOS Developer Library 中的[新增功能](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html)。 如需支援功能的完整清單，請參閱[支援的功能](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html)。

### App Wrapping Tool for iOS 的支援功能

|功能|說明|建議的指引|
|--------------|---------------|------------------------|
|應用程式群組|使用 [應用程式群組] 可讓多個應用程式存取共用容器，並可在應用程式之間進行其他處理序間通訊。<br /><br />若要啟用 [應用程式群組]，請開啟 [功能] 窗格，然後在 [應用程式群組] 區段中按一下 [開啟] 開關。 您可以新增應用程式群組或選取現有的應用程式群組。|使用應用程式群組時，請使用反向 DNS 標記法：<br /><br />*group.com.companyName.AppGroup*|
|背景模式|啟用 [背景模式] 可讓您的 iOS 應用程式繼續在背景執行。||
|資料保護|[資料保護] 為使用 iOS 應用程式儲存在磁碟上的檔案，增加一層安全性。 [資料保護] 使用特定裝置上的現有內建加密硬體，以加密格式將檔案儲存在磁碟上。 您必須佈建應用程式，才能使用 [資料保護]。||
|在應用程式內購買|[在應用程式內購買] 可讓您連線到市集，並安全地處理來自使用者的付款，以直接將市集內嵌到您的應用程式中。 您可以使用 [在應用程式內購買] 針對增強功能或您應用程式可用的其他內容收款。||
|金鑰鏈共用|啟用 [金鑰鏈共用] 可讓您的應用程式與您小組所開發的其他應用程式共用金鑰鏈中的密碼。|使用 [金鑰鏈共用] 時，請使用反向 DNS 標記法：<br /><br />*com.companyName.KeychainGroup*|
|個人 VPN|啟用 [個人 VPN] 可讓您的應用程式建立及控制使用網路擴充功能架構的自訂系統 VPN 組態。||
|推播通知|Apple Push Notification Service (APNs) 可讓不在前景執行的應用程式在有使用者可用的資訊時，通知使用者。|若要讓 [推播通知] 運作，您必須使用應用程式專屬的佈建設定檔。<br /><br />遵循 [Apple 開發人員文件](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html)中的步驟。|
|無線配件組態|啟用 [無線配件組態] 可為您的專案新增外部配件架構，並讓您的應用程式設定 MFi Wi-Fi 配件。||

### 啟用權利的步驟

1.  啟用您應用程式中的功能：

    1.  在 Xcode 中，導覽至您的應用程式目標，然後按一下 [功能] 窗格。

    2.  開啟適當的功能。 如需每項功能及如何決定正確值的詳細資訊，請參閱 [iOS Developer Library 中的新增功能](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html)。

    3.  記下您在程序期間所建立的任何識別碼。

    4.  建置並簽署要包裝的應用程式。

2.  啟用您佈建設定檔中的權利：

    1.  登入 Apple Developer Member Center。

    2.  為您的應用程式建立佈建設定檔。 如需相關指示，請參閱[如何取得 Intune App Wrapping Tool for iOS 的必要條件](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)。

    3.  在您的佈建設定檔中，啟用您應用程式中所擁有的相同權利。 您必須提供在開發應用程式期間所指定的相同識別碼。

    4.  完成 [佈建設定檔精靈] 並下載您的檔案。

3.  確定您已符合所有必要條件，然後再包裝應用程式。

### 權利的常見錯誤疑難排解
如果 App Wrapping Tool for iOS 顯示權利錯誤，請嘗試下列疑難排解步驟。

|問題|原因|解決方法|
|---------|---------|--------------|
|無法剖析從輸入應用程式產生的權利。|App Wrapping Tool 無法讀取從應用程式解壓縮的權利檔案。 權利檔案的格式可能不正確。|檢查您應用程式的權利檔案。 若要這樣做，請遵循下列所述的指示進行。 檢查權利檔案時，請檢查是否有任何格式不正確的語法。 檔案格式應該是 XML。|
|佈建設定檔中遺失權利 (會列出遺失的權利)。 使用具有這些權利的佈建設定檔重新封裝應用程式。|在佈建設定檔中啟用的權利與在應用程式中啟用的功能不符。 與特定功能 (例如 [應用程式群組]、[金鑰鏈共用] 等) 相關聯的識別碼也會不符。|一般而言，您可以建立新的佈建設定檔，並啟用與應用程式相同的功能。 當設定檔與應用程式之間的識別碼不符時，App Wrapping Tool 會更換識別碼 (如果可以)。 如果在建立新的佈建設定檔之後仍然收到這個錯誤，您可以嘗試從應用程式移除權利，請使用 **-e** 參數 (請參閱以下的「使用 -e 參數移除應用程式的權利」一節)。|

### 尋找已簽署應用程式的現有權利
若要檢閱已簽署應用程式和佈建設定檔的現有權利：

1.  找到 .ipa 檔案並將其副檔名變更為 .zip。

2.  展開 .zip 檔案。 這會產生內含 .app 套件組合的 Payload 資料夾。

3.  使用 codesign 工具檢查 .app 套件組合的權利，如下所示：

    ```
    $ codesign -d --entitlements :- "Payload/YourApp.app"
    ```
    其中 `YourApp.app` 是您 .app 套件組合的實際名稱。

4.  使用安全性工具檢查應用程式內嵌佈建設定檔的權利：

    ```
    $ security -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```
    其中 `YourApp.app` 是您 .app 套件組合的實際名稱。

### 使用 –e 參數移除應用程式的權利
這個命令會移除應用程式中任何已啟用但不在權利檔案中的功能。 如果您移除的是應用程式正在使用的功能，可能會中斷您的應用程式。 例如，如果您使用廠商生產的應用程式，而它預設具有所有的功能，您有可能會移除缺漏的功能。

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## 應用程式包裝工具的安全性與隱私權
當您使用應用程式包裝工具時，請使用下列安全性與隱私權的最佳作法。

-   簽章憑證、佈建設定檔和您指定的企業營運系統應用程式所在的 macOS 電腦，與用來執行應用程式包裝工具必須為同一部。 如果檔案位在 UNC 路徑，請確定這些路徑可從 mac OS 電腦存取。 路徑必須透過 IPsec 或 SMB 簽章保護。

    匯入 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 主控台的已包裝應用程式，必須位於工具執行所在的同一部電腦上。 若檔案使用 UNC 路徑，請確定該路徑可從執行 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 主控台的電腦存取。 路徑必須透過 IPsec 或 SMB 簽章保護。

-   從 GitHub 存放庫下載應用程式包裝工具的環境，必須透過 IPsec 或 SMB 簽章保護。

-   您所處理的應用程式必須來自值得信任的來源，以確保防護免於攻擊威脅。

-   確保您在應用程式包裝工具中指定的輸出資料夾受到保護，尤其如果它是遠端資料夾的話。

-   包含檔案上傳對話方塊的 iOS 應用程式，可以讓使用者規避套用至應用程式的剪下、複製和貼上限制。 例如，使用者可以使用檔案上傳對話方塊，來上傳應用程式資料的螢幕擷取畫面。

-   當使用者從已包裝的應用程式內監視其裝置上的文件資料夾時，可能會看到一個名為 **.msftintuneapplauncher**的資料夾。 如果此資料夾遭到變更或刪除，這可能會影響受限制應用程式的正確運作。

### 請參閱
- [決定如何準備應用程式以使用 Microsoft Intune 進行行動應用程式管理](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)</br>
- [透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)</br>
- [使用 SDK 讓應用程式進行行動應用程式管理](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Oct16_HO2-->


