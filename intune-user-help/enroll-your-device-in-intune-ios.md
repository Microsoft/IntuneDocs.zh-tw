---
title: "設定對您公司資源的存取 | Microsoft Docs"
description: "描述如何讓 Intune 管理您的 iOS 裝置"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope: User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 206de56ee967f4cd142e5cd7c9d63971b9b727c6
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="set-up-access-to-your-company-resources"></a>設定對您公司資源的存取

貴公司有許多的專屬資訊，從電子郵件到檔案、網路等等。 當您從 iOS 裝置存取資訊時，貴公司會使用 Microsoft Intune 來協助保護該資訊。 這可讓他們管理這些資源，讓它們更安全，同時讓您自由地使用您慣用的裝置來完成工作。

> [!VIDEO https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment/player]

> [!NOTE]
> 若您嘗試在「郵件」應用程式中存取公司的電子郵件，可能會出現提示要管理您的裝置以確保安全。 請遵循以下指示，在 iOS 裝置上存取電子郵件以及其他公司資源。

## <a name="before-you-start"></a>開始之前

- 請確定您一開始就完成整個程序。 暫停超過幾分鐘時，通常會停止此程序，並要求您重新開始。
- 如果此程序失敗，您需要返回公司入口網站應用程式重試。
- 請確定您的 Wi-Fi 運作正常，而且您裝置上的 Safari 運作正常。
- 下載並安裝 [Intune 公司入口網站應用程式](install-and-sign-in-to-the-intune-company-portal-app-ios.md)。


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>使用公司入口網站應用程式設定公司資源的存取權

|您所看到的內容|說明|
|---|---|
|![公司入口網站登入畫面，底部有 [登入] 按鈕。](./media/ios-0-cp-enroll-1711.png)|開啟公司入口網站應用程式，然後點選 [登入]。|
|![Azure AD 登入提示。](./media/ios-0a-cp-enroll-1711.png)|輸入您的公司電子郵件地址，然後點選 [下一步]。|
|![Azure AD 密碼提示。](./media/ios-0b-cp-enroll-1711.png)|輸入您的密碼，然後點選 [登入]。|
|![正在載入公司資源啟動顯示畫面。](./media/ios-1-cp-enroll-1711.png)|等候載入。|
|![條款及條件。](./media/ios-2-cp-enroll-1711.png)|閱讀並接受所有條款及條件。|
|![設定公司存取畫面。 管理和設定目前都需要解決。](./media/ios-3-cp-enroll-1711.png)|點選 [開始] 以開始執行讓您的裝置能夠存取公司資源的程序。 如果您無法立刻執行此作業，則可以**延遲**程序，但這表示您將無法取得電子郵件、文件等。|
|![我的公司能看到什麼畫面。](./media/ios-4-cp-enroll-1711.png)|您可以透過點選底部的連結來**深入了解**您的公司能看到什麼相關資訊。 否則，請點選 [繼續]。|
|![下一步是什麼畫面。](./media/ios-5-cp-enroll-1711.png)|此畫面會引導您了解安裝程式中的情況。 您將花費時間在 Safari、[設定] 應用程式與 [公司入口網站] 應用程式來完成此程序。 點選 [下一步]。|
|![點選 [下一步是什麼] 上的 [下一步] 之後正在載入畫面。](./media/ios-6-cp-enroll-1711.png)||
|![切換到 Safari 進行註冊。](./media/ios-7-cp-enroll-1711.png)|您會被傳送到 Safari 以取得您的裝置的管理資訊。|
|![系統提示要求開啟 [設定] 應用程式。](./media/ios-8-cp-enroll-1711.png)|點選 [允許] 開啟 [設定] 應用程式以下載組態設定檔。 安裝組態設定檔，讓您的公司管理您裝置上的公司資訊。|
|![設定檔在設定中開啟。](./media/ios-9-cp-enroll-1711.png)|點選 [安裝]。|
|![畫面底部的安裝設定檔強制回應對話方塊。](./media/ios-10-cp-enroll-1711.png)|點選 [安裝]。|
|![設定檔正在安裝載入畫面。](./media/ios-11-cp-enroll-1711.png)|等候載入。|
|![設定檔管理警告畫面。](./media/ios-12-cp-enroll-1711.png)|這個由 Apple 撰寫的警告，讓您可以深入了解在受管理的裝置上，可以採取哪些類型的動作。 深入了解[貴公司可以看到哪些資訊](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)|
|![系統提示詢問對遠端管理的信任。](./media/ios-13-cp-enroll-1711.png)|點選 [信任]，讓您的公司管理您裝置上的公司資訊和設定。|
|![設定檔完成安裝載入畫面。](./media/ios-14-cp-enroll-1711.png)|等候載入。|
|![已安裝設定檔畫面。](./media/ios-15-cp-enroll-1711.png)|您的設定檔已安裝，且您的裝置的公司資訊和設定離受管理更近一步。|
|![切換到 Safari 進行註冊。](./media/ios-16-cp-enroll-1711.png)|您會被傳送回 Safari 以完成取得您裝置的管理資訊。 |
|![系統提示開啟公司入口網站。](./media/ios-17-cp-enroll-1711.png)|點選 [開啟]。|
|![正在載入公司資源畫面。](./media/ios-18-cp-enroll-1711.png)|等候載入。|
|![在公司入口網站應用程式中選取裝置類別。](./media/ios-19-cp-enroll-1711.png)|為您的裝置選取最適合的類別。 這通常與誰擁有該裝置，或大部分時間裝置位於何處有關。|
|![已選取類別。](./media/ios-20-cp-enroll-1711.png)||
|![裝置管理成功；現在需要更新設定。](./media/ios-21-cp-enroll-1711.png)|您已成功讓您的裝置受到管理。 您的公司可能還有需要您更新的設定，例如密碼的長度。 按一下 [繼續] 以繼續執行。|
|![確認裝置設定。](./media/ios-22-cp-enroll-1711.png)|「公司入口網站」將檢查是否有任何設定需要更新。|
|![設定檢查完成，具有不正確的 OS 版本](./media/ios-23-cp-enroll-1711.png)|「公司入口網站」將提供有關如何修正設定問題的指示。 修復問題後，點選 [檢查設定]。|
|![確認裝置設定載入畫面](./media/ios-24-cp-enroll-1711.png)|您的裝置將檢查您的設定是否足夠安全地存取公司資源。|
|![已成功註冊和更新設定](./media/ios-25-cp-enroll-1711.png)|恭喜！ 您的裝置現在已在 Intune 註冊。|

> [!Note]
> 在完全管理您的裝置之前，還有幾個步驟需要完成。 請深入了解[使用電信費用管理註冊您的裝置](enroll-your-device-with-telecom-expense-management-ios.md)。 如果您的組織使用 Apple 裝置註冊方案，請在[這裡](enroll-your-device-dep-ios.md)取得詳細資訊。

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://portal.manage.microsoft.com)。
