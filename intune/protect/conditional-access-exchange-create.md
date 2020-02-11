---
title: 建立 Exchange 條件式存取原則
titleSuffix: Microsoft Intune
description: 在 Intune 中，為 Exchange 內部部署及舊版 Exchange Online Dedicated 設定條件式存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/24/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d04897d38c1b46f27fe86e72ecfa6856aa9eece2
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755632"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>為 Exchange 內部部署及舊版 Exchange Online Dedicated 建立條件式存取原則

本文將示範如何根據裝置合規性來設定 Exchange 內部部署的條件式存取。

如果您有 Exchange Online Dedicated 環境，而且需要了解它是使用新版或舊版的設定，請連絡您的帳戶管理員。 若要控制對 Exchange 內部部署或舊版 Exchange Online Dedicated 環境的電子郵件存取，請在 Intune 中設定 Exchange 內部部署的條件式存取。

## <a name="before-you-begin"></a>開始之前

設定條件式存取之前，請確認下列設定存在：

- 您的 Exchange 版本為 **Exchange 2010 SP1 或更新版本**。 支援 Exchange 伺服器用戶端存取伺服器 (CAS) 陣列。

- 您已安裝並使用 [Exchange ActiveSync 內部部署 Exchange 連接器](exchange-connector-install.md)，可將 Intune 連線至內部部署 Exchange。

    >[!IMPORTANT]  
    >Intune 支援每個訂閱有多個內部部署 Exchange 連接器。  不過，每個內部部署 Exchange 連接器均專屬於單一 Intune 租用戶，無法與任何其他租用戶搭配使用。  如果您有多個內部部署 Exchange 組織，則可以為每個 Exchange 組織設定個別的連接器。

- 內部部署 Exchange 組織的連接器可以安裝在任何機器上，只要該機器能與 Exchange 伺服器通訊即可。

- 此連接器支援 **Exchange CAS 環境**。 Intune 支援將連接器直接安裝在 Exchange CAS 伺服器上。 因為連接器會對伺服器造成額外負載，所以建議將其安裝在另一部電腦上。 設定連接器時，您必須將它設定成可以與其中一部 Exchange CAS 伺服器通訊。

- 必須以憑證式驗證或使用者認證項目來設定 **Exchange ActiveSync**。

- 設定條件式存取原則並以使用者為目標後，使用者使用的**裝置**必須符合下列條件，他們才能連線到其電子郵件：
  - 已向 Intune **註冊**，或為加入網域的電腦。
  - 已在 **Azure Active Directory** 中註冊。 此外，必須向 Azure Active Directory 註冊用戶端 Exchange ActiveSync 識別碼。

- Intune 和 Office 365 客戶會自動啟用 Azure AD 裝置註冊服務 (DRS)。 已經部署 ADFS 裝置註冊服務的客戶，不會在其內部部署 Active Directory 中看到已註冊的裝置。 **這不適用於 Windows 電腦和 Windows Phone 裝置**。

- 「符合」  部署到該裝置的合規性原則。

- 若裝置不符合條件式存取設定，就會在使用者登入時，對使用者顯示下列其中一則訊息：
  - 如果裝置未向 Intune 註冊，或未在 Azure Active Directory 中註冊，就會顯示一則訊息，其中包含如何安裝公司入口網站應用程式、註冊裝置及啟動電子郵件的指示。 此程序也會將裝置的 Exchange ActiveSync 識別碼與 Azure Active Directory 中的裝置記錄相關聯。
  - 如果裝置不相容，即會顯示一則訊息來將使用者導向 Intune 公司入口網站或公司入口網站應用程式。 使用者可在公司入口網站中找到問題的相關資訊及其補救方式。

### <a name="support-for-mobile-devices"></a>支援行動裝置

- Windows Phone 8.1 和更新版本
- iOS 上的原生電子郵件應用程式。
- EAS 郵件用戶端 (例如 Android 4 或更新版本上的 Gmail)。
- EAS 郵件用戶端 **Android 工作設定檔裝置：** Android 工作設定檔裝置只支援**工作設定檔**中的 **Gmail** 和 **Nine Work for Android Enterprise**。 若要搭配 Android 工作設定檔使用條件式存取，除了必須部署 Gmail 或 Nine Work for Android Enterprise 應用程式的電子郵件設定檔之外，還必須將那些應用程式部署為必要安裝。

> [!NOTE]
> Android 與 iOS 版 Microsoft Outlook 不透過 Exchange 內部部署連接器支援。 若要利用 Azure Active Directory 條件式存取原則與 Intune 應用程式防護原則來保護您內部部署信箱的 iOS 與 Android 版 Outlook，請參閱[搭配 iOS 與 Android 版 Outlook 使用混合式現代化驗證](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) \(機器翻譯\)。

### <a name="support-for-pcs"></a>對電腦的支援

