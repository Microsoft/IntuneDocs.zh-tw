---
title: "新增應用程式"
description: "使用 Intune 開始部署應用程式之前，請花點時間熟悉本主題所介紹的概念。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b770f4f-6d36-41e4-b535-514b46e29aaa
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 788e8a7f15566c4b15fec09f3e861d9380278e3f
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2017
---
# <a name="add-apps-with-microsoft-intune"></a>使用 Microsoft Intune 新增應用程式

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用 Microsoft Intune 開始部署應用程式之前，請花點時間熟悉本主題所介紹的概念。 這些概念有助於您了解可將哪些應用程式部署到哪一個平台。 還可協助您了解在部署應用程式之前，必須先準備就緒的必要條件。

## <a name="app-types-that-you-can-deploy"></a>您可以部署的應用程式類型

### <a name="software-installer"></a>軟體安裝程式

|應用程式類型|詳細資料|
|----------------|-------|
|**Windows Installer (&#42;.exe, &#42;.msi)**|這種類型的應用程式必須支援不需要使用者輸入的無訊息安裝。 應用程式文件應該包括相關的命令列選項，以無訊息方式安裝應用程式 (例如，**/q**)。 您可以在 [Microsoft Windows Installer 工具的命令列參數](https://support.microsoft.com/kb/227091)中，找到常用的命令列選項。<br><br>應用程式安裝程式需要的任何其他檔案和資料夾，都必須可以在您為應用程式安裝檔指定的位置中找到。<br><br>在大多數情況下，Windows Installer (.msi) 和 Windows Installer 修補 (.msp) 檔案都不需要 Intune 安裝任何命令列引數。 請查看您的應用程式文件。<br><br>如果需要命令列引數，必須以「名稱=值」配對的格式輸入 (例如 TRANSFORMS=custom_transform.mst)。<br><br>此應用程式類型只適用於執行 Intune 軟體用戶端的電腦。|
|**Android 應用程式套件 (&#42;.apk)**|若要部署 Android 應用程式，必須具備有效的 .apk 套件。|
|**iOS 應用程式套件 (&#42;.ipa)**|若要部署 iOS 應用程式，必須具備有效的 .ipa 套件。<br><br>.ipa 套件必須已由 Apple 簽署，而且佈建設定檔中的到期日必須有效。 Intune 可散發企業憑證 iOS 應用程式。<br><br>但無法支援所有 Apple 開發人員憑證應用程式。<br><br>您的公司必須註冊 iOS Developer Enterprise Program。<br><br>請確定您的組織防火牆可讓您存取 iOS 佈建與憑證網站。<br><br>您不需要搭配應用程式部署資訊清單檔案 (.plist)。|
|**Windows Phone 應用程式套件 (&#42;.xap、.appx、.appxbundle)**|若要部署應用程式，您需要企業行動程式碼簽署憑證。 如需詳細資訊，請參閱[使用 Microsoft Intune 設定 Windows Phone 管理](set-up-windows-device-management-with-microsoft-intune.md)。|
|**Windows 應用程式套件 (.appx、.appxbundle)**|若要部署應用程式，您需要企業行動程式碼簽署憑證。 如需詳細資訊，請參閱[使用 Microsoft Intune 設定 Windows 裝置管理](set-up-windows-device-management-with-microsoft-intune.md)。|
|**透過 MDM 的 Windows Installer (&#42;.msi)**|您可以使用此應用程式建立以 Windows Installer 為基礎的應用程式，並部署到執行 Windows 10 的已註冊電腦上。 這些電腦可以透過行動裝置管理 (MDM) 來管理。<br /><br />您只能上傳副檔名為 .msi 的單一檔案。<br><br>使用檔案的產品代碼和產品版本來偵測應用程式。<br><br>使用應用程式的預設重新啟動行為。 Intune 無法控制此行為。<br><br>針對單一使用者安裝每位使用者的 MSI 套件。<br><br>針對裝置上的所有使用者安裝每部電腦的 MSI 套件。<br><br>目前只有裝置上的所有使用者可安裝雙重模式的 MSI 封裝。<br><br>當各版的 MSI 產品代碼相同時，支援應用程式更新。<br>
所有的軟體安裝程式應用程式類型都會上傳到您的雲端儲存空間。

### <a name="external-link"></a>**外部連結**
當您有下列各項時，請使用外部連結：
- 可讓使用者從 App Store 下載應用程式的 URL。
- 可從網頁瀏覽器執行 Web 應用程式的連結。

根據外部連結的應用程式不會儲存在您的 Intune 雲端儲存空間。
### <a name="managed-ios-app-from-the-app-store"></a>**App Store 中的受管理 iOS 應用程式**
您可以使用受管理 iOS 應用程式，管理和部署 App Store 的免費 iOS 應用程式。 您也可以使用受管理 iOS 應用程式，將[行動應用程式管理原則](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)與[相容的應用程式](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx)產生關聯，並在系統管理員主控台中檢閱其狀態。<br /><br />受管理 iOS 應用程式不會儲存在您的 Intune 雲端儲存空間中。

> [!TIP]
> 在您[設定 MDM 授權單位](prerequisites-for-enrollment.md)為 Intune 前，無法使用行動裝置的選項。

## <a name="intune-software-publisher"></a>Intune 軟體發行者
當您從 Intune 管理主控台新增或修改應用程式時，Microsoft Intune 軟體發行者便會啟動。 您可以從發行者選取和設定軟體安裝程式類型，以便：

- 上傳要儲存在 Intune 雲端儲存空間的應用程式 (電腦的程式或行動裝置的應用程式)。
- 連結到線上商店或 Web 應用程式。

開始使用軟體發行者之前，您必須先安裝 [Microsoft .NET Framework 4.0](https://www.microsoft.com/download/details.aspx?id=17851) 的完整版本。 安裝之後，您可能必須重新啟動電腦，才能正確開啟軟體發行者。

## <a name="cloud-storage-space"></a>雲端儲存空間
使用軟體安裝程式安裝類型所建立的所有應用程式都必須上傳至 Microsoft Intune 雲端儲存空間。 Intune 的試用版訂閱內容包含 2 GB 的雲端式儲存空間，可用來儲存受管理的應用程式和更新。 完整訂閱將包含 20 GB 的儲存空間。

您可以在 [系統管理] 工作區的 [使用的存放裝置] 節點中，查看您正在使用的空間量。 您可以使用原始購買方法來購買 Intune 的額外存放空間。  如果您是用發票或信用卡支付，請前往[訂用帳戶管理入口網站](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions)。  否則，請連絡合作夥伴或銷售人員。

雲端儲存空間需求如下：

-   所有應用程式安裝檔案必須位於相同的資料夾。
-   您上傳的任何檔案其檔案大小上限都是 2 GB。


## <a name="support-for-universal-windows-platform-uwp-apps"></a>支援通用 Windows 平台 (UWP) 應用程式
Windows 10 電腦不需要側載金鑰，即可安裝商務營運應用程式。 不過，登錄機碼 **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** 的值必須為 **1** 才能啟用側載。

如果未設定此登錄機碼，Intune 就會在您初次將應用程式部署到裝置時，自動將此值設為 **1**。 如果您已將此值設為 **0**，Intune 即無法自動變更此值，因此部署商務營運應用程式會失敗。

通用 Windows 平台商務營運應用程式必須經過程式碼簽署憑證，而且此憑證受到部署該應用程式的每部目標裝置信任。 您可以使用來自內部公開金鑰基礎結構 (PKI) 的憑證，也可以使用安裝於裝置上的協力廠商公用根憑證。

在 Windows 10 行動裝置版的裝置上，您可以使用非 Symantec 的程式碼簽署憑證來簽署通用 **.appx** 應用程式。 要安裝於 Windows 10 行動裝置版裝置的 **.xap** 應用程式以及針對 Windows Phone 8.1 所建置的 **.appx** 套件，則必須使用 Symantec 程式碼簽署憑證。

### <a name="dependencies-for-uwp-apps"></a>UWP app 的相依性

當您將 Windows 10 通用 appxbundle 套件新增到 Intune 時，您也必須確定已上傳該 App 的任何相依性。
若要上傳相依性，請確定在建置應用程式時所建立的 [Dependencies] 資料夾是和 .appxbundle 檔案本身位於相同的資料夾。
這樣一來，當您將應用程式上傳到 Intune 時，也會上傳在 [Dependencies] 資料夾中的任何檔案。 下列螢幕擷取畫面將說明此程序：


![如何選取 Windows 10 UWP appxbundle 相依性](./media/w10-dependencies.png)


## <a name="next-steps"></a>後續步驟

您必須先在 Intune 主控台中新增應用程式，然後才能部署它們。 您可以新增適用於[註冊的裝置](add-apps-for-mobile-devices-in-microsoft-intune.md)，或[使用 Intune 用戶端軟體所管理的 Windows 電腦](add-apps-for-windows-pcs-in-microsoft-intune.md)的應用程式。
