---
# required metadata

title: 限制存取 SharePoint Online | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: b088e5a0-fd4a-4fe7-aa49-cb9c8cfb1585

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 限制存取 SharePoint Online
使用 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 條件式存取來控制存取位於 SharePoint Online 的檔案。
條件式存取有兩個元件：
- 裝置相容性原則，裝置必須符合此原則才算相容。
- 條件式存取原則，其中指定裝置必須符合才能存取服務的條件。
若要深入了解條件式存取如何運作，請參閱[限制存取電子郵件和 O365 服務](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)主題。

當使用者嘗試在其裝置 (例如 OneDrive) 上使用支援的應用程式連接到檔案時，將會進行下列評估：

![此圖顯示決定允許或禁止裝置存取 SharePoint 的決策點 ](../media/ConditionalAccess8-6.png)

>[!IMPORTANT]
>透過使用新式驗證的應用程式來設定電腦和 Windows 10 行動裝置版的條件式存取，目前未提供給所有 Intune 客戶使用。 如果您已經在使用這些功能，您不需要採取任何動作。 您可以繼續使用它們。

>如果您尚未針對使用新式驗證的應用程式建立電腦或 Windows 10 行動裝置版的條件式存取原則，但想要這樣做，您必須提交要求。  您可以在 [Connect 網站](http://go.microsoft.com/fwlink/?LinkId=761472)了解已知問題及如何存取這項功能的相關資訊

設定 SharePoint Online 的條件式存取原則之前，您必須：
- 具有 SharePoint Online 訂用帳戶，且使用者必須獲得 SharePoint Online 的授權。
- 具有 Enterprise Mobility Suite 或 Azure Active Directory Premium 的訂用帳戶

  若要連接到所需的檔案，裝置必須：
-   已向 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 註冊或是已加入網域的電腦。

-   在 Azure Active Directory 中註冊裝置 (自動發生於當裝置註冊到


-   與所有已部署的 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 相容性原則相容

裝置狀態儲存在 Azure Active Directory，它會根據您指定的條件，授與或封鎖檔案的存取權。

如不符合條件，使用者會在登入時看見下列訊息之一：

-   如果裝置未向 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 註冊，或未在 Azure Active Directory 中註冊，就會顯示訊息，指示如何安裝公司入口網站應用程式並註冊。

-   如果裝置不相容，就會顯示訊息，將使用者引導至 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 公司入口網站，讓他們找到問題的相關資訊，以及如何修復問題的方法。

## 支援行動裝置
- iOS 7.1 和更新版本
- Android 4.0 和更新版本、Samsung Knox Standard 4.0 或更新版本
- Windows Phone 8.1 和更新版本

## 對電腦的支援
- Windows 8.1 及更新版本 (已向 Intune 註冊)
- Windows 7.0 或 Windows 8.1 (已加入網域時)

  - 已加入網域的電腦必須設定為向 Azure Active Directory [自動登錄](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/)。
Intune 和 Office 365 客戶將會自動啟用 AAD DRS。 已部署 ADFS 裝置註冊服務的客戶不會在其內部部署 Active Directory 中看到已註冊的裝置。

  - 如果原則設為需要加入網域，而電腦未加入網域，即會顯示連絡 IT 管理員的訊息。

  - 如果原則設為需要加入網域或相容，但電腦不符合任一要求，即會顯示訊息，指示如何安裝公司入口網站應用程式並註冊。
-    [必須啟用 Office 365 新式驗證](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)，並安裝所有最新的 Office 更新。

    新式驗證將 Active Directory 驗證程式庫 (ADAL) 登入整合到 Office 2013 Windows 用戶端中，提供更高的安全性，例如多因素驗證和憑證式驗證。


## 設定 SharePoint Online 的條件式存取

### 步驟 1：設定 Active Directory 安全性群組
在開始之前，請先為條件式存取原則設定 Azure Active Directory 安全性群組。 您可以在 Office 365 系統管理中心或 Intune 帳戶入口網站中設定這些群組。 這些群組將用於設定原則的目標使用者，或將使用者豁免於原則。 當使用者成為原則的目標時，他們使用的每個裝置都必須相容，才能存取資源。

您可以在 SharePoint Online 原則中指定兩種群組類型：

-   目標群組 - 包含套用原則的使用者群組。

-   豁免群組 - 包含豁免於原則的使用者群組。

如果使用者隸屬於這兩個群組，他們將免套用原則。

### 步驟 2：設定及部署相容性原則
如果您尚未這麼做，請建立相容性原則，並部署到 SharePoint Online 原則的目標使用者。

> 雖然相容性原則會部署到 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 群組，但條件式存取原則以 Azure Active Directory 安全性群組為目標。

如需如何設定相容性原則的詳細資料，請參閱[建立相容性原則](create-a-device-compliance-policy-in-microsoft-intune.md)

> 如果您尚未部署相容性原則，則會將裝置視為相容。

當您準備好時，請繼續執行步驟 3

### 步驟 3：設定 SharePoint Online 原則
接著，設定原則要求只有受管理和相容的裝置才可以存取 SharePoint Online。 這項原則會儲存在 Azure Active Directory。

#### <a name="bkmk_spopolicy"></a>

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，按一下 [原則] > [條件式存取] > [SharePoint Online 原則]
![[SharePoint Online 原則] 頁面的螢幕擷取畫面](../media/IntuneSASharePointOnlineCAPolicy.png)

2.  選取 [啟用 SharePoint Online 的條件式存取原則] 

3.  在 [應用程存取] 下，您可以選擇將條件式存取原則套用至：

    -   **所有平台**

        任何用來存取 SharePoint Online 的裝置都必須在 Intune 中註冊並符合原則。  任何使用新式驗證的用戶端應用程式都必須遵守條件式存取原則。 如果 Intune 目前不支援此平台，則會禁止存取 SharePoint Online
        >[!TIP]
        >如果您尚未對電腦使用條件式存取，可能看不到此選項。  請改用 [特定平台]。 電腦的條件式存取目前未提供給所有 Intune 客戶使用。   您可以在 [Microsoft Connect 網站](http://go.microsoft.com/fwlink/?LinkId=761472)了解已知問題及如何存取這項功能的相關資訊

    -   **特定平台**

         條件式存取原則會套用至在您指定的平台上使用新式驗證的任何用戶端應用程式。

     Windows 電腦則必須已加入網域，或已向 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 註冊且相容。 您可以設定下列要求：

     -   **裝置必須已加入網域或相容。** 如果您希望電腦已加入網域或符合 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 中設定的原則，請選擇此選項。 如果電腦不符合上述任一需求，則會提示使用者將裝置註冊到

     -   **裝置必須已加入網域。** 選擇此選項會要求電腦必須已加入網域才能存取 Exchange Online。 如果電腦未加入網域，則會封鎖存取電子郵件並提示使用者連絡 IT 管理員。

     -   **裝置必須相容。** 選擇此選項會要求電腦必須在 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 註冊且相容。 如果電腦未註冊，則會顯示註冊指示訊息。

4.  按一下 [目標群組] 下方的 [修改]  ，選取要套用原則的 Azure Active Directory 安全性群組。 您可以選擇針對所有使用者，或僅針對選取的使用者群組。

5.  按一下 [豁免群組] 下方的 [修改]  ，選取豁免此原則的 Azure Active Directory 安全性群組。

6.  完成之後，請按一下 [儲存]

您不需部署條件式存取原則，它會立即生效。

### 步驟 4：監視相容性及條件式存取原則
在 [群組]  工作區中，您可以檢視裝置的狀態。

選取任何行動裝置群組，然後在 [裝置]  索引標籤上，選取下列 [篩選器] 其中之一：

-   [沒有登錄 AAD 的裝置] – 從 SharePoint Online 封鎖這些裝置。

-   [不相容的裝置] – 從 SharePoint Online 封鎖這些裝置。

-   [已登錄了 AAD 並相容的裝置] – 這些裝置可以存取 SharePoint Online。

### 請參閱
[使用 Microsoft Intune 限制電子郵件和 O365 服務的存取](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->


