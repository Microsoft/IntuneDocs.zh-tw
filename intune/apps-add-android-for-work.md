---
title: "將應用程式指派給 Android for Work 裝置"
titlesuffix: Azure portal
description: "您可以使用本主題進行同步處理，再將應用程式從 Google Play for Work 商店指派給 Android for Work 裝置。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 06/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 803f1475a220e52a0f7d8a41d58f0a5337ff6555
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-assign-apps-to-android-for-work-devices-with-intune"></a>如何使用 Intune 將應用程式指派至 Android for Work 裝置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

將應用程式指派至 Android for Work 裝置的方式，與您將應用程式指派至標準 Android 裝置的方式不同。 您針對 Android for Work 安裝的所有應用程式都是來自 Google Play for Work 商店。 您可以登入商店、瀏覽所需的應用程式並核准這些應用程式。
應用程式接著會出現在 Azure 入口網站的 [授權的應用程式] 節點中。 您可以在這裡管理應用程式的指派，方式與指派任何其他應用程式相同。

此外，如果您已建立自己的企業營運 (LOB) 應用程式，則可以依照以下方式指派這些應用程式：
- 註冊一個 Google 開發人員帳戶，您就能夠在 Google Play 商店的私人區域發佈應用程式。
- 使用 Intune 同步應用程式。

## <a name="before-you-start"></a>開始之前

確定您已在 Azure 入口網站的 [裝置註冊] 工作負載中，設定 Intune 與 Android for Work 搭配使用。

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>與 Google Play for Work 商店中的應用程式同步處理

1. 移至 [Google Play for Work 商店](https://play.google.com/work)。 使用您用來設定 Intune 和 Android for Work 間連線的相同帳戶進行登入。
2. 搜尋商店以尋找您要使用 Intune 指派的應用程式。
3. 在您選擇的應用程式頁面上，選擇 [核准]。 在此範例中，您已選擇 Microsoft Excel 應用程式。<br>
  ![核准應用程式範例](media/approve.png)
4. 應用程式視窗隨即開啟，要求您授權讓應用程式執行各種作業。 請選擇 [核准] 來繼續。<br>
  ![核准應用程式權限範例](media/approve-app-permissions.png)
5. 應用程式已通過核准並顯示在您的 IT 管理主控台中。

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>從 Google Play for Work 商店發行企業營運應用程式，再進行同步處理

1. 移至 Google Play Developer Console ([play.google.com/apps/publish](https://play.google.com/apps/publish))。
2. 使用您用來設定 Intune 和 Android for Work 間連線的相同帳戶進行登入。 如果您是第一次登入，您必須註冊並支付費用，才能成為 Google 開發人員計劃的會員。
3. 在主控台中，選擇 「Add new application」 \(加入新的應用程式)。
4. 您可以透過用來將任何應用程式發行至 Google Play 商店的相同方式，來上傳及提供應用程式的相關資訊。 不過，您必須選取 [只讓我的組織 (<*組織名稱*>) 使用此應用程式]**** 設定：<br>
  ![只將應用程式提供給您組織使用的選項](media/restrict.png)<br>
此作業可確保只有您的組織可以使用此應用程式，而不會在公用 Google Play 商店中提供。
如需如何上傳及發行 Android 應用程式的詳細資訊，請參閱 [Google Developer Console Help](https://support.google.com/googleplay/android-developer/answer/113469)。
5. 在您發行應用程式之後，移至 [Google Play for Work 商店](https://play.google.com/work)。 使用您用來設定 Intune 和 Android for Work 間連線的相同帳戶進行登入。
6. 在商店的 [應用程式] 節點中，確認您可以看見已發行的應用程式。 應用程式會自動通過核准，以與 Intune 同步處理。

## <a name="assign-an-android-for-work-app"></a>指派 Android for Work 應用程式

如果您已核准商店中的某個應用程式，但未在 [行動應用程式] 工作負載的 [授權的應用程式] 節點中看到它，請以如下方式強制立即同步：

1. 登入 Azure 入口網站。
2. 在 [Intune] 刀鋒視窗上，選擇 [行動應用程式]。
3. 在 [行動應用程式] 工作負載中，選擇 [安裝] > [Android for Work]。
4. 在 [Android for Work] 刀鋒視窗上，選擇 [立即同步]。
5. 此頁面也會顯示上一次同步的時間和狀態。

當此應用程式顯示在 [行動應用程式] 工作負載的 [授權的應用程式] 節點時，您就可以[像是指派任何其他應用程式一樣來指派它](/intune-azure/manage-apps/deploy-apps)。 您只能將應用程式指派給使用者的群組。

在您指派應用程式之後，它將會安裝在您的目標裝置上， 而不會要求裝置的使用者核准安裝。

## <a name="manage-android-for-work-app-permissions"></a>管理 Android for Work 應用程式權限
Android for Work 會要求您在 Google 受管理的 Play Web 主控台核准應用程式，然後才能將應用程式同步到 Intune 並指派給使用者。  因為 Android for Work 可讓您以無訊息模式且自動地將這些應用程式推送到使用者的裝置，您必須代表您所有的使用者接受應用程式的權限。  使用者在安裝時不會看到任何應用程式權限，因此請務必閱讀並了解這些權限。

當應用程式開發人員發行含有已更新權限的新版本應用程式時，即使您已核准先前的權限，也不會自動核准那些權限。 執行舊版本應用程式的裝置仍可以繼續使用該應用程式。 但是，在核准新的權限之前，不會升級應用程式。 在您核准應用程式的新權限之前，未安裝該應用程式的裝置不會安裝應用程式。

### <a name="how-to-update-app-permissions"></a>如何更新應用程式權限

請定期造訪受管理的 Google Play 主控台來檢查新的權限。 您可以設定 Google Play 在需要新權限以使用核准的應用程式時，寄送電子郵件給您或其他使用者。 如果您指派了應用程式，並發現它並未安裝在裝置上，請依下列步驟檢查是否有新的權限：

1. 造訪 http://play.google.com/work
2. 使用您用來發行及核准應用程式的 Google 帳戶登入。
3. 瀏覽 [更新] 索引標籤以查看是否有任何應用程式需要更新。  任何列出的應用程式都需要新的權限，而且在套用新權限之前將不會指派。  

或者，您可以設定 Google Play，以每個應用程式為基礎，自動核准應用程式權限。 



