---
title: "如何將 Windows 市集應用程式新增至 Intune"
titleSuffix: Intune on Azure
description: "了解如何將 Windows 市集應用程式新增至 Intune。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7ad1156076f0ec34d5ac110e32a19a8332c8f863
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-add-windows-store-apps-to-microsoft-intune"></a>如何將 Windows 市集應用程式新增至 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 **Intune** 刀鋒視窗上選擇 [管理應用程式]。
4. 在**行動應用程式**工作負載中選擇 [管理]  >  [應用程式]。
5. 從應用程式清單上方選擇 [新增]。
6. 在 [新增應用程式] 刀鋒視窗中選擇 [應用程式資訊]。
7. 在 [編輯應用程式] 刀鋒視窗中設定下列資訊。 完成設定後，按一下 [新增]。 刀鋒視窗中有一些值會隨所選的應用程式自動填入︰
    - **名稱** - 輸入要顯示在公司入口網站中的應用程式名稱。 確定您使用的所有應用程式名稱都是唯一的。 如果有重複的應用程式名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **描述** - 輸入應用程式的描述。 使用者會在公司入口網站中看到這個描述。
    - **發行者** - 輸入應用程式的發行者名稱。
    - **App Store URL** - 輸入您要建立之應用程式的 App Store URL。
    - **最小作業系統** - 從清單中選擇應用程式所能安裝的最小作業系統版本。 若將應用程式指派給安裝舊版作業系統的裝置，就不會進行安裝。
    - **類別 (選用)** - 選取一或多個內建應用程式類別，或選取您建立的類別。 這可以讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式** - 當使用者瀏覽應用程式時，以醒目方式在公司入口網站的主頁面上顯示此應用程式。
    - **資訊 URL** - 選擇是否要輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL** - 選擇是否要輸入包含此應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員** - 選擇是否要輸入應用程式開發人員的姓名。
    - **擁有者** - 選擇是否要輸入此應用程式的擁有者名稱，例如**人力資源部門**。
    - **注意** - 輸入要與此應用程式相關聯的附註。
    - **上傳圖示** - 上傳應用程式所要關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
8. 完成之後，請在 [新增應用程式] 刀鋒視窗中選擇 [儲存]。

您建立的應用程式將會顯示在應用程式清單中，而您可從中將應用程式指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](apps-deploy.md)。

## <a name="manually-assign-windows-10-company-portal-app"></a>手動指派 Windows 10 公司入口網站應用程式
終端使用者可以從 Windows 市集安裝公司入口網站應用程式，以管理裝置及安裝應用程式。 不過，如果因企業需求而必須指派公司入口網站應用程式，即使尚未整合 Intune 與商務用 Windows 市集，您仍然可直接從 Intune 手動指派 Windows 10 公司入口網站應用程式。

 > [!NOTE]
 > 這個選項將需要在每次應用程式發行更新時，指派手動更新。

