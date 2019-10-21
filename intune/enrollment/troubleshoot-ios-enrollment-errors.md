---
title: 針對 Microsoft Intune 中的 iOS 裝置註冊問題進行疑難排解
titleSuffix: Microsoft Intune
description: 當您在 Intune 中註冊 iOS 裝置時，針對一些最常見的問題進行疑難排解的建議。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/25/2019
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
ms.openlocfilehash: e7c7ec23d0408aa4d4cf81baff2d7cdf749fb65e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509241"
---
# <a name="troubleshoot-ios-device-enrollment-problems-in-microsoft-intune"></a>針對 Microsoft Intune 中的 iOS 裝置註冊問題進行疑難排解

本文可協助 Intune 系統管理員瞭解並疑難排解在 Intune 中註冊 iOS 裝置時的問題。

## <a name="prerequisites"></a>必要條件

開始進行疑難排解之前，請務必收集一些基本資訊。 此資訊可協助您進一步瞭解問題，並縮短尋找解決方案的時間。

收集與問題相關的下列資訊：

- 確切錯誤訊息為何？
- 您會在哪裡看到錯誤訊息？
- 問題何時開始發生？ 註冊是否曾經有作用？
- 哪個平臺（Android、iOS、Windows）有問題？
- 有多少使用者受到影響？ 所有使用者都會受到影響，還是只有部分？
- 有多少裝置受到影響？ 所有裝置是否受到影響，或只是部分？
- 什麼是 MDM 授權單位？ 如果 System Center Configuration Manager，您使用的是哪一版的 Configuration Manager？
- 如何執行註冊？ 它是「攜帶您自己的裝置」（BYOD）或 Apple 裝置註冊計劃（DEP）與註冊設定檔嗎？

## <a name="error-messages"></a>錯誤訊息

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>設定檔安裝失敗。 發生網路錯誤。

**原因：** 裝置上的 iOS 發生未指定的問題。

#### <a name="resolution"></a>解決方案

