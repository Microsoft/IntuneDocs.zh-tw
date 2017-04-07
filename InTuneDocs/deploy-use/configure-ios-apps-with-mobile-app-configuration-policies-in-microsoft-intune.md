---
title: "使用 iOS 行動應用程式設定原則 | Microsoft Docs"
description: "您可以在 Intune 中使用行動裝置應用程式組態原則，來提供使用者執行 iOS 應用程式時可能需要的設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: dfc76481a673dff5dd8be40659cc267a792760ec
ms.lasthandoff: 12/30/2016


---

# <a name="configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune"></a>在 Microsoft Intune 中使用行動裝置應用程式組態原則設定 iOS 應用程式

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

您可以在 Microsoft Intune 中使用行動裝置應用程式組態原則，來提供使用者執行應用程式時可能需要的設定。 例如，應用程式可能需要使用者指定：

-   自訂連接埠號碼。

-   語言設定。

-   安全性設定。

-   公司標誌等品牌設定。

如果使用者輸入不正確的設定，可能會增加技術支援中心的負擔，並使新應用程式的採用速度變慢。

行動裝置應用程式組態原則可協助您避免這些問題；您可以在使用者執行應用程式之前，先在原則中將這些設定部署給使用者。 接著系統會自動提供這些設定，使用者不需要採取任何動作。

您不會直接將這些原則部署給使用者和裝置。 您將會將原則與應用程式關聯，然後才部署應用程式。 每當應用程式檢查是否有原則時 (通常是第一次執行時)，便會使用這些原則設定。

> [!TIP]
> 此原則類型目前僅針對執行 iOS 8.0 和更新版本的裝置提供。 它支援下列應用程式安裝類型︰
>
> -   **App Store 中的受管理 iOS 應用程式**
> -   **iOS 應用程式套件**
>
> 如需應用程式安裝類型的詳細資訊，請參閱[使用 Microsoft Intune 部署應用程式](deploy-apps.md)。

## <a name="configure-a-mobile-app-configuration-policy"></a>設定行動裝置應用程式組態原則

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [原則] &gt; [概觀] &gt; [新增原則]。

2.  在原則清單中，展開 [iOS]，選擇 [行動裝置應用程式組態]，然後選擇 [建立原則]。

    > [!TIP]
    > 針對這種原則類型，您只能設定自訂設定。 沒有建議的設定。

3.  在 [建立原則] 頁面的 [一般] 區段中，為行動裝置應用程式組態原則提供名稱和選擇性描述。

4.  在頁面的 [行動裝置應用程式組態原則] 區段中，於方塊中輸入或貼上含有您所要應用程式組態設定的 XML 屬性清單。 XML 屬性清單的格式會依您所設定的應用程式而有所不同。 如需所要使用之確切格式的詳細資訊，請連絡應用程式供應商。

    > [!TIP]
    > 若要深入了解 XML 屬性清單，請參閱 iOS Developer Library 中的 [Understanding XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)。

5.  按一下 [驗證] 以確保您輸入的 XML 採用有效的屬性清單格式。

    > [!IMPORTANT]
    > 當您按一下 [驗證] 時，Intune 會檢查您輸入的 XML 格式是否有效。 但 Intune 不會檢查 XML 屬性清單是否適用於相關聯的應用程式。

6.  完成之後，按一下 [儲存原則] 。

新的原則會顯示在 [組態原則]  節點中。

## <a name="information-about-the-xml-file-format"></a>XML 檔案格式的相關資訊

Intune 支援屬性清單中的下列資料類型：
    
- &lt;integer&gt;
- &lt;real&gt;
- &lt;string&gt;
- &lt;array&gt;
- &lt;dict&gt;
- &lt;true /&gt; 或 &lt;false /&gt;
     
如需資料類型的詳細資訊，請參閱 iOS Developer Library 中的 [關於屬性清單](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) 。

此外，Intune 支援屬性清單中的下列權杖類型︰
- \{\{userprincipalname\}\} - (範例：**John@contoso.com**)
- \{\{mail\}\} - (範例：**John@contoso.com**)
- \{\{partialupn\}\} - (範例：**John**)
- \{\{accountid\}\} - (範例：**fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
- \{\{deviceid\}\} - (範例：**b9841cd9-9843-405f-be28-b2265c59ef97**)
- \{\{userid\}\} - (範例：**3ec2c00f-b125-4519-acf0-302ac3761822**)
- \{\{username\}\} - (範例：**John Doe**)
- \{\{serialnumber\}\} - 適用於 iOS 裝置 (範例：**F4KN99ZUG5V2**)
- \{\{serialnumberlast4digits\}\} - 適用於 iOS 裝置 (範例：**G5V2**)
    
\{\{ 和 \}\} 字元僅供權杖類型使用，絕不能用於其他用途。

## <a name="associate-a-mobile-app-configuration-policy-with-an-app"></a>建立行動裝置應用程式組態原則與應用程式的關聯
建立行動裝置應用程式組態原則之後，您必須將其與要套用組態原則之設定的 iOS 應用程式建立關聯。

若要這樣做，請遵循[在 Microsoft Intune 中新增行動裝置的應用程式](add-apps-for-mobile-devices-in-microsoft-intune.md)和[使用 Microsoft Intune 部署應用程式](deploy-apps-in-microsoft-intune.md)中建立應用程式部署的步驟。 在精靈的 [行動應用程式組態] 頁面中，從 [應用程式組態原則] 下拉式清單選取您要與應用程式建立關聯的原則。

然後，如往常般繼續部署和監視應用程式部署。

當已部署的應用程式在裝置上執行時，它會使用您在行動裝置應用程式組態原則中所做的設定來執行。

> [!TIP]
> 如果有一或多項行動裝置應用程式組態原則與彼此衝突，則不會強制執行任何一項原則。 這些衝突將會在 Intune 管理主控台的 [儀表板] 中做出報告。

## <a name="example-format-for-a-mobile-app-configuration-xml-file"></a>行動裝置應用程式組態 XML 檔案的範例格式

當您建立行動裝置應用程式組態檔時，您可以使用此格式指定下列的一或多個值︰

```
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
</dict>

```

