---
title: "在 Intune 註冊 iOS 裝置 | Microsoft Docs"
description: "描述在 Intune 註冊 iOS 裝置的方式"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 09/01/2017
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
ms.openlocfilehash: 41f39740b62074e06ccc64c6211d642d224efd6c
ms.sourcegitcommit: db7a7bbead3a3fa78c4d643607f709a2909eb608
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2017
---
# <a name="enroll-your-ios-device-in-intune"></a>在 Intune 註冊 iOS 裝置

如果您的公司或學校使用 Microsoft Intune，您可以註冊 iOS 裝置來存取公司電子郵件、檔案和其他資源。 當您註冊裝置時，您的 IT 部門可以管理這些公司或學校資源、保護它們的安全，並讓您能夠自由地使用慣用的裝置來完成工作。 若要深入了解註冊，請參閱[如果您安裝公司入口網站應用程式並在 Intune 註冊裝置時，會發生什麼情況？](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md)。

> [!VIDEO https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment/player]

> [!NOTE]
> 若您嘗試在「郵件」應用程式中存取公司的電子郵件，可能會出現提示要管理您的裝置以確保安全。 請遵循以下指示，在 iOS 裝置上存取電子郵件以及其他公司資源。

**開始之前：**

- 開始步驟之後，請務必完成註冊。 暫停超過幾分鐘時，通常會停止此程序，並要求您重新啟動。
- 如果您的註冊因為任何原因失敗，您必須返回公司入口網站應用程式再試一次。
- 確定您的 Wi-Fi 運作正常。 否則，註冊將會失敗。
- 如果您在裝置上封鎖 Safari，請將它解除封鎖。 在裝置註冊的過程中會使用 Safari。


**註冊 iOS 裝置：**

1.  遵循[安裝並登入 Intune 公司入口網站應用程式](install-and-sign-in-to-the-intune-company-portal-app-ios.md)中的步驟。

2. 在 [公司存取設定] 頁面上，點選 [開始]。

    ![ios-enroll-comp-access-setup-begin](./media/ios-enroll-1a-comp-access-setup.png)

3. 在 [為什麼要註冊您的裝置?] 畫面上，閱讀有關註冊您的裝置時可執行的作業，然後點選 [繼續]。

    ![ios-enroll-why-enroll](./media/ios-enroll-1b-why-enroll.png)

  > [!NOTE]
  > 黃色三角形並不代表您遇到錯誤。 這些圖示表示註冊程序仍有步驟要完成。

4. 檢閱公司支援人員在您已註冊裝置上可看到和不可看到的項目清單，然後點選 [繼續]。

    ![ios-enroll-what-it-can-see](./media/ios-enroll-1c-we-care-privacy.png)

5.  在 [接下來該做什麼] 畫面上，閱讀有關註冊期間所發生的事況，然後點選 [註冊]。

    ![ios-enroll-what-comes-next](./media/ios-enroll-1d-what-comes-next.png)

6.  在 [安裝設定檔] 畫面上，點選 [安裝]，然後在出現提示時輸入您的密碼。

    ![ios-enroll-install-profile](./media/ios-enroll-2-mgt-profile-install.png)

7.  點選 [安裝]。

    ![ios-enroll-tap-install](./media/ios-enroll-3-mgt-profile-install-2.png)    

8.  點選 [安裝] 表示您已閱讀警告。

    ![ios-enroll-tap-install-after-warning](./media/ios-enroll-4-warning.png)

9.  點選 [信任]。

    ![ios-enroll-tap-trust](./media/ios-enroll-5-trust.png)

10.  畫面變更成顯示設定檔已完成安裝時，請點選 [完成]。

    ![ios-enroll-tap-done](./media/ios-enroll-6-done.png)

    畫面上會顯示 [正在註冊裝置] 訊息。

11.  當訊息詢問您是否要在公司入口網站中開啟頁面時，請點選 [開啟]。

    ![ios-enroll-open-comp-portal](./media/ios-enroll-7-open-cp.png)

12. 在 [公司存取設定] 畫面上，點選 [繼續]。 這個畫面會顯示有哪些您必須完成以使裝置符合標準的其他需求，如設定密碼。 遵循畫面上的指示，直到您符合所有的合規性需求為止。 完成之後，您會回到 [公司存取設定] 畫面。 點選 [繼續]。

    ![ios-enroll-comp-access-tap-continue](./media/ios-enroll-8-comp-access-setup-compliance.png)

13. 點選 [完成]。

    ![ios-enroll-tap-done](./media/ios-enroll-9-comp-access-setup-complete.png)

您的裝置現在已註冊在 Intune 中，而且會將您帶回公司入口網站應用程式。

> [!Note]
> 在完全註冊您的裝置之前，還有幾個步驟需要完成。 請深入了解[使用電信費用管理註冊您的裝置](enroll-your-device-with-telecom-expense-management-ios.md)。 如果您的組織使用 Apple 裝置註冊方案，請在[這裡](enroll-your-device-dep-ios.md)取得詳細資訊。

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://portal.manage.microsoft.com)。
