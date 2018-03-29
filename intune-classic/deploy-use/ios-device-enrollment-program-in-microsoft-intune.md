---
title: iOS 裝置的 Apple DEP 管理
description: 部署註冊設定檔，以藉由無線方式註冊透過 iOS 裝置註冊方案 (DEP) 購買的 iOS 裝置，進而管理 Apple 裝置。
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 03/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bf47c802291d802ac890aa4ba00cf79d9d2d10f0
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="enroll-corporate-owned-device-enrollment-program-ios-devices"></a>註冊屬公司擁有的裝置註冊方案 iOS 裝置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 可以部署註冊設定檔，以藉由「無線」方式註冊透過裝置註冊方案 (DEP) 購買的 iOS 裝置。 註冊套件可以包括裝置的設定助理選項。

>[!NOTE]
>DEP 註冊不能與[裝置註冊管理員](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)方法一起使用。
>此外，如果使用者註冊 iOS 裝置 (即使用公司入口網站應用程式)，並接著將這些裝置的序號匯入並指派給 DEP 設定檔，將會從 Intune 取消註冊裝置。
> 此外，macOS 目前不支援 DEP。

## <a name="prerequisites-for-enrolling-ios-devices-by-using-apple-dep-management"></a>使用 Apple DEP 管理註冊 iOS 裝置的必要條件

- [安裝 APNs 憑證](set-up-ios-and-mac-management-with-microsoft-intune.md)

