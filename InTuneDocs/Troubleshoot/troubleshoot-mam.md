---
title: "行動應用程式管理疑難排解 | Microsoft Docs"
description: "本主題描述一些針對條件式存取部署進行疑難排解的秘訣。"
keywords: 
author: NathBarn
ms.author: oldang
manager: angerobe
ms.date: 09/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
translationtype: Human Translation
ms.sourcegitcommit: d50a5751a5afd987196336e9443dc5a429a283fd
ms.openlocfilehash: b333c0f5097fec38bf0dd78726a028fd7aaccd2f


---

# <a name="troubleshoot-mobile-application-management"></a>行動應用程式管理疑難排解

如果您有 Intune 行動應用程式管理的問題，請從這裡開始。 本主題包含一些您可能會遇到的常見問題和疑問，並提供解決方法與解答。

## <a name="common-it-administrator-issues"></a>常見的 IT 系統管理員問題

1. **問題：**在 Azure 入口網站中設定的無裝置註冊應用程式保護原則，沒有套用至 iOS 和 Android 裝置上的商務用 Skype。

  **解決方法**：商務用 Skype 必須設定為使用新式驗證。  請依照 [Enable your tenant for modern authentication](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) (啟用租用戶的新式驗證) 中的指示，設定 Skype 的新式驗證。

2. **問題：**應用程式保護原則沒有為任何使用者套用至任何[支援的 Office 應用程式](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)。

  **解決方法**：確認使用者已獲得 Intune 授權，且部署的應用程式保護原則已將 Office 應用程式設為目標。 新部署的應用程式保護原則可能需要最多 8 小時才會套用。

