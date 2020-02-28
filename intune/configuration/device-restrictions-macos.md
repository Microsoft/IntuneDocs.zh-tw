---
title: Microsoft Intune 中的 macOS 裝置設定 - Azure | Microsoft Docs
titleSuffix: ''
description: 在 Microsoft Intune 中於 macOS 裝置上新增、設定或建立設定來限制功能 (包括設定密碼需求)、控制鎖定畫面、使用內建應用程式、新增受限制或核准的應用程式、處理藍牙裝置、連線到雲端以進行備份和儲存、啟用 Kiosk 模式、新增網域，以及控制使用者與 Safari 網頁瀏覽器的互動方式。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3d26c4c6cd05a411555f7824ad21b72431eb569c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511167"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>使用 Intune 來允許或限制功能的 macOS 裝置設定



本文列出並描述您可以在 macOS 裝置上控制的各種不同設定。 作為行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來允許或停用功能、設定密碼規則、允許或限制特定應用程式，以及執行其他作業。

這些設定會新增至 Intune 裝置組態設定檔，然後指派或部署到您的 macOS 裝置。

## <a name="before-you-begin"></a>開始之前

[建立裝置限制組態設定檔](../device-restrictions-configure.md)。

> [!NOTE]
> 這些設定適用於不同註冊類型。 如需不同註冊類型的詳細資訊，請參閱 [macOS 註冊](../macos-enroll.md)。

## <a name="general"></a>一般

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>設定適用於：裝置註冊與自動裝置註冊

