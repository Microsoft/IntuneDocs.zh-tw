---
title: 對 Microsoft Intune 中的原則進行疑難排解 - Azure | Microsoft Docs
description: 了解如何使用內建的疑難排解功能，並閱讀有關在 Microsoft Intune 中使用合規性政策和組態設定檔時的常見問題及其解決方法
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/20/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68ffdcccdd3588ac5127e6c54426acfdcad17d34
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071714"
---
# <a name="troubleshoot-policies-and-profiles-and-in-intune"></a>針對 Intune 中的原則和設定檔進行疑難排解

Microsoft Intune 包含一些內建的疑難排解功能。 使用這些功能可協助您針對環境中的合規性政策和組態設定檔進行疑難排解。

本文列出一些常見的疑難排解技術，並描述您可能會遇到的一些問題。

## <a name="check-tenant-status"></a>檢查租使用者狀態
檢查[租使用者狀態](tenant-status.md)，並確認訂用帳戶為作用中。 您也可以查看可能會影響您的原則或設定檔部署之作用中事件和建議的詳細資料。

## <a name="use-built-in-troubleshooting"></a>使用內建的疑難排解

1. 在 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 中，選取 [疑難排解]  ：

    ![在 Intune 中，移至 [說明及支援]，然後選取 [疑難排解]](./media/help-and-support-troubleshoot.png)

2. 選擇 [選取使用者]  > 選取發生問題的使用者 > [選取]  。
3. 確認 [Intune 授權]  和 [帳戶狀態]  同時顯示綠色核取記號：

    ![在 Intune 中選取使用者，並確認 [帳戶狀態] 和 [Intune 授權] 顯示綠色核取記號狀態](./media/account-status-intune-license-show-green.png)

    **實用的連結**：

    - [指派授權，讓使用者可以註冊裝置](licenses-assign.md)
    - [將使用者新增至 Intune](users-add.md)

4. 在 [裝置]  下，尋找有問題的裝置。 檢閱不同欄位：

    - **受控**：若要讓裝置接收相容性或設定原則，此屬性必須顯示 [MDM]  或 [EAS/MDM]  。

      - 如果未將 [受控]  設定為 [MDM]  或 [EAS/MDM]  ，則不會註冊裝置。 在註冊之前，它不會接收合規性或設定原則。

      - 應用程式防護原則 (行動應用程式管理) 不需要註冊裝置。 如需詳細資訊，請參閱[建立及指派應用程式防護原則](app-protection-policies.md)。

    - **Azure AD 聯結類型**：應設定為 [Workplace]  或 [AzureAD]  。
 
      - 如果此欄位是 [未註冊]  ，則可能有註冊問題。 一般而言，取消註冊再重新註冊裝置會解決此狀態。

    - **符合 Intune 規範**：應為 [是]  。 如果顯示 [否]  ，則可能有合規性政策問題，或裝置未連線到 Intune 服務。 例如，裝置可能已關機或可能沒有網路連線。 裝置最終會變成不符合規範，可能是 30 天後。

      如需詳細資訊，請參閱[裝置合規性政策入門](device-compliance-get-started.md)。

    - **符合 Azure AD 規範**：應為 [是]  。 如果顯示 [否]  ，則可能有合規性政策問題，或裝置未連線到 Intune 服務。 例如，裝置可能已關機或可能沒有網路連線。 裝置最終會變成不符合規範，可能是 30 天後。

      如需詳細資訊，請參閱[裝置合規性政策入門](device-compliance-get-started.md)。

    - **上次簽入**：應為最近的時間和日期。 根據預設，Intune 裝置會每 8 小時檢查一次。

      - 如果 [上次簽入時間]  超過 24 小時，則可能是裝置發生問題。 無法簽入的裝置將無法從 Intune 接收原則。

      - 若要強制簽入：
        - 在 Android 裝置上，開啟公司入口網站應用程式 > [裝置]  > 從清單中選擇裝置 > [檢查裝置設定]  。
        - 在 iOS 裝置上，開啟公司入口網站應用程式 > [裝置]  > 從清單中選擇裝置 > [檢查設定]  。 
        - 在 Windows 裝置上，開啟 [設定]   > [帳戶]   > [存取公司或學校資源]  > 選取帳戶或 MDM 註冊 > [資訊]   > [同步]  。

    - 選取裝置以查看原則特定資訊。

      [裝置合規性]  顯示指派給裝置的合規性政策狀態。

      [裝置設定]  顯示指派給裝置的設定原則狀態。

      如果 [裝置合規性]  或 [裝置設定]  下未顯示預期的原則，則設為目標的原則不正確。 開啟原則，然後將原則指派給此使用者或裝置。

      **原則狀態**：

      - **不適用**：此平台不支援此原則。 例如，iOS 原則不適用於 Android。 Samsung KNOX 原則不適用於 Windows 裝置。
      - **衝突**：裝置上有 Intune 無法覆寫的現有設定。 或者，您使用不同值部署了兩個具有相同設定的原則。
      - **擱置**：裝置尚未簽入 Intune，因此無法取得原則。 或者，裝置已收到原則，但尚未對 Intune 回報狀態。
      - **錯誤**：在[針對公司資源存取問題進行疑難排解](troubleshoot-company-resource-access-problems.md)中查詢錯誤和可能的解決方法。

      **實用的連結**： 

      - [部署裝置合規性政策的方式](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies)
      - [監視裝置合規性原則](compliance-policy-monitor.md)

