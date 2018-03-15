---
title: "了解 iOS 裝置註冊體驗"
titlesuffix: Microsoft Intune
description: "經由體驗完整的 iOS 裝置註冊，學習註冊。"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b595848d-c451-43ab-812d-b22e0170fb7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 18a3225ef81d7f13b8656326540e30cf5ee07f1e
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
---
# <a name="understand-the-users-experience-enrolling-an-ios-device"></a>了解使用者註冊 iOS 裝置的體驗

Microsoft Intune 可協助您的工作人員使用行動裝置，而於同時仍能保護公司的資料。 因為您的終端使用者會在其裝置上與 Intune 互動，而非在管理主控台中互動，所以請確定您的註冊體驗能流暢進行。 如此一來，您即可結合精細規劃的合規性原則與您的體驗，展現對使用者的同理心。 因為使用者完全了解身為系統管理員的您可以看到哪些資訊，所以這一點尤其重要：

| IT 看不到的內容 | IT 可以看到的內容 |
|---|---|
| 電話與網頁瀏覽歷程記錄 | 型號 |
| 位置 | 序號 |
| 個人電子郵件 | 作業系統版本 |
| 簡訊 | 應用程式名稱 |
| 連絡人 | 擁有者 |
| 您的個人帳戶密碼 | 裝置名稱 |
| 行事曆活動 | 製造商 (適用於非 Apple 裝置) |
| 圖片，包括相片應用程式或手機相簿的內容 | 電話號碼 (若為公司的裝置，為完整號碼。 若為個人裝置，則只有後四碼。) |

## <a name="how-do-i-enroll-a-device"></a>如何註冊裝置？

註冊裝置是許多終端使用者在存取公司資源時的第一項體驗。 [了解該體驗](end-user-educate.md)有助於讓可能不愉快的體驗變得較好。

1. 開啟 **App Store**，搜尋 **Intune 公司入口網站**。
2. 下載 [Microsoft Intune 公司入口網站] 應用程式。
3. 開啟**公司入口網站**應用程式，輸入您的測試使用者電子郵件地址和密碼，然後點選 [登入]。
4. 將暫時密碼更新為新的密碼。
5. 在 [公司存取設定] 頁面上，點選 [裝置註冊]。
6. 在 [為什麼要註冊您的裝置?] 頁面上，閱讀有關使用者註冊其裝置時可執行的作業，然後點選 [繼續]。
7. 檢閱使用者註冊時會取得哪些存取權限的清單，然後點選 [繼續]。
8. 檢閱 IT 系統管理員在裝置上可看見及無法看見的內容，然後點選 [繼續]。
9. 在 [接下來要做什麼] 頁面上，閱讀有關註冊期間所發生的情況，然後點選 [註冊]。
10. 在 [安裝設定檔] 頁面上，點選 [安裝]，然後在出現提示時輸入裝置密碼。
11. 點選 [安裝]。
12. 再次點選 [安裝]，表示您已閱讀過警告。
13. 在 [警告] 快顯視窗中，點選 [信任]。
14. 畫面變更為顯示設定檔已完成安裝時，點選 [完成]。
15. 畫面上隨即會出現「註冊裝置」訊息，然後顯示該裝置已成功註冊。 之後會出現快顯視窗，詢問您是否要在公司入口網站中開啟該頁面。 點選 [開啟]。
16. 您會回到 [公司存取設定] 畫面。 如果您未設定任何測試原則，裝置應會顯示為符合規範。 如果您有任何測試原則，則點選 [裝置合規性] 會顯示需要完成才可確保裝置安全的事項。

## <a name="next-steps"></a>後續步驟

[開始新增應用程式](get-started-apps.md) - 找到應用程式，並將其新增至裝置，讓您的員工可以完成工作。

## <a name="learn-more"></a>深入了解

* [Intune 註冊選項](enrollment-options.md)
* [使用 Intune 啟用攜帶您自己的裝置](byod-enable.md)
* [教育終端使用者有關註冊與裝置管理](end-user-educate.md)
