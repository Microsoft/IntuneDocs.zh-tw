---
title: "建立及部署應用程式保護原則"
titleSuffix: Intune on Azure
description: "了解 Intune 應用程式保護原則如何協助保護您管理之應用程式所使用的公司資料。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 56a19bc4d970f230f719af9369dada45ffb65e76
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>如何建立及部署應用程式保護原則

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="before-you-begin"></a>開始之前

如果您正在 Intune 傳統主控台中尋找指示，請參閱[如何建立應用程式保護原則](https://docs.microsoft.com/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)。

無論裝置是否交由 Intune 管理，都能對裝置上執行的應用程式套用應用程式保護原則。 如需應用程式保護原則的運作方式，以及 Intune 應用程式保護原則支援案例詳細說明，請參閱[什麼是 Microsoft Intune 應用程式保護原則](app-protection-policy.md)。

如果您正在尋找 MAM 支援之應用程式的清單，請參閱 [MAM 應用程式清單](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。

##  <a name="create-an-app-protection-policy"></a>建立應用程式保護原則
1.  在 [行動應用程式] 工作負載中，選擇 [管理] > [應用程式保護原則]。

2.  這會開啟 [應用程式原則] 刀鋒視窗，讓您從中建立新的原則及編輯現有的原則。 選擇 **[新增原則]**。

  ![[新增原則] 刀鋒視窗的螢幕擷取畫面](./media/app-protection-add-policy.png)

3.  輸入原則的名稱、新增簡短描述並選取平台類型，以建立適用於 iOS 或 Android 的原則。 您可以針對每部平台建立多項原則。

4.  選擇 [應用程式] 開啟 [應用程式]  刀鋒視窗，其中會顯示可用的應用程式清單。 請從清單中選取要與所建立之原則建立關聯的一或多個應用程式。 選取應用程式之後，選擇 [應用程式] 刀鋒視窗底部的 [選取] 儲存您的選擇。

    > [!IMPORTANT]
    > 您至少必須選取一個應用程式，才能建立原則。

5.  在 [新增原則] 刀鋒視窗上，選擇 [設定必要設定] 開啟 [原則設定] 刀鋒視窗。

    原則設定分為兩類：[資料重新配置] 和 [存取]。  資料重新配置原則適用於在應用程式中移入及移出資料，而存取原則決定使用者如何存取工作內容中的應用程式。
    原則設定中的預設值可協助您開始使用。 如果預設值符合您的需求，則不需要進行任何變更。

    > [!TIP]
    > 只有在工作內容中使用應用程式時，才會強制執行這些原則設定。  當使用者使用應用程式來執行個人工作時，不會受到這些原則的影響。



6.  選擇 [確定] 儲存這項設定。 現在您已回到 [新增原則]  刀鋒視窗。 選擇 [建立] 建立原則並儲存您的設定。


當您如先前程序中所述完成建立原則時，該原則不會部署給任何使用者。 若要部署原則，請參閱下列章節＜將原則部署給使用者＞。

## <a name="deploy-a-policy-to-users"></a>將原則部署給使用者

1.  在 [原則] 刀鋒視窗中，選擇 [使用者群組] 開啟 [使用者群組] 刀鋒視窗。 在 [使用者群組] 刀鋒視窗中，選擇 [新增使用者群組] 開啟 [新增使用者群組] 刀鋒視窗。

  ![反白顯示 [新增使用者群組] 功能表選項的 [使用者群組] 刀鋒視窗的螢幕擷取畫面](./media/app-protection-policy-add-users.png)

2.  [新增使用者群組]  刀鋒視窗中會顯示使用者群組清單。 這是 **Azure Active Directory**中的所有安全性群組清單。 請選取要套用這項原則的使用者群組，然後選擇 [選取]。 選擇 [選取] 可將原則部署給使用者。
  ![顯示 Azure Active Directory 使用者清單的 [新增使用者群組] 刀鋒視窗的螢幕擷取畫面](./media/azure-ad-user-group-list.png)

您現在已建立原則並將其部署給使用者。

只有獲指派 Microsoft Intune 授權的使用者才會受此原則影響。 所選安全性群組中的使用者若未獲指派 Microsoft Intune 授權，將不受影響。

>[!IMPORTANT]
> 如果您使用 Intune 和 Configuration Manager 來管理您的 iOS 和 Android 裝置，則只會將原則套用至您選取之群組中的直屬使用者， 而不會影響巢狀於您選取之群組中的子群組成員。

使用者可以從應用程式市集或 Google Play 下載應用程式。 如需詳細資訊，請參閱：
* [當 Android 應用程式交由應用程式保護原則管理時的行為](app-protection-enabled-apps-android.md)
* [當 iOS 應用程式交由應用程式保護原則管理時的行為](app-protection-enabled-apps-ios.md)

##  <a name="change-existing-policies"></a>變更現有的原則
您可以編輯現有的原則，並將它套用到目標使用者。 不過，當您變更現有的原則時，已登入應用程式的使用者將有 8 小時看不到變更。

若要立即查看變更的影響，使用者必須登出應用程式再重新登入。

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>變更與原則相關聯的應用程式清單

1.  在 [應用程式原則] 刀鋒視窗中，選擇您要變更的原則。 這會開啟您剛才選取之原則的特定刀鋒視窗。

2.  在 [原則] 刀鋒視窗中，選擇 [目標應用程式] 開啟應用程式清單。

3.  在清單中移除或新增應用程式，然後選擇 [儲存] 圖示儲存您的變更。

### <a name="to-change-the-list-of-user-groups"></a>變更使用者群組清單

1.  在 [應用程式原則] 刀鋒視窗中，選擇您要變更的原則。 這會開啟您選取之原則的特定刀鋒視窗。

2.  在 [原則] 刀鋒視窗中，選擇 [使用者群組] 開啟 [使用者群組] 刀鋒視窗，其中會顯示具有這項原則的目前使用者群組清單。

3.  若要將新的使用者群組加入原則中，請選擇 [新增使用者群組]，然後選取使用者群組。 選擇 [選取] 將原則部署到您選取的群組。

4.  若要刪除使用者群組，請反白顯示您想要移除的使用者群組。 然後選擇省略符號 (...)，再選擇 [刪除] 移除使用者群組。
  ![顯示 [刪除] 選項的螢幕擷取畫面](./media/app-protection-policy-delete-user.png)

### <a name="to-change-policy-settings"></a>變更原則設定

1.  在 [應用程式原則] 刀鋒視窗中，選擇您要變更的原則。 這會開啟您剛才選取之原則的特定刀鋒視窗。


2.  選擇 [原則設定] 開啟 [原則設定] 刀鋒視窗。

3.  變更設定，然後選擇 [儲存] 圖示儲存您的變更。

## <a name="policy-settings"></a>原則設定
若要查看 iOS 和 Android 的原則設定的完整清單，請選取下列其中一項︰

- [iOS 原則](app-protection-policy-settings-ios.md)
- [Android 原則](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>後續步驟
[監視合規性和使用者狀態](app-protection-policies-monitor.md)

### <a name="see-also"></a>請參閱
* [當 Android 應用程式交由應用程式保護原則管理時的行為](app-protection-enabled-apps-android.md)
* [當 iOS 應用程式交由應用程式保護原則管理時的行為](app-protection-enabled-apps-ios.md)
