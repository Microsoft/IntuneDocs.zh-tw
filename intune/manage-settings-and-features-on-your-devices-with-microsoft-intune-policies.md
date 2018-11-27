---
title: Intune 的裝置原則、設定檔和問與答 - Azure | Microsoft Docs
description: 閱讀您可以在 Microsoft Intune 中使用的不同原則和設定檔，包括設定裝置、存取公司資源、啟用條件式存取及註冊公司裝置的原則。 此外，取得常見問題的解答。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ROBOTS: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 3b1115a91707c639caba6410ace3c2e255e40a39
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184993"
---
# <a name="manage-settings-and-features-on-your-devices-with-intune-policies"></a>透過 Intune 原則管理裝置上的設定和功能

Microsoft Intune *原則*是控制行動裝置和電腦功能的設定群組。 您可以使用包含建議或自訂設定的範本建立原則。 然後將原則部署到裝置或使用者群組。

## <a name="types-of-policies"></a>原則類型

Intune 原則可分為以下類別。 您使用的類別會影響您建立和部署原則的方式。

- **設定原則**︰通常用來管理您裝置的安全性設定和功能，包括對公司資源的存取。 從 [Intune 裝置設定檔](device-profiles.md)開始使用。
- **裝置合規性政策**：定義裝置必須符合，才能被條件式存取原則視為符合規範的規則與設定。 您也可以使用相容性原則，來監視和修復與條件式存取無關的裝置相容性。 開始使用[裝置合規性政策](device-compliance-get-started.md)。
- **條件式存取原則**：協助您依據輸入的條件保護電子郵件及其他服務。 [什麼是條件式存取](conditional-access.md)和[使用條件式存取的常見方式](conditional-access-intune-common-ways-use.md)都是開始使用的不錯資源。
- **公司裝置註冊原則**：如需公司裝置註冊原則的資訊，請參閱[註冊 iOS 裝置](ios-enroll.md)。

## <a name="frequently-asked-questions-about-intune-policies"></a>Intune 原則常見問題

### <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-being-deployed"></a>部署原則或應用程式之後，行動裝置需要多久時間才能取得這些原則或應用程式？
部署原則或應用程式後，Intune 會立即開始通知裝置簽入 Intune 服務。 此步驟通常需要不到五分鐘的時間。

如果在送出第一個通知之後，裝置未簽入以取得原則，Intune 還會另外嘗試三次。  如果裝置處於離線狀態 (例如已關閉或未連線到網路)，則可能不會收到通知。 在這種情況下，裝置會在其下次排定簽入 Intune 服務的時間取得原則，如下所示：

| 平台 | 簽入頻率 |
| --- | --- |
| iOS | 每 6 小時 | 
| Mac OS X | 每 6 小時 |
| Android | 每 8 小時 | 
| Windows Phone | 每 8 小時 | 
| Windows 8.1  | 每 8 小時 |  
| 註冊為裝置的 Windows 10 電腦 | 每 8 小時 | 

如果裝置最近剛註冊，簽入頻率會更頻繁，如下所示：

| 平台 | 頻率 |
| --- | --- |
| iOS | 前 6 小時每 15 分鐘，之後每 6 小時 |  
| Mac OS X | 前 6 小時每 15 分鐘，之後每 6 小時 | 
| Android | 前 15 分鐘每 3 分鐘，之後 2 小時每 15 分鐘，再來每 8 小時 | 
| Windows Phone | 前 15 分鐘每 5 分鐘，之後 2 小時每 15 分鐘，再來每 8 小時 | 
| 註冊為裝置的 Windows 電腦 | 前 30 分鐘每 3 分鐘，之後每 8 小時 | 

使用者也可以開啟公司入口網站應用程式並同步處理裝置，以隨時立即檢查是否有原則。

### <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>哪些動作會致使 Intune 立即傳送通知給裝置？
裝置可在收到簽入通知時簽入 Intune，或在它們的排定簽入時間定期簽入。  當您想要對目標裝置或使用者執行抹除、鎖定、重設密碼、應用程式部署、設定檔部署 (Wi-Fi、VPN、電子郵件) 或原則部署等動作時，Intune 會立即嘗試通知裝置簽入 Intune 服務。

修訂公司入口網站中的連絡資訊等其他變更，則不會對裝置傳送立即通知。

### <a name="if-multiple-policies-are-deployed-to-the-same-user-or-device-how-do-i-know-which-settings-are-applied"></a>如果有多項原則部署到同一位使用者或同一部裝置，如何得知要套用哪些設定？
請注意，當有兩項或多項原則部署到同一位使用者或同一部裝置時，會在個別的設定層級評估要套用哪項設定：

- 合規性政策設定一律優先於設定原則設定。

- 如果與不同合規性政策中的相同設定一起評估，則會套用限制最嚴格的合規性政策設定。

- 如果設定原則的設定與不同設定原則中的設定衝突，這項衝突會顯示在 Intune 中。 請手動解決這些衝突。

### <a name="what-happens-when-mobile-application-management-policies-conflict-with-each-other-which-one-applies-to-the-app"></a>當行動應用程式管理原則彼此衝突時，會發生什麼情況？ 哪一項原則會套用至應用程式？
除了數字輸入欄位 (例如重設前的 PIN 嘗試次數) 之外，衝突值是 MAM 原則中限制最嚴格的設定。  數字輸入欄位會設定為相同的值，如同您在主控台中使用建議的設定選項建立 MAM 原則一樣。

當兩項原則設定相同時，就會發生衝突。  例如，您設定了兩項 MAM 原則，其中除了複製/貼上設定之外，這兩項原則完全相同。  在這種情況下，複製/貼上設定會設定為限制最嚴格的值，但其餘設定則會依照設定來套用。

如果其中一項原則部署到應用程式並生效，然後再部署第二項原則，則會優先使用並持續套用第一項原則。 第二項原則會顯示為衝突。 如果同時套用這兩項原則，代表沒有優先的原則，則兩者皆處於衝突狀態。 任何衝突的設定都會設為限制最嚴格的值。

### <a name="what-happens-when-ios-custom-policies-conflict"></a>iOS 自訂原則衝突時，會發生什麼情況？
Intune 不會評估 Apple 設定檔或自訂開放行動聯盟的統一資源識別項 (OMA-URI) 原則的承載。 它只做為傳遞機制。

當您部署自訂原則時，請確認所進行的設定未與合規性、設定或其他自訂原則衝突。 如果自訂原則與設定衝突，則會依隨機順序來套用設定。

### <a name="what-happens-when-a-policy-is-deleted-or-no-longer-applicable"></a>當原則已刪除或不再適用時，會發生什麼情況？
當您刪除原則，或從群組中移除已經部署原則的裝置時，則會依照以下清單，從裝置移除該原則及設定。

#### <a name="enrolled-devices"></a>已註冊的裝置

- Wi-Fi、VPN、憑證及電子郵件設定檔：這些設定檔會從所有支援的已註冊裝置中移除。
- 所有其他原則類型：
  - [Windows 和 Android 裝置]：設定不會從裝置中移除。
  - [Windows Phone 8.1 裝置]：會移除下列設定：
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

  - [iOS]：移除所有設定，除了︰
    - 允許語音漫遊
    - 允許數據漫遊
    - 允許漫遊時自動同步處理

### <a name="where-can-i-find-help-troubleshooting-policies"></a>哪裡可以找到疑難排解原則的說明？

請參閱[原則疑難排解](troubleshoot-policies-in-microsoft-intune.md)。
