---
title: 將受控 Google Play 應用程式指派給 Android Enterprise 裝置
titleSuffix: Microsoft Intune
description: 了解如何同步應用程式，並將應用程式從受控 Google Play 商店指派給 Android Enterprise 裝置。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 138bf192f5244eb6e44a6be96af3cc15c47bdc76
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755386"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>使用 Intune 將受控 Google Play 應用程式新增至 Android Enterprise 裝置

受控 Google Play 是 Google 的企業應用程式商店，也是適用於 Android Enterprise 之應用程式的唯一來源。 您可以使用 Intune，針對任何 Android Enterprise 案例 (包括工作設定檔、專用和完全受控註冊) 透過受控 Google Play 來協調應用程式部署。 將受控 Google Play 應用程式新增至 Intune 的方式，不同於針對非 Android Enterprise 新增 Android 應用程式的方式。 商店應用程式、企業營運 (LOB) 應用程式，以及 Web 應用程式會核准於或新增至受控 Google Play 中，然後再同步到 Intune，以使它們出現在用戶端應用程式清單中。 一旦它們出現在用戶端應用程式清單中之後，您就能以和管理任何其他應用程式指派相同的方式，來管理所有受控 Google Play 應用程式的指派。

為了讓您能夠更輕鬆地設定並使用 Android Enterprise 管理，在將您的 Intune 租用戶連線至受控 Google Play 之後，Intune 便會將四個通用的 Android Enterprise 相關應用程式自動新增到 Intune 管理主控台。 這四個應用程式如下所示：

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - 用於 Android 企業完全受控案例。 此應用程式會在裝置註冊程序中自動安裝到完全受控裝置上。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 協助您登入帳戶 (若您使用雙重要素驗證)。 此應用程式會在裝置註冊程序中自動安裝到完全受控裝置上。
- **[Intune 公司入口網站](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - 用於應用程式保護原則 (APP) 與 Android 企業公司設定檔案例。
- **[Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise)** - 用於 Android Enterprise 專用的多應用程式 Kiosk 案例。 IT 系統管理員應該建立指派，以在要用於多應用程式 Kiosk 案例的專用裝置上安裝此應用程式。

>[!NOTE]
>當終端使用者註冊其 Android Enterprise 完全受控裝置時，系統會自動安裝 Intune 公司入口網站應用程式，而終端使用者或許能夠看到該應用程式圖示。 如果終端使用者嘗試啟動 Intune 公司入口網站應用程式，系統會將終端使用者重新導向至 Microsoft Intune 應用程式，而公司入口網站應用程式圖示隨後將會隱藏。

## <a name="before-you-start"></a>在您開始使用 Intune 之前
- 確定您已將 Intune 租用戶連線到受控 Google Play。  如需詳細資訊，請參閱[將您的 Intune 帳戶連結到受控 Google Play 帳戶](../enrollment/connect-intune-android-enterprise.md)。
- 如果您想要註冊工作設定檔裝置，請確定您已在 Azure 入口網站的 [裝置註冊] 工作負載中，將 Intune 與 Android 工作設定檔設定為協同作業。  如需詳細資訊，請參閱[註冊 Android 裝置](../enrollment/android-work-profile-enroll.md)。

>[!NOTE]
>當您使用 Microsoft Intune 時，建議使用 Microsoft Edge 或 Google Chrome 瀏覽器。

## <a name="managed-google-play-app-types"></a>受控 Google Play 應用程式類型
受控 Google Play 提供三種應用程式類型：

- **受控 Google Play 商店應用程式**：已在 Play Store 中正式推出的公用應用程式。 透過瀏覽您要管理的應用程式、核准它們，然後將它們同步至 Intune，以在 Intune 中管理這些應用程式。
- **受控 Google Play 私人應用程式**：這些是由 Intune 系統管理員發佈至受控 Google Play 的 LOB 應用程式。  這些都是私人應用程式，僅可供您的 Intune 租用戶使用。 這是使用受控 Google Play 和 Android Enterprise 來管理及部署 LOB 應用程式的方式。
- **受控 Google Play 網頁連結**：具有可部署至 Android Enterprise 裝置之 IT 系統管理員定義圖示的網頁連結。 這些會顯示於裝置的應用程式清單中，就像一般應用程式一樣。

## <a name="managed-google-play-store-apps"></a>受控 Google Play 商店應用程式
使用 Intune 瀏覽及核准受控 Google Play 商店應用程式的方式有兩種：

1. 直接在 Intune 主控台中：在 Intune 內裝載的檢視中瀏覽及核准商店應用程式。 這會在 Intune 主控台中直接開啟，而不需要您使用不同的帳戶重新驗證。
1. 在受控 Google Play 主控台中：您可以選擇直接開啟受控 Google Play 主控台，並在該處核准應用程式。 如需詳細資訊，請參閱[與 Intune 同步受控 Google Play 應用程式](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune)。  這要求您必須使用您用來將 Intune 租用戶連線到受控 Google Play 的帳戶進行個別登入。

### <a name="add-a-managed-google-play-store-app-directly-in-the-intune-console"></a>在 Intune 主控台中直接新增受控 Google Play 商店應用程式

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [所有應用程式]   > [新增]  。
3. 在 [選取應用程式類型]  窗格中，在可用的 [市集應用程式]  類型下，選取 [受控 Google Play 應用程式]  。
4. 按一下 [選取]  。 [受控的 Google Play]  應用程式市集隨即顯示。

    > [!NOTE]
    > 您的 Intune 租用戶帳戶必須連線到您的 Android Enterprise 帳戶以瀏覽受控 Google Play 商店應用程式。 如需詳細資訊，請參閱[將您的 Intune 帳戶連結到受控 Google Play 帳戶](../enrollment/connect-intune-android-enterprise.md)。

5. 選取應用程式以檢視應用程式詳細資料。
6. 在顯示應用程式的頁面上，按一下 [核准]  。 應用程式視窗隨即開啟，要求您授權讓應用程式執行各種作業。
7. 選取 [核准]  接受應用程式權限，並繼續作業。
8. 在 [核准設定]  索引標籤中選取 [在應用程式要求新權限時保持核准]  ，然後按一下 [完成]  。 

    > [!IMPORTANT]
    > 如果您不選擇此選項，當應用程式開發人員發佈新的更新時，您便必須手動核准任何新的權限。 這會導致應用程式的安裝和更新停止，直到權限被核准為止。 基於此原因，建議選取自動核准新權限的選項。 

9. 按一下 [選取]  來選取應用程式。
10. 按一下刀鋒視窗頂端的 [同步]  ，以與受控 Google Play 服務同步應用程式。
11. 按一下 [重新整理]  以更新應用程式清單並顯示新增的應用程式。

### <a name="add-additional-app-settings-to-a-managed-google-play-store-app"></a>新增其他應用程式設定到受控 Google Play 商店應用程式
1. 如果您需要新增其他應用程式詳細資料，請從應用程式清單選取應用程式。
2. 按一下 [屬性]   > [應用程式資訊]  旁邊的 [編輯]  。 [應用程式資訊]  頁面隨即顯示。
3. 在 [應用程式資訊]  頁面中，新增應用程式詳細資料：
    - **類別**：(選擇性) 選取一或多個內建的應用程式類別，或選取您建立的類別。 這麼做的話，當使用者在瀏覽公司入口網站時，可以更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式**：若要在使用者瀏覽應用程式時，於公司入口網站的主頁面上以醒目方式顯示應用程式套件，請選取此選項。
    - **資訊 URL**：(選用) 輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL**：(選擇性) 輸入包含這個應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員**：(選擇性) 輸入應用程式開發人員的姓名。
    - **擁有者**：(選擇性) 輸入此應用程式的擁有者名稱，例如「人力資源部門」  。
    - **附註**：(選擇性) 輸入要與此應用程式建立關聯的任何附註。
4. 按一下 [檢閱並儲存]  來檢視 [檢閱並儲存]  頁面。 
5. 完成後，請按一下 [儲存]  來在 Intune 中更新應用程式。

### <a name="add-a-managed-google-play-store-app-in-the-managed-google-play-console-alternative"></a>在受控 Google Play 主控台中新增受控 Google Play 商店應用程式 (替代方法)
如果您希望將受控 Google Play 應用程式與 Intune 同步處理，而不是使用 Intune 直接新增，請使用下列步驟。

> [!IMPORTANT]
> 下面提供的資訊是使用 Intune 新增受控 Google Play 應用程式的另一種方法，如上所述。

1. 前往[受控 Google Play 商店](https://play.google.com/work)。 使用與您用來設定 Intune 與 Android 企業間連線的相同帳戶進行登入。
2. 搜尋市集並選取您要使用 Intune 指派的應用程式。
3. 在顯示應用程式的頁面上，按一下 [核准]  。  
    在下列範例中，已經選擇 Microsoft Excel 應用程式。

    ![受控 Google Play 商店中的 [核准] 按鈕](./media/apps-add-android-for-work/approve.png)

   應用程式視窗隨即開啟，要求您授權讓應用程式執行各種作業。

4. 選取 [核准]  接受應用程式權限，並繼續作業。

    ![應用程式權限的 [核准] 按鈕](./media/apps-add-android-for-work/approve-app-permissions.png)

5. 選取其中一個選項來處理新的應用程式權限要求，然後選取 [儲存]  。

    ![用來處理新應用程式權限要求的選項](./media/apps-add-android-for-work/approve-app-settings.png)

    應用程式已通過核准並顯示在您的 IT 管理主控台中。 接下來，您可以[使用 Intune 同步 Android 工作設定檔應用程式](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune)。

## <a name="managed-google-play-private-lob-apps"></a>受控 Google Play 私人 (LOB) 應用程式

有兩種方式可將 LOB 應用程式新增至受控 Google Play：

1. 直接在 Intune 主控台中：這讓您透過直接在 Intune 內只提交應用程式 APK 和標題來新增 LOB 應用程式。 此方法不需要您擁有 Google 開發人員帳戶，也不需要向 Google 支付註冊為開發人員的費用。  此方法較為簡單，而且步驟數大幅減少，可在短短十分鐘內使 LOB 應用程式可供管理。
1. 在 Google Play 開發人員主控台中：如果您有 Google 開發人員帳戶，或是想要設定僅在 Google Play 開發人員主控台中提供的進階散發功能 (如新增其他應用程式螢幕擷取畫面)，則可使用 [Google Play 開發人員主控台](https://play.google.com/apps/publish)。 

### <a name="managed-google-play-private-lob-app-publishing-directly-in-the-intune-console"></a>直接在 Intune 主控台中發佈受控 Google Play 私人 (LOB) 應用程式

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [所有應用程式]   > [新增]  。
3. 在 [選取應用程式類型]  窗格中，在可用的 [市集應用程式]  類型下，選取 [受控 Google Play 應用程式]  。
4. 按一下 [選取]  。 [受控的 Google Play]  應用程式市集隨即在 Intune 內顯示。
5. 在 Google Play 視窗中選取 [私人應用程式]  (位於「鎖頭」  圖示旁邊)。 
6. 按一下右下方的 **"+"** 按鈕來新增應用程式。
7. 新增應用程式 [標題]  ，然後按一下 [上傳 APK]  來新增 APK 應用程式套件。
8. 按一下 [建立]  。
9. 如果您已完成新增應用程式，請關閉 [受控的 Google Play] 窗格。
10. 按一下 [應用程式]  窗格上的 [同步]  ，以與受控的 Google Play 服務進行同步處理。 

    > [!NOTE]
    > 私人應用程式可能需要數分鐘，才能進行同步。如果應用程式並未在您第一次執行同步時出現，請等候數分鐘，然後起始新的同步。

如需受控 Google Play 私人應用程式的詳細資訊 (包括常見問題集)，請參閱 Google 的支援文章： https://support.google.com/googleplay/work/answer/9146439

>[!IMPORTANT]
>使用此方法新增的私人應用程式絕對不能設為公用。 只有在您確定此應用程式對於您的組織一律是私人時，才使用此發佈選項。

### <a name="managed-google-play-private-lob-app-publishing-using-the-google-developer-console"></a>使用 Google 開發人員主控台發佈受控 Google Play 私人 (LOB) 應用程式

1. 使用與您用來設定 Intune 和 Android 企業間連線的相同帳戶來登入 [Google Play Developer Console](https://play.google.com/apps/publish)。  
    如果您是第一次登入，則必須註冊並支付費用，才能成為 Google 開發人員計劃的會員。
2. 在主控台中，選取 [加入新的應用程式]  。
3. 您可以用與發行應用程式至 Google Play 商店的相同方式，上傳並提供應用程式的相關資訊。 不過，您必須選取 [只讓我的組織 (<組織名稱>) 使用此應用程式]  。

    ![只將應用程式提供給您組織使用](./media/apps-add-android-for-work/restrict.png)

    這項作業會讓應用程式僅提供給您的組織使用。 在公用 Google Play 商店上則不提供該應用程式。

    如需如何上傳及發行 Android 應用程式的詳細資訊，請參閱 [Google Developer Console 說明](https://support.google.com/googleplay/android-developer/answer/113469)。
4. 發佈您的應用程式之後，使用與您用來設定 Intune 與 Android 企業間連線的相同帳戶來登入[受控 Google Play 商店](https://play.google.com/work)。
5. 在商店的 [應用程式]  節點中，確認您可以看見自己發行的應用程式。  
    應用程式會自動通過核准，以與 Intune 同步處理。

## <a name="managed-google-play-web-links"></a>受控 Google Play 網頁連結

受控 Google Play 網頁連結是可安裝且可管理的，就像其他 Android 應用程式一樣。 安裝在裝置上時，它們將會與使用者已安裝的其他應用程式一起出現在他們的應用程式清單中。 點選時，它們將在裝置的瀏覽器中啟動。

網頁連結將透過 Microsoft Edge 或您選擇部署的任何其他瀏覽器應用程式來開啟。 務必至少將一個瀏覽器應用程式部署至裝置，讓網頁連結能夠正確開啟。 不過，網頁連結可用的所有 [顯示]  選項 (全螢幕、獨立及最基本的 UI) 都只能搭配 Chrome 瀏覽器運作。 

> [!IMPORTANT]
> 在此文件發行時，有一個已知的 Google 錯誤會防止網頁連結透過 Chrome 以外的瀏覽器在裝置上開啟。 Google 已致力於修正此錯誤。  在 Microsoft 確認過 Google 已發佈其修正後，將會移除此通知。

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [所有應用程式]   > [新增]  。
3. 在 [選取應用程式類型]  窗格中，在可用的 [市集應用程式]  類型下，選取 [受控 Google Play 應用程式]  。
4. 按一下 [選取]  。 [受控的 Google Play]  應用程式市集隨即在 Intune 內顯示。
5. 在 Google Play 視窗中選取 [Web 應用程式]  (位於「地球」  圖示旁邊)。
6. 按一下右下方的 **"+"** 按鈕來新增應用程式。
7. 新增應用程式 [標題]  、Web 應用程式 [URL]  ，選取應用程式的顯示方式，然後選取應用程式圖示。
8. 按一下 [建立]  。
9. 如果您已完成新增應用程式，請關閉 [受控的 Google Play] 窗格。
10. 按一下 [應用程式]  窗格上的 [同步]  ，以與受控的 Google Play 服務進行同步處理。 

    > [!NOTE]
    > Web 應用程式可能需要數分鐘，才能進行同步。如果應用程式並未在您第一次執行同步時出現，請等候數分鐘，然後起始新的同步。

## <a name="sync-a-managed-google-play-app-with-intune"></a>使用 Intune 同步處理受控 Google Play 應用程式

如果您已核准商店中的某個應用程式，但它並未出現在 [應用程式]  工作負載中，請以下列方式強制立即同步處理：

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 選取 [應用程式]   > [租用戶系統管理]   > [連接器與權杖]   > [受控的 Google Play]  。
5. 在 [受控 Google Play]  窗格中，選擇 [重新整理]  。  
    此頁面會更新最近一次同步的時間和狀態。
6. 在 Microsoft 端點管理員系統管理中心內，選取 [應用程式]   > [所有應用程式]  。  
    隨即會顯示新的可用受控 Google Play 應用程式。

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices"></a>將受控 Google Play 應用程式指派給 Android Enterprise 工作設定檔裝置

當此應用程式顯示在 [應用程式]  工作負載窗格的 [應用程式授權]  節點中時，您便可以透過將應用程式指派給使用者群組，來以[和指派任何其他應用程式相同的方式來指派它](/intune-azure/manage-apps/deploy-apps)。

在您指派應用程式之後，它就會安裝 (或可供安裝) 在目標使用者的裝置上。 並且不會經過裝置使用者的核准。 如需 Android Enterprise 工作設定檔裝置的詳細資訊，請參閱[設定 Android Enterprise 工作設定檔裝置的註冊](../enrollment/android-work-profile-enroll.md)。 

> [!NOTE] 
> 只有已獲指派的應用程式才會顯示於終端使用者的受控 Google Play 商店中。 因此，這是系統管理員在使用受控 Google Play 設定應用程式時應採取的重要步驟。

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-fully-managed-devices"></a>將受控 Google Play 應用程式指派給 Android Enterprise 完全受控裝置

[Android Enterprise 完全受控裝置](../enrollment/android-fully-managed-enroll.md)為與單一使用者相關聯的公司擁有裝置，且僅供工作而非個人用途使用。 完全受控裝置上的使用者可以從其裝置上的受控 Google Play 應用程式取得可供他們使用的公司應用程式。

根據預設，Android Enterprise 完全受控裝置將不允許員工安裝組織未核准的任何應用程式。 此外，員工也無法移除任何已安裝的應用程式，因為這違反原則。 如果您想讓使用者存取完整的 Google Play 商店來安裝應用程式，而非只能存取受控 Google Play 商店中已核准的應用程式，您可以將 [允許存取 Google Play 商店中的所有應用程式]  設定為 [允許]  。 透過此設定，使用者便可使用其公司帳戶來存取 Google Play 商店中的所有應用程式，不過，購買可能會受限。 您可以透過允許使用者將帳戶新增至裝置，來移除受限的購買限制。 這麼做將讓終端使用者能夠使用個人帳戶從 Google Play 商店購買應用程式，以及進行應用程式內購買。 如需詳細資訊，請參閱[使用 Intune 來允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。 

> [!NOTE]
> Microsoft Intune 應用程式與 Microsoft Authenticator 應用程式將於上線期間，在所有完全受控裝置上安裝為必要的應用程式。 自動安裝這些應用程式將提供條件式存取支援，而 Microsoft Intune 應用程式使用者可以查看並解決合規性問題。 

## <a name="manage-android-enterprise-app-permissions"></a>管理 Android Enterprise 應用程式權限
Android Enterprise 會要求您先在受控 Google Play Web 主控台中核准應用程式，然後才能利用 Intune 同步它們，並將它們指派給使用者。 由於 Android Enterprise 可讓您以無訊息模式自動將應用程式推送到使用者的裝置，因此，您必須代表您的所有使用者接受應用程式權限。 使用者在安裝應用程式時不會看到任何應用程式權限，因此請務必了解這些權限。

即使您已核准先前的權限，當應用程式開發人員使用新版本應用程式更新權限時，那些權限也不會自動接受。 執行舊版本應用程式的裝置仍可以繼續使用， 然而，若要升級應用程式，則必須先核准新權限。 在您核准應用程式的新權限之前，未安裝該應用程式的裝置不會安裝應用程式。 

### <a name="update-app-permissions"></a>更新應用程式權限

請定期造訪受控的 Google Play 主控台來檢查新的權限。 您可以設定當已核准的應用程式需要新權限時，讓 Google Play 寄送電子郵件給您或其他使用者。 若您指派了應用程式，卻發現它並未安裝在裝置上，請遵循下列步驟來檢查是否有新的權限：

1. 前往 [Google Play](https://play.google.com/work)。
2. 使用您用來發行及核准應用程式的 Google 帳戶登入。
3. 選取 [更新]  索引標籤，然後檢查是否有任何應用程式需要更新。  
    任何列出的應用程式都需要新的權限，而且在套用新權限之前將不會指派。

或者，您可以設定讓 Google Play 針對每個應用程式，自動核准權限。

## <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices"></a>Android Enterprise 工作設定檔裝置的其他受控 Google Play 應用程式報告

針對部署到 Android Enterprise 工作設定檔裝置的受控 Google Play 應用程式，您可以使用 Intune 檢視裝置上所安裝應用程式的狀態與版本號碼。 

## <a name="delete-managed-google-play-apps"></a>刪除受控的 Google Play 應用程式
必要時，您可以從 Microsoft Intune 刪除受控的 Google Play 應用程式。 若要刪除受控的 Google Play 應用程式，請在 Azure 入口網站中開啟 Microsoft Intune，然後選取 [應用程式]   > [所有應用程式]  。 從應用程式清單，選取受控的 Google Play 應用程式右側的省略符號 (...)，然後從顯示的清單選取 [刪除]  。 當您從應用程式清單刪除受控 Google Play 應用程式時，會自動取消核准受控 Google Play 應用程式。

## <a name="android-enterprise-system-apps"></a>Android Enterprise 系統應用程式

您可以針對 [Android Enterprise 專用裝置](../enrollment/android-kiosk-enroll.md)或[完全受控裝置](../enrollment/android-fully-managed-enroll.md)啟用 Android Enterprise 系統應用程式。 如需新增 Android Enterprise 系統應用程式的詳細資訊，請參閱[將 Android Enterprise 系統應用程式新增至 Microsoft Intune](apps-ae-system.md)。

## <a name="next-steps"></a>後續步驟

- [將應用程式指派給群組](apps-deploy.md)
