---
title: 設定 iOS 裝置對您公司資源的存取 | Microsoft Docs
description: 描述如何讓 Intune 管理您的 iOS 裝置
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 50fc19410b280e984c8dc3abe620baad7c3267de
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959531"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>設定 iOS 裝置對公司資源的存取

使用 Intune 公司入口網站應用程式註冊您的 iOS 裝置，以安全地存取您組織的電子郵件、檔案和應用程式。

您需要先管理裝置，才能從公司或個人裝置存取專有資料。 裝置成為受控之後，組織可以透過其行動裝置管理 (MDM) 提供者將原則和應用程式指派給裝置。 

若要維護從您的裝置存取公司或學校資訊，您必須設定裝置以符合組織的偏好設定。 本文描述公司入口網站如何協助您註冊、設定和維護裝置，以符合這些需求。

> [!NOTE]
> 如果您已嘗試在郵件應用程式中存取公司電子郵件，並且收到提示讓您管理裝置，則您位於正確位置。 請遵循以下指示，在 iOS 裝置上存取電子郵件以及其他公司資源。

## <a name="what-to-expect-from-the-company-portal-app"></a>公司入口網站應用程式的預期行為

### <a name="security"></a>安全性
在初始設定期間，應用程式需要您向組織自我驗證。 應用程式接著會通知您必須更新的任何裝置設定。 例如，組織通常會設定您必須符合的密碼字元數下限或上限需求。    

### <a name="protection"></a>保護
註冊裝置之後，公司入口網站應用程式會繼續確保您的裝置受到保護。 例如，如果您從未受信任的來源安裝應用程式，應用程式會提醒您有時會撤銷公司資料的存取權。 這類應用程式保護原則在組織中十分常見。 它們通常需要您先解除安裝未受信任的應用程式，才能重新取得存取。

### <a name="setting-notifications"></a>設定通知
如果在註冊之後，您的組織強制執行新的安全性需求 (例如多重要素驗證)，公司入口網站應用程式會通知您。 您將有機會調整設定，以便繼續在裝置上工作。  

若要深入了解註冊，請參閱[當我安裝公司入口網站應用程式並註冊我的裝置時，會發生什麼情況？](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios) 

## <a name="before-you-start"></a>開始之前

- 開始註冊之後，請務必完成整個程序。 如果您暫停超過幾分鐘，設定可能會結束，並要求您重新開始。  
- 如果此程序失敗，請返回公司入口網站應用程式並再試一次。  
- 請檢查您的 Wi-Fi 運作正常，而且您裝置上的 Safari 運作正常。
- 下載並安裝 [Intune 公司入口網站應用程式](install-and-sign-in-to-the-intune-company-portal-app-ios.md)。  


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>使用公司入口網站應用程式設定公司資源的存取權