1. 為避免下列步驟中的資料遺失（還原 iOS 會刪除裝置上的所有資料），請務必備份您的資料。
2. 讓裝置進入復原模式，然後將它還原。 請確定您已將它設定為新的裝置。 如需有關如何還原 iOS 裝置的詳細資訊，請參閱[https://support.apple.com/HT201263](https://support.apple.com/HT201263)。
3. 重新註冊裝置。

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>設定檔安裝失敗。 無法建立與伺服器的連線。

**原因：** 您的 Intune 租使用者已設定為只允許公司擁有的裝置。 

#### <a name="resolution"></a>解決方案
1. 登入 Azure 入口網站。
2. 選取 [更多服務]  並搜尋 Intune，然後選取 [Intune]  。
3. 選取 [裝置註冊]   > [註冊限制]  。
4. 在 **[裝置類型限制**] 下，選取您想要**設定 > 內容**的限制  >  選取 [**平臺**] > 選取 [**允許** **iOS**]，然後按一下 **[確定]** 。
5. 選取 [**設定平臺**]，選取 [**允許**個人擁有的 iOS 裝置]，然後按一下 **[確定]** 。
6. 重新註冊裝置。

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>不支援此服務。 無註冊原則。

**原因**：未在 Intune 中設定 Apple MDM push certificate，或憑證無效。 

#### <a name="resolution"></a>解決方案

- 如果未設定 MDM push certificate，請依照[取得 APPLE MDM push certificate](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate)中的步驟進行。
- 如果 MDM push certificate 無效，請依照[更新 APPLE MDM push certificate](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate)中的步驟進行。

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>公司入口網站暫時無法使用。 公司入口網站應用程式發生問題。 如果問題持續發生，請連絡您的系統管理員。

**原因：** 公司入口網站應用程式已過期或已損毀。

#### <a name="resolution"></a>解決方案
1. 從裝置移除公司入口網站應用程式。
2. 從 **App Store** 下載並安裝 **Microsoft Intune 公司入口網站**應用程式。
3. 重新註冊裝置。

### <a name="device-cap-reached"></a>已到達裝置上限

**原因：** 使用者嘗試註冊的裝置數量超過裝置註冊限制。

#### <a name="resolution"></a>解決方案
1. 開啟[Intune 系統管理員入口網站](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview) >  [**裝置**]  >  [**所有裝置**]，並檢查使用者已註冊的裝置數目。
    > [!NOTE]
    > 您也應該讓受影響的使用者登入[Intune 使用者入口網站](https://portal.manage.microsoft.com/)，並檢查已註冊的裝置。 有些裝置可能出現在[intune 使用者入口網站](https://portal.manage.microsoft.com/)中，但不在[intune 系統管理員入口網站](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)中，這類裝置也會計入裝置註冊限制。
2. 移至 [系統**管理**] [ > ] [行動**裝置管理** >  個**註冊規則**] > 檢查裝置註冊限制。 根據預設，此限制數目為 15。 
3. 如果註冊的裝置數目已達到限制，請移除不必要的裝置，或增加裝置註冊限制。 由於每個已註冊的裝置都會使用 Intune 授權，因此建議您一律先移除不必要的裝置。
4. 重新註冊裝置。

### <a name="workplace-join-failed"></a>Workplace Join 失敗

**原因：** 公司入口網站應用程式已過期或已損毀。  

#### <a name="resolution"></a>解決方案
1. 從裝置移除公司入口網站應用程式。
2. 從 **App Store** 下載並安裝 **Microsoft Intune 公司入口網站**應用程式。
3. 重新註冊裝置。

### <a name="user-license-type-invalid"></a>使用者授權類型無效

**原因：** 嘗試註冊裝置的使用者沒有有效的 Intune 授權。

#### <a name="resolution"></a>解決方案
1. 移至[Microsoft 365 系統管理中心](https://portal.office.com/adminportal/home#/homepage)，然後選擇 [**使用者**]  >  [作用中**使用者**]。
2. 選取受影響的使用者帳戶 >**產品授權** > **編輯**。
3. 確認已將有效的 Intune 授權指派給此使用者。
4. 重新註冊裝置。

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>無法辨識使用者名稱。 此使用者帳戶未獲授權，無法使用 Microsoft Intune。 如果您認為您已收到錯誤訊息，請洽詢系統管理員。

**原因：** 嘗試註冊裝置的使用者沒有有效的 Intune 授權。

1. 移至[Microsoft 365 系統管理中心](https://portal.office.com/adminportal/home#/homepage)，然後選擇 [**使用者**]  >  [作用中**使用者**]。
2. 選取受影響的使用者帳戶，然後選擇 **產品授權**  > **編輯**。
3. 確認已將有效的 Intune 授權指派給此使用者。
4. 重新註冊裝置。

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>設定檔安裝失敗。 新的 MDM 承載不符合舊承載。

**原因：** 裝置上已安裝管理設定檔。

#### <a name="resolution"></a>解決方案

1. 在 iOS 裝置上開啟 [**設定**] > **[一般** > **裝置管理**]。
2. 按一下現有的管理設定檔，然後按 [**移除管理**]。
3. 重新註冊裝置。

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**原因：** Apple Push Notification Service （APNs）憑證遺失、無效或已過期。

#### <a name="resolution"></a>解決方案
確認已將有效的 APNs 憑證新增至 Intune。 如需詳細資訊，請參閱[設定 iOS 與 Mac 裝置管理](https://docs.microsoft.com/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)。 

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**原因：** Intune 中設定的 Apple Push Notification service （APNs）憑證發生問題。

#### <a name="resolution"></a>解決方案
更新 APNs 憑證，然後重新註冊裝置。

> [!IMPORTANT]
> 請確定您已更新 APNs 憑證。 請勿取代 APNs 憑證。 如果您取代憑證，就必須在 Intune 中重新註冊所有 iOS 裝置。 

- 若要在 Intune 獨立版中更新 APNs 憑證，請參閱[更新 APPLE MDM push certificate](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate)。
- 若要使用 Configuration Manager 更新 Intune 混合式中的 APNs 憑證，請參閱[使用 System Center Configuration Manager 和 Microsoft Intune 設定 iOS 混合式裝置管理](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac)。
- 若要更新 Office 365 中的 APNs 憑證，請參閱[建立適用于 iOS 裝置的 Apns 憑證](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7)。

### <a name="xpc_type_error-connection-invalid"></a>XPC_TYPE_ERROR 連接無效

當您開啟已指派註冊設定檔的 DEP 管理裝置時，註冊將會失敗，而且您會收到下列錯誤訊息：

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**原因：** 裝置與 Apple DEP 服務之間有連線問題。

#### <a name="resolution"></a>解決方案
請修正連線問題，或使用不同的網路連接來註冊裝置。 如果問題持續發生，您可能也必須與 Apple 聯繫。


## <a name="other-issues"></a>其他問題

### <a name="dep-enrollment-doesnt-start"></a>DEP 註冊未啟動
當您開啟已指派註冊設定檔的 DEP 管理裝置時，並不會起始 Intune 註冊程式。

**原因：** 註冊設定檔會在 DEP 權杖上傳至 Intune 之前建立。

#### <a name="resolution"></a>解決方案

1. 編輯註冊設定檔。 您可以對設定檔進行任何變更。 其目的是要更新設定檔的修改時間。
2. 同步處理 DEP 管理的裝置：開啟 Intune 入口網站 > 系統**管理員** >  行動**裝置管理** > **IOS**  > **裝置註冊計劃** > **立即同步**。 同步處理要求會傳送至 Apple。

### <a name="dep-enrollment-stuck-at-user-login"></a>DEP 註冊停滯于使用者登入
當您開啟已指派註冊設定檔的 DEP 管理裝置時，在您輸入認證後的初始安裝程式將會變棒。

**原因：** 已啟用多重要素驗證（MFA）。 在 DEP 裝置註冊期間，目前無法使用 MFA。

#### <a name="resolution"></a>解決方案
停用 MFA，然後重新註冊裝置。

## <a name="next-steps"></a>後續步驟

- [疑難排解 Intune 的裝置註冊問題](../troubleshoot-device-enrollment-in-intune.md)
- [在 Intune 論壇中發問](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [查看 Microsoft Intune 支援小組的 Blog](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [查看 Microsoft 企業行動性和安全性的網路日誌](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
