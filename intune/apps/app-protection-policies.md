---
title: 建立及部署應用程式保護原則
titleSuffix: Microsoft Intune
description: 本主題描述如何建立及指派 Microsoft Intune 應用程式保護原則 (簡稱 APP)。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
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
ms.openlocfilehash: a8e105dae43c4e7139c8e44a8c6535baebe31cc4
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585490"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>如何建立及部署應用程式保護原則

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

了解如何建立及指派 Microsoft Intune 應用程式保護原則 (APP) 給您組織的使用者。 本主題也會描述如何變更現有的原則。

## <a name="before-you-begin"></a>開始之前

無論裝置是否由 Intune 管理，都能對裝置上執行的應用程式套用應用程式防護原則。 如需應用程式防護原則運作方式，以及 Intune 應用程式防護原則支援案例的詳細描述，請參閱[什麼是 Microsoft Intune 應用程式防護原則？](app-protection-policy.md)

如果您正在尋找 MAM 支援之應用程式的清單，請參閱 [MAM 應用程式清單](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。

如需有關將您組織的企業營運 (LOB) 應用程式新增到 Microsoft Intune 以準備應用程式保護原則的資訊，請參閱[將應用程式新增至 Microsoft Intune](apps-add.md)。

目前，建立應用程式保護原則的程序流程會根據平台而有所不同：
- 適用於 iOS/iPadOS 和 Android 應用程式的應用程式保護原則
- 適用於 Windows 10 應用程式的應用程式保護原則

## <a name="app-protection-policies-for-iosipados-and-android-apps"></a>適用於 iOS/iPadOS 和 Android 應用程式的應用程式保護原則

當您建立適用於 iOS/iPadOS 和 Android 應用程式的應用程式保護原則時，您會遵循會產生新應用程式保護原則的新式 Intune 程序流程。

### <a name="create-an-iosipados-or-android-app-protection-policy"></a>建立 iOS/iPadOS 或 Android 應用程式保護原則
1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在 Intune 入口網站中，選擇 [用戶端應用程式]   > [應用程式保護原則]  。 此選取項目會開啟 [應用程式原則]  的詳細資料，讓您從中建立新的原則及編輯現有的原則。
3. 選取 [建立原則]  然後選取 [iOS/iPadOS]  或 [Android]  。 隨即顯示 [建立原則]  刀鋒視窗。
4. 在 [基本]  頁面上，新增下列值：

    | 值 | 說明 |
    |--------------|------------------------------------------------|
    | 名稱 | 此應用程式保護原則的名稱。 |
    | 說明 | [選擇性] 此應用程式保護原則的描述。 |


    [平台]  值是根據您的上述選擇進行設定。

    ![[建立原則] 刀鋒視窗 [基本] 頁面的螢幕擷取畫面](~/apps/media/app-protection-policies/app-protection-add-policies-01.png)

5. 按一下 [下一步]  以顯示 [應用程式]  頁面。<br>
    [應用程式]  頁面可讓您選擇要如何將此原則套用至不同裝置上的應用程式。 您必須新增至少一個應用程式。<p>
    
    | 值/選項 | 說明 |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | 鎖定所有裝置類型上的應用程式 | 使用此選項可將原則的目標設為任何管理狀態裝置上的應用程式。 選擇 [否]  ，將特定裝置類型上的應用程式設為目標。 |
    |     裝置類型 | 使用此選項來指定此原則是否適用於 MDM 受控裝置或非受控裝置。 針對 iOS 應用程式原則，請從 [非受控]  和 [受控]  裝置中選取。 針對 Android 應用程式原則，請從 [非受控]  、[Android 裝置系統管理員]  和 [Android Enterprise]  中選取。  |
    | 公用應用程式 | 按一下 [選取公用應用程式]  以選擇要設為目標的應用程式。 |
    | 自訂應用程式 | 按一下 [選取自訂應用程式]  以根據套件組合識別碼選取要設為目標的自訂應用程式。 |
    
    您所選取的應用程式將會出現在公用和自訂應用程式清單中。 
6. 按一下 [下一步]  以顯示 [資料保護]  頁面。<br>
    此頁面提供資料遺失防護 (DLP) 控制項的設定，包含剪下、複製、貼上，以及另存新檔限制。 這些設定會決定使用者如何與套用此應用程式保護原則之應用程式中的資料互動。

    **資料保護設定**：<br>
    - **iOS/iPadOS 資料保護** - 如需詳細資訊，請參閱 [iOS 應用程式保護原則設定 - 資料保護](~/apps/app-protection-policy-settings-ios.md#data-protection)。
    - **Android 資料保護** - 如需詳細資訊，請參閱 [Android 應用程式保護原則設定 - 資料保護](~/apps/app-protection-policy-settings-android.md#data-protection)。

7. 按一下 [下一步]  以顯示 [存取需求]  頁面。<br>
    此頁面提供的設定可讓您設定使用者必須符合的 PIN 和認證需求，才能存取工作內容中的應用程式。 
 
    **存取需求設定**：<br>
    - **iOS/iPadOS 存取需求** - 如需詳細資訊，請參閱 [iOS 應用程式保護原則設定 - 存取需求](~/apps/app-protection-policy-settings-ios.md#access-requirements)。
    - **Android 存取需求** - 如需詳細資訊，請參閱 [Android 應用程式保護原則設定 - 存取需求](~/apps/app-protection-policy-settings-android.md#access-requirements)。

8. 按一下 [下一步]  以顯示 [條件式啟動]  頁面。<br>
    此頁面提供您設定應用程式保護原則的登入安全性需求的設定。 選取 [設定]  ，並輸入使用者必須符合以登入公司應用程式的 [值]  。 然後選取使用者不符合您的需求時要採取的 [動作]  。 在某些情況下，您可以針對單一設定指定多個動作。

    **條件式啟動設定**：<br>
    - **iOS/iPadOS 條件式啟動** - 如需詳細資訊，請參閱 [iOS 應用程式保護原則設定 - 條件式啟動](~/apps/app-protection-policy-settings-ios.md#conditional-launch)。
    - **Android 條件式啟動** - 如需詳細資訊，請參閱 [Android 應用程式保護原則設定 - 條件式啟動](~/apps/app-protection-policy-settings-android.md#conditional-launch)。

7. 按一下 [下一步]  以顯示 [指派]  頁面。<br>
   [指派]  頁面可讓您將應用程式保護原則指派給使用者群組。 
8. 按一下 [下一步:  檢閱 + 建立]，以檢閱您為此應用程式保護原則輸入的值和設定。
9. 完成後，請按一下 [建立]  ，在 Intune 中建立應用程式保護原則。 

## <a name="app-protection-policies-for-windows-10-apps"></a>適用於 Windows 10 應用程式的應用程式保護原則

當您建立適用於 Windows 10 應用程式的應用程式保護原則時，您將會遵循傳統的 Intune 程序流程。

### <a name="create-a-windows-10-app-protection-policy"></a>建立 Windows 10 應用程式保護原則
1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在 Intune 入口網站中，選擇 [用戶端應用程式]   > [應用程式保護原則]  。 此選取項目會開啟 [應用程式原則]  的詳細資料，讓您從中建立新的原則及編輯現有的原則。
3. 選取 [建立原則]  。

    <img alt="Screenshot of the 'Create policy' blade for Windows 10" src="~/apps/media/app-protection-policies/app-protection-add-policy.png" width="350">

4. 為您的原則指定名稱、新增簡短描述並選取平台類型。 您可以針對每部平台建立多項原則。

4. 您可以選擇 [以所有應用程式類型為目標]  。 此選項可讓您將原則的目標設為任何管理狀態裝置上的應用程式。 在原則衝突解決期間，如果使用者有以特定管理狀態為目標的原則，則會取代此設定。 如需詳細資訊，請參閱[根據裝置管理狀態將應用程式保護原則設為目標](~/apps/app-protection-policies.md#target-app-protection-policies-based-on-device-management-state)。

5. 選取 [應用程式]  以開啟 [應用程式]  刀鋒視窗，其中會顯示可用的應用程式清單。 請從清單中選取要與所建立之原則建立關聯的一或多個應用程式。 請至少選取一個應用程式以建立原則。  

6. 選取應用程式後，請選擇 [選取]  來儲存您的選擇。

7. 在 [新增原則]  刀鋒視窗上，選取 [設定必要設定]  以開啟 [設定]  。

   原則設定有三個類別：
   - **資料保護** - 此群組包含資料遺失防護 (DLP) 控制項，例如剪下、複製、貼上，以及另存新檔限制。 這些設定會決定使用者如何與應用程式中的資料互動。
   - **存取需求** - 此群組包含每個應用程式的 PIN 選項，用於決定終端使用者如何在工作環境中存取應用程式。  
   - **條件式啟動** - 此群組包含最低作業系統設定、越獄和 Root 裝置偵測以及離線寬限期等設定。

   原則設定中的預設值可協助您開始使用。 如果預設值符合您的需求，則不需要進行任何變更。

   > [!TIP]
   > 只有在工作內容中使用應用程式時，才會強制執行這些原則設定。 當終端使用者使用應用程式來執行個人工作時，不會受到這些原則的影響。 請記得，當您建立新檔案時，它會被視為個人檔案。 

8. 選取 [確定]  以儲存這項設定。 現在您已回到 [新增原則]  刀鋒視窗。
9. 選取 [建立]  以建立原則並儲存您的設定。

在您明確執行此操作之前，您建立的新 Windows 10 原則不會指派給任何使用者。 若要指派 Windows 10 原則，請參閱[將 Windows 10 原則指派給使用者](~/apps/app-protection-policies.md#assign-a-windows-10-policy-to-users)

### <a name="assign-a-windows-10-policy-to-users"></a>將 Windows 10 原則指派給使用者 

1. 在 [應用程式防護原則]  窗格中，選取原則。

2. 在 *[Intune 應用程式防護]  窗格中，選取 [指派]  以開啟 [Intune 應用程式防護 - 指派]  窗格。 在 [包含]  索引標籤上，選取 [選取要包含的群組]  。 

   ![顯示 [選取要包含的群組] 功能表的 [指派] 窗格螢幕擷取畫面](./media/app-protection-policies/app-protection-policy-add-users.png)

3. 會顯示 **Azure Active Directory** 中的所有安全性群組清單。 請選取要套用這項原則的使用者群組，然後選擇 [選取]  。 

    ![顯示 Azure AD 使用者清單的 [新增使用者群組] 窗格螢幕擷取畫面](./media/app-protection-policies/azure-ad-user-group-list.png)

4. 您將群組包含及排除之後，請選取 [儲存]  以儲存設定，並將原則部署至使用者。 如果您在儲存設定之前選取 [捨棄]  ，您將會捨棄您對 [包含]  和 [排除]  索引標籤所做的所有變更。   
 
     ![顯示儲存和捨棄選項的螢幕擷取畫面](./media/app-protection-policies/save-assignment.png)
  
您現在已建立原則並將其部署給使用者。

只有獲指派 Microsoft Intune 授權的使用者才會受此原則影響。 已選取安全性群組中的使用者若無指派的 Intune 授權，則不會受到影響。

>[!IMPORTANT]
> 如果您使用 Intune 和 Configuration Manager 來管理您的裝置，則只會將原則套用至您選取之群組中的直屬使用者。 而不會影響巢狀於您選取之群組中的子群組成員。

使用者可以從應用程式市集或 Google Play 下載應用程式。 如需詳細資訊，請參閱：
* [當 Android 應用程式交由應用程式防護原則管理時的行為](../fundamentals/end-user-mam-apps-android.md)
* [當 iOS 應用程式交由應用程式防護原則管理時的行為](../fundamentals/end-user-mam-apps-ios.md)

### <a name="change-existing-windows-10-policies"></a>變更現有的 Windows 10 原則
您可以編輯現有的原則，並將它套用到目標使用者。 不過，當您變更現有的原則時，已登入應用程式的使用者將有 8 小時看不到變更。

若要立即查看變更的影響，終端使用者必須登出應用程式再重新登入。

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>變更與原則相關聯的應用程式清單

1. 在 [應用程式防護原則]  窗格中，選取您想要變更的原則。

2. 在 [Intune 應用程式防護]  窗格中，選取 [目標應用程式]  以開啟應用程式清單。

3. 在清單中移除或新增應用程式，然後選取**儲存**圖示儲存您的變更。

#### <a name="to-change-the-list-of-user-groups"></a>變更使用者群組清單

1. 在 [應用程式防護原則]  窗格中，選取您想要變更的原則。

2. 在 [Intune 應用程式防護]  窗格中，選取 [指派]  來開啟 [Intune 應用程式防護 - 指派]  窗格，該窗格會顯示具有這項原則的目前使用者群組清單。

3. 若要將新的使用者群組新增至原則，在 [包含]  索引標籤選擇 [選取要包含的群組]  ，並選取使用者群組。 選擇 [選取]  來新增群組。 

4. 若要排除使用者群組，在 [排除]  索引標籤上，選取 [選取要排除的群組]  ，並選取使用者群組。 選擇 [選取]  以移除使用者群組。  

5. 若要刪除先前新增的群組，請在 [包含]  或 [排除]  索引標籤上，選取省略符號 (...)，然後選取 [刪除]  。 

5. 完成對指派的變更之後，選取 [儲存]  來儲存設定，並將原則部署到新的一組使用者。 如果您在儲存設定之前選取 [捨棄]  ，您將會捨棄您對 [包含]  和 [排除]  索引標籤所做的所有變更。

### <a name="to-change-windows-10-policy-settings"></a>變更 Windows 10 原則設定

1. 在 [應用程式防護原則]  窗格中，選擇您想要變更的原則。

2. 在 [Intune 應用程式防護]  窗格中，選取 [屬性]  以開啟您可以編輯之設定區域的清單。 

3. 以您想要變更的設定來選取設定區域，例如 [資料重新配置]  或 [存取需求]  。 然後將設定變更為新的值。

4. 選取**儲存**圖示以儲存您的變更。 重複此程序，選取設定區域並進行修改，然後儲存變更，直到您的所有變更都已完成。 接著，您即可以關閉 [Intune 應用程式防護 - 屬性]  窗格。 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>根據裝置管理狀態來設定應用程式保護原則目標
在許多組織中，同時允許使用者使用 Intune「行動裝置管理」(MDM) 受控裝置 (例如公司擁有的裝置) 及僅以 Intune 應用程式防護原則保護的非受控裝置，是很常見的情況。 非受控裝置通常被視為「攜帶您自己的裝置」 (BYOD)。

因為 Intune 應用程式防護原則會以使用者的身分識別為目標，使用者的防護設定可以同時套用至已註冊 (MDM 受控) 和未註冊的裝置 (非 MDM)。 因此，您可以讓 Intune 應用程式防護原則以 Intune 已註冊或未註冊 iOS 及 Android 裝置為目標。 您可以有一個適用於非受控裝置的保護原則來提供嚴格的資料外洩防護 (DLP) 控制，並有另一個適用於 MDM 受控裝置的保護原則來提供可能較寬鬆的 DLP 控制。 如需這如何在個人 Android Enterprise 裝置上運作的詳細資訊，請參閱[應用程式保護原則與工作設定檔](android-deployment-scenarios-app-protection-work-profiles.md)。

若要建立這些原則，請在 Intune 主控台中瀏覽至 [用戶端應用程式]   > [應用程式防護]  ，然後選取 [新增原則]  。 您也可以編輯現有的應用程式保護原則。 若要將應用程式保護原則同時套用至受控和非受控裝置，請瀏覽至 [應用程式]  頁面，並確認將 [鎖定所有裝置類型上的應用程式]  設定為 [是]  (預設值)。 如果您想要根據管理狀態進行更精細的指派，請將 [鎖定所有裝置類型上的應用程式]  設定為 [否]  。 

![顯示 [目標為所有應用程式類型] 的 [新增原則] 刀鋒視窗螢幕擷取畫面](./media/app-protection-policies/app-protection-policies-target-all.png)

### <a name="app-types"></a>應用程式類型

- **非受控裝置上的應用程式**：非受控裝置是指尚未檢測到 Intune MDM 管理的裝置。 這包括第 3 方 MDM 廠商。
- **Intune 受控裝置上的應用程式**：受控裝置由 Intune MDM 管理。
- **Android 工作設定檔中的應用程式**：已註冊為 Android Enterprise 工作設定檔裝置的受控裝置。

> 請注意，無論選擇哪種應用程式類型，Android 裝置都將提示您安裝 Intune 公司入口網站應用程式。 例如，如果您選擇 [Intune 受控裝置上的應用程式]，則仍將提示使用非受控 Android 裝置的使用者。

針對 iOS，需要額外的應用程式組態設定，才能將應用程式保護原則 (APP) 設定的目標設為 Intune 已註冊裝置上的應用程式：

- **IntuneMAMUPN** 必須針對所有 MDM 受控應用程式進行設定。 如需詳細資訊，請參閱[如何使用 Microsoft Intune 管理 iOS 應用程式之間的資料傳輸](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm)。
- **IntuneMAMDeviceID** 必須針對所有協力廠商及 LOB MDM 受控應用程式進行設定。 **IntuneMAMDeviceID** 應設為裝置識別碼權杖。 例如，`key=IntuneMAMDeviceID, value={{deviceID}}` 。 如需詳細資訊，請參閱[為受控 iOS 裝置新增應用程式設定原則](app-configuration-policies-use-ios.md)。
- 若只有設定 **IntuneMAMDeviceID**，則 Intune 應用程式會將裝置視為非受控。

> [!NOTE]
> 針對以裝置管理狀態為基礎的應用程式保護原則，如需特定 iOS 的支援資訊，請參閱[根據管理狀態來設定目標的 MAM 保護原則](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state-)。

## <a name="policy-settings"></a>原則設定
若要查看 iOS 和 Android 的原則設定的完整清單，請選取下列其中一個連結︰

- [iOS 原則](app-protection-policy-settings-ios.md)
- [Android 原則](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>後續步驟
[監視合規性和使用者狀態](app-protection-policies-monitor.md)

## <a name="see-also"></a>請參閱
* [當 Android 應用程式交由應用程式防護原則管理時的行為](../fundamentals/end-user-mam-apps-android.md)
* [當 iOS 應用程式交由應用程式防護原則管理時的行為](../fundamentals/end-user-mam-apps-ios.md)
