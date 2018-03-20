---
title: "手動新增 Windows 10 公司入口網站應用程式"
titleSuffix: Microsoft Intune
description: "了解如何手動新增 Windows 10 公司入口網站應用程式。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 06ed9395d06e2d64edcedcaadfe819ad03f1d495
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="manually-add-the-windows-10-company-portal-app-using-microsoft-intune"></a>使用 Microsoft Intune 手動新增 Windows 10 公司入口網站應用程式

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

終端使用者可以從 Microsoft 網上商店安裝公司入口網站應用程式，以管理裝置及安裝應用程式。 不過，如果因企業需求而必須指派公司入口網站應用程式，即使尚未整合 Intune 與商務用 Microsoft 網上商店，您仍然可直接從 Intune 手動指派 Windows 10 公司入口網站應用程式。

 > [!NOTE]
 > 這個選項將需要在每次應用程式發行更新時，指派手動更新。

## <a name="configure-settings-to-show-offline-apps"></a>組態設定以顯示離線應用程式
1. 移至 [商務用 Microsoft Store](https://www.microsoft.com/business-store) 並確定您已使用系統管理員帳戶登入。
2. 選取靠近視窗頂端的 [管理] 索引標籤。
3. 在左側導覽行上選取 [設定]。
4. 在 [購物體驗] 區段中，將 [顯示離線應用程式] 設定為 [開啟]。 這會在商務用 Microsoft Store 中顯示離線授權應用程式。

## <a name="download-the-offline-company-portal-app"></a>下載離線公司入口網站應用程式
1. 搜尋並選取 [公司入口網站] 應用程式。
2. 將 [授權類型] 設定為 [離線]。
3. 按一下 [取得應用程式] 以取得離線公司入口網站應用程式，並將其新增至您的清查。
4. 在 [公司入口網站] 應用程式頁面按一下 [管理]。
5. 在 [平台] 選取 [Windows 10 所有裝置]，然後選取適當的 [最小版本]、[架構]，並下載應用程式中繼資料** 值。 
6. 按一下 [下載] 將檔案儲存至本機電腦。

    ![Windows 10 所有裝置和供下載之 X86 架構套件詳細資料的圖片](./media/Win10CP-all-devices.png)

7. 下載「必要架構」底下的所有套件。 x86、x64 及 ARM 架構都要執行這個步驟，共 12 個套件。
8. 將公司入口網站應用程式上傳至 Intune 之前，先建立資料夾 (例如：C:&#92;Company Portal)，並以如下結構放置套件︰
  - 將公司入口網站套件放入 C:\Company Portal。 在此位置中建立 Dependencies 子資料夾。  

    ![已建好 Dependencies 資料夾並存有 APPXBUN 檔案的圖片](./media/Win10CP-Dependencies-save.png)

  - 將相依性套件放在 *Dependencies* 資料夾中。 

     > [!NOTE]
     > 如果相依性套件未依正確方式放置，Intune 將無法在套件上傳期間辨識及上傳這些項目，而導致上傳失敗並顯示錯誤。

9. 回到 Azure 入口網站中的 Microsoft Intune。
10. 上傳公司入口網站應用程式作為新的應用程式。 針對所需的目標使用者群，將其指派為必要的應用程式。  

有關 Intune 如何處理通用應用程式的相依性，詳細資訊請參閱[透過 Microsoft Intune MDM 部署具相依性的 appxbundle](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/)。  

## <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>如果使用者已從市集安裝較舊的公司入口網站應用程式，我如何能更新他們裝置上的公司入口網站應用程式？
如果您的使用者已經從市集安裝 Windows 8.1 或 Windows Phone 8.1 公司入口網站應用程式，則他們的裝置應該會自動更新到新版本，您或您的使用者不需要採取任何動作。 如果更新沒發生，請使用者確認他們已在其裝置上啟用自動更新市集應用程式。   

## <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何將我側載的 Windows 8.1 公司入口網站應用程式升級至 Windows 10 公司入口網站應用程式？
我們建議的移轉路徑是刪除 Windows 8.1 公司入口網站應用程式的指派，做法是將指派動作設定為「解除安裝」。 進行此設定之後，就可以使用上述任何選項來指派 Windows 10 公司入口網站應用程式。  

如果您需要側載應用程式並指派 Windows 8.1 公司入口網站，但不使用 Symantec 憑證來簽署，請遵循之前＜透過 Intune 直接指派＞一節所述步驟完成升級。

如果您需要側載應用程式，並使用 Symantec 程式碼簽署憑證來簽署及指派 Windows 8.1 公司入口網站，請遵循下一節的步驟。  

## <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何將我已簽署及側載的 Windows Phone 8.1 公司入口網站應用程式或 Windows 8.1 公司入口網站應用程式，升級至 Windows 10 公司入口網站應用程式？
我們建議的移轉路徑是刪除 Windows Phone 8.1 公司入口網站應用程式或 Windows 8.1 公司入口網站應用程式的現有指派，做法是將指派動作設定為「解除安裝」。 進行此設定之後，就可以正常指派 Windows 10 公司入口網站應用程式。  

否則，必須適當地更新及簽署 Windows 10 公司入口網站應用程式，以確保遵循升級方式。  

如果是以這種方式簽署及指派 Windows 10 公司入口網站應用程式，每當市集內有新的應用程式更新時，您就必須為每個應用程式重複此程序。 當市集更新時，應用程式不會自動更新。  

以下是以這種方式簽署和指派應用程式的方法：

1. 從 [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript) 下載 Microsoft Intune Windows 10 公司入口網站應用程式簽署指令碼。  此指令碼需要在主機電腦上安裝適用於 Windows 10 的 Windows SDK。 若要下載適用於 Windows 10 的 Windows SDK，請前往 [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296)。
2. 從商務用 Microsoft 網上商店下載 Windows 10 公司入口網站應用程式，詳如前述。  
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

## <a name="next-steps"></a>接下來的步驟

- [如何將應用程式指派到群組](apps-deploy.md)

