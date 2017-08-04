---
title: "開始使用註冊裝置"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b595848d-c451-43ab-812d-b22e0170fb7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7f52c9d44a91ed6547aadd712db42ea68cfd01dc
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2017
---
# <a name="getting-started-enrolling-devices"></a>開始使用註冊裝置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune 可協助您提供行動裝置給您的工作人員，同時保護公司資料。 因為您的終端使用者會與 Intune 在其裝置上互動，而不是在管理主控台互動，所以請確定您的註冊體驗流暢。 如此一來，您可以結合精巧的合規性原則與體驗，展現對使用者的同理心。 這點尤其重要，因為您的使用者將會知道身為系統管理員的您究竟可以看到哪些資訊：

## <a name="what-it-cannot-see"></a>IT 看不到的內容
* 電話和 Web 瀏覽歷程記錄
* 位置
* 個人電子郵件
* 簡訊
* 連絡人
* 您的個人帳戶密碼
* 行事曆事件
* 圖片，包括相片應用程式或手機相簿的內容

## <a name="what-it-can-see"></a>IT 可以看到的內容
* 型號
* 序號
* 作業系統版本
* 應用程式名稱
* Owner
* 裝置名稱
* 製造商 (適用於非 Apple 製造的裝置)
* 電話號碼 (若為公司的裝置，則為完整號碼。 若為個人裝置，則僅為末四碼)。

## <a name="how-do-i-enroll-a-device"></a>如何註冊裝置？

註冊裝置是許多終端使用者在存取公司資源時會有的第一項體驗。 [了解該體驗](end-user-educate.md)可協助讓可能不愉快的體驗變得較好。

1. 開啟 **App Store**，搜尋 **Intune 公司入口網站**。
2. 下載 [Microsoft Intune 公司入口網站] 應用程式。
3. 開啟公司入口網站應用程式，輸入您的測試使用者電子郵件地址和密碼，然後點選 [登入]。
4. 將暫時密碼更新為新的密碼。
5. 在 [公司存取設定] 頁面上，點選 [裝置註冊]。
6. 在 [為什麼要註冊您的裝置?] 頁面上，閱讀有關使用者註冊裝置時可執行的作業，然後點選 [繼續]。
7. 檢閱使用者註冊時會取得哪些存取權限的清單，然後點選 [繼續]。
8. 檢閱 IT 系統管理員在裝置上可以和不可以看到的內容，然後點選 [繼續]。
9. 在 [接下來要做什麼] 頁面上，閱讀有關註冊期間所發生的事況，然後點選 [註冊]。
10. 在 [安裝設定檔] 頁面上，點選 [安裝]，然後在出現提示時輸入裝置密碼。
11. 點選 [安裝]。
12. 再次點選 [安裝] 表示您已閱讀警告。
13. 在 [警告] 快顯視窗中，點選 [信任]。
14. 畫面變更成顯示設定檔已完成安裝時，請點選 [完成]。
15. 畫面上會顯示「註冊裝置」訊息，然後顯示已成功註冊裝置。 會出現快顯視窗，詢問是否在公司入口網站中開啟頁面。 點選 [開啟]。
16. 您會回到 [公司存取設定] 畫面。 如果您未設定任何測試原則，那麼裝置應該會顯示為符合規範。 如果您有任何測試原則，則點選 [裝置合規性] 會顯示需要完成的事項，以確保裝置安全。
