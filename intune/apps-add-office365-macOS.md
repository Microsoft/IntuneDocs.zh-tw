---
title: "使用 Microsoft Intune 將 Office 365 安裝到 macOS 裝置"
titlesuffix: 
description: "了解如何使用 Microsoft Intune 在 macOS 裝置上安裝 Office 365 應用程式。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8de14184c4d23adc79d5b519fdcf272f0d7f6804
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>如何使用 Microsoft Intune 將 Office 365 指派到 macOS 裝置

[市集應用程式] 類型可讓您輕鬆地將 Office 365 應用程式指派給 macOS 裝置。 這個應用程式類型可讓您安裝 Word、Excel、PowerPoint、Outlook 與 OneNote。 這些應用程式也會隨附 Microsoft 自動更新程式 (MAU)，以協助保護您的應用程式並使它保持在最新狀態。 您希望在 Intune 主控台的應用程式清單中，顯示為一個應用程式的那些應用程式。


## <a name="before-you-start"></a>開始之前

在您開始將 Office 365 新增到 macOS 裝置之前，須了解下列詳細資料：

- 部署這些應用程式的裝置必須執行 macOS 10.10 或更新版本。
- Intune 只支援新增 Mac 版 Office 2016 套件所包含的 Office 應用程式。
- 如果在 Intune 安裝應用程式套件時有任何 Office 應用程式是開啟的，使用者未儲存的檔案可能會遺失資料。

## <a name="create-and-configure-the-app-suite"></a>建立並設定應用程式套件

使用 [應用程式] 刀鋒視窗新增 Office 365。
1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Monitoring + Management] (監視 + 管理) > [Intune]。
3. 從 [Intune] 刀鋒視窗選擇 [行動應用程式]。
4. 在 [Mobile Apps] 工作負載中，選擇 [管理] 區段中的 [應用程式]。 
5. 選擇 [新增] 顯示 [新增應用程式] 刀鋒視窗。
6. 在 [應用程式類型] 清單中，選取 [Office 365 套件] 群組中的 [macOS]。
7. 選取 [應用程式套件資訊]，提供應用程式套件的相關資訊。 這項資訊可協助您在 Intune 中識別應用程式套件，同時也能幫助使用者在公司入口網站應用程式中尋找。
8.  指定下列資訊：
    - **套件名稱** - 輸入應用程式套件要顯示在公司入口網站中的名稱。 確定使用的所有套件名稱都是唯一的。 如果有重複的應用程式套件名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **套件描述** - 輸入應用程式套件的描述。
    - **發行者** - Microsoft 會顯示為發行者。
    - **類別**：選取一或多個內建應用程式類別，或選取您建立的類別。 此設定可讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式套件。
    - **將此顯示為公司入口網站中的精選應用程式** - 當使用者瀏覽應用程式時，此設定會以醒目方式在公司入口網站的主頁面上顯示此應用程式套件。
    - **資訊 URL** - (選擇性) 輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL**(選擇性) - 輸入包含這個應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員** - Microsoft 會顯示為開發人員。
    - **擁有者** - Microsoft 會顯示為擁有者。
    - **備註** (選擇性) - 輸入要與這個應用程式建立關聯的備註。
    - **標誌** - 使用者瀏覽公司入口網站時，Office 365 標誌會隨應用程式一起顯示。
9.  按一下 [應用程式資訊] 刀鋒視窗的 [確定]。
10. 按一下 [新增應用程式] 刀鋒視窗上的 [新增]。
    套件會在應用程式清單中顯示為單一項目。

## <a name="configure-app-assignments"></a>設定應用程式指派

在此步驟中，設定應用程式套件的指派。 

1. 在應用程式清單中選取 [Office 365] 應用程式套件，顯示 [Office 365] 概觀刀鋒視窗。
2. 從 [Office 365] 刀鋒視窗按一下 [指派]。
3. 按一下 [新增群組] 來新增群組，以便使用應用程式套件。 [新增群組] 刀鋒視窗隨即顯示。
3. 將 [指派類型] 設定為 [必要]。
4. 將套件指派到您選擇的群組。 如需詳細資訊，請參閱[如何使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)。

    >[!Note]
    > 對於您需要 Office 365 應用程式套件的任何群組，您無法透過 Microsoft Intune 解除安裝它。

5. 選取 [指派] 刀鋒視窗的 [確定]。
6. 選取 [新增群組] 刀鋒視窗的 [確定]。
7. 選取 [儲存] 以認可您的指派。

## <a name="next-steps"></a>接下來的步驟

- 若要了解如何將 Office 365 應用程式新增到 Windows 10 裝置，請參閱[如何使用 Microsoft Intune 將 Office 365 ProPlus 2016 應用程式指派給 Windows 10 裝置](apps-add-office365.md)。
- 若要深入了解包含和排除使用者群組的應用程式指派，請參閱[包含與排除應用程式指派](apps-inc-exl-assignments.md)。
