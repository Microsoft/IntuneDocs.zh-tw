---
title: 建立 Exchange 條件式存取原則 | Microsoft Intune
titlesuffix: Microsoft Intune
description: 在 Intune 中為 Exchange 內部部署及舊版的 Exchange Online Dedicated 設定條件式存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: ed996ec17ab0c8144286eeed0a87f07b35da2969
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53817053"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>為 Exchange 內部部署及舊版的 Exchange Online Dedicated 建立條件式存取原則。

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文將說明，如何根據裝置相容性來設定 Exchange 內部部署的條件式存取。

如果您有 Exchange Online Dedicated 環境，而且需要了解它是使用新版或舊版的設定，請連絡您的帳戶管理員。 若要控制 Exchange 內部部署或舊版 Exchange Online Dedicated 環境的電子郵件存取，請在 Intune 中設定 Exchange 內部部署的條件式存取。

## <a name="before-you-begin"></a>開始之前

在設定條件式存取之前，請確定下列事項：

- 您的 Exchange 版本必須是「Exchange 2010 SP1 或更新版本」。 支援 Exchange 伺服器用戶端存取伺服器 (CAS) 陣列。

- 您必須使用 [Exchange Active Sync 內部部署 Exchange Connector](exchange-connector-install.md)，將 Intune 連線至內部部署 Exchange。

    >[!IMPORTANT]
    >內部部署 Exchange Connector 僅適用於您的 Intune 租用戶，無法搭配任何其他租用戶使用。 Intune 現在支援每個訂閱有多個內部部署 Exchange 連接器。 如果您有多個內部部署 Exchange 組織，則可以為每個 Exchange 組織設定個別的連接器。

- 內部部署 Exchange 組織的連接器可以安裝在任何電腦上，只要該電腦能與 Exchange 伺服器通訊。

- 此連接器支援 **Exchange CAS 環境**。 想要的話，在技術上您可以將連接器直接安裝在 Exchange CAS 伺服器上，但不建議這麼做，因為這會增加伺服器負載。 設定連接器時，您必須將它設定成可以與其中一部 Exchange CAS 伺服器通訊。

- 必須以憑證式驗證或使用者認證項目來設定 **Exchange ActiveSync**。

- 設定條件式存取原則並以使用者為目標後，使用者使用的**裝置**必須符合下列條件，使用者才能連接到其電子郵件：
    - 已向 Intune **註冊**，或為加入網域的電腦。
    - 已在 **Azure Active Directory** 中註冊。 此外，必須向 Azure Active Directory 註冊用戶端 Exchange ActiveSync 識別碼。
<br></br>
- Intune 和 Office 365 客戶會自動啟用 Azure AD 裝置註冊服務 (DRS)。 已部署 ADFS 裝置註冊服務的客戶不會在其內部部署 Active Directory 中看到已註冊的裝置。 **這不適用於 Windows 電腦和 Windows Phone 裝置**。

- 「符合」部署到該裝置的合規性原則。

- 若裝置不符合條件式存取設定，將會在使用者登入時，對其顯示下列其中一則訊息：
    - 若裝置未向 Intune 註冊，或未在 Azure Active Directory 中註冊，將會顯示一則訊息，指示使用者如何安裝公司入口網站應用程式、如何註冊裝置，以及如何啟用電子郵件。 此程序也會將裝置的 Exchange ActiveSync 識別碼與 Azure Active Directory 中的裝置記錄相關聯。
    - 若裝置不合規，將會顯示一則訊息，將使用者導向 Intune 公司入口網站或公司入口網站應用程式，讓使用者能夠從中尋找到問題及其修復方法的相關資訊。

### <a name="support-for-mobile-devices"></a>支援行動裝置

- Windows Phone 8.1 和更新版本
- iOS 上的原生電子郵件應用程式。
- EAS 郵件用戶端 (例如 Android 4 或更新版本上的 Gmail)。
- EAS 郵件用戶端 **Android 工作設定檔裝置：** Android 工作設定檔裝置只支援**工作設定檔**中的 **Gmail** 和 **Nine Work for Android Enterprise**。 Android 工作設定檔若要使用條件式存取，除了必須部署 Gmail 或 Nine Work for Android Enterprise 應用程式的電子郵件設定檔之外，還必須將這些應用程式部署為必要安裝。

> [!NOTE]
> Android 與 iOS 版 Microsoft Outlook 不透過 Exchange 內部部署連接器支援。 若要利用 Azure Active Directory 條件式存取原則與 Intune 應用程式防護原則來保護您內部部署信箱的 iOS 與 Android 版 Outlook，請參閱[搭配 iOS 與 Android 版 Outlook 使用混合式現代化驗證](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) \(機器翻譯\)。 

