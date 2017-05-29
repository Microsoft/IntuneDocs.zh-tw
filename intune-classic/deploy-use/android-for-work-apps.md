---
title: "將應用程式部署至 Android for Work 裝置 | Microsoft Docs"
description: "您可以使用本主題進行同步處理，再將應用程式從 Google Play for Work 商店部署至Android for Work 裝置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd0bbd90-d3fe-4efc-83fd-d1f3f86800d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3b608d42f04b9fce457b6b61587d05ab5d59bb0a
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-deploy-apps-to-android-for-work-devices-with-intune"></a>如何使用 Intune 將應用程式部署至 Android for Work 裝置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

您可以透過用來部署至 Android 裝置的不同方式，將應用程式部署至 Android for Work 裝置。 您針對 Android for Work 安裝的所有應用程式都是來自 Google Play for Work 商店。 您可以登入商店、瀏覽所需的應用程式並核准這些應用程式。
應用程式接著會出現在 Intune 主控台的 [大量採購應用程式] 節點中。 您可以在這裡透過用來部署任何其他應用程式的相同方式，來管理應用程式的部署。

此外，如果您已建立自己的企業營運 (LOB) 應用程式，您可以部署這些應用程式。 若要這樣做，您需要註冊 Google 開發人員帳戶，該帳戶可讓您將應用程式發行至 Google Play 商店中的私人區域，再與 Intune 進行同步處理。

## <a name="before-you-start"></a>開始之前

1. 確定您已在 Intune 主控台的 [管理] 索引標籤中，設定 Intune 與 Android for Work 搭配使用。

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>與 Google Play for Work 商店中的應用程式同步處理


1. 移至 [Google Play for Work 商店](https://play.google.com/work)。 使用您用來設定 Intune 和 Android for Work 間連線的相同帳戶進行登入。
2. 搜尋商店以尋找您要使用 Intune 部署的應用程式。
3. 在您選擇的應用程式頁面上，選擇 [核准]。 在此範例中，您已選擇 Microsoft Excel 應用程式。<br>
  ![核准應用程式範例](media/approve.png)
4. 應用程式視窗隨即開啟，要求您授權讓應用程式執行各種作業。 您必須選擇 [核准] 才能繼續。<br>
  ![核准應用程式權限範例](media/approve-app-permissions.png)
5. 不久，您將會看到一則確認訊息，指出此應用程式已經過核准，而且可在您的 IT 系統管理員主控台中使用。

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>從 Google Play for Work 商店發行企業營運應用程式，再進行同步處理

1. 移至 Google Play Developer Console ([play.google.com/apps/publish](https://play.google.com/apps/publish))。
2. 使用您用來設定 Intune 和 Android for Work 間連線的相同帳戶進行登入。 如果您是第一次登入，您必須註冊並支付費用，才能成為 Google 開發人員計劃的會員。
3. 在主控台中，選擇 「Add new application」 \(加入新的應用程式)。
4. 您可以透過用來將任何應用程式發行至 Google Play 商店的相同方式，來上傳及提供應用程式的相關資訊。 不過，您必須選取 **「只讓我的組織 (<*組織名稱*>) 使用此應用程式」** 設定，如下所示。<br>
  ![只將應用程式提供給您組織使用的選項](media/restrict.png)<br>
這可確保只有您的組織可以使用此應用程式，而不會在公用 Google Play 商店中提供。
如需如何上傳及發行 Android 應用程式的詳細資訊，請參閱 [Google Developer Console Help](https://support.google.com/googleplay/android-developer/answer/113469)。
5. 在您發行應用程式之後，移至 [Google Play for Work 商店](https://play.google.com/work)。 使用您用來設定 Intune 和 Android for Work 間連線的相同帳戶進行登入。
6. 在商店的 [應用程式] 節點中，確認您可以看見已發行的應用程式。 請注意，它已經過自動核准，可與 Intune 同步處理。

## <a name="deploy-an-android-for-work-app"></a>部署 Android for Work 應用程式

如果您已核准商店中的某個應用程式，但尚未在 [應用程式] 工作區的 [大量採購應用程式] 節點中看到此應用程式，您可以強制立即同步，如下所示：

1. 在 [Intune 系統管理員主控台](https://manage.microsoft.com)中，選擇 [管理] > [行動裝置管理] > [Android for Work]。
2. 在 [Android for Work 行動裝置管理設定] 頁面上，選擇 [立即同步]。
3. 此頁面也會顯示上一次同步的時間和狀態。

當此應用程式顯示在 [應用程式] 工作區的 [大量採購應用程式] 節點時，您就可以[像是任何其他應用程式一樣來將它部署](deploy-apps-in-microsoft-intune.md)。 您只能將應用程式部署給使用者群組。 目前，您只能選取 [必要] 和 [解除安裝] 動作。

將應用程式部署為 [可用] 的能力，採用新的分組和目標設定體驗。 新佈建的 Intune 服務帳戶將可在發行時使用此功能。 現有的 Intune 客戶在其租用戶移轉至 Intune Azure 入口網站後，也可以使用這項功能。 歡迎現有的 Intune 客戶在其租用戶完成移轉之前，先建立 Intune 試用帳戶來規劃及測試此功能。

在您部署應用程式之後，此應用程式將會安裝在您的目標裝置上。 而不會要求裝置的使用者進行核准。

## <a name="manage-app-permissions"></a>管理應用程式權限
Android for Work 會要求您在 Google 受管理的 Play Web 主控台核准應用程式，然後才將它們同步到 Intune 並部署到使用者。  因為 Android for Work 可讓您以無訊息模式且自動地將這些應用程式推送到使用者的裝置，您必須代表您所有的使用者接受應用程式的權限。  使用者在安裝時將不會看到任何應用程式權限，因此請務必閱讀並了解這些權限。

當應用程式開發人員發行含有已更新權限的新版本應用程式時，即使您已核准先前的權限，也不會自動核准那些權限。 執行舊版應用程式的裝置仍然可以使用應用程式，但應用程式將不會升級，直到已核准新的權限為止。 在您核准應用程式的新權限之前，未安裝該應用程式的裝置將無法安裝應用程式。

### <a name="how-to-update-app-permissions"></a>如何更新應用程式權限

您應該定期造訪受管理的 Google Play 主控台來檢查新的權限。 如果您部署應用程式並觀察到它並未安裝在裝置上，請依下列步驟檢查是否有新的權限：

1. 造訪 http://play.google.com/work
2. 使用您用來發行及核准應用程式的 Google 帳戶登入。
3. 瀏覽 [更新] 索引標籤以查看是否有任何應用程式需要更新。  任何列出的應用程式都需要新的權限，而且在更新權限前將不會部署。  

