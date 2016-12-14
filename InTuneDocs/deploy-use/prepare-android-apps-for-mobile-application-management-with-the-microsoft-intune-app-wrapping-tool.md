---
title: "使用 App Wrapping Tool 包裝 Android 應用程式 | Microsoft Intune"
description: "使用本文中的資訊，了解如何在不需變更應用程式本身程式碼的情況下，包裝您的 Android 應用程式。 準備應用程式，以便您可以套用行動裝置應用程式管理原則。"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ee7e0491c0635c45cbc0377a5de01d5eba851132
ms.openlocfilehash: e8ca141b31104fb5759d9796f19b618debe74752


---

# <a name="prepare-android-apps-for-mobile-application-management-with-the-intune-app-wrapping-tool"></a>準備 Android 應用程式以使用 Intune 應用程式包裝工具進行行動應用程式管理

使用 Microsoft Intune App Wrapping Tool for Android 變更內部 Android 應用程式的行為，讓您限制應用程式的功能，而不需變更應用程式本身的程式碼。

此工具是一個 Windows 命令列應用程式，可在 PowerShell 中執行並在您的 Android 應用程式周圍建立包裝函式。 包裝好應用程式後，您便可以在 Intune 中設定[行動應用程式管理原則](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)，變更應用程式功能。


