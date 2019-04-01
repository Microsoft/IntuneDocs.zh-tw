---
title: Microsoft Intune App SDK for Android 開發人員測試指南
description: Microsoft Intune App SDK for Android 測試的指南可協助您測試您受 Intune 管理的 Android 應用程式。
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4203f424c395399cb0ed1e7472b006602aa0b210
ms.sourcegitcommit: db7a6b8fc9e82dae4f2111ca0b2d3c14e33658f9
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072467"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Microsoft Intune App SDK for Android 開發人員測試指南

Microsoft Intune App SDK for Android 測試的指南，旨在協助您測試您受 Intune 管理的 Android 應用程式。  

## <a name="prerequisite-test-accounts"></a>必要的測試帳戶
您可以建立新的帳戶，而預先產生的資料。 建立新帳戶：
1. 瀏覽至[Microsoft 示範](https://demos.microsoft.com/environments/create/tenant)站台。 
2. [設定 Intune](https://docs.microsoft.com/intune/setup-steps)啟用行動裝置管理 (MDM)。
3. [建立使用者](https://docs.microsoft.com/intune/users-add)。
4. [建立群組](https://docs.microsoft.com/intune/groups-add)。
5. [將授權指派](https://docs.microsoft.com/intune/licenses-assign)為適合您的測試。


## <a name="azure-portal-policy-configuration"></a>Azure 入口網站的原則組態
[建立及指派應用程式保護原則](https://docs.microsoft.com/intune/app-protection-policies)中[Azure 入口網站的 Intune 刀鋒視窗](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview)。 您[應用程式設定原則](https://docs.microsoft.com/intune/app-configuration-policies-overview)也可以建立並指派的 Intune 刀鋒視窗中。

> [!NOTE]
> 如果您的應用程式不會列在 Azure 入口網站中，您可以套用其原則選取**更多應用程式**選項，並提供封裝的名稱，在文字方塊中。

> [!IMPORTANT]
> 若要套用的應用程式組態原則，註冊的使用者必須目標[Intune 應用程式保護原則](https://docs.microsoft.com/intune/app-protection-policy)。

## <a name="test-cases"></a>測試案例

下列測試案例提供設定和確認步驟。 您可以使用本指引來協助疑難排解受 Intune 管理的 Android 應用程式的問題。

### <a name="required-pin-and-corporate-credentials"></a>需要 pin 碼和公司認證

您可以要求 pin 才能存取公司資源。 此外，您可以強制執行公司的驗證使用者才能使用受管理的應用程式。 您可以使用下列步驟來設定這些需求：

1. 設定**需要 PIN 以存取**並**需要公司認證才能存取**來**是**。 如需詳細資訊，請參閱 [Microsoft Intune 的 Android 應用程式保護原則設定](app-protection-policy-settings-android.md#access-requirements)。
2. 確認下列條件：
    - 啟動應用程式應呈現輸入設定的 PIN 和/或實際執行使用者在公司入口網站註冊期間所使用的提示。
    - 呈現有效的登入提示的失敗可能是因為設定不正確 android 資訊清單中，特別是 ADAL 的整合 （SkipBroker、 ClientID 和授權單位） 的值。
    - 若未顯示任何提示字元可能是因為不正確的整合式`MAMActivity`值。 如需詳細資訊`MAMActivity`，請參閱 < [Microsoft Intune App SDK for Android 開發人員指南](app-sdk-android.md)。

> [!NOTE] 
> 如果未使用上述的測試，測試可能也會失敗。 檢閱[SDK](app-sdk-android.md##sdk-integration)並[ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal)整合。

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>限制傳送和接收資料，與其他應用程式
您可以控制受管理的公司應用程式之間傳輸資料，如下所示：

1. 設定**允許應用程式將資料傳送到其他應用程式**要**受原則管理的應用程式**。
2. 將 [允許應用程式接收其他應用程式的資料] 設定為 [所有應用程式]。 使用對應方式和內容提供者會受到這些原則。
3. 確認下列條件：
    - 從開啟的未受管理的應用程式到您的應用程式函式正確。
    - 允許共用受管理的應用程式之間的內容。
    - 從受控應用程式未受管理的應用程式 (例如，Chrome) 會封鎖共用。

### <a name="restrict-cut-copy-and-paste"></a>限制剪下、複製及貼上
您可以限制受管理的應用程式的系統剪貼簿，如下所示：

1. 設定**限制剪下、 複製和貼上與其他應用程式**要**貼上的受原則管理**。
2. 確認下列條件：
    - 將文字複製到 managed 應用程式會封鎖未受管理的應用程式 （例如，訊息）。

### <a name="prevent-save-as"></a>禁止**另存新檔**
您可以控制**將儲存為**功能，如下所示：

1. 如果您的應用程式需要[整合 另存為' 控制項](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted)，將**防止 另存新檔 '** 來**是**。
2. 確認下列條件：
    - 儲存限制為只有適當的 managed 位置上。

### <a name="file-encryption"></a>檔案加密
您可以加密裝置上的資料，如下所示：

1. 設定**應用程式資料加密**要**是**。
2. 確認下列條件：
    - 一般應用程式的行為不會受到影響。

### <a name="prevent-android-backups"></a>禁止 Android 備份
您可以控制應用程式備份，如下所示：

1. 如果您已將[整合式備份的限制](app-sdk-android.md#protecting-backup-data)，設定**禁止 Android 備份**來**是**。
2. 確認下列條件：
    - 備份會限制。

### <a name="unenrollment"></a>取消註冊
您可以從遠端抹除受管理的應用程式，從包含公司的電子郵件和文件和個人資料會解密當它不會再進行管理，如下所示：

1. 從 Azure 入口網站中，[發出抹除](https://docs.microsoft.com/intune/apps-selective-wipe)。
2. 如果您的應用程式不會註冊的任何抹除處理常式會確認下列條件：
    - 完整抹除應用程式，就會發生。
3. 如果您的應用程式已註冊`WIPE_USER_DATA`或`WIPE_USER_AUXILARY_DATA`，確認下列條件：
    - 受管理的內容會從應用程式移除。 如需詳細資訊，請參閱 < [Intune App SDK for Android 開發人員指南-選擇性抹除](app-sdk-android.md#selective-wipe)。

### <a name="multi-identity"></a>多重身分識別
整合[多重身分識別支援](app-sdk-android.md#multi-identity-optional)是高風險的變更，必須先徹底測試。 最常見的問題會因為不正確設定為身分識別 （與威脅層級的內容），也在追蹤檔案 (`MAMFileProtectionManager`)。

最低限度應該重新驗證多重身分識別的下列案例：

- **另存新檔**原則是否正常運作，為受管理的身分識別。
- 管理以個人複製貼上從正確強制執行限制。
- 只有屬於受管理的身分識別的資料會加密並不會修改個人檔案。
- 在取消註冊期間的選擇性抹除只會移除受管理的身分識別資料。
- 系統會提示使用者的條件式啟動時從非受控變更為受管理的帳戶 （僅限第一次）。

### <a name="app-configuration-optional"></a>應用程式設定 （選擇性）
您可以設定受管理的應用程式的行為，如下所示：

1. 如果您的應用程式會取用任何應用程式組態設定，您應該測試您的應用程式會正確處理您 （以系統管理員） 可以設定的所有值。 [應用程式設定原則](https://docs.microsoft.com/intune/app-configuration-policies-overview)可以建立和指派中使用 Intune。

## <a name="next-steps"></a>後續步驟

- [將 Android 企業營運應用程式新增至 Microsoft Intune](lob-apps-android.md)。
