---
title: "使用 Intune 將 Office 365 安裝到 macOS 裝置"
titlesuffix: Azure portal
description: "了解如何使用 Intune 以更容易在 macOS 裝置上安裝 Office 365 應用程式。"
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1573a6a2ca78489df46c9e08ebbfe9a16b0731c7
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>如何使用 Microsoft Intune 將 Office 365 指派到 macOS 裝置

此應用程式類型可讓您輕鬆地將 Office 365 應用程式指派給 macOS 裝置。 這個新的應用程式類型可讓您安裝 Word、Excel、PowerPoint、Outlook 與 OneNote。 這些應用程式也會隨附 Microsoft 自動更新程式 (MAU)，以協助保護您的應用程式並使它保持在最新狀態。 您希望在 Intune 主控台的應用程式清單中，顯示為一個應用程式的那些應用程式。


## <a name="before-you-start"></a>開始之前

- 部署這些應用程式的裝置必須執行 macOS 10.10 或更新版本。
- Intune 只支援新增 Mac 版 Office 2016 套件所包含的 Office 應用程式。
- 如果在 Intune 安裝應用程式套件時有任何 Office 應用程式是開啟的，使用者未儲存的檔案可能會遺失資料。


## <a name="get-started"></a>開始使用
使用 [應用程式] 刀鋒視窗新增 Office 365。
1.  登入 Azure 入口網站。
2.  選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3.  在 [Intune] 刀鋒視窗上，選擇 [行動應用程式]。
4.  在 [Mobile Apps] 工作負載中，選擇 [管理] 群組中的 [應用程式]。 選擇 [新增]。
5.  在 [新增應用程式] 刀鋒視窗上，選擇 [Office 365] > [macOS]。
6.  選取 [新增]。

## <a name="configure-the-app-suite"></a>設定應用程式套件

提供應用程式套件的相關資訊。 這項資訊可協助您在 Intune 中識別，同時也能幫助使用者在公司入口網站應用程式中尋找。

1.  在 [新增應用程式] 刀鋒視窗中選擇 [App Suite Information] \(應用程式套件資訊)。
2.  指定下列資訊：
    - **套件名稱** - 輸入應用程式套件要顯示在公司入口網站中的名稱。 確定使用的所有套件名稱都是唯一的。 如果有重複的應用程式套件名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **套件描述** - 輸入應用程式套件的描述。
    - **發行者** - Microsoft 會顯示為發行者。
    - **類別** - 或者選取一或多個內建應用程式類別，或您建立的類別。 這可讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式套件。
    - **將此顯示為公司入口網站中的精選應用程式** - 當使用者瀏覽應用程式時，這會以醒目方式在公司入口網站的主頁面上顯示此應用程式套件。
    - **資訊 URL** - 選擇是否要輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL** - 選擇是否要輸入包含此應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員** - Microsoft 會顯示為開發人員。
    - **擁有者** - Microsoft 會顯示為擁有者。
    - **注意** - 輸入要與此應用程式相關聯的附註。
    - **上傳圖示** - 上傳當使用者瀏覽公司入口網站時，隨應用程式一起顯示的圖示。
3.  選取 [確定]。 套件會在應用程式清單中顯示為單一項目。

## <a name="configure-app-assignments"></a>設定應用程式指派

在此步驟中，設定應用程式套件的指派。 請注意，可用的應用程式類型即將推出。

1.  選取應用程式清單中的應用程式套件，然後選取 [指派]。
2.  選擇 [選取群組]。
3.  將套件指派到您選擇的群組。 如需詳細資訊，請參閱[如何使用 Microsoft Intune 將應用程式指派給群組](/intune/apps-deploy)。
4.  針對每個群組，您必須選取 [Require Install] \(要求安裝\)。
        >[!Note]
        > You cannot uninstall Office 365 through Intune.

5. 選取 [儲存] 以認可您的指派。

## <a name="next-steps"></a>接下來的步驟

若要了解如何將 Office 365 應用程式新增到 Windows 10 裝置，請參閱[如何使用 Microsoft Intune 將 Office 365 ProPlus 2016 應用程式指派給 Windows 10 裝置](/intune/apps-add-office365)。
