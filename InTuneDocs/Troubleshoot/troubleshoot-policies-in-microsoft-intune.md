---
# required metadata

title: 原則疑難排解 | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 的原則疑難排解

本文列出您的 Microsoft Intune 原則設定中可能會發生的一些問題，以及這些問題的疑難排解建議。

如果此資訊無法解決您的問題，請參閱[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)，以尋找更多方法來取得協助。


## 裝置是否已套用原則？
問題： 不確定是否要將特定原則套用至裝置，或者裝置的行為是否違反原則。

檢查每部裝置可用的原則資訊，以了解各項原則如何影響特定裝置。

在 Intune 管理主控台中，每部裝置在 [裝置內容] 下會有一個 [原則] 索引標籤。 如果沒有，則裝置可能仍在進行註冊，或者可能未套用原則。 每個原則都具有 [預定的值]  和 [狀態] 。 預定的值是您在指派原則時想要達到的值。 狀態則是在一併考慮要套用到裝置的所有原則，以及硬體和作業系統的限制與需求時，實際達成的情況。 可能的狀態包括：

-   符合：裝置已收到原則，並對服務回報其符合設定。

-   不適用：此原則設定不適用。 例如，iOS 裝置的電子郵件設定不適用於 Android 裝置。

-   擱置：原則已傳送至裝置，但尚未對服務回報狀態。 例如，Android 上的加密需要使用者啟用加密，因此可能擱置中。

在下列螢幕擷取畫面中，您可以看到兩個明確的範例：

-   [允許簡單密碼] 已設為 [是] (如 [預定的值] 欄中所示)，但其 [狀態] 為 [不適用]。 這是因為 Android 裝置不支援簡單的密碼。

-   同樣地，擴充的原則項目 [iOS 裝置的電子郵件設定] 不會套用到此裝置，因為它是 Android 裝置。

![Intune 裝置原則](../media/Intune-Device-Policy-v.2.jpg)

> 請記住，當有兩項不同限制等級的原則套用至同一部裝置或使用者時，實際上會套用限制更嚴格的原則。

## 原則的重新整理和更新間隔
請注意，原則會定期重新整理和更新。 一般而言，原則應該在變更後的 15 分鐘內在裝置上註冊。 以下是定期重新整理原則的詳細資訊︰

-   已註冊 MDM 的 Windows 裝置︰這由每天當地時間上午 3:00 的裝置排程工作觸發。

-   Windows Phone：每隔 8 小時更新原則。 可以透過公司入口網站 [設定] 下的重新整理強制執行

-   iOS︰每天一次不定時更新原則。 開啟公司入口網站、選取該裝置並按一下 [同步處理] 也可以強制執行

-   Android：每天一次不定時更新原則。 開啟公司入口網站、選取該裝置並按一下 [同步處理] 也可以強制執行

## Microsoft Intune policyplatform.log 中的原則相關錯誤
至於非 MDM Windows 裝置，policyplatform.log 檔案中的原則錯誤可能是因為裝置上 Windows 使用者帳戶控制 (UAC) 的非預設設定所造成。 某些非預設的 UAC 設定可能會影響 Microsoft Intune 用戶端安裝和原則執行。

### 解決 UAC 問題

1.  請依[從 Microsoft Intune 管理淘汰裝置](/intune/deploy-use/retire-devices-from-microsoft-intune-management)一文中所述來淘汰電腦

2.  等候 20 分鐘讓用戶端軟體被移除。

    > 請勿嘗試從 [程式和功能] 移除用戶端。

3.  在 [開始] 功能表中輸入 UAC，開啟 [使用者帳戶控制] 設定。

4.  將通知滑桿移至預設設定。

## KNOX 裝置的錯誤 0x87D1FDE8
問題：針對各種 Android 裝置建立及部署 Samsung KNOX 的 Exchange Active Sync 電子郵件設定檔之後，在 [裝置內容] &gt; [原則] 索引標籤中，回報錯誤 0x87D1FDE8 或 [補救失敗]。

檢閱 Samsung KNOX 的 EAS 設定檔和來源原則的組態。 不再支援 Samsung Note 同步處理選項，因此不應該在您的設定檔中選取該選項。 請確定裝置有足夠的時間來處理原則，最多 24 小時。

## 警示：將存取規則儲存到 Exchange 失敗
問題：您在管理主控台中收到警示「將存取規則儲存到 Exchange 失敗」   。

如果您在管理主控台下的 [Exchange 內部部署原則] 工作區中建立原則，但使用 O365，Intune 將不會強制執行已設定的原則設定。 記下警示中的原則來源。  刪除 [Exchange 內部部署原則] 工作區下的舊版規則，因為這些規則是適用於內部部署 Exchange 的 Intune 中的通用 Exchange 規則，與 O365 無關。 接著，建立適用於 O365 的新原則。

## 錯誤：無法從電腦取得值，0x80041013
如果本機系統上的時間與同步差距五分鐘以上，就可能發生這個錯誤。 如果本機電腦上的時間不同步，因為時間戳記無效，安全交易會失敗。

若要解決這個問題，設定本機系統時間時請盡可能接近網際網路時間，或接近網路上網域控制站的設定時間。

## 無法變更各種 MDM 裝置的安全性原則
當您透過 MDM 或 EAS 設定安全性原則之後，Windows Phone 和 Windows RT 裝置不允許降低這些原則的安全性。 例如，您將 [字元密碼數目下限]  設定為 8，然後嘗試減少為 4。 此裝置已套用較嚴格的原則。

根據裝置平台，如果您想要將原則變更為較不安全的值，您可能需要重設安全性原則。
例如，在 Windows RT 的桌面上，從右向內撥動以開啟 [快速鍵] 列，然後按一下 [設定]  &gt;  [控制台]。  選取 [使用者帳戶]  小程式。
左導覽功能表底部有一個 [重設安全性原則]  連結。 按一下連結，然後按一下 [重設原則]  按鈕。
您可能需要停用 Android、Windows Phone 8.1 (含) 以後版本和 iOS 等其他 MDM 裝置，再重新註冊到服務中，才能套用較不嚴格的原則。

## Android 裝置不會在使用者未接受的情況下，強制執行安全性原則變更。
Android MDM 不允許服務在裝置上強制執行其他平台所允許的初始原則變更。 這是 Android 本身功能所致，與 Intune 服務無關。 Android 裝置會透過相關原則變更 (例如密碼、加密等) 的通知視窗來提示使用者。  使用者必須回應提示，而且一旦接受，就應該套用原則。

## 如果公司名稱包含特殊字元，就無法建立原則或註冊用戶端
問題︰您無法建立原則或註冊用戶端。

解決方式︰在 [Office 365 系統管理中心](https://portal.office.com/)中，移除公司名稱的特殊字元並儲存公司資訊。

### 後續步驟
如果這項疑難排解資訊對您沒有幫助，請連絡 Microsoft 支援服務，如[如何取得 Microsoft Intune 的支援](how-to-get-support-for-microsoft-intune.md)中所述


<!--HONumber=May16_HO2-->