## <a name="youre-unsure-if-a-profile-is-correctly-applied"></a>您不確定設定檔是否已正確套用

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置]   > [所有裝置]  > 選取裝置 > [裝置設定]  。 

    每部裝置都會列出其設定檔。 每個設定檔都有 [狀態]  。 狀態是將所有指派的設定檔 (包括硬體和 OS 的限制與需求) 全部一起考慮時所達成的情況。 可能的狀態包括：

    - **符合**：裝置已收到設定檔，並對 Intune 回報其符合設定。

    - **不適用**：該設定檔設定不適用。 例如，iOS 裝置的電子郵件設定不會套用至 Android 裝置。

    - **擱置**：設定檔已傳送至裝置，但尚未對 Intune 回報狀態。 例如，Android 上的加密需要使用者啟用加密，因此可能顯示為擱置。

**實用的連結**：[監視裝置組態設定檔](device-profile-monitor.md)

> [!NOTE]
> 當兩個不同限制等級的原則套用至同一部裝置或同一個使用者時，系統會套用較嚴格的原則。

## <a name="policy-troubleshooting-resources"></a>原則疑難排解資源

- 針對[未套用至裝置的 iOS 或 Android 原則進行疑難排解](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-tip-Troubleshooting-iOS-or-Android-policies-not-applying/ba-p/280154)（開啟另一個 Microsoft 網站）
- 針對[Windows 10 Intune 原則失敗進行疑難排解](https://blogs.technet.microsoft.com/configmgrdogs/2018/08/09/troubleshooting-windows-10-intune-policy-failures/)（開啟 blog）
- [針對適用于 Windows 10 的 CSP 自訂設定進行疑難排解](https://support.microsoft.com/en-us/help/4055338/troubleshoot-csp-setting-windows-10-computer-intune)（開啟另一個 Microsoft 網站）
- [Windows 10 群組原則 Vs INTUNE MDM 原則](https://blogs.technet.microsoft.com/cbernier/2018/04/02/windows-10-group-policy-vs-intune-mdm-policy-who-wins/)（開啟另一個 Microsoft 網站）

## <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>警示：將存取規則儲存到 Exchange 失敗

**問題：** 您在管理主控台中收到警示「將存取規則儲存到 Exchange 失敗」   。

如果您在 [Exchange 內部部署原則] 工作區 (管理主控台) 中建立原則，但使用 Office 365，則 Intune 將不會強制執行已設定的原則設定。 記下警示中的原則來源。 在 [Exchange 內部部署原則] 工作區下，刪除舊版規則。 舊版規則是 Intune 內適用於內部部署 Exchange 的全域 Exchange 規則，且與 Office 365 不相關。 接著，建立適用於 Office 365 的新原則。

[針對 Intune On-Premises Exchange Connector 進行疑難排解](troubleshoot-exchange-connector.md)可能是不錯的資源。

## <a name="cant-change-security-policies-for-enrolled-devices"></a>無法變更已註冊裝置的安全性原則

當您使用 MDM 或 EAS 設定安全性原則之後，Windows Phone 裝置不允許降低這些原則的安全性。 例如，您將 [字元密碼字元數下限]  設定為 8 個，然後嘗試減少為 4 個。 此裝置已套用較嚴格的原則。

當您取消指派原則（停止部署）時，Windows 10 裝置可能不會移除安全性原則。 您可能需要保留指派的原則，然後將安全性設定變更回預設值。

根據裝置平台，如果您想要將原則變更為較不安全的值，您可能需要重設安全性原則。

例如，在 Windows 8.1 中的桌面上，從右向內撥動以開啟 [常用鍵]  列。 選擇 [設定]   > [控制台]   > [使用者帳戶]  。 在左側，選取 [重設安全性原則]  連結，然後選擇 [重設原則]  。

其他平台 (例如 Android、iOS 和 Windows Phone 8.1) 可能需要先被淘汰，再重新註冊以套用較不嚴格的原則。

[裝置註冊疑難排解](troubleshoot-device-enrollment-in-intune.md)可能是不錯的資源。

## <a name="pcs-using-the-intune-software-client---classic-portal"></a>使用 Intune 軟體用戶端的電腦 - 傳統入口網站

> [!NOTE]
> 本節適用於傳統入口網站。 

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Microsoft Intune policyplatform.log 中的原則相關錯誤

針對使用 Intune 軟體用戶端管理的 Windows 電腦，`policyplatform.log` 檔案中的原則錯誤可能來自裝置上 Windows 使用者帳戶控制 (UAC) 的非預設設定。 某些非預設的 UAC 設定可能會影響 Microsoft Intune 用戶端安裝和原則執行。

#### <a name="resolve-uac-issues"></a>解決 UAC 問題

1. 將電腦淘汰。 請參閱[移除裝置](devices-wipe.md)。

2. 等候 20 分鐘讓用戶端軟體被移除。

    > [!NOTE]
    > 請勿嘗試從 [程式和功能] 移除用戶端。

3. 在 [開始] 功能表中鍵入 **UAC**，開啟 [使用者帳戶控制] 設定。

4. 將通知滑桿移至預設設定。

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>錯誤：無法從電腦取得值，0x80041013

在本機系統時間不同步的程度超過五分鐘以上時便會發生。 如果本機電腦上的時間不同步，因為時間戳記無效，安全交易會失敗。

若要解決這個問題，設定本機系統時間時請盡可能接近網際網路時間。 或者，將它設定為網路上網域控制站的時間。


## <a name="next-steps"></a>後續步驟

[有關電子郵件設定檔的常見問題和解決方式](troubleshoot-email-profiles-in-microsoft-intune.md)

取得[來自 Microsoft 的支援說明](get-support.md)或使用[社群論壇](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)。
