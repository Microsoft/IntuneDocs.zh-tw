---
title: 側載 Windows 和 Windows Phone 應用程式
titleSuffix: Microsoft Intune
description: 了解如何簽署企業營運應用程式，讓您可以使用 Intune 部署它們。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4a4c6d40dc729fb72210c455c7819baaf89de3b
ms.sourcegitcommit: a66b5916eaab9cb537e483064efc584a6a63a390
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75691834"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>簽署企業營運應用程式以使用 Intune 將它們部署到 Windows 裝置

身為 Intune 管理員，您可以將企業營運 (LOB) 通用應用程式部署到 Windows 8.1 Desktop 和 Windows 10 Desktop 與行動裝置版的裝置，包括公司入口網站應用程式。 若要將 .appx 應用程式部署到 Windows 8.1 Desktop 和 Windows 10 Desktop 與行動裝置版的裝置，您可以使用來自您 Windows 裝置已經信任之公開憑證授權單位的程式碼簽署憑證，或者，您可以使用自己的憑證授權單位。

 > [!NOTE]
 > Windows 8.1 Desktop 需要有企業原則，才能啟用側載或使用側載金鑰 (針對已加入網域的裝置自動啟用)。 如需詳細資訊，請參閱 [Windows 8 側載](https://blogs.technet.microsoft.com/scd-odtsp/2012/09/27/windows-8-sideloading-requirements-from-technet/) \(英文\)。

## <a name="windows-10-sideloading"></a>Windows 10 側載

在 Windows 10 中，側載與舊版 Windows 不同：

- 您可以使用企業原則來解除鎖定裝置，以進行側載。 Intune 提供稱為「安裝信任的應用程式」的裝置設定原則。 對於已經信任用來簽署 appx 應用程式之憑證的裝置而言，只需將此設定為 <allow>。

- 不需要 Symantec 電話憑證和側載授權金鑰。 不過，如果內部部署憑證授權單位無法使用，則您可能需要從公開憑證授權單位取得程式碼簽署憑證。 如需詳細資訊，請參閱[程式碼簽署簡介](https://docs.microsoft.com/windows/desktop/SecCrypto/cryptography-tools#introduction-to-code-signing) \(英文\)。

### <a name="code-sign-your-app"></a>對您的應用程式進行程式碼簽署

第一個步驟是對您的 appx 套件進行程式碼簽署。 如需詳細資訊，請參閱[使用 SignTool 簽署應用程式套件](https://docs.microsoft.com/windows/uwp/packaging/sign-app-package-using-signtool) \(部分機器翻譯\)。

### <a name="upload-your-app"></a>上傳您的應用程式

接下來，您必須上傳已簽署的 appx 檔案。 如需詳細資訊，請參閱[將 Windows 企業營運應用程式新增至 Microsoft Intune](lob-apps-windows.md)。

如果您視需要將應用程式部署到使用者或裝置，則不需要 Inutne 公司入口網站應用程式。 不過，如果您將應用程式部署為可供使用者使用，則他們可從公用 Microsoft Store 使用公司入口網站應用程式、從商務用私人 Microsoft Store 使用公司入口網站應用程式，或者您必須簽署並手動部署 Intune 公司入口網站應用程式。

### <a name="upload-the-code-signing-certificate"></a>上傳程式碼簽署憑證

如果您的 Windows 10 裝置尚未信任憑證授權單位，則在您簽署 appx 套件並將它上傳至 Intune 服務之後，您需要將程式碼簽署憑證上傳至 Intune 入口網站：

1. 按一下 [用戶端應用程式]
2. 按一下 [Windows 企業憑證]
3. 選取程式碼簽署憑證底下的 [選取檔案]
4. 選取您的 .cer 檔案，然後按一下 [上傳]

現在，任何 Windows 10 Desktop 與行動裝置版的裝置 (Intune 服務已在其中部署 appx) 都將自動下載對應的企業憑證，並將允許應用程式在安裝後啟動。

Intune 只會部署最新上傳的 .cer 檔案。 如果您有多個由與貴組織沒有關聯的不同開發人員所建立的 appx 檔案，則您必須讓他們提供未簽署的 appx 檔案以使用您的憑證進行簽署，或為他們提供貴組織所使用的程式碼簽署憑證。

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>如何更新 Symantec 企業程式碼簽署憑證

用來部署 Windows Phone 8.1 行動裝置應用程式的憑證已於 2019 年 2 月 28 日中止，無法再從 Symantec 續訂。 如果您要部署到 WIndows 10 行動裝置版，則可遵循 [Windows 10 側載](app-sideload-windows.md#windows-10-sideloading)指示，繼續使用 Symantec Desktop Enterprise 程式碼簽署憑證。

## <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>如何安裝企業營運 (LOB) 應用程式的更新憑證

Windows Phone 8.1

一旦現有的 Symantec Mobile Enterprise 程式碼簽署憑證過期之後，Intune 服務就無法再部署適用於此平台的 LOB 應用程式。 您仍然可以藉由使用 SD 記憶卡或將檔案下載至裝置，來側載未簽署的 XAP/APPX 檔案。 如需詳細資訊，請參閱[如何在 Windows Phone 上安裝 XAP 檔案](https://answers.microsoft.com/en-us/mobiledevices/forum/mdlumia-mdapps/how-to-install-xap-file-in-windows-phone-8/da09ee72-51ae-407c-9b85-bc148df89280) \(英文\)。

Windows 8.1 Desktop/Windows 10 Desktop 與行動裝置版

如果憑證期間已過期，則 appx 檔案可能會停止啟動。 您應該取得新的 .cer 檔案，並遵循指示以對每個部署的 appx 檔案進行程式碼簽署，並將所有 appx 檔案和更新的 .cer 檔案重新上傳至 Intune 入口網站的 [Windows 企業憑證] 區段。

## <a name="manually-deploy-windows-10-company-portal-app"></a>手動部署 Windows 10 公司入口網站應用程式

如果您不想提供 Microsoft Store 的存取權限，即使您還沒有整合 Intune 與商務用 Microsoft Store (MSFB)，仍可直接從 Intune 手動部署 Windows 10 公司入口網站應用程式。 或者，如果您已整合，則可透過[使用 MSFB 部署應用程式](store-apps-windows.md)來部署公司入口網站應用程式。

 > [!NOTE]
 > 這個選項將需要在每次應用程式發行更新時，部署手動更新。

1. 在[商務用 Microsoft Store ](https://www.microsoft.com/business-store) 中登入您的帳戶，並取得公司入口網站應用程式的**離線授權**版本。  
2. 取得應用程式之後，在 [詳細目錄]  頁面中選取該應用程式。  
3. 在 [平台]  選取 [Windows 10 所有裝置]  ，然後選取適當的 [架構]  並下載。 此應用程式不需要應用程式授權檔案。
   ![供下載的 Windows 10 X86 套件詳細資料的影像](./media/app-sideload-windows/Win10CP-all-devices.png)
4. 下載「必要架構」底下的所有套件。 x86、x64 及 ARM 架構都要執行這個步驟 – 所以總共 9 個套件，如下圖所示。

   ![要下載之相依性檔案的圖片 ](./media/app-sideload-windows/Win10CP-dependent-files.png)
5. 將公司入口網站應用程式上傳至 Intune 之前，先建立資料夾 (例如 C:&#92;Company Portal)，並以如下結構放置套件︰
   1. 將公司入口網站套件放入 C:\Company Portal。 在此位置中建立 Dependencies 子資料夾。  
      ![已建好 Dependencies 資料夾並存有 APPXBUN 檔案的圖片](./media/app-sideload-windows/Win10CP-Dependencies-save.png)
   2. 將 9 個相依性套件放在 Dependencies 資料夾中。  
      如果相依性套件未依如此方式放置，Intune 將無法在套件上傳期間辨識及上傳這些項目，而導致上傳失敗並出現下列錯誤。  
      ![錯誤訊息 - 必須提供 Windows 應用程式相依性。](./media/app-sideload-windows/Win10CP-error-message.png)
6. 返回 Intune，將公司入口網站應用程式上傳為新應用程式。 針對所需的目標使用者群，將其部署為必要的應用程式。  

有關 Intune 如何處理通用應用程式的相依性，詳細資訊請參閱[透過 Microsoft Intune MDM 部署具相依性的 appxbundle](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/)。  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>如果使用者已從市集安裝較舊的公司入口網站應用程式，我如何能更新他們裝置上的公司入口網站應用程式？

如果您的使用者已經從市集安裝 Windows 8.1 或 Windows Phone 8.1 公司入口網站應用程式，則他們的裝置應該會自動更新到新版本，您或您的使用者不需要採取任何動作。 如果更新沒發生，請使用者確認他們已在其裝置上啟用自動更新市集應用程式。

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何將我側載的 Windows 8.1 公司入口網站應用程式升級至 Windows 10 公司入口網站應用程式？

我們建議的移轉方式是刪除 Windows 8.1 公司入口網站應用程式的部署，做法是將部署動作設定為「解除安裝」。 完成後，可以使用任何上述選項部署 Windows 10 公司入口網站應用程式。  

如果您需要側載應用程式，且您部署 Windows 8.1 公司入口網站時未使用 Symantec 憑證簽署它，請遵循之前「透過 Intune 直接部署」一節所述步驟完成升級。

如果您需要側載應用程式，且您已使用 Symantec 程式碼簽署憑證簽署及部署 Windows 8.1 公司入口網站，請遵循下一節的步驟。  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何將我已簽署及側載的 Windows Phone 8.1 公司入口網站應用程式或 Windows 8.1 公司入口網站應用程式，升級至 Windows 10 公司入口網站應用程式？

我們建議的移轉方式是刪除 Windows Phone 8.1 公司入口網站應用程式或 Windows 8.1 公司入口網站應用程式的現有部署，做法是將部署動作設定為「解除安裝」。 完成後，便可以正常部署 Windows 10 公司入口網站應用程式。  

否則，必須適當地更新及簽署 Windows 10 公司入口網站應用程式，以確保遵循升級方式。  

如果是以這種方式簽署及部署 Windows 10 公司入口網站應用程式，每當市集內有新的應用程式更新時，您就必須為每個應用程式重複此程序。 當市集更新時，應用程式不會自動更新。  

以下說明如何以此方式簽署和部署應用程式︰

1. 從 [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript) 下載「Microsoft Intune Windows 10 公司入口網站應用程式簽署指令碼」。  此指令碼需要在主機電腦上安裝適用於 Windows 10 的 Windows SDK。 若要下載適用於 Windows 10 的 Windows SDK，請瀏覽 [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296)。
2. 從商務用 Microsoft 網上商店下載 Windows 10 公司入口網站應用程式，詳如前述。  
3. 搭配輸入參數執行詳載於指令碼標頭內的指令碼，簽署 Windows 10 公司入口網站應用程式 (摘錄於下)。 相依性不需要傳遞至指令碼。 這些只有在將應用程式上傳至 Intune 管理主控台時才需要。

|       參數       |                                                                    說明                                                                    |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                             來源 appxbundle 檔案所在路徑。                                              |
| OutputWin10AppxBundle |                                                  已簽署之 appxbundle 檔案的輸出路徑。                                                  |
|       Win81Appx       |                          Windows 8.1 或 Windows Phone 8.1 公司入口網站 (.APPX) 檔案所在路徑。                           |
|      PfxFilePath      |                                   Symantec 企業行動程式碼簽署憑證 (.PFX) 的路徑。                                    |
|      PfxPassword      |                                     Symantec 企業行動程式碼簽署憑證的密碼。                                      |
|      PublisherId      |      企業的發行者識別碼。 如果這個參數不存在，則會使用 Symantec 企業行動程式碼簽署憑證的 [主旨] 欄位。       |
|        SdkPath        | 適用於 Windows 10 之 Windows SDK 的根資料夾路徑。 這個引數是選擇性，且預設值為 ${env:ProgramFiles(x86)}\Windows Kits\10 |

指令碼執行完成時，會輸出簽署版的 Windows 10 公司入口網站應用程式。 然後，您可以透過 Intune 將簽署版的應用程式部署為 LOB 應用程式，這會將目前部署的版本升級至此新應用程式。  
