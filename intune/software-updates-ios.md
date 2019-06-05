---
title: 在 Microsoft Intune 中設定 iOS 軟體更新原則 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中建立或新增設定原則，以限制在 Intune 管理或監督的 iOS 裝置上自動安裝軟體更新的時間。 您可以選擇未安裝更新的日期與時間。 您也可以將此原則指派給群組、使用者或裝置，並檢查是否有任何安裝失敗。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5a5c9dea847ace51c7d6f06cfa43c44beead18f8
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66373421"
---
# <a name="add-ios-software-update-policies-in-intune"></a>在 Intune 中新增 iOS 軟體更新原則

軟體更新原則可讓您強制受監督的 iOS 裝置自動安裝最新可用的 OS 更新。 設定原則時，您可以新增不希望裝置安裝更新的天數和時間。 

本功能適用於：

- iOS 10.3 和更新版本 (受監督)

裝置大約每隔 8 小時簽入 Intune 一次。 如果有更新可用，而且不在限制期間內，則裝置會下載並安裝最新的 OS 更新。 更新裝置不需要任何使用者互動。 原則不會阻止使用者手動更新 OS。

## <a name="configure-the-policy"></a>設定原則

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [軟體更新]   > [iOS 更新原則]   > [建立]  。
3. 輸入下列設定：

    - **名稱**：輸入軟體更新原則的名稱。 例如，輸入 `iOS restricted update times`。
    - **描述**：輸入原則的描述。 這是選擇性設定，但建議執行。

4. 選取 [設定] > [設定]  。 輸入下列設定：

    - **選取時間以避免更新安裝**：指定不強制安裝更新的受限制時間範圍。 
      - 不支援夜間區間，因此可能無法運作。 例如，請勿設定「開始時間」  為下午 8 點且「結束時間」  為上午 6 點的原則。
      - 在上午 12 點開始且在上午 12 點結束的原則會被評估為 0 小時，而不是 24 小時，這會導致沒有限制。

      設定受限制的時間範圍時，請輸入下列詳細資料：

      - **天數**：選擇不會安裝更新的一週天數。 例如，勾選星期一、星期三及星期五，以防止更新在這幾天安裝。
      - **時區**：選擇時區。
      - **開始時間**：選擇受限制時間範圍的開始時間。 例如，輸入上午 5 點，因此從上午 5 點開始不會安裝更新。
      - **結束時間**：選擇受限制時間範圍的結束時間。 例如，輸入上午 1 點，因此從上午 1 點開始可以安裝更新。

    - **延遲軟體更新對終端使用者的可見性，而不會變更排程更新 (天)** ： 

      **這項設定已移至[裝置限制](device-restrictions-ios.md#general)。將會從入口網站的這個位置中移除該設定**。 很快就可在此處變更現有的原則。 大約一個月之後，此設定將從現有的原則中移除。

      若要限制影響，建議您：
        - 從入口網站的這個位置中移除現有原則。
        - 建立新的[裝置限制原則](device-restrictions-ios.md#general)。
        - 目標為與原始原則相同的使用者。

      如果有衝突，「除非」  這兩個值完全相同，否則這項設定不會執行任何動作。 若要避免發生衝突，請務必要從入口網站的這個位置中變更或移除現有原則。
      > [! 重要]  
      > 「開始時間」  和「結束時間」  設為上午 12 點的原則會被評估為 0 小時，而不是 24 小時。 這會導致沒有限制。  

5. 選取 [確定]   > [建立]  ，以儲存您的變更並建立原則。

設定檔隨即建立，並顯示在原則清單中。

如需來自 Intune 支援小組的指引，請參閱 [Delay visibility of software updates in Intune for supervised devices](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753) (延遲軟體更新在 Intune 中對受監督裝置的可見性)。

> [!NOTE]
> Apple MDM 不允許您強制裝置依特定時間或日期安裝更新。

## <a name="change-the-restricted-times-for-the-policy"></a>變更原則的限定時間

1. 在 [軟體更新]  中，選取 [iOS 更新原則]  。
2. 選擇現有的原則 > [屬性]  。
3. 更新受限制的時間：

    1. 選擇每星期幾
    2. 選擇會套用此原則的時區
    3. 輸入列入封鎖清單時段的開始與結束時間

    > [!NOTE]
    > 如果**開始時間**和**結束時間**均設定為上午 12 點，則 Intune 不會檢查是否有何時要安裝更新的限制。 這表示會忽略針對**選取時間以避免更新安裝**使用的任何設定，因此隨時可以安裝更新。  

## <a name="assign-the-policy-to-users"></a>指派原則給使用者

現有的原則會指派給群組、使用者或裝置。 指派後即會套用原則。

1. 在 [軟體更新]  中，選取 [iOS 更新原則]  。
2. 選擇現有的原則 > [指派]  。 
3. 選取要包含或排除此原則的 Azure Active Directory 群組、使用者或裝置。
4. 選擇 [儲存]  將原則部署至群組。

要套用原則之使用者的裝置將會接受更新合規性的評估。 此原則也支援無使用者的裝置。

## <a name="monitor-device-installation-failures"></a>監視裝置安裝的錯誤
<!-- 1352223 -->
[軟體更新]   > [iOS 裝置的安裝失敗]  會顯示要套用更新原則、嘗試更新及無法更新的受監督 iOS 裝置清單。 針對每部裝置，您可以檢視狀態，以了解為何尚未自動更新裝置。 此清單中不會顯示狀況良好的最新裝置。 「最新」裝置包含裝置本身可支援的最新更新。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
