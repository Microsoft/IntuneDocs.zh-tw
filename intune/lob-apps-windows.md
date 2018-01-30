---
title: "如何將 Windows 企業營運應用程式新增至 Intune"
titlesuffix: Azure portal
description: "了解如何將 Windows 企業營運應用程式新增至 Intune。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/3/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b5bf34cf68edea7c010fa06af75589492e0d0520
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-add-windows-line-of-business-lob-apps-to-microsoft-intune"></a>如何將 Windows 企業營運 (LOB) 應用程式新增至 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


## <a name="step-1---specify-the-software-setup-file"></a>步驟 1 - 指定軟體安裝檔

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  +  [Intune]。
3. 在 [Intune] 刀鋒視窗上選擇 [管理應用程式]。
4. 在**行動應用程式**工作負載中選擇 [管理]  >  [應用程式]。
5. 從應用程式清單上方選擇 [新增]。
6. 在 [新增應用程式] 刀鋒視窗中，選擇 [企業營運應用程式]。

## <a name="step-2---configure-the-app-package-file"></a>步驟 2：設定應用程式套件檔案

1. 在 [新增應用程式] 刀鋒視窗上選擇 [應用程式套件] 檔案。
2. 在 [應用程式套件] 檔案刀鋒視窗中，選擇瀏覽按鈕，然後選取副檔名為 **.msi**、**.appx** 或 **.appxbundle** 的 Windows 安裝檔案。
3. 完成之後，請選擇 [確定]。


## <a name="step-3---configure-app-information"></a>步驟 3：設定應用程式資訊

1. 在 [新增應用程式] 刀鋒視窗上選擇 [應用程式套件] 檔案。
2. 在 [應用程式資訊] 刀鋒視窗中，設定下列資訊 (此刀鋒視窗中的一些值可能會自動填入)：
    - **名稱** - 輸入將顯示在公司入口網站中的應用程式名稱。 確定您使用的所有應用程式名稱都是唯一的。 如果有重複的應用程式名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **描述** - 輸入應用程式的描述。 使用者會在公司入口網站上看到此描述。
    - **發行者** - 輸入應用程式的發行者名稱。
    - **類別**：選取一或多個內建應用程式類別，或選取您建立的類別。 將應用程式分類可讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式** - 當使用者瀏覽應用程式時，以醒目方式在公司入口網站的主頁面上顯示此應用程式。
    - **資訊 URL** - (選擇性) 輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL** - (選擇性) 輸入包含此應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **命令列引數** - (選擇性) 輸入任何您想要在該 .msi 檔案執行時套用的命令列引數，例如 **/q**。
    - **開發人員** - 選擇是否要輸入應用程式開發人員的姓名。
    - **擁有者** - 選擇是否要輸入此應用程式的擁有者名稱，例如**人力資源部門**。
    - **注意** - 輸入要與此應用程式相關聯的附註。
    - **標誌** - 上傳將與應用程式相關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
3. 完成之後，請選擇 [確定]。

## <a name="step-4---finish-up"></a>步驟 4：完成

1. 在 [新增應用程式] 刀鋒視窗中，確認您所設定的應用程式資訊正確無誤。
2. 選擇 [新增]，將應用程式上傳至 Intune。

## <a name="step-5---update-a-line-of-business-app"></a>步驟 5 - 更新企業營運應用程式

[!INCLUDE[shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

## <a name="next-steps"></a>接下來的步驟

您已建立的應用程式會顯示在應用程式清單中。 您現在可以將它指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](apps-deploy.md)。

深入了解您可用來監視應用程式屬性和指派的方式。 如需詳細資訊，請參閱[如何監視應用程式資訊和指派](apps-monitor.md)。

深入了解您應用程式在 Intune 中的內容。 如需詳細資訊，請參閱[裝置和應用程式生命週期的概觀](introduction-device-app-lifecycles.md)。