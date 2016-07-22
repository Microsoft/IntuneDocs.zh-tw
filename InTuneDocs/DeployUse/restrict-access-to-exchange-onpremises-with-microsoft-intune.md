---
title: "限制 Exchange 內部部署和舊版 Exchange Online Dedicated 的電子郵件存取 | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a55071f5-101e-4829-908d-07d3414011fc
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ded7bd6c971a9448ad6e6492ebc5e42dfcb5d76e
ms.openlocfilehash: 6bc85a0291fa62069ba6a0f63fdd9306db3c4195


---

# 使用 Intune 限制 Exchange 內部部署和舊版 Exchange Online Dedicated 的電子郵件存取


如果您有 Exchange Online Dedicated 環境，而且需要了解它是使用新版或舊版的設定，請連絡您的帳戶管理員。


若要控制 Exchange 內部部署或舊版 Exchange Online Dedicated 環境的電子郵件存取，請在 Intune 中設定 Exchange 內部部署的條件式存取。
若要深入了解條件式存取如何運作，請參閱[限制存取電子郵件和 O365 服務]( restrict-access-to-email-and-o365-services-with-microsoft-intune.md)文件。

在設定條件式存取**之前**，請驗證：

-   您的 Exchange 版本必須是 **Exchange 2010 或更新版本**。 支援 Exchange 伺服器用戶端存取伺服器 (CAS) 陣列。

-   您必須使用 **內部部署 Exchange 連接器**，將 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 連接到 Microsoft Exchange 內部部署。 這可讓您透過 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 主控台管理裝置。 如需此連接器的詳細資訊，請設定 [Intune 內部部署 Exchange Connector](intune-on-premises-exchange-connector.md)。

    -   您在 Intune 主控台中可使用的內部部署 Exchange 連接器僅適用於 Intune 租用戶，無法搭配任何其他租用戶使用。 您也應該確定適用於租用戶的 Exchange 連接器**只安裝在一部電腦上**。

        應從 Intune 管理主控台下載這個連接器。  如需如何設定內部部署 Exchange 連接器的逐步解說，請參閱[設定適用於內部部署或託管 Exchange 的 Exchange 內部部署連接器](intune-on-premises-exchange-connector.md)。

    -   連接器可以安裝在任何電腦上，只要該電腦能與 Exchange 伺服器通訊。

    -   此連接器支援 **Exchange CAS 環境**。 想要的話，在技術上您可以將連接器直接安裝在 Exchange CAS 伺服器上，但不建議這麼做，因為這會增加伺服器負載。
    設定連接器時，您必須將它設定成可以與其中一部 Exchange CAS 伺服器通訊。

-   必須以憑證式驗證或使用者認證項目來設定 **Exchange ActiveSync**。

設定條件式存取原則並以使用者為目標後，使用者使用的**裝置**必須符合下列條件，使用者才能連接到其電子郵件：

-  已向 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] **註冊**或是已加入網域的電腦。

-  已在 **Azure Active Directory** 中註冊。 此外，必須向 Azure Active Directory 註冊用戶端 Exchange ActiveSync 識別碼。

  Intune 和 Office 365 客戶將會自動啟用 AAD DRS。 已部署 ADFS 裝置註冊服務的客戶不會在其內部部署 Active Directory 中看到已註冊的裝置。 **這不適用於 Windows 電腦和 Windows Phone 裝置**。

-   與所有部署到該裝置的 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 相容性原則**相容**。

下圖說明適用於 Exchange 內部部署的條件式存取原則在評估允許或封鎖裝置時的流程。

![此圖顯示決定允許或禁止裝置存取 Exchange 內部部署的決策點](../media/ConditionalAccess8-2.png) 如果不符合條件式存取原則，使用者在登入時會看見下列其中一個訊息：

- 如果裝置未向 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 註冊，或未在 Azure Active Directory 中註冊，就會顯示訊息，指示如何安裝公司入口網站應用程式、註冊裝置及啟用電子郵件。 此程序也會將裝置的 Exchange ActiveSync 識別碼與 Azure Active Directory 中的記錄產生關聯。

-   如果裝置不相容，就會顯示訊息，將使用者引導至 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 公司入口網站或公司入口網站應用程式，讓他們找到問題的相關資訊，以及如何修復問題的方法。

## 支援行動裝置
-   Windows Phone 8 和更新版本

-   iOS 上的原生電子郵件應用程式。

-   Android 4 或更新版本上的原生電子郵件應用程式
> [!NOTE]
> 不支援適用於 Android 和 iOS 的 Microsoft Outlook 應用程式。

## 對電腦的支援

Windows 8 和更新版本上的**郵件**應用程式 (已註冊到 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)])

