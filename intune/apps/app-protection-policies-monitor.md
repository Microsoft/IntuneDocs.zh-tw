---
title: 如何監視應用程式保護原則
titleSuffix: Microsoft Intune
description: 此主題說明如何在 Intune 中監視應用程式保護原則。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 899e2d2dc8458d0909f01e9dfcc1056874ef0fa7
ms.sourcegitcommit: ecaff388038fb800f2e646f8efcf8f3b1e2fd1b1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/18/2020
ms.locfileid: "77437965"
---
# <a name="how-to-monitor-app-protection-policies"></a>如何監視應用程式保護原則
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

您可以從 [Azure 入口網站](https://portal.azure.com)的 [Intune 應用程式防護] 窗格中，監視已套用到使用者的應用程式保護原則狀態。 此外，您可以找到受應用程式保護原則影響的使用者、原則合規性狀態，以及您的使用者可能遇到之任何問題的相關資訊。

您有三個不同的位置可監視應用程式保護原則︰
- 摘要檢視
- 詳細檢視
- 報告檢視

應用程式保護資料的保留期間為 90 天。 過去 90 天內簽入至 Intune 服務的任何應用程式執行個體，都將包含於 [應用程式保護狀態] 報告中。 應用程式執行個體  是唯一的使用者 + 應用程式 + 裝置。 

> [!NOTE]
> 如需詳細資料，請參閱[如何建立及指派應用程式防護原則](app-protection-policies.md)。

## <a name="summary-view"></a>摘要檢視

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 選取 [應用程式]   > [監視]   > [應用程式保護狀態]  。

   ![[Intune 行動應用程式管理] 窗格的 [摘要] 圖格螢幕擷取畫面](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **指派的使用者**：您公司中使用與工作內容原則建立關聯之應用程式的指派使用者當中，受到保護且授權的總數，以及未受保護且未授權的總數。
- **已標幟的使用者**：其裝置遇到問題的使用者數目。 [已標幟的使用者]  下會報告已進行 JB (iOS) 或 Root (Android) 破解的裝置。 此外，這裡將會報告具有透過 Google SafetyNet 裝置證明檢查 (如果 IT 系統管理員有開啟) 標幟之裝置的使用者。 
- **具潛在有害應用程式的使用者**：Google Play 安全防護所偵測到其 Android 裝置上可能具有害應用程式的使用者數目。 
- **iOS 使用者狀態**和 **Android 使用者狀態**：已使用應用程式並在相關平台工作內容中獲派原則的使用者數目。 此資訊顯示由原則管理的使用者數目，以及使用工作內容中任何原則未設為目標之應用程式的使用者數目。 您可以考慮將這些使用者新增至原則。
- [最受保護的 iOS/iPadOS 應用程式]  與 [最受保護的 Android 應用程式]  ：根據最常使用的 iOS/iPadOS 與 Android 應用程式，此資訊會依平台顯示受保護與未受保護之應用程式的數目。
- [前幾大未註冊的已設定 iOS/iPadOS 應用程式]  與 [前幾大未註冊的已設定 Android 應用程式]  ：根據未註冊裝置最常使用的 iOS/iPadOS 與 Android 應用程式，此資訊會依平台顯示已設定之應用程式 (也就是使用應用程式設定原則) 的數目。

    > [!NOTE]
    > 如果一個平台有多個原則，當至少指派一個原則給使用者時，使用者會視為由原則管理。

## <a name="detailed-view"></a>詳細檢視
您可以透過選擇 [標有旗標的使用者]  磚和 [具潛在有害應用程式的使用者]  磚來取得摘要的詳細檢視。

### <a name="flagged-users"></a>標有旗標的使用者
[詳細檢視] 會顯示錯誤訊息、發生錯誤時存取的應用程式、受影響的裝置作業系統平台和時間戳記。 此錯誤通常用於已進行越獄 (iOS) 或 Root (Android) 的裝置。 此外，這裡會報告具有透過「SafetyNet 裝置證明」條件式啟動檢查旗標之裝置的使用者，以及 Google 所報告的原因。 若要從報告中移除使用者，裝置本身的狀態必須已變更，這會在下一次根偵測檢查 (或越獄檢查/SafetyNet 檢查發生) 需要回報正面結果之後發生。 如果裝置已真正修復，則在窗格重新載入時，將會在 [標有旗標的使用者] 報表上進行重新整理。

### <a name="users-with-potentially-harmful-apps"></a>具潛在有害應用程式的使用者
這裡會報告具有透過 [需要對應用程式進行威脅掃描]  條件式啟動檢查旗標之裝置的使用者，以及 Google 所報告的威脅類別。 如果這份報告中列出的應用程式是透過 Intune 部署的，請連絡該應用程式的應用程式開發人員，或移除該應用程式，以使其無法指派給您的使用者。 詳細的檢視會顯示：

- **使用者**：使用者的名稱。
- **應用程式套件識別碼**：這是 Android OS 唯一判斷應用程式的方式。
- **應用程式是否已啟用 MAM**：應用程式是否是透過 Microsoft Intune 部署。 
- **威脅類別**：Google 判斷此應用程式所屬的威脅類別。 
- **電子郵件**：使用者的電子郵件。
- **裝置名稱**：與使用者帳戶相關聯之任何裝置的名稱。
- **時間戳記**：這是 Google 與 Microsoft Intune 針對潛在有害應用程式最後一次同步的日期。

## <a name="reporting-view"></a>報告檢視

您可以在 [應用程式保護狀態]  窗格頂端找到相同的報表。 若要檢視這些報表，請選取 [應用程式]   > [應用程式保護狀態]   > [報表]  。 [報表]  窗格提供數個以使用者和應用程式為基礎的報表，包括：

### <a name="user-report"></a>使用者報表
您可以搜尋單一使用者，並查看該使用者的相容性狀態。 [應用程式報告]  窗格會顯示所選使用者的下列資訊：
- **圖示**：顯示應用程式狀態是否是最新的。
- **應用程式名稱**：應用程式的名稱。
- **裝置名稱**：與使用者帳戶相關聯的裝置。
- **裝置類型**：裝置或裝置所執行之作業系統的類型。
- **原則**：與應用程式相關聯的原則。
- **狀態**：
  - **已簽入**：此原則已部署至使用者，而且在工作內容中至少使用一次應用程式。
  - **未簽入**：此原則已部署至使用者，但從那時起並未在工作內容中使用應用程式。
- **上次同步處理**：上次應用程式與 Intune 同步的時間。 

>[!NOTE]
> [上次同步處理]  資料行代表主控台內使用者狀態報告與應用程式保護原則[可匯出的 .csv 報告](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities)兩者中相同的值。 差異在於兩個報告中，值之間的些許同步處理延遲。 
>
> [上次同步處理] 中參考的時間是 Intune 上次看到應用程式執行個體的時間。 當使用者啟動應用程式時，它可能會在啟動時通知 Intune 應用程式保護服務，取決於它上次的簽入時間。 請參閱[應用程式保護原則簽入的重試間隔時間](~/apps/app-protection-policy-delivery.md)。 如果使用者未在上次簽入間隔 (通常是 30 分鐘的主動使用) 之內使用該特定應用程式，而且他們啟動應用程式，則：
>
> - 應用程式保護原則可匯出 .csv 報告有最新的時間，範圍介於 1 分鐘 (最小值) 到 30 分鐘 (最大值)。
> - 使用者狀態報告將會立即有最新的時間。
>
> 例如，考慮已設定目標的已授權使用者，它在下午 12:00 啟動了受控應用程式：
> - 若這是第一次登入，則表示使用者之前已登出，並且沒有向 Intune 進行應用程式執行個體註冊。 使用者登入之後，會取得新的應用程式執行個體註冊，而且可以立即簽入 (未來簽入與先前所列的時間延遲相同)。 因此，上次同步處理時間在使用者狀態報告中為下午 12:00，而在應用程式保護原則報告中則為下午 12:01 (或至少為下午 12:30)。 
> - 若使用者剛啟動應用程式，則回報的上次同步處理時間取決於使用者上次簽入的時間。

若要查看使用者的報告，請遵循下列步驟︰

1. 若要選取使用者，請選擇 [使用者狀態]  摘要磚。

    ![[Intune 行動應用程式管理] 的 [摘要] 磚螢幕擷取畫面](./media/app-protection-policies-monitor/MAM-reporting-6.png)

2. 在 [應用程式報告]  窗格上，選擇 [選取使用者]  來搜尋 Azure Active Directory 使用者。

    ![[應用程式報告] 窗格上的 [選取使用者] 選項螢幕擷取畫面](./media/app-protection-policies-monitor/MAM-reporting-2.png)

3. 從清單中選取一個使用者。 您可以看到該使用者之合規性狀態的詳細資料。

>[!NOTE]
> 如果您搜尋的使用者沒有部署 MAM 原則，則會看見一則訊息，通知您該使用者不針對任何 MAM 原則。

### <a name="app-report"></a>應用程式報表
您可以依平台和應用程式搜尋，然後此報表將會提供兩種不同的應用程式保護狀態，供您在產生報表之前選取。 狀態可以是 [受保護]  或 [不受保護]  。

  - 受控 MAM 活動的使用者狀態 ([受保護]  )：這份報告會依每個使用者列出每個受控 MAM 應用程式的活動。 它會針對每個使用者顯示 MAM 原則設為目標的所有應用程式，以及使用 MAM 原則簽入的每個應用程式的狀態。 此報告還包括以 MAM 原則設為目標，但從未簽入的每個應用程式的狀態。
  - 非受控 MAM 活動的使用者狀態 ([不受保護]  )：此報告會依每個使用者，列出目前非受控之啟用 MAM 的應用程式活動。 發生這種情況的可能原因是：
    - 使用者或目前不是由 MAM 原則設為目標的應用程式正在使用這些應用程式。
    - 所有的應用程式都已簽入，但未收到任何 MAM 原則。

    ![使用者的 [應用程式報告] 窗格螢幕擷取畫面，其中包含三個應用程式的詳細資料](./media/app-protection-policies-monitor/MAM-reporting-4.png)

### <a name="user-configuration-report"></a>**使用者設定報表**
根據選取的使用者，此報表會提供使用者已收到的任何應用程式設定的相關詳細資料。

### <a name="app-configuration-report"></a>**應用程式設定報表**
根據選取的平台和應用程式，此報表會提供有哪些使用者已收到所選應用程式之設定的相關詳細資料。

### <a name="app-learning-report-for-windows-information-protection"></a>Windows 資訊保護的應用程式學習報表
此報表會顯示哪些應用程式嘗試跨越原則界限。

### <a name="website-learning-for-windows-information-protection"></a>Windows 資訊保護的網站學習
此報表會顯示哪些網站嘗試跨越原則界限。

## <a name="export-app-protection-activities"></a>匯出應用程式防護活動
您可以將您所有的應用程式保護原則活動匯出到單一的 .csv 檔案。 當您分析使用者回報的所有應用程式保護狀態時，可以加以使用。 **應用程式保護 .csv 檔案會顯示**：
- **使用者**：使用者的名稱。
- **電子郵件**：使用者的電子郵件。
- **應用程式**：應用程式的名稱。
- **應用程式版本**：應用程式的版本。
- **裝置名稱**：與使用者帳戶相關聯之任何裝置的名稱。
- **裝置製造商**：這會列出裝置的製造商 (僅限 Android)。 
- **裝置型號**：這會列出裝置的製造商 (僅限 Android)。 
- **Android 修補程式版本**：最新 Android 安全性修補程式的日期。
- **AAD 裝置識別碼**：如果裝置已加入 AAD，則會填入此欄。
- **MDM 裝置識別碼**：如果裝置已註冊 Microsoft Intune MDM，則會填入此欄。
- **平台**：作業系統。
- **平台版本**：作業系統版本。
- **管理類型**：裝置上的管理類型。 例如 Android Enterprise、非受控或 MDM。  
- **應用程式保護狀態**：未保護或已保護。
- **原則**：與應用程式相關聯的應用程式保護原則。
- **上次同步處理**：應用程式上次與 Microsoft Intune 同步的時間。 
- **合規性狀態**：使用者裝置上的應用程式是否符合任何應用程式型條件式存取原則的規範。  

遵循這些步驟以產生應用程式保護 .csv 檔案或應用程式設定 .csv 檔案：

1. 在 Intune [行動應用程式管理] 窗格上，選擇 [應用程式保護報表]  。

    ![應用程式防護下載連結的螢幕擷取畫面](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. 選擇 [是]  以儲存報告，然後選擇 [另存新檔]  。 選取用來儲存報告的資料夾。

    ![[儲存報表] 確認方塊的螢幕擷取畫面](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)
   
> [!NOTE]
> Intune 提供其他裝置報告欄位，包括應用程式註冊識別碼、Android 製造商、型號與安全性修補程式版本，以及 iOS/iPadOS 型號。 在 Intune 中，您可以透過選取 [應用程式]   > [應用程式保護狀態]   > [應用程式防護報告: iOS/iPadOS、Android]  來存取這些欄位。 此外，這些參數會協助您設定適用於裝置製造商的 [允許]  清單 (Android)、適用於裝置型號的 [允許]  清單 (Android 和 iOS)，以及 [最低 Android 安全性修補程式版本]  設定。   
 
## <a name="see-also"></a>請參閱
- [管理 iOS/iPadOS 應用程式之間的資料傳輸](data-transfer-between-apps-manage-ios.md)
- [當 Android 應用程式交由應用程式防護原則管理時的行為](../fundamentals/end-user-mam-apps-android.md)
- [當 iOS/iPadOS 應用程式交由應用程式保護原則管理時的行為](../fundamentals/end-user-mam-apps-ios.md)