3. **問題：**IT 系統管理員使用者無法在 Azure 入口網站中設定應用程式保護原則。

  **解決方案**：

  下列使用者角色可以存取 Azure 入口網站：

  - 全域管理員，您可以在 [Office 入口網站](http://portal.office.com/)中設定
  - 擁有者，您可以在 [Azure 入口網站](https://portal.azure.com/)中設定。
  - 參與者，您可以在 [Azure 入口網站](https://portal.azure.com/)中設定。<br>

  如需設定這些角色的說明，請參閱[準備使用 Microsoft Intune 設定行動應用程式管理原則](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)。

4. **問題：**管理員主控台報表沒有顯示最近部署應用程式保護原則的使用者帳戶。

  **解決方法**：如果使用者是應用程式保護原則的新目標，則可能需要最多 24 小時該使用者才會以目標使用者的狀態顯示在報表中。

5. **問題**︰原則變更/更新最多可能需要花費 8 小時來套用。  

  **解決方法**：使用者可以登出應用程式並重新登入，來強制與服務同步。  

6. **問題：**應用程式保護原則沒有套用至 Apple DEP 裝置。

  **解決方法**：請確認您搭配使用「使用者親和性」與 Apple「裝置登記方案」(DEP)。 需要在 DEP 下進行使用者驗證的任何應用程式都需要有使用者親和性。
如需 iOS DEP 註冊的詳細資訊，請參閱[註冊屬公司擁有的裝置註冊方案 iOS 裝置](../deploy-use/ios-device-enrollment-program-in-microsoft-intune.md)。

## <a name="common-end-user-issues"></a>常見使用者問題

### <a name="issues-on-ios"></a>iOS 上的問題

對話方塊/錯誤訊息 | 原因 | 修復 |
-- | --- | --- |
**應用程式未設定**：此應用程式未設定供您使用。 如需協助，請連絡 IT 系統管理員。 | 無法針對該應用程式偵測所需的應用程式保護原則。 |請確認 iOS 應用程式保護原則已部署至使用者的安全性群組，且以此應用程式為目標。
**歡迎使用 Intune Managed Browser**：此應用程式在由 Microsoft Intune 管理的情況下，可以達到最佳的運作效果。 您隨時可以使用此應用程式來瀏覽網路，且當它由 Microsoft Intune 管理時，還能進一步存取其他資料保護功能。 | 無法針對該 Intune Managed Browser 應用程式偵測所需的應用程式保護原則。 <br><br>使用者仍可以使用該應用程式瀏覽網站，但應用程式不受 Intune 管理。 | 請確認 iOS 應用程式保護原則已部署至使用者的安全性群組，且以該 Intune Managed Browser 應用程式為目標。
**登入失敗**：目前無法將您登入。 請稍後再試一次。 | 使用者嘗試以工作或學校帳戶登入之後，無法向 MAM 服務註冊使用者。 | 請確認 iOS 應用程式保護原則已部署至使用者的安全性群組，且以此應用程式為目標。
**帳戶未設定**：貴組織尚未將您的帳戶設定為可存取工作或學校資料。 請連絡您的 IT 系統管理員以尋求協助。 | 該使用者帳戶沒有 Intune A Direct 授權。 | 請確認使用者的帳戶具有在 [Office 入口網站](http://portal.office.com)中指派的 Intune 授權。
**裝置不符合規範**無法使用此應用程式，因為您是使用越獄的裝置。 如需協助，請連絡 IT 系統管理員。 | Intune 偵測到使用者是在越獄的裝置上。 | 將裝置重設為原廠設定。 請遵循 Apple 支援網站的[這些指示](https://support.apple.com/en-us/HT201274)。
**需要網際網路連線**：您必須連線至網際網路，以驗證您是否可使用此應用程式。 | 裝置未連線至網際網路。 | 請將裝置連線至 WiFi 或資料網路。
**未知錯誤**：請嘗試重新啟動此應用程式。 如果問題持續發生，請連絡您的 IT 系統管理員尋求協助。 | 發生未知錯誤。 | 請稍待片刻，然後再試一次。 如果錯誤持續發生，請在[這裡](/how-to-get-support-for-microsoft-intune.md)建立 Intune 的支援票證。
**正在存取貴組織的資料**：您指定的工作或學校帳戶無權存取此應用程式。 您可能必須使用不同的帳戶登入。 如需協助，請連絡 IT 系統管理員。 | Intune 偵測到使用者嘗試以不同於該裝置之 MAM 註冊帳戶的第二個工作或學校帳戶來登入。 每部裝置一次只能有一個工作或學校帳戶由 MAM 管理。 | 讓使用者以登入畫面預先填入的使用者名稱登入。 <br> <br> 或者，讓使用者以新的工作或學校帳戶登入，並移除現有的 MAM 註冊帳戶。
**連線問題**：發生未預期的連線問題。 請檢查您的連線並再試一次。  |  發生非預期的失敗。 | 請稍待片刻，然後再試一次。 如果錯誤持續發生，請在[這裡](/how-to-get-support-for-microsoft-intune.md)建立 Intune 的支援票證。
**警示**：此應用程式已無法再使用。 如需詳細資訊，請洽詢 IT 系統管理員。 | 無法驗證應用程式的憑證。 | 請確認應用程式為最新版。 <br><br> 重新安裝應用程式。
**錯誤**：這個應用程式遇到問題，必須關閉。 如果問題持續發生，請連絡您的 IT 系統管理員。 | 無法從 Apple iOS 鑰匙圈讀取 MAM 應用程式 PIN。 | 重新啟動裝置。 請確認應用程式為最新版。 <br><br> 重新安裝應用程式。


### <a name="issues-on-android"></a>Android 上的問題

對話方塊/錯誤訊息 | 原因 | 修復 |
-- | --- | --- |
**應用程式未設定**：此應用程式未設定供您使用。 如需協助，請連絡 IT 系統管理員。 | 無法針對該應用程式偵測所需的應用程式保護原則。 |請確認 iOS 應用程式保護原則已部署至使用者的安全性群組，且以此應用程式為目標。
**應用程式啟動失敗**：啟動應用程式發生問題。 請嘗試更新該應用程式或 Intune Company 入口網站應用程式。 如果您需要協助，請連絡您的 IT 系統管理員。 | Intune 針對該應用程式偵測到有效的應用程式保護原則，但應用程式在 MAM 初始化期間當機。 | 請確認應用程式為最新版。 <br><br> 請確認裝置上已經安裝 Intune 公司入口網站應用程式且為最新版。 <br><br> 如果錯誤持續發生，請使用入口網站應用程式將記錄傳送至 Intune，或在[這裡](/how-to-get-support-for-microsoft-intune.md)建立支援票證。
**找不到任何應用程式**：此裝置上沒有您公司允許用來開啟此內容的任何應用程式。 如需協助，請連絡 IT 系統管理員。 | 使用者嘗試以其他應用程式開啟工作或學校資料，但 Intune 找不到任何其他已允許可開啟該資料之受管理的應用程式。 | 請確認已將 Android 應用程式保護原則部署到該使用者的安全性，並且至少將另一個支援 MAM 且開啟資料有問題的應用程式設為目標。
**登入失敗**：請嘗試重新登入。 如果此問題持續發生，請連絡您的 IT 系統管理員尋求協助。 | 無法驗證使用者嘗試登入的帳戶。 | 請確認使用者是使用已經向 MAM 服務註冊的工作或學校帳戶登入 (第一個登入此應用程式的工作或學校帳戶)。 <br><br> 清除應用程式的資料。 <br><br> 請確認應用程式為最新版。 <br><br> 請確認公司入口網站為最新版。
**需要網際網路連線**：您必須連線至網際網路，以驗證您是否可使用此應用程式。 | 裝置未連線至網際網路。 | 請將裝置連線至 WiFi 或資料網路。
**裝置不符合規範**無法使用此應用程式，因為您是使用已進行 Root 破解的裝置。 如需協助，請連絡 IT 系統管理員。 | Intune 偵測到使用者是在已進行 Root 破解的裝置上。 | 將裝置重設為原廠設定。
**帳戶未設定**：此應用程式必須由 Microsoft Intune 管理，但您的帳戶尚未設定。 如需協助，請連絡 IT 系統管理員。 | 該使用者帳戶沒有 Intune A Direct 授權。 | 請確認使用者的帳戶具有在 [Office 入口網站](http://portal.office.com)中指派的 Intune 授權。
**無法登錄應用程式**：此應用程式必須由 Microsoft Intune 管理，但我們目前無法註冊此應用程式。 如需協助，請連絡 IT 系統管理員。 | 當應用程式保護原則為必要條件時，無法自動向 MAM 服務註冊應用程式。 | 清除應用程式的資料。 <br><br> 請使用入口網站應用程式將記錄傳送至 Intune，或在[這裡](/how-to-get-support-for-microsoft-intune.md)建立支援票證。





### <a name="see-also"></a>請參閱
- [驗證您的行動應用程式管理設定](../deploy-use/validate-mobile-application-management.md)
- [準備使用 Microsoft Intune 設定行動應用程式管理原則](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


