---
title: "如何將 Android 市集應用程式新增至 Intune"
titleSuffix: Azure portal
description: "了解如何將 Android 市集應用程式新增至 Intune。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cdf00d8adc5a854f90b59c6066d6f0ab7c6ae94a
ms.sourcegitcommit: 754fcc31155b28d6910bba45419c6be745f8793e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-add-android-store-apps-to-microsoft-intune"></a>如何將 Android 市集應用程式新增至 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

在您將應用程式指派給一部裝置或一群使用者之前，必須先將該應用程式新增到 Microsoft Intune。 下列步驟可讓您從 Azure 入口網站，將 Android 市集應用程式新增到 Intune。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Microsoft Intune] 刀鋒視窗上，選擇 [行動應用程式]。
4. 在 [Mobile Apps] 工作負載中，選擇 [管理] 區段下的 [應用程式]。
5. 從應用程式清單上方選擇 [新增]。
6. 在 [新增應用程式] 刀鋒視窗中，選取可用 [市集應用程式] 類型下的 [Android]。
7. 選取 [設定]，設定應用程式的下列資訊：取決於您選擇的應用程式，此刀鋒視窗中某些值可能已自動填入：
    - **名稱** - 輸入要顯示在公司入口網站中的應用程式名稱。 確定您使用的所有應用程式名稱都是唯一的。 如果有重複的應用程式名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **描述** - 輸入應用程式的描述。 使用者會在公司入口網站中看到這個描述。
    - **發行者** - 輸入應用程式的發行者名稱。
    - **Appstore URL** - 輸入您要建立之應用程式的應用程式市集 URL。
    - **最低作業系統** - 從清單中選擇能夠安裝應用程式的最低作業系統版本。 若將應用程式指派給安裝舊版作業系統的裝置，就不會進行安裝。
    - **類別** (選用) - 選取一或多個內建應用程式類別，或選取您建立的類別。 這可以讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式** - 當使用者瀏覽應用程式時，以醒目方式在公司入口網站的主頁面上顯示此應用程式。
    - **資訊 URL** - (選擇性) 輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL**(選擇性) - 輸入包含這個應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員** (選擇性) - 輸入應用程式開發人員的姓名。
    - **擁有者** (選擇性)- 輸入此應用程式的擁有者名稱，例如**人力資源部門**。
    - **備註** (選擇性) - 輸入要與這個應用程式建立關聯的備註。
    - **標誌** (選擇性) - 上傳要與應用程式建立關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
8. 當您完成應用程式資料的設定時，按一下 [確定]。
9. 按一下 [新增]，以新增應用程式。

您建立的應用程式會顯示在應用程式清單中，而您可從中將該應用程式指派給您選擇的群組。 

##<a name="next-steps"></a>接下來的步驟

- [如何將應用程式指派到群組](apps-deploy.md)