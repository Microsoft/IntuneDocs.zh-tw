---
title: 管理 Apple 大量採購的應用程式
titleSuffix: Microsoft Intune
description: 針對從 iOS 與 macOS App Store 大量採購的應用程式，了解如何將應用程式同步處理到 Microsoft Intune，然後管理及並追蹤其使用情況。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d965ac35719d809ab922d28f76dec1754e9a4c6b
ms.sourcegitcommit: 9b29478f815e10c46c8030abe0146d601ce0e28c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051621"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>如何使用 Microsoft Intune 管理透過 Apple 大量採購方案購買的 iOS 與 macOS 應用程式


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Apple 讓您使用 [Apple Business Manager](https://business.apple.com/) 或 [Apple School Manager](https://school.apple.com/)，針對您想要在組織中用於 iOS 和 macOS 裝置上的應用程式購買多個授權。 您可以將您的大量採購資訊與 Intune 同步處理，並追蹤大量採購的應用程式使用情況。 購買應用程式授權可協助您有效地管理公司內的應用程式，並保留對已購買之應用程式的擁有權和控制。 

Microsoft Intune 可藉由下列方式協助您管理透過此方案所購買的應用程式：

- 同步您從 Apple Business Manager 所下載的位置權杖。
- 追蹤有多少已購買的應用程式可供使用及已經使用。
- 協助您安裝所擁有之最大授權數量的應用程式。

此外，針對從 Apple Business Manager 所購買的書籍，您可以使用 Intune 來針對 iOS 裝置進行同步處理、管理及指派。 如需詳細資訊，請參閱[如何管理透過大量採購方案購買的 iOS 電子書](vpp-ebooks-ios.md)。

## <a name="what-are-location-tokens"></a>什麼是位置權杖？
位置權杖也稱為大量採購方案 (VPP) 權杖。 這些權杖是用來指派及管理使用 Apple Business Manager 購買的授權。 內容管理員可以購買及指派授權，並在 Apple Business Manager 與他們具授權的位置權杖相關聯。 接著會從 Apple Business Manager 下載這些位置權杖，並在 Microsoft Intune 中上傳它們。 Microsoft Intune 支援針對每個租用戶上傳多個位置權杖。 每個權杖有效期限為一年。

## <a name="how-are-purchased-apps-licensed"></a>已購買之應用程式的授權方式為何？
可以使用 Apple 針對 iOS 和 macOS 裝置所提供的兩種授權類型，來將已購買的應用程式指派給群組。

|   | 裝置授權 | 使用者授權 |
|-----|------------------|----------------|
| **App Store 登入** | 不需要。 | 在系統提示登入 App Store 時，每個使用者都必須使用唯一的 Apple ID。 |
| **裝置設定封鎖對 App Store 的存取** | 可以使用公司入口網站來安裝及更新應用程式。 | 加入 Apple VPP 的邀請需要 App Store 的存取權。 如果您已經設定原則來停用 App Store，則 VPP 應用程式的使用者授權將無法運作。 |
| **自動應用程式更新** | 由 Intune 系統管理員在 [Apple VPP 權杖] 設定中設定，其中應用程式的 [指派類型]  為 [需要]  。 <br> <br> 如果 [指派類型]  為 [適用於已註冊的裝置]  ，便可以從公司入口網站安裝可用的應用程式更新。 | 由使用者在個人的 App Store 設定中設定。 這無法由 Intune 系統管理員管理。 |
| **使用者註冊** | 不支援。 | 透過使用受控 Apple ID 來支援。 |
| **書籍** | 不支援。 | 支援。 |
| **已使用授權** | 每個裝置 1 個授權。 授權會與裝置建立關聯。 | 1 個授權可用於使用相同個人 Apple ID 的 5 個裝置。 授權會與使用者建立關聯。 <br> <br> 在 Intune 中與個人 Apple ID 和受控 Apple ID 建立關聯的使用者會耗用 2 個應用程式授權。|
| **授權移轉** | 應用程式可以透過無訊息方式從使用者授權移轉為裝置授權。 | 應用程式無法從裝置授權移轉為使用者授權。 |

> [!NOTE]  
> 公司入口網站不會在「使用者註冊」裝置上顯示裝置授權的應用程式，因為在「使用者註冊」裝置上只能安裝使用者授權的應用程式。

## <a name="what-app-types-are-supported"></a>支援哪些應用程式類型？
您可以使用 Apple Business Manager 來購買並散發公用及私人應用程式。
- **市集應用程式：** 內容管理員可以使用 Apple Business Manager 來購買 App Store 中所提供的免費和付費應用程式。
- **自訂應用程式：** 內容管理員也可以使用 Apple Business Manager 來購買以私人方式向您的組織提供的自訂應用程式。 這些應用程式會由與您直接合作的開發人員，針對您組織的特定需求量身打造。 深入了解[如何散發自訂應用程式](https://developer.apple.com/business/custom-apps/) \(英文\)。

## <a name="prerequisites"></a>先決條件
- 適用於您組織的 [Apple Business Manager](https://business.apple.com/) 或 [Apple School Manager](https://school.apple.com/) 帳戶。 
- 已指派至一或多個位置權杖之已購買的應用程式授權。 
- 已下載的位置權杖。 

> [!IMPORTANT]
> - 單一位置權杖同時只能搭配單一裝置管理解決方案使用。 開始搭配 Intune 使用已購買的應用程式之前，請撤銷並移除搭配其他行動裝置管理 (MDM) 廠商使用的任何現有位置權杖。 
> - 單一位置權杖僅支援同時搭配單一 Intune 用戶端使用。 請勿將相同的權杖重複用於多個 Intune 租用戶。
> - 根據預設，Intune 每天會將位置權杖與 Apple 同步兩次。 您可以隨時從 Intune 起始手動同步處理。
> - 在您將位置權杖匯入到 Intune 之後，請不要將相同的權杖匯入到任何其他裝置管理解決方案。 這樣做會導致授權指派與使用者記錄遺失。

## <a name="migrate-from-volume-purchase-program-vpp-to-apps-and-books"></a>從大量採購方案 (VPP) 移轉至「App 及書籍」
如果您的組織尚未移轉至 Apple Business Manager 或 Apple School Manager，請檢閱 [Apple 針對移轉至 [App 及書籍] 的指引](https://support.apple.com/HT208257)，再繼續於 Intune 中管理已購買的應用程式。

> [!IMPORTANT]
> - 為了獲得最佳的移轉體驗，請針對每個位置僅移轉單一 VPP 購買者。 如果每個購買者都移轉到唯一位置，所有的授權 (包括已指派和未指派的授權) 都會移轉至 [App 及書籍]。
> - 請不要刪除 Intune 中的現有舊版 VPP 權杖，或是 Intune 中與現有舊版 VPP 權杖相關聯的應用程式和指派。 這些動作將需要在 Intune 中重新建立所有應用程式指派。

在 Apple Business Manager 或 Apple School Manager 中將現有的已購買 VPP 內容和權杖移轉至 [App 及書籍] 的步驟如下：

1. 邀請 VPP 購買者加入您的組織，並引導每個使用者選取唯一的位置。 
2. 在繼續之前，請確定組織內的所有 VPP 購買者都已完成步驟 1。
3. 確認所有已購買的應用程式和授權都已經移轉至 Apple Business Manager 或 Apple School Manager 中的 [App 及書籍]。
4. 透過移至 [Apple Business (或 School) Manager]   > [設定]   > [App 及書籍]   > [我的伺服器權杖]  來下載新的位置權杖。
5. 透過移至 Microsoft 端點管理員系統管理中心中的 [租用戶系統管理]   > [連接器與權杖]   > [Apple VPP 權杖]  並同步權杖來更新位置權杖。

## <a name="upload-an-apple-vpp-or-location-token"></a>上傳 Apple VPP 或位置權杖

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 選取 [租用戶系統管理]   > [連接器與權杖]   > [Apple VPP 權杖]  。
4. 在 VPP 權杖清單窗格上，選取 [建立]  。
5. 在 [建立 VPP 權杖]  窗格上，指定下列資訊：
    - **VPP 權杖檔案** - 如果您尚未這麼做，請註冊 Apple Business Manager 或 Apple School Manager。 註冊之後，請下載您帳戶的 Apple VPP 權杖，然後在這裡選取它。
    - **Apple ID** - 輸入與已上傳的權杖相關聯之帳戶的受控 Apple ID。
    - **從其他 MDM 中控制權杖** - 將此選項設定為 [是]  ，以允許從其他 MDM 解決方案將權杖重新指派給 Intune。
    - **權杖名稱** - 用於設定權杖名稱的系統管理欄位。    
    - **國家/地區** - 選取 VPP 國家/地區市集。  Intune 會從指定的 VPP 國家/地區市集同步處理所有地區設定的 VPP 應用程式。
        > [!WARNING]  
        > 變更國家/地區將會針對搭配此權杖所建立的應用程式，在下次與 Apple 服務進行更新時更新應用程式中繼資料和 App Store URL。 如果應用程式不存在於新的國家/地區市集，即不會更新應用程式。

    - **VPP 帳戶類型** - 請選擇 [商務]  或 [教育]  。
    - **自動更新應用程式** - 從 [開啟]  或 [關閉]  進行選擇，以啟用自動更新。 若啟用，Intune 會偵測應用程式市集內的 VPP 應用程式更新，並在裝置簽入時將更新自動推送至裝置。 
        
        > [!NOTE] 
        > Apple VPP 應用程式的自動應用程式更新只會自動更新使用**必要**安裝用途部署的應用程式。 針對使用**可用**安裝意圖部署的應用程式，自動更新會自動為 IT 系統管理員產生狀態訊息，通知已有可用的新版本應用程式。 透過選取應用程式、選取 [裝置安裝狀態]，然後檢查 [狀態詳細資料]，即可看到此狀態訊息。  

    - **我授與 Microsoft 傳送使用者及裝置資訊到 Apple 的權限。** - 您必須選取 [我同意]  才能繼續。 若要檢閱 Microsoft 將哪些資料傳送給 Apple，請參閱 [Intune 傳送至 Apple 的資料](~/protect/data-intune-sends-to-apple.md)。

6. 完成之後，請選取 [建立]  。 該權杖會顯示在權杖清單窗格內。

## <a name="synchronize-a-vpp-token"></a>同步 VPP 權杖
您可以在 Intune 中針對選取的權杖選擇 [同步]  ，來同步您已購買之應用程式的應用程式名稱、中繼資料和授權資訊。

## <a name="assign-a-volume-purchased-app"></a>指派大量採購應用程式

1. 選取 [應用程式]   > [所有應用程式]  。
2. 在應用程式窗格清單上，選擇您要指派的應用程式，然後選擇 [指派]  。
3. 在 [應用程式名稱]   - [指派]  窗格上，選擇 [新增群組]  ，然後在 [新增群組]  窗格中選擇 [指派類型]  ，選擇要指派該應用程式的 Azure AD 使用者或裝置群組。
5. 針對您選取的每個群組，選擇下列設定：
    - **類型** - 選擇應用程式會是 [可用]  (終端使用者可以從公司入口網站安裝應用程式) 或 [必要]  (終端使用者的裝置會自動安裝應用程式)。
    - **授權類型** - 選擇 [使用者授權]  或 [裝置授權]  。
6. 完成之後，請選擇 [儲存]  。


>[!NOTE]
>可用的部署用途不支援裝置群組，僅支援使用者群組。 顯示的應用程式清單與權杖建立關聯。 如果您的應用程式與多個 VPP 權杖建立關聯，您會看到相同的應用程式顯示多次；針對每個權杖各一次。

> [!NOTE]  
> Intune (或任何其他 MDM) 實際上不會安裝 VPP 應用程式。 相反地，Intune 會連線到您的 VPP 帳戶，並告訴 Apple 要將哪些應用程式授權指派給哪些裝置。 從該處，所有實際安裝都會在 Apple 與裝置之間處理。
> 
> [Apple MDM 通訊協定參考，第 135 頁](https://developer.apple.com/business/documentation/MDM-Protocol-Reference.pdf) \(英文\)

## <a name="end-user-prompts-for-vpp"></a>VPP 的終端使用者提示

終端使用者將會在許多案例中收到 VPP 應用程式安裝的提示。 下表說明每個狀況：

| # | 案例                                | 邀請加入 Apple VPP 方案                              | 應用程式安裝提示 | 提示輸入 Apple ID |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD – 授權的使用者 (非「使用者註冊裝置」裝置)                             | Y                                                                                               | Y                                           | Y                                 |
| 2 | 公司 – 授權的使用者 (不受監督的裝置)     | Y                                                                                               | Y                                           | Y                                 |
| 3 | 公司 – 授權的使用者 (受監督的裝置)         | Y                                                                                               | N                                           | Y                                 |
| 4 | BYOD – 授權的裝置                           | N                                                                                               | Y                                           | N                                 |
| 5 | 公司 – 授權的裝置 (不受監督的裝置)                           | N                                                                                               | Y                                           | N                                 |
| 6 | 公司 – 授權的裝置 (受監督的裝置)                           | N                                                                                               | N                                           | N                                 |
| 7 | Kiosk 模式 (受監督的裝置) – 授權的裝置 | N                                                                                               | N                                           | N                                 |
| 8 | Kiosk 模式 (受監督的裝置) – 授權的使用者   | --- | ---                                          | ---                                |

> [!Note]  
> 不建議將 VPP 應用程式指派給使用使用者授權的 Kiosk 模式裝置。

## <a name="revoking-app-licenses"></a>撤銷應用程式授權

您可以根據指定的裝置、使用者或應用程式，撤銷所有相關聯的 iOS 或 macOS 大量採購方案 (VPP) 應用程式授權。  但 iOS 和 macOS 平台之間有一些差異。 

|   | iOS | macOS |
|-----|------------------|----------------|
| **移除應用程式指派** | 當您移除已指派給使用者的應用程式，Intune 會回收使用者或裝置授權，並從裝置解除安裝應用程式。 | 當您移除已指派給使用者的應用程式授權時，Intune 會回收該使用者或裝置授權。 該應用程式不會從裝置解除安裝。 |
| **撤銷應用程式授權** | 撤銷應用程式授權會從使用者或裝置回收應用程式授權。 您必須將指派變更為 [解除安裝]  來從裝置移除應用程式。 | 撤銷應用程式授權會從使用者或裝置回收應用程式授權。 具有已撤銷授權的 macOS 應用程式仍可在裝置上使用，但必須等到將授權重新指派給使用者或裝置之後，才能更新。 根據 Apple，這類應用程式會在 30 天的寬限期後移除。 不過，Apple 不會提供讓 Intune 使用 [解除安裝] 指派動作來移除應用程式的方法。

>[!NOTE]
> - 當員工離職且不再屬於 AAD 群組時，Intune 會回收應用程式授權。
> - 將 [解除安裝]  意圖指派給已購買的應用程式時，Intune 會同時回收授權並解除安裝應用程式。
> - 從 Intune 管理移除裝置時，並不會回收應用程式授權。 

## <a name="deleting-vpp-tokens"></a>刪除 VPP 權杖
<!-- 820879 -->  
您可以使用主控台來刪除 Apple 大量採購方案 (VPP) 權杖。 當您擁有重複的 VPP 權杖執行個體時，這可能是必要的。 刪除權杖也會刪除任何相關聯的應用程式和指派。 不過，刪除權杖不會撤銷應用程式授權或解除安裝應用程式。 

>[!NOTE]
>刪除權杖之後，Intune 無法撤銷應用程式授權。 

<!-- 820870 -->  
若要撤銷指定 VPP 權杖的所有 VPP 應用程式的授權，您必須先撤銷與權杖建立關聯的所有應用程式授權，然後刪除權杖。

## <a name="renewing-app-licenses"></a>更新應用程式授權

您可以透過從 Apple Business Manager 或 Apple School Manager 下載新的權杖並在 Intune 中更新現有權杖，來更新 Apple VPP 權杖。

## <a name="deleting-a-vpp-app"></a>刪除 VPP 應用程式

目前，您無法從 Microsoft Intune 刪除 iOS VPP 應用程式。

## <a name="assigning-custom-role-permissions-for-vpp"></a>指派 VPP 的自訂角色權限

您可以使用指派給 Intune 中自訂系統管理員角色的權限，獨立控制 Apple VPP 權杖和 VPP 應用程式的存取權。

* 若要允許 Intune 自訂角色管理 [應用程式]   > [Apple VPP 權杖]  底下的 Apple VPP 權杖，請指派 [受管理的應用程式]  權限。
* 若要允許 Intune 自訂角色管理 [應用程式]   > [所有應用程式]  下使用 iOS VPP 權杖購買的應用程式，請指派 [行動應用程式]  權限。 

## <a name="additional-information"></a>其他資訊

Apple 提供建立和更新 VPP 權杖的直接協助。 如需詳細資訊，請參閱 Apple 文件中的 [ Distribute content to your users with the Volume Purchase Program (VPP)](https://go.microsoft.com/fwlink/?linkid=2014661) (使用大量採購計劃 (VPP) 發佈內容給使用者)。 

如果 Intune 入口網站中指出**已指派給外部 MDM**，您 (系統管理員) 必須先從協力廠商 MDM 移除 VPP 權杖，才能在 Intune 中使用 VPP 權杖。

## <a name="frequently-asked-questions"></a>常見問題集

### <a name="how-many-tokens-can-i-upload"></a>我可以上傳幾個權杖？
您可以在 Intune 中上傳最多 3,000 個權杖。

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>在裝置上安裝或移除應用程式之後，入口網站需要多久的時間才能更新授權計數？
在安裝或解除安裝應用程式之後的幾小時內，應該就會更新授權。 請注意，如果使用者從裝置移除應用程式，該授權仍然會指派給該使用者或裝置。

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>是否可以過度訂閱某個應用程式，如果可以，是在怎樣的情況下？
是。 Intune 系統管理員可以過度訂閱應用程式。 例如，如果系統管理員購買 100 份 XYZ 應用程式的授權，然後將該應用程式的對象設為一個有 500 個成員的群組。 前 100 個成員 (使用者或裝置) 將會獲得授權指派，其餘成員的授權指派則會失敗。


## <a name="next-steps"></a>後續步驟

請參閱[如何監視應用程式](apps-monitor.md)，以取得協助您監視應用程式指派的資訊。

請參閱[如何對應用程式進行疑難排解](~/apps/troubleshoot-app-install.md)，來取得對應用程式相關問題進行疑難排解的相關資訊。
