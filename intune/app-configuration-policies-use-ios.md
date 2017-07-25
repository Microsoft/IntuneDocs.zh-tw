---
title: "如何使用 iOS 適用的 Intune 應用程式設定原則"
titleSuffix: Intune on Azure
description: "了解如何使用應用程式設定原則在 iOS 應用程式執行時，將設定資料提供給該應用程式。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0cbcf70af17ba7690f54196790da04becd8ba1eb
ms.sourcegitcommit: 388c5f59bc992375ac63968fd7330af5d84a1348
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-ios"></a>如何使用 iOS 適用的 Microsoft Intune 應用程式設定原則

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

在 Microsoft Intune 中使用應用程式設定，以提供使用者執行 iOS 應用程式時會使用的設定。 例如，應用程式可能需要使用者指定：

-   自訂連接埠號碼。

-   語言設定。

-   安全性設定。

-   公司標誌等品牌設定。

若使用者未正確輸入這些設定，可能會增加技術支援中心的負擔，使得採用新應用程式的速度變慢。

應用程式組態原則可讓您在使用者執行應用程式之前，將這些設定指派給使用者來避開這些問題。 這些設定會自動提供，使用者無須採取任何動作。

您不會直接將這些原則部署給使用者與裝置。 而是將原則與應用程式關聯，然後再指派應用程式。 每當應用程式檢查是否有原則設定時 (通常於初次執行時)，都會加以使用。

> [!TIP]
> 此原則類型目前僅針對執行 iOS 8.0 和更新版本的裝置提供。 它支援下列應用程式安裝類型︰
>
> -   **App Store 中的受管理 iOS 應用程式**
> -   **iOS 應用程式套件**
>
> 如需應用程式安裝類型的詳細資訊，請參閱[如何將應用程式新增至 Microsoft Intune](apps-add.md)。

## <a name="create-an-app-configuration-policy"></a>建立應用程式設定原則
1.  登入 Azure 入口網站。
2.  選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3.  在 [Intune] 刀鋒視窗上，選擇 [行動應用程式]。
4.  在 [行動應用程式] 工作負載中，選擇 [管理] > [應用程式設定原則]。
5.  在原則清單刀鋒視窗中選擇 [新增]。
6.  在 [新增設定原則] 刀鋒視窗上，為應用程式原則提供 [名稱] 及選擇性 [敘述]。
7.  對於 [裝置註冊類型]，請選擇下列其中一項：
    - **已向 Intune 註冊** - 適用於已整合 Intune 應用程式 SDK，且受 Intune 管理的應用程式。
    - **未向 Intune 註冊** - 適用於已整合 Intune 應用程式 SDK，且不受 Intune 管理，或由另一個解決方案管理的應用程式。
8.  對於 [平台]，請選擇 [iOS] (僅限已向 Intune 註冊的裝置)
9.  選擇 [相關聯的應用程式]，然後在 [相關聯的應用程式] 刀鋒視窗中，選擇要套用設定之受管理的應用程式。
10. 在 [新增設定原則] 刀鋒視窗上，選擇 [組態設定]
11. 在 [組態設定] 刀鋒視窗上，於下列選項中，選擇您想要如何指定組成組態設定檔的 XML 值：
    - **輸入 XML 資料** (僅限已向 Intune 註冊的裝置) - 輸入或貼上 XML 屬性清單，其中包含您需要的應用程式組態設定。 XML 屬性清單的格式會依您所設定的應用程式而有所不同。 如需所要使用之確切格式的詳細資訊，請連絡應用程式供應商。
Intune 會檢查您輸入的 XML 格式是否正確。 而不會檢查 XML 屬性清單是否適用於已建立關聯的應用程式。
若要深入了解 XML 屬性清單，請參閱 iOS Developer Library 中的 [Understanding XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)。
    - **使用設定設計工具** (不論裝置是否已向 Intune 註冊) - 讓您能夠在入口網站中直接指定 XML 索引鍵/值組。
11. 當您完成時，請返回 [新增設定原則] 刀鋒視窗，然後點擊 [建立]。

已建立此原則，並顯示在 [原則清單] 刀鋒視窗上。



>[!Note]
>不論裝置是否已向 Intune 註冊，您都可以使用 [Intune App SDK](https://docs.microsoft.com/intune/app-sdk-ios) 準備讓企業營運應用程式受 Intune 應用程式防護原則及應用程式設定原則管理。 例如，您可以使用應用程式設定原則，設定 [Intune Managed Browser](app-configuration-managed-browser.md) 允許及封鎖的 URL。 只要應用程式與這些原則相容，即可使用原則加以設定。


當指派的應用程式在裝置上執行時，會依照您在應用程式設定原則中的設定執行。
請參閱您正在設定之應用程式的文件以取得資訊，了解若一或多個應用程式設定原則發生衝突，會產生甚麼影響。

>[!Tip]
>此外，您也可以使用圖形 API 來完成這些工作。 如需詳細資料，請參閱 [Graph API Reference MAM Targeted Config](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create) (以圖形 API 參考 MAM 為目標的設定)。


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

## <a name="next-steps"></a>後續步驟

一如往常般地[指派](apps-deploy.md)及[監視](apps-monitor.md)應用程式。