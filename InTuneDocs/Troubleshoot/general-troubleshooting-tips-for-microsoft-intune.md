---
title: "一般疑難排解提示 | Microsoft Intune"
description: 
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 05/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79617dd41e51402a73759da792f581028095a2f5
ms.openlocfilehash: 6b2d1d5eecb543e45fca5fbb8aa1854c88ec4f9c


---

# Microsoft Intune 的一般疑難排解提示
部署 Microsoft Intune 之後，設定或用戶端可能會發生問題。 下列資源可以協助您找出問題的原因，以便您解決問題。

> [!NOTE]
> 若要建立支援要求，或檢視現有的要求，請[瀏覽 Office 365 系統管理中心](https://portal.office.com/admin/default.aspx)。 如需支援選項的詳細資訊，請參閱[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)。
## 定義問題

-   什麼是行為？

-   什麼人在什麼樣的平台和裝置上會發生這種行為？

-   裝置之前運作正常嗎？

-   您對 Intune 或裝置設定進行過什麼變更？

-   請想想是否曾對操作環境進行過設定變更以外的其他變更。

-   這個問題發生的頻率如何，是斷斷續續還是一直出現？

-   使用者是否可能發生驗證問題？ 如有這個可能性，請檢查使用者可否登入使用 Azure Active Directory 的其他服務。 亦請檢查使用者可否從其他裝置登入。

-   是否已檢查服務狀態？ 您可以在 [Office 365 管理入口網站](https://portal.office.com/Admin/Default.aspx)中監視 Intune 服務健全狀況。 選擇左窗格中的 **[服務健全狀況]**。

## 收集可用資料

-   裝置記錄檔。 了解如何在下列位置收集裝置記錄檔︰
  - [使用 USB 纜線將 Android 診斷資料記錄檔傳送給 IT 系統管理員](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [使用電子郵件將 Android 診斷資料記錄檔傳送給 IT 系統管理員](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [將 Android 註冊錯誤傳送給 IT 系統管理員](/intune/enduser/send-enrollment-errors-to-your-it-administrator-android)
  - [將 iOS 註冊錯誤傳送給 IT 系統管理員](/intune/enduser/send-errors-to-your-it-admin-ios)

-   例如，處理原則實作問題需要的管理主控台資料，您應該檢查預期的原則及該原則的狀態，如[利用 Microsoft Intune，使用群組管理使用者和裝置](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune)中所述。

## 研究解決方案

-   搜尋網站上的解決方案。 例如，如果您收到錯誤 0x80073CF0，則可以在網路上搜尋 **technet intune 0x80073cf0**，並尋找 [Microsoft Intune 的應用程式部署問題疑難排解](troubleshoot-app-deployment-problems-in-microsoft-intune.md)一文，取得解決這個問題的建議。

-   您可以在 [Intune TechNet 論壇](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod) 中搜尋解答。  如果這不是已解決的問題，您應該提問，求教於社群。

-   您可以提出支援要求。 如果您定義了問題並收集到可取得的資料，Intune 支援中心會比較容易幫助您解決問題。

    若要建立支援要求，請[瀏覽 Office 365 系統管理中心](https://portal.office.com/admin/default.aspx)。 如需支援選項的詳細資訊，請參閱[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)。

## 社群資源
您可以在這些社群資源中尋找其他實用資訊：

-   [Microsoft Intune 求生指南](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx)包含可協助您對 Intune 進行設定、維護和疑難排解的多項資源連結。

-   [Intune 部落格](http://blogs.technet.com/b/windowsintune/)

-   [在 Twitter 上關注 Intune](https://twitter.com/MSIntune)

-   [Intune 論壇](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

### 後續步驟
下面所列的主題都有特定問題的疑難排解說明。 如果該資訊對您沒有幫助，請連絡 Microsoft 支援服務 (如[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)中所述)。

[Troubleshoot Endpoint Protection in Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[使用 Microsoft Intune 的公司資源存取問題疑難排解](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[Microsoft Intune 的應用程式部署問題疑難排解](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[Intune 的裝置註冊疑難排解](troubleshoot-device-enrollment-in-intune.md)

[Microsoft Intune 的原則疑難排解](troubleshoot-policies-in-microsoft-intune.md)

[Microsoft Intune 的用戶端設定疑難排解](troubleshoot-client-setup-in-microsoft-intune.md)

[Microsoft Intune 的軟體更新疑難排解](troubleshoot-software-updates-in-microsoft-intune.md)



<!--HONumber=Jul16_HO1-->


