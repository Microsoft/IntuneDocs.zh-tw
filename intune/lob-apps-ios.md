---
title: 將 iOS 企業營運應用程式新增至 Microsoft Intune
titlesuffix: ''
description: 了解如何將 iOS 企業營運 (LOB) 應用程式新增至 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9722eece13cf6f3c2dfbb69ce7118a6dfd45c891
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55833832"
---
# <a name="add-an-ios-line-of-business-app-to-microsoft-intune"></a>將 iOS 企業營運應用程式新增至 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用本文中的資訊，協助您將 iOS 企業營運 (LOB) 應用程式新增至 Microsoft Intune。

>[!NOTE]
>iOS 裝置的使用者可以移除部分內建的 iOS 應用程式，例如股票和地圖。 您無法使用 Intune 來重新部署這些應用程式。 如果使用者刪除這些應用程式，則必須移至應用程式商店，並手動重新安裝。

## <a name="step-1-specify-the-software-setup-file"></a>步驟 1：指定軟體安裝檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務] > [Intune]。 Intune 位於 [監視 + 管理] 區段。
3. 在 [Intune] 窗格中，選取 [用戶端應用程式]。
4. 在 [用戶端應用程式] 工作負載中，選取 [管理] > [應用程式]。
5. 從應用程式清單上方，選取 [新增]。
6. 在 [新增應用程式] 窗格中，選取 [企業營運應用程式]。

## <a name="step-2-configure-the-app-package-file"></a>步驟 2：設定應用程式套件檔案

1. 在 [新增應用程式] 窗格中，選取 [應用程式套件檔案]。
2. 在 [應用程式套件檔案] 窗格中，選取 [瀏覽] 按鈕。 然後選取副檔名為 **.xap** 的 iOS 安裝檔案。
3. 完成後，按一下 [確定]。


## <a name="step-3-configure-app-information"></a>步驟 3：設定應用程式資訊

1. 在 [新增應用程式] 窗格中，選取 [應用程式資訊]。
2. 在 [應用程式資訊] 窗格中，新增應用程式的詳細資料。 窗格中某些值會隨著所選的應用程式自動填入。
    - **名稱**：輸入在公司入口網站中顯示的應用程式名稱。 確定您使用的所有應用程式名稱都是唯一的。 如果有重複的應用程式名稱，只有一個應用程式會出現在公司入口網站中。
    - **描述**：輸入應用程式的描述。 此描述會出現在公司入口網站上。
    - **發行者**：輸入應用程式發行者的名稱。
    - **最基本的作業系統**：從清單中，選擇能夠安裝應用程式的最基本作業系統版本。 若將應用程式指派給安裝舊版作業系統的裝置，就不會進行安裝。
    - **類別**：選取一或多個內建的應用程式類別，或選取您建立的類別。 類別可以讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式**：當使用者瀏覽應用程式時，在公司入口網站的主頁面上，以突顯的方式顯示應用程式。
    - **資訊 URL**：(選用) 輸入包含此應用程式相關資訊的網站 URL。 此 URL 會出現在公司入口網站上。
    - **隱私權 URL**：(選擇性) 輸入包含這個應用程式之隱私權資訊的網站 URL。 此 URL 會出現在公司入口網站上。
    - **開發人員**：(選擇性) 輸入應用程式開發人員的姓名。
    - **擁有者**：(選擇性) 輸入此應用程式之擁有者的名稱。 **人力資源部門**就是一個例子。
    - **附註**：輸入要與此應用程式建立關聯的任何附註。
    - **標誌**：上傳與應用程式相關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
3. 完成後，按一下 [確定]。

## <a name="step-4-finish-up"></a>步驟 4：完成

1. 在 [新增應用程式] 窗格中，確認應用程式的詳細資料正確無誤。
2. 選取 [新增]，將應用程式上傳至 Intune。

您所建立的應用程式現在會出現在應用程式清單中。 在清單中，您可以將應用程式指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](apps-deploy.md)。

> [!NOTE]
> iOS LOB 應用程式的佈建設定檔到期前有 30 天的通知時間。

## <a name="step-5-update-a-line-of-business-app"></a>步驟 5：更新企業營運應用程式

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> 若要讓 Intune 服務成功地將新的 IPA 檔案部署到裝置，您必須對 IPA 套件中 Info.plist 檔案內的 `CFBundleVersion` 字串進行遞增處理。

## <a name="next-steps"></a>後續步驟

- 您所建立的應用程式會出現在應用程式清單中。 您現在可以將它指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](apps-deploy.md)。

- 深入了解您可用來監視應用程式屬性和指派的方式。 請參閱[如何監視應用程式資訊和指派](apps-monitor.md)。

- 深入了解您應用程式在 Intune 中的內容。 請參閱[裝置和應用程式生命週期的概觀](introduction-device-app-lifecycles.md)。
