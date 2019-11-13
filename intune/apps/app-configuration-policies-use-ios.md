---
title: 為受控的 iOS 裝置新增應用程式設定原則
titleSuffix: Microsoft Intune
description: 了解如何使用應用程式設定原則在 iOS 應用程式執行時，將設定資料提供給該應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ee3ecd64254c0e212ffc86155d677bf18ba647a
ms.sourcegitcommit: f6b82c62af81a2643a1aaec774afa42d02eef352
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566187"
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>為受控的 iOS 裝置新增應用程式設定原則

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

使用 Microsoft Intune 中的應用程式設定原則，提供 iOS 應用程式的自訂組態設定。 這些組態設定可讓您根據應用程式供應商指示來自訂應用程式。 您必須從應用程式的供應商取得這些組態設定 (金鑰和值)。 若要設定應用程式，請以金鑰和值的形式，或以包含金鑰和值的 XML 形式來指定設定。

身為 Microsoft Intune 系統管理員，您可以控制在受控裝置上要新增至 Microsoft Office 應用程式的使用者帳戶。 您可以僅允許組織使用者帳戶進行存取，並封鎖已註冊裝置上的個人帳戶。 支援的應用程式會處理應用程式設定和移除，並封鎖未經核准的帳戶。 每當應用程式檢查是否有設定原則設定時 (通常是第一次執行時)，便會使用這些設定。

新增應用程式設定原則後，就可以設定指派應用程式設定原則。 當您設定原則指派時，您可以選擇包含與排除要套用原則的使用者群組。 當您選擇要包含一或多個群組時，您可以選擇選取要包含特定群組或選取內建群組。 內建群組包括 [所有使用者]  、[所有裝置]  和 [所有使用者及所有裝置]  。 

> [!NOTE]
> Intune 會在主控台中提供預先建立的 [所有使用者]  和 [所有裝置]  群組，附有內建的最佳化方便您使用。 強烈建議您使用這些群組針對所有使用者和所有裝置，而不是您自行建立的任何「所有使用者」或「所有裝置」群組。

選取應用程式設定原則包含的群組後，您也可以選擇要排除的特定群組。 如需詳細資訊，請參閱 [Microsoft Intune 的包含與排除應用程式指派](apps-inc-exl-assignments.md)。

