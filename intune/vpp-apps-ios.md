---
title: 在 Microsoft Intune 中管理 iOS 大量採購的應用程式
titlesuffix: ''
description: 針對從 iOS Store 大量採購的應用程式，了解如何將應用程式同步到 Microsoft Intune，然後管理及並追蹤其使用情況。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cbe9f28b66031f6eddef4804c157f01ca79ad81d
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347513"
---
# <a name="how-to-manage-ios-apps-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

iOS App Store 可讓您購買多個想要在公司內執行的應用程式授權。 購買多個複本有助於您在公司中有效率地管理應用程式。

Microsoft Intune 可透過下列方式協助您管理透過此計畫購買的多個應用程式複本：

- 從應用程式市集報告授權資訊。
- 追蹤您已經使用多少個授權。
- 協助您不要安裝超過擁有數目的應用程式複本。

您可以使用兩種方法來指派大量採購的應用程式：

### <a name="device-licensing"></a>裝置授權

當您將一個應用程式指派給多部裝置時，會使用一個應用程式授權，並與您指派的目標裝置保持關聯。

當您將大量採購的應用程式指派給一部裝置時，裝置的終端使用者不需要提供 Apple ID 來存取市集。

### <a name="user-licensing"></a>使用者授權

當您將應用程式指派給使用者時，會使用一個應用程式授權，並與使用者建立關聯。 該應用程式可以在使用者擁有的多部裝置上執行 (受 Apple 有限控制)。

當您將大量採購的應用程式指派給多位使用者時，每位終端使用者都必須具備有效和唯一的 Apple ID，才能存取 App Store。

此外，針對從 Apple 大量採購方案 (VPP) 市集購買的書籍，您可以使用 Intune 來進行同步處理、管理及指派。 如需詳細資訊，請參閱[如何管理透過大量採購方案購買的 iOS 電子書](vpp-ebooks-ios.md)。

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>管理大量採購的 iOS 裝置應用程式

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps-for-ios-devices"></a>iOS 裝置支援 Apple 大量採購方案大量採購的應用程式

