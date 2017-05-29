---
title: "使用受管理的瀏覽器管理 Web 存取 | Microsoft Docs"
description: "部署受管理的瀏覽器應用程式，以限制網頁瀏覽和傳輸網頁資料至其他應用程式。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 49ad005846265deb7d4b34b52a1c139e8f61372b
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>透過 Microsoft Intune 使用受管理的瀏覽器原則管理網際網路存取

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Managed Browser 是一個網頁瀏覽應用程式，您可以在組織中使用 Microsoft Intune 來部署此應用程式。 受管理的瀏覽器原則會設定允許清單或封鎖清單，以限制受管理瀏覽器的使用者可瀏覽的網站。

因為此應用程式已整合 Intune SDK，您也可以將應用程式保護原則套用至此應用程式。 這些原則可能包括控制剪下、複製與貼上的使用、防止螢幕擷取，以及確保使用者選取的內容連結只在其他受管理的應用程式中開啟。 如需詳細資訊，請參閱[在 Microsoft Intune 主控台中設定及部署行動應用程式管理原則](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)。

>[!IMPORTANT]
>Managed Browser 應用程式只會在裝置上另一個應用程式已擷取應用程式保護原則的情況下，擷取並套用 Intune 應用程式保護原則。<br><br> 此外，如果使用者從應用程式市集安裝 Managed Browser，且 Intune 未加以管理，則會適用下列行為︰<br /><br />
>**iOS**：Managed Browser 應用程式可以當做基本網頁瀏覽器使用，但某些功能將無法使用，且它將無法存取來自其他受 Intune 管理之應用程式的資料。<br />
**Android**：無法使用 Managed Browser 應用程式。<br /><br />
如果使用者自行在版本早於 iOS 9 的 iOS 裝置上安裝 Managed Browser，您建立的任何原則管理都不會管理瀏覽器。 若要確保 Intune 會管理瀏覽器，使用者必須先將該應用程式解除安裝，您才可將其部署為受管理的應用程式以供其使用。 在 iOS 9 及更新版本，如果使用者自行安裝受管理瀏覽器，將會提示他們允許其受到原則管理。

您可以針對下列裝置類型建立受管理的瀏覽器原則：

-   執行 Android 4 和更新版本的裝置

-   執行 iOS 8.0 和更新版本的裝置

Intune Managed Browser 支援從 [Microsoft Intune 應用程式合作夥伴](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx)開啟網路內容。

## <a name="create-a-managed-browser-policy"></a>建立受管理的瀏覽器原則

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 **[原則]** &gt; **[新增原則]**。

2.  設定下列其中一種 [軟體]  原則類型：

    -   **Managed Browser (Android 4 和更新版本)**

    -   **Managed Browser (iOS 8.0 和更新版本)**

    如需如何建立和部署原則的詳細資訊，請參閱[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)主題。

3.  使用下列項目協助您設定受管理的瀏覽器原則設定：

    - **名稱**。 輸入受管理瀏覽器原則的專用名稱，有助於您在 Intune 主控台中識別該原則。
    - **描述**。 提供可給予受管理瀏覽器原則概觀的說明，以及可協助您找到該說明的其他相關資訊。
    - **啟用允許清單或封鎖清單來限制 Managed Browser 可開啟的 URL**。 選取下列其中一個選項：
        - **允許 Managed Browser 只開啟下列 URL**。 指定 Managed Browser 可開啟的 URL 清單。
        - **禁止 Managed Browser 開啟下列 URL**。 指定 Managed Browser 無法開啟的 URL 清單。
**注意：**您不能在同一個受管理的瀏覽器原則中同時包含允許和封鎖的 URL。
如需您可指定的 URL 格式詳細資訊，請參閱本主題中的**適用於允許和封鎖 URL 的 URL 格式**。

4.  完成之後，請選擇 [儲存原則]。

新的原則會顯示在 [原則] 工作區的 [設定原則] 節點中。

## <a name="create-a-deployment-for-the-managed-browser-app"></a>針對受管理的瀏覽器應用程式建立部署
建立受管理的瀏覽器原則之後，您接著可針對 Managed Browser 應用程式建立軟體部署，然後將其與您建立的受管理瀏覽器原則產生關聯。

> [!IMPORTANT]
> 受管理的瀏覽器原則不會使用與其他 Intune 原則相同的方式來進行部署。 此類型的原則必須與受管理的瀏覽器軟體套件相關聯。

部署應用程式，確定您在 [行動應用程式管理]  頁面上選取了受管理的瀏覽器原則，並將該原則與應用程式產生關聯。

如需如何部署應用程式的詳細資訊，請參閱[在 Microsoft Intune 中部署應用程式](deploy-apps-in-microsoft-intune.md)。

## <a name="security-and-privacy-for-the-managed-browser"></a>受管理瀏覽器的安全性與隱私權

-   在 iOS 裝置上，無法開啟使用者利用過期或未受信任的憑證瀏覽的網站。