### <a name="support-for-pcs"></a>對電腦的支援

Windows 8.1 及更新版本上的原生「郵件」應用程式 (必須已向 Intune 註冊)


## <a name="configure-exchange-on-premises-access"></a>設定 Exchange 內部部署存取

1. 移至 [Azure 入口網站](https://portal.azure.com/)，並使用您的 Intune 認證登入。

1. 成功登入之後，您會看到 [Azure 儀表板]。

1. 選擇左功能表中的 [所有服務]，然後在文字方塊篩選中輸入  **Intune** 。  **** 

1. 選擇 [Intune]，您會看到 [Intune 儀表板]。  ****

1. 選擇 [內部部署存取]。 [內部部署] 窗格會顯示條件式存取原則與受該原則影響之裝置的狀態。

1. 從 [管理] 下選擇 [Exchange 內部部署存取]。

1. 在 [Exchange 內部部署存取] 窗格中選擇 [是]，以啟用 Exchange 內部部署存取控制。

    > [!NOTE]
    > 若未設定 Exchange Active Sync 內部部署連接器，則會停用此選項。  您必須至少先安裝及設定一個連接器，才能為 Exchange 內部部署啟用條件式存取。 如需詳細資訊，請參閱[安裝 Intune 內部部署 Exchange 連接器](exchange-connector-install.md)

1. 從 [指派] 下選擇 [包含的群組]。  請使用應套用條件式存取的安全性使用者群組。 此動作會需要使用者向 Intune 註冊其裝置，而且必須符合相容性設定檔的規範。

1. 若要排除特定的使用者群組，可以選擇 [排除的群組]，然後選取要免套用裝置註冊與合規需求的使用者群組。

1. 從 [設定] 下選擇 [使用者通知]，可修改預設的電子郵件訊息。 當使用者裝置不合規範，卻又要存取 Exchange 內部部署時，即會將此訊息會傳送給使用者。 訊息範本會使用標記語言。  當您一邊鍵入訊息時，會一邊顯示訊息的預覽。
    > [!TIP]
    > 若要深入了解標記語言，請參閱 Wikipedia 上的這篇[文章](https://en.wikipedia.org/wiki/Markup_language)。

1. 依據接下來的兩個步驟所述，在 [Advanced Exchange Active Sync access settings] (進階 Exchange Activesync 存取設定) 窗格中，為從不是由 Intune 管理的裝置存取設定全域預設規則及平台層級規則。

1. 對於不受條件式存取影響的裝置或其他規則，您可以選擇允許它們存取 Exchange 或加以封鎖。

   - 當您設定成允許存取時，所有裝置即可立即存取 Exchange 內部部署。  若**包含的群組**中之使用者的裝置稍後被評估為不符合合規性政策，或未向 Intune 註冊，將會予以封鎖。
   - 當您設定為禁止存取時，會立即禁止所有裝置存取 Exchange 內部部署。  **包含的群組**中之使用者的裝置若已向 Intune 註冊，並經評估為相容，即可存取 Exchange 內部部署。 因為非執行 Samsung Knox Standard 的 Android 裝置不支援此設定，所以一律會被封鎖。

1. 從 [裝置平台例外狀況] 下選擇 [新增]，以指定平台。 若將 [未受控的裝置存取] 設定設定為 [封鎖]，即使已在平台例外狀況中指定要禁止的平台，仍會允許已經註冊且相容的裝置進行存取。 選擇 [確定]，以儲存設定。

1. 在 [內部部署] 窗格中，按一下 [儲存]，以儲存條件式存取原則。

## <a name="create-azure-ad-conditional-access-policies-in-intune"></a>在 Intune 中建立 Azure AD 條件式存取原則

從 Intune 1704 版開始，管理員可以從 Intune Azure 入口網站建立 Azure AD 條件式存取原則，如此您就不需要在 Azure 和 Intune 工作負載之間切換。

> [!IMPORTANT]
> 您必須要有 Azure AD Premium 授權，才能從 Intune Azure 入口網站建立 Azure AD 條件式存取原則。

### <a name="to-create-azure-ad-conditional-access-policy"></a>建立 Azure AD條件式存取原則

1. 在 [Intune 儀表板] 中，選擇 [條件式存取]。

2. 在 [原則] 窗格中，選擇 [新增原則] 來建立新的 Azure AD 條件式存取原則。

## <a name="see-also"></a>請參閱

[Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
