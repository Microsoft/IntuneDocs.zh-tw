---
title: "使用 Intune 將 Office 365 ProPlus 應用程式安裝到 Windows 10 裝置"
titleSuffix: Intune on Azure
description: "了解如何使用 Intune 以更容易在 Windows 10 裝置上安裝 Office 365 應用程式。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 471b4dd524cea553af89acc3e158fd2a05cebe3d
ms.sourcegitcommit: c8fb42fcb8735af432c7e07c380d956171012bd4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2017
---
# <a name="how-to-assign-office-365-proplus-2016-apps-to-windows-10-devices-with-microsoft-intune"></a>如何使用 Microsoft Intune 將 Office 365 ProPlus 2016 應用程式指派給 Windows 10 裝置

此應用程式類型方便您將 Office 365 ProPlus 2016 應用程式指派給由您管理且執行 Windows 10 的裝置。 若有其授權，您也可以安裝適用於 Microsoft Project Online 桌面用戶端以及 Microsoft Visio Pro for Office 365 的應用程式。 您希望在 Intune 主控台的應用程式清單中，顯示為一個應用程式的那些應用程式。


## <a name="before-you-start"></a>開始之前

>[!IMPORTANT]
>這種安裝 Office 的方法，只有在裝置上未安裝其他版本的 Microsoft Office 時才支援。

- 部署這些應用程式的裝置必須執行 Windows 10 Creators Update 或更新版本。
- Intune 僅支援從 Office 365 ProPlus 2016 套件新增 Office 應用程式。
- 如果在 Intune 安裝應用程式套件時有任何 Office 應用程式是開啟的，使用者未儲存的檔案可能會遺失資料。
- Windows 10S 裝置不支援此安裝方法。
- Intune 不支援在已使用 Intune 部署 Office 365 應用程式的裝置上，安裝來自 Windows 市集的 Office 365 傳統型應用程式 (又稱為 Office Centennial 應用程式)。 如果您安裝此設定，可能會導致資料遺失或損毀。


## <a name="get-started"></a>開始使用

1.  登入 Azure 入口網站。
2.  選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3.  在 [Intune] 刀鋒視窗上，選擇 [行動應用程式]。
4.  在**行動應用程式**工作負載中選擇 [管理]  >  [應用程式]。
5.  從應用程式清單上方選擇 [新增]。
6.  在 [新增應用程式] 刀鋒視窗中，選擇 [Office 365 ProPlus Suite (Windows 10)] (Office 365 ProPlus 套件 (Windows 10))。

## <a name="configure-the-app-suite"></a>設定應用程式套件

在此步驟中，選擇您想要指派給裝置的 Office 應用程式。

1.  在 [新增應用程式] 刀鋒視窗上選擇 [Configure App Suite] (設定應用程式套件)。
2.  在 [Configure App Suite] (設定應用程式套件) 刀鋒視窗中，選擇您想要指派給裝置的標準 Office 應用程式。 此外，若有其授權，您也可以安裝適用於 Microsoft Project Online 桌面用戶端以及 Microsoft Visio Pro for Office 365 的應用程式。
3.  完成之後，請按一下 [確定] 。

>[!IMPORTANT]
> 建立應用程式套件之後，即無法編輯其屬性。 若要設定不同的屬性，請刪除應用程式套件，另外新建一個。

## <a name="configure-app-information"></a>設定應用程式資訊

在此步驟中，提供應用程式套件的相關資訊。 這項資訊可協助您在 Intune 主控台中識別它，同時也能幫助使用者在公司入口網站應用程式中尋找它。

1.  在 [新增應用程式] 刀鋒視窗中選擇 [App Suite Information] (應用程式套件資訊)。
2.  在 [App Suite Information] (應用程式套件資訊) 刀鋒視窗中，指定下列資訊： 
    - **套件名稱** - 輸入應用程式套件要顯示在公司入口網站中的名稱。 確定使用的所有套件名稱都是唯一的。 如果有重複的應用程式套件名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **套件描述** - 輸入應用程式套件的描述。 例如，您可以列出已選取包含的應用程式。
    - **發行者** - 輸入應用程式的發行者名稱。
    - **類別** - 或者選取一或多個內建應用程式類別，或您建立的類別。 這可讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式套件。
    - **將此顯示為公司入口網站中的精選應用程式** - 當使用者瀏覽應用程式時，以醒目方式在公司入口網站的主頁面上顯示此應用程式套件。
    - **資訊 URL** - 選擇是否要輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL** - 選擇是否要輸入包含此應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員** - 選擇是否要輸入應用程式開發人員的姓名。
    - **擁有者** - 選擇是否要輸入此應用程式的擁有者名稱，例如**人力資源部門**。
    - **注意** - 輸入要與此應用程式相關聯的附註。
    - **上傳圖示** - 上傳當使用者瀏覽公司入口網站時，隨應用程式一起顯示的圖示。
