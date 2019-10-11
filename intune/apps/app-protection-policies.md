---
title: 建立及部署應用程式保護原則
titleSuffix: Microsoft Intune
description: 本主題描述如何建立及指派 Microsoft Intune 應用程式保護原則 (簡稱 APP)。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4958a35f3a83fecffacf26421e4c1d797f45ddaa
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940384"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>如何建立及部署應用程式保護原則

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

了解如何建立及指派 Microsoft Intune 應用程式防護原則給使用者。 本主題也會描述如何變更現有的原則。

## <a name="before-you-begin"></a>開始之前

無論裝置是否由 Intune 管理，都能對裝置上執行的應用程式套用應用程式防護原則。 如需應用程式防護原則運作方式，以及 Intune 應用程式防護原則支援案例的詳細描述，請參閱[什麼是 Microsoft Intune 應用程式防護原則？](app-protection-policy.md)

如果您正在尋找 MAM 支援之應用程式的清單，請參閱 [MAM 應用程式清單](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。

如需有關將您組織的企業營運 (LOB) 應用程式新增到 Microsoft Intune 以準備應用程式保護原則的資訊，請參閱[將應用程式新增至 Microsoft Intune](apps-add.md)。

## <a name="create-an-app-protection-policy"></a>建立應用程式保護原則
1. 在 Intune 入口網站中，選取 [用戶端應用程式]   > [應用程式防護原則]  。 此選取項目會開啟 [應用程式原則]  的詳細資料，讓您從中建立新的原則及編輯現有的原則。
2. 選取[建立原則]  。

   ![[新增原則] 刀鋒視窗的螢幕擷取畫面](./media/app-protection-policies/app-protection-add-policy.png)

3. 為您的原則指定名稱、新增簡短描述並選取平台類型。 您可以針對每部平台建立多項原則。

4. 選取 [應用程式]  以開啟 [應用程式]  刀鋒視窗，其中會顯示可用的應用程式清單。 請從清單中選取要與所建立之原則建立關聯的一或多個應用程式。 請至少選取一個應用程式以建立原則。  

5. 選取應用程式後，請選擇 [選取]  來儲存您的選擇。

6. 在 [新增原則]  刀鋒視窗上，選取 [設定必要設定]  以開啟 [設定]  。

   原則設定有三個類別：
   - **資料保護** - 此群組包含資料遺失防護 (DLP) 控制項，例如剪下、複製、貼上，以及另存新檔限制。 這些設定會決定使用者如何與應用程式中的資料互動。
   - **存取需求** - 此群組包含每個應用程式的 PIN 選項，用於決定終端使用者如何在工作環境中存取應用程式。  
   - **條件式啟動** - 此群組包含最低作業系統設定、越獄和 Root 裝置偵測以及離線寬限期等設定。

   原則設定中的預設值可協助您開始使用。 如果預設值符合您的需求，則不需要進行任何變更。

   > [!TIP]
   > 只有在工作內容中使用應用程式時，才會強制執行這些原則設定。 當終端使用者使用應用程式來執行個人工作時，不會受到這些原則的影響。 請記得，當您建立新檔案時，它會被視為個人檔案。 

7. 選取 [確定]  以儲存這項設定。 現在您已回到 [新增原則]  刀鋒視窗。
8. 選取 [建立]  以建立原則並儲存您的設定。

在您明確執行此操作之前，您建立的新原則不會部署至任何使用者。 若要部署原則，請參閱[＜將原則部署給使用者＞](app-protection-policies.md#deploy-a-policy-to-users)。

## <a name="deploy-a-policy-to-users"></a>將原則部署給使用者

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
* [當 iOS 應用程式交由應用程式保護原則管理時的行為](../fundamentals/end-user-mam-apps-ios.md)

## <a name="change-existing-policies"></a>變更現有的原則
您可以編輯現有的原則，並將它套用到目標使用者。 不過，當您變更現有的原則時，已登入應用程式的使用者將有 8 小時看不到變更。

若要立即查看變更的影響，終端使用者必須登出應用程式再重新登入。

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>變更與原則相關聯的應用程式清單

1. 在 [應用程式防護原則]  窗格中，選取您想要變更的原則。

2. 在 [Intune 應用程式防護]  窗格中，選取 [目標應用程式]  以開啟應用程式清單。

3. 在清單中移除或新增應用程式，然後選取**儲存**圖示儲存您的變更。

### <a name="to-change-the-list-of-user-groups"></a>變更使用者群組清單


1. 在 [應用程式防護原則]  窗格中，選取您想要變更的原則。

2. 在 [Intune 應用程式防護]  窗格中，選取 [指派]  來開啟 [Intune 應用程式防護 - 指派]  窗格，該窗格會顯示具有這項原則的目前使用者群組清單。

3. 若要將新的使用者群組新增至原則，在 [包含]  索引標籤選擇 [選取要包含的群組]  ，並選取使用者群組。 選擇 [選取]  來新增群組。 

4. 若要排除使用者群組，在 [排除]  索引標籤上，選取 [選取要排除的群組]  ，並選取使用者群組。 選擇 [選取]  以移除使用者群組。  

5. 若要刪除先前新增的群組，請在 [包含]  或 [排除]  索引標籤上，選取省略符號 (...)，然後選取 [刪除]  。 

5. 完成對指派的變更之後，選取 [儲存]  來儲存設定，並將原則部署到新的一組使用者。 如果您在儲存設定之前選取 [捨棄]  ，您將會捨棄您對 [包含]  和 [排除]  索引標籤所做的所有變更。

### <a name="to-change-policy-settings"></a>變更原則設定

1. 在 [應用程式防護原則]  窗格中，選擇您想要變更的原則。

2. 在 [Intune 應用程式防護]  窗格中，選取 [屬性]  以開啟您可以編輯之設定區域的清單。 

3. 以您想要變更的設定來選取設定區域，例如 [資料重新配置]  或 [存取需求]  。 然後將設定變更為新的值。

4. 選取**儲存**圖示以儲存您的變更。 重複此程序，選取設定區域並進行修改，然後儲存變更，直到您的所有變更都已完成。 接著，您即可以關閉 [Intune 應用程式防護 - 屬性]  窗格。 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>根據裝置管理狀態來設定應用程式保護原則目標
在許多組織中，同時允許使用者使用 Intune「行動裝置管理」(MDM) 受控裝置 (例如公司擁有的裝置) 及僅以 Intune 應用程式防護原則保護的非受控裝置，是很常見的情況。 非受控裝置通常被視為「攜帶您自己的裝置」 (BYOD)。

因為 Intune 應用程式防護原則會以使用者的身分識別為目標，使用者的防護設定可以同時套用至已註冊 (MDM 受控) 和未註冊的裝置 (非 MDM)。 因此，您可以讓 Intune 應用程式防護原則以 Intune 已註冊或未註冊 iOS 及 Android 裝置為目標。 您可以有一個適用於非受控裝置的保護原則來提供嚴格的資料外洩防護 (DLP) 控制，並有另一個適用於 MDM 受控裝置的保護原則來提供可能較寬鬆的 DLP 控制。 如需這如何在個人 Android Enteprise 裝置上運作的詳細資訊，請參閱[應用程式保護原則與工作設定檔](android-deployment-scenarios-app-protection-work-profiles.md)。

若要建立這些原則，請在 Intune 主控台中瀏覽至 [用戶端應用程式]   > [應用程式防護]  ，然後選取 [新增原則]  。 您也可以編輯現有的應用程式保護原則。 若要將應用程式保護原則同時套用至受控和非受控裝置，請確認將 [目標為所有應用程式類型]  設定為 [是]  (預設值)。 如果您想要根據管理狀態進行更精細的指派，請將 [目標為所有應用程式類型]  設定為 [否]  。 

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
