---
title: 建立及部署應用程式保護原則
titleSuffix: Microsoft Intune
description: 了解如何建立及指派 Microsoft Intune 應用程式防護原則。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3a66ed41442e89ed40850f5b9cd56cbc004a43d0
ms.sourcegitcommit: 8b4f5685dc7f41f5e967a8f9d0627707a36dbe93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2018
ms.locfileid: "40251491"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>如何建立及部署應用程式保護原則

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

了解如何建立及指派 Microsoft Intune 應用程式防護原則給使用者。 本主題也會描述如何變更現有的原則。

## <a name="before-you-begin"></a>開始之前

無論裝置是否交由 Intune 管理，都能對裝置上執行的應用程式套用應用程式保護原則。 如需應用程式保護原則的運作方式，以及 Intune 應用程式保護原則支援案例詳細說明，請參閱[什麼是 Microsoft Intune 應用程式保護原則？](app-protection-policy.md)。

如果您正在尋找 MAM 支援之應用程式的清單，請參閱 [MAM 應用程式清單](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。

如需有關將您組織的企業營運 (LOB) 應用程式新增到 Microsoft Intune 以準備應用程式保護原則的資訊，請參閱[將應用程式新增至 Microsoft Intune](apps-add.md)。

##  <a name="create-an-app-protection-policy"></a>建立應用程式保護原則
1. 在 [行動應用程式] 工作負載中，從 [管理] 區段中選取 [應用程式防護原則]。 此選取項目會開啟 [應用程式原則] 的詳細資料，讓您從中建立新的原則及編輯現有的原則。
2. 選擇 **[新增原則]**。

   ![[新增原則] 刀鋒視窗的螢幕擷取畫面](./media/app-protection-add-policy.png)

3. 為您的原則鍵入名稱、新增簡短描述並選取平台類型。 如需要，您可以針對每個平台建立多項原則。

4. 選擇 [應用程式] 以開啟 [應用程式]  刀鋒視窗，其中會顯示可用的應用程式清單。 請從清單中選取要與所建立之原則建立關聯的一或多個應用程式。
5. 選取應用程式後，請選擇 [選取] 來儲存您的選擇。

    > [!IMPORTANT]
    > 您至少必須選取一個應用程式，才能建立原則。

6. 在 [新增原則] 刀鋒視窗上，選擇 [設定必要設定] 以開啟 [設定]。

   原則設定分為兩類：[資料重新配置] 和 [存取]。  資料重新配置原則適用於應用程式的資料移入和移出。 存取原則決定終端使用者如何存取工作內容中的應用程式。
   原則設定中的預設值可協助您開始使用。 如果預設值符合您的需求，則不需要進行任何變更。

   > [!TIP]
   > 只有在工作內容中使用應用程式時，才會強制執行這些原則設定。 當終端使用者使用應用程式來執行個人工作時，不會受到這些原則的影響。

7. 選擇 [確定] 儲存此設定。 現在您已回到 [新增原則]  窗格。 選擇 [建立] 建立原則並儲存您的設定。
8. 選擇 [確定] 儲存此設定。 現在您已回到 [新增原則]  刀鋒視窗。
9. 選擇 [建立] 建立原則並儲存您的設定。

當您如先前程序中所述完成建立原則時，該原則不會部署給任何使用者。 若要部署原則，請參閱[＜將原則部署給使用者＞](app-protection-policies.md#deploy-a-policy-to-users)。

## <a name="deploy-a-policy-to-users"></a>將原則部署給使用者


1. 在 [應用程式防護原則] 窗格中，選取原則。

1. 在 [原則] 窗格中，選擇 [指派]，這會開啟 [Intune 應用程式防護 - 指派] 窗格。 在 [指派] 窗格中選擇 [選取要包含的群組]，來開啟 [選取要包含的群組] 窗格。

   ![將 [選取要包含的群組] 功能表選項反白之指派窗格的螢幕擷取畫面](./media/app-protection-policy-add-users.png)

2.  [新增使用者群組]  窗格中會顯示使用者群組清單。 此清單會顯示 **Azure Active Directory**中的所有安全性群組。 請選取要套用此原則的使用者群組，然後選擇 [選取]。 選擇 [選取] 可將原則部署給使用者。

    ![顯示 Azure Active Directory 使用者清單的 [新增使用者群組] 窗格的螢幕擷取畫面](./media/azure-ad-user-group-list.png)

您現在已建立原則並將其部署給使用者。

只有獲指派 Microsoft Intune 授權的使用者才會受此原則影響。 已選取安全性群組中的使用者若無指派的 Intune 授權，則不會受到影響。

>[!IMPORTANT]
> 如果您使用 Intune 和 Configuration Manager 來管理您的裝置，則只會將原則套用至您選取之群組中的直屬使用者。 而不會影響巢狀於您選取之群組中的子群組成員。

使用者可以從應用程式市集或 Google Play 下載應用程式。 如需詳細資訊，請參閱：
* [當 Android 應用程式交由應用程式防護原則管理時的行為](app-protection-enabled-apps-android.md)
* [當 iOS 應用程式交由應用程式保護原則管理時的行為](app-protection-enabled-apps-ios.md)

##  <a name="change-existing-policies"></a>變更現有的原則
您可以編輯現有的原則，並將它套用到目標使用者。 不過，當您變更現有的原則時，已登入應用程式的使用者將有 8 小時看不到變更。

若要立即查看變更的影響，終端使用者必須登出應用程式再重新登入。

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>變更與原則相關聯的應用程式清單

1.  在 [應用程式防護原則] 窗格中，選擇您想要變更的原則，以開啟特定於您選取之原則的窗格。

2.  在 [原則] 窗格中，選擇 [目標應用程式] 開啟應用程式清單。

3.  在清單中移除或新增應用程式，然後選擇 [儲存] 圖示儲存您的變更。

### <a name="to-change-the-list-of-user-groups"></a>變更使用者群組清單


1.  在 [應用程式防護原則] 窗格中，選擇您想要變更的原則，以開啟特定於您選取之原則的窗格。

2.  在 [原則] 窗格中，選擇 [指派] 來開啟 [Intune 應用程式防護 - 指派]窗格，該窗格會顯示具有此原則的目前使用者群組清單。

3.  若要將新的使用者群組新增至原則，在 [包含] 索引標籤選擇 [選取要包含的群組]，並選取使用者群組。 選擇 [選取] 將原則部署到您選取的群組。

4.  若要刪除使用者群組新增，在 [排除] 索引標籤選擇 [選取群組以排除]，並選取使用者群組。 選擇 [選取]以移除使用者群組。

### <a name="to-change-policy-settings"></a>變更原則設定

1.  在 [應用程式防護原則] 窗格中，選擇您想要變更的原則，以開啟特定於您選取之原則的窗格。

2.  選擇 [原則設定] 以開啟 [原則設定] 窗格。

3.  變更設定，然後選擇 [儲存] 圖示儲存您的變更。

## <a name="target-app-protection-policies-based-on-device-management-state"></a>根據裝置管理狀態來設定應用程式保護原則目標
在許多組織中，同時允許使用者使用 Intune「行動裝置管理」(MDM) 受控裝置 (例如公司擁有的裝置) 及僅以 Intune 應用程式保護原則保護的非受控裝置 (例如 BYO 裝置)，是很常見的情況。

因為 Intune 應用程式保護原則會以使用者的身分識別為目標，所以傳統上，使用者的保護設定會同時套用至已註冊 (MDM 受控) 和未註冊的裝置 (非 MDM)。 因此，您可以讓 Intune 應用程式保護原則以 Intune 已註冊或未註冊 iOS 及 Android 裝置為目標。 您可以有一個用於非受控裝置的保護原則，其中會提供適當的嚴格資料外洩防護 (DLP) 控制措施，並有另一個用於 MDM 受控裝置的保護原則，其中可能提供較寬鬆的 DLP 控制措施。 

若要建立這些原則，請在 Intune 主控台中瀏覽至 [行動應用程式] > [應用程式保護原則]，然後按一下 [新增原則]。 您也可以編輯現有的應用程式保護原則。 如果您想要將應用程式保護原則同時套用至受控和非受控裝置，請確認將 [以所有應用程式類型為目標] 設定為 [是] (預設值)。 如果您想要根據管理狀態進行更精細的指派，請將 [以所有應用程式類型為目標] 選項設定為 [否]。 

針對視為「受控」的 iOS 應用程式，需要為每個應用程式部署 **IntuneMAMUPN** 設定原則設定。 如需詳細資訊，請參閱[如何使用 Microsoft Intune 管理 iOS 應用程式之間的資料傳輸](https://docs.microsoft.com/en-us/intune/data-transfer-between-apps-manage-ios#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm)。

> [!NOTE]
> 針對以裝置管理狀態為基礎的應用程式保護原則，如需特定 iOS 的支援資訊，請參閱[根據管理狀態來設定目標的 MAM 保護原則](whats-new.md#mam-protection-policies-targeted-based-on-management-state-)。

## <a name="policy-settings"></a>原則設定
若要查看 iOS 和 Android 的原則設定的完整清單，請選取下列其中一個連結︰

- [iOS 原則](app-protection-policy-settings-ios.md)
- [Android 原則](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>接下來的步驟
[監視合規性和使用者狀態](app-protection-policies-monitor.md)

### <a name="see-also"></a>另請參閱
* [當 Android 應用程式交由應用程式防護原則管理時的行為](app-protection-enabled-apps-android.md)
* [當 iOS 應用程式交由應用程式防護原則管理時的行為](app-protection-enabled-apps-ios.md)