- **定義查閱**：[封鎖]  會防止使用者將某個文字醒目提示，然後在裝置上查閱其定義。 [未設定]  (預設) 會允許存取定義查閱功能。
- **聽寫**：[封鎖]  會防止使用者使用語音輸入來輸入文字。 [未設定]  (預設) 會允許使用者使用聽寫輸入。
- **內容快取**：選擇 [未設定]  \(預設\) 來啟用內容快取。 快取存放會將應用程式資料、網頁瀏覽器資料、下載及更多資料儲存在本機裝置上。 選取 [封鎖]  來防止這項資料儲存在快取中。

  如需 macOS 上的內容快取詳細資訊，請參閱 [Manage content caching on Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (在 Mac 上管理內容快取) (開啟另一個網站)。

  本功能適用於：  
  - macOS 10.13 與更新版本

- **延遲軟體更新**：當設定為 [未設定]  \(預設\) 時，當 Apple 發行軟體更新時便會顯示在裝置上。 例如，如果 macOS 更新由 Apple 在特定日期發行，則該更新會在發行日期左右自然地出現在裝置上。 種子組建更新會立即被允許，不會有延遲。

  [啟用]  可讓您延遲在裝置上顯示軟體更新的時間，從 0-90 天。 此設定無法控制更新何時安裝或未安裝。 

  - **延遲軟體更新的可見度**：輸入從 0-90 天的值。 當延遲到期時，使用者會收到通知，以更新為觸發延遲時可用的最舊版 OS。

    例如，如果 macOS 更新在 **1 月 1 日**推出，且 [延遲可見度]  設定為 [5 天]  ，則更新不會顯示為可用的更新。 在發行之後的**第六天**，可以使用該更新，終端使用者也可以安裝它。

    本功能適用於：  
    - macOS 10.13.4 與更新版本

- **螢幕擷取畫面**：裝置必須在 Apple 的自動裝置註冊 (DEP) 中註冊。 當設定為 [封鎖]  時，使用者無法儲存顯示器的螢幕擷取畫面。 這也會防止 [課堂] 應用程式觀察遠端畫面。 [未設定]  \(預設\) 允許使用者擷取螢幕擷取畫面，並允許 [課堂] 應用程式檢視遠端畫面。

### <a name="settings-apply-to-automated-device-enrollment"></a>設定適用於：自動裝置註冊

- **透過「課堂」應用程式觀看遠端螢幕畫面**：[停用]  會防止老師使用 [課堂] 應用程式查看其學生的畫面。 [未設定]  (預設) 可讓老師查看其學生的畫面。

  若要使用此設定，請將 [螢幕擷取畫面]  設定設定為 [未設定]  \(允許螢幕擷取畫面\)。

- **「課堂」應用程式的無提示螢幕畫面觀看**：[允許]  可讓老師看到學生的畫面，而不需要學生同意。 [未設定]  \(預設\) 會需要學生同意，老師才能看到畫面。

  若要使用此設定，請將 [螢幕擷取畫面]  設定設定為 [未設定]  \(允許螢幕擷取畫面\)。

- **學生必須要求離開「課堂」教室的權限**：[需要]  會強制註冊非受控「課堂」課程的學生，必須經老師同意才能離開課程。 [未設定]  \(預設\) 可讓學生隨時能選擇離開課程。

- **老師可以在「課堂」應用程式中自動鎖定裝置或應用程式**：[允許]  可讓老師鎖定學生的裝置或應用程式，而不需要學生核准。 [未設定]  \(預設\) 會需要學生同意，老師才能鎖定裝置或應用程式。

- **學生可以自動加入「課堂」教室**：[允許]  可讓學生在不提示老師的情況下加入教室。 [未設定]  \(預設\) 需要老師核准才能加入教室。

## <a name="password"></a>密碼

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>設定適用於：裝置註冊與自動裝置註冊

- **密碼**：**需要**終端使用者輸入密碼才可存取該裝置。 [未設定]  \(預設\) 不需要密碼。 這也不會強制任何限制，例如，封鎖簡單密碼或設定最小長度。
  - **必要的密碼類型**：指定密碼是否只能是數字，或者是否必須為英數字元 (包含字母和數字)。

    本功能適用於：  
    - macOS 10.10.3 與更新版本

  - **密碼中的非英數字元數目**：指定密碼所需的複合字元數 (**0** 到 **4** 個)。<br>複雜字元是一種符號，例如 " **?** "。
  - **密碼長度下限**：輸入使用者必須設定的密碼長度下限 (介於 **4** 到 **16** 個字元之間)。
  - **簡單密碼**：允許使用簡單密碼，例如 **0000** 或 **1234**。
  - **在螢幕鎖定最少幾分鐘後必須輸入密碼**：指定電腦必須處於非使用狀態多久的時間，才需要密碼來解除鎖定。
  - **停止活動最多幾分鐘後鎖定螢幕**：指定電腦必須閒置多久的時間，螢幕才會鎖定。
  - **密碼到期 (天數)** ：指定使用者經過多少天後必須變更密碼 (**1** 到 **255** 天)。
  - **避免重複使用以前用過的密碼**：輸入不可重複使用先前用過之密碼的次數 (從 **1** 到 **24**)。

- **禁止使用者修改密碼**：選擇 [封鎖]  可防止變更、新增或移除密碼。 [未設定]  (預設) 允許新增、變更或移除密碼。
- **禁止指紋解鎖**：選擇 [封鎖]  可防止使用指紋來解除鎖定裝置。 [未設定]  (預設) 會允許使用者使用指紋將裝置解除鎖定。

- **防止自動填滿密碼**：選擇 [封鎖]  來防止使用 macOS 上的自動填滿密碼功能。 選擇 [封鎖]  也有下列影響：

  - 系統不會提示使用者使用 Safari 或任何應用程式中的已儲存密碼。
  - 系統會停用 [自動高強度密碼]，且不會向使用者建議高強度密碼。

  [未設定]  (預設) 可允許這些功能。

- **防止近接要求密碼**：選擇 [封鎖]  可讓使用者的裝置不會向鄰近裝置要求密碼。 [未設定]  (預設) 允許這些密碼要求。

- **防止共用密碼**：[封鎖]  會防止裝置使用 AirDrop 與彼此共用密碼。 [未設定]  (預設) 允許共用密碼。

## <a name="built-in-apps"></a>內建應用程式

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>設定適用於：裝置註冊與自動裝置註冊

- **封鎖 Safari 自動填滿**：[封鎖]  會停用裝置上 Safari 中的 [自動填滿] 功能。 [未設定]  (預設) 會允許使用者變更網頁瀏覽器中的自動完成設定。
- **封鎖相機**：選擇 [封鎖]  以防止存取裝置上的相機。 [未設定]  (預設) 會允許存取裝置的相機。
- **封鎖 Apple Music**：[封鎖]  會將 [音樂] 應用程式還原至傳統模式，並停用 Music 服務。 [未設定]  (預設) 會允許使用 Apple Music 應用程式。
- **封鎖 Spotlight 網際網路搜尋結果**：[封鎖]  會防止 Spotlight 傳回來自網際網路搜尋的任何結果。 [未設定]  (預設) 會允許 Spotlight 搜尋連線到網際網路以提供搜尋結果。
- **禁止使用 iTunes 傳輸檔案**：[封鎖]  會停用應用程式檔案共用服務。 [未設定]  (預設) 可允許應用程式檔案共用服務。

  本功能適用於：  
  - macOS 10.13 與更新版本

## <a name="restricted-apps"></a>受限應用程式

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>設定適用於：裝置註冊與自動裝置註冊

- **受限應用程式類型清單**：建立不允許使用者安裝或使用的應用程式清單。 選項包括：

  - **未設定** (預設值)：Intune 不會有任何限制。 使用者可以存取您指派的應用程式，以及內建應用程式。
  - **禁止的應用程式**：沒有受 Intune 管理，且不應該安裝在裝置上的應用程式。 使用者在安裝禁止的應用程式時不會受到阻止。 但若使用者安裝此清單中的應用程式，Intune 會加以回報。
  - **核准的應用程式**：允許使用者安裝的應用程式。 使用者絕不能安裝未列出的應用程式。 自動允許 Intune 所管理的應用程式。 使用者要安裝不在核准清單上的應用程式並不會受到阻止。 但若有人安裝，Intune 會加以回報。
- **應用程式套件組合識別碼**：輸入您要之應用程式的應用程式[搭售方案識別碼](bundle-ids-built-in-ios-apps.md)。 您可以顯示或隱藏內建應用程式和企業營運應用程式。 Apple 的網站會提供[內建 Apple 應用程式](https://support.apple.com/HT208094)清單。
- **應用程式名稱**：輸入您要之應用程式的名稱。 您可以顯示或隱藏內建應用程式和企業營運應用程式。 Apple 的網站會提供[內建 Apple 應用程式](https://support.apple.com/HT208094)清單。
- **發行者**：輸入您要之應用程式的發行者。

若要將應用程式新增至這些清單中，您可以：

- **新增**：選取以建立您的應用程式清單。
- **匯入**具有應用程式詳細資料 (包括其 URL) 的 CSV 檔案。 請使用 `<app bundle ID>, <app name>, <app publisher>` 格式。 或者，選取 [匯出]  可用使用相同的格式建立您所新增的應用程式清單。

## <a name="connected-devices"></a>已連線的裝置

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>設定適用於：裝置註冊與自動裝置註冊

- **封鎖 AirDrop**：[封鎖]  會防止在裝置上使用 AirDrop。 [未設定]  (預設) 允許使用 AirDrop 功能與鄰近裝置交換內容。
- **禁止 Apple Watch 自動解除鎖定**：[封鎖]  會防止使用者以他們的 Apple Watch 解除鎖定其 macOS 裝置。 [未設定]  (預設) 會允許使用者以 Apple Watch 解除鎖定其 macOS 裝置。

## <a name="cloud-and-storage"></a>雲端與儲存體

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>設定適用於：裝置註冊與自動裝置註冊

- **防止同步 iCloud 鑰匙圈**：選擇 [封鎖]  可防止將儲存在 [鑰匙圈] 中的認證同步到 iCloud。 [未設定]  (預設) 會讓使用者同步這些認證。
- **禁止 iCloud Document 同步**：[封鎖]  會防止 iCloud 同步文件和資料。 [未設定]  (預設) 會允許將文件和索引鍵/值同步到 iCloud 儲存空間。
- **封鎖 iCloud 郵件備份**：[封鎖]  會防止 iCloud 同步處理到 macOS 郵件應用程式。 [未設定]  (預設) 會允許郵件同步到 iCloud。
- **封鎖 iCloud 聯絡人備份**：[封鎖]  會防止 iCloud 同步處理裝置連絡人。 [未設定]  (預設) 會允許使用 iCloud 同步連絡人。
- **封鎖 iCloud 行事曆備份**：[封鎖]  會防止 iCloud 同步處理到 macOS 行事曆應用程式。 [未設定]  (預設) 會允許行事曆同步到 iCloud。
- **封鎖 iCloud 提醒事項備份**：[封鎖]  會防止 iCloud 同步處理到 macOS 提醒事項應用程式。 [未設定]  (預設) 會允許提醒同步到 iCloud。
- **封鎖 iCloud 書籤備份**：[封鎖]  會防止 iCloud 同步處理裝置書籤。 [未設定]  (預設) 會允許書籤同步到 iCloud。
- **封鎖 iCloud 備忘錄備份**：[封鎖]  會防止 iCloud 同步處理裝置備忘錄。 [未設定]  (預設) 會允許備忘稿同步到 iCloud。
- **封鎖 iCloud 照片圖庫**：[封鎖]  會停用 iCloud 照片圖庫，並防止 iCloud 同步處理裝置相片。 所有尚未從 iCloud 照片圖庫完整下載的相片，都會從裝置的本機儲存體上移除。 [未設定]  \(預設\) 允許在裝置與 iCloud 照片圖庫之間同步處理相片。
- **遞交**：[未設定]  \(預設\) 會允許使用者在一部 macOS 裝置上開始工作，然後在另一部 iOS/iPadOS 或 macOS 裝置上繼續執行他們已啟動的工作。 [封鎖]  會防止裝置上的「接力」功能。 

  本功能適用於：  
  - macOS 10.15 與更新版本

## <a name="domains"></a>網域

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>設定適用於：裝置註冊與自動裝置註冊

- **電子郵件網域 URL**：將一或多個 URL **新增**到清單中。 當使用者接收到來自不是您所設定之網域的電子郵件時，該電子郵件會在 macOS 郵件應用程式中標記為不受信任。

## <a name="next-steps"></a>後續步驟

[指派設定檔](../device-profile-assign.md)並[監視其狀態](../device-profile-monitor.md)。

您也可以在 [iOS/iPadOS](../device-restrictions-ios.md) 裝置上限制裝置功能與設定。
