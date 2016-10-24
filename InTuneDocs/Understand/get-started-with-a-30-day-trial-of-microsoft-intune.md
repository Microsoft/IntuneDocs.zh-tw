---
title: "Intune 評估指南 | Microsoft Intune"
description: "如何設定免費 30 天 Intune 評估版的簡介和先決條件"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 08/09/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 619a1d11-3d22-4635-8f70-770eba3e1712
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 581e880fa4308ec627f5b2c1242fb5b30b713743
ms.openlocfilehash: 3973ac11d4734b17f905e88259863d7ddb59c1f4


---

# Intune 評估指南
您可以輕鬆快速地設定 Intune 30 天免費評估，來管理您的行動裝置與電腦。 只要在評估版中執行幾個簡單的步驟，就能新增多達 100 個使用者與裝置、設定群組、設定相容性原則，以及註冊與管理行動裝置與電腦。

在本主題中，您將了解啟動及執行 Intune 評估版的基本作業，並概略了解這項服務，以便您可以評估 Intune 的特色與功能。

請觀看這段五分鐘示範影片，以了解如何輕鬆開始使用 Microsoft Intune 免費評估版來管理您的裝置。 影片的第一個部分提及已「淘汰」的入口網站，因此，儘管您將使用不同的入口網站，在本質上步驟仍會相同。 您可以前往[這裡](https://docs.microsoft.com/intune/deploy-use/account-portal-merged-with-Office-365)閱讀入口網站的相關資訊。

<iframe width="675" height="480" src="https://www.youtube.com/embed/ltcZvm4VOFU" frameborder="0" allowfullscreen></iframe>

## 開始之前
開始使用 Intune 之前，您需要下列項目：

-   具備已啟用 Silverlight 之網頁瀏覽器的裝置，您可以使用這部裝置來存取建立 Intune 使用者帳戶的網站 (**Office 365 系統管理中心**)，以及管理裝置、群組與原則的網站 (**Intune 管理主控台**)。

-   具備網頁瀏覽器的第二部裝置，您將使用這部裝置來測試 Intune 使用者如何透過公司入口網站來註冊及管理其裝置。 您也將測試使用者如何尋找並安裝應用程式，以及如何向系統管理員尋求協助。 如果您沒有第二部裝置，您可以在用於 Intune 系統管理的相同瀏覽器上使用「隱私權模式」設定 (例如，在 Internet Explorer 中，您可以選擇 [工具] &gt; [InPrivate 瀏覽])。

-   如果您已經具有 Microsoft Online Services 帳戶，則需要該帳戶的系統管理員認證。 如果您沒有這類帳戶，或者使用這個 Intune 租用戶的目的為僅供評估，則不需要這些系統管理員認證。

-   如果您要以 Intune 評估版管理 iOS 或 Windows Phone 8.1 裝置，將需要憑證 (或金鑰) 和帳戶，以擷取這些憑證 (請參閱下表)。 Android 裝置不需要任何額外的憑證。

    |平台|憑證需求|詳細資訊|
    |------------|----------------------------|--------------------|
    |Windows Phone 8.1 |從市集安裝公司入口網站應用程式的 Windows Phone 8.1 使用者不需要憑證。 |本指南假設您的使用者可從 Windows Phone 8.1 或更新版本裝置的市集，取得公司入口網站應用程式。 |
    |Windows 10、Windows RT 8.1 或 Windows 8.1 裝置|註冊 Windows RT 和 Windows 裝置不需要憑證。|[使用 Microsoft Intune 安裝 Windows 電腦用戶端](/Intune/Deploy-Use/install-the-windows-pc-client-with-microsoft-intune)。|
    |iOS 7.1 或更新版本|取得 Apple Push Notification service 憑證。|如[使用 Microsoft Intune 設定 iOS 和 Mac 管理](/Intune/Deploy-Use/set-up-ios-and-mac-management-with-microsoft-intune)中所述，向 Apple 要求 Apple Push Notification 服務憑證。|

## 完成 Intune 30 天評估步驟
- [步驟 1︰登入或註冊 30 天評估](get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)。 註冊或登入 Intune 之前，您應該考慮是否要使用現有帳戶進行登入，還是建立僅用於 Microsoft Intune 30 天評估的暫時帳戶。
- [步驟 2：新增使用者](get-started-with-a-30-day-trial-of-microsoft-intune-step-2.md)。 完成設定您的帳戶之後，您會將個別使用者帳戶新增至 Intune，或大量新增使用者 (請參閱本節中的指示)。 開始之前，請務必了解 Intune 如何處理系統管理員帳戶。
- [步驟 3：建立群組來組織使用者和裝置](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)。 Intune 中的群組讓您在管理裝置和使用者時有絕佳的彈性。 您可以設定群組，使其符合組織的需求 (例如依據地理位置、部門或硬體特性)，並且使用它們來大規模地執行各種系統管理工作，從設定一組使用者的原則，到部署應用程式至一組裝置。
- [步驟 4：建立原則及發行應用程式](get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)。 Intune 原則提供設定，協助您控制行動裝置上的安全性設定、維護電腦的 Windows 防火牆和 Endpoint Protection 設定，以及部署應用程式。
- [步驟 5：註冊行動裝置並安裝應用程式](get-started-with-a-30-day-trial-of-microsoft-intune-step-5.md)。 若要使用 Intune 設定行動裝置管理，您必須設定行動裝置管理授權單位、啟用特定裝置平台的管理，然後使用公司入口網站應用程式註冊您的裝置。 接著便可部署您發行的 Microsoft Skype 應用程式。
- [步驟 6：其他選項和額外項目](get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)。 選擇如何使用警示、報表和其他 Intune 功能，以符合您商務需求。
- [步驟 7：後續步驟](get-started-with-a-30-day-trial-of-microsoft-intune-step-7.md)。 準備移至 Intune 付費訂閱，並利用 Intune「FastTrack Center 權益」。


### 後續步驟
已經可以開始使用 30 天試用訂閱！

>[!div class="step-by-step"]
[**註冊 Intune** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)

### 請參閱
[Intune 快速入門指南](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune)



<!--HONumber=Oct16_HO2-->


