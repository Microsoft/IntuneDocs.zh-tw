---
title: 使用公司入口網站在 Intune 註冊 macOS 裝置 | Microsoft Docs
description: 描述如何使用公司入口網站應用程式在 Intune 中註冊 macOS 裝置
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: d54c778923b0d217187f6e4c70e4bc8730788fbc
ms.sourcegitcommit: dde9e1e1d15c412751a186410c2a04974ff1b102
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2019
ms.locfileid: "55690796"
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>使用公司入口網站應用程式在 Intune 中註冊 macOS 裝置

使用 Intune 公司入口網站應用程式註冊您的 macOS 裝置，以安全地存取您組織的電子郵件、檔案和應用程式。

組織通常需要您讓裝置成為受控，才能存取其中的專屬資料。 裝置成為受控之後，組織可以透過其行動裝置管理提供者將原則和應用程式推送至裝置。 若要從您的裝置持續存取公司或學校資訊，您必須設定裝置以符合原則設定。  

本文說明適用於 macOS 的 Intune 公司入口網站應用程式如何協助您註冊、設定及維護裝置，以符合您組織的需求。

## <a name="what-to-expect-from-the-company-portal-app"></a>公司入口網站應用程式的預期行為

在初始設定期間，應用程式需要您向組織自我驗證。 應用程式接著會通知您必須進行的任何裝置設定。 例如，組織通常會設定您必須符合的密碼字元數下限或上限需求。    

註冊裝置之後，公司入口網站應用程式會繼續確保您的裝置受到保護。 例如，如果您從未受信任的來源安裝應用程式，應用程式會提醒您有時會撤銷公司資料的存取權。 這類應用程式防護原則在組織中很常見，而且通常需要您解除安裝未受信任的應用程式，才能重新取得存取權。

如果在註冊之後，您的組織強制執行新的安全性需求 (例如多重要素驗證)，公司入口網站應用程式會通知您。 您將有機會調整設定，以便繼續在裝置上工作。  

若要深入了解註冊，請參閱[當我安裝公司入口網站應用程式並註冊我的裝置時，會發生什麼情況？](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md)  

## <a name="get-your-device-managed"></a>讓您的裝置成為受控  
請使用下列步驟以註冊執行 OS X El Capitan 10.11 和更新版本的 macOS 裝置。   


1. 若要存取公司入口網站，請在 __Safari__ 中開啟新視窗，然後前往 https://portal.manage.microsoft.com 。  

2. 使用您的公司或學校帳戶登入公司入口網站。

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. 移至頁面左上角，然後按一下 [功能表] > [裝置]。  

4. [裝置] 頁面會顯示受控裝置清單或橫幅。 您所看到的內容取決於是否已有受控裝置。 
    * 若要新增未列出的裝置，請選取橫幅：[Tap here to tell us which device you're using or add a new device.] \(請點選這裡告訴我們您將使用的裝置或新增裝置。\)
    * 如果您沒有任何裝置，橫幅會顯示：**您沒有任何受控裝置。Add this one by tapping here. \(您沒有任何受控裝置。請點選這裡新增這部裝置。\) 按一下橫幅以新增您的裝置。  

     ![[裝置] 頁面的螢幕擷取畫面，含有圍住橫幅選項的紅色方框以醒目提示要按下的位置。](./media/CP-enroll-MACOS-1808.png)  
5.  完成符合您目前在公司入口網站中看到訊息的下列步驟。  
    * 如果是第一次新增裝置，系統會提示您將公司入口網站應用程式下載到裝置。 按一下 [下載] 繼續。  

         ![下載 macOS 公司入口網站應用程式提示畫面的範例螢幕擷取畫面。 使用者可以選擇按一下提示畫面左下方的藍色 [下載] 按鈕，或右下方的灰色 [取消] 按鈕。](./media/CP-enroll-download-macOS-1808.png)  

    * 如果您已有受控 macOS 裝置，您會收到目前受控 macOS 裝置清單的提示。 選取 [My device isn't listed here] \(我的裝置未列於此處\) > [下載]，將公司入口網站應用程式下載到您要新增的裝置。  

         ![下載 macOS 公司入口網站應用程式提示畫面的範例螢幕擷取畫面。 使用者可以選擇選取 [My device isn't listed here] \(我的裝置未列於此處\)，或頁面中間的特定裝置。 提示畫面左下方會顯示藍色 [下載] 按鈕，右下方會顯示灰色 [取消] 按鈕](./media/cp-mac-os-device-isnt-here-1808.png)  

6. 您的裝置將確認可安全地開啟安裝檔案 **CompanyPortal.pkg**。 完成之後，請開啟安裝程式並完成安裝。  

7. 安裝程式完成後，移至 [啟動控制板]，然後開啟 [公司入口網站]。  

8. 您的 macOS 裝置會提示您確認是否要開啟公司入口網站應用程式。 按一下 [開啟]。  

   > [!TIP]
   > Intune 需要存取您的電腦，藉此確定您的裝置具備足夠的安全性可存取您組織的資源。 如果您的電腦拒絕開啟公司入口網站應用程式，請[關閉閘道管理員](https://support.apple.com/HT202491)。 然後開啟應用程式。

9. 您在公司入口網站應用程式中看到的第一個畫面，會提示您 [登入]。 請使用您用來登入公司入口網站的相同公司或學校帳戶。

10. 公司入口網站會確認您的帳戶資訊，並顯示您的 [裝置註冊] 和 [裝置合規性] 狀態。 黃色三角形醒目提示您需要採取以保護學校或公司用 macOS 裝置的動作。 按一下 [開始] 開始註冊。 

11. 如果出現提示，請鍵入您電腦的登入資訊。  

註冊裝置管理可能需要幾分鐘的時間。 在此期間，您可以在裝置上執行其他事項。 完成公司存取設定之後，您會收到一則訊息，讓您知道已完成。  

## <a name="unverified-profiles"></a>未驗證的設定檔
當您檢視 macOS 裝置的已安裝行動裝置管理 (MDM) 設定檔時，有些設定檔可能會顯示 [未驗證] 狀態。 只要 [管理設定檔] 顯示 [已驗證] 狀態，您就不需要擔心。  

管理設定檔定義 MDM 通道連線。 只要管理設定檔經過驗證，透過該通道遞送至電腦的任何其他設定檔就會繼承管理設定檔的安全性特性。

此外，因為這些其他設定檔不需要個別驗證，所以可以更快速地產生和遞送至裝置。 

## <a name="updating-the-company-portal-app"></a>更新公司入口網站應用程式

更新公司入口網站應用程式的完成方式與任何其他 Office 應用程式一樣，都是透過 Microsoft AutoUpdate for Mac。 深入了解[更新 macOS 版的 Microsoft 應用程式](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1)。  

## <a name="next-steps"></a>後續步驟  
需要其他協助嗎？ 請向公司支援人員確認。 您可以在[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)中找到他們的連絡資訊。  