3.  完成之後，請按一下 [確定] 。

## <a name="configure-app-settings"></a>設定應用程式設定

在此步驟中，設定應用程式套件的安裝選項。 此設定適用於您新增至套件的所有應用程式。

1.  在 [新增應用程式] 刀鋒視窗中選擇 [App Suite Settings] (應用程式套件設定)。
2.  在 [App Suite Settings] (應用程式套件設定) 刀鋒視窗中，指定下列資訊： 
    - **Office 版本** - 選擇要指派 32 位元還是 64 位元版本的 Office。 32 位元版本可以安裝在 32 位元和 64 位元的裝置上，但 64 位元版本只能安裝在 64 位元的裝置。
    - **更新頻道** - 選擇裝置更新 Office 的方式。 如需不同更新頻道的相關資訊，請參閱＜Office 365 ProPlus 更新頻道概觀＞。 從下列選項進行選擇： 
        - **目前**
        - **延遲**
        - **初次發行，目前**
        - **初次發行，延遲**
    - **自動接受應用程式的使用者授權合約** - 如果您不需要使用者接受授權合約，請選取此選項。 Intune 會自動接受合約。
    - **使用共用的電腦啟用** - 有多位使用者共用一部電腦時使用共用的電腦啟用。 如需詳細資訊，請參閱 ＜Office 365 專業增強版的共用電腦啟用概觀＞。
    - **語言** - Office 會自動以終端使用者裝置上與 Windows 一起安裝的任何受支援的語言安裝。 如果想要使用其他語言安裝應用程式套件，請選取此選項。

>[!IMPORTANT]
> 建立應用程式套件之後，即無法編輯其屬性。 若要設定不同的屬性，請刪除應用程式套件，另外新建一個。

## <a name="finish-up"></a>完成

完成之後，請在 [新增應用程式] 刀鋒視窗中選擇 [儲存]。 您已建立的應用程式會顯示在應用程式清單中。

## <a name="error-codes-when-installing-the-app-suite"></a>安裝應用程式套件時的錯誤碼

下表列出您可能會遇到的常見錯誤碼及其意義。

### <a name="status-for-office-csp"></a>Office CSP 狀態： 

||||
|-|-|-|
|狀態|階段|描述|
|1460 (ERROR_TIMEOUT)|下載|無法下載 Office 部署工具|    
|13 (ERROR_INVALID_DATA)|-|無法驗證下載的 Office 部署工具簽章| 
|來自 CertVerifyCertificateChainPolicy 的錯誤碼|-|對下載的 Office 部署工具的憑證檢查失敗|    
|997|WIP|安裝| 
|0|安裝後|安裝成功|    
|1603 (ERROR_INSTALL_FAILURE)|-|任何必要條件檢查皆失敗，例如：<br>- SxS (已安裝 2016 MSI 時嘗試安裝)<br>- 版本不符<br>- 等等|     
|0x8000ffff (E_UNEXPECTED)|-|電腦上沒有隨選即用 Office 時嘗試解除安裝。|    
|17002|-|無法完成案例 (安裝)。 可能的原因：<br>- 使用者已取消安裝<br>- 其他安裝已取消安裝<br>- 安裝期間磁碟空間不足<br>- 未知的語言識別碼| 
|17004|-|未知的 SKU|   


### <a name="office-deployment-tool-error-codes"></a>Office 部署工具錯誤碼

|||||
|-|-|-|-|
|案例|傳回碼|UI|注意| 
|沒有任何使用中的隨選即用安裝時即解除安裝|-2147418113、0x8000ffff 或 2147549183|錯誤碼：30088-1008<br>錯誤碼：30125-1011 (404)|Office 部署工具| 
|已安裝 MSI 版本時安裝|1603|-|Office 部署工具| 
|使用者或另一個安裝已取消安裝|17002|-|隨選即用| 
|嘗試在已安裝 32 位元的裝置上安裝 64 位元。|1603|-|Office 部署工具傳回碼| 
|嘗試安裝未知的 SKU (Office CSP 的不合法使用案例，因為我們應該只傳遞有效的 SKU)|17004|-|隨選即用| 
|空間不足|17002|-|隨選即用| 
|隨選即用用戶端無法啟動 (非預期)|17000|-|隨選即用| 
|隨選即用用戶端無法佇列案例 (非預期)|17001|-|隨選即用| 

## <a name="next-steps"></a>後續步驟

您現在可以將應用程式指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](/intune-azure/manage-apps/deploy-apps)。

             


