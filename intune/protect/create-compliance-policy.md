---
title: 建立 Microsoft Intune 中的裝置合規性原則 - Azure | Microsoft Docs
description: 建立裝置合規性原則、狀態和嚴重性等級的概觀、使用 InGracePeriod 狀態、使用條件式存取、處理沒有已指派原則的裝置，以及 Azure 入口網站與傳統入口網站中的 Microsoft Intune 合規性差異
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 76998c32f09b20e624359cc8a38231e14a70399b
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72786067"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>在 Microsoft Intune 中建立合規性政策

裝置合規性政策是使用 Intune 保護您組織資源時的一項重要功能。 在 Intune 中，您可以建立裝置必須符合才能視為符合規範的規則和設定，例如最低作業系統版本。 如果裝置不符合規範，您接著可以使用[條件式存取](conditional-access.md)來封鎖對資料和資源的存取。

您也可以針對不符合規範的裝置採取動作，例如將通知電子郵件傳送給使用者。 如需合規性政策用途及其用法的概觀，請參閱[開始使用裝置合規性](device-compliance-get-started.md)。

這篇文章：

- 列出建立合規性政策的必要條件以及步驟。
- 向您示範如何將政策指派給您的使用者和裝置群組。
- 描述其他功能 (包括範圍標籤) 以「篩選」您的政策，以及您可以針對不符合規範的裝置所採取的步驟。
- 當裝置收到政策更新時，列出簽入重新整理週期時間。

## <a name="before-you-begin"></a>開始之前

若要使用裝置合規性政策，請確定您：

- 使用下列訂用帳戶：

  - Intune
  - 如果您使用條件式存取，則需要有 Azure Active Directory (AD) Premium 版本。 [Azure Active Directory 定價](https://azure.microsoft.com/pricing/details/active-directory/)會列出不同版本的功能。 Intune 合規性並不需要 Azure AD。

- 使用支援的平台：

  - Android 裝置管理員
  - Android 企業
  - iOS
  - macOS
  - Windows 10
  - Windows 8.1
  - Windows Phone 8.1

- 在 Intune 中註冊裝置 (查看合規性狀態所必需)

- 向一位使用者註冊裝置，或者在沒有主要使用者的情況下進行註冊。 不支援向多位使用者註冊裝置。

## <a name="create-the-policy"></a>建立政策

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置合規性]  。 下列選項可供您選擇：

    - **概觀**：顯示符合規範、未評估之裝置的摘要和數量等等。 此外，它也會列出政策以及政策中的個別設定。 [監視 Intune 裝置合規性政策](compliance-policy-monitor.md)會提供一些有用的資訊。
    - **管理**：建立裝置政策、將[通知](quickstart-send-notification.md)傳送到不符合規範的裝置，然後啟用 [網路隔離](use-network-locations.md)。
    - **監視**：請在設定和政策層級檢查您裝置的合規性狀態。 [監視 Intune 裝置合規性政策](compliance-policy-monitor.md)是不錯的資源。 此外，請檢視記錄檔，並檢查您裝置的威脅代理程式狀態。
    - **安裝**：使用[內建的合規性原則](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies)、啟用 [Microsoft Defender 進階威脅防護 (ATP)](advanced-threat-protection.md)、新增 [Mobile Threat Defense 連接器](mobile-threat-defense.md)，以及使用 [Jamf](conditional-access-integrate-jamf.md)。

3. 選取 [政策]   > [建立政策]  。 輸入下列內容：

   - **名稱**：輸入政策的描述性名稱。 為您的設定檔命名，以方便之後能夠輕鬆識別。 例如，**Mark iOS jailbroken devices as not compliant** 是一個不錯的政策名稱。  

   - **描述**：輸入政策的描述。 這是選擇性設定，但建議執行。  

   - **平台**：選擇您的裝置平台。 選項包括：
     - **Android 裝置系統管理員**
     - **Android Enterprise**
     - **iOS/iPadOS**
     - **macOS**
     - **Windows Phone 8.1**
     - **Windows 8.1 及更新版本**
     - **Windows 10 及更新版本**

     針對 *Android Enterprise*，您接著必須選取**設定檔類型**：
     - **裝置擁有者**
     - **工作設定檔**

   - **設定**：下列文章會列出並描述每個平台的設定︰
     - [Android 裝置系統管理員](compliance-policy-create-android.md)
     - [Android Enterprise](compliance-policy-create-android-for-work.md)
     - [iOS/iPadOS](compliance-policy-create-ios.md)
     - [macOS](compliance-policy-create-mac-os.md)
     - [Windows Phone 8.1，Windows 8.1 和更新版本](compliance-policy-create-windows-8-1.md)
     - [Windows 10 及更新版本](compliance-policy-create-windows.md)  

   - **位置** (Android 裝置系統管理員)  ：在您的原則中，您可以透過裝置的位置強制實行相容性。 從現有的位置中選擇。 還沒有位置？ 在 Intune 中[使用位置 (網路柵欄)](use-network-locations.md) 可提供一些指導。  

   - **因不符合規範而採取的動作**：針對不符合合規性政策的裝置，您可以新增一連串動作，以便自動套用。 您可以變更裝置標示為不符合規範的排程 (例如一天之後)。 您也可以設定第二個動作，在裝置不符合規範時傳送電子郵件給使用者。
    
     [為不符合規範的裝置新增動作](actions-for-noncompliance.md)提供詳細資訊，包括建立通知電子郵件給您的使用者。

     例如，您正在使用 [位置] 功能，並在合規性政策中新增一個位置。 當您選取至少一個位置時，則會套用不符合規範的預設動作。 如果裝置未連線到所選取的位置，則會立即視為不符合規範。 您可以提供使用者寬限期，例如一天。

   - **範圍 (標籤)** ：範圍標籤是將政策指派並篩選到特定群組 (例如銷售、人力資源、所有 US-NC 員工等等) 的絕佳方式。 新增設定之後，您也可以將範圍標籤新增至合規性政策。 [使用範圍標籤篩選政策](../fundamentals/scope-tags.md)是不錯的資源。

