---
title: 使用 Microsoft Intune 將內建應用程式新增到行動裝置
titlesuffix: ''
description: 了解如何使用 Intune 以更容易安裝內建應用程式行動裝置。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 54eb50a47b28d04fc32662098c4ee521ae63589e
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="add-built-in-apps-to-microsoft-intune"></a>將內建應用程式新增至 Microsoft Intune

*內建*應用程式類型可讓您輕鬆將 Office 365 應用程式等受控應用程式，指派給 iOS 和 Android 裝置。 您可以指派此應用程式類型的特定應用程式，例如 Excel、OneDrive、Outlook、Skype 及其他。 新增應用程式之後，應用程式會顯示為*內建 iOS 應用程式*或*內建 Android 應用程式*。 使用內建應用程式類型，您可以選擇向裝置使用者發佈這些應用程式的哪一些。

在舊版的 Intune 主控台中，Intune 提供數種預設的受控 Office 365 應用程式，例如 Outlook 和 OneDrive。 這些受控應用程式的應用程式類型標記為*受控 iOS Store 應用程式*或*受控 Android 應用程式*。 我們不建議使用這些應用程式類型，請使用內建應用程式類型。 藉著使用程式類型，您能夠獲得編輯及刪除 Office 365 應用程式的額外彈性。

>[!NOTE]
>當所有指派都已刪除時，標記為*受控 iOS 市集*和*受控 Android 應用程式*的預設 Office 365 應用程式就會從應用程式清單中移除。

## <a name="add-a-built-in-app"></a>新增內建應用程式

若要將內建應用程式新增至 Microsoft Intune 的可用應用程式，請執行下列作業：
1. 登入 Azure 入口網站。
2. 若要顯示 [Microsoft Intune] 窗格，請選取 [更多服務] > [監視 + 管理] > [Intune]。
3. 在 [Intune] 窗格中，選取 [行動應用程式]。
4. 在 [行動應用程式] 窗格中的 [管理] 底下，選取 [應用程式]。
5. 選取 [新增]。
6. 在 [新增] 應用程式窗格中的 [應用程式類型] 清單中，選取 [內建應用程式]。
7. 選取 [選取應用程式]。
8. 在 [內建應用程式] 窗格中，選取您想要包含的應用程式。
9. 在 [新增應用程式] 窗格中，選取 [新增]。


## <a name="configure-app-information"></a>設定應用程式資訊

您可修改內建應用程式的相關資訊。 這項資訊可協助您在 Intune 中識別應用程式，並幫助使用者在公司入口網站中尋找應用程式。
1. 在 [行動應用程式 - 應用程式] 窗格中，選取您想要修改的內建應用程式。  
    即會顯示內建應用程式的窗格。
2. 在 [管理] 底下，選取 [屬性] 選項。
3. 若要修改內建應用程式資訊，請選取 [設定] 選項。
4. 在 [應用程式資訊] 窗格中，您可修改下列資訊：
    - **名稱**輸入將顯示在公司入口網站中的內建應用程式名稱。 確定您使用的所有名稱都是唯一的。 如果有重複的應用程式名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **描述**：輸入應用程式的描述。 
    - **發行者**：輸入應用程式的發行者名稱。
    - **類別**(選擇性) 選取一或多個內建應用程式類別。 設定此選項可讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式**：當使用者瀏覽應用程式時，以醒目方式在公司入口網站的主頁面上顯示此應用程式。
    - **資訊 URL**：選擇是否要輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL**：選擇是否要輸入包含此應用程式隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員**：選擇是否要輸入應用程式開發人員的姓名。
    - **擁有者**選擇是否要輸入此應用程式的擁有者名稱 (例如*人力資源部門*)。
    - **附註**：輸入要與此應用程式相關聯的任何附註。
    - **上傳圖示**上傳當使用者瀏覽公司入口網站時，隨應用程式一起顯示的圖示。
4. 選取 [確定]。
5. 在 [屬性] 窗格中，選取 [儲存]。

## <a name="next-steps"></a>接下來的步驟

- 您現在可以將應用程式指派給您選擇的群組。 如需詳細資訊，請參閱[將應用程式指派給群組](apps-deploy.md)。
