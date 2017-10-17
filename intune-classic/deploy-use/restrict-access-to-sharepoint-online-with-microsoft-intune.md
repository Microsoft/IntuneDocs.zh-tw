---
title: "保護 SharePoint Online"
description: "使用條件式存取保護與控制 SharePoint Online 上的公司資料存取。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b088e5a0-fd4a-4fe7-aa49-cb9c8cfb1585
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f86508d9b187e0026a74c4e82e94cdd5a4d29c3a
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2017
---
# <a name="protect-access-to-sharepoint-online-with-microsoft-intune"></a>使用 Microsoft Intune 限制存取 SharePoint Online

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用 Microsoft Intune 條件式存取來控制對於 SharePoint Online 上檔案的存取權。
條件式存取有兩個元件：
- 裝置合規性原則，裝置必須符合此原則才算符合規範。
- 條件式存取原則，其中您要指定裝置必須符合才能存取服務的條件。
若要深入了解條件式存取如何運作，請參閱[限制電子郵件、O365 和其他服務的存取](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)主題。

您要向使用者部署合規性及條件式存取原則。 使用者用來存取服務的所有裝置都會經過檢查，以確定符合原則規範。

當使用者嘗試在其裝置 (例如 OneDrive) 上使用支援的應用程式連接到檔案時，將會進行下列評估：

![此圖顯示決定允許或禁止裝置存取 SharePoint 的決策點](../media/ConditionalAccess8-6.png)


