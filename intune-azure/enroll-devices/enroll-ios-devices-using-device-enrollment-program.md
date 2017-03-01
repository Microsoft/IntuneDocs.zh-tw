---
title: "註冊 iOS 裝置 - 裝置註冊方案 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版：了解如何使用裝置註冊方案來註冊公司擁有的 iOS 裝置。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: da6d377c94ce5db7bbfa1cb3fc165581d649a1fb
ms.lasthandoff: 02/15/2017


---

# <a name="enroll-ios-devices-using-device-enrollment-program"></a>使用裝置註冊方案註冊 iOS 裝置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Microsoft Intune 可以部署註冊設定檔，以藉由「無線」方式註冊透過裝置註冊方案 (DEP) 購買的 iOS 裝置。 設定檔包含您要套用到裝置的管理設定。 註冊套件可包含裝置的設定助理選項。 透過 DEP 註冊的裝置不能由使用者取消註冊。

>[!NOTE]
>此註冊方法不能與[裝置註冊管理員](enroll-devices-using-device-enrollment-manager.md)方法一起使用。

若要使用 Apple 的裝置註冊方案 (DEP) 來管理屬公司擁有的 iOS 裝置，您的組織必須加入 Apple DEP，並透過該方案購得裝置。 下列網址提供該程序的詳細資料：  [https://deploy.apple.com](https://deploy.apple.com)。 這個方案的優點包括不需要使用 USB 纜線將每部裝置連接到電腦，即可進行裝置的無操作安裝作業。

您必須先從 Apple [取得 DEP 權杖](get-apple-dep-token.md)，才可為屬公司擁有的 iOS 裝置註冊 DEP。 此權杖可讓 Intune 同步處理貴公司所擁有的 DEP 參與裝置資訊。 它也允許 Intune 執行註冊設定檔上傳至 Apple ，並將這些設定檔指定給裝置。

註冊 iOS 裝置的其他方法，詳述於 [Choose how to enroll iOS devices in Intune](choose-ios-enrollment-method.md) (選擇如何在 Intune 中註冊 iOS 裝置)。

## <a name="prerequisites"></a>必要條件

請於設定 iOS 裝置註冊之前，先完成下列必要條件︰

- [設定網域](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [設定 MDM 授權單位](set-mdm-authority.md)
- [建立群組](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- 指派 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)中的使用者授權
- [取得 Apple MDM Push Certificate](get-an-apple-mdm-push-certificate.md)
- [取得 Apple DEP 權杖](get-apple-dep-token.md)

## <a name="create-an-apple-dep-profile-for-devices"></a>建立裝置的 Apple DEP 設定檔

裝置註冊設定檔會定義套用至裝置群組的設定。 下列步驟示範如何使用 DEP 來為 iOS 裝置建立裝置註冊設定檔。

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 Intune 刀鋒視窗上，選擇 [註冊裝置]，然後選擇 [Apple 註冊]。

3. 在 [管理 Apple 裝置註冊方案 (DEP) 設定] 下，選取 [DEP 設定檔]。

4. 在 [Apple DEP 設定檔] 刀鋒視窗中，選取 [建立]。

5. 在 [建立註冊設定檔] 刀鋒視窗中，為設定檔輸入名稱以及描述。

6. 為 [使用者親和性] 選擇具備此設定檔的裝置，在註冊時要或不要有使用者親和性。

 - **搭配使用者親和性進行註冊** - 裝置必須在初始設定期間與使用者建立關聯，之後便可以存取公司資料與電子郵件。 為屬於使用者而受 DEP 管理的裝置，以及使用公司入口網站進行像是安裝應用程式等服務的裝置，選擇使用者親和性。 請注意，在具有使用者親和性的 DEP 裝置註冊期間，無法使用多重要素驗證 (MFA)。 註冊後，MFA 會如預期地在這些裝置上運作。

    >[!NOTE]
    >具有使用者親和性的 DEP 必須啟用 WS-Trust 1.3 使用者名稱/混合端點，才能要求使用者權杖。

 - **不搭配使用者親和性進行註冊** - 該裝置不會與使用者建立關聯。 針對執行工作而不需存取本機使用者資料的裝置，請使用此關係。 需要使用者關聯的應用程式 (包含用於安裝企業營運應用程式的公司入口網站應用程式) 將無法運作。

7. 選取 [裝置管理設定]，設定下列設定檔設定，然後選取 [儲存]：

    - **受監督** - 啟用更多管理選項，且預設會停用 [啟用鎖定] 的管理模式。 若將核取方塊留為空白，則管理功能有限。

    - **鎖定的註冊** - (需要管理模式 = 受監督) 停用允許移除管理設定檔的 iOS 設定。 若將核取方塊留為空白，表示允許從 [設定] 功能表移除管理設定檔。 此項目於啟用期間設定，且除非重設為出廠預設值，否則無法變更。

    - **允許配對** - 指定 iOS 裝置是否可與電腦同步。 若選擇 [依據憑證允許 Apple Configurator]，則必須在 [Apple Configurator 憑證] 下選擇憑證。

    - **Apple Configurator 憑證** - 如果在 [允許配對] 下選擇了 [依據憑證允許 Apple Configurator]，則請選取要匯入的 Apple Configurator 憑證。

8. 選取 [設定助理設定]，設定下列設定檔設定，然後選取 [儲存]：

    - **部門名稱** - 使用者於啟用期間點選 [About Configuration] (關於設定) 時顯示。

    - **部門電話號碼** - 使用者於啟用期間按一下 [需要協助] 按鈕時顯示。
    - **設定輔助程式選項** - 這些是選用設定，稍後可以在 iOS [設定] 功能表中進行設定。
        - **密碼** - 在啟用期間提示輸入密碼。 除非裝置將受到保護，或以其他方式控制存取 (例如，將裝置限制為單一應用程式的 Kiosk 模式)，否則一律需要密碼。
        - **定位服務** - 啟用時，設定助理會在啟用期間提示服務
        - **還原** - 啟用時，設定助理會在啟用期間提示 iCloud 備份
        - **Apple ID** - 啟用時，如果 Intune 嘗試不使用 Apple ID 來安裝應用程式，iOS 會提示使用者輸入 Apple ID。 若要下載 iOS App Store 應用程式 (包含 Intune 所安裝的應用程式)，您必須提供 Apple ID。
        - **條款及條件** - 啟用時，設定助理會在啟用期間提示使用者接受 Apple 的條款及條件
        - **Touch ID** - 啟用時，設定助理會在啟用期間提示此服務
        - **Apple Pay** - 啟用時，設定助理會在啟用期間提示此服務
        - **縮放** - 啟用時，設定助理會在啟用期間提示此服務
        - **Siri** - 啟用時，設定助理會在啟用期間提示此服務
        - **診斷資料** - 啟用時，設定助理會在啟用期間提示此服務

9. 若要儲存設定檔設定，請於 [建立註冊設定檔] 刀鋒視窗上，選取 [建立]。

## <a name="assign-apple-dep-serial-numbers-to-your-mdm-server"></a>將 Apple DEP 序號指派到 MDM 伺服器

1. 前往[裝置註冊方案入口網站](https://deploy.apple.com) (https://deploy.apple.com)，並使用公司的 Apple ID 登入。 

2. 移至 [部署方案] &gt; [裝置註冊方案] &gt; [管理裝置]。 

3. 指定您**選擇裝置**的方式，然後提供裝置資訊，並利用裝置的 [序號]、[訂單號碼] 或 [上傳 CSV 檔案] 的方式，指定詳細資料。 

4. 依序選擇 [Assign to Server] (指派給伺服器)、針對 Microsoft Intune 指定的 &lt;伺服器名稱&gt; 以及 [確定]。

## <a name="synchronize-dep-managed-devices"></a>同步 DEP 管理的裝置

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 Azure 入口網站的 Intune 刀鋒視窗上，選擇 [註冊裝置]，然後選擇 [Apple 註冊]。

3. 在 [管理 Apple 裝置註冊方案 (DEP) 設定] 下，選取 [DEP 序號]。

4. 在 [Apple DEP 序號] 刀鋒視窗中，選取 [同步]。

5. 在 [同步] 刀鋒視窗中，選取 [要求同步]。 進度列會顯示再次要求進行同步之前，必須要等待的總時間。

    若要符合可接受 DEP 流量的 Apple 詞彙，Intune 具有下列限制︰
     -    完整 DEP 同步處理每&7; 天只能執行一次。 在完整同步處理期間，Intune 會重新整理 Apple 已指派給 Intune 的每個序號，不論先前是否已同步處理序號。 如果在上一次完整同步處理過後的&7; 天內嘗試進行完整同步處理，Intune 只會重新整理尚未列在 Intune 中的序號。
     -    任何同步處理要求都會在 10 分鐘內完成。 在此期間或直到要求成功，會停用 [同步處理] 按鈕。

>[!NOTE]
>您也可以從 [Apple DEP 序號] 刀鋒視窗中，將 DEP 序號指派給設定檔。

## <a name="distribute-devices-to-users"></a>將裝置散發給使用者

現在已可將公司擁有的裝置提供給使用者。 iOS 裝置開機時，該裝置就會註冊交由 Intune 管理。


## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>使用者在其裝置安裝及使用公司入口網站的方式

已設定使用者親和性的裝置可以安裝並執行公司入口網站 App，以下載 App 及管理裝置。 使用者收到裝置之後，必須如下所示完成一些額外的步驟，來完成設定助理並安裝公司入口網站應用程式。

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>使用者如何註冊具有使用者親和性之公司擁有的 iOS 裝置 

1. 當使用者將其裝置開啟時，系統會提示他們完成設定助理。 設定期間，系統會提示使用者輸入其認證。 他們必須輸入與其 Intune 中訂閱相關聯的認證 (也就是不重複的個人名稱或 UPN)。

2. 設定期間，系統會提示使用者輸入 Apple ID。 使用者必須提供 Apple ID 以允許裝置安裝「公司入口網站」。 他們也可以在安裝完成後，從 iOS 設定功能表提供 ID。

3. 設定完成之後，使用者必須從 App Store 安裝公司入口網站應用程式。

4. 使用者現已可使用於設定裝置時所用的 UPN，來登入公司入口網站。

5. 登入之後，會提示使用者註冊其裝置。 第一個步驟是識別裝置。 App 會在清單中顯示已經過公司註冊並指派給使用者 Intune 帳戶的 iOS 裝置。 使用者應該要選擇相符的裝置。 如果此裝置尚未經過公司註冊，使用者應選擇新裝的置來繼續進行標準註冊流程。

6. 使用者要在下一個畫面中，確認新裝置的序號。 若要進行此作業，使用者要選取顯示的連結。 該連結會啟動「設定」應用程式，其能讓使用者可確認其序號。 然後使用者必須在公司入口網站應用程式中，輸入該序號的最後四個字元。

   此步驟會確認裝置是公司在 Intune 中註冊的裝置。 如果裝置上的序號不符，則使用者可能選取了錯誤的裝置。 使用者必須返回上一個畫面，並選取不同的裝置。

7. 序號通過驗證後，公司入口網站 App 會重新導向至「公司入口網站」網站，以完成註冊。 該網站隨即會提示使用者返回應用程式。

如此即已完成註冊，且使用者現已可使用此裝置的完整功能。

