---
title: 針對 Microsoft Intune - Azure 中的裝置設定檔問題進行疑難排解 | Microsoft Docs
description: 對於裝置原則與設定檔的常見疑問和解答，包括設定檔變更未套用至使用者或裝置、新的原則會花多少時間推送至裝置、存在多個原則時該套用哪些設定、刪除或移除設定檔時會發生什麼事，以及與 Microsoft Intune 相關的其他事項。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/15/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7779e265680ded1b5d5d5b670bcf694376ee8016
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72494410"
---
# <a name="common-questions-issues-and-resolutions-with-device-policies-and-profiles-in-microsoft-intune"></a>對於 Microsoft Intune 中的裝置原則和設定檔的常見疑問、問題和解決方式

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

獲得使用 Intune 中裝置設定檔與原則時的常見問題解答。 本文也列出簽入時間間隔、提供更多衝突的相關詳細資料等等。

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>在現有的 Wi-Fi 設定檔上變更密碼或複雜密碼時，為什麼使用者不會收到新的設定檔？

建立公司的 Wi-Fi 設定檔、將設定檔部署到群組、變更密碼，以及儲存設定檔。 當設定檔變更時，某些使用者可能不會取得新的設定檔。

若要解決這個問題，請設定訪客 Wi-Fi。 如果公司 Wi-Fi 無法使用，使用者可以連線到訪客 Wi-Fi。 請確認啟用任何自動連線設定。 將訪客 Wi-Fi 設定檔部署至所有使用者。

一些其他建議：  

- 如果您正在連線的 Wi-Fi 網路使用密碼或複雜密碼，請確認您可以直接連線到 Wi-Fi 路由器。 您可以使用 iOS 裝置進行測試。
- 成功連線至 Wi-Fi 端點 (Wi-Fi 路由器) 後，請注意使用的 SSID 和認證 (這個值是密碼或複雜密碼)。
- 在 [預先共用金鑰] 欄位中輸入 SSID 和認證 (密碼或複雜密碼)。 
- 部署到使用者數目有限的測試群組，建議僅限 IT 小組。 
- 將您的 iOS 裝置同步處理到 Intune。 如尚未註冊，請註冊。 
- 再次測試連線到相同的 Wi-Fi 端點 (如第一個步驟中所述)。
- 推出較大的群組，最後是您組織中所有預期的使用者。 

## <a name="how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned"></a>為裝置指派原則、設定檔或應用程式之後，它們需要多久時間才能取得這些原則、設定檔或應用程式？

Intune 會通知裝置使用 Intune 服務簽入。 通知時間各不相同，包括立即到最多數小時。 這些通知時間也會因平台而異。

如果裝置未在第一個通知之後簽入以取得原則或設定檔，Intune 還會另外嘗試三次。 離線裝置 (例如已關閉或未連線到網路) 可能不會收到通知。 在這種情況下，裝置會在其下一次使用 Intune 服務簽入時取得原則或設定檔，**估計**為：

| 平台 | 重新整理週期|
| --- | --- |
| iOS | 大約每 8 小時 |
| macOS | 大約每 8 小時 |
| Android | 大約每 8 小時 |
| 註冊為裝置的 Windows 10 電腦 | 大約每 8 小時 |
| Windows Phone | 大約每 8 小時 |
| Windows 8.1 | 大約每 8 小時 |

如果裝置是最近註冊的，則合規性和設定簽入的執行頻率比較高，**估計**為：

| 平台 | 頻率 |
| --- | --- |
| iOS | 前 1 小時每 15 分鐘，之後大約每 8 小時 |  
| macOS | 前 1 小時每 15 分鐘，之後大約每 8 小時 | 
| Android | 前 15 分鐘每 3 分鐘，之後 2 小時每 15 分鐘，再來大約每 8 小時 | 
| 註冊為裝置的 Windows 10 電腦 | 前 15 分鐘每 3 分鐘，之後 2 小時每 15 分鐘，再來大約每 8 小時 | 
| Windows Phone | 前 15 分鐘每 5 分鐘，之後 2 小時每 15 分鐘，再來大約每 8 小時 | 
| Windows 8.1 | 前 15 分鐘每 5 分鐘，之後 2 小時每 15 分鐘，再來大約每 8 小時 | 

使用者隨時都可開啟公司入口網站應用程式中的 [設定]   > [同步處理]  ，以立即檢查是否有原則或設定檔更新。

若為無使用者親和性的裝置，註冊後立即進行的同步處理頻率可以從數小時到一或多天不等。 Intune 會以不同的時間間隔傳送要求，讓裝置簽入 Intune。 不過，仍會以裝置簽入為準。 一開始註冊之後，裝置完成簽入所需的時間是無法預測的。 它也取決於裝置註冊的類型，以及指派給裝置的原則和設定檔。 在裝置註冊並套用所有初始原則和設定檔之後，裝置會根據裝置在 Intune 中註冊的時間，檢查是否有每 6-8 小時的新原則和設定檔。

最佳做法是確定您的裝置至少連續八小時處於連線狀態，才能得到最佳結果。

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>哪些動作會致使 Intune 立即傳送通知給裝置？

有多種會觸發通知的動作，例如，何時指派 (或取消指派)、更新、刪除原則、設定檔或應用程式等。 這些動作時間會因平台而異。

裝置可在收到簽入通知時簽入 Intune，或在其排定簽入時間簽入。 當您對目標裝置或使用者執行鎖定、密碼重設、應用程式指派、設定檔指派或原則指派等動作時，則 Intune 會立即通知裝置簽入以接收這些更新。

