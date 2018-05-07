---
title: 將應用程式指派給 Android for Work 裝置
titlesuffix: Microsoft Intune
description: 了解如何同步處理，並將應用程式從 Google Play for Work 商店指派給 Android for Work 裝置。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1742c33642667a9e7b8ca2f780094345959cd86c
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="assign-apps-to-android-for-work-devices-with-intune"></a>使用 Intune 將應用程式指派至 Android for Work 裝置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android for Work 是適用於 Android 裝置的計劃。 您在 Android for Work 裝置上安裝的所有應用程式都是來自 Google Play for Work 商店。 將應用程式指派至 Android for Work 裝置的方式，與您將應用程式指派至標準 Android 裝置的方式不同。 您需要登入商店、瀏覽所需的應用程式，並核准這些應用程式。 然後，該應用程式會出現在 Azure 入口網站的 [授權的應用程式] 節點中，而且您可以管理應用程式的指派，如同其他應用程式一樣。

此外，如果您已建立自己的企業營運 (LOB) 應用程式，則可以依照以下方式指派這些應用程式：
- 註冊一個 Google 開發人員帳戶，您就能夠在 Google Play 商店的私人區域發佈應用程式。
- 使用 Intune 同步應用程式。

## <a name="before-you-start"></a>開始之前

確定您已在 Azure 入口網站的 [裝置註冊] 工作負載中，設定 Intune 與 Android for Work 搭配使用。

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>與 Google Play for Work 商店中的應用程式同步處理

1. 移至 [Google Play for Work 商店](https://play.google.com/work)。 使用您用來設定 Intune 和 Android for Work 間連線的相同帳戶進行登入。
2. 搜尋市集並選取您要使用 Intune 指派的應用程式。
3. 在顯示應用程式的頁面上，選取 [核准]。  
    在下列範例中，已經選擇 Microsoft Excel 應用程式。

    ![Google Play for Work 商店中的 [核准] 按鈕](media/approve.png)
    
   應用程式視窗隨即開啟，要求您授權讓應用程式執行各種作業。 

4. 選取 [核准] 接受應用程式權限，並繼續作業。

    ![應用程式權限的 [核准] 按鈕](media/approve-app-permissions.png)

5. 選取一個選項來處理新的應用程式權限要求，然後選取 [儲存]。

    ![用來處理新應用程式權限要求的選項](media/approve-app-settings.png)

    應用程式已通過核准並顯示在您的 IT 管理主控台中。 接下來，您可以[使用 Intune 同步處理 Android for Work 應用程式](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune)。 

## <a name="sync-an-android-for-work-app-with-intune"></a>使用 Intune 同步處理 Android for Work 應用程式

如果您已核准商店中的某個應用程式，但未在 [行動應用程式] 工作負載的 [授權的應用程式] 節點中看到它，請以如下方式強制立即同步：

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務] > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選取 [行動應用程式]。
4. 在 [行動應用程式] 工作負載窗格的 [安裝] 底下，選取 [Android for Work]。
5. 在 [Android for Work] 窗格中選取 [同步處理]。  
    此頁面會更新上一次同步的時間和狀態。
6. 在 [行動應用程式] 工作負載窗格中，選取 [應用程式]。  
    會顯示新的、可用的 Android for Work 應用程式。

當此應用程式顯示在 [行動應用程式] 工作負載窗格的 [應用程式授權] 節點時，您就可以[像是指派任何其他應用程式一樣來指派它](/intune-azure/manage-apps/deploy-apps)。 您只能將應用程式指派給使用者的群組。

在您指派應用程式之後，它會安裝在您的目標裝置上， 而不會要求裝置的使用者核准安裝。

## <a name="manage-android-for-work-app-permissions"></a>管理 Android for Work 應用程式權限
Android for Work 會要求您在受控 Google Play Web 主控台核准應用程式，然後才能利用 Intune 同步應用程式並指派給使用者。 因為 Android for Work 可讓您以無訊息模式且自動地將這些應用程式推送到使用者的裝置，因此您必須代表所有使用者接受應用程式的權限。 使用者在安裝應用程式時不會看到任何應用程式權限，因此請務必閱讀並了解這些權限。

當應用程式開發人員發行含有已更新權限的新版本應用程式時，即使您已核准先前的權限，也不會自動接受那些權限。 執行舊版本應用程式的裝置仍可以繼續使用該應用程式。 但是，在核准新的權限之前，不會升級應用程式。 在您核准應用程式的新權限之前，未安裝該應用程式的裝置不會安裝應用程式。

### <a name="update-app-permissions"></a>更新應用程式權限

請定期造訪受管理的 Google Play 主控台來檢查新的權限。 您可以設定 Google Play 在需要新權限以使用核准的應用程式時，寄送電子郵件給您或其他使用者。 如果您指派了應用程式，並發現它並未安裝在裝置上，請執行下列步驟來檢查是否有新的權限：

1. 前往 [Google Play](http://play.google.com/work)。
2. 使用您用來發行及核准應用程式的 Google 帳戶登入。
3. 選取 [更新] 索引標籤，然後檢查任何應用程式是否需要更新。  
    任何列出的應用程式都需要新的權限，而且在套用新權限之前將不會指派。

或者，您可以設定 Google Play，以每個應用程式為基礎，自動核准應用程式權限。 

## <a name="working-with-a-line-of-business-app-from-the-google-play-for-work-store"></a>使用 Google Play for Work 商店的企業營運應用程式

1. 使用您用來設定 Intune 和 Android for Work 間連線的相同帳戶來登入 [Google Play Developer Console](https://play.google.com/apps/publish)。  
    如果您是第一次登入，則必須註冊並支付費用，才能成為 Google 開發人員計劃的會員。
2. 在主控台中，選取 [加入新的應用程式]。
3. 您可以透過用來將任何應用程式發行至 Google Play 商店的相同方式，來上傳及提供應用程式的相關資訊。 不過，您必須選取 [只讓我的組織 (<組織名稱>) 使用此應用程式]。

    ![只將應用程式提供給您組織使用](media/restrict.png)

    此作業可確保只有您的組織可以使用此應用程式，而不會在公用 Google Play 商店中提供。

    如需如何上傳及發行 Android 應用程式的詳細資訊，請參閱 [Google Developer Console 說明](https://support.google.com/googleplay/android-developer/answer/113469)。
4. 發行您的應用程式之後，使用您用來設定 Intune 和 Android for Work 間連線的相同帳戶來登入 [Google Play for Work 商店](https://play.google.com/work)。
5. 在商店的 [應用程式] 節點中，確認您可以看見自已發行的應用程式。  
    應用程式會自動通過核准，以與 Intune 同步處理。

## <a name="next-steps"></a>接下來的步驟

- [將應用程式指派給群組](apps-deploy.md) 

