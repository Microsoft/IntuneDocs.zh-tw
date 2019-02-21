---
title: 將受控 Google Play 應用程式指派給 Android Enterprise 裝置
titlesuffix: Microsoft Intune
description: 了解如何同步處理，並將應用程式從受控 Google Play 商店指派給 Android Enterprise 裝置。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/25/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba3e4ae88423183d5d0317dedb59715d2adb4e11
ms.sourcegitcommit: 5708ec1d7ae50494be44ed5064f150b636188c84
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56240022"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>使用 Intune 將受控 Google Play 應用程式新增至 Android Enterprise 裝置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android Enterprise 是適用於 Android 工作設定檔裝置、專用/kiosk 裝置及完全受控裝置的方案。 對於 Android 工作設定檔裝置來說，Android 企業是一組功能與服務，可將個人應用程式與資料和公司應用程式與資料分隔開來。 使用者以 Android 裝置進行工作時，Android 企業可提供額外的管理選項與隱私權。 Intune 可協助您將應用程式和設定部署到 Android 工作設定檔裝置，以確定公司及個人資訊各自分開。 您在 Android 工作設定檔裝置上安裝的所有應用程式都是來自受控 Google Play 商店。 將應用程式指派給 Android 工作設定檔裝置的方式，與您將應用程式指派給標準 Android 裝置的方式不同。 您需要登入商店、瀏覽所需的應用程式，並核准這些應用程式。 然後，該應用程式會出現在 Azure 入口網站的 [授權的應用程式] 節點中，而且您可以管理應用程式的指派，如同其他應用程式一樣。

此外，如果您已建立自己的企業營運 (LOB) 應用程式，則可以依照以下方式指派這些應用程式：
- 註冊一個 Google 開發人員帳戶，您就能夠在 Google Play 商店的私人區域發佈應用程式。
- 使用 Intune 同步應用程式。

## <a name="before-you-start"></a>開始之前

確定您已在 Azure 入口網站的 [裝置註冊] 工作負載中，設定 Intune 與 Android 工作設定檔搭配使用。 如需詳細資訊，請參閱[註冊 Android 裝置](android-work-profile-enroll.md)。

>[!NOTE]
>當您使用 Microsoft Intune 時，建議使用 Microsoft Edge 或 Google Chrome 瀏覽器。

