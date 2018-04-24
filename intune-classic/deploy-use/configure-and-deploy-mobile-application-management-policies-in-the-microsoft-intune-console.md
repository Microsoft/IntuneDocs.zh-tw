---
title: 在 Intune 主控台中設定 MAM 原則
description: Microsoft Intune 中的行動應用程式管理原則可讓您修改所部署應用程式的功能，以使它能符合公司的相容性和安全性原則。
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 03/17/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b4fb33a8-a2fa-4353-bd89-5bda48b68e83
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e1b4903eedaec53015a01a7711f87401dc02d24e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console"></a>在 Microsoft Intune 主控台中設定及部署行動應用程式管理原則

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune 中的行動應用程式管理原則 (MAM) 可讓您修改所部署應用程式的功能，以使它能符合公司的相容性和安全性原則。 例如，您可以限制受管理應用程式中的剪下、複製及貼上作業，或將應用程式設定成只能在受管理瀏覽器中開啟所有的網頁連結。

行動應用程式管理原則支援：

-   執行 Android 4 和更新版本的裝置。

-   執行 iOS 8.0 及更新版本的裝置。

> [!TIP]
> 行動應用程式管理原則支援向 Intune 註冊的裝置。
>
> 如需如何針對 Intune 未管理的裝置建立應用程式管理原則的資訊，請參閱[使用行動應用程式管理原則搭配 Microsoft Intune 保護應用程式資料](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)。

不同於其他 Intune 原則，您不會直接部署行動應用程式管理原則。 相反地，您會將原則與您想要限制的應用程式相關聯。 當應用程式部署並安裝在裝置上時，您指定的設定將會生效。

應用程式必須加入 Microsoft Intune 應用程式 SDK，才能將限制套用至該應用程式。 有三種方法可以取得這種類型的應用程式：

