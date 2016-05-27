---
# required metadata

title: 常見問題 | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a8126cca-9ec4-454b-a20b-dc1bb6797327

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Intune 常見問題
本文回答 Intune 的一些常見問題。 如果您在這裡看不到您問題的解答，請[告訴我們](https://microsoftintune.uservoice.com/)

## 一般問題

-   **我要如何知道 Intune 服務已更新？**

    於 manage.microsoft.com 登入您的帳戶。 在 [系統管理概觀] 中，選擇 [檢視服務狀態]。 租用戶位置與維護排程會列於該處。 閱讀[新功能](/intune/deploy-use/whats-new-in-microsoft-intune)文章中的服務更新。

-   **如果使用者重新命名了公司入口網站應用程式內的裝置，則在 Intune 或 Configuration Manager 中該名稱會變更嗎？**

    不會，變更該名稱只是為了使用者方便使用而已。

-   **行動裝置的 Intune 有遠端協助功能嗎？**

    否，沒有。 [Bomgar](http://www.bomgar.com/) 和 [TeamViewer](https://www.teamviewer.com/) 這類協力廠商應用程式可能有所助益。

## 帳戶

-   **如果我開始評估 Intune，且建立新的租用戶進行試用，可以使用相同的租用戶將 Office 365 加入評估嗎？**

    是。 只要從現有 Intune 租用戶/訂閱使用全域管理員登入即可 (例如 globaladmin@&lt;公司&gt;.onmicrosoft.com)

-   **如果我在試用版訂閱期間將 MDM 授權單位指派到 Intune，若我對 Intune 的想法有所改變，會不會讓我在換到另一家公司的服務時變得很困難？**

    雖然很難想像您不會繼續使用 Intune，但 MDM 授權單位的選擇並不會影響您移到其他服務。 特別是選擇 Intune 或具備 System Center Configuration Manager 的 Intune。

-   **我可以為之後的 Intune 帳戶使用現有的 Office 365 網域名稱嗎？**

    是，如果登入所用的組織識別碼與您現有的 Office 365 租用戶相關聯，且在建立 Intune 試用版或啟用授權時已驗證過網域。

    Intune 之後就會使用與您 Office 365 帳戶相同的網域/使用者等等。 請注意，必須要使用 Intune 授權將每位 Office 365 使用者啟用為 Intune 使用者。 此項作業必須要由管理租用戶的全域管理員執行。

## 註冊

-   **我的使用者要於何處了解如何註冊其裝置？**

    您可以使用 [IT 系統管理員的使用者 Intune 註冊指示](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a)的資訊，或從此處自訂資訊。

-   **要如何疑難排解裝置註冊？**

    [Intune 的裝置註冊疑難排解](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune)中提供常見註冊問題的疑難排解方法

-   **如果使用者有註冊問題，我該如何收集註冊記錄檔？**

    請遵循[這些指示](http://www.microsoft.com/en-us/download/46391)。

## 行動裝置管理

-   **一般 MDM**

    -   **Intune 可以偵測到裝置是否被破解了嗎？**

        是，有些作業系統可以。 如需如何管理經過破解之裝置的資訊，請參閱[建立裝置相容性原則](/intune/deploy-use/create-a-device-compliance-policy-in-microsoft-intune.md)。

    -   **我可以從裝置選擇性地清除公司資料嗎？**

        是。 如需選擇性抹除的資訊，請參閱[透過遠端抹除、遠端鎖定或密碼重設來協助保護您的資料](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune.md)。

    -   **是否有任何方法可透過 Intune 在行動裝置瀏覽器上封鎖特定的網站？**

        在任何平台的原生瀏覽器上都不能。 但當您在 iOS 及 Android 裝置上部署受 Intune 管理的網頁瀏覽器之後，就能允許或封鎖 URL。 如需詳細資訊，請參閱[使用受管理的瀏覽器原則管理網際網路存取](/intune/Deploy-Use/Manage-Internet-access-using-managed-browser-policies-with-Microsoft-Intune.md)。

    -   **我們可以限制使用者無法解除安裝應用程式嗎？**

        一般而言，不可以。 但在受監督的 iOS 裝置上，您可以讓使用者無法解除安裝使用 Apple Configurator 所散發的應用程式。 

    -   **有方法可以管理行動資料使用量嗎？**

        無法直接管理，但可以將 Wi-Fi 設定檔推送到裝置 (如[使用 Wi-Fi 設定檔，協助使用者連線到公司網路](/intune/Deploy-Use/wi-fi-connections-in-microsoft-intune.md)中所述)，確保將 Wi-Fi 設為慣用的連線方式。 此外，某些平台 (例如 iOS 與 Android KNOX) 會啟用控制設定的能力，例如控制語音及數據漫遊。

    -   **有方法可以讓使用者無法取消註冊裝置嗎？ 如果是公司所擁有的裝置呢？**

        一般來說，不行。 但可使用自訂的 Windows Phone 設定，防止使用者在 Windows Phone 8.1 上進行取消註冊。 同時，對於在 Apple 裝置註冊方案 (DEP) 中所監督及註冊的 iOS 裝置而言，可以讓使用者無法取消註冊裝置。

    -   **我可以切換所選的 MDM 授權單位嗎？**

        在某些情況下，您可以切換 MDM 授權單位。 若要這樣做，請依[如何取得 Microsoft Intune 支援](/intune/Troubleshoot/How-to-get-support-for-Microsoft-Intune.md)所述連絡支援人員。 下表描述可能有的變更。 MDM 授權單位若有任何變更，即需重新註冊裝置。

        變更為： Intune!變更為： O365|變更為：具備 Intune 的 Configuration Manager|
        
        從：Intune| |是&#42;|是|



-   **從：O365||是&#42;||是|**

    -   **從：具備 Intune 的 Configuration Manager|是|是| |**

        &#42;O365 與 Intune MDM 授權單位可以共存，因此您不需要重新註冊行動裝置。 Windows 我可以側載 Windows 市集應用程式嗎？

    -   **公開上市的應用程式無法側載。**

        雖然您可以下載 XAP，但無法將其上傳至 Intune，因為其為公用 XAP，已經過開發人員的程式碼簽署憑證進行加密及簽署。 只可側載您開發且經過您自己程式碼簽署憑證所簽署的應用程式。

    -   **透過公司入口網站所散發的 Windows Phone 市集應用程式，需要使用者擁有 Microsoft 帳戶嗎？**

        是，沒有 Microsoft 帳戶的話，使用者無法取得應用程式。 但側載的私人 LOB 應用程式是例外，其無需 Microsoft 帳戶即可部署到裝置。

        **Windows Phone 8.1 上需要 Microsoft 帳戶才可由 Intune 管理嗎？**
        不會。 但安裝公用市集的大部分應用程式，都需要 Microsoft 帳戶。 Windows Phone 為什麼需要 Symantec 需要憑證才能進行管理？ Windows Phone 控制您安裝應用程式的方式。 任何具有 Microsoft 帳戶的使用者都可以安裝 Windows Phone 市集中的應用程式，而公司可使用 Windows Phone 文件中所述的特殊程序，安裝或側載其內部開發的企業營運 (LOB) 應用程式。

        安裝 LOB 應用程式時，Windows Phone 只會信任 Symantec 所發行的一種特殊類型憑證。 您無法使用任何其他商業或非公開產生的憑證。 所有行動裝置管理解決方案都必須符合這項需求，而不只有 Intune。 Symantec 憑證會建立應用程式註冊語彙基元 (AET)。 AET 可以在裝置註冊行動裝置管理時安裝在裝置上，也可在之後從安全的網站或電子郵件附件安裝。 系統管理員必須使用 [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=268439)所提供的工具，使用 Symantec 憑證簽署每一個 LOB 應用程式。 當使用者嘗試安裝 LOB 應用程式時，Windows Phone 作業系統會比對應用程式上與 AET 中的簽章。

        -   若簽章相符，就可以執行安裝。

        -   若無法驗證 AET，安裝便會失敗。

        -   下列有幾項原因可能造成 AET 無法驗證：

        裝置上從未安裝過 AET

    **AET 已過期**
  AET 不是使用簽署應用程式所使用的 Symantec 憑證所建立 在 MDM 註冊期間，Windows Phone 不需要有 AET，但在 2014 年 11 月之前的版本中，因為除了註冊期間之外，沒有其他方法可以安裝 AET 及 ssp.xap，所以 Intune 會需要 AET 及經過簽署的 ssp.xap。

      > 如何為 Intune 使用者建立 AET？

    **當系統管理員上傳其 Symantec 憑證的.pfx 檔案時，Intune 會自動建立 AET，並將其部署到已經註冊 Windows Phone 上。**
       Intune 系統管理員不需要使用 Windows Phone SDK 中的 AET 產生器工具。

       -   Intune 不支援在安裝之後手動建立及部署 AET。 對於降低 Symantec 憑證需求做了哪些變更？

        -   對於 2014 年 11 月的版本，Intune 做了一些變更，方便沒有 Symantec 憑證的公司進行安裝。 Windows Phone 8.1 的公司入口網站可以從市集安裝，因此不需要以 Symantec 憑證簽署並與 AET 核對驗證。 應用程式會改成在市集發行期間進行驗證。

        Windows Phone 8.1 裝置註冊時，手機上可有 AET，也可以沒有 AET。 如有 AET，將會在裝置第一次與 Intune 同步時加以安裝。

        **若沒有 AET，裝置仍可由 Intune 管理，而使用者也可以從市集安裝公司入口網站，並使用公司入口網站絕大部分的功能，但無使用 Symantec 憑證簽署應用程式。**
        Windows Phone 8 裝置的 Symantec 需求仍維持不變。

        -   Windows Phone 8 裝置在註冊期間必須有經過簽署的 ssp.xap 及 AET，否則將無法註冊。

        -   完成註冊的 Windows Phone 8.1 裝置若沒有 Symantec 憑證，可支援哪些功能？

        -   完成註冊的 Windows Phone 8.1 裝置若沒有 Symantec 憑證，您可以：

        -   建立原則，並將其推送到裝置

        -   設定要顯示在公司入口網站中的 IT 部門連絡資訊

        建立市集的深層連結，並將其部署到公司入口網站

        > [!IMPORTANT]
        > 建立網頁的連結，並將其部署到公司入口網站 建立條款與條件；使用者必須接受，才可使用公司入口網站

        **沒有 Symantec 憑證唯一無法執行的動作是部署 LOB 應用程式。**
        Intune 軟體發行者不會在您上傳應用程式時，驗證其是否經過簽署。 若您部署未經簽署的應用程式，使用者會在嘗試安裝遭遇失敗。 當使用者只有公司入口網站而沒有 Symantec 憑證時，該怎麼辦？

        使用者若未從市集安裝公司入口網站，便無須註冊 Windows Phone 8.1 裝置。

        -   對於未註冊的裝置，使用者會收到提示要求註冊。 使用者只要點一下公司入口網站中的提示，就可直接進入 [設定]/[工作場所] 註冊其裝置。

        -   即使未註冊裝置，使用者也可使用從市集安裝的公司入口網站執行下列動作：

        -   接受或拒絕系統管理員所設定的任何條款和條件。

        -   若使用者拒絕了條款與條件，公司入口網站會隨即關閉。

        -   檢視 IT 部門的連絡資訊

        檢視任何完成註冊的裝置，包括 iOS、 Android 及 Windows 裝置 使用市集中應用程式的深層連結 使用網頁連結開啟網頁 使用者可以利用完成註冊的裝置，檢視 我的裝置 清單中的裝置。

        裝置一經註冊之後，就必須接受所部署之任何 Intune 原則的規範。

        **裝置必須註冊，才能取得 AET 並安裝 LOB 應用程式。 任何未經註冊的裝置若要嘗試安裝 LOB 應用程式，將會被導向註冊。**
        若使用者的公司沒有 Symantec 憑證，其唯一無法執行的工作便是安裝系統管理員所部署的 LOB 應用程式。 我們公司已有一份憑證，並已經註冊 Windows Phone 8.1 裝置。

        **對於市集目前所提供的公司入口網站，我需要採取任何不同的動作嗎？**
        Windows Phone 8.1 裝置目前仍可從下載中心取得最新的 ssp.xap。

        -   您可以繼續將使用者導向註冊，並在安裝期間取得公司入口網站。

        -   使用者從市集取得公司入口網站各有哪些優缺點？

        -   優點：

        -   即使未註冊 Windows Phone 8.1 裝置，使用者仍可取得深層連結及網頁連結

        當 Microsoft 更新公司入口網站時，您無須下載、簽署及重新部署 ssp.xap，市集應用程式便會自動更新

        -   Windows Phone 8.1、iOS、Android 及 Windows 使用者的文件一律須「前往市集並安裝公司入口網站」。

        -   使用者在安裝時就可看到應用程式，並會在應用程式開啟時取得註冊指示

        缺點：

        -   使用者會看到安裝公司應用程式中心的核取方塊，但不會將他們導向裝置應用程式清單中的公司入口網站

        -   在使用者開啟公司入口網站之前，無須接受自訂的條款與條件

        -   在下列情況下，您可以繼續將使用者導向註冊，並在註冊期間安裝 ssp.xap：

        **若公司封鎖使用者 Windows Phone 存取市集，使用者必須在註冊期間安裝 ssp.xap。**

        -   若使用者的 Windows Phone 上未設定 Microsoft 帳戶，將無法從市集安裝公司入口網站。

        -   若現有的 Windows Phone 註冊文件告訴他們先前往 [設定] / [工作場所]，可能需要一些時間來更新文件，將使用者導向市集。

        -   下載中心上的 ssp.xap 與市集中的應用程式有何不同？

        **市集中的公司入口網站無須經由 Symantec 憑證簽署就能安裝**
        市集中的公司入口網站會對使用者顯示條款與條件，但下載中心的 ssp.xap 不會 市集中的公司入口網站是 .appx 而不是 .xap

        -   我可以在取得公司入口網站檔案之後，直接將其推送給我的使用者，而不要傳送到市集嗎？

        -   是。

        -   您可以從下載中心下載適用於下列作業系統的公司入口網站應用程式：

        **Windows Phone 8.1： [http://go.microsoft.com/fwlink/?LinkId=615799](http://go.microsoft.com/fwlink/?LinkId=615799)**
        Windows Phone 8.0： [http://go.microsoft.com/fwlink/?LinkId=268440](http://go.microsoft.com/fwlink/?LinkId=268440) Windows 8.1： [http://go.microsoft.com/fwlink/?LinkId=615800](http://go.microsoft.com/fwlink/?LinkId=615800) 若公司沒有 Symantec 憑證，是否仍可使用 Windows Phone 的 Windows Intune 試用版管理支援工具？此外是否仍可讓使用者從市集安裝公司入口網站？

        是。

        > [!IMPORTANT]
        > 若您必須執行包含的 LOB 應用程式安裝的概念證明，試用版管理工具可用於市集版的公司入口網站。 因為註冊 Windows Phone 8.1 裝置已不再需要 Symantec 憑證的 AET，但公司仍可使用市集中的應用程式深層連結來測試應用程式安裝。

        **Windows Phon 的 Windows Intune 試用版管理支援工具僅適用於 Intune 的試用訂閱。**
        只使用試用版管理工具進行測試。 當無法再使用試用版管理工具的 Symantec 憑證，或當公司取得自己的 Symantec 憑證來簽署應用程式時，從試用版管理工具以 AET 註冊的裝置，必須先取消註冊再重新註冊。 公司開始時沒有 Symantec 憑證，可以在 Windows Phone 8.1 註冊之後再增加嗎？ 是。 即使 Windows Phone 8.1 裝置已經註冊，您也可以取得 Symantec 憑證來簽署 ssp.xap，並上傳其和 pfx 檔案。


-   **Intune 會隨後產生 AET。**

    -   **Windows Phone 8.1 裝置會在下次同步 (最多八小時) 時取得 AET。**

        上傳 xap 及 pfx 之後，請至少等候八小時的時間，再部署企業營運應用程式。

-   **Android**

    -   **加密 Android 裝置需要多長的時間？**

        時間長短主要取決於裝置處理器的速度，以及記憶體總數和已使用的記憶體數，而非 Intune 的功能。 iOS

    -   **透過 Intune 部署 iOS 應用程式時，如果已上傳應用程式的 IPA 與資訊清單檔案，則裝置需要指定 AppleID 才可繼續安裝嗎？**

        不會。 當 Intune 提供位元 (IPA 已上傳至 Intune) 時，會側載該應用程式且不需要 Apple ID。

    -   **有方法可以無須允許存取 Apple Store 而在 iOS 上啟用應用程式的安裝嗎？**

        沒有。但您可以啟用應用程式市集，並在 iOS 上使用允許及封鎖的應用程式，以隨時掌握使用者的動態。

    -   **側載的 LOB 應用程式不需要存取 Apple APP Store。**

        透過公司入口網站散發的 Apple Store 應用程式，會需要使用者具有 iTunes 帳戶嗎？ 會。沒有 iTunes 帳戶的使用者無法取得應用程式。

## 我可以封鎖 App Store 嗎？

-   **是的，您可以。但如此將會封鎖從 App Store 安裝及更新所有應用程式，而不只是由使用者所起始的安裝及更新。**

    這表示您從 Intune 部署的所有公用應用程式市集應用程式也會失敗。

-   **應用程式部署**

    我要如何新增建議的應用程式？ 在 Intune 中，這些稱為「熱門應用程式」，並記錄於[在 Microsoft Intune 中部署應用程式](/Intune/Deploy-Use/deploy-apps-in-microsoft-intune.md)。

## 我可以為我想要部署的應用程式取得額外的雲端儲存空間嗎？

-   **是。**

    相關內容位於[部署應用程式](/Intune/Deploy-Use/deploy-apps.md)中的＜雲端儲存體需求＞一節。 安全性 Intune 可強制進行 BitLocker 嗎？

-   **Windows 8.1/RT 中的 OMA-DM 代理程式允許您讀取 (取得) 加密狀態。**

    您無法設定它。 這對於 Intune 與其他行動裝置管理服務而言為 True。 如果使用 BitLocker 加密 Windows 8 平板電腦，若使用者連續數次登入失敗，我可以強制執行完整的裝置清除嗎？

## 在 Windows 8.1/RT 裝置上，對於任何行動裝置管理服務而言 (包括 Intune)，沒有完整清除的選項。

-   **Intune 為這些裝置提供選擇性清除。**

    如需 Intune 抹除/選擇性抹除的詳細資訊，請參閱[使用 Microsoft Intune 保護應用程式和資料](/intune/Deploy-Use/protect-apps-and-data-with-microsoft-intune.md)。 公司入口網站

## 我可以自訂我的公司入口網站嗎？

-   **是。**

    在 Intune 管理主控台中，移至 [管理]&gt;[公司入口網站] 進行這些設定。 Microsoft Intune 與 Configuration Manager

-   **當我使用 Configuration Manager 與 Intune 時，應在何處管理我的裝置？**

    雖然安裝有 Intune 代理程式的裝置會顯示在 Intune 主控台中，但您仍應從 Configuration Manager 主控台管理您的所有裝置。 行動裝置不會出現在 Intune 主控台中。

-   **可以在裝置上進行選擇性清除？**

    若您是使用 System Center 2012 R2 Configuration Manager 或更新版本與 Intune，可執行選擇性抹除作業將公司資料移除。 如需詳細資訊，請參閱[使用 Microsoft Intune 保護應用程式和資料](/intune/Deploy-Use/protect-apps-and-data-with-microsoft-intune.md)。



<!--HONumber=May16_HO2-->


