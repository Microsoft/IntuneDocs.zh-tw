---
title: "Intune 快速入門指南 | Microsoft Intune"
description: "開始使用 Intune 訂用帳戶的需求和必要條件"
keywords: 
author: Staciebarker
manager: arob98
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 376e6c1ae229187ab8ec73390f091f1d534365dd
ms.openlocfilehash: e7ecf24c3fa678e68603f0e3523f2694a73e145c


---


# Intune 快速入門指南
本快速入門指南逐步引導您設定 Microsoft Intune 的付費訂用帳戶，以快速又輕鬆地管理組織使用的行動裝置和 Windows 電腦。 您可以依序執行每個步驟。當某個步驟不適用於您的特定環境或商務需求時，您可以直接跳過該步驟。

>[!NOTE]
>本文著重在將 Intune 設定為獨立服務。 或者，如果您目前正在使用 Microsoft System Center Configuration Manager 來管理電腦和伺服器，您可以[延伸 Configuration Manager 來管理行動裝置](https://technet.microsoft.com/library/jj884158.aspx)。 您可以透過在混合式行動裝置管理 (MDM) 部署中連接 Intune 和 Configuration Manager 來達成。

本快速入門指南中的步驟共用 [Intune 評估指南](/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune)中許多相同的步驟。 不過，當您完成評估並準備好開始管理行動裝置時，您必須先解決幾個額外的需求：

-   使用 Intune 與 Azure Active Directory 同步處理內部部署的 Active Directory 帳戶。

-   向網域註冊機構更新公用網域和 DNS 服務記錄。

-   針對生產環境用途自訂 Intune 功能。

>[!TIP]
>如果您在符合條件的方案中購買了至少 150 套的 Microsoft Intune 授權，則可使用 *FastTrack 中心權益*服務，透過此服務能讓您與 Microsoft 專家一起將您的環境備妥供 Intune 運作。 請參閱 [Microsoft Intune 服務權益說明](https://technet.microsoft.com/library/mt228265.aspx)。


## 開始之前
當您開始使用付費訂用帳戶，並準備好部署 Intune 和變更現有的網路基礎結構時，請使用本指南。 這些工作內容的範圍從單純涉及新增或更新內部和外部 DNS 記錄，乃至於將現有的 Active Directory 使用者帳戶同步至 Azure Active Directory。 無論您決定混合使用哪些 Intune 行動裝置管理功能，都需要仔細規劃 Intune 與現有的網路元件和服務的互動方式。 具體而言，您應該要檢閱：

-   **管理使用者身分識別的方式**：對於大部分的中型到大型組織而言，使用 Intune 管理使用者身分識別最佳且最方便的方式，便是將現有的目錄服務透過 Azure Active Directory 連線到 Intune。 特別是如果您已經使用其他 Microsoft 雲端服務時，例如 Office 365 或 Exchange Online。 使用 [Microsoft Azure Active Directory Connect](https://www.microsoft.com/download/details.aspx?id=47594) 同步處理現有使用者帳戶，可快速又簡單地將內部部署 Active Directory 連線到 Azure Active Directory，並為使用者設定單一登入驗證體驗。

-   **DNS 會受到什麼影響**：如果您想要使用您自己的網域名稱，而不是您首次註冊 Intune 時所取得的預設 onmicrosoft.com 網域，您將需要更新一些公用 DNS 記錄。 需要更新 DNS 記錄，行動裝置才能找到 Intune 服務，並確保訂用帳戶的管理服務正常運作，以管理組織中使用的所有裝置。

## 備妥下列項目
準備好開始了嗎？ 當您開始使用付費訂用帳戶來執行 Intune 時，您需要下列項目：

### 啟用 Silverlight 之網頁瀏覽器的裝置
您需要此項目來存取 Intune 管理主控台，以管理裝置、應用程式和原則。 當您不是從行動裝置存取公司入口網站應用程式時，您也需要網頁瀏覽器來存取網頁型 Intune 公司入口網站。 為了方便起見，您可以在用於 Intune 系統管理的相同瀏覽器上使用「隱私權模式」設定 (例如，在 Internet Explorer 中，您可以按一下 [工具] &gt;[InPrivate 瀏覽])。

>[!TIP]
>由於有此需求，不支援使用 Microsoft Edge 瀏覽器來存取 Intune 管理主控台。


### 行動裝置的憑證
如果您要以 Intune 管理 iOS 或 Windows Phone 裝置，將需要憑證和帳戶以擷取那些憑證。 管理 Android 裝置不需要任何額外的憑證。

- 從市集安裝公司入口網站應用程式的 **Windows Phone 8.1** 使用者不需要憑證。 不過，針對 **Windows Phone 8.0**，或當您想要使用 Intune 將公司入口網站應用程式部署到 Windows Phone 8.1 裝置時，則需要 [Symantec 程式碼簽署憑證](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)。

>[!NOTE]
>本指南假設使用者是在 Windows Phone 8.1 或更新版本的裝置上，從市集取得公司入口網站應用程式。 如需 Windows Phone 8.0 支援的相關資訊，請參閱[使用 Microsoft Intune 設定 Windows Phone 8.0 管理](/Intune/deploy-use/set-up-windows-phone-8.0-management-with-microsoft-intune)。

- 當您將 Windows 電腦註冊為裝置，或[安裝 Microsoft Intune 的 Windows 電腦用戶端](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune)時，**Windows 電腦**或 **Windows RT 裝置**將不會有憑證需求。

- 針對 **iOS** 或 **Mac OS X** 裝置，您需要向 Apple 要求 Apple 推播通知服務憑證，如[使用 Microsoft Intune 設定 iOS 和 Mac 管理](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)中的步驟 3 所述。

## 後續步驟
現在就開始使用 Intune 快速入門指南！

>[!div class="step-by-step"]
[**登入 Intune** &rarr;](start-with-a-paid-subscription-to-microsoft-intune-step-1.md)



<!--HONumber=Jul16_HO3-->