1. 在[商務用 Windows 市集](https://www.microsoft.com/business-store)登入您的帳戶，取得公司入口網站應用程式的**離線授權**版本。  
2. 取得應用程式之後，在 [詳細目錄] 頁面中選取該應用程式。  
3. 在 [平台] 選取 [Windows 10 所有裝置]，然後選取適當的 [架構] 並下載。 此應用程式不需要應用程式授權檔案。
![Windows 10 所有裝置和供下載之 X86 架構套件詳細資料的圖片](./media/Win10CP-all-devices.png)
4. 下載「必要架構」底下的所有套件。 x86、x64 及 ARM 架構都要執行這個步驟 – 所以總共 9 個套件，如下圖所示。

![要下載之相依性檔案的圖片 ](./media/Win10CP-dependent-files.png)
5. 將公司入口網站應用程式上傳至 Intune 之前，先建立資料夾 (例如 C:&#92;Company Portal)，並以如下結構放置套件︰
  1. 將公司入口網站套件放入 C:\Company Portal。 在此位置中建立 Dependencies 子資料夾。  
  ![已建好 Dependencies 資料夾並存有 APPXBUN 檔案的圖片](./media/Win10CP-Dependencies-save.png)
  2. 將 9 個相依性套件放在 Dependencies 資料夾中。  
  如果相依性套件未依如此方式放置，Intune 將無法在套件上傳期間辨識及上傳這些項目，而導致上傳失敗並出現下列錯誤。  
  ![在應用程式資料夾中找不到此軟體安裝程式的 Windows 應用程式相依性。 您可以繼續建立並指派此應用程式，但必須等到提供遺失的 Windows 應用程式相依性之後，它才能執行。](./media/Win10CP-error-message.png)
6. 返回 Intune，將公司入口網站應用程式上傳為新應用程式。 針對所需的目標使用者群，將其指派為必要的應用程式。  

有關 Intune 如何處理通用應用程式的相依性，詳細資訊請參閱[透過 Microsoft Intune MDM 部署具相依性的 appxbundle](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/)。  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>如果使用者已從市集安裝較舊的公司入口網站應用程式，我如何能更新他們裝置上的公司入口網站應用程式？
如果您的使用者已經從市集安裝 Windows 8.1 或 Windows Phone 8.1 公司入口網站應用程式，則他們的裝置應該會自動更新到新版本，您或您的使用者不需要採取任何動作。 如果更新沒發生，請使用者確認他們已在其裝置上啟用自動更新市集應用程式。   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何將我側載的 Windows 8.1 公司入口網站應用程式升級至 Windows 10 公司入口網站應用程式？
我們建議的移轉路徑是刪除 Windows 8.1 公司入口網站應用程式的指派，做法是將指派動作設定為「解除安裝」。 完成後，就可以使用上述任何選項來指派 Windows 10 公司入口網站應用程式。  

如果您需要側載應用程式並指派 Windows 8.1 公司入口網站，但不使用 Symantec 憑證來簽署，請遵循之前＜透過 Intune 直接指派＞一節所述步驟完成升級。

如果您需要側載應用程式，並使用 Symantec 程式碼簽署憑證來簽署及指派 Windows 8.1 公司入口網站，請遵循下一節的步驟。  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何將我已簽署及側載的 Windows Phone 8.1 公司入口網站應用程式或 Windows 8.1 公司入口網站應用程式，升級至 Windows 10 公司入口網站應用程式？
我們建議的移轉路徑是刪除 Windows Phone 8.1 公司入口網站應用程式或 Windows 8.1 公司入口網站應用程式的現有指派，做法是將指派動作設定為「解除安裝」。 完成後，便可以正常指派 Windows 10 公司入口網站應用程式。  

否則，必須適當地更新及簽署 Windows 10 公司入口網站應用程式，以確保遵循升級方式。  

如果是以這種方式簽署及指派 Windows 10 公司入口網站應用程式，每當市集內有新的應用程式更新時，您就必須為每個應用程式重複此程序。 當市集更新時，應用程式不會自動更新。  

以下是以這種方式簽署和指派應用程式的方法：

1. 從 [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript) 下載 Microsoft Intune Windows 10 公司入口網站應用程式簽署指令碼。  此指令碼需要在主機電腦上安裝適用於 Windows 10 的 Windows SDK。 若要下載適用於 Windows 10 的 Windows SDK，請前往 [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296)。
2. 從商務用 Windows 市集下載 Windows 10 公司入口網站應用程式，詳如前述。  
3. 搭配輸入參數執行詳載於指令碼標頭內的指令碼，簽署 Windows 10 公司入口網站應用程式 (摘錄於下)。 相依性不需要傳遞至指令碼。 這些只有在將應用程式上傳至 Intune 管理主控台時才需要。

|參數 | 說明|
| ------------- | ------------- |
|InputWin10AppxBundle |來源 appxbundle 檔案所在路徑。 |
|OutputWin10AppxBundle |已簽署之 appxbundle 檔案的輸出路徑。  Win81Appx Windows 8.1 或 Windows Phone 8.1 公司入口網站 (.APPX) 檔案所在路徑。|
|PfxFilePath |Symantec 企業行動程式碼簽署憑證 (.PFX) 的路徑。 |
|PfxPassword| Symantec 企業行動程式碼簽署憑證的密碼。 |
|PublisherId |企業的發行者識別碼。 如果這個參數不存在，則會使用 Symantec 企業行動程式碼簽署憑證的 [主旨] 欄位。|
|SdkPath | 適用於 Windows 10 之 Windows SDK 的根資料夾路徑。 這個引數是選擇性，且預設值為 ${env:ProgramFiles(x86)}\Windows Kits\10|
指令碼執行完成時，會輸出簽署版的 Windows 10 公司入口網站應用程式。 然後，您可以透過 Intune 將應用程式經過簽署的版本指派為 LOB 應用程式，這會將目前指派的版本升級至此新應用程式。  
