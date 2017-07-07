---
title: "Microsoft Intune 的版本資訊"
description: "Intune 版本資訊"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 751bd0bc90b762c5b51b85fae2129e53773b54fe
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="release-notes-for-microsoft-intune"></a>Microsoft Intune 的版本資訊

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 是一套整合式雲端架構的用戶端管理解決方案。除了提供最新版 Windows 的工具、報表和升級授權之外， 還能幫助您讓電腦保持最新狀態並維護電腦安全。 此外，Intune 也可讓您透過 Exchange ActiveSync 或是直接透過 Intune 管理網路上的行動裝置。 下列版本資訊說明 Microsoft Intune 的重要資訊和已知問題。

<!-- 3-6-17: customer asked if this is still current; Stacie asked Chris Baldwin about it. Chris said it's a Samsung issue, but that he hasn't heard any reports about it for months, so he suggested that I share that with the customer and remove this item from the release notes. I'm only going to comment it out in case it resurfaces.
## Android users can’t send email when conditional access for Exchange Online is implemented

**Issue:** Users running Samsung Android 5.1.1 and later on their devices can't send email when conditional access for Exchange Online has been set up. Samsung acknowledges that the issue is in its built-in email client in Android 5.1.1 and later, and is investigating a fix.

**Workaround 1:** Advise users to use the Outlook app for Android.

**Workaround 2:** To let affected users send email, you can follow these steps:

1. Put each affected user in a security group in the “exempted groups” section of the conditional access policy for Exchange Online.
2. Let the user temporarily sync email on the built-in email client.
3. Remove the affected user from the exempted group, and confirm that the user can now send email.

Microsoft will continue to work closely with Samsung on a fix or additional workarounds.
-->


## <a name="changing-resource-access-profiles-between-groups-for-ios-and-android-might-fail"></a>在 iOS 和 Android 群組之間變更資源存取設定檔可能會失敗
**問題**︰當您變更群組之間的電子郵件或簡單憑證註冊通訊協定 (SCEP) 資源存取設定檔時，設定檔可能會發生衝突並且失敗。 例如，假設您有現有的電子郵件設定檔，指向內部部署 Exchange 伺服器，並以群組 A 為目標。然後您建立了新的電子郵件設定檔，指向 Exchange Online，並以群組 B 為目標。當您將使用者從群組 A 移到群組 B 時，裝置將保留內部部署的 Exchange 電子郵件設定檔，並嘗試安裝以群組 B 為目標的 Exchange Online 電子郵件設定檔。

此時，發生下列其中一種情況： 
* 如果電子郵件設定檔 A 和 B 相同，裝置會拒絕電子郵件設定檔 B，因為電子郵件設定檔 B 已經包含電子郵件設定檔 A。
* 如果電子郵件設定檔 A 與電子郵件設定檔 B 不同，如範例中所述，則裝置最後會有兩個電子郵件設定檔。

> [!NOTE]
> 系統會檢查使用者名稱所用的主機名稱和屬性，以區別電子郵件設定檔。

在這兩種情況下，不會移除裝置的資源存取設定檔 (電子郵件設定檔)，以防止意外移除使用者對電子郵件或用戶端 SCEP 憑證的存取。

**因應措施：** 無。

## <a name="when-you-enroll-a-windows-81-device-that-must-authenticate-to-a-proxy-server-the-enrollment-process-fails-with-no-visible-cause"></a>在註冊必須完成 Proxy 伺服器驗證的 Windows 8.1 裝置時，註冊程序失敗，且未顯示任何原因
**問題：**當您註冊 Windows 8.1 裝置，且該裝置在註冊過程中必須向 Proxy 伺服器驗證時，如果裝置未快取 Proxy 伺服器認證，註冊便會失敗。 當裝置未快取 Proxy 伺服器的認證時，註冊程序必須等待使用者輸入認證。 但是，註冊過程中並未出現提供 Proxy 伺服器認證的提示。 結果造成註冊程序無法通過 Proxy 伺服器驗證， 而且使用者不會看到這項失敗的任何指示。

**因應措施**：若 Windows 8.1 裝置必須在需要使用已驗證之 Proxy 伺服器的網路上註冊，請在註冊裝置之前設定並儲存 Proxy 伺服器的認證。 若要在 Windows 8.1 裝置上設定並儲存認證：

1.  在 Windows 8.1 裝置上，開啟 Internet Explorer。
2.  當系統提示您輸入 Proxy 伺服器認證時，請輸入認證，然後選擇 [記住我的認證] 選項。
3.  註冊裝置。

## <a name="windows-phone-81-devices-fail-to-enroll-with-microsoft-intune-when-device-authentication-is-enabled-in-ad-fs"></a>當 AD FS 中啟用了裝置驗證時，無法對 Microsoft Intune 註冊 Windows Phone 8.1 裝置。
**問題**：當您註冊 Windows Phone 8.1 裝置時，如果將裝置驗證的選擇性設定當作 Active Directory 同盟服務 (AD FS) 中全域驗證原則的一部分啟用，註冊會失敗。

**因應措施：** 取消核取 [編輯全域驗證原則]  中的 [啟用裝置驗證] ，以停用 AD FS 伺服器上的裝置驗證。 如需詳細資訊，請參閱 [Configuring Authentication Policies](http://technet.microsoft.com/library/dn486781.aspx) (設定驗證原則)。


## <a name="microsoft-intune-app-wrapping-tool-for-android-has-no-built-in-uninstall-capability"></a>適用於 Android 的 Microsoft Intune 應用程式包裝工具沒有任何內建的解除安裝功能
**問題：****Microsoft App Wrapping Tool for Android** 沒有任何內建功能可用來解除安裝工具。

**因應措施：** 瀏覽至安裝工具的位置，然後刪除該目錄。 預設安裝位置為：**C:\Program Files\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool。 如需 App Wrapping Tool 的詳細資訊，請參閱[準備將 Android 應用程式交由 App Wrapping Tool 管理](/intune/app-wrapper-prepare-android)。

## <a name="remote-assistance-is-not-available-on-computers-that-run-windows-8-or-windows-81"></a>執行 Windows 8 或 Windows 8.1 的電腦無法使用遠端協助
**問題：** 在這個版本中，遠端協助功能無法在執行 Windows 8 或 Windows 8.1 的電腦上使用。

**因應措施：** 無。

## <a name="alert-notifications-for-recipients-that-are-automatically-added-might-not-work"></a>自動新增的收件者警示通知可能無法運作
**問題**：如果將收件者自動新增至警示通知，他們並不一定會收到通知。

**因應措施**：為了確定收件者會收到訊息通知，您應手動將收件者新增至警示通知。

## <a name="language-support-in-the-azure-portal"></a>Azure 入口網站的語言支援
Azure 入口網站支援下列語言：簡體中文、繁體中文、捷克文、荷蘭文、英文、德文、匈牙利文、義大利文、日文、葡萄牙文 (巴西)、葡萄牙文 (葡萄牙)、俄文、西班牙文、英文、法文、韓文、波蘭文、瑞典文、土耳其文。

Intune 管理主控台和使用者導向的行動體驗支援丹麥文、希臘文、芬蘭文、挪威文和羅馬尼亞文，以及 Azure 入口網站支援的所有語言。
