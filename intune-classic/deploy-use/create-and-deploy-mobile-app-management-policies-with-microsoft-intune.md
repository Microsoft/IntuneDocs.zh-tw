---
title: "建立和部署 MAM 原則 | Microsoft Docs"
description: "使用本主題中的逐步指示來建立及部署行動應用程式管理原則。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c1b9a343-1737-4a65-a9c6-aca48acad11c
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: d91ce526650166197520d37c82084c0ff141ec80
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="create-and-deploy-app-protection-policies-with-microsoft-intune"></a>使用 Microsoft Intune 建立及部署應用程式保護原則

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主題描述在 **Azure 入口網站**中建立應用程式保護原則的程序 。 Azure 入口網站是用於建立應用程式保護原則的新管理主控台，並建議您使用這個入口網站建立應用程式保護原則。 Azure 入口網站支援下列 MAM 案例：

- Intune 中註冊的裝置。
- 協力廠商 MDM 解決方案管理的裝置。
- 未受任何 MDM 解決方案 (BYOD) 管理的裝置。

>[!IMPORTANT]
以下是使用 **Intune 管理主控台**來管理裝置時的一些考量：

> * 您可以建立應用程式保護原則，該原則使用 [Intune 管理主控台](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)支援 Intune 中註冊之裝置的應用程式。
> * 在 Intune 管理主控台中建立的應用程式保護原則無法匯入到 Azure 入口網站。  您必須在 Azure 入口網站中重新建立應用程式保護原則。

> * 您在 Intune 管理主控台中可能看不到所有應用程式保護原則設定。 Azure 入口網站是建立應用程式保護原則的新管理主控台。

> * 若要部署受管理應用程式，您必須在 Intune 管理主控台中建立應用程式保護原則。 在此情況下，您可能想要在 Intune 管理主控台和 Azure 入口網站中建立應用程式保護原則︰在 Intune 管理主控台中建立應用程式保護原則，可確定您能夠部署受管理的應用程式，而在 Azure 入口網站中建立應用程式保護原則，則是由於它是具有所有應用程式保護原則設定的新管理主控台。

> * 如果您在 Intune 管理主控台和 Azure 入口網站上建立應用程式保護原則，則會將在 Azure 入口網站中建立的原則套用至應用程式。

若要查看為 Android 和 iOS 平台支援的原則設定清單，請選取下列其中一項︰

> [!div class="op_single_selector"]
- [iOS 原則](ios-mam-policy-settings.md)
- [Android 原則](android-mam-policy-settings.md)

- 如需應用程式保護原則的運作方式，以及 Intune 應用程式保護原則支援案例詳細說明，請參閱[使用應用程式保護原則來保護應用程式和資料](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)。

##  <a name="create-an-app-protection-policy"></a>建立應用程式保護原則
應用程式保護原則是在 Azure 入口網站所建立。 如果這是您第一次使用 Azure 入口網站，請閱讀 [Microsoft Intune 應用程式保護原則的 Azure 入口網站](azure-portal-for-microsoft-intune-mam-policies.md)以更熟悉 Azure入口網站。 建立應用程式保護原則之前，請檢閱[必要條件和支援](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)資訊。

請遵循下列步驟來建立應用程式保護原則：