## <a name="managed-google-play-app-type"></a>受控的 Google Play 應用程式類型
[受控的 Google Play] 應用程式類型可讓您將[受控 Google Play 應用程式](https://play.google.com/work/search?q=microsoft&c=apps)明確新增至 Intune。 身為 Intune 系統管理員，您現在可以在 Intune 中瀏覽、搜尋、核准、同步及指派已核准之受控的 Google Play 應用程式。  您不再需要另外瀏覽至受控的 Google Play 主控台，而且您不再需要重新驗證。

> [!NOTE]
> 如果您希望將受控 Google Play 應用程式與 Intune 同步處理，請參閱[將受控 Google Play 應用程式與 Intune 同步處理](apps-add-android-for-work.md#synchronize-a-managed-google-play-app-with-intune-alternative)

## <a name="add-a-managed-google-play-app-using-intune"></a>使用 Intune 新增受控 Google Play 應用程式

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務] > [Intune]。  
    Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選取 [用戶端應用程式] > [應用程式]。
5. 在 [應用程式] 窗格中，選取 [新增]。
6. 在 [應用程式類型] 下拉式清單方塊中，選取 [受控的 Google Play]。
7. 選取 [受控的 Google Play - 核准] 來開啟受控的 Google Play 目錄。
8. 使用搜尋方塊來搜尋想要包含的應用程式。
9. 按一下 [核准] 來在受控 Google Play 中核准該應用程式，然後按一下 [核准] 來接受應用程式權限。
10. 在 [核准設定] 視窗中選取 [在應用程式要求新權限時保持核准]，然後按一下 [儲存]。 如果您不選擇此選項，當應用程式開發人員發佈新的更新時，您便必須手動核准任何新的權限。  這會導致應用程式的安裝和更新停止，直到權限被核准為止。 基於此原因，建議選取自動核准新權限的選項。 
11. 按一下 [確定] 以包含您已核准的應用程式。
12. 按一下 [應用程式] 窗格上的 [同步]，以與受控的 Google Play 服務進行同步處理。

## <a name="synchronize-a-managed-google-play-app-with-intune-alternative"></a>使用 Intune 同步處理受控 Google Play 應用程式 (替代方法)
如果您希望將受控 Google Play 應用程式與 Intune 同步處理，而不是使用 Intune 直接新增，請使用下列步驟。

> [!IMPORTANT]
> 下面提供的資訊是使用 Intune 新增受控 Google Play 應用程式的另一種方法，如上所述。

### <a name="synchronize-an-app-from-the-managed-google-play-store"></a>與受控 Google Play 商店中的應用程式同步處理

1. 前往[受控 Google Play 商店](https://play.google.com/work)。 使用您用來設定 Intune 與 Android 企業間連線的相同帳戶進行登入。
2. 搜尋市集並選取您要使用 Intune 指派的應用程式。
3. 在顯示應用程式的頁面上，選取 [核准]。  
    在下列範例中，已經選擇 Microsoft Excel 應用程式。

    ![受控 Google Play 商店中的 [核准] 按鈕](media/approve.png)

   應用程式視窗隨即開啟，要求您授權讓應用程式執行各種作業。

4. 選取 [核准] 接受應用程式權限，並繼續作業。

    ![應用程式權限的 [核准] 按鈕](media/approve-app-permissions.png)

5. 選取一個選項來處理新的應用程式權限要求，然後選取 [儲存]。

    ![用來處理新應用程式權限要求的選項](media/approve-app-settings.png)

    應用程式已通過核准並顯示在您的 IT 管理主控台中。 接下來，您可以[使用 Intune 同步處理 Android 工作設定檔應用程式](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune)。

### <a name="sync-a-managed-google-play-app-with-intune"></a>使用 Intune 同步處理受控 Google Play 應用程式

如果您已核准商店中的某個應用程式，但未出現在 [用戶端應用程式] 工作負載的 [授權的應用程式] 節點中，請以下述方式強制立即同步：

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務] > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選取 [用戶端應用程式]。
4. 在 [用戶端應用程式] 工作負載窗格的 [安裝] 底下，選取 [受控 Google Play]。
5. 在 [受控 Google Play] 窗格中，選擇 [重新整理]。  
    此頁面會更新上一次同步的時間和狀態。
6. 在 [用戶端應用程式] 工作負載窗格中，選取 [應用程式]。  
    隨即會顯示新的可用受控 Google Play 應用程式。

## <a name="assigning-the-managed-google-play-app"></a>指派受控 Google Play 應用程式

當此應用程式顯示在 [用戶端應用程式] 工作負載窗格的 [應用程式授權] 節點時，您就可以透過將應用程式指派給使用者群組，[如同指派其他應用程式一樣予以指派](/intune-azure/manage-apps/deploy-apps)。

在您指派應用程式之後，它會安裝在您的目標裝置上， 而不會要求裝置的使用者核准安裝。

## <a name="manage-android-enterprise-app-permissions"></a>管理 Android 企業應用程式權限
Android 企業會要求您在受控 Google Play Web 主控台核准應用程式，然後才能利用 Intune 同步處理應用程式並指派給使用者。 因為 Android 企業可讓您以無訊息模式且自動地將這些應用程式推送到使用者的裝置，因此您必須代表所有使用者接受應用程式的權限。 使用者在安裝應用程式時不會看到任何應用程式權限，因此請務必了解這些權限。

當應用程式開發人員使用新版本應用程式更新權限時，即使您已核准先前的權限，也不會自動接受那些權限。 執行舊版本應用程式的裝置仍可以繼續使用該應用程式。 但是，在核准新的權限之前，不會升級應用程式。 在您核准應用程式的新權限之前，未安裝該應用程式的裝置不會安裝應用程式。

### <a name="update-app-permissions"></a>更新應用程式權限

請定期造訪受管理的 Google Play 主控台來檢查新的權限。 您可以設定 Google Play 在需要新權限以使用核准的應用程式時，寄送電子郵件給您或其他使用者。 若您指派了應用程式，並發現它並未安裝在裝置上，請遵循下列步驟來檢查是否有新的權限：

1. 前往 [Google Play](https://play.google.com/work)。
2. 使用您用來發行及核准應用程式的 Google 帳戶登入。
3. 選取 [更新] 索引標籤，然後檢查任何應用程式是否需要更新。  
    任何列出的應用程式都需要新的權限，而且在套用新權限之前將不會指派。

或者，您可以設定 Google Play，以每個應用程式為基礎，自動核准應用程式權限。

## <a name="working-with-a-line-of-business-app-from-the-managed-google-play-store"></a>使用受控 Google Play 商店的企業營運應用程式

1. 使用您用來設定 Intune 與 Android 企業間連線的相同帳戶來登入 [Google Play Developer Console](https://play.google.com/apps/publish)。  
    如果您是第一次登入，則必須註冊並支付費用，才能成為 Google 開發人員計劃的會員。
2. 在主控台中，選取 [加入新的應用程式]。
3. 您可以透過用來將任何應用程式發行至 Google Play 商店的相同方式，來上傳及提供應用程式的相關資訊。 不過，您必須選取 [只讓我的組織 (<組織名稱>) 使用此應用程式]。

    ![只將應用程式提供給您組織使用](media/restrict.png)

    此作業只會將應用程式提供給您的組織使用。 在公用 Google Play 商店上則不提供該應用程式。

    如需如何上傳及發行 Android 應用程式的詳細資訊，請參閱 [Google Developer Console 說明](https://support.google.com/googleplay/android-developer/answer/113469)。
4. 發佈您的應用程式之後，使用您用來設定 Intune 與 Android 企業間連線的相同帳戶來登入[受控 Google Play 商店](https://play.google.com/work)。
5. 在商店的 [應用程式] 節點中，確認您可以看見自已發行的應用程式。  
    應用程式會自動通過核准，以與 Intune 同步處理。

## <a name="delete-managed-google-play-apps"></a>刪除受控的 Google Play 應用程式
必要時，您可以從 Microsoft Intune 刪除受控的 Google Play 應用程式。 若要刪除受控的 Google Play 應用程式，請在 Azure 入口網站中開啟 Microsoft Intune，然後選取 [用戶端應用程式] > [應用程式]。 從應用程式清單，選取受控的 Google Play 應用程式右側的省略符號 (...)，然後從顯示的清單選取 [刪除]。 當您從應用程式清單刪除受控 Google Play 應用程式時，會自動取消核准受控 Google Play 應用程式。

## <a name="next-steps"></a>後續步驟

- [將應用程式指派給群組](apps-deploy.md)
