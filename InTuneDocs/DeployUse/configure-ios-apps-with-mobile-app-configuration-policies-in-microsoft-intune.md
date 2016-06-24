---
# required metadata

title: 在 Microsoft Intune 中使用行動裝置應用程式組態原則設定 iOS 應用程式 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 在 Microsoft Intune 中使用行動裝置應用程式組態原則設定 iOS 應用程式
您可以在 Microsoft Intune 中使用行動裝置應用程式組態原則，來提供使用者執行應用程式時可能需要的設定。 例如，應用程式可能需要使用者指定：

-   執行時的自訂連接埠號碼

-   語言設定

-   安全性設定

-   公司標誌等品牌設定

如果使用者輸入不正確的設定，可能會增加技術支援中心的負擔，並使新應用程式的採用速度變慢。

行動裝置應用程式組態原則可協助您避免這些問題；您可以在使用者執行應用程式之前，先在原則中將這些設定部署給使用者。 接著會自動提供這些設定，使用者不需要採取任何動作。

您不會直接將這些原則部署給使用者和裝置。 相反地，您會建立原則與應用程式的關聯，再部署應用程式。 每當應用程式檢查是否有原則時 (通常是第一次執行時)，便會使用這些原則設定。

> [!TIP]
> 這種原則類型目前僅適用於執行 iOS 7.1 和更新版本的裝置，並支援下列應用程式安裝類型：
> 
> -   **應用程式商店中的受管理 iOS 應用程式**
> -   **iOS 應用程式套件**
> 
> 如需應用程式安裝類型的詳細資訊，請參閱[使用 Microsoft Intune 部署應用程式](deploy-apps.md).

## 設定行動裝置應用程式組態原則

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，按一下 [原則] &gt; [概觀] &gt; [新增原則].

2.  在原則清單中，展開 [iOS]，按一下 [行動裝置應用程式組態]，然後按一下 [建立原則].

    > [!TIP]
    > 您只能針對這種原則類型進行自訂設定。 沒有建議的設定。

3.  在 [建立原則]  頁面的 [一般]  區段中，提供行動裝置應用程式組態原則的名稱和選擇性描述。

4.  在頁面之 [行動裝置應用程式組態原則]  區段的方塊中，輸入或貼上含有您想要之應用程式組態設定的 XML 屬性清單。

    > [!TIP]
    > 若要深入了解 XML 屬性清單，請參閱 iOS Developer Library 中的 [Understanding XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)。
    > 
    > XML 屬性清單的格式會依您所設定的應用程式而有所不同。 如需所要使用之確切格式的詳細資訊，請連絡應用程式供應商。
    > 
    > Intune 支援屬性清單中的下列資料類型：
    > 
    > &lt;整數&gt;
    > &lt;real&gt;
    > &lt;字串&gt;
    > &lt;array&gt;
    > &lt;dict&gt;
    > &lt;true /&gt; 或 &lt;false /&gt;
    > 
    > 如需資料類型的詳細資訊，請參閱 iOS Developer Library 中的 [關於屬性清單](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) 。
    >
        > 此外，Intune 支援屬性清單中的下列權杖類型︰
    >    
    > \{\{使用者主體名稱\}\} - (範例：John@contoso.com)
    > \{\{郵件\}\} - (範例：John@contoso.com)
    > \{\{部分 UPN\}\} - (範例：John)
    > \{\{帳戶識別碼\}\} - (範例：fc0dc142-71d8-4b12-bbea-bae2a8514c81)
    > \{\{裝置識別碼\}\} - (範例：b9841cd9-9843-405f-be28-b2265c59ef97)
    > \{\{使用者識別碼\}\} - (範例：3ec2c00f-b125-4519-acf0-302ac3761822)
    > \{\{使用者名稱\}\} - (範例：John Doe)
    > \{\{序號\}\} - 適用於 iOS 裝置 (範例：F4KN99ZUG5V2)
    > \{\{序號後 4 個數字\}\} - 適用於 iOS 裝置 (範例：G5V2)
>
> \{\{ 和 \}\} 字元僅供權杖類型使用，絕不能用於其他用途。




5.  按一下 [驗證]  ，以確保您輸入的 XML 採用有效的屬性清單格式。

    > [!IMPORTANT]
    > 當您按一下 [驗證] 時，Intune 會檢查您輸入的 XML 格式是否有效。 但不會檢查 XML 屬性清單是否適用於相關聯的應用程式。

6.  完成之後，按一下 [儲存原則].

新的原則會顯示在 [組態原則]  節點中。

## 建立行動裝置應用程式組態原則與應用程式的關聯
建立行動裝置應用程式組態原則之後，您必須將其與要套用組態原則之設定的 iOS 應用程式建立關聯。

若要這樣做，請遵循[在 Microsoft Intune 中新增行動裝置的應用程式](add-apps-for-mobile-devices-in-microsoft-intune.md)和[使用 Microsoft Intune 部署應用程式](deploy-apps-in-microsoft-intune.md)中建立應用程式部署的步驟。 在精靈的 行動應用程式組態 頁面中，從 應用程式組態原則 下拉式清單選取您要與應用程式建立關聯的原則。

然後，如往常般繼續部署和監視應用程式部署。

當已部署的應用程式在裝置上執行時，它會使用您在行動裝置應用程式組態原則中所做的設定來執行。

> [!TIP]
> 如果有一或多項行動裝置應用程式組態原則衝突，則不會強制執行任何一項原則，而且會在 Intune 管理主控台的 [儀表板] 中報告這項衝突.

## 行動應用程式設定 XML 檔案的範例格式

當您建立行動應用程式組態檔時，您可以使用這個格式指定一個或多個下列值︰

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




<!--HONumber=May16_HO1-->


