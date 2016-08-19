---
title: "Microsoft Intune 的版本資訊 | Microsoft Intune"
description: "Intune 版本資訊"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: d4961042d3fbd1d6467fa784db5adef6ed5f7f1f


---

# Microsoft Intune 的版本資訊
Microsoft Intune 是一套整合式雲端架構的用戶端管理解決方案。除了提供最新版 Windows 的工具、報表和升級授權之外，還能幫助您讓電腦保持最新狀態並維護電腦安全。 此外，Intune 也可讓您透過 Exchange ActiveSync 或是直接透過 Intune 管理網路上的行動裝置。 下列版本資訊說明 Microsoft Intune 的重要資訊和已知問題。


## 實作 Exchange Online 條件式存取時，Android 使用者無法傳送電子郵件

設定 Exchange Online 的條件式存取之後，在裝置上執行 Samsung Android 5.1.1 和更新版本的使用者無法傳送電子郵件。 Samsung 確認問題出在 Android 5.1.1 和更新版本中內建的郵件用戶端，目前正在研究修正程式。

**因應措施 1：**建議使用者使用適用於 Android 的 Outlook 應用程式。

**因應措施 2：**若要讓受影響的使用者能夠傳送電子郵件，請遵循下列步驟 ︰

1. 將受影響的使用者放入 Exchange Online 條件式存取原則的「豁免群組」區段中的安全性群組。
2. 允許使用者在內建的電子郵件用戶端上暫時同步電子郵件。
3. 從豁免群組中移除受影響的使用者，並確認使用者現在可以傳送電子郵件。

Microsoft 將持續與 Samsung 密切合作來研究修正程式或其他因應措施。



## 在 iOS 和 Android 群組之間變更資源存取設定檔可能會失敗
**問題︰**當您變更群組之間的電子郵件或簡單憑證註冊通訊協定 (SCEP) 資源存取設定檔時，設定檔可能會發生衝突並且失敗。 比方說，假設您有現有的電子郵件設定檔，指向內部部署 Exchange 伺服器，以群組 A 為目標，然後您建立了新的電子郵件設定檔，指向 Exchange Online，並以群組 B 為目標。當您將使用者從群組 A 移到群組 B 時，裝置將保留內部部署的 Exchange 電子郵件設定檔，並嘗試安裝以群組 B 為目標的 Exchange Online 電子郵件設定檔。

此時，發生下列其中一種情況： 
* 如果電子郵件設定檔 A 和 B 相同，裝置會拒絕電子郵件設定檔 B，因為電子郵件設定檔 B 已經包含電子郵件設定檔 A。
* 如果電子郵件設定檔 A 與電子郵件設定檔 B 不同，如上述範例中所述，則裝置最後會有兩個電子郵件設定檔。

**注意︰**會檢查使用者名稱所用的主機名稱和屬性，以區別電子郵件設定檔。

在上述兩種情況下，不會移除資源存取設定檔 (電子郵件設定檔)，以防止意外移除使用者對電子郵件或用戶端 SCEP 憑證的存取。

**因應措施：** 無。

## 在註冊必須完成 Proxy 伺服器驗證的 Windows 8.1 裝置時註冊程序失敗，且未顯示任何有關失敗原因的指示
**問題：**當您註冊 Windows 8.1 裝置，且該裝置在註冊過程中必須向 Proxy 伺服器驗證時，如果裝置未快取 Proxy 伺服器認證，註冊便會失敗。 當裝置未快取 Proxy 伺服器的認證時，註冊程序必須等待使用者輸入認證。 不過，註冊過程中並未顯示提供 Proxy 伺服器認證的提示。 結果造成註冊程序無法通過 Proxy 伺服器驗證，而且使用者不會看到這項失敗的任何指示。

**因應措施：**若 Windows 8.1 裝置必須在需要使用已驗證之 Proxy 伺服器的網路上註冊，請在註冊裝置之前設定並儲存 Proxy 伺服器的認證。 若要在 Windows 8.1 裝置上設定並儲存認證：

1.  在 Windows 8.1 裝置上，開啟 **Internet Explorer**。

2.  當系統提示您輸入 Proxy 伺服器認證時，請輸入認證，然後選取 [記住我的認證] 選項。

3.  註冊裝置。

## 當 AD FS 中啟用了裝置驗證時，無法對 Microsoft Intune 註冊 Windows Phone 8.1 裝置。
**問題：** 當您註冊 Windows Phone 8.1 裝置時，如果將裝置驗證的選用設定當作 Active Directory 同盟服務 (AD FS) 中全球驗證原則的一部分啟用，註冊會失敗。

**因應措施：** 取消核取 [編輯全域驗證原則]  中的 [啟用裝置驗證] ，以停用 AD FS 伺服器上的裝置驗證。 如需詳細資訊，請參閱 [設定驗證原則](http://technet.microsoft.com/library/dn486781.aspx)(英文)。


## 適用於 Android 的 Microsoft Intune 應用程式包裝工具沒有任何內建的解除安裝功能
**問題：****Microsoft App Wrapping Tool for Android** 沒有任何內建功能可用來解除安裝工具。

**因應措施：** 瀏覽至安裝工具的位置，然後刪除該目錄。 預設安裝位置為：**C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**。 如需 App Wrapping Tool 的詳細資訊，請參閱[準備將 Android 應用程式交由 App Wrapping Tool 管理](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)。

## 執行 Windows 8 或 Windows 8.1 的電腦無法使用遠端協助
**問題：** 在這個版本中，遠端協助功能無法在執行 Windows 8 或 Windows 8.1 的電腦上使用。

**因應措施：** 無。

## 自動新增的收件者警示通知可能無法運作
**問題：** 如果將收件者自動加入到警示通知，他們並不一定會收到通知。

**因應措施：** 若要確定收件者會收到訊息通知，您應手動將收件者加入到警示通知名單中。

## Azure Preview 入口網站中的語言支援
Azure Preview 入口網站建置在新的平台上，支援下列語言：簡體中文、繁體中文、捷克文、荷蘭文、英文、德文、匈牙利文、義大利文、日文、葡萄牙文 (巴西)、葡萄牙文 (葡萄牙)、俄文、西班牙文、英文、法文、韓文、波蘭文、瑞典文、土耳其文。

Intune 管理主控台和使用者導向的行動體驗支援丹麥文、希臘文、芬蘭文、挪威文和羅馬尼亞文，以及 Azure Preview 入口網站支援的所有語言。



<!--HONumber=Jul16_HO4-->


