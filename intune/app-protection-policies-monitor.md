---
title: "如何監視應用程式保護原則"
titleSuffix: Azure portal
description: "查看有多少使用者擁有原則，並向下鑽研以了解更多詳細資料。"
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d369b311339218edcb3204ce7c575986c7a08528
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2017
---
# <a name="how-to-monitor-app-protection-policies"></a>如何監視應用程式保護原則
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**若您不是在 Azure 入口網站中**，本主題會說明在 Intune 傳統入口網站中[如何建立應用程式保護原則](https://docs.microsoft.com/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)。


您可以在 [Azure 入口網站](https://portal.azure.com)的 Intune 應用程式保護刀鋒視窗中，監視已套用到使用者的行動應用程式管理 (MAM) 原則的合規性狀態。 您能夠找到受 MAM 原則影響的使用者相關資訊、其合規性狀態，以及您的使用者可能發生的任何問題。

您有三個不同的位置可以監視合規性狀態︰

-   摘要檢視

-   詳細檢視

-   報告檢視

## <a name="summary-view"></a>摘要檢視

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗上，選擇 [行動應用程式]。
4. 在 [行動應用程式] 工作負載中，選擇 [監視] > [應用程式保護使用者狀態]，以查看摘要檢視︰

![Intune 行動應用程式管理刀鋒視窗上的摘要磚](./media/app-protection-user-status-summary.png)

-   **使用者**︰公司中使用與工作內容中的原則建立關聯之應用程式的使用者總數。

-   **由原則管理**：已使用應用程式並在工作內容中獲派原則的使用者數目。

-   **沒有原則**：使用工作內容中的任何原則未設為目標之應用程式的使用者數目。 您可以考慮將這些使用者新增至原則。
    > [!NOTE]
    > 如果一個平台有多個原則，當至少指派一個原則給使用者時，使用者會視為由原則管理。

- **已標記的使用者**︰遇到問題的使用者數目。 目前只有使用已進行 JB 破解之裝置的使用者，會被報告為**已標記的使用者**。


## <a name="detailed-view"></a>詳細檢視
選擇 [使用者狀態] 磚 (依裝置作業系統平台而定) 和 [已標記的使用者] 磚，即可進入摘要的 [詳細檢視]。

### <a name="user-status"></a>使用者狀態
您可以搜尋單一使用者，並查看該使用者的相容性狀態。 [應用程式報告] 刀鋒視窗會顯示所選使用者的下列資訊：
- 與使用者帳戶相關聯的裝置

- 裝置上具有 MAM 原則的應用程式

- 狀態：

  - **已簽入**︰此原則已部署至使用者，而且在在工作環境中至少使用一次應用程式。

  - **未簽入**：此原則已部署至使用者，但是從那時起並未在工作環境中使用應用程式。

>[!NOTE]
> 如果您搜尋的使用者沒有部署 MAM 原則，您會看見一則訊息，通知您該使用者不針對任何 MAM 原則。

若要查看使用者的報告，請遵循下列步驟︰

1.  若要選取使用者，請選擇 [摘要] 磚。

    ![螢幕擷取畫面 3](./media/MAM-reporting-6.png)

2. 在開啟的 [應用程式報告] 刀鋒視窗上，選擇 [選取使用者] 來搜尋 Azure Active Directory 使用者。

    ![[應用程式報告] 刀鋒視窗上的 [選取使用者] 選項](./media/MAM-reporting-2.png)

3. 從清單中選取一個使用者。 您會看到該使用者之相容性狀態的詳細資料。

### <a name="flagged-users"></a>標有旗標的使用者
[詳細檢視] 會顯示錯誤訊息、發生錯誤時存取的應用程式、受影響的裝置作業系統平台和時間戳記。

## <a name="reporting-view"></a>報告檢視

您可以在 [詳細檢視] 中找到相同的報表，以及協助您處理 MAM 原則合規性狀態的其他報表︰

![螢幕擷取畫面 4](./media/MAM-reporting-7.png)

-   **應用程式保護使用者報表︰**列出的資訊與您在上述 [詳細檢視] 區段下找到的**使用者狀態**報表資訊相同。

-   **應用程式保護應用程式報表︰**提供兩種不同的應用程式保護狀態，供管理員在產生報表之前選取。 狀態可以受保護或不受保護。

    -   受管理 MAM 活動的使用者狀態 (受保護)︰這份報表會依每個使用者列出每個受管理 MAM 應用程式的活動。

        -   它會顯示每個使用者的所有 MAM 原則目標應用程式，並將每個應用程式的狀態細分為使用 MAM 原則簽入，或由 MAM 原則鎖定但永遠不會簽入應用程式。
<br></br>
    -   未受管理之 MAM 活動的使用者狀態 (不受保護)︰這份報表會依每個使用者列出目前未受管理之 MAM 啟用的應用程式活動。 可能的發生原因如下︰

        -   使用者或目前不是由 MAM 原則鎖定的應用程式正在使用這些應用程式。

        -   所有的應用程式都已簽入，但未收到任何 MAM 原則。

![螢幕擷取畫面 2](./media/MAM-reporting-4.png)

## <a name="table-grouping"></a>資料表群組

當**應用程式保護使用者報表**資料顯示時，您可以依據下列項目彙總資料︰

- **驗證結果**：顯示的資料會依應用程式保護狀態分組，可能是失敗、警告或成功。
- **應用程式名稱**：顯示的資料會依應用程式 (實際應用程式名稱)，這些應用程式的狀態可能是失敗、警告或成功。

## <a name="export-app-protection-activities-to-csv"></a>將應用程式保護活動匯出到 CSV

您可以將您所有的應用程式保護原則活動匯出到單一的 .csv 檔案。 當您分析使用者回報的所有應用程式保護狀態時，可以加以使用。

若要產生應用程式保護報表，請執行下列步驟︰

1. 在 Intune [行動應用程式管理] 刀鋒視窗中，選擇 [應用程式保護報表]。

    ![螢幕擷取畫面 6](./media/app-protection-report-csv-2.png)

2. 選擇 [是] 儲存報表，然後選擇 [另存新檔]，再選取報表的儲存資料夾。

    ![螢幕擷取畫面 7](./media/app-protection-report-csv-1.png)

## <a name="see-also"></a>請參閱
[管理 iOS 應用程式之間的資料傳輸](data-transfer-between-apps-manage-ios.md)

* [當 Android 應用程式交由應用程式保護原則管理時的行為](app-protection-enabled-apps-android.md)
* [當 iOS 應用程式交由應用程式保護原則管理時的行為](app-protection-enabled-apps-ios.md)
