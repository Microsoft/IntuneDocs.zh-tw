---
title: "使用電子郵件設定檔存取公司電子郵件 | Microsoft Docs"
description: "電子郵件設定檔設定可用來設定行動裝置上，特定電子郵件用戶端的電子郵件存取設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 10f0cd61-e514-4e44-b13e-aeb85a8e53ae
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e0ecc775f70703574c4e1adf0f0aa204f2745b72
ms.openlocfilehash: 21eee53a4e3674dc28b01311a61dda0d71f9f7fa
ms.lasthandoff: 04/20/2017


---

# <a name="configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune"></a>使用電子郵件設定檔與 Microsoft Intune 來設定公司電子郵件存取權

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

許多行動平台包括隨附於作業系統的原生電子郵件用戶端。 其中部分用戶端可使用電子郵件設定檔加以設定，如本主題所述。

電子郵件設定檔設定可用來設定行動裝置上，特定電子郵件用戶端的電子郵件存取設定。 在支援的平台上，Microsoft Intune 可設定原生電子郵件用戶端，以讓使用者存取其個人裝置上的公司電子郵件，而不需任何額外設定。

如果您需要採取其他資料外洩防護的措施，請使用 [條件式存取](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)，這會控制任何電子郵件用戶端 (包括原生電子郵件用戶端) 的使用者信箱存取。

IT 系統管理員或使用者也可以選擇安裝替代的電子郵件用戶端 (例如 Microsoft Outlook for Android 或 iOS)。 這些電子郵件用戶端可能不支援電子郵件設定檔，並且不能使用 Intune 電子郵件設定檔進行設定。  

您可以使用電子郵件設定檔，在下列裝置類型上設定原生電子郵件用戶端：
-    Windows Phone 8.1 和更新版本
-    Windows 10 (適用於桌上型電腦)、Windows 10 Mobile 和更新版本
-    iOS 8.0 和更新版本
-    Samsung KNOX 標準 4.0 及更新版本
-    Android for Work (協力廠商電子郵件應用程式，原生的電子郵件應用程式僅限個人設定檔)

除了在裝置上設定電子郵件帳戶，您可以設定要同步處理的電子郵件數量，以及每種裝置類型所要同步處理的內容類型。

如果使用者在 Intune 設定設定檔前已經安裝電子郵件設定檔，Intune 電子郵件設定檔部署的結果取決於裝置平台：

**iOS**<br>依據主機名稱和電子郵件地址，偵測到重複的現有電子郵件設定檔。 使用者建立的重複電子郵件設定檔會封鎖 Intune 系統管理員所建立設定檔的部署作業。 這是常見的問題，因為 iOS 使用者通常會建立電子郵件設定檔，然後註冊。 公司入口網站會通知使用者這些檔案不相容，因為他們手動設定電子郵件設定檔，並提示使用者移除該設定檔。 使用者應該移除電子郵件設定檔，使 Intune 設定檔可以設定。 若要避免問題，請指示使用者先進行註冊，再安裝電子郵件設定檔，並允許 Intune 設定設定檔。

**Windows**<br>依據主機名稱和電子郵件地址，偵測到重複的現有電子郵件設定檔。 Intune 會覆寫使用者建立的現有電子郵件設定檔。

**Samsung KNOX**<br>依據電子郵件地址，偵測到重複的現有電子郵件設定檔，且會以 Intune 設定檔覆寫它。 如果使用者設定了該帳戶，Intune 設定檔會再次將其覆寫。 請注意，這可能導致使用者產生一些混淆。

由於 Samsung KNOX 不會使用主機名稱來識別設定檔，因此建議您不要建立多個電子郵件設定檔來使用在不同主機上的同一個電子郵件地址，以避免彼此覆寫。

**Android for Work**<br>Intune 提供兩個 Android for Work 電子郵件設定檔，分別用於 Gmail 和 Nine Work 電子郵件應用程式。 這些應用程式都是在 Google Play 商店取得，並且安裝在裝置工作設定檔中，因此不會產生重複的設定檔。 兩個應用程式都支援連線到 Exchange。 若要啟用電子郵件連線功能，請將其中一個電子郵件應用程式部署到使用者的裝置後，再建立及部署適當的電子郵件設定檔。 Nine Work 之類的電子郵件應用程式可能不是免費的。 請檢閱應用程式的授權詳細資料，如有任何問題，請連絡應用程式公司。

## <a name="secure-email-profiles"></a>保護電子郵件設定檔
您可以使用憑證或密碼保護電子郵件設定檔。

### <a name="certificates"></a>憑證
當您建立電子郵件設定檔時，請選擇先前在 Intune 中建立的憑證設定檔。 這稱為識別憑證，用來針對允許使用者裝置連線的受信任憑證設定檔 (或根憑證) 進行驗證。 受信任的憑證會部署到可驗證電子郵件連線的電腦 (一般是原生郵件伺服器)。

如需如何建立和使用 Intune 中憑證設定檔的詳細資訊，請參閱[使用憑證設定檔保護資源存取](secure-resource-access-with-certificate-profiles.md)。

### <a name="user-name-and-password"></a>使用者名稱和密碼
使用者藉由提供使用者名稱和密碼向原生郵件伺服器進行驗證。

密碼不會包含在電子郵件設定檔中，因此使用者需要在連線至電子郵件時提供。

### <a name="create-an-email-profile"></a>建立電子郵件設定檔

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 **[原則]** &gt; **[新增原則]**。

