---
title: 教學課程 - 設定 Slack 以針對 EMM 和應用程式設定使用 Intune
titleSuffix: Microsoft Intune
description: 在本教學課程中，您將設定 Slack，以針對 EMM 和應用程式設定使用 Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 55db37c5-0da7-4d9c-8027-525afb1c6349
Customer intent: As an Intune admin, I want to learn how to configure Slack to use Intune for EMM and app configuration..
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86e9d100847641064f472f0c3da0c9ec694f72dd
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72496714"
---
# <a name="tutorial-configure-slack-to-use-intune-for-emm-and-app-configuration"></a>教學課程：設定 Slack 以針對 EMM 和應用程式設定使用 Intune

Slack 是您可以與 Microsoft Intune 搭配使用的共同作業應用程式。   

在本教學課程中，您將：
> [!div class="checklist"]
> - 在 Slack Enterprise Grid 上，將 Intune 設定為企業行動力管理 (EMM) 提供者。 您能夠將對 Grid 方案工作區的存取限制為受 Intune 管理的裝置。
> - 建立應用程式設定原則，來管理 iOS 上的 Slack for EMM 應用程式和適用於 Android 工作設定檔裝置的 Slack 應用程式。
> - 建立 Intune 裝置合規性政策，來設定 Android 和 iOS 裝置必須符合才能視為符合規範的條件。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](../fundamentals/free-trial-sign-up.md)。

