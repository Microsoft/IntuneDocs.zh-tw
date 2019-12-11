---
title: 向 Intune 公司入口網站註冊您的 Mac |Microsoft Docs
description: 瞭解如何使用公司入口網站應用程式在 Intune 中註冊您的 Mac。
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: kakyker
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba285fc9de58b3fb739a16722e0e05e36e840e87
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74098095"
---
# <a name="enroll-your-macos-device-using-the-company-portal-app"></a>使用公司入口網站應用程式註冊您的 macOS 裝置  

使用 Intune 公司入口網站應用程式註冊您的 macOS 裝置，以安全地存取您的公司或學校電子郵件、檔案和應用程式。

組織通常會要求您註冊您的裝置，才能存取專屬資料。 您的裝置註冊之後，它就變成「受控」  。 您的組織可以透過 Intune 等行動裝置管理 (MDM) 提供者將原則和應用程式指派給裝置。 若要從您的裝置持續存取公司或學校資訊，您必須設定裝置以符合您組織的原則設定。  

本文描述如何使用適用於 macOS 的公司入口網站應用程式來註冊、設定及維護裝置，以符合您組織的要求。  


## <a name="what-to-expect-from-the-company-portal-app"></a>公司入口網站應用程式的預期行為

在初始設定期間，公司入口網站應用程式會要求您先登入並向您的組織驗證。 公司入口網站接著會通知您需要設定以符合組織需求的任何裝置設定。 例如，組織通常會設定您必須符合的密碼字元數下限或上限需求。    

註冊裝置之後，公司入口網站一律會確保您的裝置會根據貴組織的需求受到保護。 例如，如果您安裝來自不受信任來源的應用程式，公司入口網站會發出警示，且可能會限制對您組織資源的存取。 這類應用程式保護原則是常見的。 若要重新取得存取權，您可能需要卸載不受信任的應用程式。 

如果在註冊之後，您的組織強制執行新的安全性需求 (例如多重要素驗證)，公司入口網站會通知您。 您將有機會調整設定，以便繼續在裝置上工作。  

若要深入了解註冊，請參閱[當我安裝公司入口網站應用程式並註冊我的裝置時，會發生什麼情況？](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md)  

## <a name="get-your-macos-device-managed"></a>讓您的 macOS 裝置受管理  
使用下列步驟向您的組織註冊您的 macOS 裝置。 您的裝置必須執行 macOS 10.12 或更新版本。   

> [!NOTE]
> 在整個過程中，系統可能會提示您允許公司入口網站使用儲存在 keychain 中的機密資訊。 這些提示是 Apple 安全性的一部分。 當您收到提示時，請輸入您的登入 keychain 密碼，然後選取 [**永遠允許**]。 如果您按**enter**鍵或在鍵盤上**返回**，則提示會改為選取 [**允許**]，這可能會導致額外的提示。  

### <a name="install-company-portal-app"></a>安裝公司入口網站應用程式  
1. 移至 [[註冊我的 Mac](https://go.microsoft.com/fwlink/?linkid=853070)]。  
2. 公司入口網站 .pkg 檔案將會下載。 開啟安裝程式，並繼續執行步驟。 
3. 同意軟體授權合約。 
4. 輸入您的裝置密碼或已註冊的指紋，以安裝軟體。  
5. 開啟公司入口網站。 

> [!IMPORTANT]
> 「Microsoft 自動更新」可能會開啟以更新您的 Microsoft 軟體。 安裝所有更新之後，請開啟公司入口網站應用程式。 若要獲得最佳的安裝經驗，請安裝最新版的 Microsoft 自動更新和公司入口網站。  


### <a name="enroll-your-mac"></a>註冊您的 Mac  


1. 使用您的公司或學校帳戶登入公司入口網站。  
2. 當應用程式開啟時，請選取 [**開始**]。  
3. 檢查您的組織在您已註冊的裝置上[可以看到和不能看見的內容](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)。 接著，選取 [繼續]  。  
4. 在 [**安裝管理設定檔**] 畫面上，選取 [**下載設定檔**]。   

    ![公司入口網站 [安裝管理設定檔] 畫面的範例螢幕擷取畫面，其中反白顯示 [下載設定檔] 按鈕。](./media/install-mgmt-profile-mac-1911.PNG)   
5. 您裝置的系統喜好設定將會開啟。 選取 [**安裝**]，然後再次選取 [**安裝**]。 若出現提示，請輸入您的裝置密碼。  

    ![MacOS 系統喜好設定（安裝提示）的範例螢幕擷取畫面，反白顯示 [安裝] 按鈕。](./media/system-preference-install-1911.PNG)  
6. 安裝設定檔之後，它會出現在 [**管理設定檔**] 底下的配置檔案清單中。  

   ![MacOS 系統喜好設定 [設定檔] 畫面的範例螢幕擷取畫面，其中反白顯示已安裝的管理設定檔。](./media/system-preference-verify-1911.PNG)   
7. 返回公司入口網站。   
8. 您的組織可能會要求您更新您的裝置設定。 當您完成更新設定時，請選取 [**檢查設定**]。  

    ![公司入口網站的範例螢幕擷取畫面，[更新裝置設定] 畫面，反白顯示 [檢查設定] 按鈕。](./media/update-settings-mac-1911.PNG)  
9. 當安裝程式完成時，請選取 [**完成**]。  


 ## <a name="troubleshooting-and-feedback"></a>疑難排解與意見反應   

如果您在註冊期間遇到問題，請移至 說明 ** > ** **傳送診斷報告**，將問題回報給 Microsoft 應用程式開發人員。 這是用來協助改善應用程式的資訊。 他們也會使用此資訊來協助解決問題（如果您的 IT 支援人員與他們聯繫以取得協助）。  

將問題回報給 Microsoft 之後，您可以將體驗的詳細資料傳送給您的 IT 支援人員。 選取 [**電子郵件詳細資料**]。 輸入您在電子郵件內文中遇到的內容。 若要尋找支援人員的電子郵件地址，請移至公司入口網站應用程式 >**連絡人**。 或檢查[公司入口網站網站](https://go.microsoft.com/fwlink/?linkid=2010980)。  
 

此外，Microsoft Intune 公司入口網站團隊也很樂意聽到您的意見反應。 前往 [說明 **] > ** **傳送意見**反應，分享您的想法和想法。  

## <a name="unverified-profiles"></a>未驗證的設定檔  
當您在 [系統喜好設定]   > [設定檔]  中檢視已安裝的行動裝置管理 (MDM) 設定檔時，有些設定檔可能會顯示未驗證狀態。 只要管理設定檔顯示已驗證狀態，您就不需要擔心。  

管理設定檔定義 MDM 通道連線。 只要管理設定檔經過驗證，透過該通道傳遞至機器的任何其他設定檔就會繼承管理設定檔的安全性特性。  

## <a name="updating-the-company-portal-app"></a>更新公司入口網站應用程式

更新公司入口網站應用程式的完成方式與任何其他 Office 應用程式一樣，都是透過適用於 macOS 的 Microsoft AutoUpdate。 深入了解[更新 macOS 版的 Microsoft 應用程式](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1)。  

## <a name="next-steps"></a>後續步驟  
是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。  


