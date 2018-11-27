---
title: 對 Microsoft Intune 中的原則進行疑難排解 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中使用原則時的常見問題和解決方式
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: bb55ddc283ce4633b5057d5b96ae2ed6973dcf8a
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181763"
---
# <a name="troubleshoot-policies-in-intune"></a>在 Intune 中對原則進行疑難排解

如果您有部署和管理 Intune 原則上的問題，請從這裡開始。 本文會描述您可能會遇到的一些常見問題，以及可能的解決方案。

## <a name="general-issues"></a>一般問題

### <a name="was-a-deployed-policy-applied-to-the-device"></a>部署原則是否已套用到裝置？
**問題：** 您不確定是否已正確套用某個原則。

在 Intune 中 > [裝置] > [所有裝置] > 選取裝置 > [裝置設定]，每個裝置都會列出其原則。 每個原則都有 [狀態]。 狀態是將套用到裝置的所有原則 (包括硬體和作業系統的限制與需求) 全部一起考慮時所達成的情況。 可能的狀態包括：

- **符合**：裝置已收到原則，並對服務回報其符合設定。

- **不適用**：該原則設定不適用。 例如，iOS 裝置的電子郵件設定不會套用至 Android 裝置。

- **擱置**：原則已傳送至裝置，但尚未對服務回報狀態。 例如，Android 上的加密需要使用者啟用加密，因此可能顯示為擱置。

> [!NOTE]
> 當兩個不同限制等級的原則套用至同一部裝置或同一個使用者時，系統會套用較嚴格的原則。

## <a name="issues-with-enrolled-devices"></a>已註冊裝置的問題

### <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>警示：將存取規則儲存到 Exchange 失敗
**問題：** 您在管理主控台中收到警示「將存取規則儲存到 Exchange 失敗」   。

如果您在管理主控台下的 [Exchange 內部部署原則] 工作區中建立原則，但使用 O365，則 Intune 將不會強制執行已設定的原則設定。 記下警示中的原則來源。  在 [Exchange 內部部署原則] 工作區下，刪除舊版規則。 舊版規則是 Intune 內適用於內部部署 Exchange 的全域 Exchange 規則，並與 O365 不相關。 接著，建立適用於 O365 的新原則。

### <a name="cannot-change-security-policy-for-various-enrolled-devices"></a>無法變更各種已註冊裝置的安全性原則
當您透過 MDM 或 EAS 設定安全性原則之後，Windows Phone 裝置不允許降低這些原則的安全性。 例如，您將 [字元密碼數目下限]  設定為 8，然後嘗試減少為 4。 此裝置已套用較嚴格的原則。

根據裝置平台，如果您想要將原則變更為較不安全的值，您可能需要重設安全性原則。

例如，在 Windows 中的桌面上，從右向內撥動以開啟 [常用鍵] 列。 選擇 [設定] > [控制台]，然後選取 [使用者帳戶]。 在左側，選取 [重設安全性原則] 連結，然後選擇 [重設原則]。

其他 MDM 裝置 (例如 Android、Windows Phone 8.1 及更新版本，以及 iOS) 可能需要先被淘汰，然後再重新註冊到服務中，以套用較不嚴格的原則。

## <a name="issues-with-pcs-that-run-the-intune-software-client"></a>執行 Intune 軟體用戶端之電腦的問題

適用於傳統型入口網站。

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Microsoft Intune policyplatform.log 中的原則相關錯誤
針對使用 Intune 軟體用戶端管理的 Windows 電腦，policyplatform.log 檔案中的原則錯誤可能是因為裝置上 Windows 使用者帳戶控制 (UAC) 的非預設設定所造成。 某些非預設的 UAC 設定可能會影響 Microsoft Intune 用戶端安裝和原則執行。

#### <a name="resolve-uac-issues"></a>解決 UAC 問題

1. 將電腦淘汰。 請參閱[移除裝置](devices-wipe.md)。

2. 等候 20 分鐘讓用戶端軟體被移除。

    > [!NOTE]
    > 請勿嘗試從 [程式和功能] 移除用戶端。

3. 在 [開始] 功能表中輸入 **UAC**，開啟 [使用者帳戶控制] 設定。

4. 將通知滑桿移至預設設定。

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>錯誤：無法從電腦取得值，0x80041013
在本機系統時間不同步的程度超過五分鐘以上時便會發生。 如果本機電腦上的時間不同步，因為時間戳記無效，安全交易會失敗。

若要解決這個問題，設定本機系統時間時請盡可能接近網際網路時間，或接近網路上網域控制站的設定時間。

### <a name="next-steps"></a>接下來的步驟
如果此疑難排解資訊對您沒有幫助，請連絡 Microsoft 支援服務 (如[取得 Microsoft Intune 支援](get-support.md)中所述)。
