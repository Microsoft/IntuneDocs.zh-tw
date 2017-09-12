---
title: "適用於 iOS 裝置的 Intune 網路內容篩選器設定"
titlesuffix: Azure portal
description: "了解您可以用來允許及禁止從 iOS 裝置上存取網站的設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 7/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 16aa0f3c-8977-4495-9fbe-ca30ad278c9e
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e2ff764b7500cf79b2feb64f55cac29d7dcf2eee
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2017
---
# <a name="web-content-filter-settings-for-ios-devices"></a>適用於 iOS 裝置的網路內容篩選器

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

您可以使用這些設定來設定 iOS 裝置上的網頁瀏覽器使用者可以或無法瀏覽的 URL。 設定 URL 的方法有兩種：

- **設定 URL**：使用 Apple 的內建網站篩選，它會尋找例如不雅或成人內容語言等成人詞彙。 這項功能會在每個網頁載入時對它進行評估，並嘗試識別和封鎖不合適的內容。 您也可以設定不讓篩選器檢查的 URL，或是不論篩選器設定為何都會一律封鎖的 URL。

- **僅限特定網站** (僅適用於 Safari 網頁瀏覽器)：這些 URL 會新增至 Safari 瀏覽器的書籤。 「僅允許」使用者瀏覽這些網站；他們將無法存取任何其他網站。 只有在您知道使用者可以存取的確切 URL 清單時，才使用此選項。
如果不指定任何 URL，使用者即無法存取任何網站 (但 microsoft.com、microsoft.net 和 apple.com 除外)。



## <a name="get-started"></a>開始使用

1. 在 [裝置功能] 刀鋒視窗上選擇 [網路內容篩選 (僅限受監督)]。
2. 在 [網路內容篩選器] 刀鋒視窗上，選擇您要設定的 [篩選器類型]：
    - **未設定**：不會執行任何篩選。
    - **設定 URL**
    - **僅限特定網站**
3. 接下來，根據您要使用的篩選器類型，使用下列一項程序：


## <a name="configure-urls"></a>設定 URL

1. 在 [網路內容篩選器] 刀鋒視窗上，視需要選擇下列一項設定：
    - **允許的 URL**：在 [允許的 URL] 刀鋒視窗上，輸入您要允許 (略過 Apple 網站篩選) 的 URL，並在輸入每個 URL 後選擇 [輸入]。
    - **封鎖的 URL**：在 [封鎖的 URL] 刀鋒視窗上，輸入您要封鎖 (不論 Apple 網站篩選設定為何) 的 URL，並在輸入每個 URL 後選擇 [輸入]。
2. 完成後，請按一下 [確定] 。


## <a name="specific-websites-only"></a>僅限特定網站

1. 在 [網路內容篩選器] 刀鋒視窗上，針對您要允許的每個網站設定下列設定：
    - **URL**：輸入您要允許之網站的 URL，例如 **http://www.contoso.com**。
    - **書籤路徑**：輸入您要儲存書籤的位置路徑，例如 **/Contoso/Business Apps**。 如果您不新增路徑，書籤就會新增到裝置的預設書籤資料夾。
    - **標題**：輸入書籤的描述性標題。
2. 輸入每個網站的資訊後，按一下 [新增]。
3. 完成後，請按一下 [確定] 。

>[!IMPORTANT] 
> Intune 會自動允許下列 URL。
> - www.microsoft.com
> - www.microsoft.net
> - www.apple.com

## <a name="finish-up"></a>完成

選擇 [確定] 以返回 [建立設定檔] 刀鋒視窗，然後選擇 [建立]。

## <a name="next-steps"></a>後續步驟

您現在可以將裝置設定檔指派給您選擇的群組。 如需詳細資料，請參閱[如何指派裝置設定檔](device-profile-assign.md)。