Windows 8.1 及更新版本上原生的**郵件**應用程式 (在使用 Intune 向 MDM 註冊時)

## <a name="configure-exchange-on-premises-access"></a>設定 Exchange 內部部署存取

在您可以使用下列程序來設定 Exchange 內部部署存取控制之前，您必須先為 Exchange 內部部署至少安裝並設定一個 [Intune 內部部署 Exchange 連接器](exchange-connector-install.md)。

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 移至 [租用戶系統管理]   > [Exchange 存取]  ，然後選取 [Exchange 內部部署存取]  。

3. 在 [Exchange 內部部署存取]  窗格中選擇 [是]  ，以 [啟用 Exchange 內部部署存取控制]  。

   > [!div class="mx-imgBorder"]
   > ![Exchange 內部部署存取畫面的範例螢幕擷取畫面](./media/conditional-access-exchange-create/exchange-on-premises-access.png)

4. 在 [指派]  底下，選擇 [選取要納入的群組]  ，然後選取一或多個群組來設定存取。

   已將適用於 Exchange 內部部署存取的條件式存取原則套用至您所選群組的成員。 接收到此原則的使用者必須先在 Intune 中註冊其裝置，並符合合規性設定檔的規範，才能存取 Exchange 內部部署。

   > [!div class="mx-imgBorder"]
   > ![選取要包含的群組](./media/conditional-access-exchange-create/select-groups.png)

5. 若要排除群組，請選擇 [選取要排除的群組]  ，然後選取無須註冊裝置及符合合規性設定檔規範然後才能存取 Exchange 內部部署的一或多個群組。

   選取 [儲存]  以儲存您的設定，然後返回 [Exchange 存取]  窗格。

6. 接下來，設定 Intune 內部部署 Exchange 連接器的設定。 在主控台中，選取 [租用戶系統管理]   > [Exchange 存取]  > [Exchange ActiveSync 內部部署連接器]  ，然後選取您要設定的 Exchange 組織連接器。

7. 針對 [使用者通知]  ，選取 [編輯]  以開啟 [編輯組織]  工作流程，您可以在其中修改「使用者通知」  訊息。

   > [!div class="mx-imgBorder"]
   > ![針對通知編輯組織工作流程的範例螢幕擷取畫面](./media/conditional-access-exchange-create/edit-organization-user-notification.png)

   修改傳送給使用者的預設電子郵件訊息，如果使用者的裝置不符合規範，且他們想要存取 Exchange 內部部署，就會收到此訊息。 訊息範本會使用標記語言。 您也可以在輸入時看到訊息外觀的預覽

   選取 [檢閱並儲存]  ，然後選取 [儲存]  來儲存您的編輯，以完成 Exchange 內部部署存取的設定。

   > [!TIP]
   > 若要深入了解標記語言，請參閱 Wikipedia 上的這篇[文章](https://en.wikipedia.org/wiki/Markup_language)。

8. 接下來，選取 [進階 Exchange ActiveSync 存取設定]  以開啟 [進階 Exchange ActiveSync 存取設定]  工作流程，您可以在其中設定裝置存取規則。

   > [!div class="mx-imgBorder"]
   > ![針對進階設定編輯組織工作流程的範例螢幕擷取畫面](./media/conditional-access-exchange-create/edit-organization-advanced-settings.png)

   - 針對 [非受控裝置存取]  ，為來自不受條件式存取或其他規則影響之裝置的存取，設定全域預設規則：

     - **允許存取**：所有裝置皆可立即存取 Exchange 內部部署。 如果擁有裝置的使用者屬於您在上一個程序中設定為包含的群組，則當裝置稍後被評估為不符合合規性政策的規範或未向 Intune 註冊時，即會予以封鎖。

     - **封鎖存取**和**隔離**：立即封鎖所有裝置存取 Exchange 內部部署。 如果擁有裝置的使用者屬於您在上一個程序中設定為包含的群組中，則在該裝置向 Intune 註冊且評估為符合規範之後，即可存取。

       「未」  執行 Samsung Knox Standard 的 Android 裝置不支援此設定，且一律會遭到封鎖。

   - 針對 [裝置平台例外]  選取 [新增]  ，然後視您的環境需要指定詳細資料。

      若將 [非受控裝置存取]  設定設為 [已封鎖]  ，即使已有封鎖它們的平台例外狀況，仍允許已註冊且符合規範的裝置。  

9. 選取 [確定]  以儲存您的編輯。

10. 選取 [檢閱並儲存]  ，然後選取 [儲存]  以儲存 Exchange 條件式存取原則。

## <a name="next-steps"></a>後續步驟

接下來，建立合規性政策，並將它指派給 Intune 的使用者以評估其行動裝置，請參閱[開始使用裝置合規性](device-compliance-get-started.md)。

[在 Microsoft Intune 中對 Intune 內部部署 Exchange 連接器進行疑難排解](https://support.microsoft.com/help/4471887)