## <a name="prerequisites"></a>必要條件
您將需要在本教學課程中，使用以下訂用帳戶測試租用戶：
- Azure Active Directory Premium ([免費試用](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Intune 訂用帳戶 ([免費試用](../fundamentals/free-trial-sign-up.md))

您也需要一個 [Slack Enterprise Grid](https://get.slack.help/hc/articles/360004150931-What-is-Slack-Enterprise-Grid-) \(英文\) 方案。

## <a name="configure-your-slack-enterprise-grid-plan"></a>設定您的 Slack Enterprise Grid 方案
遵循 [Slack 的指示](https://get.slack.help/hc/articles/115002579426-Enable-Enterprise-Mobility-Management-for-your-org#step-2:-turn-on-emm) \(英文\)，針對 Slack Enterprise Grid 方案開啟 EMM，並[連線 Azure Active Directory](https://docs.microsoft.com/azure/active-directory/saas-apps/slack-tutorial) 作為您 Grid 方案的識別提供者 (IDP)。

## <a name="sign-in-to-intune"></a>登入 Intune
請以全域管理員或 Intune 服務管理員身分登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。 如果您已建立 Intune 試用版訂閱，則用來建立訂閱的帳戶是全域管理員。

## <a name="set-up-slack-for-emm-on-ios-devices"></a>在 iOS 裝置上設定 Slack for EMM
將 iOS 應用程式「Slack for EMM」新增到您的 Intune 租用戶，並建立應用程式設定原則，讓貴組織的 iOS 使用者能夠使用 Intune 作為 EMM 提供者來存取 Slack。

### <a name="add-slack-for-emm-to-intune"></a>將 Slack for EMM 新增到 Intune
在 Intune 中新增 Slack for EMM 作為受控的 iOS 應用程式，並指派您的 Slack 使用者。 應用程式是平台特定的，因此，您必須在 Android 裝置上為您的 Slack 使用者新增個別的 Intune 應用程式。
1. 在 Intune 中，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。
2. 在 [應用程式類型] 下方，選取 [市集應用程式 - iOS]  。
3. 選取 [Search the App Store]  \(搜尋應用程式市集\)。 輸入搜尋詞彙 "Slack for EMM"，然後選取該應用程式。
4. 選取 [應用程式資訊]  ，並適當地設定任何變更。
5. 選取 [新增]  。
6. 在搜尋列中，輸入 "Slack for EMM"，然後選取您剛新增的應用程式。
7. 從管理員中，選取 [指派]  。
8. 選取 [新增群組]  。 根據您選擇來在開啟適用於 Slack 的 EMM 時受到影響的人員而定，在 [指派類型]  下方，您可能想要：
    - 在選擇 [全部成員 (包括來賓)] 時，選取 [適用於已註冊的裝置]  ，或者
    - 在選擇 [全部成員 (不包括來賓)] 或 [選擇性] 時，選取 [無論註冊與否均可使用]  。
9. 選取 [包含的群組]  ，並在 [讓所有使用者都可以使用這個應用程式] 下方，選取 [是]  。
10. 按一下 [確定]  ，然後再按一次 [確定]  。
11. 按一下 **[儲存]** 。

### <a name="add-an-app-configuration-policy-for-slack-for-emm"></a>針對 Slack for EMM 新增應用程式設定原則
針對 Slack for EMM iOS 新增應用程式設定原則。 受控裝置的應用程式設定原則是平台特定的，因此，您需要在 Android 裝置上針對您的 Slack 使用者新增不同的原則。
1. 在 Intune 中，選取 [用戶端應用程式]   > [應用程式設定原則]   > [新增]  。
2. 在 [名稱] 中，輸入 Slack 應用程式設定原則測試。
3. 在 [裝置註冊類型] 下方，選取 [受控裝置]  。
4. 在 [平台] 下方，選取 [iOS]  。
5. 選取 [相關聯的應用程式]  。
6. 在搜尋列中，輸入 "Slack for EMM"，然後選取該應用程式。
7. 按一下 [確定]  ，然後選取 [組態設定]  。 
8. 選取 [確定]  ，然後選取 [新增]  。
9. 在搜尋列中，輸入「Slack 應用程式設定原則測試」，然後選取您剛新增的原則。
10. 從管理員中，選取 [指派]  。
11. 在 [指派至] 下方，選取 [所有使用者 + 所有裝置]  。
12. 按一下 **[儲存]** 。

### <a name="optional-create-an-ios-device-compliance-policy"></a>(選擇性) 建立 iOS 裝置合規性政策
建立 Intune 裝置合規性政策來設定裝置必須符合才能視為合規的條件。 我們將會在本教學課程中，為 iOS 裝置建立裝置合規性政策。 合規性政策是平台特定的，因此，您需要在 Android 裝置上針對您的 Slack 使用者新增不同的原則。
1. 在 Intune 中選取 [裝置合規性]   > [原則]   > [建立原則]  。
2. 在 [名稱] 中，輸入「iOS 合規性政策測試」。
3. 在 [描述] 中，輸入「iOS 合規性政策測試」。
4. 在 [平台] 下方，選取 [iOS]  。
5. 選取 [裝置健全狀況]  。 在 [破解的裝置] 旁邊，選取 [封鎖]  ，然後選取 [確定]  。
6. 選取 [系統安全性]  並進入 [密碼] 設定。 針對本教學課程，請選取下列建議設定：
    - 針對 [需要密碼才可解除鎖定行動裝置]，選取 [必要]  。
    - 針對 [簡單密碼]，選取 [封鎖]  。
    - 針對 [密碼長度下限]，輸入 4。
    - 針對 [必要的密碼類型]，選擇 [英數字元]  。
    - 針對 [在螢幕鎖定最少幾分鐘後必須輸入密碼]，選擇 [立即]  。
    - 針對 [密碼到期 (天數)]，輸入 41。
    - 針對 [避免重複使用以前用過的密碼次數]，輸入 5。
7. 按一下 [確定]  ，然後再次選取 [確定]  。
8. 按一下 [建立]  。

## <a name="set-up-slack-on-android-work-profile-devices"></a>在 Android 工作設定檔裝置上設定 Slack
將受 Slack 管理的 Google Play 應用程式新增到您的 Intune 租用戶，並建立應用程式設定原則，讓貴組織的 Android 使用者能夠使用 Intune 作為 EMM 提供者來存取 Slack。

### <a name="add-slack-to-intune"></a>將 Slack 新增到 Intune
在 Intune 中新增 Slack 作為受控的 Google Play 應用程式，並指派您的 Slack 使用者。 應用程式是平台特定的，因此，您必須在 iOS 裝置上為您的 Slack 使用者新增個別的 Intune 應用程式。
1. 在 Intune 中，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。
2. 在 [應用程式類型] 下方，選取 [市集應用程式 - 受控的 Google Play]  。
3. 選取 [受控的 Google Play - 核准]  。 輸入搜尋詞彙 "Slack for EMM"，然後選取該應用程式。
4. 選取 [核准]  。
5. 在搜尋列中，輸入 "Slack"，然後選取您剛新增的應用程式。
6. 從管理員中，選取 [指派]  。
7. 選取 [新增群組]  。 根據您選擇來在開啟適用於 Slack 的 EMM 時受到影響的人員而定，在 [指派類型]  下方，您可能想要：
    - 在選擇 [全部成員 (包括來賓)] 時，選取 [適用於已註冊的裝置]  ，或者
    - 在選擇 [全部成員 (不包括來賓)] 或 [選擇性] 時，選取 [無論註冊與否均可使用]  。
8. 選取 [包含的群組]，並在 [讓所有使用者都可以使用這個應用程式] 下方，選取 [是]  。
9. 按一下 [確定]  ，然後再按一次 [確定]  。
10. 按一下 **[儲存]** 。

### <a name="add-an-app-configuration-policy-for-slack"></a>針對 Slack 新增應用程式設定原則
針對 Slack 新增應用程式設定原則。 受控裝置的應用程式設定原則是平台特定的，因此，您需要在 iOS 裝置上針對您的 Slack 使用者新增個別的原則。
1. 在 Intune 中，選取 [用戶端應用程式]   > [應用程式設定原則]   > [新增]  。
2. 在 [名稱] 中，輸入 Slack 應用程式設定原則測試。
3. 在 [裝置註冊類型] 下方，選取 [受控裝置]  。
4. 在 [平台] 下方，選取 [Android]  。
5. 選取 [相關聯的應用程式]  。
6. 在搜尋列中，輸入 "Slack"，然後選取該應用程式。
7. 選取 [確定]  ，然後選取 [組態設定]  。
    - 如需設定金鑰及其值的相關資訊，請參閱 [Slack 的 AppConfig 網頁](https://www.appconfig.org/company/slack/) \(英文\) 之「技術」索引標籤上的文件。
8. 按一下 [確定]  ，然後選取 [新增]  。
9. 在搜尋列中，輸入「Slack 應用程式設定原則測試」，然後選取您剛新增的原則。
10. 從管理員中，選取 [指派]  。
11. 在 [指派至] 下方，選取 [所有使用者 + 所有裝置]  。
12. 按一下 **[儲存]** 。

### <a name="optional-create-an-android-device-compliance-policy"></a>(選擇性) 建立 Android 裝置合規性政策
建立 Intune 裝置合規性政策來設定裝置必須符合才能視為合規的條件。 我們將在本教學課程中，為 Android 裝置建立裝置合規性政策。 合規性政策是平台特定的，因此，您需要在 iOS 裝置上針對您的 Slack 使用者新增個別的原則。
1. 在 Intune 中選取 [裝置合規性]   > [原則]   > [建立原則]  。
2. 在 [名稱] 中，輸入「Android 合規性政策測試」。
3. 在 [描述] 中，輸入「Android 合規性政策測試」。
4. 在 [平台] 下方，選取 [Android Enterprise]  。
5. 在 [設定檔類型] 下方，選取 [工作設定檔]  。
6. 選取 [裝置健全狀況]  。 在 [破解的裝置] 旁邊選取 [封鎖]  ，然後選取 [確定]  。
7. 選取 [系統安全性]  並進入 [密碼]  設定。 針對本教學課程，請選取下列建議設定：
    - 針對 [需要密碼才可解除鎖定行動裝置]，選取 [必要]  。
    - 針對 [必要的密碼類型]，選取 [至少要有英數字元]  。
    - 針對 [密碼長度下限]，輸入 4。
    - 針對 [在螢幕鎖定最少幾分鐘後必須輸入密碼]，選擇 [15 分鐘]  。
    - 針對 [密碼到期 (天數)]，輸入 41。
    - 針對 [避免重複使用以前用過的密碼次數]，輸入 5。
8. 按一下 [確定]  ，然後再按一次 [確定]  。
9. 按一下 [建立]  。

## <a name="launch-slack"></a>啟動 Slack

透過您剛建立的原則，任何嘗試登入您任一個工作區的 iOS 或 Android 工作設定檔裝置都必須在 Intune 中註冊。 若要測試此案例，請嘗試在已於 Intune 中註冊的 iOS 裝置上啟動 Slack for EMM，或者在已於 Intune 註冊的 Android 工作設定檔裝置上啟動 Slack。 

## <a name="next-steps"></a>後續步驟

在本教學課程中：
- 您已在 Slack Enterprise Grid 上，將 Intune 設定為企業行動力管理 (EMM) 提供者。 
- 您建立了應用程式設定原則，來管理 iOS 上的 Slack for EMM 應用程式和適用於 Android 工作設定檔裝置的 Slack 應用程式。
- 您建立了 Intune 裝置合規性政策，來設定 Android 和 iOS 裝置必須符合才能視為符合規範的條件。

若要深入了解應用程式設定原則，請參閱 [Microsoft Intune 的應用程式設定原則](app-configuration-policies-overview.md)。 若要深入了解裝置合規性政策，請參閱[在裝置上設定規則可在您的組織中使用 Intune 存取資源](../protect/device-compliance-get-started.md)。