設定 SharePoint Online 的條件式存取原則**之前**，您必須：
- 具有 **SharePoint Online 訂用帳戶**，且使用者必須獲得 SharePoint Online 的授權。
- 具有 **Enterprise Mobility + Security (EMS) 訂用帳戶**或 **Azure Active Directory (Azure AD) Premium 訂用帳戶**，且使用者必須獲得 EMS 或 Azure AD 的授權。 如需詳細資訊，請參閱 [Enterprise Mobility 定價頁面](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing)或 [Azure Active Directory 定價頁面](https://azure.microsoft.com/pricing/details/active-directory/)。


  若要連接到所需的檔案，裝置必須：
-   已向 Intune **註冊**或已加入網域的電腦。

-   在 Azure Active Directory 中**註冊** (向 Intune 註冊裝置時即會自動進行此動作)。


-   **符合**任何已部署的 Intune 合規性原則。

裝置狀態儲存在 Azure Active Directory，它會根據您指定的條件，授與或禁止檔案的存取。

如不符合條件，使用者會在登入時看到下列其中一個訊息：

-   如果裝置未向 Intune 註冊，或未在 Azure Active Directory 中註冊，就會顯示一則訊息，指示如何安裝公司入口網站應用程式並註冊。

-   如果裝置不符合規範，就會顯示一則訊息，將使用者引導至 Intune 公司入口網站，讓他們找到問題的相關資訊與修復問題的方法。

**條件式存取不適用於外部共用**。 若要了解如何防止租用戶或站台集合中的外部共用，請參閱[為您的 SharePoint Online 環境管理外部共用](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)。

>[!NOTE]
>如果您啟用 SharePoint Online 的條件式存取，建議您停用清單上的網域，如 [Remove-SPOTenantSyncClientRestriction](https://technet.microsoft.com/library/dn917451.aspx) 主題中所述。  

## <a name="support-for-mobile-devices"></a>支援行動裝置
支援下列版本：
- iOS 8.0 和更新版本
- Android 4.0 和更新版本、Samsung Knox Standard 4.0 或更新版本
- Windows Phone 8.1 和更新版本

您可以在 **iOS** 和 **Android** 裝置從瀏覽器進行存取時，限制 SharePoint Online 的存取。 只允許從符合規範裝置上的支援瀏覽器存取︰
* Safari (iOS)
* Chrome (Android)
* Intune 受管理的瀏覽器 (iOS 以及 Android 5.0 和更新版本)

**不支援的瀏覽器則會遭到封鎖**。

## <a name="support-for-pcs"></a>對電腦的支援
支援下列版本：
- Windows 8.1 及更新版本 (已向 Intune 註冊電腦時)
- Windows 7.0、Windows 8.1 或 Windows 10 (電腦已加入網域時)
> [!NOTE]
>若要搭配使用條件式存取與 Windows 10 電腦，您必須使用 Windows 10 年度更新版來更新這些電腦。

  - 您必須將已加入網域的電腦設定為向 Azure Active Directory [自動註冊](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/)。 Intune 和 Office 365 客戶將會自動啟用 Azure AD 裝置註冊服務。 已部署 ADFS 裝置註冊服務的客戶將不會在內部部署 Active Directory 中看到已註冊的裝置。

  - 如果原則設為需要加入網域，而電腦未加入網域，則會顯示連絡 IT 系統管理員的訊息。

  - 如果原則設為需要加入網域或合規性，但電腦不符合任一需求，則會顯示一個訊息，指示如何安裝公司入口網站應用程式並註冊。
  >[!NOTE]
  >執行 Intune 電腦用戶端的電腦不支援條件式存取。

[必須啟用 Office 365 新式驗證](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)，並且具備所有最新的 Office 更新。

新式驗證將 Active Directory 驗證程式庫 (ADAL) 登入整合到 Office 2013 Windows 用戶端中，並啟用更佳的安全性，例如**多重要素驗證** 和**憑證式驗證**。


## <a name="configure-conditional-access-for-sharepoint-online"></a>設定 SharePoint Online 的條件式存取

### <a name="step-1-configure-active-directory-security-groups"></a>步驟 1：設定 Active Directory 安全性群組
在開始之前，請先為條件式存取原則設定 Azure Active Directory 安全性群組。 您可以在 **Office 365 系統管理中心**或 **Intune 帳戶入口網站**中設定這些群組。 您可以使用這些群組將使用者設為原則目標或者將他們從原則中豁免。 當使用者成為原則的目標時，他們使用的每個裝置都必須符合規範，才能存取資源。

您可以在 SharePoint Online 原則中指定兩種群組類型：

-   **目標群組**：包含套用原則的使用者群組。

-   **豁免群組**：包含豁免於原則的使用者群組。

如果使用者同時隸屬於這兩個群組，則將免套用原則。

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>步驟 2：設定及部署相容性原則
如果您尚未這麼做，請建立合規性原則，並將其部署到 SharePoint Online 原則的目標使用者。

> [!NOTE]
> 雖然合規性原則會部署到 Intune 群組，但條件式存取原則以 Azure Active Directory 安全性群組為目標。

如需如何設定合規性原則的詳細資料，請參閱[建立合規性原則](create-a-device-compliance-policy-in-microsoft-intune.md)。

> [!IMPORTANT]
> 如果您尚未部署合規性原則，則會將裝置視為符合規範。

當您就緒時，請繼續執行**步驟 3**。

### <a name="step-3-configure-the-sharepoint-online-policy"></a>步驟 3：設定 SharePoint Online 原則
接著，設定原則要求只有受管理和相容的裝置才可以存取 SharePoint Online。 這項原則會儲存在 Azure Active Directory。

#### <a name="bkmk_spopolicy"></a>

>[!NOTE]
> 您也可以在 Azure AD 管理主控台中建立 Intune 裝置的條件式存取原則 (此原則在 Azure AD 中稱為**裝置型條件式存取原則**)。 此外，您還可以建立其他條件式存取原則，例如多重要素驗證。 您也可以針對 Azure AD 所支援的協力廠商企業應用程式 (例如，Salesforce 和 Box)，設定條件式存取原則。 如需詳細資訊，請參閱[如何設定 Azure Active Directory 裝置型條件式存取原則來控制對 Azure Active Directory 連線應用程式的存取](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-policy-connected-applications/)。


1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com) 中，選擇 [原則]  >  [條件式存取]  >  [SharePoint Online 原則]。
![[SharePoint Online 原則] 頁面的螢幕擷取畫面](../media/mdm-ca-spo-policy-configuration.png)

2.  選取 [啟用 SharePoint Online 的條件式存取原則]。

3.  在 [應用程式存取] 下，您可以選擇將條件式存取原則套用至：

    -   **所有平台**

        用來存取 **SharePoint Online** 的任何裝置都必須在 Intune 中註冊並符合原則規範。 使用**新式驗證**的任何用戶端應用程式都必須遵守條件式存取原則。 如果 Intune 目前不支援此平台，則會禁止存取 **SharePoint Online**。

        選取 [所有平台] 選項表示不論用戶端應用程式所回報的平台為何，Azure Active Directory 都會將此原則套用至所有驗證要求。 所有平台都必須經過註冊並成為符合規範，除了︰
        *   必須註冊並符合規範的 Windows 裝置、使用內部部署 Active Directory 加入網域的 Windows 裝置，或兩者。
        * 不支援例如 Mac 的平台。 不過，使用來自這些平台之新式驗證的應用程式仍然會遭到封鎖。

    -   **特定平台**

         條件式存取原則會套用至在您指定的平台上使用新式驗證的任何用戶端應用程式。

     Windows 電腦必須已加入網域，或向 Intune 註冊並符合其規範。 您可以設定下列要求：

     -   **裝置必須已加入或與網域相容。** 選擇此選項時，會要求電腦必須已加入網域，或符合 Intune 中設定的原則。 如果電腦不符合上述任一需求，則會提示使用者向 Intune 註冊裝置。

     -   **裝置必須符合規範。** 選擇此選項時，會要求電腦必須在 Intune 中註冊且符合規範。 如果電腦未註冊，則會顯示註冊指示的訊息。

4.   在 SharePoint Online 和商務用 OneDrive 的 [瀏覽器存取] 下，您可以選擇只允許透過支援的瀏覽器存取 Exchange Online︰Safari (iOS) 以及 Chrome (Android)。 從其他瀏覽器存取則會遭到禁止。 您為 OneDrive 應用程式存取所選取的相同平台限制也適用於此處。

  在 **Android** 裝置上，使用者必須啟用瀏覽器存取。 若要這樣做，使用者必須在已註冊的裝置上，選擇 [啟用瀏覽器存取] 選項，如下所示︰
  1.    開啟**公司入口網站**應用程式。
  2.    從省略符號 (...) 或硬體功能表按鈕移至 [設定] 頁面。
  3.    按下 [允許瀏覽器存取] 按鈕。
  4.    在 Chrome 瀏覽器中，登出 Office 365 並重新啟動 Chrome。

  在 **iOS** 和 **Android** 平台上，若要識別用來存取服務的裝置，Azure Active Directory 會將傳輸層安全性 (TLS) 憑證核發給裝置。 裝置會顯示憑證，並提示使用者選取該憑證，如以下螢幕擷取畫面所示。 使用者必須選取此憑證，才可以使用瀏覽器。

  **iOS**

  ![iPad 上憑證提示的螢幕擷取畫面](../media/mdm-browser-ca-ios-cert-prompt.png)

  **Android**

  ![Android 裝置上憑證提示的螢幕擷取畫面](../media/mdm-browser-ca-android-cert-prompt.png)
5.  選擇 [目標群組] 下方的 [修改]，以選取要套用原則的 Azure Active Directory 安全性群組。 您可以選擇以所有使用者或僅一群特定的使用者為目標。

6.  選擇 [免套用的群組] 下方的 [修改]，選取免套用此原則的 Azure Active Directory 安全性群組。

7.  完成後，選擇 [儲存]。

您不需部署條件式存取原則，它會立即生效。

### <a name="step-4-monitor-the-compliance-and-conditional-access-policies"></a>步驟 4：監視相容性及條件式存取原則
在 [群組]  工作區中，您可以檢視裝置的狀態。

選取任何行動裝置群組。 然後在 [裝置] 索引標籤上，選擇下列其中一個 [篩選器]：

-   **沒有登錄 AAD 的裝置** 這些裝置受到封鎖而無法存取 SharePoint Online。

-   **不符合規範的裝置**。 這些裝置受到封鎖而無法存取 SharePoint Online。

-   **已登錄了 AAD 並符合規範的裝置**。 這些裝置可以存取 SharePoint Online。

### <a name="see-also"></a>請參閱
[使用 Microsoft Intune 限制電子郵件和 O365 服務的存取](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
