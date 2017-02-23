---
title: "設定的電信費用管理服務 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰設定 Saaswedo 電信費用管理服務，與 Intune 相互整合。"
keywords: Saaswedo
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 915d61344a3c1d388305dd51b1e2463bd2e32770
ms.openlocfilehash: 8d94fec099e1dc8918077062fb73b94a5973ea96

---

# <a name="set-up-a-telecom-expense-management-service-in-intune-azure-preview"></a>在 Intune Azure 預覽版中設定電信費用管理服務
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune 整合了第三方體開發人員 Saaswedo 的 Datalert 電信費用管理解決方案。 Datalert 是即時的電信費用管理軟體，可讓您管理電信數據使用量，協助 Intune 管理的裝置避免高額費用及非預期的超額數據費和漫遊費。 Intune 與 Datalert 整合可讓您集中設定、監視及實施漫遊與國內數據使用量限制，並在超出定義的閾值限制時自動發出警示。 您可以設定服務對個人或使用者群組套用不同的動作，包括在使用者超過閾值時停用漫遊。 Datalert 管理主控台也提供有關數據使用量與監視資訊的報表。

在開始使用 Intune 的 Datalert 服務之前，必須先個別在 Datalert 主控台與 Intune 中設定。 Datalert 服務與 Intune 都必須開啟連線。 若只有 Datalert 端的連線開啟，但 Intune 端未開啟，Intune 將會在收到通訊後予以忽略。

>[!NOTE]
>若要在您的試用租用戶中啟用此功能，請[連絡 Microsoft 支援服務](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)為您啟用，並連絡Datalert 支援服務洽談所需的軟體授權。

## <a name="supported-platforms"></a>支援的平台

- Samsung Knox
- iOS 8.0 和更新版本

## <a name="prerequisites"></a>必要條件

- 訂問 Microsoft Intune
- 訂閱 Datalert 電信費用管理服務

## <a name="list-of-telecom-expense-management-providers"></a>電信費用管理提供者清單

Intune 目前整合了下列電信費用管理提供者︰

[Saaswedo Datalert 電信費用管理服務](http://www.datalert.biz/)

## <a name="configure-intune-to-work-with-the-datalert-service"></a>設定 Intune 與 Datalert 服務搭配運作

 

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中選擇 [設定裝置]。
2. 在 [裝置設定] 刀鋒視窗中選擇 [設定]   >  [電信費用管理]。
2. 從 [電信費用管理] 下選取 [連線狀態]。

3. 選取 [TEM 服務提供者清單]，然後從顯示的清單中選取您的提供者。 您提供者的專屬頁面會隨即開啟。 若為 Saaswedo，將會開啟 Datalert 頁面。 您必須使用 Saaswedo Datalert 才能購買訂閱。

4. 在 **Datalert** 管理主控台中︰

    a. 前往 [設定] 索引標籤，然後前往 [MDM 組態] 區段。

    b. 選取 [解除鎖定]，讓您可以在該頁面上輸入設定。

    c. 為 [Server MDM] (伺服器的 MDM) 選擇 [ Microsoft Intune]。

    d. 在 [租用戶識別碼] 中輸入您的 Intune 租用戶識別碼，然後選取 [連線] 按鈕。 選取 [連線] 會指定 Datalert 簽入 Intune，確保 Datalert 之前與 Intune 之間沒有任何連線。 Microsoft [登入] 頁面會在幾秒後出現，然後是 Datalert Azure 驗證。

    e. 在 Microsoft 驗證頁面上選取 [接受]。 您會被重新導向至 Datalert 的 [Thank you] 頁面，並於幾秒之後關閉。 Datalert 會驗證連線，並在驗證過的項目清單旁顯示綠色核取記號。 若驗證失敗，將會顯示紅色的訊息。 當發生此情況時，請連絡 Datalert 支援服務尋求協助。

5. 請稍候幾分鐘後前往 Azure 入口網站檢查連線狀態是否為**作用中**。 

    >[!NOTE]
    >若要在您的試用租用戶中啟用此功能，請[連絡 Microsoft 支援服務](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

6. 返回 Datalert 管理主控台並設定您的資料行︰

    a. 按一下 [設定] 索引標籤。

    b。 前往 [安裝精靈]，並遵循精靈中的步驟。



Datalert 服務現在已上線執行，會開始監視數據使用量，並停用超出設定使用量限制之裝置的行動數據與漫遊數據。

## <a name="turning-off-the-datalert-service"></a>關閉 Datalert 服務

若在 Azure 入口網站停用 Datalert 服務︰

- 所有因為過去違反使用量限制而對裝置套用的動作都會復原。
- 使用者不再受限於數據存取與漫遊。
- Intune 仍會接收來自服務的訊號，但會予以忽略。

**關閉服務**

1. 在 Azure 入口網站的 [電信費用管理] 刀鋒視窗中選取 [停用]。

2. 選取 [儲存]。

## <a name="viewing-data-usage-and-roaming-reports"></a>檢視數據使用量及漫遊報表

目前只會在 Saaswedo 的 Datalert 管理主控台中提供數據使用量報告。



<!--HONumber=Feb17_HO2-->


