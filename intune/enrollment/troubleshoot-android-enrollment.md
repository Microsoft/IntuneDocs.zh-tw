---
title: 在 Microsoft Intune 中對 Android 企業裝置進行疑難排解
description: 針對在 Intune 中註冊 Android 裝置時，一些最常見問題的疑難排解建議。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/25/2020
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
ms.openlocfilehash: 04c726c1dc6af7e92b75335d105de605ef00e712
ms.sourcegitcommit: 8b716db3c0fdbb7dff62497ec283902a5069a343
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652363"
---
# <a name="troubleshoot-android-enterprise-device-problems-in-microsoft-intune"></a>在 Microsoft Intune 中對 Android 企業裝置問題進行疑難排解

本文可協助 Intune 系統管理員了解在 Intune 中註冊 Android 企業裝置時的問題，並進行疑難排解。

## <a name="apps-on-android-enterprise-devices"></a>Android 企業裝置上的應用程式

### <a name="managed-google-play-apps-that-arent-deployed-through-intune-are-displayed-in-the-work-profile"></a>未透過 Intune 部署的受控 Google Play 應用程式會顯示在工作設定檔中
裝置 OEM 可以在建立工作設定檔時，在工作設定檔中啟用系統應用程式。 這不是由 MDM 提供者所控制。

若要進行疑難排解，請遵循下列步驟：

  1. 收集公司入口網站記錄。
  2. 記下非預期出現在工作設定檔中的應用程式。
  3. 從 Intune 取消註冊裝置並解除安裝公司入口網站。
  4. 安裝[測試 DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc) 應用程式，這可在沒有 EMM 可供測試的情況下建立工作設定檔。
  5. 遵循[測試 DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc) 中的指示，在裝置上建立工作設定檔。
  6. 檢查出現在工作設定檔中的應用程式。 
  7. 如果在測試 DPC 應用程式中出現相同的應用程式，即表示這是 OEM 希望裝置應有的應用程式。

### <a name="unapproved-managed-google-play-for-work-store-apps-arent-being-removed-from-the-client-apps-page-in-intune"></a>Intune 的 [用戶端應用程式] 頁面不會移除未核准的受控 Google Play for Work 商店應用程式
這是正常的現象。

### <a name="managed-google-play-apps-arent-being-reported-under-the-discovered-apps-blade-in-the-intune-portal"></a>Intune 入口網站的 [探索到的應用程式] 刀鋒視窗下不會回報受控 Google Play 應用程式
這是正常的現象。 [探索到的應用程式] 刀鋒視窗只會清查安裝在工作設定檔中的系統應用程式。 若要查看已安裝的受控 Google Play 應用程式，請使用 [受控的應用程式]  刀鋒視窗。

### <a name="are-web-applications-supported-for-work-profile-enrolled-devices"></a>工作設定檔註冊的裝置是否支援 Web 應用程式？
是。 如需詳細資訊，請參閱[受控的 Google Play Web 連結](../apps/apps-add-android-for-work.md#managed-google-play-web-links)

## <a name="device-management"></a>裝置管理

### <a name="file-path-internal-storageandroiddatacommicrosoftwindowsintunecompanyportalfiles-missing-on-work-profile-enrolled-devices"></a>工作設定檔註冊的裝置上遺失檔案路徑 Internal storage/Android/Data.com.microsoft.windowsintune.companyportal/files

  **解答**：這是正常的現象。 只有裝置系統管理員 (前稱 Android 註冊) 案例才會建立此路徑。

  若要收集公司入口網站記錄，請遵循下列步驟：

  1. 在有徽章的公司入口網站應用程式中，點選 [功能表]   > [說明]   > [電子郵件支援]  ，然後點選 [Send Email & Upload logs] \(傳送電子郵件與上傳記錄\)  。 
  2. 當系統提示您**使用下列項目來傳送協助要求**時，請選取其中一個電子郵件應用程式。
  3. 您的 IT 系統管理員會收到一封電子郵件，其中包含可提供給 Microsoft 產品支援的事件識別碼。

### <a name="managed-google-play-last-sync-time--hasnt-been-updated-in-days"></a>受控 Google Play 上次同步時間未在數天內更新
這是正常的現象。 只有當您手動執行作業時，才會觸發同步處理。

### <a name="encryption-is-required-when-a-device-is-enrolled-can-it-be-turned-off"></a>註冊裝置時，需要加密。 可以關閉嗎？
否，Google 要求裝置必須加密，才能建立工作設定檔。 

### <a name="samsung-devices-are-blocking-the-use-of-third-party-keyboards-like-swiftkey"></a>Samsung 裝置封鎖使用協力廠商鍵盤，例如 SwiftKey
Samsung 已在 Android 8.0 以上的裝置上開始強制執行這項限制。 Microsoft 目前正與 Samsung 處理此問題，如有新資訊即會公布。

## <a name="remote-actions"></a>遠端動作

### <a name="wipe-factory-reset-option-isnt-available-for-work-profile-enrolled-device"></a>工作設定檔註冊的裝置無法使用抹除 (重設成出廠預設值) 選項
這是正常的現象。 在工作設定檔案例中，MDM 提供者沒有裝置的完整控制權。 唯一可用的選項是 [淘汰] (移除公司資料)，這會移除整個工作設定檔及其所有內容。

### <a name="is-device-passcode-reset-supported"></a>是否支援裝置密碼重設？
工作設定檔註冊的裝置只能在下列情況下，重設在 Android 8.0 或更新版本裝置上的工作設定檔密碼：
- 工作設定檔密碼受管理時
- 終端使用者已允許您重設此密碼。

支援專用裝置 (COSU) 和完全受控裝置來重設裝置密碼。


## <a name="next-steps"></a>後續步驟

- [疑難排解 Intune 的裝置註冊問題](../troubleshoot-device-enrollment-in-intune.md)
- [在 Intune 論壇中發問](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [查看 Microsoft Intune 支援小組部落格](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess) \(英文\)
- [查看 Microsoft Enterprise Mobility 與安全性小組部落格](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210) \(英文\)