---
title: "針對 Microsoft Intune 中的裝置設定檔問題進行疑難排解"
titlesuffix: Azure portal
description: "當您遭遇難解的問題時，可使用本主題協助您解決 Intune 裝置設定檔的問題。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ff950ce35c491ca576dc9cc77ab561e2cfef0381
ms.sourcegitcommit: 1df625330f4e8f7f661b5f2b9f16b5590971838d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2017
---
# <a name="troubleshooting-device-profiles-in-microsoft-intune"></a>針對 Microsoft Intune 中的裝置設定檔問題進行疑難排解


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主題中的資訊可協助您針對 Intune 裝置設定檔的常見問題進行疑難排解。

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>在現有的 Wi-Fi 設定檔上變更密碼或複雜密碼時，為什麼使用者不會收到新的設定檔？ 
當您建立公司的 Wi-Fi 設定檔、將設定檔部署到群組、變更密碼，以及儲存設定檔時，您可能希望使用者會收到新的設定檔。 不過，使用者可能不會取得新的設定檔。 

為緩和這個問題，請確定您已設定客體 Wi-Fi，讓使用者在公司 Wi-Fi 失敗時可回到客體 Wi-Fi。 需要啟用自動連線設定。 此客體 Wi-Fi 設定檔需要部署至所有使用者。

另有一些最佳做法可以遵循：
- 既然您正在連接的 Wi-Fi 網路採用密碼或複雜密碼，請確定您可以直接連接到 Wi-Fi 路由器。 您可以使用 iOS 裝置進行測試。
- 成功連線至 Wi-Fi 端點 (Wi-Fi 路由器) 後，請注意使用的 SSID 和認證 (這是密碼或複雜密碼)。
- 在 [預先共用金鑰] 欄位中輸入 SSID 和認證 (密碼或複雜密碼)。 
- 部署到使用者數目有限的測試群組，最好是僅限 IT 小組。 
- 將您的 iOS 裝置同步處理到 Intune。 如尚未註冊，請註冊。 
- 再次測試連線到相同的 Wi-Fi 端點 (如第一個步驟中所述)。
- 推出較大的群組，最後是您組織中所有預期的使用者。 

## <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned"></a>指派原則或應用程式之後，行動裝置需要多久時間才能取得這些原則或應用程式？
指派原則或應用程式後，Intune 會立即開始嘗試通知裝置，指出裝置應該簽入 Intune 服務。 這通常只需要不到 5 分鐘的時間。

如果在送出第一個通知之後，裝置未簽入以取得原則，Intune 還會另外嘗試三次。  如果裝置處於離線狀態 (例如已關閉或未連線到網路)，則可能不會收到通知。 在這種情況下，裝置會在其下次排定簽入 Intune 服務的時間取得原則，如下所示：

- iOS 和 macOS：每 6 小時。
- Android：每 8 小時。
- Windows Phone：每 8 小時。
- 註冊為裝置的 Windows 8.1 和 Windows 10 電腦：每 8 小時。

如果裝置剛註冊，簽入頻率會更頻繁，如下所示：

- iOS 和 macOS：前 6 小時每 15 分鐘，之後每 6 小時。
- Android：前 15 分鐘每 3 分鐘，之後 2 小時每 15 分鐘，再來每 8 小時。
- Windows Phone：前 15 分鐘每 5 分鐘，之後 2 小時每 15 分鐘，再來每 8 小時。
- Windows 電腦註冊為裝置：前 30 分鐘每 3 分鐘，之後每 8 小時。

使用者也可以開啟公司入口網站應用程式並同步處理裝置，以隨時立即檢查是否有原則。

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>哪些動作會致使 Intune 立即傳送通知給裝置？
裝置可在收到簽入通知時簽入 Intune，或在它們的排定簽入時間定期簽入。  當您對目標裝置或使用者執行抹除、鎖定、密碼重設、應用程式指派、設定檔指派 (Wi-Fi、VPN、電子郵件等) 或原則指派等特定動作時，Intune 會立即開始嘗試通知裝置，指出裝置應該簽入 Intune 服務才能接收這些更新。

