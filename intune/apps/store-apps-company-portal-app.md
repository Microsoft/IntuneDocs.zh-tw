---
title: 手動新增 Windows 10 公司入口網站應用程式
titleSuffix: Microsoft Intune
description: 了解您的員工如何手動從 Microsoft Store 將 Windows 10 公司入口網站應用程式新增到他們的電腦上。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 31fcc3a47a131ca017e3691cc53a7295b81fe67c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724590"
---
# <a name="manually-add-the-windows-10-company-portal-app-by-using-microsoft-intune"></a>使用 Microsoft Intune 手動新增 Windows 10 公司入口網站應用程式

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

使用者可以透過 Microsoft Store 自行安裝公司入口網站應用程式，以管理裝置及安裝應用程式。 不過，如果企業需要由您指派公司入口網站應用程式給使用者，您也可以直接透過 Intune 手動指派 Windows 10 公司入口網站應用程式。 即使尚未整合 Intune 與商務用 Microsoft Store，您仍可以進行上述作業。

 > [!NOTE]
 > 本文中所述的選項需要您在每次應用程式更新發行之後指派手動更新。

## <a name="configure-settings-to-show-offline-apps"></a>組態設定以顯示離線應用程式
1. 使用您的系統管理員帳戶，登入[商務用 Microsoft Store](https://www.microsoft.com/business-store)。
2. 選取靠近視窗頂端的 [管理]  索引標籤。
3. 在左窗格中，選取 [設定]  。
4. 在 [購物體驗]  下方，將 [顯示離線應用程式]  設定為 [開啟]  。  
    隨即顯示離線授權應用程式。

## <a name="download-the-offline-company-portal-app"></a>下載離線公司入口網站應用程式
1. 搜尋「公司入口網站」  應用程式，然後加以選取。
2. 將 [授權類型]  設定為 [離線]  。
3. 選取 [取得應用程式]  ，以取得離線公司入口網站應用程式，並將其新增至您的清查。
4. 選取「公司入口網站」  應用程式頁面的 [管理]  。
5. 針對 [平台]  ，選取 [Windows 10 所有裝置]  ，然後選取適當的 [最低版本]  、[架構]  ，以及 [下載應用程式中繼資料]  值。 
6. 選取 [套件詳細資料]  底下的 [下載]  ，將檔案儲存至本機電腦。

    ![選取架構等於 X86 的 Windows 10 裝置](./media/app-sideload-windows/Win10CP-all-devices.png)

7. 選取 [下載]  ，即可下載「必要架構」底下的所有套件。  

    您必須針對 x86、x64 及 ARM 架構完成此動作：<br> 
    *選取 1507 作為最低 OS 版本時有 9 個必要的 Framework 套件、選取 1511 時有 12 個套件，而選取 1607 時有 15 個套件。*

8. 在 Azure 入口網站的 Microsoft Intune 中，將公司入口網站應用程式上傳為新的應用程式。 您必須在 [新增應用程式]  窗格中選取 [企業營運應用程式] 作為 [應用程式類型]  來新增應用程式。 然後，選取應用程式套件檔案 (副檔名為 .AppxBundle)。

9. 在 [選取相依性應用程式檔案]  下，透過按住 Shift 鍵並選取您在步驟 7 中下載的所有相依性，然後確認 [已新增]  資料行針對您所需的架構顯示 [是]  。

     > [!NOTE]
     > 如果未新增相依性，應用程式可能不會安裝在指定的裝置類型上。

10. 按一下 [確定]  ，輸入所需的 [應用程式資訊]  ，然後按一下 [新增]  。

11. 針對您所選的一組使用者或裝置群組，將公司入口網站應用程式指派為他們的必要應用程式。  

如需 Intune 對通用應用程式相依性的處理方式詳細資訊，請參閱[透過 Microsoft Intune MDM 部署具相依性的 appxbundle](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/)。  

## <a name="frequently-asked-questions"></a>常見問題集 
### <a name="how-do-i-update-the-company-portal-app-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>如果使用者已從市集安裝舊版的公司入口網站應用程式，該如何更新他們裝置上的公司入口網站應用程式？
如果使用者已經從 Microsoft Store 安裝 Windows 8.1 或 Windows Phone 8.1 公司入口網站應用程式，他們的應用程式應該會自動更新到最新版本，而不需要您或使用者採取任何動作。 如果未進行更新，請使用者確認他們是否已在裝置上啟用市集應用程式的自動更新。   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何將我側載的 Windows 8.1 公司入口網站應用程式升級至 Windows 10 公司入口網站應用程式？
我們建議的移轉路徑是將指派動作設為 [解除安裝]  ，以刪除 Windows 8.1 公司入口網站應用程式的指派。 選取此設定之後，您即可使用先前說明過的任何選項，來指派 Windows 10 公司入口網站應用程式。  

如果您需要側載應用程式，但您已指派 Windows 8.1 公司入口網站，而未使用 Symantec 憑證來簽署，請遵循本文上述幾節的步驟完成升級。

如果您需要側載應用程式，但您已使用 Symantec 程式碼簽署憑證來簽署及指派 Windows 8.1 公司入口網站應用程式，請遵循下一節中的步驟。

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>如何將我已簽署及側載的 Windows Phone 8.1 公司入口網站應用程式或 Windows 8.1 公司入口網站應用程式，升級至 Windows 10 公司入口網站應用程式？
我們建議的移轉路徑是將指派動作設為 [解除安裝]  ，以刪除 Windows Phone 8.1 公司入口網站應用程式或 Windows 8.1 公司入口網站應用程式的現有指派。 選取此設定之後，您即可正常指派 Windows 10 公司入口網站應用程式。  

否則，必須適當地更新及簽署 Windows 10 公司入口網站應用程式，以確保遵循升級路徑。  

如果是以這種方式簽署及指派 Windows 10 公司入口網站應用程式，則每當市集內有新的應用程式更新時，您就必須為每個應用程式重複此程序。 因為當市集更新時，應用程式不會自動更新。  

以下是以這種方式簽署和指派應用程式的方法：

1. 下載 [Microsoft Intune Windows 10 公司入口網站應用程式簽署指令碼](https://aka.ms/win10cpscript)。  
    此指令碼需要在主機電腦上安裝適用於 Windows 10 的 Windows SDK。 [下載適用於 Windows 10 的 Windows SDK](https://go.microsoft.com/fwlink/?LinkId=619296)。
2. 如之前所述，從商務用 Microsoft Store 下載 Windows 10 公司入口網站應用程式。  
3. 若要簽署 Windows 10 公司入口網站應用程式，請使用輸入參數來執行指令碼，這些參數詳載於指令碼標頭內，如下表所示。  
    相依性不需要傳遞至指令碼。 只有在將應用程式上傳至 Intune 管理主控台時，才需要這些項目。

| 參數 |  說明  |
|---|---|
| InputWin10AppxBundle  |  來源 appxbundle 檔案的路徑。 |
| OutputWin10AppxBundle | 已簽署之 appxbundle 檔案的輸出路徑。 
| Win81Appx  | Windows 8.1 或 Windows Phone 8.1 公司入口網站 (.APPX) 檔案的路徑。 |
| PfxFilePath  |  Symantec 企業行動程式碼簽署憑證 (.PFX) 的路徑。  |
| PfxPassword  | Symantec 企業行動程式碼簽署憑證的密碼。 |
| PublisherId | 企業的發行者識別碼。 如果這個參數不存在，則會使用 Symantec 企業行動程式碼簽署憑證的 [主旨] 欄位。 |
| SdkPath | 適用於 Windows 10 之 Windows SDK 的根資料夾路徑。 這個引數是選擇性，且預設值為 ${env:ProgramFiles(x86)}\Windows Kits\10。  |

指令碼執行完成時，會輸出簽署版的 Windows 10 公司入口網站應用程式。 然後，您可以透過 Intune 將簽署版的應用程式指派為企業營運 (LOB) 應用程式，以將目前指派的版本升級至這個新的應用程式。  

## <a name="next-steps"></a>後續步驟

- [將應用程式指派給群組](apps-deploy.md)