-   Managed Browser 不會使用使用者在其裝置上針對內建瀏覽器所做的設定。 這是因為受管理的瀏覽器沒有這些設定的存取權。

-   如果您在已與 Managed Browser 建立關聯的行動應用程式管理原則中設定了 **[需要簡單的 PIN 以進行存取]** 或 **[需要公司認證以進行存取]** 選項，而且使用者選取驗證頁面上的說明連結，他們就可以瀏覽任何的網際網路網站，而不論其是否已加入受管理瀏覽器原則的封鎖清單中。

-   Managed Browser 可以在直接存取網站時，只封鎖網站的存取。 使用中繼服務 (例如翻譯服務) 存取網站時，它無法封鎖存取。

-   若要允許驗證，並確定 Intune 文件可供存取，請從允許或封鎖清單設定中排除 **&#42;.microsoft.com**。 一律允許。

### <a name="turn-off-usage-data"></a>關閉使用量資料
Microsoft 會自動收集有關 Managed Browser 效能和使用的匿名資料，以改善 Microsoft 產品和服務。 使用者可以在裝置上使用 **[使用方式資料]** 設定以關閉資料收集。 您無法控制這項資料的收集。

## <a name="reference-information"></a>參考資訊

### <a name="url-format-for-allowed-and-blocked-urls"></a>適用於允許和封鎖 URL 的 URL 格式
使用下列資訊，來了解您在允許和封鎖清單中指定 URL 時可使用的允許格式與萬用字元：

-   您可以根據下列許可模式清單中的規則，來使用萬用字元符號 (**&#42;**)。

-   確定您在清單中輸入 UTL 時，已在所有 URL 中加上 **http** 或 **https** 的前置詞。

-   您可以在位址中指定連接埠號碼。 如果未指定連接埠號碼，將使用下列值：

    -   針對 http 使用連接埠 80

    -   針對 https 使用連接埠 443

    不支援對連接埠號碼使用萬用字元。 例如，不支援 **http&colon;//www&period;contoso&period;com:*;** 與 **http&colon;//www&period;contoso&period;com: /*;**。

-   使用下表來了解您在指定 URL 時可使用的允許模式：

|URL|詳細資料|相符項|不符合|
    |-------|---------------|-----------|------------------|
    |http://www.contoso.com|比對單一頁面|www.contoso.com|host.contoso.com<br /><br />www.contoso.com/images<br /><br />contoso.com/|
    |http://contoso.com|比對單一頁面|contoso.com/|host.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com|
    |http://www.contoso.com/&#42;|比對所有以 www.contoso.com 開頭的 URL|www.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com/videos/tvshows|host.contoso.com<br /><br />host.contoso.com/images|
    |http://&#42;.contoso.com/&#42;|比對 contoso.com 下的所有子網域|developer.contoso.com/resources<br /><br />news.contoso.com/images<br /><br />news.contoso.com/videos|contoso.host.com|
    |http://www.contoso.com/images|比對單一資料夾|www.contoso.com/images|www.contoso.com/images/dogs|
    |http://www.contoso.com:80|使用連接埠號碼來比對單一頁面|http://www.contoso.com:80||
    |https://www.contoso.com|比對單一且安全的頁面|https://www.contoso.com|http://www.contoso.com|
    |http://www.contoso.com/images/&#42;|符合單一資料夾及所有子資料夾|www.contoso.com/images/dogs<br /><br />www.contoso.com/images/cats|www.contoso.com/videos|

-   以下是一些您無法指定的輸入範例：

    -   &#42;.com

    -   &#42;.contoso/&#42;

    -   www.contoso.com/&#42;images

    -   www.contoso.com/&#42;images&#42;pigs

    -   www.contoso.com/page&#42;

    -   IP 位址

    -   https://&#42;

    -   http://&#42;

    -   http://www.contoso.com:&#42;

    -   http://www.contoso.com: /&#42;

### <a name="how-conflicts-between-the-allow-and-block-list-are-resolved"></a>如何解決允許和封鎖清單間的衝突
如果將多個受管理的瀏覽器原則部署到裝置且設定發生衝突，則會針對衝突評估這兩種模式 (允許或封鎖) 和 URL 清單。 一旦發生衝突，會採用下列行為：

-   如果每個原則中的模式都一樣，但 URL 清單不同，則不會在裝置上強制執行 URL。

-   如果每個原則中的模式都不同，但 URL 清單一樣，則不會在裝置上強制執行 URL。

-   如果裝置是第一次接收受管理的瀏覽器原則且有兩個原則發生衝突，則不會在裝置上強制執行 URL。 請使用 [原則]  工作區的 [原則衝突]  節點來檢視衝突。

-   如果裝置已經接收受管理的瀏覽器原則且部署的第二個原則含有發生衝突的設定，則會在裝置上保留原始的設定。 請使用 [原則]  工作區的 [原則衝突]  節點來檢視衝突。

