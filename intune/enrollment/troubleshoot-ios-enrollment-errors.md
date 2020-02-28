---
title: 針對 Microsoft Intune 中的 iOS/iPadOS 裝置註冊問題進行疑難排解
titleSuffix: Microsoft Intune
description: 針對在 Intune 中註冊 iOS/iPadOS 裝置時的一些最常見問題進行疑難排解的建議。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a29fab4be6e2046b2c6757505001a7ba3455b8d6
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514314"
---
# <a name="troubleshoot-iosipados-device-enrollment-problems-in-microsoft-intune"></a>針對 Microsoft Intune 中的 iOS/iPadOS 裝置註冊問題進行疑難排解

此文章可協助 Intune 管理員了解在 Intune 中註冊 iOS/iPadOS 裝置時的問題，並進行疑難排解。

## <a name="prerequisites"></a>先決條件

開始進行疑難排解之前，請務必先收集一些基本資訊。 此資訊可協助您進一步了解問題，並縮短尋找解決方案的時間。

收集與問題相關的下列資訊：

- 確切錯誤訊息為何？
- 您會在哪裡看到錯誤訊息？
- 問題何時開始發生？ 註冊成功了嗎？
- 哪個平台 (Android、iOS/iPadOS、Windows) 有問題？
- 有多少使用者受到影響？ 所有使用者都受到影響，還是只有部分使用者受到影響？
- 有多少裝置受到影響？ 所有裝置都受到影響，還是只有部分裝置受到影響？
- 什麼是 MDM 授權單位？
- 如何執行註冊？ 是「攜帶您自己的裝置」(BYOD)，還是使用註冊設定檔的 Apple 裝置註冊計劃 (DEP)？

## <a name="error-messages"></a>錯誤訊息

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>設定檔安裝失敗。 發生網路錯誤。

**原因：** 裝置上的 iOS/iPadOS 發生未指定的問題。

#### <a name="resolution"></a>解決方案

