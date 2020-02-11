---
title: 使用 Microsoft Intune 將 Office 365 安裝到 macOS 裝置
titleSuffix: ''
description: 了解如何使用 Microsoft Intune 在 macOS 裝置上安裝 Office 365 應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3cf4c2abb5506f297af8a4e77145abea5360381b
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755352"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>使用 Microsoft Intune 將 Office 365 指派到 macOS 裝置

此應用程式類型可讓您輕鬆地將 Office 365 2016 應用程式指派給 macOS 裝置。 這個應用程式類型可讓您安裝 Word、Excel、PowerPoint、Outlook 與 OneNote。 為了讓您保有最安全以及最新版的應用程式，這些應用程式也自帶 Microsoft AutoUpdate (MAU)。 您所要的多個應用程式在 Intune 主控台的應用程式清單中會顯示為一個應用程式。


## <a name="before-you-start"></a>在您開始使用 Intune 之前

在您開始將 Office 365 新增到 macOS 裝置之前，請先了解下列詳細資料：

- 部署這些應用程式的裝置必須執行 macOS 10.10 或更新版本。
- Intune 只支援新增 Mac 版 Office 2016 套件所包含的 Office 應用程式。
- 如果在 Intune 安裝應用程式套件時有任何 Office 應用程式是開啟的，則使用者未儲存的檔案可能會遺失資料。

## <a name="select-the-office-365-suite-app-type"></a>選取 Office 365 套件應用程式類型

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [所有應用程式]   > [新增]  。
3. 選取 [選取應用程式類型]  窗格 [Office 365 套件]  區段中的 [macOS]  。
4. 按一下 [選取]  。 [新增 Office 365 套件]  步驟隨即顯示。

## <a name="step-1---app-suite-information"></a>步驟 1 - 應用程式套件資訊

在此步驟中，您要提供應用程式套件的相關資訊。 這項資訊可協助您在 Intune 中識別應用程式套件，且能幫助使用者在公司入口網站中尋找應用程式套件。

1. 在 [應用程式套件資訊]  頁面中，您可以確認或修改預設值：
    - **套件名稱**：輸入應用程式套件在公司入口網站中顯示的名稱。 請確定使用的所有套件名稱都是唯一的。 如果有重複的應用程式套件名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **套件描述**：輸入應用程式套件的描述。 例如，您可以列出已選取包含的應用程式。
    - **發行者**：Microsoft 會顯示為發行者。
    - **類別**：(選擇性) 選取一或多個內建的應用程式類別，或選取您建立的類別。 此設定可讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式套件。
    - **將此顯示為公司入口網站中的精選應用程式**：若要在使用者瀏覽應用程式時，於公司入口網站的主頁面上以醒目方式顯示應用程式套件，請選取此選項。
    - **資訊 URL**：(選用) 輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL**：(選擇性) 輸入包含這個應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員**：Microsoft 會顯示為開發人員。
    - **擁有者**：Microsoft 會顯示為擁有者。
    - **附註**：輸入要與此應用程式建立關聯的任何附註。
    - **標誌**：當使用者瀏覽公司入口網站時，Office 365 標誌會隨應用程式一起顯示。
2. 按一下 [下一步]  以顯示 [範圍標籤]  頁面。

## <a name="step-2---select-scope-tags-optional"></a>步驟 2 - 選取範圍標籤 (選擇性)
您可以使用範圍標籤來決定可在 Intune 中看見用戶端應用程式資訊的人員。 如需範圍標籤的完整詳細資料，請參閱[針對分散式 IT 使用角色型存取控制和範圍標籤](../fundamentals/scope-tags.md)。

1. 按一下 [選取範圍標籤]  來選擇性地為應用程式套件新增範圍標籤。 
2. 按一下 [下一步]  以顯示 [指派]  頁面。

## <a name="step-3---assignments"></a>步驟 3 - 指派

1. 為應用程式套件選取 [必要]  或 [適用於已註冊的裝置]  群組指派。 如需詳細資訊，請參閱[新增群組來組織使用者和裝置](~/fundamentals/groups-add.md)和[使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)。

    >[!Note]
    > 您無法透過 Intune 將 macOS 版 Office 365 應用程式套件解除安裝。

2. 按一下 [下一步]  以顯示 [檢閱 + 建立]  頁面。 

## <a name="step-4---review--create"></a>步驟 4 - 檢閱 + 建立

1. 檢閱您針對應用程式套件所輸入的值和設定。
2. 當您完成時，請按一下 [建立]  以將應用程式新增到 Intune。

    您所建立的 Office 365 Window 10 應用程式套件的 [概觀]  刀鋒視窗隨即顯示。 套件會在應用程式清單中顯示為單一項目。

## <a name="next-steps"></a>後續步驟

- 若要了解如何將 Office 365 應用程式新增到 Windows 10 裝置，請參閱[使用 Microsoft Intune 將 Office 365 ProPlus 2016 應用程式指派給 Windows 10 裝置](apps-add-office365.md)。
- 若要深入了解包含和排除使用者群組的應用程式指派，請參閱[包含與排除應用程式指派](apps-inc-exl-assignments.md)。