2.  設定下列其中一種原則類型：

    -   **Samsung KNOX Standard (4.0 及更新版本) 的電子郵件設定檔**

    -   **電子郵件設定檔 (iOS 8.0 及更新版本)**

    -   **電子郵件設定檔 (Windows Phone 8.1 及更新版本)**

    -   **電子郵件設定檔 (Windows 10 Desktop/行動裝置版及更新版本)**

    -   **電子郵件設定檔 (Android for Work - Gmail)**

    -    **電子郵件設定檔 (Android for Work - Nine Work)**

    您只能建立和部署自訂電子郵件設定檔原則。 沒有建議的設定。

3.  使用下表協助您建立電子郵件設定檔設定：

|設定名稱 | 詳細資訊|
| ----------- | --------------- |
    |**Name**|電子郵件設定檔的唯一名稱。|
    |**說明**|可協助您識別此設定檔的描述。|
    |**主機**|您公司伺服器的主機名稱，用來裝載原生電子郵件服務。|
    |**帳戶名稱**|在使用者裝置上向使用者顯示的電子郵件帳戶顯示名稱。|
    |**使用者名稱**|Active Directory (AD) 或 Azure AD 中的這個屬性，將會用來產生此電子郵件設定檔的使用者名稱。 選取主要 SMTP 位址，例如 *user1@contoso.com* 或使用者主體名稱，例如 *user1* 或 *user1@contoso.com*。|
    |**電子郵件地址**|每個裝置上使用者的電子郵件地址的產生方式。 選取 [主要 SMTP 位址]，使用主要 SMTP 位址以登入 Exchange；或使用 [使用者主體名稱]，將完整主體名稱作為電子郵件地址。|
    |**驗證方法** (Android for Work、Samsung KNOX 和 iOS)|選取 [使用者名稱和密碼] 或 [憑證] 作為電子郵件設定檔所使用的驗證方法。|
    |**選取用戶端憑證以進行用戶端驗證 (識別憑證)** (Android for Work、Samsung KNOX 和 iOS)|選取先前建立的用戶端 SCEP 憑證，以用來驗證 Exchange 連線。 如需如何使用 Intune 中憑證設定檔的詳細資訊，請參閱[使用憑證設定檔保護資源存取](secure-resource-access-with-certificate-profiles.md)。 只有在驗證方法是 [憑證] 時，才會顯示此選項。|
    |**使用 S/MIME** (Samsung KNOX 和 iOS)|使用 S/MIME 簽署傳送外寄電子郵件。|
    |**簽署憑證** (Samsung KNOX 和 iOS)|選取將用來簽署外寄電子郵件的簽署憑證。 只有在選取 [Use S/MIME (使用 S/MIME)] 時，才會顯示此選項。|
    |**同步電子郵件的間隔天數**|您想要同步處理電子郵件的天數，或選取 [無限制] 同步處理所有可用的電子郵件。|
    |**同步排程** (Android for Work、Samsung KNOX、Windows Phone 8 和更新版本、Windows 10)|選取裝置用來同步處理 Exchange Server 中資料的排程。 您也可以選取 [郵件送達時] 以在資料到達時立即同步處理資料，或 [手動 (使用此方式，裝置使用者必須啟動同步處理)]。|
    |**使用 SSL**|傳送電子郵件、接收電子郵件以及與 Exchange Server 進行通訊時，請使用 Secure Sockets Layer (SSL) 通訊。 對於執行 Samsung KNOX 4.0 或更新版本的裝置，您必須匯出 Exchange Server 的 SSL 憑證，並在 Intune 中將其部署為 Android 信任的憑證設定檔。 Intune 不支援存取此憑證 (若此憑證以其他方法安裝到 Exchange Server 上)。|
    |**要同步處理的內容類型** (Android for Work Gmail 以外的所有平台)|選取您想要與裝置同步處理的內容類型。|
    |**允許從協力廠商應用程式傳送電子郵件** (僅限 iOS)|允許使用者選取此設定檔作為預設的帳戶來傳送電子郵件，以及允許在原生電子郵件應用程式中開啟協力廠商應用程式以開啟電子郵件，例如，將檔案附加至電子郵件。|

> [!IMPORTANT]
>
> 如果您已部署電子郵件設定檔，然後想要變更 [主機] 或 [電子郵件地址] 的值，則必須刪除現有電子郵件設定檔，並使用必要值建立新的電子郵件設定檔。

4.  完成之後，請按一下 [儲存原則] 。

新的原則會顯示在 [原則]  工作區的 [設定原則]  節點中。

## <a name="deploy-the-policy"></a>部署原則

1.  在 [原則] 工作區中，選取您要部署的原則，然後選擇 [管理部署]。

2.  在 [管理部署]  對話方塊中：

    -   **部署原則** - 選取您要部署原則的一或多個群組，然後選擇 [新增] &gt; [確定]。

    -   **若要關閉對話方塊但不加以部署** - 選擇 [取消]。

在 [原則]  工作區的 [概觀]  頁面上，狀態摘要和警示可識別需要注意的原則問題。 此外，狀態摘要還會顯示在 [儀表板] 工作區中。

> [!NOTE]
> - 對於 Android for Work，除了適當的電子郵件設定檔之外，也必須部署 Gmail 或 Nine Work 應用程式。
> - 若想要從裝置移除電子郵件設定檔，請編輯部署，再移除裝置所屬的群組。 請注意，若該電子郵件設定檔是裝置上唯一的電子郵件設定檔，即無法以此方式移除。
> - 如果您變更之前部署的電子郵件設定檔，使用者可能會看到要求核准其電子郵件設定重新設定的訊息。

