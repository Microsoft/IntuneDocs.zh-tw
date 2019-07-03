---
title: 使用 Microsoft Intune 將 Office 365 安裝到 macOS 裝置
titleSuffix: ''
description: 了解如何使用 Microsoft Intune 在 macOS 裝置上安裝 Office 365 應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1ac752c503f523ab7f55db38488fdf31f8d886fa
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67527429"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>使用 Microsoft Intune 將 Office 365 指派到 macOS 裝置

此應用程式類型可讓您輕鬆地將 Office 365 2016 應用程式指派給 macOS 裝置。 這個應用程式類型可讓您安裝 Word、Excel、PowerPoint、Outlook 與 OneNote。 為了讓您保有最安全以及最新版的應用程式，這些應用程式也自帶 Microsoft AutoUpdate (MAU)。 您所要的多個應用程式在 Intune 主控台的應用程式清單中會顯示為一個應用程式。


## <a name="before-you-start"></a>開始之前

在您開始將 Office 365 新增到 macOS 裝置之前，請先了解下列詳細資料：

- 部署這些應用程式的裝置必須執行 macOS 10.10 或更新版本。
- Intune 只支援新增 Mac 版 Office 2016 套件所包含的 Office 應用程式。
- 如果在 Intune 安裝應用程式套件時有任何 Office 應用程式是開啟的，則使用者未儲存的檔案可能會遺失資料。

## <a name="create-and-configure-the-app-suite"></a>建立並設定應用程式套件

從**應用程式**窗格新增 Office 365。
1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在 [Intune]  窗格中，選取 [用戶端應用程式]  。
4. 在 [用戶端應用程式]  工作負載窗格中的 [管理]  下，選取 [應用程式]  。 
5. 選取 [新增]  。
6. 在 [應用程式類型]  清單的 [Office 365 套件]  群組中，選取 [macOS]  。
7. 如需應用程式套件的相關資訊，請選取 [應用程式套件資訊]  。  
    這項資訊可協助您在 Intune 中識別應用程式套件，且能幫助使用者在公司入口網站中尋找應用程式套件。
8. 輸入下列資訊：
    - **套件名稱**：輸入應用程式套件在公司入口網站中顯示的名稱。 請確定使用的所有套件名稱都是唯一的。 如果有重複的應用程式套件名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **套件描述**：輸入應用程式套件的描述。
    - **發行者**：Microsoft 會顯示為發行者。
    - **類別**：選取一或多個內建應用程式類別，或選取您建立的類別。 此設定可讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式套件。
    - **將此顯示為公司入口網站中的精選應用程式**：若要在使用者瀏覽應用程式時，於公司入口網站的主頁面上以醒目方式顯示應用程式套件，請選取此選項。
    - **資訊 URL**：(選用) 輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL**：(選擇性) 輸入包含這個應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員**：Microsoft 會顯示為開發人員。
    - **擁有者**：Microsoft 會顯示為擁有者。
    - **附註**：(選擇性) 輸入要與此應用程式建立關聯的任何附註。
    - **標誌**：當使用者瀏覽公司入口網站時，Office 365 標誌會隨應用程式一起顯示。
9. 選取 [確定]  。
10. 在 [新增應用程式]  窗格中，選取 [新增]  。  
    套件會在應用程式清單中顯示為單一項目。

## <a name="configure-app-assignments"></a>設定應用程式指派

在此步驟中，設定應用程式套件的指派。 

1. 在應用程式清單中選取 [Office 365]  應用程式套件，以顯示 [Office 365]  概觀窗格。
2. 在 [Office 365]  窗格中選取 [指派]  。
3. 若要新增群組來使用該應用程式套件，請選取 [新增群組]  。  
    [新增群組]  窗格隨即顯示。
4. 將 [指派類型]  設定為 [必要]  或 [可用]  。
5. 將套件指派到您選取的群組。 如需詳細資訊，請參閱[使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)。

    >[!Note]
    > 您無法透過 Intune 來將 Office 365 應用程式套件解除安裝。

5. 在 [指派]  窗格中，選取 [確定]  。
6. 在 [新增群組]  窗格中，選取 [確定]  。
7. 若要認可您的指派，請選取 [儲存]  。

## <a name="next-steps"></a>後續步驟

- 若要了解如何將 Office 365 應用程式新增到 Windows 10 裝置，請參閱[使用 Microsoft Intune 將 Office 365 ProPlus 2016 應用程式指派給 Windows 10 裝置](apps-add-office365.md)。
- 若要深入了解包含和排除使用者群組的應用程式指派，請參閱[包含與排除應用程式指派](apps-inc-exl-assignments.md)。
