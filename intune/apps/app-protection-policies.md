---
title: 建立及部署應用程式保護原則
titleSuffix: Microsoft Intune
description: 本主題描述如何建立及指派 Microsoft Intune 應用程式保護原則 (簡稱 APP)。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d1a55f758be50c342a5c8851106f0c37e6aec50
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513719"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>如何建立及部署應用程式保護原則

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

了解如何建立及指派 Microsoft Intune 應用程式保護原則 (APP) 給您組織的使用者。 本主題也會描述如何變更現有的原則。

## <a name="before-you-begin"></a>開始之前

無論裝置是否由 Intune 管理，都能對裝置上執行的應用程式套用應用程式防護原則。 如需應用程式防護原則運作方式，以及 Intune 應用程式防護原則支援案例的詳細描述，請參閱[什麼是 Microsoft Intune 應用程式防護原則？](app-protection-policy.md)

如果您正在尋找 MAM 支援之應用程式的清單，請參閱 [MAM 應用程式清單](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。

如需有關將您組織的企業營運 (LOB) 應用程式新增到 Microsoft Intune 以準備應用程式保護原則的資訊，請參閱[將應用程式新增至 Microsoft Intune](apps-add.md)。

## <a name="app-protection-policies-for-iosipados-and-android-apps"></a>適用於 iOS/iPadOS 和 Android 應用程式的應用程式保護原則

當您建立適用於 iOS/iPadOS 和 Android 應用程式的應用程式保護原則時，您會遵循會產生新應用程式保護原則的新式 Intune 程序流程。

### <a name="create-an-iosipados-or-android-app-protection-policy"></a>建立 iOS/iPadOS 或 Android 應用程式保護原則
1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 在 Intune 入口網站中，選擇 [應用程式]   > [應用程式保護原則]  。 此選取項目會開啟 [應用程式原則]  的詳細資料，讓您從中建立新的原則及編輯現有的原則。
3. 選取 [建立原則]  然後選取 [iOS/iPadOS]  或 [Android]  。 隨即顯示 [建立原則]  窗格。
4. 在 [基本]  頁面上，新增下列值：

    | 值 | 說明 |
    |--------------|------------------------------------------------|
    | Name | 此應用程式保護原則的名稱。 |
    | 說明 | [選擇性] 此應用程式保護原則的描述。 |


    [平台]  值是根據您的上述選擇進行設定。

    ![[建立原則] 窗格 [基本] 頁面的螢幕擷取畫面](~/apps/media/app-protection-policies/app-protection-add-policies-01.png)

5. 按一下 [下一步]  以顯示 [應用程式]  頁面。<br>
    [應用程式]  頁面可讓您選擇要如何將此原則套用至不同裝置上的應用程式。 您必須新增至少一個應用程式。<p>
    
    | 值/選項 | 說明 |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | 鎖定所有裝置類型上的應用程式 | 使用此選項可將原則的目標設為任何管理狀態裝置上的應用程式。 選擇 [否]  ，將特定裝置類型上的應用程式設為目標。 如需相關資訊，請參閱[根據裝置管理狀態來設定應用程式保護原則目標](#target-app-protection-policies-based-on-device-management-state) |
    |     裝置類型 | 使用此選項來指定此原則是否適用於 MDM 受控裝置或非受控裝置。 針對 iOS/iPadOS 應用程式原則，請從 [非受控]  和 [受控]  裝置中選取。 針對 Android 應用程式原則，請從 [非受控]  、[Android 裝置系統管理員]  和 [Android Enterprise]  中選取。  |
    | 公用應用程式 | 按一下 [選取公用應用程式]  以選擇要設為目標的應用程式。 |
    | 自訂應用程式 | 按一下 [選取自訂應用程式]  以根據套件組合識別碼選取要設為目標的自訂應用程式。 |
    
    您所選取的應用程式將會出現在公用和自訂應用程式清單中。 
6. 按一下 [下一步]  以顯示 [資料保護]  頁面。<br>
    此頁面提供資料遺失防護 (DLP) 控制項的設定，包含剪下、複製、貼上，以及另存新檔限制。 這些設定會決定使用者如何與套用此應用程式保護原則之應用程式中的資料互動。

    **資料保護設定**：<br>
    - **iOS/iPadOS 資料保護** - 如需資訊，請參閱 [iOS/iPadOS 應用程式保護原則設定 - 資料保護](~/apps/app-protection-policy-settings-ios.md#data-protection)。
    - **Android 資料保護** - 如需詳細資訊，請參閱 [Android 應用程式保護原則設定 - 資料保護](~/apps/app-protection-policy-settings-android.md#data-protection)。

7. 按一下 [下一步]  以顯示 [存取需求]  頁面。<br>
    此頁面提供的設定可讓您設定使用者必須符合的 PIN 和認證需求，才能存取工作內容中的應用程式。 
 
    **存取需求設定**：<br>
    - **iOS/iPadOS 存取需求** - 如需資訊，請參閱 [iOS/iPadOS 應用程式保護原則設定 - 存取需求](~/apps/app-protection-policy-settings-ios.md#access-requirements)。
    - **Android 存取需求** - 如需詳細資訊，請參閱 [Android 應用程式保護原則設定 - 存取需求](~/apps/app-protection-policy-settings-android.md#access-requirements)。

8. 按一下 [下一步]  以顯示 [條件式啟動]  頁面。<br>
    此頁面提供您設定應用程式保護原則的登入安全性需求的設定。 選取 [設定]  ，並輸入使用者必須符合以登入公司應用程式的 [值]  。 然後選取使用者不符合您的需求時要採取的 [動作]  。 在某些情況下，您可以針對單一設定指定多個動作。

    **條件式啟動設定**：<br>
    - **iOS/iPadOS 條件式啟動** - 如需資訊，請參閱 [iOS/iPadOS 應用程式保護原則設定 - 條件式啟動](~/apps/app-protection-policy-settings-ios.md#conditional-launch)。
    - **Android 條件式啟動** - 如需詳細資訊，請參閱 [Android 應用程式保護原則設定 - 條件式啟動](~/apps/app-protection-policy-settings-android.md#conditional-launch)。

9. 按一下 [下一步]  以顯示 [指派]  頁面。<br>
   [指派]  頁面可讓您將應用程式保護原則指派給使用者群組。

10. 按一下 [下一步:  檢閱 + 建立]，以檢閱您為此應用程式保護原則輸入的值和設定。

11. 完成後，請按一下 [建立]  ，在 Intune 中建立應用程式保護原則。 

    > [!TIP]
    > 只有在工作內容中使用應用程式時，才會強制執行這些原則設定。 當終端使用者使用應用程式來執行個人工作時，不會受到這些原則的影響。 請記得，當您建立新檔案時，它會被視為個人檔案。 

使用者可以從應用程式市集或 Google Play 下載應用程式。 如需詳細資訊，請參閱：
* [當 Android 應用程式交由應用程式防護原則管理時的行為](../fundamentals/end-user-mam-apps-android.md)
* [當 iOS 應用程式交由應用程式保護原則管理時的行為](../fundamentals/end-user-mam-apps-ios.md)

## <a name="change-existing-policies"></a>變更現有的原則
您可以編輯現有的原則，並將它套用到目標使用者。 不過，當您變更現有的原則時，已登入應用程式的使用者將有 8 小時看不到變更。

若要立即查看變更的影響，終端使用者必須登出應用程式再重新登入。

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>變更與原則相關聯的應用程式清單

1. 在 [應用程式防護原則]  窗格中，選取您想要變更的原則。

2. 在 [Intune 應用程式防護]  窗格中，選取 [屬性]  。

3. 在標題為 [應用程式]  的區段旁邊，選取 [編輯]  。

4. [應用程式]  頁面可讓您選擇要如何將此原則套用至不同裝置上的應用程式。 您必須新增至少一個應用程式。<p>
    
    | 值/選項 | 說明 |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | 鎖定所有裝置類型上的應用程式 | 使用此選項可將原則的目標設為任何管理狀態裝置上的應用程式。 選擇 [否]  ，將特定裝置類型上的應用程式設為目標。 如需相關資訊，請參閱[根據裝置管理狀態來設定應用程式保護原則目標](#target-app-protection-policies-based-on-device-management-state) |
    |     裝置類型 | 使用此選項來指定此原則是否適用於 MDM 受控裝置或非受控裝置。 針對 iOS/iPadOS 應用程式原則，請從 [非受控]  和 [受控]  裝置中選取。 針對 Android 應用程式原則，請從 [非受控]  、[Android 裝置系統管理員]  和 [Android Enterprise]  中選取。  |
    | 公用應用程式 | 按一下 [選取公用應用程式]  以選擇要設為目標的應用程式。 |
    | 自訂應用程式 | 按一下 [選取自訂應用程式]  以根據套件組合識別碼選取要設為目標的自訂應用程式。 |

    您所選取的應用程式將會出現在公用和自訂應用程式清單中。 

5. 按一下 [檢閱 + 建立]  以檢閱針對此原則所選取的應用程式。

6. 完成後，請按一下 [儲存]  來更新應用程式保護原則。
 
#### <a name="to-change-the-list-of-user-groups"></a>變更使用者群組清單

1. 在 [應用程式防護原則]  窗格中，選取您想要變更的原則。

2. 在 [Intune 應用程式防護]  窗格中，選取 [屬性]  。

3. 在標題為 [指派]  的區段旁邊，選取 [編輯]  。

4. 若要將新的使用者群組新增至原則，在 [包含]  索引標籤選擇 [選取要包含的群組]  ，並選取使用者群組。 選擇 [選取]  來新增群組。 

5. 若要排除使用者群組，在 [排除]  索引標籤上，選取 [選取要排除的群組]  ，並選取使用者群組。 選擇 [選取]  以移除使用者群組。  

6. 若要刪除先前新增的群組，請在 [包含]  或 [排除]  索引標籤上，選取省略符號 (...)，然後選取 [刪除]  。

7. 按一下 [檢閱 + 建立]  以檢閱針對此原則所選取的使用者群組。

8. 完成對指派的變更之後，選取 [儲存]  來儲存設定，並將原則部署到新的一組使用者。 如果您在儲存設定之前選取 [取消]  ，您將會捨棄您對 [包含]  和 [排除]  索引標籤所做的所有變更。

### <a name="to-change-policy-settings"></a>變更原則設定

1. 在 [應用程式防護原則]  窗格中，選取您想要變更的原則。

2. 在 [Intune 應用程式防護]  窗格中，選取 [屬性]  。

3. 在您想要變更設定之對應區段的旁邊，選取 [編輯]  。 然後將設定變更為新的值。

7. 按一下 [檢閱 + 建立]  以檢閱針對此原則所更新的設定。

4. 選取 [儲存]  以儲存您的變更。 重複此程序，選取設定區域並進行修改，然後儲存變更，直到您的所有變更都已完成。 接著，您即可以關閉 [Intune 應用程式防護 - 屬性]  窗格。 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>根據裝置管理狀態來設定應用程式保護原則目標
在許多組織中，同時允許使用者使用 Intune「行動裝置管理」(MDM) 受控裝置 (例如公司擁有的裝置) 及僅以 Intune 應用程式防護原則保護的非受控裝置，是很常見的情況。 非受控裝置通常被視為「攜帶您自己的裝置」 (BYOD)。

因為 Intune 應用程式防護原則會以使用者的身分識別為目標，使用者的防護設定可以同時套用至已註冊 (MDM 受控) 和未註冊的裝置 (非 MDM)。 因此，您可以讓 Intune 應用程式保護原則以已註冊或未註冊 Intune 的 iOS/iPadOS 與 Android 裝置為目標。 您可以有一個適用於非受控裝置的保護原則來提供嚴格的資料外洩防護 (DLP) 控制，並有另一個適用於 MDM 受控裝置的保護原則來提供可能較寬鬆的 DLP 控制。 如需這如何在個人 Android Enterprise 裝置上運作的詳細資訊，請參閱[應用程式保護原則與工作設定檔](android-deployment-scenarios-app-protection-work-profiles.md)。

若要建立這些原則，請在 Intune 主控台中瀏覽至 [應用程式]   > [應用程式保護原則]  ，然後選取 [建立原則]  。 您也可以編輯現有的應用程式保護原則。 若要將應用程式保護原則同時套用至受控和非受控裝置，請瀏覽至 [應用程式]  頁面，並確認將 [鎖定所有裝置類型上的應用程式]  設定為 [是]  (預設值)。 如果您想要根據管理狀態進行更精細的指派，請將 [鎖定所有裝置類型上的應用程式]  設定為 [否]  。 

### <a name="device-types"></a>裝置類型

- **非受控**：非受控裝置是指尚未檢測到 Intune MDM 管理的裝置。 這包含由協力廠商 MDM 廠商所管理的裝置。
- **Intune 受控裝置**：受控裝置由 Intune MDM 管理。
- **Android 裝置系統管理員**：使用 Android 裝置系統管理員 API 的 Intune 受控裝置。
- **Android Enterprise**：使用 Android Enterprise 工作設定檔或 Android Enterprise 完整裝置管理的 Intune 受控裝置。

> [!NOTE]
> 無論選擇哪種裝置類型，Android 裝置都將提示您安裝 Intune 公司入口網站應用程式。 例如，如果您選擇 [Android Enterprise]，則系統仍將提示使用非受控 Android 裝置的使用者。

針對 iOS/iPadOS，需要額外的應用程式組態設定，才能將應用程式保護原則 (APP) 設定其目標設為 Intune 已註冊裝置上的應用程式：

- **IntuneMAMUPN** 必須針對所有 MDM 受控應用程式進行設定。 如需詳細資訊，請參閱[如何使用 Microsoft Intune 管理 iOS/iPadOS 應用程式之間的資料傳輸](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm)。
- **IntuneMAMDeviceID** 必須針對所有協力廠商及企業營運 MDM 受控應用程式進行設定。 **IntuneMAMDeviceID** 應設為裝置識別碼權杖。 例如 `key=IntuneMAMDeviceID, value={{deviceID}}`。 如需詳細資訊，請參閱[為受控 iOS/iPadOS 裝置新增應用程式設定原則](app-configuration-policies-use-ios.md)。
- 若只有設定 **IntuneMAMDeviceID**，則 Intune 應用程式會將裝置視為非受控。

> [!NOTE]
> 如需關於以裝置管理狀態為基礎之應用程式保護原則的特定 iOS/iPadOS 支援資訊，請參閱[根據管理狀態將 MAM 保護原則設為目標](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state)。

## <a name="policy-settings"></a>原則設定
若要查看 iOS/iPadOS 與 Android 的完整原則設定清單，請選取下列其中一個連結︰

- [iOS/iPadOS policies](app-protection-policy-settings-ios.md)
- [Android 原則](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>後續步驟
[監視合規性和使用者狀態](app-protection-policies-monitor.md)

## <a name="see-also"></a>請參閱
* [當 Android 應用程式交由應用程式防護原則管理時的行為](../fundamentals/end-user-mam-apps-android.md)
* [當 iOS/iPadOS 應用程式交由應用程式保護原則管理時的行為](../fundamentals/end-user-mam-apps-ios.md)
