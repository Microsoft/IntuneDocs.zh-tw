---
title: 如何將 Windows Phone 企業營運應用程式新增至 Microsoft Intune
titlesuffix: ''
description: 了解如何將 Windows Phone 企業營運 (LOB) 應用程式新增至 Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4053c2f932f6101397deb6bf0c3a142fa713aec4
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-add-windows-phone-line-of-business-lob-apps-to-microsoft-intune"></a>如何將 Windows Phone 企業營運 (LOB) 應用程式新增至 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用本文中的資訊，協助您將 Windows Phone 企業營運應用程式新增至 Microsoft Intune。 企業營運 (LOB) 應用程式是您從應用程式安裝檔案新增的應用程式。 這些類型的應用程式通常都是內部撰寫的。 Intune 將 LOB 應用程式安裝在使用者的裝置上。 

## <a name="step-1---specify-the-software-setup-file"></a>步驟 1 - 指定軟體安裝檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [行動應用程式]。
4. 在**行動應用程式**工作負載中選擇 [管理]  >  [應用程式]。
5. 從應用程式清單上方選擇 [新增]。
6. 在 [新增應用程式] 窗格中，選擇 [企業營運應用程式]。

## <a name="step-2---configure-the-app-package-file"></a>步驟 2：設定應用程式套件檔案

1. 在 [新增應用程式] 窗格上選擇 [應用程式套件] 檔案。
2. 在 [應用程式套件] 檔案窗格中，選擇瀏覽按鈕，然後選取副檔名為 **.xap** 的 Windows Phone 安裝檔案。
3. 完成之後，請選擇 [確定]。


## <a name="step-3---configure-app-information"></a>步驟 3：設定應用程式資訊

1. 在 [新增應用程式] 窗格上選擇 [應用程式套件] 檔案。
2. 在 [應用程式資訊] 窗格中，設定應用程式資訊。 窗格中某些值會隨所選的應用程式自動填入︰
    - **名稱** - 輸入將顯示在公司入口網站中的應用程式名稱。 確定您使用的所有應用程式名稱都是唯一的。 如果有重複的應用程式名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **描述** - 輸入應用程式的描述。 使用者會在公司入口網站上看到此描述。
    - **發行者** - 輸入應用程式的發行者名稱。
    - **忽略應用程式版本** - 如果應用程式會由應用程式開發人員自動更新，則設為 [是]。
    - **類別**：選取一或多個內建應用程式類別，或選取您建立的類別。 使用類別可讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式** - 當使用者瀏覽應用程式時，以醒目方式在公司入口網站的主頁面上顯示此應用程式。
    - **資訊 URL** - 選擇是否要輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL** - 選擇是否要輸入包含此應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員** - 選擇是否要輸入應用程式開發人員的姓名。
    - **擁有者** - 選擇是否要輸入此應用程式的擁有者名稱，例如**人力資源部門**。
    - **注意** - 輸入要與此應用程式相關聯的附註。
    - **標誌** - 上傳將與應用程式相關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
3. 完成之後，請選擇 [確定]。

## <a name="step-4---finish-up"></a>步驟 4：完成

1. 在 [新增應用程式] 窗格中，確認您所設定的資訊正確無誤。
2. 選擇 [新增]，將應用程式上傳至 Intune。

## <a name="next-steps"></a>接下來的步驟

- 您已建立的應用程式會顯示在應用程式清單中。 您現在可以將它指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](apps-deploy.md)。

- 深入了解您可用來監視應用程式屬性和指派的方式。 如需詳細資訊，請參閱[如何監視應用程式資訊和指派](apps-monitor.md)。

- 深入了解您應用程式在 Intune 中的內容。 如需詳細資訊，請參閱[裝置和應用程式生命週期的概觀](introduction-device-app-lifecycles.md)。