修訂公司入口網站應用程式中的連絡資訊等其他變更，不會立即對裝置傳送通知。

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>如果有多個原則指派到同一個使用者或同一部裝置，如何得知會套用哪些設定？

請注意，當有兩個或多個原則指派到同一個使用者或同一部裝置時，所套用的設定將會在個別的設定層級進行：

- 合規性政策設定一律優先於組態設定檔設定。

- 如果合規性政策針對另一個合規性政策中的相同設定進行評估，則會套用限制最嚴格的合規性政策設定。

- 如果設定原則的設定與另一個設定原則中的設定衝突，這項衝突會顯示在 Intune 中。 請手動解決這些衝突。

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>應用程式保護原則互相衝突時，會發生什麼情況？ 哪一項原則會套用至應用程式？

*除了*數字輸入欄位 (例如重設前的 PIN 嘗試次數) 之外，衝突值是應用程式保護原則中限制最嚴格的設定。 數字輸入欄位會設定為相同的值，如同您使用建議的設定選項建立 MAM 原則一樣。

當兩個設定檔設定相同時，就會發生衝突。 例如，您設定了兩項 MAM 原則，其中除了複製/貼上設定之外，這兩項原則完全相同。 在這種情況下，複製/貼上設定會設定為限制最嚴格的值，但其餘設定則會依照設定來套用。

原則會部署至應用程式並生效。 接著再部署另一個原則。 在此案例中，第一個原則會優先使用並持續套用。 第二個原則會顯示衝突。 如果同時套用這兩個原則，代表沒有優先的原則，則兩者處於衝突狀態。 任何衝突的設定都會設為限制最嚴格的值。

## <a name="what-happens-when-ios-custom-policies-conflict"></a>iOS 自訂原則衝突時，會發生什麼情況？

Intune 不會評估 Apple 設定檔或自訂開放行動聯盟的統一資源識別項 (OMA-URI) 原則的承載。 它只做為傳遞機制。

當您指派自訂原則時，請確認所進行的設定未與合規性、設定或其他自訂原則衝突。 如果自訂原則及其設定衝突，則會隨機套用設定。

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>當設定檔已刪除或不再適用時，會發生什麼情況？

當您刪除設定檔，或從具有該設定檔的群組中移除裝置之後，接著會從裝置中移除該設定檔及設定，如下所述：

- Wi-Fi、VPN、憑證及電子郵件設定檔：這些設定檔會從所有支援的已註冊裝置中移除。
- 所有其他設定檔類型：  

  - **Windows 和 Android 裝置**：設定不會從裝置中移除
  - **Windows Phone 8.1 裝置**：下列設定會予以移除：  
  
    - 需要密碼來解除鎖定行動裝置
    - 允許簡單密碼
    - 密碼長度下限
    - 所需的密碼類型
    - 密碼到期 (天數)
    - 記住密碼歷程記錄
    - 抹除裝置前允許的重複登入失敗次數
    - 要求密碼前的閒置分鐘數
    - 需要的密碼類型 – 最小字元集數
    - 允許相機
    - 在行動裝置上要求加密
    - 允許卸除式存放裝置
    - 允許網頁瀏覽器
    - 允許應用程式市集
    - 允許螢幕擷取
    - 允許地理位置
    - 允許 Microsoft 帳戶
    - 允許複製並貼上
    - 允許 Wi-Fi 網際網路共用功能
    - 允許自動連線到免費的 Wi-Fi 熱點
    - 允許 Wi-Fi 熱點回報
    - 允許抹除
    - 允許藍芽
    - 允許 NFC
    - 允許 Wi-Fi

  - **iOS**：移除所有設定，除了：
  
    - 允許語音漫遊
    - 允許數據漫遊
    - 允許漫遊時自動同步處理

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>我變更了裝置限制設定檔，但變更一直沒有作用

一旦設定之後，Windows Phone 裝置便不允許使用 MDM 或 EAS 設定的安全性原則降低安全性。 例如，您將 [字元密碼字元數下限]  設定為 8 個。 然後您嘗試將其減少為 4 個。 裝置已套用較嚴格的設定檔。

若要將設定檔變更為較不安全的值，請重設安全性原則。 例如，在 Windows 8.1 的桌面上從右向內撥動，然後選取 [設定]   > [控制台]  。 選取 [使用者帳戶]  小程式。 左導覽功能表底部有一個 [重設安全性原則]  連結。 請加以選取，然後選擇 [重設原則]  。

您可能需要淘汰 Android、Windows Phone 8.1 和更新版本、iOS 以及 Windows 10 等其他 MDM 裝置，再重新註冊到 Intune 中，以套用較不嚴格的設定檔。

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Windows 10 設定檔中的某些設定會傳回「不適用」

Windows 10 裝置上的某些設定可能會顯示為「不適用」。 當發生這種情況時，表示在裝置上執行的 Windows 版本或版次不支援該特定設定。 發生此訊息的原因可能如下：

- 此設定僅適用於新版 Windows，並不適用於裝置上的目前作業系統 (OS) 版本。
- 此設定僅適用於特定 Windows 版本或特定 SKU，例如家用版、專業版、企業版和教育版。

若要深入了解不同設定的版本和 SKU 需求，請參閱 [Configuration Service Provider (CSP) reference](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) (設定服務提供者 (CSP) 參考)。

## <a name="next-steps"></a>後續步驟

需要額外說明嗎？ 請參閱[如何取得 Microsoft Intune 支援](../fundamentals/get-support.md)。