-   **使用受原則管理的應用程式**。 受原則管理的應用程式有內建的應用程式 SDK。 若要加入此類型的應用程式，請從應用程式市集 (例如 iTunes Store 或 Google Play) 指定應用程式的連結。 這種類型的應用程式不需要進行任何處理。 如需詳細資訊，請參閱[可與 Microsoft Intune 行動應用程式管理原則搭配使用的應用程式清單](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。

-   **使用包裝的應用程式**。 包裝的應用程式就是經過 Microsoft Intune App Wrapping Tool 重新封裝，以包含應用程式 SDK 的應用程式。 此工具通常用來處理內部建立的公司應用程式。 您不能用它來處理從應用程式市集下載的應用程式。 如需詳細資訊，請參閱[準備將 iOS 應用程式交由 Microsoft Intune App Wrapping Tool 進行行動應用程式管理](/intune/app-wrapper-prepare-ios)和[準備 Android 應用程式以使用 Microsoft Intune App Wrapping Tool 進行行動應用程式管理](/intune/app-wrapper-prepare-android)。

- **自行撰寫納入 Intune App SDK 的應用程式**。 Intune App SDK 讓您可在撰寫應用程式時，將應用程式管理功納入該應用程式中。 如需詳細資訊，請參閱 [Intune App SDK 概觀](/intune/app-sdk)。
/intune/apps-prepare-mobile-application-management 如需在 App Wrapping Tool 與 Intune App SDK 之間做出選擇的協助，請參閱[決定如何準備應用程式以使用 Microsoft Intune 進行行動應用程式管理](/intune/apps-prepare-mobile-application-management)。

某些受管理的應用程式 (例如適用於 iOS 和 Android 的 Outlook 應用程式) 支援「多重身分識別」。 這表示 Intune 只會將管理設定套用到應用程式中的公司帳戶或資料。

例如，使用 Outlook 應用程式：

-   如果使用者有設定公司電子郵件帳戶和個人電子郵件帳戶，則 Intune 只會將管理設定套用到公司帳戶，而不會管理個人帳戶。

-   如果裝置已淘汰或取消註冊，則只會從裝置中移除公司的 Outlook 資料。

-   公司帳戶必須與用來向 Intune 註冊裝置的帳戶相同。

> [!TIP]
> 如果您搭配使用 Intune 與 Configuration Manager，請參閱[如何使用 Configuration Manager 中的行動應用程式管理原則來控制應用程式](https://technet.microsoft.com/library/mt131414.aspx)。

## <a name="create-and-deploy-an-app-with-a-mobile-application-management-policy"></a>以行動應用程式管理原則建立及部署應用程式

-   **步驟 1：**取得受原則管理的應用程式連結，建立包裝的應用程式，或使用 Intune App SDK 撰寫啟用 MAM 的應用程式。

-   **步驟 2：** 將應用程式發佈到您的雲端儲存空間。

-   **步驟 3：** 建立行動應用程式管理原則。

-   **步驟 4：**將應用程式與行動應用程式管理原則關聯，然後部署應用程式。

-   **步驟 5：** 監視應用程式部署。

## <a name="step-1-get-the-link-to-a-policy-managed-app-create-a-wrapped-app-or-use-the-intune-app-sdk-to-write-a-mam-enabled-app"></a>步驟 1：取得受原則管理的應用程式連結，建立包裝的應用程式，或使用 Intune App SDK 撰寫啟用 MAM 的應用程式

從應用程式市集尋找並記下您所要部署之受原則管理的應用程式的 URL。 例如 iPad 版 Microsoft Word 應用程式的 URL 為 **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**。


## <a name="step-2-publish-the-app-to-your-cloud-storage-space"></a>步驟 2：將應用程式發佈到您的雲端儲存空間
當您發行受管理的應用程式時，其程序將根據您是發行受原則管理的應用程式，還是使用 iOS 的 Microsoft Intune App Wrapping Tool 處理的應用程式而有不同。

#### <a name="to-publish-a-policy-managed-app"></a>發行原則管理應用程式

1.  當您準備好要將應用程式上傳至雲端儲存空間時，請遵循[在 Microsoft Intune 中新增行動裝置的應用程式](add-apps-for-mobile-devices-in-microsoft-intune.md)中的指示。

2.  針對 iOS 應用程式，請在 [選取將此軟體開放給裝置使用的方式] 下，選取 [App Store 中的受管理 iOS 應用程式]。

    若為 Android 應用程式，請選取 [外部連結] 。

3.  在 [指定 URL] 下，輸入您先前記下的原則管理應用程式 URL。

上傳完成之後，您會在已上傳應用程式的 [軟體屬性] 頁面上，看到 [應用程式管理原則] 為 [是]。

確認應用程式上傳成功之後，請繼續進行步驟 3。

#### <a name="to-publish-an-app-that-was-processed-through-the-microsoft-intune-app-wrapping-tool"></a>發行經過 Microsoft Intune App Wrapping Tool 處理的應用程式

1.  當您準備好要將應用程式上傳至雲端儲存空間時，請遵循[在 Microsoft Intune 中新增行動裝置的應用程式](add-apps-for-mobile-devices-in-microsoft-intune.md)中的指示。

2.  在 [選取將此軟體開放給裝置使用的方式] 下選取 [軟體安裝程式]。

3.  選取 [軟體安裝程式檔案類型] 下的 [iOS 的應用程式套件 (&#42;.ipa 檔案)]。

上傳完成之後，您會在已上傳應用程式的 [軟體屬性] 頁面上，看到 [應用程式管理原則] 為 [是]。

確認應用程式上傳成功之後，請繼續進行步驟 3。

## <a name="step-3-create-a-mobile-application-management-policy"></a>步驟 3：建立行動應用程式管理原則

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [原則] &gt; [概觀] &gt; [新增原則]。

2.  根據您想要設定應用程式的裝置類型而定，設定和部署下列其中一種「軟體」原則：

    -   **行動應用程式管理原則 (Android 4 及更新版本)**

    -   **行動應用程式管理原則 (iOS 8.0 及更新版本)**

    您可以使用建議的設定或自訂設定。 如需詳細資訊，請參閱[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

3.  視需要進行以下設定。 選項可能會視您設定原則的裝置類型而不同。

|設定名稱|詳細資料|
    |---------|--------------------|
    |**名稱**|指定這個原則的名稱。|
    |**描述**|(選用) 指定這個原則的描述。|
    |**限制要在公司管理的瀏覽器中顯示網頁內容**|啟用這項設定時，會在受管理的瀏覽器中開啟應用程式中的任何連結。 您必須將此應用程式部署到裝置，此選項才會運作。|
    |**防止 Android 備份** 或 **防止 iTunes 和 iCloud 備份**|這個設定可停用針對來自應用程式之任何資訊的備份。|
    |**允許應用程式將資料傳送到其他應用程式**|這個設定指定此應用程式可傳送資料的應用程式。 您可以選擇不允許將資料傳送到任何應用程式、只允許傳送至其他受管理的應用程式，或允許傳送到任何應用程式。 <br /><br />例如，若不允許資料傳輸，可以限制資料只可傳輸給像是 SMS 訊息等服務、限制不得將影像指派給連絡人，以及不得張貼到 Facebook 或 Twitter。<br /><br />針對 iOS 裝置，若要避免受管理與未受管理應用程式之間的文件傳送，您必須也設定及部署行動裝置安全性原則來停用 [在其他未受管理的應用程式中允許受管理的文件] 設定。 若您選擇只允許傳送到其他受管理的應用程式，系統將會使用 Intune PDF 及影像檢視器 (如有部署) 開啟個別類型的內容。<br /><br />此外，如果這個選項設定為 [受原則管理的應用程式] 或 [無]，則會封鎖允許焦點搜尋在應用程式中搜尋資料的 iOS 9 功能。<br><br>此設定對於在行動裝置上使用「開啟於」功能沒有影響。 若要管理「開啟於」功能，請參閱[使用 Microsoft Intune 管理 iOS 應用程式之間的資料傳輸](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)。|
    |**允許應用程式接收來自其他應用程式的資料**|這個設定指定此應用程式可以接收其資料的應用程式。 您可以選擇不允許任何應用程式傳送資料，只允許從其他受管理的應用程式傳送，或允許從任何應用程式傳送。<br /><br />當使用者從不受行動應用程式管理原則管理的應用程式存取資料時，該資料會被視為公司資料並受原則保護。 這適用於支援多重身分識別的 iOS 應用程式 (Intune 只會針對應用程式中的公司帳戶或資料套用管理設定)。 或者，這適用於已套用行動應用程式管理原則的已註冊裝置。|
    |**避免「另存新檔」**|此設定可停用 [另存新檔] 選項，以避免在任何使用此原則的應用程式中，將資料儲存到個人雲端儲存空間的位置 (例如 OneDrive 或 Dropbox)。|
    |**限制與其他應用程式的剪下、複製和貼上**|此設定可指定搭配應用程式使用剪下、複製和貼上作業的方式。 從下列選項進行選擇：<br /><br />**已封鎖**。 不允許在此應用程式與其他應用程式之間進行剪下、複製和貼上作業。<br /><br />**受原則管理的應用程式**。 只允許在此應用程式與其他受管理的應用程式之間進行剪下、複製和貼上作業。<br /><br />**可貼上的受原則管理應用程式**。 從此應用程式剪下或複製的資料，只可以貼到其他受管理的應用程式。 允許從任何應用程式剪下或複製資料貼上到此應用程式。<br /><br />**任何應用程式**。 不限制這個應用程式與其他應用程式之間的剪下、複製和貼上作業。<br /><br />若要在受管理的應用程式之間複製並貼上資料，這兩個應用程式皆必須設有 [受原則管理的應用程式] 或 [可貼上的受原則管理應用程式] 設定。|
    |**需要簡單的 PIN 碼才能存取**|此設定要求使用者輸入他們指定的 PIN 碼，才能使用此應用程式。 會要求使用者在第一次執行應用程式時設定。|
    |**PIN 重設之前的嘗試次數**|指定使用者必須重設 PIN 之前可以嘗試的 PIN 輸入次數。|
    |**需要公司認證才能存取**|此設定要求使用者輸入其公司的登入資訊，才能存取應用程式。|
    |**需要裝置符合公司原則才能存取**|此設定只允許在裝置未越獄或 Root 時，才能使用應用程式。|
    |**重新檢查存取需求前等候時間 (分鐘)**|在 [逾時] 欄位中，指定在開啟應用程式之後，重新檢查應用程式存取需求之前的時間間隔。|
    |**離線寬限期**|如果裝置已離線，指定重新檢查應用程式存取需求之前的時間間隔。|
    |**加密應用程式資料**|此設定指定所有與此應用程式相關聯的資料都將加密。 這包括儲存在外部 (例如 SD 卡) 的資料。<br /><br />**iOS 的加密**<br /><br />針對與 Intune 行動應用程式管理原則相關聯的應用程式，資料會透過作業系統所提供的裝置層級加密，於靜止時進行加密。 您可以透過 IT 系統管理員設定的裝置 PIN 原則來啟用。 需要 PIN 時，資料將會根據行動應用程式管理原則中的設定加密。 如 Apple 文件中所述，[iOS 所使用的模組都已通過 FIPS 140-2 認證](http://support.apple.com/HT202739)。<br /><br />**Android 的加密**<br /><br />對於與 Intune 行動應用程式管理原則相關聯的應用程式，Microsoft 會提供加密。 資料會在檔案 I/O 作業期間，以同步方式加密。  裝置儲存空間上的內容將一律加密。 加密方法符合 FIPS 140-2 規範且僅限 Samsung KNOX 裝置。|
    |**封鎖螢幕擷取** (僅限 Android 裝置)|此設定指定有人使用此應用程式時，將封鎖裝置的螢幕擷取功能。|

4. 完成之後，請選擇 [儲存原則]。

新的原則會顯示在 [原則] 工作區的 [設定原則] 節點中。

## <a name="step-4-associate-the-app-with-a-mobile-application-management-policy-and-then-deploy-the-app"></a>步驟 4：將應用程式與行動應用程式管理原則產生關聯，然後部署應用程式
確定您在 [管理部署] 對話方塊的 [行動應用程式管理] 頁面選取行動應用程式管理原則，將原則與應用程式產生關聯。

如需詳細資訊，請參閱[在 Microsoft Intune 中部署應用程式](deploy-apps.md)。

> [!IMPORTANT]
> 如果裝置從 Intune 取消註冊，原則將不會從應用程式中移除。 即使之後解除安裝並重新安裝應用程式，已套用原則的任何應用程式將會保留原則設定。

### <a name="what-to-do-when-an-app-is-already-deployed-on-devices"></a>如果裝置上已部署應用程式，該怎麼辦
當您部署應用程式時，有時候目標使用者或裝置之一可能已經安裝未受管理的應用程式版本。 例如，使用者可能已從應用程式市集安裝 Microsoft Word。

在這種情況下，您必須要求使用者手動解除安裝未受管理的版本，以便安裝您設定的受管理版本。

不過，如果使用執行 iOS 9 和更新版本的裝置，Intune 會自動要求使用者授權，以便接管現有應用程式的管理工作。 如果使用者同意，則應用程式會變成由 Intune 管理，而且也會套用與應用程式相關聯的所有行動應用程式管理原則。

> [!TIP]
> 如果裝置處於受監督的模式，Intune 會在不要求使用者授權的情況下，直接接管現有應用程式的管理工作。

## <a name="step-5-monitor-the-app-deployment"></a>步驟 5：監視應用程式部署
建立並部署與行動應用程式管理原則相關聯的應用程式之後，請使用下列程序來監視應用程式並解決任何原則衝突。

#### <a name="to-view-the-status-of-the-deployment"></a>檢視部署的狀態

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [群組] &gt; [概觀]。

2.  執行下列步驟：

    -   選擇 [所有使用者]，然後按兩下您想要檢查其裝置的使用者。 在 [使用者內容] 頁面上，選擇 [裝置]，然後按兩下您想要檢查的裝置。

    -   選擇 [所有裝置] &gt; [所有行動裝置]。 在 [裝置群組內容] 頁面上，選擇 [裝置]，然後按兩下您想要檢查的裝置。

3.  從 [行動裝置內容] 頁面上，選擇 [原則] 來查看已部署至裝置的行動應用程式管理原則清單。

4.  選取您想要檢視其狀態的行動應用程式管理原則。 您可以在下方窗格中檢視原則的詳細資料，並展開其節點以顯示其設定。

5.  在每個行動應用程式管理原則的 [狀態] 欄下，將會顯示 [符合]、[符合 (擱置)]，或 [錯誤]。 如果選取的原則有一個或多個設定衝突，此欄位會顯示 [錯誤]。

6.  識別衝突之後，您可以修改衝突的原則設定以使用相同的設定，或您也可以只將其中一個原則部署到應用程式和使用者。

### <a name="how-policy-conflicts-are-resolved"></a>如何解決原則衝突
第一次部署到使用者或裝置時，如果行動應用程式管理原則有衝突，衝突的特定設定值會從部署到應用程式的原則中移除。 應用程式會使用內建的衝突值。

後續部署到應用程式或使用者時，如果行動應用程式管理原則有衝突，衝突的特定設定值將不會在部署到應用程式的行動應用程式管理原則上更新。 應用程式會使用該設定現有的值。

在裝置或使用者收到兩個衝突原則的情況下，會適用下列行為：

-   如果原則已部署至裝置，則不會覆寫現有的原則設定。

-   如果原則尚未部署到裝置，而已部署兩個衝突的設定，則會使用裝置內建的預設設定。