> [!TIP]
> 此原則類型目前僅針對執行 iOS 8.0 和更新版本的裝置提供。 它支援下列應用程式安裝類型︰
>
> - **App Store 中的受管理 iOS 應用程式**
> - **iOS 應用程式套件**
>
> 如需應用程式安裝類型的詳細資訊，請參閱[如何將應用程式新增至 Microsoft Intune](apps-add.md)。 如需將應用程式設定整合至受控裝置的 .ipa 應用程式套件的詳細資訊，請參閱 [iOS 開發人員文件](https://developer.apple.com/library/archive/samplecode/sc2279/Introduction/Intro.html) \(英文\) 中的受控應用程式組態。

## <a name="create-an-app-configuration-policy"></a>建立應用程式設定原則

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 選擇 [用戶端應用程式]  工作負載。
4. 選擇 [管理]  群組中的 [應用程式設定原則]  ，然後選擇 [新增]  。
5. 使用下列詳細資料：
    - **名稱** - 在 Azure 入口網站中顯示的設定檔名稱。
    - **描述** - 在 Azure 入口網站中顯示的設定檔描述。
    - **裝置註冊類型** - 針對已在 Intune 註冊的裝置選擇 [受控裝置]  。
6. 為 [平台]  選取 [iOS]  。
7. 選擇 [相關聯的應用程式]  。 然後，在 [相關聯的應用程式]  窗格上，選擇要套用設定的受控應用程式，然後選取 [確定]  。
8. 在 [新增設定原則]  窗格上，選擇 [組態設定]  。
9. 選取 [組態設定格式]  。 選取下列其中一種方法來新增設定資訊：
    - **使用設定設計工具**
    - **輸入 XML 資料**<br><br>
    如需使用設定設計工具的詳細資料，請參閱[使用設定設計工具](#use-configuration-designer)。 如需輸入 XML 資料的詳細資料，請參閱[輸入 XML 資料](#enter-xml-data)。 
10. 新增設定資訊之後，選擇 [確定]  ，然後選擇 [新增]  來新增設定原則。 即會顯示設定原則的概觀窗格。
11. 選取 [指派]  來顯示包含與排除選項。 

    ![[原則指派] [包含] 索引標籤的螢幕擷取畫面](./media/app-configuration-policies-use-ios/app-config-policy01.png)
12. 選取 [包含]  索引標籤的 [所有使用者]  。

    ![[原則指派 - 所有使用者] 下拉式選項的螢幕擷取畫面](./media/app-configuration-policies-use-ios/app-config-policy02.png)
13. 選取 [排除]  索引標籤。 
14. 按一下 [選取要排除的群組]  以顯示相關的窗格。

    ![[原則指派 - 選取要排除的群組] 刀鋒視窗的螢幕擷取畫面](./media/app-configuration-policies-use-ios/app-config-policy03.png)
15. 選擇您要排除的群組，然後按一下 [選取]  。

    >[!NOTE]
    >新增群組時，如已包含任何其他群組用於指定的指派類型，就會預先選取且無法針對其他包含指派類型進行變更。 因此，已使用的該群組，不能用為排除的群組。
16. 按一下 **[儲存]** 。

## <a name="use-configuration-designer"></a>使用設定設計工具

Microsoft Intune 提供應用程式專屬的組態設定。 您可在 Microsoft Intune 中已註冊或未註冊的裝置上，針對應用程式使用設定設計工具。 設計工具可讓您設定特定的設定金鑰和值，以協助您建立基礎 XML。 您也必須指定每個值的資料類型。 安裝應用程式時，會自動將這些設定提供給應用程式。

### <a name="add-a-setting"></a>新增設定

1. 對於設定中的每個金鑰和值，請設定：
   - **設定金鑰** - 唯一識別特定設定組態的金鑰。
   - **實值型別** - 設定值的資料類型。 類型包括整數、實數、字串或布林值。
   - **設定值** - 設定的值。
2. 選擇 [確定]  來設定您的組態設定。

### <a name="delete-a-setting"></a>刪除設定

1. 選擇設定旁邊的省略符號 ( **...** )。
2. 選取 [刪除]  。

\{\{ 和 \}\} 字元僅供權杖類型使用，絕不能用於其他用途。

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>在多重身分識別應用程式中只允許設定的組織帳戶 

針對 iOS 裝置，請使用下列機碼/值組：

| **Key** | IntuneMAMAllowedAccountsOnly |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **值** | <ul><li>**啟用**：唯一允許的帳戶是 [IntuneMAMUPN](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm) 機碼所定義的受控使用者帳戶。</li><li>**Disabled** (或任何不是以不區分大小寫方式與 **Enabled** 相符的值)：允許任何帳戶。</li></ul> |。

   > [!NOTE]
   > 只允許搭配多身分識別使用已設定的組織帳戶時，您必須使用 iOS 版 OneDrive 10.34 或更新版本、iOS 版Outlook 2.99.0 或更新版本或 iOS 版 Edge 44.8.7 或更新版本，且必須使用 [Intune 應用程式保護原則](app-protection-policy.md)將應用程式設為目標。

## <a name="enter-xml-data"></a>輸入 XML 資料

您可以輸入或貼上 XML 屬性清單，其中包含 Intune 中所註冊裝置的應用程式組態設定。 XML 屬性清單的格式會依您所設定的應用程式而有所不同。 如需所要使用之確切格式的詳細資訊，請連絡應用程式供應商。

Intune 會驗證 XML 格式。 但 Intune 不會檢查 XML 屬性清單 (PList) 是否適用於目標應用程式。

若要深入了解 XML 屬性清單：

- 請參閱 iOS 開發人員程式庫的 [Understand XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (了解 XML 屬性 Plist)。

### <a name="example-format-for-an-app-configuration-xml-file"></a>應用程式設定 XML 檔案的範例格式

當您建立應用程式設定檔時，可以使用下列格式指定下列一或多個值︰

```xml
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
  <key>aaddeviceid</key>
  <string>{{aaddeviceid}}</string>
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
- \{\{userprincipalname\}\}—例如，**John\@contoso.com**
- \{\{mail\}\}—例如，**John\@contoso.com**
- \{\{partialupn\}\}—例如，**John**
- \{\{accountid\}\}—例如，**fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\}—例如，**b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\}—例如，**3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\}—例如，**John Doe**
- \{\{serialnumber\}\}—例如，**F4KN99ZUG5V2** (適用於 iOS 裝置)
- \{\{serialnumberlast4digits\}\}—例如，**G5V2** (適用於 iOS 裝置)
- \{\{aaddeviceid\}\} - 例如 **ab0dc123-45d6-7e89-aabb-cde0a1234b56**

## <a name="configure-the-company-portal-app-to-support-ios-dep-devices"></a>設定公司入口網站應用程式以支援 iOS DEP 裝置

DEP (Apple 的裝置註冊計劃) 註冊與公司入口網站應用程式的 App Store 版本不相容。 不過，您可以使用下列步驟，將公司入口網站應用程式設定成支援 iOS DEP 裝置。

1. 在 Azure 入口網站上的 Intune 中：
    - 如有必要，請移至 [Intune]   > [用戶端應用程式]   > [應用程式]   > [新增]  來新增 Intune 公司入口網站。
    - 移至 [用戶端應用程式]   > [應用程式設定原則]  ，以建立公司入口網站應用程式的應用程式設定原則。
2. 使用以下 XML 建立應用程式設定原則。 如需如何建立應用程式設定原則和輸入 XML 資料的詳細資訊，請參閱[為受控的 iOS 裝置新增應用程式設定原則](app-configuration-policies-use-ios.md)，或針對混合式 MDM，請參閱[在 System Center Configuration Manager 中使用應用程式設定原則將設定套用至 iOS 應用程式](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-ios-apps-with-app-configuration-policies) \(部分機器翻譯\)。

    ``` xml
    <dict>
        <key>IntuneCompanyPortalEnrollmentAfterUDA</key>
        <dict>
            <key>IntuneDeviceId</key>
            <string>{{deviceid}}</string>
            <key>UserId</key>
            <string>{{userid}}</string>
        </dict>
    </dict>
    ```

3. 使用目標為所需群組的應用程式設定原則，來將公司入口網站部署到裝置。 確定只將原則部署到已向 DEP 註冊的裝置群組。
4. 告訴終端使用者在自動安裝公司入口網站應用程式時登入。

## <a name="monitor-ios--app-configuration-status-per-device"></a>監視每個裝置的 iOS 應用程式設定狀態 
一旦指派設定原則，您可以監視每個受控裝置的 iOS 應用程式設定狀態。 從 Azure 入口網站的 [Microsoft Intune]  中，選取 [裝置]   > [所有裝置]  。 從受控裝置清單中，選取特定的裝置以顯示裝置的刀鋒視窗。 在裝置的刀鋒視窗中，選取 [應用程式設定]  。  

## <a name="additional-information"></a>其他資訊

- [部署 iOS 與 Android 版 Outlook 應用程式組態設定](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune) \(部分機器翻譯\)

## <a name="next-steps"></a>後續步驟

繼續[指派](apps-deploy.md)及[監視](apps-monitor.md)應用程式。
