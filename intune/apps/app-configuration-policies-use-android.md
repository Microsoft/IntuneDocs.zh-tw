---
title: 為受控的 Android Enterprise 裝置新增應用程式設定原則
titleSuffix: Microsoft Intune
description: 在 Microsoft Intune 中使用應用程式設定原則，以提供使用者執行受控 Google Play 應用程式時的設定。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 59d93bed7bae2b757a4bd1e7b1dffc814629f6a1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725734"
---
# <a name="add-app-configuration-policies-for-managed-android-enterprise-devices"></a>為受控的 Android Enterprise 裝置新增應用程式設定原則

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune 中的應用程式設定原則能為受控 Android Enterprise 裝置上的受控 Google Play 應用程式提供設定。 應用程式開發人員會公開受 Android 管理的應用程式組態設定。 Intune 會使用這些公開設定來讓系統管理員設定應用程式的功能。 應用程式設定原則會指派給您的使用者群組。 每當應用程式檢查是否有原則設定時 (通常是應用程式第一次執行時)，便會使用這些原則設定。

> [!NOTE]  
> 並非每個應用程式都支援應用程式設定。 請連絡應用程式開發人員，以了解他們的應用程式是否支援應用程式設定原則。

1. 在 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 中，選取 [用戶端應用程式]   > [應用程式設定原則]   >  [新增]  。
2. 輸入下列內容：

    - **名稱**：輸入政策的描述性名稱。 為您的設定檔命名，以方便之後能夠輕鬆識別。 例如，一個良好的名稱是 **Android Enterprise Nine Work app policy for entire company**。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **裝置註冊類型**：選取 **受控裝置**。
    - **平台**：選取 [Android]  。

