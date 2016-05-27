---
# required metadata

title: Intune 快速入門指南 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Intune 快速入門指南
本快速入門指南逐步引導您設定 Microsoft Intune 的付費訂用帳戶，以快速又輕鬆地開始管理組織中使用的行動裝置和 Windows 電腦。 您可以依序執行每個步驟，而當某個步驟不適用於您的特定環境或商務需求時，也可直接跳過此步驟。

>[!NOTE]
>本文著重在將 Intune 設定為獨立服務。 或者，如果您目前使用 Microsoft System Center Configuration Manager 來管理電腦和伺服器，您也可以在混合式 MDM 部署中連接 Intune 與 Configuration Manager 來管理行動裝置，以[延伸 Configuration Manager 來管理行動裝置](https://technet.microsoft.com/library/jj884158.aspx)。

本快速入門指南中的步驟共用 [Intune 評估指南](/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune)中許多相同的步驟。 不過，在評估之後，當您準備好開始管理行動裝置時，您必須解決幾個額外的需求。 這些將根據您目前的網路基礎結構和商業需求而有所不同，包括︰

-   使用 Intune 與 Azure Active Directory 同步處理內部部署的 Active Directory 帳戶

-   向網域註冊機構更新公用網域和 DNS 服務記錄

-   自訂用於實際執行環境的 Intune 功能

>[!TIP]
>如果您在符合條件的方案中購買了至少 150 套的 Microsoft Intune 授權，則可使用「FastTrack 中心權益」服務，透過此服務能讓您與 Microsoft 專家一起將您的環境備妥供 Intune 運作。 請參閱 [Microsoft Intune 服務權益說明](https://technet.microsoft.com/library/mt228265.aspx)


## 開始之前
當您開始使用付費訂用帳戶，並準備好部署 Intune 和變更現有的網路基礎結構時，請使用本指南。 其中可能只涉及加入或更新內部和外部 DNS 記錄，乃至於將現有的 Active Directory 使用者帳戶同步至 Azure Active Directory。 無論您決定混合使用哪些 Intune 行動裝置管理功能，您都需要仔細規劃 Intune 與現有的網路元件和服務如何互動。 具體而言，您應該要檢閱：

-   您將如何管理使用者身分識別：對於大部分的中型到大型組織而言，若要使用 Intune 來管理使用者身分識別，最佳又最方便的方法就是透過 Azure Active Directory 將現有的目錄服務連線至 Intune。 特別是如果您已經使用其他 Microsoft 雲端服務時，例如 Office 365 或 Exchange Online。 使用 [Microsoft Azure Active Connect](https://www.microsoft.com/download/details.aspx?id=47594) 同步處理現有使用者帳戶，可快速又簡單地將內部部署 Active Directory 連線到 Azure Active Directory，並為使用者設定單一登入驗證體驗。

-   將會如何影響 DNS：如果您想要使用您自己的網域名稱，而不是第一次註冊 Intune 時所取得的預設 onmicrosoft.com 網域，則需要某些公用 DNS 記錄更新。 需要 DNS 記錄的更新，行動裝置才能找到 Intune 服務，並確保訂用帳戶的管理服務正常運作，以管理組織中使用的所有裝置。

## 備妥下列項目
準備好開始了嗎？ 當您開始使用付費訂用帳戶來執行 Intune 時，您需要下列項目：

### 啟用 Silverlight 之網頁瀏覽器的裝置
您需要此項目來存取 Intune 管理主控台，以管理裝置、應用程式和原則。 當您不是從行動裝置存取公司入口網站應用程式時，您也需要網頁瀏覽器來存取網頁型公司入口網站。 為了方便起見，您可以在用於 Intune 系統管理的相同瀏覽器上使用「隱私權模式」設定 (例如，在 Internet Explorer 中，您可以按一下 [工具] &gt; [InPrivate 瀏覽]

>由於有此需求，不支援使用 Microsoft Edge 瀏覽器來存取 Intune 管理主控台。


### 行動裝置的憑證
如果您要以 Intune 管理 iOS 或 Windows Phone 裝置，將需要憑證和用以擷取這些憑證的帳戶。 管理 Android 裝置不需要任何額外的憑證。

- 從市集安裝公司入口網站應用程式的 Windows Phone 8.1 使用者不需要憑證。 不過，對於 Windows Phone 8.0，或想要使用 Intune 將公司入口網站應用程式部署至 Windows Phone 8.1 裝置，則需要 [Symantec 程式碼簽署憑證](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)。

>[!NOTE]
>本指南假設使用者是在 Windows Phone 8.1 或更新版本的裝置上，從市集取得公司入口網站應用程式。 如需 Windows Phone 8.0 支援的相關資訊，請參閱[使用 Microsoft Intune 設定 Windows Phone 8.0 管理](/Intune/deploy-use/set-up-windows-phone-8.0-management-with-microsoft-intune)

- 將 Windows 電腦註冊為裝置時，或[安裝 Microsoft Intune 的 Windows 電腦用戶端](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune)時，Windows 電腦或 Windows RT 裝置沒有憑證需求

- 對於 iOS 或 Mac OS X 裝置，您需要向 Apple 要求 Apple 推播通知服務憑證，如[使用 Microsoft Intune 設定 iOS 和 Mac 管理](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)中的步驟 3 所述

### 後續步驟
現在就開始使用 Intune 快速入門指南！

>[!div class="step-by-step"]


<!--HONumber=May16_HO2-->


