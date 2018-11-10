---
title: 在 Intune 中放棄註冊公司入口網站
titlesuffix: Microsoft Intune
description: 了解公司入口網站放棄報告。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: ba1ee5a6811457b8c6e7343de7355261a2fcecdb
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236743"
---
# <a name="company-portal-abandonment-report"></a>公司入口網站放棄報告

此報告會告訴您，使用者在公司入口網站註冊的哪個地方放棄註冊程序。

若要查看報告，請選擇 [Intune] > [裝置註冊] > [公司入口網站的放棄]。

您可以利用此放棄資訊來更新上線文件，以協助使用者完成註冊。 例如，如果許多使用者在使用條款處放棄，您可以調查該區域，並讓使用者更容易了解。

## <a name="what-is-abandonment"></a>什麼是放棄？

當使用者執行下列任何動作時，即視為放棄：

-   明確選擇終止註冊的動作
-   在註冊期間關閉公司入口網站
-   在註冊區段之間花費超過 30 分鐘

如果使用者選擇停止註冊並重新啟動多次，則會顯示為多次嘗試和多次放棄。 如果使用者在不同的註冊畫面之間等候 30 分鐘，則會視為多次放棄。

## <a name="what-does-the-report-show"></a>報告會顯示哪些內容？

註冊報告包含 iOS 和 Android 裝置的資料。

報告顯示過去兩週的資料，但您可以篩選報告以顯示最多為過去 30 天的任何期間。

您可以選擇 [篩選] 來篩選日期範圍、作業系統和註冊區段。

### <a name="number-and-percentage-tiles"></a>數目和百分比磚

在報告頂端，您可以看到放棄的報告數目和百分比 (相對於所有註冊)。

-   起始的註冊：嘗試的註冊數目。
-   放棄的註冊：已嘗試但未能產生完整註冊且符合規範裝置的註冊數目。
-   放棄率：嘗試但放棄的註冊百分比 (放棄的註冊/起始的註冊)。

### <a name="line-graph"></a>折線圖

折線圖會顯示四個核心註冊區段各自的每日放棄數目：

-   安裝程式檢查清單
-   平台畫面
-   使用條款
-   合規性/啟用

### <a name="user-abandonment-actions"></a>使用者放棄動作

下表顯示符合放棄資格的使用者動作清單。 若要查看註冊畫面範例，您可以觀看 [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment) 和 [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment) 註冊影片。 


#### <a name="setup-checklist-section"></a>安裝程式檢查清單區段

| 放棄名稱 | 畫面或流程 | 平台 | 動作 |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | 提示在公司入口網站中開啟頁面 | iOS/Android | **取消** |
| EnrollmentWrapUp | 註冊裝置畫面，直到完成**載入公司資源** | iOS/Android | 需要 > 30 分鐘 |
| DeviceCategory | 裝置類別選取 (如果管理員已設定)，直到按一下 [完成] | iOS/Android | 需要 > 30 分鐘 |
| PreEnrollmentWizard | 設定存取畫面 (若已啟動註冊但返回至設定存取) | iOS/Android| **延期** |
| PreEnrollmentWizard | 設定存取畫面，直到按一下 [下一步是什麼] 畫面上的 [下一步] | iOS/Android | 需要 > 30 分鐘 |

#### <a name="platform-screens-section"></a>平台畫面區段

| 放棄名稱 | 畫面或流程 | 平台 | 動作 |
| ---- |---- |---- |---- |
| iOSProfileLaunch | 提示顯示組態設定檔 | iOS | **忽略** |
| iOSProfileLaunch | 安裝設定檔畫面 | iOS | **取消** |
| iOSProfileLaunch | 提示信任設定檔來源註冊裝置 | iOS | **取消** |
| iOSProfileLaunch | 安裝設定檔畫面，直到設定檔安裝完成 | iOS | 需要 > 30 分鐘 |
| AndroidPermissions | 裝置管理員啟用畫面 | Android | **取消** |
| AndroidPermissions | 從提示核准撥打電話及管理通話，直到裝置管理員**啟用** | Android | 需要 > 30 分鐘 |
| KnoxActivation | KLMS 代理程式啟用 (僅限 Samsung) | Android| **取消** |
| KnoxActivation | KLMS 代理程式啟用，直到**確認** | Android | 需要 > 30 分鐘|

#### <a name="terms-of-use-section"></a>使用條款區段

| 放棄名稱 | 畫面或流程 | 平台 | 動作 |
| ---- |---- |---- |---- |
| TermsofUse | 使用條款 (如果管理員已設定) | iOS/Android | **全部拒絕** |
| TermsofUse | 使用條款，直到**全部接受** | iOS/Android | 需要 > 30 分鐘 |

#### <a name="complianceactivation-section"></a>合規性/啟用區段

| 放棄名稱 | 畫面或流程 | 平台 | 動作 |
| ---- |---- |---- |---- |
| 合規性 | 裝置合規性 (如果管理員已設定) 會在註冊後的存取設定上顯示為非綠色| iOS/Android | **延期** |
| 合規性 | 裝置合規性會顯示為非綠色，直到更新為顯示綠色 | iOS/Android | 需要 > 30 分鐘 |
| 啟用 | 註冊啟用 (如果管理員已設定) 會在存取設定上顯示為非綠色 | iOS/Android | **延期** |
| 合規性 | 裝置啟用會顯示為非綠色，直到更新為顯示綠色 | iOS/Android | 需要 > 30 分鐘 |

## <a name="next-steps"></a>接下來的步驟

檢查放棄率之後，您可以檢閱[註冊選項](enrollment-options.md)，了解是否可以進行任何變更來改善註冊。