---
title: 將受控 Google Play 應用程式指派給 Android Enterprise 裝置
titleSuffix: Microsoft Intune
description: 了解如何同步處理應用程式，並將應用程式從受控 Google Play 商店指派給 Android Enterprise 裝置。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbcc777cc6d8b803c502d847114ef7cff04ceb26
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725331"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>使用 Intune 將受控 Google Play 應用程式新增至 Android Enterprise 裝置

受控 Google Play 是 Google 的企業應用程式商店，也是適用於 Android Enterprise 之應用程式的唯一來源。 您可以使用 Intune 來針對任何 Android Enterprise 案例 (包括工作設定檔、專用和完全受控註冊) 透過受控 Google Play 來協調應用程式部署。 將受控 Google Play 應用程式新增至 Intune 的方式，不同於針對非 Android Enterprise 新增 Android 應用程式的方式。 商店應用程式、企業營運 (LOB) 應用程式，以及 Web 應用程式會核准於或新增至受控 Google Play 中，然後再同步處理到 Intune，以使它們會出現在用戶端應用程式清單中。 一旦它們出現在用戶端應用程式清單中，您就能以和管理任何其他應用程式指派相同的方式來管理受控 Google Play 應用程式。

為了讓您能夠輕鬆地設定並使用 Android Enterprise 管理，在將您的 Intune 租用戶連線至受控 Google Play 之後，Intune 便會將四個通用的 Android Enterprise 相關應用程式自動新增到 Intune 管理主控台。 這四個應用程式如下所示：

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - 用於 Android 企業完全受控案例。 此應用程式會在裝置註冊程序期間自動安裝到完全受控裝置上。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 協助您登入帳戶 (若您使用雙重要素驗證的話)。 此應用程式會在裝置註冊程序期間自動安裝到完全受控裝置上。
- **[Intune 公司入口網站](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - 用於應用程式保護原則 (APP) 與 Android 企業公司設定檔案例。
- **[Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise)** - 用於 Android Enterprise 專用的多應用程式 Kiosk 案例。 IT 系統管理員應該建立指派，以在要用於多應用程式 Kiosk 案例的專用裝置上安裝此應用程式。

>[!NOTE]
>當使用者註冊其 Android Enterprise 完全受控裝置時，系統會自動安裝 Intune 公司入口網站應用程式，且使用者可能可以看到該應用程式的圖示。 如果使用者嘗試啟動 Intune 公司入口網站應用程式，系統會將該使用者重新導向至 Microsoft Intune 應用程式，而公司入口網站應用程式圖示隨後將會隱藏。

## <a name="before-you-start"></a>開始之前
- 確定您已將 Intune 租用戶連線到受控 Google Play。  如需詳細資訊，請參閱[將您的 Intune 帳戶連結到受控 Google Play 帳戶](../enrollment/connect-intune-android-enterprise.md)。
- 如果您想要註冊工作設定檔裝置，請確定您已在 Azure 入口網站的 [裝置註冊]  工作負載中設定 Intune 與 Android 工作設定檔以搭配使用。 如需詳細資訊，請參閱[註冊 Android 裝置](../enrollment/android-work-profile-enroll.md)。

>[!NOTE]
>當您使用 Microsoft Intune 時，建議使用 Microsoft Edge 或 Google Chrome 瀏覽器。

## <a name="managed-google-play-app-types"></a>受控 Google Play 應用程式類型
受控 Google Play 提供三種應用程式類型：

* **受控 Google Play 商店應用程式**：已在 Play Store 中正式推出的公用應用程式。 透過瀏覽您想要管理的應用程式並核准它們，然後將它們同步處理至 Intune，來在 Intune 中管理這些應用程式。
* **受控 Google Play 私人應用程式**：這些是由 Intune 系統管理員發佈至受控 Google Play 的 LOB 應用程式。  這些是私人應用程式，且僅可供您的 Intune 租用戶使用。 這是使用受控 Google Play 和 Android Enterprise 來管理和部署 LOB 應用程式的方式。
* **受控 Google Play 網頁連結**：具有可部署至 Android Enterprise 裝置之 IT 系統管理員定義圖示的網頁連結。 這些會顯示於裝置的應用程式清單中，就像一般應用程式一樣。

## <a name="managed-google-play-store-apps"></a>受控 Google Play 商店應用程式
有兩種方式可以用來使用 Intune 瀏覽和核准受控 Google Play 商店應用程式：

1. 直接在 Intune 主控台中：在 Intune 內裝載的檢視中瀏覽及核准商店應用程式。 這會在 Intune 主控台中直接開啟，而且不需要您使用不同的帳戶重新驗證。
1. 在受控 Google Play 主控台中：您可以選擇直接開啟受控 Google Play 主控台，並在該處核准應用程式。 如需詳細資訊，請參閱[使用 Intune 同步處理受控 Google Play 應用程式](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune)。  這需要使用您用來將 Intune 租用戶連線到受控 Google Play 的帳戶進行個別登入。


### <a name="add-a-managed-google-play-store-app-directly-in-the-intune-console"></a>在 Intune 主控台中直接新增受控 Google Play 商店應用程式

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在 [Intune]  窗格中，選取 [用戶端應用程式]   > [應用程式]  。
5. 在 [應用程式]  窗格中，選取 [新增]  。
6. 在 [應用程式類型]  下拉式清單方塊中，選取 [受控的 Google Play]  。
7. 選取 [受控的 Google Play - 開啟]  來開啟受控 Google Play 目錄。
7. 在 Google Play 目錄中選取 [搜尋 Play 商店]  。
8. 使用搜尋方塊來搜尋您想要管理的應用程式。
9. 按一下 [核准]  來在受控 Google Play 中核准該應用程式，然後按一下 [核准]  來接受應用程式權限。
10. 在 [核准設定] 視窗中選取 [在應用程式要求新權限時保持核准]  ，然後按一下 [儲存]  。 如果您不選擇此選項，當應用程式開發人員發佈新的更新時，您便必須手動核准任何新的權限。 這會導致應用程式的安裝和更新停止，直到權限被核准為止。 基於此原因，建議選取自動核准新權限的選項。 
11. 按一下 [確定]  以包含您已核准的應用程式。
12. 按一下 [應用程式]  窗格上的 [同步]  ，以與受控的 Google Play 服務進行同步處理。

### <a name="add-a-managed-google-play-store-app-in-the-managed-google-play-console-alternative"></a>在受控 Google Play 主控台中新增受控 Google Play 商店應用程式 (替代方法)
如果您希望將受控 Google Play 應用程式與 Intune 同步處理，而不是使用 Intune 直接新增，請使用下列步驟。

> [!IMPORTANT]
> 下面提供的資訊是使用 Intune 新增受控 Google Play 應用程式的另一種方法，如上所述。

1. 前往[受控 Google Play 商店](https://play.google.com/work)。 使用您用來設定 Intune 與 Android Enterprise 之間連線的相同帳戶進行登入。
2. 搜尋市集並選取您要使用 Intune 指派的應用程式。
3. 在顯示應用程式的頁面上，選取 [核准]  。  
    在下列範例中，已經選擇 Microsoft Excel 應用程式。

    ![受控 Google Play 商店中的 [核准] 按鈕](./media/apps-add-android-for-work/approve.png)

   應用程式視窗隨即開啟，要求您授權讓應用程式執行各種作業。

4. 選取 [核准]  接受應用程式權限，並繼續作業。

    ![應用程式權限的 [核准] 按鈕](./media/apps-add-android-for-work/approve-app-permissions.png)

5. 選取一個選項來處理新的應用程式權限要求，然後選取 [儲存]  。

    ![用來處理新應用程式權限要求的選項](./media/apps-add-android-for-work/approve-app-settings.png)

    應用程式已通過核准並顯示在您的 IT 管理主控台中。 接下來，您可以[使用 Intune 同步處理 Android 工作設定檔應用程式](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune)。

## <a name="managed-google-play-private-lob-apps"></a>受控 Google Play 私人 (LOB) 應用程式

有兩種方式可將 LOB 應用程式新增至受控 Google Play：

1. 直接在 Intune 主控台中：這讓您藉由直接在 Intune 內只提交應用程式 APK 和標題來新增 LOB 應用程式。 此方法不需要您擁有 Google 開發人員帳戶，也不需要向 Google 支付註冊為開發人員的費用。  此方法較為簡單，而且步驟數大幅減少，可在短短十分鐘內使 LOB 應用程式可供管理。
1. 在 Google Play 開發人員控制台中：如果您有 Google 開發人員帳戶，或是想要設定僅在 Google Play 開發人員控制台中提供使用的進階散發功能 (例如新增其他應用程式螢幕擷取畫面)，則可以使用 [Google Play 開發人員控制台](https://play.google.com/apps/publish)。 

### <a name="managed-google-play-private-lob-app-publishing-directly-in-the-intune-console"></a>直接在 Intune 主控台中發佈受控 Google Play 私人 (LOB) 應用程式

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在 [Intune]  窗格中，選取 [用戶端應用程式]   > [應用程式]  。
5. 在 [應用程式]  窗格中，選取 [新增]  。
6. 在 [應用程式類型]  下拉式清單方塊中，選取 [受控的 Google Play]  。
7. 選取 [受控的 Google Play - 開啟]  來開啟受控 Google Play 目錄。
7. 在 Google Play 目錄中，選取 [私人應用程式]  。
7. 按一下 [+]  按鈕以新增應用程式
8. 針對應用程式提交應用程式標題和 APK 套件
9. 按一下 [建立] 
9. 如果您已完成新增應用程式，請關閉 [受控的 Google Play] 窗格
12. 按一下 [應用程式]  窗格上的 [同步]  ，以與受控的 Google Play 服務進行同步處理。 請注意，私人應用程式可能需要幾分鐘的時間，才能進行同步處理。如果它並未在您第一次執行同步處理時出現，請等候幾分鐘，然後起始新的同步處理。

如需受控 Google Play 私人應用程式的詳細資訊 (包括常見問題集)，請參閱 Google 的支援文章： https://support.google.com/googleplay/work/answer/9146439 \(英文\)

>[!NOTE]
>使用此方法新增的私人應用程式絕不能設為公用。 只有在您確定此應用程式對於您的組織一律會是私用時，才使用此發佈選項。
  

### <a name="managed-google-play-private-lob-app-publishing-using-the-google-developer-console"></a>使用 Google 開發人員控制台發佈受控 Google Play 私人 (LOB) 應用程式

1. 使用您用來設定 Intune 與 Android Enterprise 之間連線的相同帳戶來登入 [Google Play 開發人員控制台](https://play.google.com/apps/publish)。  
    如果您是第一次登入，則必須註冊並支付費用，才能成為 Google 開發人員計劃的會員。
2. 在主控台中，選取 [加入新的應用程式]  。
3. 您可以透過用來將任何應用程式發行至 Google Play 商店的相同方式，來上傳及提供應用程式的相關資訊。 不過，您必須選取 [只讓我的組織 (<組織名稱>) 使用此應用程式]  。

    ![只將應用程式提供給您組織使用](./media/apps-add-android-for-work/restrict.png)

    這項作業只會將應用程式提供給您的組織使用。 在公用 Google Play 商店上則不提供該應用程式。

    如需如何上傳及發行 Android 應用程式的詳細資訊，請參閱 [Google Developer Console 說明](https://support.google.com/googleplay/android-developer/answer/113469)。
4. 發佈您的應用程式之後，使用您用來設定 Intune 與 Android Enterprise 之間連線的相同帳戶來登入[受控 Google Play 商店](https://play.google.com/work)。
5. 在商店的 [應用程式]  節點中，確認您可以看見自已發行的應用程式。  
    應用程式會自動通過核准，以與 Intune 同步處理。

## <a name="managed-google-play-web-links"></a>受控 Google Play 網頁連結

受控 Google Play 網頁連結是可安裝且可管理的，就像其他 Android 應用程式一樣。 安裝在裝置上時，它們將會與使用者已安裝的其他應用程式一起出現在他們的應用程式清單中。 點選時，它們將會在裝置的瀏覽器中啟動。

網頁連結將會搭配 Microsoft Edge 或您選擇部署的任何其他瀏覽器應用程式開啟。 務必至少將一個瀏覽器應用程式部署至裝置，來讓網頁連結可以正確開啟。 不過，網頁連結可用的所有 [顯示]  選項 (全螢幕、獨立及最基本的 UI) 都只能搭配 Chrome 瀏覽器運作。 

> [!IMPORTANT]
> 在本文件發行時，有一個已知的 Google 錯誤會防止網頁連結搭配 Chrome 以外的瀏覽器在裝置上開啟。 Google 已致力於修正此錯誤。  在 Microsoft 已確認 Google 已發佈其修正後，將會移除此通知。

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在 [Intune]  窗格中，選取 [用戶端應用程式]   > [應用程式]  。
5. 在 [應用程式]  窗格中，選取 [新增]  。
6. 在 [應用程式類型]  下拉式清單方塊中，選取 [受控的 Google Play]  。
7. 選取 [受控的 Google Play - 開啟]  來開啟受控 Google Play 目錄。
7. 在 Google Play 目錄中，選取 [Web 應用程式]  。
7. 按一下 [+]  按鈕以新增應用程式
7. 輸入必要的資訊，然後按一下 [建立] 
7. 如果您已完成新增應用程式，請關閉 [受控的 Google Play] 窗格
12. 按一下 [應用程式]  窗格上的 [同步]  ，以與受控的 Google Play 服務進行同步處理。 請注意，私人應用程式可能需要幾分鐘的時間，才能進行同步處理。如果它並未在您第一次執行同步處理時出現，請等候幾分鐘，然後起始新的同步處理。

## <a name="sync-a-managed-google-play-app-with-intune"></a>使用 Intune 同步處理受控 Google Play 應用程式

如果您已核准商店中的某個應用程式，但它並未出現在 [用戶端應用程式]  工作負載中，請以下述方式強制立即同步：

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在 [Intune]  窗格中，選取 [用戶端應用程式]  。
4. 在 [用戶端應用程式]  工作負載窗格的 [安裝]  底下，選取 [受控 Google Play]  。
5. 在 [受控 Google Play]  窗格中，選擇 [重新整理]  。  
    此頁面會更新上一次同步的時間和狀態。
6. 在 [用戶端應用程式]  工作負載窗格中，選取 [應用程式]  。  
    隨即會顯示新的可用受控 Google Play 應用程式。

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices"></a>將受控 Google Play 應用程式指派給 Android Enterprise 工作設定檔裝置

當此應用程式顯示在 [用戶端應用程式]  工作負載窗格的 [應用程式授權]  節點中時，您就可以透過將應用程式指派給使用者群組，[如同指派其他應用程式一樣予以指派](/intune-azure/manage-apps/deploy-apps)。

在您指派應用程式之後，它會安裝 (或可供安裝) 在目標使用者的裝置上。 而不會要求裝置的使用者核准安裝。 如需 Android Enterprise 工作設定檔裝置的詳細資訊，請參閱[設定 Android Enterprise 工作設定檔裝置的註冊](../enrollment/android-work-profile-enroll.md)。 

> [!NOTE] 
> 只有已指派的應用程式才會為使用者顯示在受控 Google Play 商店中。 因此，這是系統管理員在搭配受控 Google Play 設定應用程式時應採取的重要步驟。

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-fully-managed-devices"></a>將受控 Google Play 應用程式指派給 Android Enterprise 完全受控裝置

[Android Enterprise 完全受控裝置](../enrollment/android-fully-managed-enroll.md)為與單一使用者建立關聯的公司擁有裝置，並僅供工作而非個人用途使用。 完全受控裝置上的使用者可以從其裝置上的受控 Google Play 應用程式取得可供他們使用的公司應用程式。

根據預設，Android Enterprise 完全受控裝置將不會允許員工安裝組織未核准的任何應用程式。 此外，員工也無法違反原則地移除任何已安裝的應用程式。 如果您想讓使用者存取完整的 Google Play 商店來安裝應用程式，而非只能存取受控 Google Play 商店中已核准的應用程式，您可以將 [允許存取 Google Play 商店中的所有應用程式]  設定為 [允許]  。 透過此設定，使用者便可以使用其公司帳戶存取 Google Play 商店中的所有應用程式，不過購買可能會受限。 您可以透過允許使用者將帳戶新增至裝置，來移除受限購買限制。 這麼做將會讓使用者能夠使用個人帳戶從 Google Play 商店購買應用程式，以及進行應用程式內購買。 如需詳細資訊，請參閱[使用 Intune 來允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。 

> [!NOTE]
> 在上線期間，Microsoft Intune 應用程式和 Microsoft Authenticator 應用程式將會做為必要應用程式安裝到完全受控裝置上。 自動安裝這些應用程式將能提供條件式存取支援，且 Microsoft Intune 應用程式使用者將可以查看及解決合規性問題。 

## <a name="manage-android-enterprise-app-permissions"></a>管理 Android Enterprise 應用程式權限
Android Enterprise 會要求您先在受控 Google Play Web 主控台中核准應用程式，然後才能利用 Intune 同步處理它們並指派給使用者。 因為 Android Enterprise可讓您以無訊息模式且自動地將應用程式推送到使用者的裝置，因此您必須代表所有使用者接受應用程式權限。 使用者在安裝應用程式時不會看到任何應用程式權限，因此請務必了解這些權限。

當應用程式開發人員使用新版本應用程式更新權限時，即使您已核准先前的權限，也不會自動接受那些權限。 執行舊版本應用程式的裝置仍可以繼續使用該應用程式。 但是，在核准新的權限之前，不會升級應用程式。 在您核准應用程式的新權限之前，未安裝該應用程式的裝置不會安裝應用程式。 

### <a name="update-app-permissions"></a>更新應用程式權限

請定期造訪受管理的 Google Play 主控台來檢查新的權限。 您可以設定 Google Play 在需要新權限以使用核准的應用程式時，寄送電子郵件給您或其他使用者。 若您指派了應用程式，並發現它並未安裝在裝置上，請遵循下列步驟來檢查是否有新的權限：

1. 前往 [Google Play](https://play.google.com/work)。
2. 使用您用來發行及核准應用程式的 Google 帳戶登入。
3. 選取 [更新]  索引標籤，然後檢查任何應用程式是否需要更新。  
    任何列出的應用程式都需要新的權限，而且在套用新權限之前將不會指派。

或者，您可以設定 Google Play，以每個應用程式為基礎，自動核准應用程式權限。

## <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices"></a>Android Enterprise 工作設定檔裝置的其他受控 Google Play 應用程式報告

針對部署到 Android Enterprise 工作設定檔裝置的受控 Google Play 應用程式，您可以檢視裝置上所安裝應用程式的特定版本號碼。 這只適用於必要的應用程式。 


## <a name="delete-managed-google-play-apps"></a>刪除受控的 Google Play 應用程式
必要時，您可以從 Microsoft Intune 刪除受控的 Google Play 應用程式。 若要刪除受控的 Google Play 應用程式，請在 Azure 入口網站中開啟 Microsoft Intune，然後選取 [用戶端應用程式]   > [應用程式]  。 從應用程式清單，選取受控的 Google Play 應用程式右側的省略符號 (...)，然後從顯示的清單選取 [刪除]  。 當您從應用程式清單刪除受控 Google Play 應用程式時，會自動取消核准受控 Google Play 應用程式。

## <a name="android-enterprise-system-apps"></a>Android Enterprise 系統應用程式

您可以針對 [Android Enterprise 專用裝置](../enrollment/android-kiosk-enroll.md)或[完全受控裝置](../enrollment/android-fully-managed-enroll.md)啟用 Android Enterprise 系統應用程式。 如需新增 Android Enterprise 系統應用程式的詳細資訊，請參閱[將 Android Enterprise 系統應用程式新增至 Microsoft Intune](apps-ae-system.md)。

## <a name="next-steps"></a>後續步驟

- [將應用程式指派給群組](apps-deploy.md)
