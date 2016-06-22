---
# required metadata

title: 新增應用程式 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2b770f4f-6d36-41e4-b535-514b46e29aaa

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mghadial
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 新增應用程式
使用 Microsoft Intune 開始部署應用程式之前，請花點時間熟悉本主題所介紹的概念。 這有助於您瞭解可將哪些應用程式部署到哪些平台，並瞭解您這麼做之前必須先準備就緒的必要條件。

## 您可以使用 Intune 部署的應用程式類型
您可以將應用程式部署至 Intune 支援的所有裝置類型。 根據您要部署的應用程式類型，程序和支援的裝置會不同。 您可以使用下列資訊來幫助您了解可部署和不可部署的項目：


### **Windows Installer (&#42;.exe、&#42;.msi)**
- 這種類型的應用程式必須支援不需要使用者輸入的無訊息安裝。 應用程式文件應該包括相關的命令列選項，以無訊息方式安裝應用程式 (例如，**/q**)。 您可以在[這裡](https://support.microsoft.com/en-us/kb/227091)找到常用命令列選項清單。
- 應用程式安裝程式需要的任何其他檔案和資料夾，都必須可以在您為應用程式安裝檔指定的位置中找到。
- 在大多數情況下，Windows Installer (.msi) 和 Windows Installer 修補 (.msp) 檔案都不需要任何命令列引數，就能由 Intune 安裝。 請查看您的應用程式文件。 如果需要命令列引數，必須以「名稱=值」配對的格式輸入 (例如 TRANSFORMS=custom_transform.mst)。

這類型的應用程式會上傳至雲端儲存空間。
### **Android 應用程式套件 (&#42;.apk 檔案)**
這類型的應用程式會上傳至雲端儲存空間。
### **iOS 應用程式套件 (&#42;.ipa 檔案)**
- 若要部署 iOS 應用程式，必須具備有效的 .ipa 套件。
- .ipa 套件必須已由 Apple 簽署，而且佈建設定檔中指明的到期日必須有效。 Intune 可散發企業憑證 iOS 應用程式。 但無法支援所有 Apple 開發人員憑證應用程式。
- 您的公司必須註冊 iOS Developer Enterprise Program。
- 請確定您的組織防火牆可讓您存取 iOS 佈建與憑證網站。
- 不需要與應用程式一起部署資訊清單檔案 (.plist)。

這類型的應用程式會上傳至雲端儲存空間。

使用者目前無法直接從適用於 iOS 的 Intune 公司入口網站應用程式安裝公司應用程式。 這是因為在 iOS 應用程式存放區中發行的應用程式的限制 (請參閱 [應用程式存放區檢閱指引](https://developer.apple.com/app-store/review/guidelines/))。 使用者可在其裝置上啟動公司入口網站應用程式，然後點選 [公司應用程式] 磚，以開啟瀏覽器，將使用者重新導向至 Intune Web 入口網站，來存取公司應用程式 (包括受管理的 App Store 應用程式及商務營運應用程式套件)。

### **Windows Phone 應用程式套件 (&#42;.xap、.appx、.appxbundle)**
- 若要部署應用程式，您將需要企業行動程式碼簽署憑證。 如需詳細資訊，請參閱[使用 Microsoft Intune 設定 Windows Phone 管理](set-up-windows-phone-management-with-microsoft-intune.md)。

這類型的應用程式會上傳至雲端儲存空間。

如需安裝通用 Windows 平台 (UWP) 上的企業營運應用程式與 Intune 相關資訊，請參閱下方內容。

### **Windows 應用程式套件 (.appx、 .appxbundle)**
- 若要部署應用程式，您將需要企業行動程式碼簽署憑證。 如需詳細資訊，請參閱[使用 Microsoft Intune 設定 Windows 裝置管理](set-up-windows-device-management-with-microsoft-intune.md)。

這類型的應用程式會上傳至雲端儲存空間。
### **透過 MDM 的 Windows Installer (&#42;.msi)**
這種安裝程式類型可讓您建立 Windows Installer 應用程式，並部署到執行 Windows 10 的已註冊電腦上。<br /><br />當您使用這種安裝程式類型時，必須考量下列幾點：
- 您只能上傳副檔名為 .msi 的單一檔案。
- 使用檔案的產品代碼和產品版本來偵測應用程式。
- 使用應用程式的預設重新啟動行為。 Intune 無法控制這點。
- 針對單一使用者會安裝每位使用者的 MSI 封裝。
- 針對裝置上的所有使用者會安裝每部電腦的 MSI 封裝。
- 目前只有裝置上的所有使用者可安裝雙重模式的 MSI 封裝。
- 當各版的 MSI 產品代碼相同時，支援應用程式更新。

這類型的應用程式會上傳至雲端儲存空間。
### **外部連結**
在具有下列項目時使用：
- 可讓使用者從 App Store 下載應用程式的 **URL**。
- 從網頁瀏覽器執行之 Ｗeb 應用程式的**連結**。

根據外部連結的應用程式不會儲存在您的 Intune 雲端儲存空間。
### **應用程式商店中的受管理 iOS 應用程式**
可讓您管理和部署 App Store 的免費 iOS 應用程式。 也能讓您關聯[行動應用程式管理原則](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)與[相容的應用程式](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)，並在管理主控台中檢閱其狀態。<br /><br />受管理 iOS 應用程式不會儲存在您的 Intune 雲端儲存空間中。
> [!TIP] 在您[設定行動裝置管理授權單位](get-ready-to-enroll-devices-in-microsoft-intune.md)為 Intune 前，無法使用行動裝置的選項。

## 支援通用 Windows 平台 (UWP) 應用程式
Windows 10 電腦不需要側載金鑰即可安裝企業營運應用程式。 不過，登錄機碼 **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** 的值必須為 **1** 才能啟用側載。

如果未設定此登錄機碼，Intune 就會在您初次將應用程式部署到裝置時，自動將此值設為 **1**。 如果您已將此值設為 **0**，Intune 即無法自動變更此值，而部署企業營運應用程式將會失敗。

通用 Windows 平台企業營運應用程式必須經過程式碼簽署憑證，而且此憑證受到部署該應用程式的每部目標裝置信任。 您可以使用來自內部 PKI 基礎結構的憑證，也可以使用安裝於裝置上的協力廠商公用根憑證。

在 Windows 10 行動裝置版的裝置上，您可以使用非 Symantec 的程式碼簽署憑證來簽署通用 **.appx** 應用程式。 要安裝於 Windows 10 行動裝置版裝置的 **.xap** 應用程式以及針對 Windows Phone 8.1 所建置的 **.appx** 套件，則必須使用 Symantec 程式碼簽署憑證。

## 後續步驟 

接下來，您必須先在 Intune 主控台中新增應用程式，才可以部署它們。 您可以加入適用於[註冊裝置](add-apps-for-mobile-devices-in-microsoft-intune.md)，或[使用 Intune 用戶端軟體所管理的 Windows 電腦](add-apps-for-windows-pcs-in-microsoft-intune.md)的應用程式。

<!--HONumber=Jun16_HO2-->


