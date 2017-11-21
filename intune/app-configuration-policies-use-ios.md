---
title: "為受管理的 iOS 裝置新增應用程式設定原則 | Microsoft Docs"
titlesuffix: Azure portal
description: "了解如何使用應用程式設定原則在 iOS 應用程式執行時，將設定資料提供給該應用程式。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2226477d40f2bb70dd047ed58e8789fd9bee4ecb
ms.sourcegitcommit: ce35790090ebe768d5f75c108e8d5934fd19c8c7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>為受管理的 iOS 裝置新增應用程式設定原則

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

在 Microsoft Intune 中使用應用程式設定原則，以提供使用者執行 iOS 應用程式時的設定。 您不會直接將這些原則部署給使用者與裝置。 而是將原則與應用程式關聯，然後再指派應用程式。 每當應用程式檢查是否有原則設定時 (通常是第一次執行時)，便會使用這些原則設定。

> [!TIP]
> 此原則類型目前僅針對執行 iOS 8.0 和更新版本的裝置提供。 它支援下列應用程式安裝類型︰
>
> -   **App Store 中的受管理 iOS 應用程式**
> -   **iOS 應用程式套件**
>
> 如需應用程式安裝類型的詳細資訊，請參閱[如何將應用程式新增至 Microsoft Intune](apps-add.md)。

## <a name="create-an-app-configuration-policy"></a>建立應用程式設定原則

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  +  [Intune]。
3. 選擇 [Mobile Apps] 工作負載。
4. 選擇 [管理] 群組中的 [應用程式設定原則]，然後選擇 [新增]。
5. 使用下列詳細資料：
    - **名稱**<br>
      將在 Azure 入口網站中顯示的設定檔名稱。
    - **描述**<br>
      將在 Azure 入口網站中顯示的設定檔描述。
    - **裝置註冊類型**<br>
      選擇 [受管理裝置]。
6. 為 [平台] 選取 [iOS]。
7.  選擇 [相關聯的應用程式]。 然後在 [相關聯的應用程式] 刀鋒視窗中，選擇要套用設定的受管理應用程式。
8.  在 [新增設定原則] 刀鋒視窗上，選擇 [組態設定]。
9. 選取 [組態設定格式]。 選取下列其中一項：
    - **[使用設定設計工具](#Use-the-configuration-designer)**
    - **[輸入 XML 資料](#enter-xml-data)**
10. 選擇 [確定]，然後選擇 [新增]。

## <a name="use-configuration-designer"></a>使用設定設計工具

您可以在 Intune 中已註冊或未註冊的裝置上，針對應用程式使用設定設計工具。 設計工具可讓您設定特定的設定金鑰和值。 您也必須指定每個值的資料類型。 安裝應用程式時，會自動將設定值提供給應用程式。

### <a name="add-a-setting"></a>新增設定

1. 對於設定中的每個金鑰和值，請設定：
   - **設定金鑰**<br>
     唯一識別特定設定組態的金鑰。
   - **實值型別**<br>
     設定值的資料類型。 類型包括整數、實數、字串或布林值。
   - **設定值**<br>
     設定的值。
2. 選擇 [確定] 來設定您的組態設定。

### <a name="delete-a-setting"></a>刪除設定

1. 選擇設定旁邊的省略符號 (**...**)。
2. 選取 [刪除]。

\{\{ 和 \}\} 字元僅供權杖類型使用，絕不能用於其他用途。

## <a name="enter-xml-data"></a>輸入 XML 資料

您可以輸入或貼上 XML 屬性清單，其中包含 Intune 中所註冊裝置的應用程式組態設定。 XML 屬性清單的格式會依您所設定的應用程式而有所不同。 如需所要使用之確切格式的詳細資訊，請連絡應用程式供應商。

Intune 會驗證 XML 格式。 但 Intune 不會檢查 XML 屬性清單 (PList) 是否適用於目標應用程式。

若要深入了解 XML 屬性清單：

  -  閱讀[在 Microsoft Intune 中使用行動應用程式設定原則設定 iOS 應用程式](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。
  -  請參閱 iOS 開發人員程式庫的 [Understand XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (了解 XML 屬性 Plist)。

### <a name="example-format-for-an-app-configuration-xml-file"></a>應用程式設定 XML 檔案的範例格式

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
### <a name="supported-xml-plist-data-types"></a>支援的 XML PList 資料類型

Intune 支援屬性清單中的下列資料類型：

- &lt;integer&gt;
- &lt;real&gt;
- &lt;string&gt;
- &lt;array&gt;
- &lt;dict&gt;
- &lt;true /&gt; 或 &lt;false /&gt;

### <a name="tokens-used-in-the-property-list"></a>屬性清單中使用的權杖

此外，Intune 支援屬性清單中的下列權杖類型︰
- \{\{userprincipalname\}\}—例如，**John@contoso.com**
- \{\{mail\}\}—例如，**John@contoso.com**
- \{\{partialupn\}\}—例如，**John**
- \{\{accountid\}\}—例如，**fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\}—例如，**b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\}—例如，**3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\}—例如，**John Doe**
- \{\{serialnumber\}\}—例如，**F4KN99ZUG5V2** (適用於 iOS 裝置)
- \{\{serialnumberlast4digits\}\}—例如，**G5V2** (適用於 iOS 裝置)

## <a name="next-steps"></a>後續步驟

一如往常般地[指派](apps-deploy.md)及[監視](apps-monitor.md)應用程式。