##  設定條件式存取原則

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 **[原則]** > **[條件式存取]** > **[Exchange 內部部署原則]**。
![IntuneSA5aSelectExchOnPremPolicy](../media/IntuneSA5aSelectExchOnPremPolicy.png)

2.  設定含有所需設定的原則：![[Exchange 內部部署原則] 頁面的螢幕擷取畫面](../media/IntuneSA5bExchangeOnPremPolicy.png)

  - **封鎖不相容或未向 Microsoft Intune 註冊之裝置的電子郵件應用程式存取 Exchange 內部部署：**當您選取此選項時，將禁止未受 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 管理或不符合相容性原則的裝置存取 Exchange 服務。

  - **預設規則覆寫 - 一律允許已註冊且相容的裝置存取 Exchange**：當您核取此選項時，將允許已在 Intune 中註冊且符合相容性原則的裝置存取 Exchange。  
  此規則會覆寫 [預設規則]，這表示即使您將 [預設規則] 設為隔離或封鎖存取，已註冊且相容的裝置仍能夠存取 Exchange。

  - **目標群組：**選取必須向 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 註冊裝置才能存取 Exchange 的 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 使用者群組。

  - **豁免群組：**選取豁免於條件式存取原則的 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 使用者群組。 此清單中的使用者即使也在 [目標群組] 清單中，仍將豁免。

  - **平台例外：**選擇 [新增規則] 設定規則，以針對指定的行動裝置系列和機型來定義存取層級。 因為這些裝置可以是任何類型，所以您也可以設定 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 不支援的裝置類型。

  - **預設規則：**針對任何其他規則未涵蓋的裝置，您可以選擇允許它存取 Exchange、封鎖它或隔離它。 當您設定規則以允許存取時，對於已註冊且相容的裝置而言，將自動授與 iOS、Windows 和 Samsung KNOX 裝置的電子郵件存取。 使用者不必經過任何程序即可取得電子郵件。  在不是執行 Samsung KNOX 的 Android 裝置上，使用者會收到隔離電子郵件，其中包含驗證註冊和相容性的引導式逐步解說，之後才可存取電子郵件。 如果您將規則設為封鎖或隔離存取，所有裝置不論是否已在 Intune 註冊，都將遭封鎖而無法存取 Exchange。 若要避免已註冊且相容的裝置受到此規則影響，請核取 [預設規則覆寫]。
>[!TIP]
>如果您在授與電子郵件存取之前打算先封鎖所有裝置，請選擇 [封鎖存取] 或 [隔離] 規則。 預設規則將套用到所有裝置類型，因此您設定為平台例外和 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 不支援的裝置類型也會受到影響。

  - **使用者通知：**除了從 Exchange 傳送的通知電子郵件，Intune 也會傳送包含裝置解除封鎖步驟的電子郵件。 您可以編輯預設訊息，依照您的需求來自訂。 由於包含修復指示的 Intune 通知電子郵件會傳遞到使用者的 Exchange 信箱，萬一使用者在收到此電子郵件訊息之前，裝置就遭到封鎖，他們可以使用未封鎖的裝置或其他方法來存取 Exchange 並檢視該訊息。 這在 [預設規則] 已設為封鎖或隔離時特別有用。  在此情況下，使用者必須前往應用程式市集，下載 [Microsoft 公司入口網站] 應用程式並註冊其裝置。 這適用於 iOS、Windows 和 Samsung KNOX 裝置。  對於不是執行 Samsung KNOX 的裝置，您必須將隔離電子郵件傳送到備用電子郵件帳戶，接著，使用者必須將郵件複製到遭封鎖的裝置，以完成註冊和相容性程序。
  > [!NOTE]
  > 為了讓 Exchange 能夠傳送通知電子郵件，您必須指定應該用來傳送通知電子郵件的帳戶。
  >
  > 如需詳細資料，請參閱[設定適用於內部部署或託管 Exchange 的 Exchange 內部部署連接器](intune-on-premises-exchange-connector.md)。

3.  完成之後，請選擇 [儲存]。

-   您不需部署條件式存取原則，它會立即生效。

-   使用者設定 Exchange ActiveSync 設定檔之後，可能需要 1-3 個小時才能封鎖裝置 (如果不是由 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 管理)。

-   如果封鎖的使用者之後向 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 註冊裝置 (並修復不相容性)，則會在 2 分鐘內解除封鎖電子郵件存取。

-   如果使用者從 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 取消註冊，則可能需要 1-3 個小時才能封鎖裝置。

**若要查看一些如何設定條件式存取原則以限制裝置存取的範例案例，請參閱[限制電子郵件存取範例案例](restrict-email-access-example-scenarios.md)。**

## 後續步驟
[限制存取 SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

[限制存取商務用 Skype Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