修訂公司入口網站中的連絡資訊等其他變更，則不會對裝置傳送立即通知。

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-will-get-applied"></a>如果有多個原則指派到同一個使用者或同一部裝置，如何得知將套用哪些設定？
請注意，當有兩個或多個原則指派到同一個使用者或同一部裝置時，會在個別設定層級評估要套用哪個設定：

-   合規性政策設定一律優先於設定原則設定。

-   如果與不同合規性政策中的相同設定一起評估，則會套用限制最嚴格的合規性政策設定。

-   如果設定原則的設定與不同設定原則中的設定衝突，這項衝突會顯示在 Azure 入口網站中。 您必須以手動方式解決此類衝突。

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-will-be-applied-to-the-app"></a>應用程式保護原則互相衝突時，會發生什麼情況？ 哪一個原則會套用至應用程式？
除了數字輸入欄位 (例如重設前的 PIN 嘗試次數) 之外，衝突值是應用程式保護原則中限制最嚴格的設定。  數字輸入欄位會設定為相同的值，如同您在主控台中使用建議的設定選項建立 MAM 原則一樣。

當兩個設定檔設定相同時，就會發生衝突。  例如，您設定了兩項 MAM 原則，其中除了複製/貼上設定之外，這兩項原則完全相同。  在這種情況下，複製/貼上設定會設定為限制最嚴格的值，但其餘設定則會依照設定來套用。

如果其中一個設定檔指派到應用程式並生效，然後再指派第二個設定檔，則會優先使用並持續套用第一個設定檔，而第二個設定檔會顯示為處於衝突狀態。 如果同時套用這兩個設定檔，代表沒有優先的設定檔，則兩者皆處於衝突狀態。 任何衝突的設定將設為限制最嚴格的值。

## <a name="what-happens-when-ios-custom-policies-conflict"></a>iOS 自訂原則衝突時，會發生什麼情況？
Intune 不會評估 Apple 設定檔或自訂開放行動聯盟的統一資源識別項 (OMA-URI) 設定檔的承載。 它只做為傳遞機制。

當您指派自訂設定檔時，請確定所進行的設定未與合規性、組態或其他自訂原則衝突。 如果是具有設定衝突的自訂設定檔案例，則會依隨機順序來套用設定。

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>當設定檔已刪除或不再適用時，會發生什麼情況？
當您刪除設定檔，或從群組中移除已經指派設定檔的裝置時，將會根據以下清單，從裝置移除該設定檔及設定。

### <a name="enrolled-devices"></a>已註冊的裝置

- Wi-Fi、VPN、憑證及電子郵件設定檔：這些設定檔會從所有支援的已註冊裝置中移除。
- 所有其他設定檔類型：
    - [Windows 和 Android 裝置]：設定不會從裝置中移除。
    - [Windows Phone 8.1 裝置]：會移除下列設定：
        - 需要密碼來解除鎖定行動裝置
        - 允許簡單密碼
        - 最小密碼長度
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
        - 允許原廠重設
        - 允許藍芽
        - 允許 NFC
        - 允許 Wi-Fi

    - [iOS]：移除所有設定，除了︰
        - 允許語音漫遊
        - 允許數據漫遊
        - 允許漫遊時自動同步處理

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>我變更了裝置限制設定檔，但變更一直沒有作用
當您透過 MDM 或 EAS 設定安全性原則之後，Windows Phone 裝置不允許降低這些原則的安全性。 例如，您將 [字元密碼數目下限]  設定為 8，然後嘗試減少為 4。 裝置已套用較嚴格的設定檔。

視裝置平台而定，如果您要將設定檔變更為較不安全的值，您可能需要重設安全性原則。
例如，在 Windows 的桌面上，從右向內撥動以開啟 [快速鍵] 列，然後選擇 [設定] &gt; [控制台]。  選取 [使用者帳戶]  小程式。
左導覽功能表底部有一個 [重設安全性原則]  連結。 選擇該連結，然後選擇 **[重設原則]** 按鈕。
您可能需要停用 Android、Windows Phone 8.1 與更新版本及 iOS 等其他 MDM 裝置，再重新註冊到服務中，才能套用較不嚴格的設定檔。


### <a name="next-steps"></a>後續步驟
如果此疑難排解資訊對您沒有幫助，請連絡 Microsoft 支援服務 (如[如何取得 Microsoft Intune 支援](get-support.md)中所述)。