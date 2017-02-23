---
title: "如何使用 Intune 應用程式設定原則 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解如何使用應用程式設定原則在 iOS 應用程式執行時，將設定資料提供給該應用程式。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 424fae862592c1ab5b4221fb5ad40a52c39f6760
ms.openlocfilehash: 75e3f3f62dd392cda1530321b12cd27e9ee8847f

---

# <a name="how-to-use-intune-app-configuration-policies"></a>如何使用 Intune 應用程式設定原則

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

在 Microsoft Intune 中使用應用程式設定原則，提供使用者執行應用程式時可能需要的設定。 例如，應用程式可能需要使用者指定：

-   自訂連接埠號碼。

-   語言設定。

-   安全性設定。

-   公司標誌等品牌設定。

如果使用者輸入不正確的設定，可能會增加技術支援中心的負擔，並使新應用程式的採用速度變慢。

應用程式組態原則可讓您在使用者執行應用程式之前，將這些設定指派給使用者來避開這些問題。 這些設定會自動提供，使用者無須採取任何動作。

您不會直接將這些原則部署給使用者與裝置。 您將會將原則與應用程式關聯，然後才部署應用程式。 每當應用程式檢查是否有原則時 (通常是第一次執行時)，便會使用這些原則設定。

> [!TIP]
> 此原則類型目前僅針對執行 iOS 8.0 和更新版本的裝置提供。 它支援下列應用程式安裝類型︰
>
> -   **App Store 中的受管理 iOS 應用程式**
> -   **iOS 應用程式套件**
>
> 如需應用程式安裝類型的詳細資訊，請參閱[如何將應用程式新增至 Microsoft Intune](/intune-azure/manage-apps/add-apps)。

## <a name="create-an-app-configuration-policy"></a>建立應用程式設定原則

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 **Intune** 刀鋒視窗上選擇 [管理應用程式]。
1.  在**管理應用程式**工作負載中選擇 [管理]  >  [應用程式設定原則]。

2.  在原則清單刀鋒視窗中選擇 [新增]。

3.  在 [新增設定原則] 刀鋒視窗中，為應用程式設定原則提供名稱，並視需要提供其描述。
4.  選擇 [相關聯的應用程式]，然後在 [相關聯的應用程式] 刀鋒視窗中，選擇要套用設定之受管理的應用程式。
5.  在 [新增設定原則] 刀鋒視窗中選擇 [組態設定]，然後在 [組態設定] 刀鋒視窗中，選擇下列其中一項，確認組成組態設定檔之 XML 值的指定方式︰
    - **輸入 XML 資料** - 輸入或貼上 XML 內容清單，其中包含您需要的應用程式組態設定。 XML 屬性清單的格式會依您所設定的應用程式而有所不同。 如需所要使用之確切格式的詳細資訊，請連絡應用程式供應商。
    Intune 會檢查您輸入的 XML 格式是否正確。 但 Intune 不會檢查 XML 屬性清單是否適用於相關聯的應用程式。
    若要深入了解 XML 屬性清單，請參閱 iOS Developer Library 中的 [Understanding XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)。
    - **使用設定設計工具** - 您可以直接在入口網站中指定 XML 索引鍵/值組。
8. 當您完成時，請返回 [新增設定原則] 刀鋒視窗，然後點擊 [建立]。

如此即可建立原則，並顯示在原則清單刀鋒視窗上。

接著一如往常般地繼續[指派](deploy-apps.md)及[監視](monitor-apps.md)應用程式。

當指派的應用程式在裝置上執行時，會依照您在應用程式組態原則中的設定執行。

> [!TIP]
> 當一或多項應用程式設定原則彼此衝突時，將不會執行任何一項原則。

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





## <a name="example-format-for-an-app-configuration-xml-file"></a>應用程式設定 XML 檔案的範例格式

當您建立應用程式設定檔時，可以使用下列格式指定下列一或多個值︰

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



<!--HONumber=Feb17_HO1-->


