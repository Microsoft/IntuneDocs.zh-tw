---
title: "行動應用程式管理疑難排解 | Microsoft Docs"
description: "本主題描述一些針對條件式存取部署進行疑難排解的秘訣。"
keywords: 
author: oydang
ms.author: oydang
manager: angerobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: a2e43444bff3b189c1516c6ca7131771035313ea
ms.openlocfilehash: 6258917de60bdbf8efde4720c17ec6fc643154bd
ms.lasthandoff: 12/30/2016


---

# <a name="troubleshoot-mobile-application-management"></a>行動應用程式管理疑難排解

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

如果您有 Intune 行動應用程式管理的問題，請從這裡開始。 本主題包含一些您可能會遇到的常見問題和疑問，並提供解決方法與解答。

如果此資訊無法解決您的問題，請參閱[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)，以尋找更多方法來取得協助。


## <a name="common-it-administrator-issues"></a>常見的 IT 系統管理員問題

這些是 IT 管理員在使用 Intune 應用程式保護原則時經常碰到的問題。

| 問題 | 說明 | 解決方法 |
| -- | -- | -- |
| 原則未套用至商務用 Skype | 在 Azure 入口網站中設定的無裝置註冊應用程式保護原則，未套用至 iOS 和 Android 裝置上的商務用 Skype。 | 商務用 Skype 必須設定使用新式驗證。  請依照 [Enable your tenant for modern authentication](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) (啟用租用戶的新式驗證) 中的指示，設定 Skype 的新式驗證。 |
| 未套用 office 應用程式原則 | 應用程式保護原則不適用於任何使用者的任何[支援的 Office 應用程式](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)。 | 確認使用者已獲得 Intune 授權，且部署的應用程式保護原則已將 Office 應用程式設為目標。 新部署的應用程式保護原則可能需要最多 8 小時才會套用。 |
| 管理員無法在 Azure 入口網站中設定應用程式保護原則 | IT 管理員使用者無法在 Azure 入口網站中設定應用程式保護原則。 | 下列使用者角色可以存取 Azure 入口網站： <ul><li>全域管理員，您可以在 [Office 入口網站](http://portal.office.com/)中設定</li><li>擁有者，您可以在 [Azure 入口網站](https://portal.azure.com/)中設定。</li><li>參與者，您可以在 [Azure 入口網站](https://portal.azure.com/)中設定。</li></ul>  如需設定這些角色的說明，請參閱[準備使用 Microsoft Intune 設定行動應用程式管理原則](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)。|
|應用程式保護原則報表中遺漏使用者帳戶 | 管理員主控台報表沒有顯示最近部署應用程式保護原則的使用者帳戶。 | 如果使用者是應用程式保護原則的新目標，則可能需要最多 24 小時該使用者才會以目標使用者的狀態顯示在報表中。 |
| 原則變更不作用 | 套用應用程式保護原則的變更與更新最多需時 8 個小時。 | 如適用，終端使用者可以登出應用程式並重新登入，來強制與服務同步。 |
| 應用程式保護原則不適合 DEP | 應用程式保護原則不適用 Apple DEP 裝置。 | 請確認 Apple「裝置登記方案」(DEP) 與「使用者親和性」搭配使用。 需要在 DEP 下進行使用者驗證的任何應用程式都需要有使用者親和性。 <br><br>如需 iOS DEP 註冊的詳細資訊，請參閱[註冊屬公司擁有的裝置註冊方案 iOS 裝置](../deploy-use/ios-device-enrollment-program-in-microsoft-intune.md)。|
| 資料傳輸原則不適合 iOS | [允許應用程式將資料傳送至其他應用程式] 和 [允許應用程式接收其他應用程式的資料] 原則在 iOS 中不能順利管理資料傳輸。 | 請參閱[使用 Microsoft Intune 管理 iOS 應用程式之間的資料傳輸](/deploy-use/manage-data-transfer-between-ios-apps-with-microsoft-intune.md)。 |






## <a name="common-end-user-issues"></a>常見使用者問題

常見終端使用者問題會細分為下列類別︰

* **一般使用案例**︰終端使用者在有 Intune 應用程式保護原則的應用程式上可能會遇到這些情況。 這些都不是真正的問題，但可能被視為 Bug 或錯誤。

* **一般使用方式對話方塊**︰這些是終端使用者在有 Intune 應用程式保護原則的應用程式中可能會看到的使用方式對話方塊。 這些訊息和對話方塊**不**顯示錯誤或 Bug。

* **錯誤訊息和對話方塊**︰這些是終端使用者在有 Intune 應用程式保護原則的應用程式中可能會看到的錯誤訊息和對話方塊。 它們顯示的錯誤通常是由 IT 管理員或 Intune 應用程式保護 Bug 所造成。



### <a name="normal-usage-scenarios"></a>一般使用案例

平台 | 案例 | 說明 |
---| --- | --- |
iOS | 終端使用者可以使用 iOS 共用延伸模組在不受管理的應用程式中開啟工作或學校資料，甚至可將資料傳輸原則設為 [僅限受管理的應用程式] 或 [沒有應用程式]。 這樣不會流失資料嗎？ | Intune 應用程式保護原則必須管理裝置才能控制 iOS 共用延伸模組。 因此，**Intune 會先加密「公司」資料再於應用程式外共用**。 您可以嘗試在受管理的應用程式外開啟「公司」檔案加以驗證。 檔案應已加密且無法在受管理的應用程式之外開啟。
Android | 為什麼終端使用者**需要安裝公司入口網站應用程式**，即使我使用的是無裝置註冊的 MAM 應用程式保護？  | 在 Android 上，大部分的應用程式保護功能是內建在公司入口網站應用程式中。 **即使公司入口網站應用程式一律為必要，也不需要註冊裝置**。 至於無裝置註冊的應用程式保護，終端使用者只需要在裝置上安裝公司入口網站應用程式即可。

### <a name="normal-usage-dialogs"></a>一般使用方式對話方塊

平台 | 訊息或對話方塊 | 說明 |
--- | --- | --- |
iOS、Android | **登入**︰若要保護其資料，貴組織需要管理此應用程式。 請使用工作或學校帳戶登入以完成此動作。 | 終端使用者必須使用其工作或學校帳戶登入才能使用此應用程式，這需要應用程式保護原則。 為使原則能套用，使用者必須針對 Azure Active Directory 進行驗證。
iOS、Android |**需要重新啟動**︰貴組織正在保護此應用程式中的資料。 您需要重新啟動應用程式才能繼續。 | 應用程式剛剛收到 Intune 應用程式保護原則，必須重新啟動才能套用原則。
iOS、Android |**不允許動作**：貴組織只允許您開啟此應用程式中的工作或學校資料。 | IT 管理員已將 [允許應用程式接收其他應用程式的資料] 設成 [僅限受管理的應用程式]。 因此，終端使用者只能將資料從有應用程式保護原則的其他應用程式傳輸到此應用程式。
iOS、Android |**不允許動作**：貴組織只允許您將其資料轉移至其他受管理的應用程式。 | IT 管理員已將 [允許應用程式將資料傳送至其他應用程式] 設成 [僅限受管理的應用程式]。 因此，終端使用者只能將資料由此應用程式傳輸到有應用程式保護原則的其他應用程式。
iOS、Android |**抹除警示**：貴組織已移除其與此應用程式相關聯的資料。 若要繼續，請重新啟動應用程式。 | IT 管理員已使用 Intune 應用程式保護開始應用程式抹除。
Android | **需要公司入口網站**：您必須安裝 Intune 公司入口網站應用程式，才可搭配使用您的工作或學校帳戶與此應用程式。 請點選 [前往商店] 以繼續。 | 在 Android 上，大部分的應用程式保護功能是內建在公司入口網站應用程式中。 **即使公司入口網站應用程式一律為必要，也不需要註冊裝置**。 至於無裝置註冊的應用程式保護，終端使用者只需要在裝置上安裝公司入口網站應用程式即可。


### <a name="error-messages-and-dialogs-on-ios"></a>iOS 的錯誤訊息和對話方塊


錯誤訊息或對話方塊 | 原因 | 修復 |
-- | --- | --- |
**應用程式未設定**：此應用程式未設定供您使用。 如需協助，請連絡 IT 系統管理員。 | 無法針對該應用程式偵測所需的應用程式保護原則。 |請確認 iOS 應用程式保護原則已部署至使用者的安全性群組，且以此應用程式為目標。
**歡迎使用 Intune Managed Browser**：此應用程式在由 Microsoft Intune 管理的情況下，可以達到最佳的運作效果。 您隨時可以使用此應用程式來瀏覽網路，且當它由 Microsoft Intune 管理時，還能進一步存取其他資料保護功能。 | 無法針對該 Intune Managed Browser 應用程式偵測所需的應用程式保護原則。 <br><br>使用者仍可以使用該應用程式瀏覽網站，但應用程式不受 Intune 管理。 | 請確認 iOS 應用程式保護原則已部署至使用者的安全性群組，且以該 Intune Managed Browser 應用程式為目標。
**登入失敗**：目前無法將您登入。 請稍後再試一次。 | 使用者嘗試以工作或學校帳戶登入之後，無法向 MAM 服務註冊使用者。 | 請確認 iOS 應用程式保護原則已部署至使用者的安全性群組，且以此應用程式為目標。
**帳戶未設定**：貴組織尚未將您的帳戶設定為可存取工作或學校資料。 請連絡您的 IT 系統管理員以尋求協助。 | 該使用者帳戶沒有 Intune A Direct 授權。 | 請確認使用者的帳戶具有在 [Office 入口網站](http://portal.office.com)中指派的 Intune 授權。
**裝置不符合規範**無法使用此應用程式，因為您是使用越獄的裝置。 如需協助，請連絡 IT 系統管理員。 | Intune 偵測到使用者是在越獄的裝置上。 | 將裝置重設為原廠設定。 請遵循 Apple 支援網站的[這些指示](https://support.apple.com/en-us/HT201274)。
**需要網際網路連線**：您必須連線至網際網路，以驗證您是否可使用此應用程式。 | 裝置未連線至網際網路。 | 請將裝置連線至 WiFi 或資料網路。
**未知錯誤**：請嘗試重新啟動此應用程式。 如果問題持續發生，請連絡您的 IT 系統管理員尋求協助。 | 發生未知錯誤。 | 請稍待片刻，然後再試一次。 如果錯誤持續發生，請在[這裡](how-to-get-support-for-microsoft-intune.md)建立 Intune 的支援票證。
**正在存取貴組織的資料**：您指定的工作或學校帳戶無權存取此應用程式。 您可能必須使用不同的帳戶登入。 如需協助，請連絡 IT 系統管理員。 | Intune 偵測到使用者嘗試以不同於該裝置之 MAM 註冊帳戶的第二個工作或學校帳戶來登入。 每部裝置一次只能有一個工作或學校帳戶由 MAM 管理。 | 讓使用者以登入畫面預先填入的使用者名稱登入。 <br> <br> 或者，讓使用者以新的工作或學校帳戶登入，並移除現有的 MAM 註冊帳戶。
**連線問題**：發生未預期的連線問題。 請檢查您的連線並再試一次。  |  發生非預期的失敗。 | 請稍待片刻，然後再試一次。 如果錯誤持續發生，請在[這裡](how-to-get-support-for-microsoft-intune.md)建立 Intune 的支援票證。
**警示**：此應用程式已無法再使用。 如需詳細資訊，請洽詢 IT 系統管理員。 | 無法驗證應用程式的憑證。 | 請確認應用程式為最新版。 <br><br> 重新安裝應用程式。
**錯誤**：這個應用程式遇到問題，必須關閉。 如果問題持續發生，請連絡您的 IT 系統管理員。 | 無法從 Apple iOS 鑰匙圈讀取 MAM 應用程式 PIN。 | 重新啟動裝置。 請確認應用程式為最新版。 <br><br> 重新安裝應用程式。


### <a name="error-messages-and-dialogs-on-android"></a>Android 的錯誤訊息和對話方塊

對話方塊/錯誤訊息 | 原因 | 修復 |
-- | --- | --- |
**應用程式未設定**：此應用程式未設定供您使用。 如需協助，請連絡 IT 系統管理員。 | 無法針對該應用程式偵測所需的應用程式保護原則。 |請確認 Android 應用程式保護原則已部署至使用者的安全性群組，且以此應用程式為目標。
**應用程式啟動失敗**：啟動應用程式發生問題。 請嘗試更新該應用程式或 Intune Company 入口網站應用程式。 如果您需要協助，請連絡您的 IT 系統管理員。 | Intune 針對該應用程式偵測到有效的應用程式保護原則，但應用程式在 MAM 初始化期間當機。 | 請確認應用程式為最新版。 <br><br> 請確認裝置上已經安裝 Intune 公司入口網站應用程式且為最新版。 <br><br> 如果錯誤持續發生，請使用入口網站應用程式將記錄傳送至 Intune，或在[這裡](how-to-get-support-for-microsoft-intune.md)建立支援票證。
**找不到任何應用程式**：此裝置上沒有您公司允許用來開啟此內容的任何應用程式。 如需協助，請連絡 IT 系統管理員。 | 使用者嘗試以其他應用程式開啟工作或學校資料，但 Intune 找不到任何其他已允許可開啟該資料之受管理的應用程式。 | 請確認已將 Android 應用程式保護原則部署到該使用者的安全性，並且至少將另一個支援 MAM 且開啟資料有問題的應用程式設為目標。
**登入失敗**：請嘗試重新登入。 如果此問題持續發生，請連絡您的 IT 系統管理員尋求協助。 | 無法驗證使用者嘗試登入的帳戶。 | 請確認使用者是使用已經向 MAM 服務註冊的工作或學校帳戶登入 (第一個登入此應用程式的工作或學校帳戶)。 <br><br> 清除應用程式的資料。 <br><br> 請確認應用程式為最新版。 <br><br> 請確認公司入口網站為最新版。
**需要網際網路連線**：您必須連線至網際網路，以驗證您是否可使用此應用程式。 | 裝置未連線至網際網路。 | 請將裝置連線至 WiFi 或資料網路。
**裝置不符合規範**無法使用此應用程式，因為您是使用已進行 Root 破解的裝置。 如需協助，請連絡 IT 系統管理員。 | Intune 偵測到使用者是在已進行 Root 破解的裝置上。 | 將裝置重設為原廠設定。
**帳戶未設定**：此應用程式必須由 Microsoft Intune 管理，但您的帳戶尚未設定。 如需協助，請連絡 IT 系統管理員。 | 該使用者帳戶沒有 Intune A Direct 授權。 | 請確認使用者的帳戶具有在 [Office 入口網站](http://portal.office.com)中指派的 Intune 授權。
**無法登錄應用程式**：此應用程式必須由 Microsoft Intune 管理，但我們目前無法註冊此應用程式。 如需協助，請連絡 IT 系統管理員。 | 當應用程式保護原則為必要條件時，無法自動向 MAM 服務註冊應用程式。 | 清除應用程式的資料。 <br><br> 請使用入口網站應用程式將記錄傳送至 Intune，或在[這裡](how-to-get-support-for-microsoft-intune.md)建立支援票證。




### <a name="see-also"></a>請參閱
- [驗證您的行動應用程式管理設定](../deploy-use/validate-mobile-application-management.md)
- [準備使用 Microsoft Intune 設定行動應用程式管理原則](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
- [如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)

