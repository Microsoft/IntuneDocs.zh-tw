---
title: 一般疑難排解提示
description: 有助於解決 Intune 問題的一般資源。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/08/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d5d55f6c3efabdde51b5627d5ddd409c2b282f6c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="general-troubleshooting-tips-for-microsoft-intune"></a>Microsoft Intune 的一般疑難排解提示

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

部署 Microsoft Intune 之後，您的設定或用戶端裝置可能會發生問題。 請使用下列資源協助您找出問題的原因，以便您解決問題。

> [!NOTE]
> 若要建立支援要求，或檢視現有的要求，請[瀏覽 Office 365 系統管理中心](https://portal.office.com/admin/default.aspx)。 如需支援選項的詳細資訊，請參閱[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)。

## <a name="define-the-problem"></a>定義問題

-   什麼是行為？

-   什麼人在什麼樣的平台和裝置上會發生這種行為？

-   裝置之前運作正常嗎？

-   您對 Intune 或裝置設定進行過什麼變更？

-   是否曾對操作環境進行過設定變更以外的其他變更？

-   這個問題發生的頻率如何，是斷斷續續還是一直出現？

-   使用者是否可能發生驗證問題？ 如有這個可能性，請查看使用者可否登入使用 Azure Active Directory 的其他服務。 亦請查看使用者可否從其他裝置登入。

-   是否已檢查服務狀態？ 您可以在 [Office 365 管理入口網站](https://portal.office.com/Admin/Default.aspx)中監視 Intune 服務健全狀況。 選擇左窗格中的 **[服務健全狀況]**。

## <a name="collect-available-data"></a>收集可用資料

- 下列資源可協助您了解如何收集裝置記錄：
  - [使用 USB 纜線將 Android 診斷資料記錄傳送給 IT 系統管理員](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [使用電子郵件將 Android 診斷資料記錄傳送給 IT 系統管理員](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [將 Android 註冊錯誤傳送給 IT 系統管理員](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)
  - [將 iOS 註冊錯誤傳送給 IT 系統管理員](/intune-user-help/send-errors-to-your-it-admin-ios)

- 例如，利用原則實作問題的管理主控台資料，檢查預期的原則及該原則的狀態，如[在 Microsoft Intune 中使用群組管理使用者和裝置](/intune-classic/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune)中所述。

## <a name="research-the-solution"></a>研究解決方案

-   搜尋網站上的解決方案。 例如，如果您收到錯誤 0x80073CF0，請在網路上搜尋 **technet intune 0x80073cf0**，您會找到 [Microsoft Intune 的應用程式部署問題疑難排解](troubleshoot-app-deployment-problems-in-microsoft-intune.md)一文。 此文章提供解決此問題的建議。

-   在 [Intune TechNet 論壇](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)中搜尋解答。  如果這不是已解決的問題，請張貼問題以查看社群可能提供的建議。

-   開立支援要求。 在您定義了問題並收集到可取得的資料之後，Intune 支援中心會比較容易協助您解決問題。

    若要建立支援要求，請[瀏覽 Office 365 系統管理中心](https://portal.office.com/admin/default.aspx)。 如需支援選項的詳細資訊，請參閱[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)。

## <a name="find-community-resources"></a>尋找社群資源
您可以在這些社群資源中尋找其他實用資訊：

-   [Microsoft Intune 求生指南](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx)包含可協助您對 Intune 進行設定、維護和疑難排解的多項資源連結。

-   [Intune 部落格](http://blogs.technet.com/b/windowsintune/)

-   [在 Twitter 上關注 Intune](https://twitter.com/MSIntune)

-   [Intune 論壇](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

### <a name="next-steps"></a>接下來的步驟
以下主題都有特定問題的疑難排解說明。 如果該資訊對您沒有幫助，請連絡 Microsoft 支援服務 (如[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)中所述)。

[使用 Microsoft Intune 疑難排解 Endpoint Protection 的問題](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[使用 Microsoft Intune 疑難排解公司資源的存取問題](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[使用 Microsoft Intune 疑難排解應用程式部署問題](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[疑難排解 Intune 的裝置註冊問題](troubleshoot-device-enrollment-in-intune.md)

[使用 Microsoft Intune 疑難排解原則的問題](troubleshoot-policies-in-microsoft-intune.md)

[使用 Microsoft Intune 疑難排解用戶端設定的問題](troubleshoot-client-setup-in-microsoft-intune.md)

[使用 Microsoft Intune 疑難排解軟體更新的問題](troubleshoot-software-updates-in-microsoft-intune.md)