請透過[商務 Apple 大量採購方案](http://www.apple.com/business/vpp/)或[教育 Apple 大量採購方案](http://volume.itunes.apple.com/us/store)，購買多份 iOS 應用程式授權。 這項程序包括從 Apple 網站設定 Apple VPP 帳戶，並將 Apple VPP 權杖上傳到 Intune。  您可以將您的大量採購資訊與 Intune 同步處理，並追蹤大量採購的應用程式使用情況。

### <a name="supports-business-to-business-volume-purchased-apps-for-ios-devices"></a>iOS 裝置支援企業對企業大量採購的應用程式

此外，協力廠商開發人員也可以私下將應用程式散發給 iTunes Connect 中所指定的授權企業大量採購方案成員。 這些企業 VPP 成員可以登入大量採購方案 App Store，並購買其應用程式。 終端使用者所購買的企業 VPP 應用程式將與其 Intune 租用戶同步。

## <a name="before-you-start"></a>開始之前
在開始之前，您必須從 Apple 取得 VPP 權杖，並將它上傳至您的 Intune 帳戶。 此外，您還應該了解下列準則︰

* 您可以讓多個 VPP 權杖與 Intune 帳戶建立關聯。
* 之前如有其他產品已使用過 VPP 權杖，您必須產生新的權杖來搭配 Intune 使用。
* 每個權杖有效期限為一年。
* Intune 預設與 Apple VPP 服務一天進行兩次同步處理。 您可以在任何時間啟動手動同步處理。
* 開始搭配 Intune 使用 Apple VPP 之前，請移除任何以其他行動裝置管理 (MDM) 廠商所建立的現有 VPP 使用者帳戶。 基於安全性考量，Intune 不會把這些使用者帳戶同步處理到 Intune。 Intune 只會同步處理 Intune 所建立的 Apple VPP 服務資料。
* Intune 支援新增最多 256 個 VPP 權杖。
* Apple 的裝置註冊設定檔 (DEP) 方案會自動化行動裝置管理 (MDM) 註冊。 使用 DEP，您可以設定企業裝置，而不需要碰觸它們。 您可以使用與 Apple 之 VPP 搭配使用的相同方案代理程式帳戶來註冊 DEP 方案。 Apple 部署方案識別碼對 [Apple Deployment Programs](https://deploy.apple.com) 網站下所列的方案而言是唯一的，而且無法用來登入 iTunes 商店這類 Apple 服務。
* 當您使用使用者授權模型指派 VPP 應用程式給使用者或裝置 (具有使用者親和性) 時，每個 Intune 使用者在裝置上接受 Apple 條款和條件時，都必須與唯一的 Apple ID 或電子郵件地址建立關聯。 請確定當您為新 Intune 使用者設定裝置時，以該使用者的唯一 Apple ID 或電子郵件地址來進行設定。 Apple ID 或電子郵件地址和 Intune 使用者形成唯一的組合，並可以用於多達五部裝置。
* VPP 權杖只支援一次用於一個 Intune 帳戶。 請勿將相同的 VPP 權杖重複用於多個 Intune 租用戶。
* 當您使用使用者授權模型指派 VPP 應用程式給使用者或裝置 (具有使用者親和性) 時，每個 Intune 使用者在裝置上接受 Apple 條款和條件時，都必須與唯一的 Apple ID 或電子郵件地址建立關聯。
請確定當您為新 Intune 使用者設定裝置時，您用該使用者的唯一 Apple ID 或電子郵件地址來進行設定。 Apple ID 或電子郵件地址和 Intune 使用者形成唯一的組合，並可以用於多達五部裝置。

>[!IMPORTANT]
>在您將 VPP 權杖匯入到 Intune 之後，請不要將相同的權杖匯入到任何其他裝置管理解決方案。 這樣做會導致授權指派與使用者記錄遺失。

## <a name="to-get-and-upload-an-apple-vpp-token"></a>取得並上傳 Apple VPP 權杖

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3.  在 [Intune] 窗格上，選擇 [設定] 下的 [用戶端應用程式] > [iOS VPP 權杖]。
4.  在 VPP 權杖清單窗格上，選取 [建立]。
5. 在 [建立 VPP 權杖] 窗格上，指定下列資訊：
    - **VPP 權杖檔案** - 若您尚未註冊，請註冊商務大量採購方案或教育方案。 註冊之後，請下載您帳戶的 Apple VPP 權杖，然後在這裡選取它。
    - **Apple ID** - 輸入與大量採購方案相關聯之帳戶的 Apple ID。
    - **國家/地區** - 選取 VPP 國家/地區市集。  Intune 會從指定的 VPP 國家/地區市集同步處理所有地區設定的 VPP 應用程式。
        > [!WARNING]  
        > 變更國家/地區，將會更新應用程式中繼資料，並且為使用此權杖建立的應用程式，更新下次與 Apple 服務同步時的存放區 URL 。 如果應用程式不存在於新的國家/地區市集，即不會更新應用程式。

    - **VPP 帳戶類型** - 請選擇 [商務] 或 [教育]。
    - **自動更新應用程式** - 從 [開啟] 選擇為 [關閉]，以啟用自動更新。 若啟用，Intune 會偵測應用程式市集內的 VPP 應用程式更新，並在裝置簽入時將更新自動推送至裝置。
        > [!NOTE]
        > 自動應用程式更新適用於 iOS 11.0 版和更新版本的裝置和使用者授權應用程式。
6. 完成之後，請選取 [建立]。

該權杖會顯示在權杖清單窗格內。

您可以隨時選擇 [立即同步處理]，使用 Intune 同步處理 Apple 所儲存的資料。

## <a name="to-assign-a-volume-purchased-app"></a>指派大量採購應用程式

1.  在 [Intune] 窗格上，選擇 [管理] 下的 [用戶端應用程式] > [應用程式]。
2.  在應用程式窗格清單上，選擇您要指派的應用程式，然後選擇 [指派]。
3.  在 [應用程式名稱] - [指派] 窗格上，選擇 [新增群組]，然後在 [新增群組] 窗格中選擇 [指派類型]，選擇要指派該應用程式的 Azure AD 使用者或裝置群組。
5.  針對您選取的每個群組，選擇下列設定：
    - **類型** - 選擇應用程式會是 [可用] (終端使用者可以從公司入口網站安裝應用程式) 或 [必要] (終端使用者的裝置會自動安裝應用程式)。
    - **授權類型** - 選擇 [使用者授權] 或 [裝置授權]。
6.  完成之後，請選擇 [儲存]。


>[!NOTE]
>顯示的應用程式清單與權杖建立關聯。 如果您的應用程式與多個 VPP 權杖建立關聯，您會看到相同的應用程式顯示多次；針對每個權杖各一次。

## <a name="end-user-prompts-for-vpp"></a>VPP 的終端使用者提示

終端使用者將會在許多案例中收到 VPP 應用程式安裝的提示。 下表說明每個狀況：

| # | 案例                                | 邀請加入 Apple VPP 方案                              | 應用程式安裝提示 | 提示輸入 Apple ID |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD – 授權的使用者                             | Y                                                                                               | Y                                           | Y                                 |
| 2 | 公司 – 授權的使用者 (不受監督的裝置)     | Y                                                                                               | Y                                           | Y                                 |
| 3 | 公司 – 授權的使用者 (受監督的裝置)         | Y                                                                                               | N                                           | Y                                 |
| 4 | BYOD – 授權的裝置                           | N                                                                                               | Y                                           | N                                 |
| 5 | 公司 – 授權的裝置 (不受監督的裝置)                           | N                                                                                               | Y                                           | N                                 |
| 6 | 公司 – 授權的裝置 (受監督的裝置)                           | N                                                                                               | N                                           | N                                 |
| 7 | Kiosk 模式 (受監督的裝置) – 授權的裝置 | N                                                                                               | N                                           | N                                 |
| 8 | Kiosk 模式 (受監督的裝置) – 授權的使用者   | --- | ---                                          | ---                                |

> [!Note]  
> 不建議將 VPP 應用程式指派給使用 VPP 使用者授權的 Kiosk 模式裝置。

## <a name="revoking-app-licenses-and-deleting-tokens"></a>撤銷應用程式授權和刪除權杖 

您可以根據指定的裝置、使用者或應用程式，撤銷所有相關聯的 iOS 大量採購方案 (VPP) 應用程式授權。 當應用程式不再指派給使用者時，您可以通知他們。 撤銷應用程式授權將不會從該裝置解除安裝相關聯的 VPP 應用程式。 若要解除安裝 VPP 應用程式，並回收指派給使用者或裝置的應用程式授權，您必須將指派動作變更為 [解除安裝]。 當您移除已指派給使用者的應用程式，Intune 會回收使用者或裝置授權，並從裝置解除安裝應用程式。 回收的授權計數將會反映在 Intune 之 [應用程式] 工作負載中的 [授權的應用程式] 節點。 一旦解除安裝 VPP 應用程式並回收應用程式授權，您可以選擇將應用程式授權指派給其他使用者或裝置。 

>[!NOTE]
>當員工離職且不再屬於 AAD 群組時，Intune 會擷取所有使用者授權的 iOS VPP 應用程式授權。

<!-- 820879 -->  
您可以使用主控台來刪除 iOS 大量採購方案 (VPP) 權杖。 當您擁有重複的 VPP 權杖執行個體時，這可能是必要的。 刪除權杖也會刪除任何相關聯的應用程式和指派。 不過，刪除權杖不會撤銷應用程式授權或解除安裝應用程式。 

>[!NOTE]
>刪除權杖之後，Intune 無法撤銷應用程式授權。 

<!-- 820870 -->  
若要撤銷指定 VPP 權杖的所有 VPP 應用程式的授權，您必須先撤銷與權杖建立關聯的所有應用程式授權，然後刪除權杖。

## <a name="renewing-app-licenses"></a>更新應用程式授權

您可以透過從 Apple 大量採購方案入口網站下載新的權杖並在 Intune 中更新現有權杖，來更新 Apple VPP 權杖。

## <a name="deleting-an-ios-vpp-app"></a>刪除 iOS VPP 應用程式

目前，您無法從 Microsoft Intune 刪除 iOS VPP 應用程式。

## <a name="additional-information"></a>其他資訊

當具有合格裝置的使用者第一次嘗試將 VPP 應用程式安裝至裝置時，系統會要求他們加入 Apple 大量採購方案。 他們必須加入，應用程式安裝才會繼續執行。 對於加入 Apple 大量採購方案的邀請，需要使用者能夠在 iOS 裝置上使用 iTunes 應用程式。 如果您已經設定停用 iTunes Store 應用程式的原則，則 VPP 應用程式以使用者為基礎的授權將無法運作。 解決方法是移除原則以允許 iTunes 應用程式，或是使用以裝置為基礎的授權。

Apple 提供建立和更新 VPP 權杖的直接協助。 如需詳細資訊，請參閱 Apple 文件中的 [ Distribute content to your users with the Volume Purchase Program (VPP)](https://go.microsoft.com/fwlink/?linkid=2014661) (使用大量採購計劃 (VPP) 發佈內容給使用者)。 

如果 Intune 入口網站中指出**已指派給外部 MDM**，您 (系統管理員) 必須先從協力廠商 MDM 移除 VPP 權杖，才能在 Intune 中使用 VPP 權杖。

## <a name="frequently-asked-questions"></a>常見問題集

#### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>在裝置上安裝或移除應用程式之後，入口網站需要多久的時間才能更新授權計數？
在安裝或解除安裝應用程式之後的幾小時內，應該就會更新授權。 請注意，如果使用者從裝置移除應用程式，該授權仍然會指派給該使用者或裝置。

#### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>是否可以過度訂閱某個應用程式，如果可以，是在怎樣的情況下？
是。 Intune 系統管理員可以過度訂閱應用程式。 例如，如果系統管理員購買 100 份 XYZ 應用程式的授權，然後將該應用程式的對象設為一個有 500 個成員的群組。 前 100 個成員 (使用者或裝置) 將會獲得授權指派，其餘成員的授權指派則會失敗。

#### <a name="i-understand-intune-automatically-syncs-app-licenses-each-day-with-apple-is-that-correct"></a>就我所知，Intune 每天都會與 Apple 自動同步應用程式授權，對嗎？
Intune 會每天兩次與 Apple 同步應用程式授權。

## <a name="next-steps"></a>接下來的步驟

請參閱[如何監視應用程式](apps-monitor.md)，以取得協助您監視應用程式指派的資訊。