4. 完成後，請選取 [確定]   > [建立]  以儲存變更。 政策隨即建立，並顯示在清單中。 接下來，將政策指派給您的群組。

## <a name="assign-the-policy"></a>指派原則

政策建立之後，下一個步驟是將政策指派給您的群組：

1. 選擇您所建立的政策。 現有的原則位於 [裝置合規性]   > [原則]  。
2. 選取政策 > [指派]  。 您可以包含或排除 Azure Active Directory (AD) 安全性群組。
3. 選擇 [選取的群組]  以查看您的 Azure AD 安全性群組。 選取您希望套用此原則的群組 > 選擇 [儲存]  以部署原則。

當您的原則設為目標的使用者或裝置使用 Intune 簽入時，會評估其合規性。

### <a name="evaluate-how-many-users-are-targeted"></a>評估設定為目標的使用者人數

當您指派政策時，您也可以**評估**有多少使用者受到影響。 此功能會計算使用者，但不會計算裝置。

1. 在 Intune 中，選取 [裝置合規性]   > [政策]  。
2. 選取政策 > [指派]   > [評估]  。 此時會出現一個訊息，向您顯示此政策設定為目標的使用者人數。

如果 [評估]  按鈕呈現灰色，請確認該政策已指派給一或多個群組。

<!-- ## Actions for noncompliance

For devices that don't meet your compliance policies, you can add a sequence of actions to apply automatically. You can change the schedule when the device is marked non-compliant, such as after one day. You can also configure a second action that sends an email to the user when the device isn't compliant.

[Add actions for noncompliant devices](actions-for-noncompliance.md) provides more information, including creating a notification email to your users.

For example, you're using the Locations feature, and add a location in a compliance policy. The default action for noncompliance applies when you select at least one location. If the device isn't connected to the selected locations, it's immediately considered not compliant. You can give your users a grace period, such as one day.

## Scope tags

Scope tags are a great way to assign and filter policies to specific groups, such as Sales, HR, All US-NC employees, and so on. After you add the settings, you can also add a scope tag to your compliance policies. [Use scope tags to filter policies](../fundamentals/scope-tags.md) is a good resource.
-->

## <a name="refresh-cycle-times"></a>重新整理週期時間

Intune 會使用各種重新整理循環來檢查合規性原則的更新。 如果裝置是最近註冊的，則簽入的執行頻率會更加頻繁。 [原則和設定檔重新整理循環](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)列出預估的重新整理時間。

使用者隨時都能開啟公司入口網站應用程式並同步處理裝置，以立即檢查是否有原則更新。

### <a name="assign-an-ingraceperiod-status"></a>指派 InGracePeriod 狀態

合規性原則的 InGracePeriod 狀態是一個值。 此值會由裝置寬限期與裝置該合規性原則實際狀態的組合來決定。

具體來說，若裝置的已指派合規性政策為 NonCompliant 狀態，且：

- 未針對裝置指派寬限期，則針對合規性原則所指派的值會是 NonCompliant
- 裝置的寬限期已過，則針對合規性原則所指派的值會是 NonCompliant
- 裝置的寬限期未到，則針對合規性原則所指派的值會是 InGracePeriod

下表摘要說明這些選項：

|實際合規性狀態|指派的寬限期值|有效合規性狀態|
|---------|---------|---------|
|NonCompliant |未指派任何寬限期 |NonCompliant |
|NonCompliant |昨天的日期|NonCompliant|
|NonCompliant |明天的日期|InGracePeriod|

如需有關監視裝置合規性政策的詳細資訊，請參閱[監視 Intune 裝置合規性政策](compliance-policy-monitor.md)。

### <a name="assign-a-resulting-compliance-policy-status"></a>指派最終合規性規則狀態

如果裝置有多個合規性原則，且裝置的兩個或更多個已指派的合規性原則具有不同的合規性狀態，系統就會指派單一的最終合規性狀態。 此指派會以指派至各合規性狀態的概念嚴重性等級為準。 每個合規性狀態均具下列嚴重性等級：

|狀態  |嚴重性  |
|---------|---------|
|Unknown     |1|
|NotApplicable     |2|
|符合標準|3|
|InGracePeriod|4|
|NonCompliant|5|
|錯誤|6|

當裝置具有多個合規性原則時，系統就會將所有原則的最高嚴重性等級指派給該裝置。

例如，有一個裝置獲指派三個合規性政策，分別是：Unknown 狀態 (嚴重性 = 1)、Compliant 狀態 (嚴重性 = 3)、InGracePeriod 狀態 (嚴重性 = 4)。 InGracePeriod 狀態的嚴重性層級最高。 因此，全部三個政策都有 InGracePeriod 合規性狀態。

## <a name="next-steps"></a>後續步驟

[監視您的原則](compliance-policy-monitor.md)。
