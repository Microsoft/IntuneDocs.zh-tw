---
title: 在 Microsoft Intune 中使用 iOS 版 Outlook 設定 S/MIME
description: 了解 Microsoft Intune 中 iOS 版 Outlook 的 S/MIME。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lance
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c9572f4accb1be232d4667d99b98beff90d81379
ms.sourcegitcommit: edd06a494a241d198ca9b0d3030c92195976e0d3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000409"
---
# <a name="configure-smime-with-outlook-for-ios"></a>使用 iOS 版 Outlook 設定 S/MIME

安全/多用途網際網路郵件延伸標準 (S/MIME) 為傳送至和來自 Exchange ActiveSync (EAS) 帳戶的電子郵件，提供額外一層安全性。 [Microsoft Outlook](https://aka.ms/omsmime) 可以利用 S/MIME，讓使用者能夠加密外寄訊息和附件，確保只有預期的收件者可以在使用 Office 365 帳戶時，讀取和存取訊息內容。 使用者也可以數位簽署訊息，這可讓收件者驗證傳送者的身分識別，並確認訊息未遭到竄改。 利用憑證可以做到此功能。 如需詳細資訊，請參閱[了解 S/MIME](https://docs.microsoft.com/previous-versions/tn-archive/aa995740(v=exchg.65)?redirectedfrom=MSDN) \(英文\)。

> [!NOTE]
> 此功能已延後，但即將發行。

> [!NOTE]
> 此主題描述如何透過 [Microsoft 端點管理員](https://go.microsoft.com/fwlink/?linkid=2109431)部署受信任的根憑證。 Microsoft 端點管理員是單一的整合式端點管理平台，可管理您的所有端點。 此 Microsoft 端點管理員系統管理中心整合 ConfigMgr 和 Microsoft Intune。

## <a name="about-message-encryption"></a>關於訊息加密
使用者可以將加密訊息傳送給組織中的人員，以及其組織外部的人員 (如果他們有加密憑證的公開部分)。 與加密憑證相關聯的私密金鑰應一律受加密訊息的收件者保護。 加密憑證的私密金鑰是由收件者用來將訊息解密。

只有擁有與加密訊息所使用憑證相對應憑證的收件者，才能讀取加密訊息。 如果您嘗試將加密訊息傳送給無法使用加密憑證的收件者，則應用程式會在傳送電子郵件之前，提示您移除這些收件者。

## <a name="about-digital-signatures"></a>關於數位簽章
數位簽署訊息可為收件者保證訊息未遭到竄改，而且傳送者的身分識別是真實的。 只有當收件者使用的電子郵件用戶端支援 S/MIME 時，收件者才能驗證數位簽章。

## <a name="prerequisites"></a>必要條件
- iOS 版 Outlook 僅在 Office 365 帳戶上支援 S/MIME。
- 必須為 Office 365 設定 S/MIME。 如需詳細資訊，請參閱[如何在 Office 365 中設定 S/MIME](https://techcommunity.microsoft.com/t5/Exchange-Team-Blog/How-to-Configure-S-MIME-in-Office-365/ba-p/584516) \(英文\)。
- 您必須有可以核發憑證 (可以用於簽署和加密) 的憑證授權單位。
- 透過端點管理員部署受信任的根憑證。 如需詳細資訊，請參閱[建立受信任的憑證設定檔](~/protect/certificates-configure.md#create-trusted-certificate-profiles)。
- 加密憑證必須匯入到端點管理員中。 如需詳細資訊，請參閱[透過 Intune 設定並使用匯入的 PKCS 憑證](~/protect/certificates-imported-pfx-configure.md)。
- 為 Microsoft Intune 安裝並設定 PFX 連接器。 如需詳細資訊，請參閱[為 Microsoft Intune 下載、安裝並設定 PFX 憑證連接器](~/protect/certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune)。
- 裝置必須已註冊 MDM，才能從端點管理員自動接收受信任的根憑證和 S/MIME 憑證。

> [!IMPORTANT]
> 您必須下載並安裝已更新的 PFX 連接器 (6.1911.11.0 版或更新版本)，以供 Microsoft Intune 使用 S/MIME 加密憑證搭配 iOS 版 Outlook。

## <a name="smime-support-in-outlook-for-ios"></a>iOS 版 Outlook 中的 S/MIME 支援
iOS 版 Outlook 支援使用憑證對訊息進行 S/MIME 簽署和加密。 許多客戶都有個別的簽署和加密憑證，而不是支援簽署和加密的單一憑證。 簽署憑證在個別使用者的已註冊裝置之間通常是唯一的，而加密憑證會在個別使用者的已註冊裝置之間共用。 通常，使用者會使用 S/MIME 數年，而且隨著憑證更新，使用不同的加密憑證。 加密憑證歷程記錄 (包括其私密金鑰) 必須存在於使用者的裝置上，如此一來，就能讀取在過去可能已使用那些憑證 (其中任一個) 加密的電子郵件。 也可以擁有支援簽署和加密的單一憑證。

iOS 版 Outlook 支援兩種方式將憑證傳遞至裝置，使它們可用於 S/MIME：

- **使用者**可以使用電子郵件傳送 S/MIME 憑證給自己，並在其行動裝置上的 iOS 版 Outlook 中，從附件安裝憑證。
- **系統管理員**可以從任何憑證授權單位將加密憑證歷程記錄匯入端點管理員。 端點管理員接著會將那些憑證自動傳遞給使用者註冊的任何裝置。 一般來說，簡單憑證註冊通訊協定 (SCEP) 是用於簽署憑證。 若使用 SCEP，系統會產生私密金鑰並儲存在已註冊裝置上，且會將唯一的憑證傳遞給該使用者所註冊的每個裝置，以用於建立不可否認性。 系統管理員將其使用者的加密憑證歷程記錄匯入到端點管理員，然後系統會將所有使用者的加密憑證傳遞給他們註冊的任何裝置。 最後，針對需要 NIST 800-157 標準支援的客戶，端點管理員支援衍生認證。 在 iOS 上，公司入口網站是用來從 Intune 擷取簽署和加密憑證。

## <a name="configuring-outlook-for-ios-smime-in-endpoint-manager"></a>在端點管理員中設定 iOS 版 Outlook S/MIME
若要在端點管理員中設定 iOS 版 Outlook S/MIME (包括自動傳遞 iOS 版 Outlook 可以使用的 S/MIME 憑證)，請使用下列步驟：

### <a name="add-the-microsoft-outlook-app"></a>新增 Microsoft Outlook 應用程式
1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 將來自 App Store 的 Microsoft iOS 版 Outlook 應用程式新增至端點管理員，或從 Apple 大量採購方案同步處理 iOS 版 Outlook。 如需詳細資訊，請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](~/apps/store-apps-ios.md) 或[如何使用 Microsoft Intune 管理透過 Apple 大量採購方案購買的 iOS 和 macOS 應用程式](~/apps/vpp-apps-ios.md)。

### <a name="create-the-outlook-for-ios-smime-configuration-policy"></a>建立 iOS 版 Outlook S/MIME 設定原則

下列步驟可讓您在端點管理員中建立和設定 iOS 版 Outlook S/MIME 原則。 這些設定提供簽署和加密憑證的自動傳遞。

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並選取 [應用程式]   > [應用程式設定原則]   > [新增]  。<br>
[新增設定原則]  窗格隨即顯示。
2. 輸入設定原則的 [名稱]  和 [描述]  。
3. 選取 [受控裝置]  作為 [裝置註冊類型]  。
4. 選取 [iOS/iPadOS]  作為 [平台]  。
5. 按一下 [選取必要的應用程式]  ，尋找並關聯您先前新增的 Microsoft iOS 版 Outlook 應用程式。 
6. 按一下 [組態設定]  來新增組態設定。 
    - 選取 [組態設定格式]  旁的 [使用組態設計工具]  ，並接受預設設定。 如需詳細資訊，請參閱 [Microsoft Outlook 組態設定](~/apps/app-configuration-policies-outlook.md)。
7. 按一下 [S/MIME]  來顯示 [Outlook S/MIME 設定]  。
8. 將 [啟用 S/MIME]  設定為 [是]  。
9. 將 [從 Intune 部署 S/MIME 憑證]  設定為 [是]  。
10. 在 [憑證設定檔類型]  旁的 [簽署憑證]  下，選擇下列其中一個選項：
    - **SCEP** - 針對裝置和使用者建立唯一憑證，可供 Microsoft Outlook 用來簽署。 如需相關資訊，請參閱[設定基礎結構以支援 SCEP 與 Intune](~/protect/certificates-scep-configure.md) 和[建立 SCEP 憑證設定檔](~/protect/certificates-profile-scep.md#create-a-scep-certificate-profile)。 
    - **已匯入 PKCS 的憑證** - 使用對於使用者是唯一的憑證，但可以在裝置之間共用，且已經由系統管理員代替使用者匯入到端點管理員。 憑證會傳遞到使用者註冊的任何裝置。 端點管理員會自動挑選支援簽署的已匯入憑證，以傳遞至與已註冊使用者對應的裝置。
    - **衍生認證** - 使用已經在裝置上，且可以用來簽署的憑證。 您必須使用 Intune 中的衍生認證流程，在裝置上擷取憑證。
11. 在 [憑證設定檔類型]  旁的 [加密憑證]  下，選擇下列其中一個選項：
    - **已匯入 PKCS 的憑證** - 會將任何已經由系統管理員匯入至端點管理員的加密憑證，傳遞給使用者已註冊的任何裝置，端點管理員會自動挑選已匯入的憑證，或支援簽署的憑證，以傳遞至與已註冊使用者對應的裝置。
    - **衍生認證** - 使用已經在裝置上，且可以用來簽署的憑證。 您必須使用 Intune 中的衍生認證流程，在裝置上擷取憑證。
12. 在 [終端使用者通知]  旁，藉由選取 [公司入口網站]  或 [電子郵件]  ，來選擇通知終端使用者擷取 iOS 版 Outlook S/MIME 憑證的方式。

    在 iOS 上，使用者必須使用公司入口網站應用程式來擷取其 S/MIME 憑證。 端點管理員會通知使用者，告訴他們必須啟動公司入口網站來擷取其 S/MIME 憑證 (透過公司入口網站的 [通知] 區段、推播通知和/或電子郵件)。 按一下其中一個通知，會帶使用者前往登陸頁面，告知他們正在擷取憑證。 擷取憑證之後，使用者就可以在 Microsoft iOS 版 Outlook 內使用 S/MIME 來簽署和加密電子郵件。
    
    終端使用者通知包含下列選項：
       - **公司入口網站** - 如果選取此選項，使用者會在其裝置上收到推播通知，這會將他們帶到公司入口網站中，擷取 S/MIME 憑證的登陸頁面。
        - **電子郵件** - 傳送電子郵件給終端使用者，告知他們必須啟動公司入口網站來擷取其 S/MIME 憑證。 如果使用者在其已註冊的 iOS 裝置上按一下電子郵件中的連結，連結會將他們重新導向至公司入口網站以擷取其憑證。
    
13. 選取 [指派]  來指派應用程式設定原則給 Azure AD 群組。 如需詳細資訊，請參閱[使用 Microsoft Intune 將應用程式指派給群組](~/apps/apps-deploy.md)。

## <a name="next-steps"></a>後續步驟

- 如需詳細資訊，請參閱 [Microsoft Intune 的應用程式設定原則](app-configuration-policies-overview.md)。