- 您的組織必須加入 Apple DEP，並透過該計畫取得裝置。 下列網址提供程序的詳細資料：[https://deploy.apple.com](https://deploy.apple.com)。這個方案的優點包括不需要使用 USB 纜線將每部裝置連接到電腦，即可進行裝置的無操作安裝作業。

- 您必須先從 Apple 取得 DEP 權杖，才能為屬公司擁有的 iOS 裝置註冊 DEP。 此權杖可讓 Intune 同步處理貴公司所擁有的 DEP 參與裝置資訊。 它也允許 Intune 執行註冊設定檔上傳至 Apple ，並將這些設定檔指定給裝置。

## <a name="steps-to-enroll-ios-devices-by-using-apple-dep-management"></a>使用 Apple DEP 管理註冊 iOS 裝置的步驟

下列步驟說明如何在「第 0 天」使用 Apple DEP 管理註冊 iOS 裝置。 當貴組織新增及移除裝置時，您可能會重複這些步驟的某部分，例如新增或移除序號，如下所述。

### <a name="get-an-encryption-key"></a>取得加密金鑰

1. 以系統管理使用者身分開啟 [Microsoft Intune 管理主控台](https://manage.microsoft.com)，並移至 [系統管理] &gt; [行動裝置管理] &gt; [iOS] &gt; [裝置註冊方案]，然後選擇 [下載加密金鑰]。

2. 將加密金鑰 (.pem) 檔案儲存在本機。 這個 .pem 檔案會用於向 Apple 裝置註冊程式入口網站要求信任關係憑證。

![更新裝置註冊方案 Token](../media/dev-sa-ios-dep.png)

### <a name="get-a-device-enrollment-program-token"></a>取得裝置註冊方案 Token

1. 前往[裝置註冊方案入口網站](https://deploy.apple.com) (https://deploy.apple.com))，並使用公司的 Apple 識別碼登入。 稍後，您必須使用這個 Apple ID 來更新 DEP 權杖。

2.  在裝置註冊方案入口網站中，移至 [裝置註冊方案]&gt; [管理伺服器]，然後選擇 [新增 MDM 伺服器]。

3.  輸入 [MDM 伺服器名稱]，然後選擇 [下一步] 。 您可參考這個伺服器名稱，以識別行動裝置管理 (MDM) 伺服器， 但它不是 Microsoft Intune 伺服器的名稱或 URL。

4.  [新增 &lt;伺服器名稱&gt;] 對話方塊隨即開啟。 選擇 [選擇檔案...] 以上傳 .pem 檔案，然後選擇 [下一步]。

5.  [新增 &lt;伺服器名稱&gt;] 對話方塊會顯示 [您的伺服器權杖] 連結。 將伺服器權杖 (.p7m) 檔案下載到您的電腦，然後選擇 [完成]。

   此憑證 (.p7m) 檔案會用於建立 Intune 與 Apple 裝置註冊程式伺服器之間的信任關係。

### <a name="add-the-dep-token-to-intune"></a>將 DEP Token 新增至 Intune

1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，移至 [管理員] &gt; [行動裝置管理] &gt; [iOS] &gt; [裝置註冊方案]。

2. 選擇 [上傳 DEP 權杖]。 **瀏覽** 至憑證 (.p7m) 檔案，輸入您的 **Apple ID**，然後選擇 [上傳] 。

### <a name="add-the-corporate-device-enrollment-policy"></a>新增公司裝置註冊原則

1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，移至 [原則] &gt; [公司裝置註冊]，然後選擇 [新增]。

2. 提供 [一般] 詳細資料 (包括 [名稱] 和 [描述])，並指定指派給設定檔的裝置是否具有使用者親和性，或隸屬於某個群組：

   - **使用者親和性的提示**：裝置必須在初始設定期間與使用者建立關聯，之後才能以該使用者身分存取公司資料與電子郵件。 如果受 DEP 管理的裝置是屬於使用者，且裝置會使用公司入口網站 (以安裝應用程式)，則必須為此裝置設定**使用者親和性**。 在具有使用者親和性的 DEP 裝置註冊期間，無法使用多重要素驗證 (MFA)。 註冊後，MFA 會如預期地在這些裝置上運作。 當第一次登入時必須變更密碼的新使用者，在 DEP 裝置上進行註冊期間無法收到提示。 此外，密碼已過期的使用者也不會在 DEP 註冊期間收到提示要重設其密碼，且必須從不同的裝置重設密碼。

    >[!NOTE]
    >具有使用者親和性的 DEP 必須啟用 [WS-Trust 1.3 使用者名稱/混合端點](https://technet.microsoft.com/library/adfs2-help-endpoints)，才能要求使用者權杖。 [深入了解 WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

   - **無使用者親和性**：該裝置不會與使用者建立關聯。 如果裝置只會用來執行工作而不存取本機使用者資料，請使用這種關聯。 在這種情況下，需要使用者關聯的應用程式將無法運作 (包括用於安裝企業營運應用程式的公司入口網站應用程式)。

   您也可以**將裝置指派給以下群組**。 選擇 [選取…] 以選擇群組。

   > [!Important]
   > 群組指派將從 Intune 移至 Azure Active Directory。 一旦 Intune 帳戶收到適用的更新，您不會看到 [將裝置指派給以下群組] 選項。 [深入了解](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune#changes-to-intune-group-assignments)。

3. 啟用 [設定此設定檔的裝置註冊方案設定] 來支援 DEP。

      ![設定助理窗格](../media/pol-sa-corp-enroll.png)

   以下是可用於 DEP 管理之裝置的設定：

   - **部門** - 使用者在啟用期間點選 「About Configuration」 \(關於設定) 時顯示。
   - **支援電話號碼** - 使用者在啟用期間按一下 [需要協助] 按鈕時顯示。
   - **準備模式** - 在啟用期間設定，而且需要將裝置重設為出廠預設值才能進行變更︰
       - **不受監督** - 有限的管理功能
       - **受監督** - 啟用更多管理選項，並且預設會停用 [啟用鎖定]
   - **鎖定裝置的註冊設定檔** - 在啟用期間設定，而且需要重設為出廠預設值才能進行變更。
       - **停用** - 允許從 **[設定]** 功能表中移除管理設定檔
       - **啟用** - (需要**準備模式** = **受監督**) 停用可移除管理設定檔的 [iOS 設定] 功能表選項
   - **設定輔助程式選項** - 這些是選用設定，稍後可以在 iOS [設定] 功能表中進行設定。
        - **密碼** - 在啟用期間提示輸入密碼。 除非裝置將受到保護，或以其他方式控制存取 (例如，將裝置限制為單一應用程式的 Kiosk 模式)，否則一律需要密碼
       - **定位服務** - 啟用時，設定助理會在啟用期間提示服務
       - **還原** - 啟用時，設定助理會在啟用期間提示 iCloud 備份
       - **Apple ID** - 啟用時，如果 Intune 嘗試不使用 Apple ID 來安裝應用程式，iOS 會提示使用者輸入 Apple ID。 若要下載 iOS App Store 應用程式 (包含 Intune 所安裝的應用程式)，您必須提供 Apple ID。
       - **條款及條件** - 啟用時，設定助理會在啟用期間提示使用者接受 Apple 的條款及條件
       - **Touch ID** - 啟用時，設定助理會在啟用期間提示此服務
       - **Apple Pay** - 啟用時，設定助理會在啟用期間提示此服務
       - **縮放** - 啟用時，設定助理會在啟用期間提示此服務
       - **Siri** - 啟用時，設定輔助程式會在啟用期間提示此服務。
       - **傳送診斷資料給 Apple** - 啟用時，設定助理會在啟用期間提示此服務
   -  **啟用其他 Apple Configurator 管理功能** - 設為 **[不允許]** 防止使用 iTunes 同步處理檔案或透過 Apple Configurator 進行管理。 建議您選擇 [不允許]，並從 Apple Configurator 匯出任何進一步設定，然後透過 Intune 將其部署為自訂 iOS 組態設定檔，而不是使用此設定來允許是否透過憑證進行手動部署。
       - **不允許** - 防止裝置透過 USB 進行通訊 (停用配對)
       - **允許** - 允許裝置透過任何電腦或 Mac 的 USB 連線進行通訊
       - **需要憑證** - 允許使用匯入至註冊設定檔的憑證與 Mac 配對

### <a name="assign-the-profile-to-devices"></a>將設定檔指派給裝置

1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，移至 [原則] &gt; [公司裝置註冊]，然後選擇 [指派]。

2. 選擇您要指派所建立之設定檔的目標裝置。 您可以選擇 [所有裝置] 或選取特定的裝置，然後選取 [新增]。

> [!Important]
> Intune 目前可讓您指定「預設的裝置註冊設定檔」，這表示當您與 Apple DEP 服務同步新的序號時，新序號會自動指派到該預設的設定檔。 當您的租用戶在不久的將來移轉到新的 Azure 入口網站時，您將無法再設定預設設定檔，並將序號自動指派給該設定檔。 而是必須將序號指派到特定的設定檔。 [深入了解](https://docs.microsoft.com/intune/device-enrollment-program-enroll-ios)

### <a name="assign-dep-devices-for-management"></a>指派要管理的 DEP 裝置

1. 前往[裝置註冊方案入口網站](https://deploy.apple.com) (https://deploy.apple.com))，並使用公司的 Apple 識別碼登入。

2. 移至 [部署方案] &gt; [裝置註冊方案] &gt; [管理裝置]。

3. 指定您 **選擇裝置**的方式、提供裝置資訊，並利用裝置的 [序號] 、[訂單號碼] 或 [上傳 CSV 檔案] 指定詳細資料。

4. 依序選擇 [Assign to Server]\(指派給伺服器)、針對 Microsoft Intune 指定的 &lt;伺服器名稱&gt; 以及 [確定]。

### <a name="synchronize-dep-managed-devices"></a>同步處理 DEP 管理的裝置

此步驟會將裝置與 Apple DEP 服務同步，並可讓裝置出現在 Intune 主控台中。

1. 以系統管理使用者身分開啟 [Microsoft Intune 管理主控台](https://manage.microsoft.com)，並移至 [管理員] &gt; [行動裝置管理] &gt; [iOS] &gt; [裝置註冊方案]，然後選擇 [立即同步處理]。 同步處理要求會傳送至 Apple。

2. 若要在同步處理之後查看 DPE 管理的裝置，請在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，移至 [群組] &gt; [所有裝置] &gt; [公司預先註冊的裝置] &gt; [依 iOS 序號]。 在 [依 iOS 序號] 工作區中，受管理裝置的 [狀態] 會顯示為 [未連線]，直到裝置開機並執行 [設定助理] 來註冊裝置為止。

   若要符合可接受 DEP 流量的 Apple 詞彙，Intune 具有下列限制︰

   - 完整 DEP 同步處理每 7 天只能執行一次。 在完整同步處理期間，Intune 會重新整理 Apple 已指派給 Intune 的每個序號，不論先前是否已同步處理序號。 如果在上一次完整同步處理過後的 7 天內嘗試進行完整同步處理，Intune 只會重新整理尚未列在 Intune 中的序號。

   - 任何同步處理要求都會在 10 分鐘內完成。 在此期間或直到要求成功，會停用 [同步處理] 按鈕。

### <a name="distribute-devices-to-users"></a>將裝置散發給使用者

現在您可以將屬公司擁有的裝置散發給使用者。 當 iOS 裝置開機時，就會加以註冊交由 Intune 管理。 使用者裝置限制會套用到 DEP 管理的裝置。

>[!NOTE]
>如果使用者嘗試註冊 DEP 裝置，但已超過其裝置限制，註冊將以無訊息的方式失敗而不警告使用者。

## <a name="changes-to-intune-group-assignments"></a>Intune 群組指派的變更

從 2017 年 4 月開始，裝置群組管理會移至 Azure Active Directory。 轉換至 Azure Active Directory 群組之後，群組指派不會出現在公司註冊設定檔選項中。 因為此變更將在連續幾個月的時間推出，您可能不會立即看到變更。 在移動到新的入口網站後，動態裝置群組指派可以根據公司的註冊設定檔名稱來定義。

在移轉之際，公司裝置註冊設定檔預先指派的每個 Intune 裝置群組，都會根據公司裝置註冊設定檔的名稱，在 Azure AD 中建立對應的動態裝置群組。 新設定檔名稱的格式如下：*EnrollmentProfile:&lt;相關設定檔的名稱&gt;*。 此程序可確保已指派裝置群組的裝置會自動在群組中註冊，並部署好原則和應用程式。

上述自動群組建立只會在群組移轉時發生一次。 移轉之後，Intune 系統管理員必須使用 Azure 入口網站來建立群組。 如需此變更如何影響公司擁有之 iOS 裝置註冊的詳細資料，請參閱[將公司預先註冊的 iOS 裝置變更為自動群組 (英文)](https://blogs.technet.microsoft.com/intunesupport/2017/04/19/changes-to-automatic-grouping-for-corporate-pre-enrolled-ios-devices/)。

您也可以[深入了解 Azure Active Directory 群組](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/)。

### <a name="see-also"></a>另請參閱
[註冊裝置的必要條件](prerequisites-for-enrollment.md)
