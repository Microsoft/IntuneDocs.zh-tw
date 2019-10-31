---
title: 在 Microsoft Intune 中設定 iOS 軟體更新原則 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，建立或新增設定原則以限制自動在 iOS 裝置上安裝軟體更新的時間。 您可以選擇未安裝更新的日期與時間。 您也可以將此原則指派給群組、使用者或裝置，並檢查是否有任何安裝失敗。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: ada1f6e5292684803fbea40430cdd43d61796746
ms.sourcegitcommit: 1a5b185acd27954b10b6d59409d82eb80fd71284
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72681363"
---
# <a name="add-ios-software-update-policies-in-intune"></a>在 Intune 中新增 iOS 軟體更新原則

軟體更新原則可讓您強制受監督的 iOS 裝置自動安裝最新可用的 OS 更新。 設定原則時，您可以新增不希望裝置安裝更新的天數和時間。

本功能適用於：

- iOS 10.3 和更新版本 (受監督)

裝置大約每隔 8 小時簽入 Intune 一次。 若有更新可用，裝置將會下載更新並安裝，但限制時間除外。 更新裝置不需要任何使用者互動。 原則不會阻止使用者手動更新 OS。

## <a name="configure-the-policy"></a>設定原則

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [軟體更新]   > [iOS 更新原則]   > [建立]  。
3. 在 [基本]  索引標籤上，指定此原則的名稱、指定描述 (選擇性)，然後選取 [下一步]  。

   ![[基本] 索引標籤](./media/software-updates-ios/basics-tab.png) 

4. 在 [更新原則設定]  索引標籤上，指定將不會強制安裝更新的受限時間範圍。  
   - 不支援夜間區間，因此可能無法運作。 例如，請勿設定「開始時間」  為下午 8 點且「結束時間」  為上午 6 點的原則。
   - 在上午 12 點開始且在上午 12 點結束的原則會被評估為 0 小時，而不是 24 小時。 此設定會導致沒有限制。

   設定受限制的時間範圍時，請輸入下列詳細資料：

   - **天數**：選擇不會安裝更新的一週天數。 例如，勾選星期一、星期三及星期五，以防止更新在這幾天安裝。
   - **時區**：選擇時區。
   - **開始時間**：選擇受限制時間範圍的開始時間。 例如，輸入上午 5 點，因此從上午 5 點開始不會安裝更新。
   - **結束時間**：選擇受限制時間範圍的結束時間。 例如，輸入上午 1 點，因此從上午 1 點開始可以安裝更新。
  
   > [!IMPORTANT]  
   > 「開始時間」  和「結束時間」  設為上午 12 點的原則會被評估為 0 小時，而不是 24 小時。 這會導致沒有限制。  
    
   若要在受監督的 iOS 裝置上將軟體更新顯示延遲一段特定時間，請在[裝置限制](../configuration/device-restrictions-ios.md#general)中設定。 軟體更新原則會覆寫任何裝置限制。 當您同時設定軟體更新原則與限制以延遲軟體更新顯示時，裝置會根據原則強制進行軟體更新。 限制會套用，因此使用者不會看到自行更新裝置的選項，而且更新會在您的 iOS 更新原則所定義的第一個時段推送。

   設定 [更新原則設定]  之後，請選取 [下一步]  。 

5. 若要將標籤套用到更新原則，請在 [範圍標籤]  索引標籤上選取 [+ 選取範圍標籤]  以開啟 [選取標籤]  窗格。
   
   - 在 [選取標籤]  窗格上，選擇一或多個標籤，然後按一下 [選取]  以將它們新增到原則並返回 [範圍標籤]  窗格。  

   當就緒時，請選取 [下一步]  以繼續到 [指派]  。

6. 在 [指派]  索引標籤上，選擇 [+ 選取要納入的群組]  ，然後將更新原則指派給一或多個群組。 使用 [+ 選取要排除的群組]  以微調指派。 接著，選取 [下一步]  以繼續。 

   要套用原則之使用者的裝置將會接受更新合規性的評估。 此原則也支援無使用者的裝置。

7. 在 [檢閱 + 建立]  索引標籤上，檢閱設定，然後在準備儲存您的 iOS 更新原則時選取 [建立]  。 您的新原則會顯示在 iOS 的更新原則清單中。


如需來自 Intune 支援小組的指引，請參閱 [Delay visibility of software updates in Intune for supervised devices](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753) (延遲軟體更新在 Intune 中對受監督裝置的可見性)。

> [!NOTE]
> Apple MDM 不允許您強制裝置依特定時間或日期安裝更新。

## <a name="edit-a-policy"></a>編輯原則
您可以編輯現有的原則，包括變更受限時間：

1. 在 [軟體更新]  中，選取 [更新 iOS 的原則]  ，然後選取您要編輯的原則。

2. 檢視原則 [屬性]  時，請選取您要修改之原則頁面的 [編輯]  。  
   ![編輯原則](./media/software-updates-ios/edit-policy.png)   

3. 引進變更之後，請選取 [檢閱並儲存]   > [儲存]  以儲存您的編輯，然後返回原則 [屬性]  。  
 
> [!NOTE]
> 如果 [開始時間]  與 [結束時間]  均設定為上午 12 點，則 Intune 不會檢查更新安裝時間限制。 這表示會忽略針對**選取時間以避免更新安裝**使用的任何設定，因此隨時可以安裝更新。  


## <a name="monitor-device-installation-failures"></a>監視裝置安裝的錯誤
<!-- 1352223 -->
[軟體更新]   > [iOS 裝置的安裝失敗]  會顯示要套用更新原則、嘗試更新及無法更新的受監督 iOS 裝置清單。 針對每部裝置，您可以檢視狀態，以了解為何尚未自動更新裝置。 此清單中不會顯示狀況良好的最新裝置。 「最新」裝置包含裝置本身可支援的最新更新。

## <a name="next-steps"></a>後續步驟

[監視其狀態](../configuration/device-profile-monitor.md)。