執行此工具之前，請檢閱[執行 App Wrapping Tool 的安全性考量](#security-considerations-for-running-the-app-wrapping-tool)。 若要下載此工具，請前往 GitHub 的 [Microsoft Intune App Wrapping Tool for Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android)。



## <a name="fulfill-the-prerequisites-for-using-the-app-wrapping-tool"></a>滿足使用 App Wrapping Tool 的必要條件

-   您必須在執行 Windows 7 或更新版本的 Windows 電腦上執行 App Wrapping Tool。

-   您的輸入應用程式必須是副檔名為 .apk 的有效 Android 應用程式套件，而且：

    -   它無法加密。
    -   它之前未使用 Intune App Wrapping Tool 進行包裝。
    -   它必須是針對 Android 4.0 或更新版本編寫的。

-   該應用程式必須是由貴公司所開發，或針對貴公司所開發。 您無法在下載自 Google Play 商店的應用程式使用這個工具。

-   若要執行 App Wrapping Tool，您必須安裝最新版的 [Java Runtime Environment](http://java.com/download/)，然後確定已在您的 Windows 環境變數中將 Java 路徑變數設為 C:\ProgramData\Oracle\Java\javapath。 如需詳細說明，請參閱 [Java 文件](http://java.com/download/help/)。

    > [!NOTE]
    > 在某些情況下，Java 32 位元版本可能會導致記憶體問題。 您最好安裝 64 位元版本。

- Android 要求所有應用程式套件 (.apk) 均已簽署。 使用 Java keytool 產生簽署包裝輸出應用程式所需的認證。 例如，下列命令使用 Java 可執行檔 keytool.exe 產生 App Wrapping Tool 可使用的金鑰，以簽署包裝的輸出應用程式。

    ```
    keytool.exe -genkeypair -v -keystore mykeystorefile -alias mykeyalias -keyalg RSA -keysize 2048 -validity 50000
    ```
    這個範例會使用 RSA 演算法產生金鑰組 (大小為 2,048 位元的公開金鑰及相關私密金鑰)。 然後將公開金鑰包裝成 X.509 v3 自我簽署憑證，以單一項目憑證鏈結的形式儲存。 此憑證鏈結與私密金鑰會儲存在名為 "mykeystorefile" 的新金鑰儲存區中，並依別名 "mykeyalias" 識別。 金鑰儲存區項目有效期限為 50,000 天。

    命令會提示您提供金鑰儲存區與金鑰的密碼。 請使用安全的密碼並記住，因為執行 App Wrapping Tool 時會需要這些密碼。

    如需詳細文件，請在 Oracle 文件網站上閱讀更多 Java [keytool](http://docs.oracle.com/javase/6/docs/technotes/tools/windows/keytool.html) 及 Java [金鑰儲存區](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html)資訊。

## <a name="install-the-app-wrapping-tool"></a>安裝應用程式包裝工具

1.  從 [GitHub 儲存機制](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android)將 Intune App Wrapping Tool for Android 的 InstallAWT.exe 安裝檔案下載至 Windows 電腦。 開啟安裝檔案。

2.  接受授權合約，然後完成安裝。

記下您安裝此工具的資料夾。 預設位置為：C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool。

## <a name="run-the-app-wrapping-tool"></a>執行應用程式包裝工具

1.  在您安裝 App Wrapping Tool 的 Windows 電腦上，以系統管理員模式開啟 PowerShell 視窗。

2.  從安裝此工具的資料夾，匯入 App Wrapping Tool PowerShell 模組：

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  使用 **invoke-AppWrappingTool** 命令執行工具，其使用語法如下：
    ```
    Invoke-AppWrappingTool [-InputPath] <String> [-OutputPath] <String> -KeyStorePath <String> -KeyStorePassword <SecureString>
    -KeyAlias <String> -KeyPassword <SecureString> [-SigAlg <String>] [<CommonParameters>]
    ```

 下表詳列 **invoke-AppWrappingTool** 命令的屬性：

|屬性|資訊|範例|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|來源 Android 應用程式 (.apk) 的路徑。| |
|**-OutputPath**&lt;String&gt;|輸出的 Android 應用程式路徑。 如果此路徑與 InputPath 的目錄路徑相同，封裝會失敗。| |
|**-KeyStorePath**&lt;String&gt;|包含要簽署之公開/私密金鑰組的金鑰儲存區檔案路徑。|根據預設，金鑰儲存區檔案會儲存在 "C:\Program Files (x86)\Java\jreX.X.X_XX\bin"。 |
|**-KeyStorePassword**&lt;SecureString&gt;|用來解密 keystore 的密碼。 Android 要求所有應用程式套件 (.apk) 均已簽署。 使用 Java keytool 來產生 KeyStorePassword。 在這裡深入了解 Java [金鑰儲存區](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html)。| |
|**-KeyAlias**&lt;String&gt;|要用於簽署的金鑰名稱。| |
|**-KeyPassword**&lt;SecureString&gt;|用來解密簽署用途之私密金鑰的密碼。| |
|**-SigAlg**&lt;SecureString&gt;| (選擇性) 要用於簽署的簽章演算法名稱。 此演算法必須與私密金鑰相容。|範例：SHA256withRSA、SHA1withRSA、MD5withRSA|
| **&lt;CommonParameters&gt;** | (選擇性) 此命令支援 verbose 和 debug 等常用 PowerShell 參數。 |


- 如需常用參數清單，請參閱 [Microsoft 指令碼中心](https://technet.microsoft.com/library/hh847884.aspx)。

- 若要查看工具的詳細使用方式資訊，請輸入命令：

    ```
    Help Invoke-AppWrappingTool
    ```

**範例：**

匯入 PowerShell 模組。
```
Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
```
在原生應用程式 HelloWorld.apk 執行 App Wrapping Tool。
```
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

系統接著會提示您提供 **KeyStorePassword** 和 **KeyPassword**。 輸入您用以建立金鑰儲存區檔案的認證。

隨即會產生已包裝的應用程式和記錄檔，並儲存於您指定的輸出路徑中。

## <a name="security-considerations-for-running-the-app-wrapping-tool"></a>執行 App Wrapping Tool 的安全性考量
若要防止潛在的詐騙、資訊洩漏和權限提升攻擊：

-   請確定輸入的企業營運 (LOB) 應用程式、輸出應用程式及 Java 金鑰儲存區都位於執行 App Wrapping Tool 的同一部 Windows 電腦上。

-   在匯入執行工具的同一部機器上，將輸出應用程式匯入 Intune 主控台。 如需 Java keytool 的詳細資訊，請參閱 [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html)。

-   如果輸出應用程式和工具位於通用命名慣例 (UNC) 路徑上，而您未在同一部電腦上執行工具和輸入檔案，請使用 [網際網路通訊協定安全性 (IPsec)](http://en.wikipedia.org/wiki/IPsec) 或[伺服器訊息區 (SMB) 簽署](https://support.microsoft.com/en-us/kb/887429)，將環境設定為安全的。

-   確認應用程式來自信任的來源。

-   保護包含已包裝應用程式的輸出目錄。 考慮針對輸出使用使用者層級目錄。

### <a name="see-also"></a>請參閱
- [決定如何準備應用程式以使用 Microsoft Intune 進行行動應用程式管理](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [使用 SDK 讓應用程式進行行動應用程式管理](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Dec16_HO2-->