3. 選取 [相關聯的應用程式]  。 選擇您想要定義應用程式設定原則的應用程式。 從受控 Google Play 應用程式的清單中，選取您已經使用 Intune 核准並同步處理的應用程式。
4. 選取 [權限]  。 您可以透過下列方式設定組態：

    - [設定設計工具](#use-the-configuration-designer)
    - [JSON 編輯器](#enter-the-json-editor)

5. 選取 [確定]   > [新增]  。

## <a name="use-the-configuration-designer"></a>使用設定設計工具

當應用程式已設計為支援組態設定時，您可以針對受控 Google Play 應用程式使用設定設計工具。 設定會套用至 Intune 中註冊的裝置。 設計工具可讓您針對應用程式公開的設定，設定特定的設定值。

1. 選取 [新增]  。 選擇您要為應用程式輸入的組態設定清單。

    如果您是使用 GMail 或 Nine Work 做為電子郵件應用程式，請參閱[用來設定電子郵件的 Android Enterprise 裝置設定](../email-settings-android-enterprise.md)以取得這些設定的詳細資訊。

2. 對於設定中的每個金鑰和值，請設定：

    - **值類型**：設定值的資料類型。 針對「字串」值類型，您可以視需要選擇變數或憑證設定檔作為值類型。
    - **設定值**：設定的值。 如果您為 [值類型]  選取變數或憑證，請從變數或憑證設定檔清單中選擇。 如果您選擇憑證，則會在執行階段填入部署至裝置之憑證的憑證別名。

### <a name="supported-variables-for-configuration-values"></a>支援的設定值變數

如果您選擇變數作為值類型，將可以選擇下列選項：

| 選項 | 範例 |
|----|----|
| Mail | john@contoso.com |
| 使用者主體名稱 | john@contoso.com |
| 部分 UPN | john |
| Domain | contoso.com |
| 使用者名稱 | John Doe |
| 帳戶識別碼 | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| 使用者識別碼 | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| 裝置識別碼 | b9841cd9-9843-405f-be28-b2265c59ef97 |

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>在多重身分識別應用程式中只允許設定的組織帳戶 

針對 Android 裝置，請使用下列索引鍵/值組：

| **Key** | com.microsoft.intune.mam.AllowedAccountUPNs |
|---|---|
| **值** | <ul><li>一或多個以 <code>;</code> 分隔的 UPN。</li><li>只有允許的帳戶才是這個索引鍵所定義受控使用者帳戶。</li><li> 若為 Intune 註冊的裝置，<code>{{userprincipalname}}</code> 權杖可用來代表註冊的使用者帳戶。</li></ul> |

   > [!NOTE]
   > 使用多重身分識別只允許設定的組織帳戶時，您必須使用 Outlook for Android 2.2.222 或更新版本。<p></p>
   > 身為 Microsoft Intune 系統管理員，您可以控制要新增至受控裝置上 Microsoft Office 應用程式的使用者帳戶。 您可以僅允許組織使用者帳戶進行存取，並封鎖已註冊裝置上的個人帳戶。 支援的應用程式會處理應用程式設定和移除，並封鎖未經核准的帳戶。<p></p>
   > 如果是 Microsoft Word、Microsoft Excel、Microsoft PowerPoint，則您必須使用應用程式 16.0.9327.1000 版和更新版本。 

## <a name="enter-the-json-editor"></a>進入 JSON 編輯器

某些應用程式 (例如套件組合類型的應用程式) 上的組態設定並無法使用設定設計工具來設定。 請使用 JSON 編輯器來編輯那些值。 安裝應用程式時，會自動將設定值提供給應用程式。

1. 對於 [組態設定格式]  ，請選取 [進入 JSON 編輯器]  。
2. 您可以在編輯器中定義組態設定的 JSON 值。 您可以選擇 [下載 JSON 範本]  來下載之後可以設定的範例檔案。
3. 選擇 [確定]  ，然後選擇 [新增]  。

原則隨即建立，並顯示在清單中。

當指派的應用程式在裝置上執行時，會依照您在應用程式設定原則中的設定執行。

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>預先設定應用程式的權限授與狀態

您也可以預先設定應用程式權限以存取 Android 裝置功能。 根據預設，需要裝置權限 (例如存取位置或裝置相機) 的 Android 應用程式會提示使用者接受或拒絕授與權限。

以使用裝置麥克風的應用程式為例。 系統會提示使用者授與應用程式使用麥克風的權限。

1. 在 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 中，選取 [用戶端應用程式]   > [應用程式設定原則]   >  [新增]  。
2. 輸入下列內容：

    - **名稱**：輸入政策的描述性名稱。 為您的設定檔命名，以方便之後能夠輕鬆識別。 例如，一個良好的名稱是 **Android Enterprise prompt permissions app policy for entire company**。
    - **描述**。 輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **裝置註冊類型**：選取 **受控裝置**。
    - **平台**：選取 [Android]  。

3. 選取 [相關聯的應用程式]  。 選擇您想要定義設定原則的應用程式。 從 Android 工作設定檔應用程式清單中選取您已經使用 Intune 核准並同步處理的應用程式。
4. 選取 [權限]   > [新增]  。 從清單中，選取可用的應用程式權限 > [確定]  。
5. 為每個權限選取要使用此原則授與的選項：
    - **提示**。 提示使用者接受或拒絕。
    - **自動授與**。 自動核准且不通知使用者。
    - **自動拒絕**。 自動拒絕且不通知使用者。
6. 若要指派應用程式設定原則，請選取應用程式設定原則 > [指派]   > [選取群組]  。 選擇要指派至的使用者群組 > [選取]  。
7. 選擇 [儲存]  來指派原則。

## <a name="additional-information"></a>其他資訊

- [將受控 Google Play 應用程式指派給 Android Enterprise 裝置](apps-add-android-for-work.md#assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices)
- [部署 iOS 和 Android 版 Outlook 應用程式組態設定](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune) \(部分機器翻譯\)

## <a name="next-steps"></a>後續步驟

繼續[指派](apps-deploy.md)及[監視](apps-monitor.md)應用程式。
