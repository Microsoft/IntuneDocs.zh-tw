---
title: "Android for Work 應用程式設定原則"
description: "您可以在 Intune 中使用行動應用程式設定原則，來提供使用者執行 Android for Work 應用程式時可能需要的設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f2284920852de5a79cf47fee81922a5b069157c3
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="configure-android-for-work-apps-with-mobile-app-configuration-policies-in-microsoft-intune"></a>在 Microsoft Intune 中使用行動應用程式設定原則設定 Android for Work 應用程式

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

您可以在 Microsoft Intune 中使用行動裝置應用程式組態原則，來提供使用者執行應用程式時可能需要的設定。 例如，應用程式可能需要使用者指定：

-   自訂連接埠號碼
-   語言設定
-   公司標誌等品牌設定

如果使用者輸入不正確的設定，可能會增加技術支援中心的負擔，並使新應用程式的採用速度變慢。

行動應用程式設定原則可讓您在使用者執行應用程式之前，先將這些設定部署至裝置。 系統會自動提供這些設定，使用者不需要採取任何動作。

若要利用應用程式設定原則，應用程式開發人員必須在建立企業應用程式時公開其設定。 例如，Google Chrome 會公開設定，讓您設定預設書籤、允許和拒絕的網站等等。 請連絡應用程式的開發人員，確認這些設定是否受到支援，以及如何在原則中指定這些設定。

您會將應用程式設定原則，部署給您部署應用程式以進行設定的相同使用者。 執行應用程式時，會套用應用程式設定。

## <a name="configure-a-mobile-app-configuration-policy"></a>設定行動裝置應用程式組態原則

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [原則] &gt; [概觀] &gt; [新增原則]。

2.  在原則清單中，展開 [Android for Work]，選擇 [行動應用程式設定原則 (Android for Work)]，然後選擇 [建立原則]。

    > [!TIP]
    > 針對這種原則類型，您只能設定自訂設定。 沒有建議的設定。

3.  在 [建立原則] 頁面的 [一般] 區段中，為行動裝置應用程式組態原則提供名稱和選擇性描述。

4. 在頁面的 [行動應用程式設定原則] 區段中，指定下列資訊：
    - **此組態所套用之應用程式的套件識別碼** - 此套件識別碼可在 Google Play 頁面上之應用程式 URL 的 'id=' 區段中找到。 例如，Microsoft Excel 應用程式的套件識別碼為 **com.microsoft.office.excel**。
    - 在文字方塊中，輸入您想要設定的應用程式設定資料。 您可以從應用程式的供應商取得這些設定。 並非所有應用程式都支援這些設定。
5.  按一下 [驗證] 以確保您輸入的資料採用有效的內容清單格式。

    > [!IMPORTANT]
    > 當您按一下 [驗證] 時，Intune 會檢查您輸入的設定資料格式是否有效。 但不會檢查資料是否適用於相關聯的應用程式。

6.  完成之後，按一下 [儲存原則] 。

新的原則會顯示在 [組態原則]  節點中。


## <a name="deploy-the-app-configuration-policy"></a>部署應用程式設定原則
建立行動應用程式設定原則之後，您必須將其部署給您部署應用程式以套用設定的相同使用者。

如需如何部署原則的資訊，請參閱[部署設定原則](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy)

如需如何將應用程式部署至 Android for Work 裝置的資訊，請參閱[如何使用 Intune 部署 Android for Work 應用程式](android-for-work-apps.md)。

當已部署的應用程式在裝置上執行時，它會使用您在行動裝置應用程式組態原則中所做的設定來執行。

> [!TIP]
> 針對每個應用程式，只部署一個應用程式設定原則給使用者。
