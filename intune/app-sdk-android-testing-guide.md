---
title: Microsoft Intune App SDK for Android 開發人員測試指南
description: Microsoft Intune App SDK for Android 測試指南可協助您測試 Intune 管理的 Android 應用程式。
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f8fa8f361e886c8eac697bb585ccf15eb9152f1
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66043848"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Microsoft Intune App SDK for Android 開發人員測試指南

Microsoft Intune App SDK for Android 測試指南旨在協助您測試 Intune 管理的 Android 應用程式。  

## <a name="prerequisite-test-accounts"></a>必要的測試帳戶
不論是否使用預先產生的資料，都可以建立新帳戶。 建立新帳戶：
1. 巡覽至 [Microsoft 示範](https://demos.microsoft.com/environments/create/tenant)網站。 
2. [設定 Intune](https://docs.microsoft.com/intune/setup-steps) 以啟用行動裝置管理 (MDM)。
3. [建立使用者](https://docs.microsoft.com/intune/users-add)。
4. [建立群組](https://docs.microsoft.com/intune/groups-add)。
5. 根據測試需要[指派授權](https://docs.microsoft.com/intune/licenses-assign)。


## <a name="azure-portal-policy-configuration"></a>Azure 入口網站原則設定
在 [Azure 入口網站的 Intune 刀鋒視窗](https://docs.microsoft.com/intune/app-protection-policies)中[建立及指派應用程式保護原則](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview)。 您的[應用程式設定原則](https://docs.microsoft.com/intune/app-configuration-policies-overview)也可以在 Intune 刀鋒視窗中建立及指派。

> [!NOTE]
> 如果您的應用程式未列於 Azure 入口網站中，您可以在文字方塊中選取 [更多應用程式]  選項並提供套件名稱，透過原則來定位該應用程式。

> [!IMPORTANT]
> 若要套用應用程式設定原則，[Intune 應用程式保護原則](https://docs.microsoft.com/intune/app-protection-policy)必須設定要註冊的目標使用者。

## <a name="test-cases"></a>測試案例

下列測試案例提供設定和確認步驟。 您可以使用本指引來對 Intune 管理的 Android 應用程式問題進行疑難排解。

### <a name="required-pin-and-corporate-credentials"></a>必要的 PIN 和公司認證

您可以要求 PIN 以存取公司資源。 此外，您可以要求使用者進行公司驗證，才能使用受控應用程式。 您可以使用下列步驟來設定這些要求：

1. 將 [需要 PIN 以進行存取]  和 [需要公司認證以進行存取]  設為 [是]  。 如需詳細資訊，請參閱 [Microsoft Intune 的 Android 應用程式保護原則設定](app-protection-policy-settings-android.md#access-requirements)。
2. 確認下列條件：
    - 應用程式啟動應顯示輸入/設定 PIN 的提示，和/或使用者在公司入口網站註冊期間所使用的生產環境。
    - 若未顯示有效的登入提示，原因可能是 Android 資訊清單設定不正確，特別是 ADAL 整合 (SkipBroker、ClientID 和授權單位) 的值。
    - 若未顯示任何提示字元，可能是因為 `MAMActivity` 值整合不正確。 如需 `MAMActivity` 的詳細資訊，請參閱 [Microsoft Intune App SDK for Android 開發人員指南](app-sdk-android.md)。

> [!NOTE] 
> 如果上述測試失敗，以下測試可能也會失敗。 檢閱 [SDK](app-sdk-android.md##sdk-integration) 與 [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) 整合。

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>限制傳送和接收其他應用程式的資料
您可以控制公司管理應用程式之間的資料傳輸，如下所示：

1. 將 [允許應用程式將資料傳送到其他應用程式]  設定為 [受原則管理的應用程式]  。
2. 將 [允許應用程式接收其他應用程式的資料]  設定為 [所有應用程式]  。 使用方式和內容提供者會受到這些原則影響。
3. 確認下列條件：
    - 可以正常從非受控應用程式開啟您的應用程式。
    - 允許共用受控應用程式之間的內容。
    - 封鎖從受控應用程式到非受控應用程式 (例如 Chrome) 的共用。

### <a name="restrict-cut-copy-and-paste"></a>限制剪下、複製及貼上
您可以將系統剪貼簿限制於受控應用程式，如下所示：

1. 將 [限制與其他應用程式的剪下、複製和貼上]  設為 [原則管理的貼上]  。
2. 確認下列條件：
    - 將文字複製從您的應用程式複製到受控與非受控應用程式 (例如 Messages) 會受到封鎖。

### <a name="prevent-save-as"></a>禁止**另存新檔**
您可以控制**另存新檔**功能，如下所示：

1. 如果您的應用程式需要[整合式 [另存新檔] 控制項](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted)，請將 [禁止另存新檔]  設為 [是]  。
2. 確認下列條件：
    - 儲存僅限於適當的受管理位置。

### <a name="file-encryption"></a>檔案加密
您可以加密裝置上的資料，如下所示：

1. 將 [應用程式資料加密]  設為 [是]  。
2. 確認下列條件：
    - 一般的應用程式行為不會受到影響。

### <a name="prevent-android-backups"></a>禁止 Android 備份
您可以控制應用程式備份，如下所示：

1. 如果您已設定 [整合式備份限制](app-sdk-android.md#protecting-backup-data)，請將 [禁止 Android 備份]  設為 [是]  。
2. 確認下列條件：
    - 備份受到限制。

### <a name="unenrollment"></a>取消註冊
您可以從遠端抹除受控應用程式，使其不再包含公司電子郵件和文件，並在個人資料不再如以下方式管理時將其解密：

1. 從 Azure 入口網站[發出抹除](https://docs.microsoft.com/intune/apps-selective-wipe)。
2. 如果您的應用程式沒有註冊任何抹除處理常式，請確認下列條件：
    - 可完整抹除應用程式。
3. 如果您的應用程式已註冊 `WIPE_USER_DATA` 或 `WIPE_USER_AUXILARY_DATA`，請確認下列條件：
    - 受管理的內容已從應用程式移除。 如需詳細資訊，請參閱 [Microsoft Intune App SDK for Android 開發人員指南 - 選擇性抹除](app-sdk-android.md#selective-wipe)。

### <a name="multi-identity"></a>多重身分識別
整合[多重身分識別支援](app-sdk-android.md#multi-identity-optional)是高風險的變更，必須先經過徹底測試。 最常見的問題是由於身分識別設定不正確 (內容與威脅層級) 與追蹤檔案 (`MAMFileProtectionManager`)。

至少應重新驗證下列多重身分識別情況：

- **另存新檔**原則是否正常運作於受控識別。
- 複製貼上的限制正確實施 (從受控到個人)。
- 僅加密屬於受控識別的資料，且未修改個人檔案。
- 在取消註冊期間的選擇性抹除只會移除受控識別資料。
- 從未受控的帳戶變更為受控帳戶時，系統會提示終端使用者進行條件式啟動 (僅限第一次)。

### <a name="app-configuration-optional"></a>應用程式設定 (選用)
您可以設定受控應用程式的行為，如下所示：

1. 如果您的應用程式會取用任何應用程式組態設定，您應該測試應用程式是否可正確處理您 (系統管理員) 能夠設定的所有值。 [應用程式設定原則](https://docs.microsoft.com/intune/app-configuration-policies-overview)可以使用 Intune 來建立及指派。

## <a name="next-steps"></a>後續步驟

- [將 Android 企業營運應用程式新增至 Microsoft Intune](lob-apps-android.md)。
