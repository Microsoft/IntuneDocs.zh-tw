---
title: 針對 Microsoft Intune - Azure 中的裝置動作問題進行疑難排解 | Microsoft Docs
description: 取得疑難排解裝置動作問題的協助。
keywords: ''
author: erikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 159e236a079adcd55ba73e8fea6f786c09d08bbd
ms.sourcegitcommit: 73fbecf7cee4fdfc37d3c30ea2007d2a9a6d2d12
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68772356"
---
# <a name="troubleshoot-device-actions-in-intune"></a>針對 Intune 中的裝置動作進行疑難排解

Microsoft Intune 有許多動作可協助您管理裝置。 本文提供一些常見問題的解答, 可協助您針對裝置動作進行疑難排解。

## <a name="bypass-activation-lock-action"></a>略過啟用鎖定動作

### <a name="i-clicked-the-bypass-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>我在入口網站中按一下 [略過啟用鎖定] 動作, 但是裝置上沒有發生任何事。
這是預期的情況。 開始略過啟用鎖定動作之後, Intune 會向 Apple 要求更新的程式碼。 您會在裝置位於 [啟用鎖定] 畫面上之後, 以手動方式在 [密碼] 欄位中輸入程式碼。 這段程式碼只會在15天內有效, 因此請務必按一下動作並複製程式碼, 然後再發出抹除。

### <a name="why-dont-i-see-the-bypass-activation-lock-code-in-the-hardware-overview-blade-of-my-ios-device"></a>為什麼我在 iOS 裝置的 硬體總覽 分頁中看不到 略過啟用鎖定的程式碼？
最可能的原因包括:
- 程式碼已過期, 並已從服務中清除。
- 裝置不受裝置限制原則的監督, 而無法允許啟用鎖定。

您可以使用下列查詢來檢查 Graph Explorer 中的程式碼:

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-bypass-activation-lock-action-greyed-out-for-my-ios-device"></a>為什麼我的 iOS 裝置的 [略過啟用鎖定] 動作呈現灰色？
最可能的原因包括: 
- 程式碼已過期, 並已從服務中清除。
- 裝置不受裝置限制原則的監督, 而無法允許啟用鎖定。

### <a name="is-the-bypass-activation-lock-code-case-sensitive"></a>略過啟用鎖定程式碼是否區分大小寫？
否。 而且您不需要輸入破折號。

## <a name="remove-devices-action"></a>移除裝置動作

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>如何? 告訴誰開始淘汰/清除？
前往 [ **Intune**  >   裝置 > ] [**裝置動作**] > 檢查 [**起始者**] 資料行。
如果您沒有看到某個專案, 則起始該動作的最有可能的人是裝置的使用者。 他們可能會使用公司入口網站應用程式或 portal.manage.microsoft.com。

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>為什麼我的應用程式在使用淘汰之後才卸載？
因為它不被視為受控應用程式。 在此內容中, 受控應用程式是使用 Intune 服務安裝的應用程式。 這包括：
- 應用程式已依需求部署
- 應用程式已部署為 [可用], 然後由終端使用者從公司入口網站應用程式內安裝。

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>為什麼 Android Enterprise 工作設定檔裝置的抹除呈現灰色？
這是正常的現象。 Google 不允許從 MDM 提供者對工作設定檔裝置進行原廠重設。

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>為什麼我可以在裝置淘汰之後重新登入我的 Office 應用程式？
因為淘汰裝置並不會撤銷存取權杖。 您可以使用條件式存取原則來減輕這種情況。

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>如何在發行後監視淘汰/抹除動作？
前往 [ **Intune**  >   裝置 > ] [**裝置動作**]。

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>為什麼抹除有時會無限期地顯示為擱置？
裝置不一定會在重設開始之前, 將其狀態回報回 Intune 服務。 因此, 此動作會顯示為 [擱置]。 如果您已確認動作已成功, 請從服務中刪除裝置。

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>如果我在離線裝置或未與服務通訊的裝置上啟動淘汰/抹除, 會發生什麼事？
裝置會維持**淘汰/抹除擱置**狀態, 直到 MDM 憑證過期為止。 MDM 憑證會持續一年的註冊, 並每年自動續訂。 如果裝置在 MDM 憑證過期之前簽入, 則會被淘汰/抹除。 如果裝置未在 MDM 憑證過期之前簽入, 則無法簽入服務。 MDM 憑證到期後180天, 將會自動從 Azure 入口網站中移除裝置。


## <a name="reset-passcode-action"></a>重設密碼動作

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>為什麼我的 Android 裝置管理註冊裝置上的 [重設密碼] 動作呈現灰色？
為了對抗 Ransom 的情況, Google 已移除裝置管理 API (適用于 Android 7.0 版或更高版本的裝置) 上的密碼重設功能。

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>為什麼當我對 Android 8.0 或更新版本的工作設定檔註冊的裝置發出密碼重設時, 會收到「不支援」的訊息？
因為尚未在裝置上啟用重設權杖。 若要啟用重設權杖:
1. 您必須在設定原則中要求工作設定檔密碼。
2. 終端使用者必須設定適當的工作設定檔密碼。
3. 使用者必須接受允許重設密碼的次要提示。
完成這些步驟之後, 您應該就不會再收到此回應。

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-ios-device-when-i-issue-the-remove-passcode-action"></a>當我發出 [移除密碼] 動作時, 為什麼會提示您在 iOS 裝置上設定新密碼？
因為其中一個合規性原則需要密碼。

## <a name="next-steps"></a>後續步驟

取得[來自 Microsoft 的支援說明](get-support.md)或使用[社群論壇](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)。