1. 若要避免在下列步驟中發生資料遺失 (還原 iOS/iPadOS 會刪除裝置上的所有資料)，請務必備份您的資料。
2. 讓裝置進入復原模式，然後將其還原。 請務必將其設定為新裝置。 如需有關如何還原 iOS/iPadOS 裝置的詳細資訊，請參閱 [https://support.apple.com/HT201263](https://support.apple.com/HT201263)。
3. 重新註冊裝置。

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>設定檔安裝失敗。 無法建立與伺服器的連線。

**原因：** 您的 Intune 租用戶設定為只允許公司擁有的裝置。 

#### <a name="resolution"></a>解決方案
1. 登入 Azure 入口網站。
2. 選取 [更多服務]  並搜尋 Intune，然後選取 [Intune]  。
3. 選取 [裝置註冊]   > [註冊限制]  。
4. 在 [裝置類型限制]  下，選取您要設定的限制 > [內容]   > 選取 [平台]  > 針對 [iOS]  選取 [允許]  ，然後按一下 [確定]  。
5. 選取 [設定平台]  ，針對個人擁有的 iOS/iPadOS 裝置選取 [允許]  ，然後按一下 [確定]  。
6. 重新註冊裝置。

**原因：** DNS 中的必要 CNAME 記錄不存在。

#### <a name="resolution"></a>解決方案
建立公司網域的 CNAME DNS 資源記錄。 例如，假設您公司的網域為 contoso.com，請在 DNS 中建立 CNAME，其會將 EnterpriseEnrollment.contoso.com 重新導向到 EnterpriseEnrollment-s.manage.microsoft.com。

雖然建立 CNAME DNS 項目並非必要，但 CNAME 記錄可以方便使用者進行註冊。 若找不到任何 CNAME 記錄，將會提示使用者手動輸入 MDM 伺服器名稱 enrollment.manage.microsoft.com。

如果已驗證的網域不止一個，請為每個網域建立一筆 CNAME 記錄。 CNAME 資源記錄必須包含下列資訊：

|類型|主機名稱|指向|TTL|
|------|------|------|------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com|1 小時|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小時|

如果您的公司對使用者認證使用多個網域，請為每個網域建立 CNAME 記錄。

> [!NOTE]
> DNS 記錄變更可能需要 72 小時才會傳播完成。 在 DNS 記錄傳播完成之前，您無法在 Intune 中驗證 DNS 變更。

**原因：** 您註冊的裝置先前是使用不同的使用者帳戶註冊的，而先前的使用者未適當地從 Intune 中移除。

#### <a name="resolution"></a>解決方案
1. 取消任何目前的設定檔安裝。
2. 在 Safari 中開啟 [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com)。
3. 重新註冊裝置。

> [!NOTE]
> 如果註冊仍然失敗，請移除 Safari 中的 Cookie (不要封鎖 Cookie)，然後重新註冊裝置。

**原因：** 裝置已向另一個 MDM 提供者註冊。

#### <a name="resolution"></a>解決方案
1. 在 iOS/iPadOS 裝置上開啟 [設定]  ，移至 [一般] > [裝置管理]  。
2. 移除任何現有的管理設定檔。
3. 重新註冊裝置。

**原因：** 嘗試註冊裝置的使用者沒有 Microsoft Intune 授權。

#### <a name="resolution"></a>解決方案
1. 移至 [Office 365 系統管理中心](https://portal.office.com/adminportal/home#/homepage)，然後選擇 [使用者] > [作用中使用者]  。
2. 選取您想要指派 Intune 使用者授權的使用者帳戶，然後選擇 [產品授權] > [編輯]  。
3. 針對您要指派給此使用者的授權，將切換開關切換至 [開啟]  位置，然後選擇 [儲存]  。
4. 重新註冊裝置。

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>不支援這項服務。 無註冊原則。

**原因**：未在 Intune 中設定 Apple MDM Push Certificate，或憑證無效。 

#### <a name="resolution"></a>解決方案

- 如果未設定 MDM Push Certificate，請依照[取得 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate) 中的步驟進行。
- 如果 MDM Push Certificate 無效，請依照[更新 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate) 中的步驟進行。

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>公司入口網站暫時無法使用。 公司入口網站應用程式發生問題。 如果問題持續發生，請連絡您的系統管理員。

**原因：** 公司入口網站應用程式已過期或已損毀。

#### <a name="resolution"></a>解決方案
1. 從裝置移除公司入口網站應用程式。
2. 從 **App Store** 下載並安裝 **Microsoft Intune 公司入口網站**應用程式。
3. 重新註冊裝置。
 > [!NOTE]
    > 如果使用者嘗試註冊的裝置數超過裝置註冊設定所允許的數目，也可能發生此錯誤。 如果這些步驟無法解決問題，請遵循下面**已到達裝置上限**的解決步驟。

### <a name="device-cap-reached"></a>已到達裝置上限

**原因：** 使用者嘗試註冊的裝置數目超過裝置註冊限制。

#### <a name="resolution"></a>解決方案
1. 在 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選擇 [裝置]   > [所有裝置]  ，並檢查使用者已註冊的裝置數目。
    > [!NOTE]
    > 您也應該讓受影響的使用者登入 [Intune 使用者入口網站](https://portal.manage.microsoft.com/)，並檢查已註冊的裝置。 有些裝置可能出現在 [Intune 使用者入口網站](https://portal.manage.microsoft.com/)中，但不在 [Intune 系統管理入口網站](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)中，這類裝置也會計入裝置註冊限制。
2. 在 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選擇 [裝置]   > [註冊限制]  > 檢查裝置註冊限制。 根據預設，此限制數目為 15。 
3. 如果註冊的裝置數目已達到限制，請移除不必要的裝置，或增加裝置註冊限制。 因為每個已註冊的裝置都會耗用 Intune 授權，所以建議您一律先移除不必要的裝置。
4. 重新註冊裝置。

### <a name="workplace-join-failed"></a>Workplace Join 失敗

**原因：** 公司入口網站應用程式已過期或已損毀。  

#### <a name="resolution"></a>解決方案
1. 從裝置移除公司入口網站應用程式。
2. 從 **App Store** 下載並安裝 **Microsoft Intune 公司入口網站**應用程式。
3. 重新註冊裝置。

### <a name="user-license-type-invalid"></a>使用者授權類型無效

**原因：** 嘗試註冊裝置的使用者沒有有效 Intune 授權。

#### <a name="resolution"></a>解決方案
1. 移至 [Microsoft 365 系統管理中心](https://portal.office.com/adminportal/home#/homepage)，然後選擇 [使用者]   > [作用中使用者]  。
2. 選取受影響的使用者帳戶 > [產品授權]   > [編輯]  。
3. 確認已將有效的 Intune 授權指派給此使用者。
4. 重新註冊裝置。

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>無法辨識使用者名稱。 此使用者帳戶未獲授權可使用 Microsoft Intune。 如果您認為自己不應該收到這則訊息，請連絡系統管理員。

**原因：** 嘗試註冊裝置的使用者沒有有效 Intune 授權。

1. 移至 [Microsoft 365 系統管理中心](https://portal.office.com/adminportal/home#/homepage)，然後選擇 [使用者]   > [作用中使用者]  。
2. 選取受影響的使用者帳戶，然後選擇 [產品授權]   > [編輯]  。
3. 確認已將有效的 Intune 授權指派給此使用者。
4. 重新註冊裝置。

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>設定檔安裝失敗。 新的 MDM 承載不符合舊的承載。

**原因：** 裝置上已安裝管理設定檔。

#### <a name="resolution"></a>解決方案

1. 在 iOS/iPadOS 裝置上開啟 [設定]  > [一般]   > [裝置管理]  。
2. 點選現有的管理設定檔，然後點選 [移除管理]  。
3. 重新註冊裝置。

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**原因：** Apple Push Notification Service (APNs) 憑證遺失、無效或已過期。

#### <a name="resolution"></a>解決方案
確認已將有效的 APNs 憑證新增至 Intune。 如需詳細資訊，請參閱[設定 iOS/iPadOS 註冊](ios-enroll.md)。

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**原因：** Intune 中設定的 Apple Push Notification service (APNs) 憑證有問題。

#### <a name="resolution"></a>解決方案
更新 APNs 憑證，然後重新註冊裝置。

> [!IMPORTANT]
> 請確定您已更新 APNs 憑證。 請勿取代 APNs 憑證。 如果您取代憑證，就必須在 Intune 中重新註冊所有 iOS/iPadOS 裝置。 

- 若要在 Intune 獨立版中更新 APNs 憑證，請參閱[更新 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate)。
- 若要更新 Office 365 中的 APNs 憑證，請參閱[建立適用於 iOS/iPadOS 裝置的 APNs 憑證](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7)。

### <a name="xpc_type_error-connection-invalid"></a>XPC_TYPE_ERROR 連線無效

當您開啟已指派註冊設定檔的 DEP 管理裝置時，註冊會失敗，而且您會收到下列錯誤訊息：

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**原因：** 裝置與 Apple DEP 服務之間有連線問題。

#### <a name="resolution"></a>解決方案
修正連線問題，或使用不同的網路連線來註冊裝置。 如果問題持續發生，您可能也必須連絡 Apple。


## <a name="other-issues"></a>其他問題

### <a name="dep-enrollment-doesnt-start"></a>DEP 註冊未啟動
當您開啟已指派註冊設定檔的 DEP 管理裝置時，不會起始 Intune 註冊程序。

**原因：** 註冊設定檔會在 DEP 權杖上傳至 Intune 之前建立。

#### <a name="resolution"></a>解決方案

1. 編輯註冊設定檔。 您可以對設定檔進行任何變更。 目的是要更新設定檔的修改時間。
2. 同步處理 DEP 管理的裝置：在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選擇 [裝置]   > [iOS]   > [iOS 註冊]   > [註冊方案權杖]  > 選擇權杖 > [立即同步]  。 同步處理要求會傳送至 Apple。

### <a name="dep-enrollment-stuck-at-user-login"></a>DEP 註冊卡在使用者登入
當您開啟已指派註冊設定檔的 DEP 管理裝置時，您輸入認證後會停在初始設定。

**原因：** 已啟用多重要素驗證 (MFA)。 目前，在 DEP 裝置上註冊期間無法使用 MFA。

#### <a name="resolution"></a>解決方案
停用 MFA，然後重新註冊裝置。


## <a name="next-steps"></a>後續步驟

- [疑難排解 Intune 的裝置註冊問題](../troubleshoot-device-enrollment-in-intune.md)
- [在 Intune 論壇中發問](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [查看 Microsoft Intune 支援小組部落格](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess) \(英文\)
- [查看 Microsoft Enterprise Mobility 與安全性小組部落格](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210) \(英文\)