1. 移至 [Azure 入口網站](https://portal.azure.com)並輸入您的認證。

2. 選擇 [更多服務] 並輸入 "Intune"。

3. 選擇 [Intune 應用程式保護]。

4. 選擇 [Intune 行動應用程式管理]&gt; [設定] 開啟 [所有設定] 刀鋒視窗。

    ![Intune 行動應用程式管理刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_Mainblade-2.png)

2.  在 [所有設定] 刀鋒視窗中，選擇 [應用程式原則]。 這會開啟 [應用程式原則] 刀鋒視窗，您將在其中建立新的原則及編輯現有的原則。 選擇 **[新增原則]**。

    ![反白顯示 [新增原則] 功能表選項的 [應用程式原則] 刀鋒視窗的螢幕擷取畫面 ](../media/AppManagement/AzurePortal_MAM_AddPolicy.png)

3.  輸入原則的名稱、新增簡短描述並選取平台類型，以建立適用於 iOS 或 Android 的原則。 您可以針對每部平台建立多項原則。

    ![[新增原則] 刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_AddPolicy_only.png)

4.  選擇 [應用程式] 開啟 [應用程式]  刀鋒視窗，其中會顯示可用的應用程式清單。 請從清單中選取要與所建立之原則建立關聯的一或多個應用程式。 選取應用程式之後，選擇 [應用程式] 刀鋒視窗底部的 [選取] 儲存您的選擇。

    > [!IMPORTANT]
    > 您至少必須選取一個應用程式，才能建立原則。

5.  在 [新增原則] 刀鋒視窗上，選擇 [設定必要設定] 開啟 [原則設定] 刀鋒視窗。

    原則設定分為兩類：[資料重新配置] 和 [存取]。  資料重新配置原則適用於在應用程式中移入及移出資料，而存取原則決定使用者如何存取工作內容中的應用程式。
    原則設定中的預設值可協助您開始使用。 如果預設值符合您的需求，則不需要進行任何變更。

    > [!TIP]
    > 只有在工作內容中使用應用程式時，才會強制執行這些原則設定。  當使用者使用應用程式來執行個人工作時，不會受到這些原則的影響。

    ![設定刀鋒視窗與 [新增原則] 刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_PolicySettings.png)

6.  選擇 [確定] 儲存這項設定。 現在您已回到 [新增原則]  刀鋒視窗。 選擇 [建立] 建立原則並儲存您的設定。

    ![顯示已設定的應用程式和設定的 [新增原則] 刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_CreatePolicy.png)

當您如先前程序中所述完成建立原則時，該原則不會部署給任何使用者。 若要部署原則，請參閱下列章節＜將原則部署給使用者＞。

> [!IMPORTANT]
> 如果您使用 Intune 管理主控台建立應用程式的應用程式保護原則，及使用 Azure 入口網站建立應用程式保護原則，則使用 Azure 入口網站建立的原則會優先適用。 不過，Intune 或 Configuration Manager 主控台中的報表會報告從 Intune 管理主控台建立的原則設定。 例如：
>
> -   您在 Intune 管理主控台中，建立了封鎖從應用程式複製的應用程式保護原則。
> -   您在 Azure 主控台中，建立了允許從應用程式複製的應用程式保護原則。
> -   您將這兩個原則與同一個應用程式建立關聯。
> -   會優先使用您從 Azure 主控台建立的原則並允許複製。
> -   不過，Intune 主控台中的狀態和報表會不正確地表示該複製遭到封鎖。

## <a name="line-of-business-lob-apps-optional"></a>企業營運 (LOB) 應用程式 (選用)

從 Intune 1703 版開始，您可以選擇在建立新的應用程式保護原則時，通常會將 LOB 應用程式新增至 Intune。 這可讓您選擇使用 MAM SDK 來定義 LOB 應用程式的應用程式保護原則，而不需要完整的應用程式部署權限。

> [!TIP]
> 您也可以在進行 [Intune App SDK](/intune-classic/develop/intune-app-sdk-get-started) 工作流程時，將 LOB 應用程式新增至 Intune。

> [!IMPORTANT]
> 如果使用者只有部署 MAM 應用程式的特定權限，而沒有完整的應用程式部署權限 (可讓他們在 Intune 中部署任何應用程式)，則不會進行 Intune SDK 工作流程，但仍然可以透過 MAM 應用程式保護原則建立工作流程新增其 LOB 應用程式。

### <a name="to-add-lob-apps-ios-and-android"></a>新增 LOB 應用程式 (iOS 和 Android)

1.  在 [新增原則] 刀鋒視窗中，選擇 [設定應用程式] 以開啟 [應用程式] 刀鋒視窗。

    ![MAM 的 [新增原則] 刀鋒視窗](../media/AppManagement/mam-lob-apps-1.png)

2.  按一下 [更多應用程式]，然後輸入 [配套識別碼] (適用於 iOS) 或 [套件識別碼] (適用於 Android)，然後按一下 [選取] 以新增您的 LOB 應用程式。

    ![MAM 的 [更多應用程式] 刀鋒視窗](../media/AppManagement/mam-lob-apps-2.png)

### <a name="to-add-lob-apps-windows"></a>新增 LOB 應用程式 (Windows)

> [!IMPORTANT]
> 當您建立新的應用程式保護原則時，您必須從 [平台] 下拉式清單選取 [Windows 10]。

1.  在 [新增原則] 刀鋒視窗中，選擇 [允許的應用程式] 或 [Exempt apps] (豁免應用程式)，以開啟 [允許的應用程式] 或 [Exempt apps] (豁免應用程式) 刀鋒視窗。

    > [!NOTE]
    >
    - **允許的應用程式**︰這些應用程式是必須遵守此原則的應用程式。
    - **豁免應用程式**︰這些應用程式不會套用此原則，而且可以存取公司資料，而沒有任何限制。
<br></br>
2. 在 [允許的應用程式] 或 [Exempt apps] (豁免應用程式) 刀鋒視窗中，按一下 [新增應用程式]。 您可以新增建議的 Microsoft 應用程式、市集應用程式或傳統型應用程式。

    a.  **建議的應用程式︰**可讓系統管理員輕鬆匯入原則之預先填入的應用程式清單 (大部分是 Office 應用程式)。

    b。  **市集應用程式︰**系統管理員可以將 Windows 市集中的任何應用程式新增至原則。

    c.  **Windows 傳統型應用程式︰**系統管理員可以將任何傳統的 Windows 傳統型應用程式新增至原則 (例如 exe、dll 等)。

## <a name="deploy-a-policy-to-users"></a>將原則部署給使用者

1.  在 [原則] 刀鋒視窗中，選擇 [使用者群組] 開啟 [使用者群組] 刀鋒視窗。 在 [使用者群組] 刀鋒視窗中，選擇 [新增使用者群組] 開啟 [新增使用者群組] 刀鋒視窗。

    ![反白顯示 [新增使用者群組] 功能表選項的 [使用者群組] 刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_AddUserstoPolicy.png)

2.  [新增使用者群組]  刀鋒視窗中會顯示使用者群組清單。 這是 **Azure Active Directory**中的所有安全性群組清單。 請選取要套用這項原則的使用者群組，然後選擇 [選取]。 選擇 [選取] 可將原則部署給使用者。

    ![顯示 Azure Active Directory 使用者清單的 [新增使用者群組] 刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_SelectUserstoDeploy.png)

    您現在已建立原則並將其部署給使用者。

只有指派 Intune 授權的使用者會受到此原則的影響。 您所選取安全性群組中的使用者，若未指派 Intune 授權，則不會受到影響。

>[!IMPORTANT]
> 如果您使用 Intune 和 Configuration Manager 來管理您的 iOS 和 Android 裝置，則只會將原則套用至您選取之群組中的直屬使用者， 而不會影響巢狀於您選取之群組中的子群組成員。

使用者可以從應用程式市集或 Google Play 下載應用程式。 如需詳細資訊，請參閱：
* [當 Android 應用程式交由應用程式保護原則管理時的行為](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [當 iOS 應用程式交由應用程式保護原則管理時的行為](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

##  <a name="change-existing-policies"></a>變更現有的原則
您可以編輯現有的原則，並將它套用到目標使用者。 不過，當您變更現有的原則時，已登入應用程式的使用者將有 8 小時看不到變更。

若要立即查看變更的影響，使用者必須登出應用程式再重新登入。

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>變更與原則相關聯的應用程式清單

1.  在 [應用程式原則] 刀鋒視窗中，選擇您要變更的原則。 這會開啟您剛才選取之原則的特定刀鋒視窗。

    ![在不同的刀鋒視窗中開啟的現有原則的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  在 [原則] 刀鋒視窗中，選擇 [目標應用程式] 開啟應用程式清單。

3.  在清單中移除或新增應用程式，然後選擇 [儲存] 圖示儲存您的變更。

### <a name="to-change-the-list-of-user-groups"></a>變更使用者群組清單

1.  在 [應用程式原則] 刀鋒視窗中，選擇您要變更的原則。 這會開啟您選取之原則的特定刀鋒視窗。

2.  在 [原則] 刀鋒視窗中，選擇 [使用者群組] 開啟 [使用者群組] 刀鋒視窗，其中會顯示具有這項原則的目前使用者群組清單。

3.  若要將新的使用者群組加入原則中，請選擇 [新增使用者群組]，然後選取使用者群組。 選擇 [選取] 將原則部署到您選取的群組。

    ![選取兩個使用者群組的 [新增使用者群組] 刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_ChangePolicy_SelectUser.png)

4.  若要刪除使用者群組，請反白顯示您想要移除的使用者群組。 然後選擇省略符號 (...)，再選擇 [刪除] 移除使用者群組。

    ![顯示 [刪除] 選項的螢幕擷取畫面 ](../media/AppManagement/AzurePortal_MAM_ChangePolicy_DeleteUser.png)

### <a name="to-change-policy-settings"></a>變更原則設定

1.  在 [應用程式原則] 刀鋒視窗中，選擇您要變更的原則。 這會開啟您剛才選取之原則的特定刀鋒視窗。

    ![在不同的刀鋒視窗中開啟現有原則的螢幕擷取畫面 ](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  選擇 [原則設定] 開啟 [原則設定] 刀鋒視窗。

3.  變更設定，然後選擇 [儲存] 圖示儲存您的變更。

    ![在頂端顯示儲存功能表選項的 [原則設定] 刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_ChangePolicy_ChangeSettings.png)

## <a name="policy-settings"></a>原則設定
若要查看 iOS 和 Android 的原則設定的完整清單，請選取下列其中一項︰

> [!div class="op_single_selector"]
- [iOS 原則](ios-mam-policy-settings.md)
- [Android 原則](android-mam-policy-settings.md)

## <a name="next-steps"></a>後續步驟
[監視合規性和使用者狀態](monitor-mobile-app-management-policies-with-microsoft-intune.md)

### <a name="see-also"></a>請參閱
* [當 Android 應用程式交由應用程式保護原則管理時的行為](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [當 iOS 應用程式交由應用程式保護原則管理時的行為](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

