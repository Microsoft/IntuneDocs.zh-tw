---
title: 針對 Microsoft Intune - Azure 中的裝置設定檔問題進行疑難排解 | Microsoft Docs
description: 對於裝置設定檔的一般問題，包括設定檔變更無法套用至部分使用者或裝置、新的原則會花多少時間推送至裝置、存在多個原則時該套用哪些設定、刪除或移除設定檔時會發生什麼事，以及更多事項，請見 Azure 入口網站中的 Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 1/10/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 32281ae37b7b36dfbf49503275a8a1e6c35d8f6d
ms.sourcegitcommit: 513c59a23ca5dfa80a3ba6fc84068503a4158757
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54210783"
---
# <a name="common-issues-and-resolutions-with-device-profiles-in-microsoft-intune"></a>Microsoft Intune 裝置設定檔的常見問題和解決方式

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

針對使用 Intune 裝置設定檔的一般問題進行疑難排解。

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>在現有的 Wi-Fi 設定檔上變更密碼或複雜密碼時，為什麼使用者不會收到新的設定檔？ 
建立公司的 Wi-Fi 設定檔、將設定檔部署到群組、變更密碼，以及儲存設定檔。 當設定檔變更時，某些使用者可能不會取得新的設定檔。

若要解決這個問題，請設定訪客 Wi-Fi。 如果公司 Wi-Fi 無法使用，使用者可以連線到訪客 Wi-Fi。 請確認啟用任何自動連線設定。 將訪客 Wi-Fi 設定檔部署至所有使用者。

一些其他建議：  

- 因為您正在連線的 Wi-Fi 網路使用了密碼或複雜密碼，請確認您可以直接連線到 Wi-Fi 路由器。 您可以使用 iOS 裝置進行測試。
- 成功連線至 Wi-Fi 端點 (Wi-Fi 路由器) 後，請注意使用的 SSID 和認證 (這個值是密碼或複雜密碼)。
- 在 [預先共用金鑰] 欄位中輸入 SSID 和認證 (密碼或複雜密碼)。 
- 部署到使用者數目有限的測試群組，建議僅限 IT 小組。 
- 將您的 iOS 裝置同步處理到 Intune。 如尚未註冊，請註冊。 
- 再次測試連線到相同的 Wi-Fi 端點 (如第一個步驟中所述)。
- 推出較大的群組，最後是您組織中所有預期的使用者。 

## <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned"></a>指派原則或應用程式之後，行動裝置需要多久時間才能取得這些原則或應用程式？
指派原則或應用程式後，Intune 會立即開始通知裝置簽入 Intune 服務。 通知通常只需要不到五分鐘的時間。

如果在送出第一個通知之後，裝置未簽入以取得原則，Intune 還會另外嘗試三次。 如果裝置處於離線狀態 (例如已關閉或未連線到網路)，則可能不會收到通知。 在這種情況下，裝置會在其下次排定簽入 Intune 服務的時間取得原則，如下所示：

- iOS 和 macOS：每 6 小時
- Android：每 8 小時
- Windows Phone：每 8 小時
- 註冊為裝置的 Windows 8.1 和 Windows 10 電腦：每 8 小時

如果裝置最近剛註冊，簽入頻率會更頻繁，如下所示：

- iOS 和 macOS：前 6 小時每 15 分鐘，之後每 6 小時
- Android：前 15 分鐘每 3 分鐘，之後 2 小時每 15 分鐘，再來每 8 小時
- Windows Phone：前 15 分鐘每 5 分鐘，之後 2 小時每 15 分鐘，再來每 8 小時
- 註冊為裝置的 Windows 電腦：前 30 分鐘每 3 分鐘，之後每 8 小時

若要隨時立即檢查原則，使用者可以開啟公司入口網站應用程式並同步處理裝置。

若為無使用者親和性的裝置，註冊後立即進行的同步處理頻率則為數小時到一或多天不等。 Intune 會以不同的時間間隔傳送要求，讓裝置簽入服務。 不過，仍會以裝置簽入為準。 起始註冊之後，根據裝置註冊類型以及指派給裝置的原則和設定檔會有所不同，因此無法預測裝置完成簽入所需的時間。 不過，一旦裝置完成註冊且套用所有初始原則，裝置通常會約每六小時檢查一次新原則。

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>哪些動作會致使 Intune 立即傳送通知給裝置？
裝置可在收到簽入通知時簽入 Intune，或在其排定簽入時間定期簽入。 當您對目標裝置或使用者執行抹除、鎖定、密碼重設、應用程式指派、設定檔指派或原則指派等動作時，Intune 會立即通知裝置簽入 Intune 服務以接收這些更新。