|您所看到的內容|說明|
|---|---|
|![公司入口網站登入畫面，底部有 [登入] 按鈕。](./media/ios-01-cp-enroll-1802.PNG)|開啟公司入口網站應用程式，然後點選 [登入]。|
|![Azure AD 登入提示。](./media/ios-02-cp-enroll-1802.PNG)|輸入您的公司電子郵件地址，然後點選 [下一步]。|
|![Azure AD 密碼提示。](./media/ios-03-cp-enroll-1802.PNG)|輸入您的密碼，然後點選 [登入]。|
|![正在載入公司資源啟動顯示畫面。](./media/ios-04-cp-enroll-1802.PNG)|等候此畫面載入。|
|![條款及條件頁面。](./media/ios-05-cp-enroll-1802.PNG)|閱讀並接受所有條款及條件。|
|![設定公司存取畫面。 管理和設定目前都需要解決。](./media/ios-06-cp-enroll-1802.PNG)|點選 [開始] 以開始執行讓您的裝置能夠存取公司資源的程序。 如果您無法立刻執行此作業，則可以**延遲**程序，但這表示您將無法取得電子郵件、文件等。|
|![我的公司能看到什麼畫面。](./media/ios-07-cp-enroll-1802.PNG)|您可以透過點選底部的連結來**深入了解**您的公司能看到什麼相關資訊。 否則，請點選 [繼續]。|
|![下一步是什麼畫面。](./media/ios-08-cp-enroll-1802.PNG)|此畫面會引導您了解安裝程式中的情況。 您將花費時間在 Safari、[設定] 應用程式和公司入口網站應用程式。 點選 [繼續]。|
|![點選 [下一步是什麼] 上的 [下一步] 之後正在載入畫面。](./media/ios-09-cp-enroll-1802.PNG)|等候此畫面載入。|
|![切換到 Safari 進行註冊。](./media/ios-cp-sent-to-safari-1808.png)|您會被傳送到 Safari 以取得您的裝置的管理資訊。|
|![系統提示要求開啟 [設定] 應用程式。](./media/ios-8-cp-enroll-1711.PNG)|點選 [允許] 開啟 [設定] 應用程式以下載組態設定檔。 安裝組態設定檔，讓您的公司管理您裝置上的公司資訊。|
|![裝置設定中 [安裝設定檔] 畫面的螢幕擷取畫面。](./media/ios-9-cp-enroll-1711.PNG)|點選 [安裝]。|
|![畫面底部的安裝設定檔強制回應對話方塊。](./media/ios-10-cp-enroll-1711.PNG)|點選 [安裝]。|
|![設定檔正在安裝載入畫面。](./media/ios-11-cp-enroll-1711.PNG)|等候此畫面載入。|
|![設定檔管理警告畫面。](./media/ios-12-cp-enroll-1711.PNG)|這個由 Apple 撰寫的警告，讓您可以深入了解在受管理的裝置上，可以採取哪些類型的動作。 深入了解[貴公司可以看到哪些資訊](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)。|
|![系統提示詢問對遠端管理的信任。](./media/ios-13-cp-enroll-1711.PNG)|點選 [信任]，讓您的公司管理您裝置上的公司資訊和設定。|
|![設定檔完成安裝載入畫面。](./media/ios-14-cp-enroll-1711.PNG)|等候此畫面載入。|
|![已安裝設定檔畫面。](./media/ios-15-cp-enroll-1711.PNG)|您的設定檔已安裝，且您的裝置的公司資訊和設定離受管理更近一步。|
|![切換到 Safari 進行註冊。](./media/ios-16-cp-enroll-1711.PNG)|您會被傳送回 Safari 以完成取得您裝置的管理資訊。 |
|![系統提示開啟公司入口網站。](./media/ios-17-cp-enroll-1711.PNG)|點選 [開啟]。|
|![正在載入公司資源畫面。](./media/ios-21-cp-enroll-1802.PNG)|等候此畫面載入。|
|![在公司入口網站應用程式中選取裝置類別。](./media/ios-22-cp-enroll-1802.PNG)|為您的裝置選取最適合的類別。 這通常與誰擁有該裝置，或大部分時間裝置位於何處有關。|
|![已選取類別。](./media/ios-23-cp-enroll-1802.PNG)||
|![裝置管理成功；現在需要更新設定。](./media/ios-24-cp-enroll-1802.PNG)|您已成功讓您的裝置受到管理。 您的公司可能還有需要您更新的設定，例如密碼的長度。 按一下 [繼續] 以繼續執行。|
|![確認裝置設定。](./media/ios-25-cp-enroll-1802.PNG)|「公司入口網站」將檢查是否有任何設定需要更新。|
|![設定檢查完成，具有不正確的 OS 版本](./media/ios-26-cp-enroll-1802.PNG)|「公司入口網站」將提供有關如何修正設定問題的指示。 修復問題後，點選 [檢查設定]。|
|![確認裝置設定載入畫面](./media/ios-27-cp-enroll-1802.PNG)|您的裝置將檢查您的設定是否足夠安全地存取公司資源。|
|![已成功註冊和更新設定](./media/ios-28-cp-enroll-1802.PNG)|恭喜！ 您的裝置現在已在 Intune 註冊。|

> [!Note]
> 在完全管理您的裝置之前，還有幾個步驟需要完成。 請深入了解[使用電信費用管理註冊您的裝置](enroll-your-device-with-telecom-expense-management-ios.md)。 如果您的組織使用 Apple 裝置註冊方案，請在[這裡](enroll-your-device-dep-ios.md)取得詳細資訊。

是否仍需要協助？ 請向公司支援人員確認。 您可以在[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)中找到他們的連絡資訊。  
