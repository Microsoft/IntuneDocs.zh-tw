---
title: "使用 Intune 將內建應用程式新增到行動裝置"
titlesuffix: Azure portal
description: "了解如何使用 Intune 以更容易安裝內建應用程式行動裝置。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d622f2cb8c6b3e8c9aace4e805108ccfa71eb4d2
ms.sourcegitcommit: 754fcc31155b28d6910bba45419c6be745f8793e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-add-built-in-apps-to-microsoft-intune"></a>如何將內建應用程式新增至 Microsoft Intune

**內建**應用程式類型可讓您輕鬆將 Office 365 應用程式等受控應用程式，指派給 iOS 和 Android 裝置。 您可以指派此應用程式類型的特定應用程式，例如 Excel、OneDrive、Outlook、Skype 及其他。 新增應用程式之後，您會看到應用程式類型為**內建 iOS 應用程式**或**內建 Android 應用程式**。 使用內建應用程式類型，您可以選擇向裝置使用者發佈這些特定應用程式的哪一些。

 在舊版的 Intune 主控台中，Intune 提供數種預設的受控 Office 365 應用程式，例如 Outlook 和 OneDrive。 這些受控應用程式的應用程式類型標記為「受控 iOS Store 應用程式」或「受控 Android 應用程式」。 建議您使用內建應用程式類型，而不是「受控 iOS Store」或「受控 Android 應用程式」。 內建應用程式類型提供額外的彈性，能夠編輯及刪除 Office 365 應用程式。

>[!NOTE]
>當所有指派都已刪除時，標記為「受控 iOS Store」和「受控 Android 應用程式」的預設 Office 365 應用程式就會從應用程式清單中移除。

## <a name="add-built-in-app"></a>新增內建應用程式

下列步驟可讓您將內建應用程式新增至 Microsoft Intune 的可用應用程式。
1.  登入 Azure 入口網站。
2.  顯示 [Microsoft Intune] 刀鋒視窗：選擇 [更多服務] > [監視 + 管理] > [Intune]。
3.  在 [Intune] 刀鋒視窗上，選擇 [行動應用程式]。
4.  在 [Mobile Apps] 刀鋒視窗上，選擇 [管理] 群組中的 [應用程式]。
5.  選擇 [新增] 新增新的應用程式。
6.  在 [新增應用程式] 刀鋒視窗中，從 [應用程式類型] 清單中選擇 [內建應用程式]。
7.  按一下 [選取應用程式] 選擇要包含的內建應用程式。
8.  在 [內建應用程式] 刀鋒視窗中，選取要包含的應用程式。
9.  在 [新增應用程式] 刀鋒視窗中，按一下 [新增] 包含應用程式。


## <a name="configure-app-information"></a>設定應用程式資訊

您可修改內建應用程式的相關資訊。 這項資訊可協助您在 Intune 中識別應用程式，同時也能幫助使用者在公司入口網站應用程式中尋找應用程式。
1.  在 [Mobile Apps - 應用程式] 刀鋒視窗中，選擇您想要修改的內建應用程式。 即會顯示內建應用程式的刀鋒視窗。
2.  選取 [管理] 群組的 [屬性] 選項。
3.  選取 [設定] 選項以修改內建應用程式資訊。
4.  在 [應用程式資訊] 刀鋒視窗中，您可修改下列資訊：
    -   **名稱** - 輸入將顯示在公司入口網站中的內建應用程式名稱。 確定您使用的所有名稱都是唯一的。 如果有重複的應用程式名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    -   **描述** - 輸入應用程式的描述。 
    -   **發行者** - 輸入應用程式的發行者名稱。
    -   **類別** - (選擇性) 選取一或多個內建應用程式類別。 設定此選項可讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    -   **將此顯示為公司入口網站中的精選應用程式** - 當使用者瀏覽應用程式時，以醒目方式在公司入口網站的主頁面上顯示此應用程式。
    -   **資訊 URL** - 選擇是否要輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    -   **隱私權 URL** - 選擇是否要輸入包含此應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    -   **開發人員** - 選擇是否要輸入應用程式開發人員的姓名。
    -   **擁有者** - 選擇是否要輸入此應用程式的擁有者名稱，例如人力資源部門。
    -   **注意** - 輸入要與此應用程式相關聯的附註。
    -   **上傳圖示** - 上傳當使用者瀏覽公司入口網站時，隨應用程式一起顯示的圖示。
3.  完成後，請按一下 [應用程式資訊] 刀鋒視窗的 [確定]。
4.  按一下 [屬性] 刀鋒視窗的 [儲存]。

## <a name="next-steps"></a>接下來的步驟

您現在可以將應用程式指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](apps-deploy.md)。