修訂公司入口網站中的連絡資訊等其他變更，則不會對裝置傳送立即通知。

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>如果有多個原則指派到同一個使用者或同一部裝置，如何得知會套用哪些設定？
如有兩個或多個原則指派到同一個使用者或同一部裝置時，哪些設定會套用於個別設定層級：

- 相容性原則設定一律優先於組態原則設定

- 如果合規性政策中與不同合規性政策中的相同設定一起評估，則會套用限制最嚴格的合規性政策設定。

- 如果設定原則的設定與不同設定原則中的設定衝突，這項衝突會顯示在 Azure 入口網站中。 在此狀況中，請手動解決這些衝突。

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>應用程式保護原則互相衝突時，會發生什麼情況？ 哪一項原則會套用至應用程式？
除了數字輸入欄位 (例如重設前的 PIN 嘗試次數) 之外，衝突值是應用程式保護原則中限制最嚴格的設定。 數字輸入欄位會設定為相同的值，如同您在主控台中使用建議的設定選項建立 MAM 原則一樣。

當兩個設定檔設定相同時，就會發生衝突。 例如，您設定了兩項 MAM 原則，其中除了複製/貼上設定之外，這兩項原則完全相同。 在這種情況下，複製/貼上設定會設定為限制最嚴格的值，但其餘設定則會依照設定來套用。

如果其中一個設定檔指派到應用程式並生效，然後指派第二個設定檔，則會優先使用並持續套用第一個設定檔，而第二個設定檔會顯示為處於衝突狀態。 如果同時套用這兩個設定檔，代表沒有優先的設定檔，則兩者皆處於衝突狀態。 任何衝突的設定都會設為限制最嚴格的值。

## <a name="what-happens-when-ios-custom-policies-conflict"></a>iOS 自訂原則衝突時，會發生什麼情況？
Intune 不會評估 Apple 設定檔或自訂開放行動聯盟的統一資源識別項 (OMA-URI) 設定檔的承載。 它只做為傳遞機制。

當您指派自訂設定檔時，請確定所進行的設定未與合規性、組態或其他自訂原則衝突。 如果自訂的設定檔與其設定衝突，則設定會隨機套用。

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>當設定檔已刪除或不再適用時，會發生什麼情況？
當您刪除設定檔，或從具有該設定檔的群組中移除裝置時，會根據以下清單，從裝置移除該設定檔及設定：

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
當您使用 MDM 或 EAS 設定安全性原則之後，Windows Phone 裝置不允許降低這些原則的安全性。 例如，您將 [字元密碼字元數下限]  設定為 8 個，然後嘗試減少為 4 個。 裝置已套用較嚴格的設定檔。

如果您要將設定檔變更為較不安全的值，請重設安全性原則。 例如，在 Windows 8.1 的桌面上從右向內撥動，然後選取 [設定] > [控制台]。 選取 [使用者帳戶]  小程式。 左導覽功能表底部有一個 [重設安全性原則] 連結。 請加以選取，然後選擇 [重設原則]。

您可能需要淘汰 Android、Windows Phone 8.1 和更新版本、iOS 以及 Windows 10 等其他 MDM 裝置，再重新註冊到服務中，以套用較不嚴格的設定檔。

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Windows 10 設定檔中的某些設定會傳回「不適用」
Windows 10 裝置上的某些設定可能會顯示為「不適用」。 當發生這種情況時，表示在裝置上執行的 Windows 版本或版次不支援該特定設定。 發生此訊息的原因可能如下：

- 此設定僅適用於新版 Windows，並不適用於裝置上的目前作業系統 (OS) 版本。
- 此設定僅適用於特定 Windows 版本或特定 SKU，例如家用版、專業版、企業版和教育版。

若要深入了解不同設定的版本和 SKU 需求，請參閱 [Configuration Service Provider (CSP) reference](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) (設定服務提供者 (CSP) 參考)。

## <a name="next-steps"></a>後續步驟
需要額外說明嗎？ 請參閱[如何取得 Microsoft Intune 支援](get-support.md)。
