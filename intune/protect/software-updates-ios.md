---
title: 在 Microsoft Intune 中設定 iOS/iPadOS 軟體更新原則 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，建立或新增設定原則以限制自動在 iOS/iPadOS 裝置上安裝軟體更新的時間。 您可以選擇未安裝更新的日期與時間。 您也可以將此原則指派給群組、使用者或裝置，並檢查是否有任何安裝失敗。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77d4a90bb2eaa8434ff9c05362dcb0d7cb270651
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576162"
---
# <a name="add-iosipados-software-update-policies-in-intune"></a>在 Intune 中新增 iOS/iPadOS 軟體更新原則

軟體更新原則可讓您強制受監督的 iOS/iPadOS 裝置自動安裝 OS 更新。 受監督的裝置是使用 Apple Business Manager 或 Apple School Manager 註冊的裝置。 設定原則以部署更新時，您可以：

- 選擇部署可用的「最新更新」  ，或是若您不想要部署最新更新，則可透過更新版本號碼來選擇部署較舊的更新。 若您選擇部署較舊的更新，則也必須設定裝置設定原則來限制軟體更新的可見度。
- 指定決定何時安裝更新的排程。 排程可以簡單地設為在下一次裝置存回時安裝更新，或建立要安裝或是要封鎖安裝的日期和時間範圍。

本功能適用於：

- iOS 10.3 和更新版本 (受監督)

根據預設，裝置大約每隔 8 小時會存回 Intune 一次。 若可以透過更新原則取得更新，裝置便會下載更新。 裝置接著會在您排程設定內的下一次存回時安裝更新。 雖然更新流程通常不會牽涉到任何使用者互動，但如果裝置有密碼，則使用者必須輸入密碼才能開始軟體更新。 設定檔無法防止使用者手動更新 OS。 您可以使用裝置設定原則限制軟體更新的可見度，以防止使用者手動更新 OS。

## <a name="configure-the-policy"></a>設定原則

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [更新 iOS/iPadOS 原則]   > [建立設定檔]  。
3. 在 [基本]  索引標籤上，指定此原則的名稱、指定描述 (選擇性)，然後選取 [下一步]  。

   ![[基本] 索引標籤](./media/software-updates-ios/basics-tab.png)

4. 在 [更新原則設定]  索引標籤上，設定下列內容：

   1. **選取要安裝的版本**。 您可以選擇：

      - [最新的更新]  ：這會部署 iOS/iPadOS 最近發行的更新。
      - 任何先前的可用版本都可以從下拉式方塊中取得。 若您選取先前的版本，則也必須設定裝置設定原則來延遲軟體更新的可見度。

   2. **排程類型**：設定此原則的排程：

      - *在下一次存回時更新*：更新會在裝置下一次存回 Intune 時安裝。 這是最簡單的選項，且不需要任何其他的設定。
      - *在排程時間的期間內更新*：您可以設定一或多個時段，並在這些時段內於存回時安裝更新。
      - *在排程時間之外更新*：您可以設定一或多個時段。更新將不會在這些時段內於存回時進行安裝。

   3. **每週排程**：若您選擇 [在下一次存回時更新]  之外的其他排程類型，請設定下列選項：

      ![選取在排程時間期間內進行更新的範例](./media/software-updates-ios/scheduled-time.png)

      - **時區**：選擇時區。
      - **時間範圍**：定義一或多個時間區塊，其限制安裝更新的時間。 下列選項效果取決於您選取的排程類型。 您可以透過使用開始日和結束日來支援隔日區塊。 這些選項包括：

        - **開始日**：選擇排程時段開始的日期。
        - **開始時間**：選擇排程時段開始日期的時間。 例如，若您選取上午 5 點，且選取了 [在排程時間的期間內更新]  排程類型，則上午 5 點將會是更新可開始安裝的時間。 若您選擇了 [在排程時間之外更新]  排程類型，則上午 5 點將會是無法安裝更新的開始時間。
        - **結束日**：選擇排程時段結束的日期。
        - **結束時間**：選擇排程時段結束日期的時間。 例如，若您選取上午 1 點，且選取了 [在排程時間的期間內更新]  排程類型，則上午 1 點之後將再也無法安裝更新。 若您選擇了 [在排程時間之外更新]  排程類型，則上午 1 點之後將會是可以安裝更新的開始時間。

       若您沒有設定時間開始或結束，則設定將不會進行任何限制，且可在任何時間安裝更新。  

       > [!NOTE]
       > 若要在您受監督 iOS/iPadOS 裝置上一段特定時間內延遲軟體更新的可見度，請在[裝置限制](../configuration/device-restrictions-ios.md#general)中設定這些設定。 軟體更新原則會覆寫任何裝置限制。 當您同時設定軟體更新原則與限制以延遲軟體更新顯示時，裝置會根據原則強制進行軟體更新。 會套用限制，因此使用者不會看到自行更新裝置的選項，且更新會在您 iOS 更新原則所定義的時間推送。

   設定 [更新原則設定]  之後，請選取 [下一步]  。

5. 若要將標籤套用到更新原則，請在 [範圍標籤]  索引標籤上選取 [+ 選取範圍標籤]  以開啟 [選取標籤]  窗格。

   - 在 [選取標籤]  窗格上，選擇一或多個標籤，然後按一下 [選取]  以將它們新增到原則並返回 [範圍標籤]  窗格。

   當就緒時，請選取 [下一步]  以繼續到 [指派]  。

6. 在 [指派]  索引標籤上，選擇 [+ 選取要納入的群組]  ，然後將更新原則指派給一或多個群組。 使用 [+ 選取要排除的群組]  以微調指派。 接著，選取 [下一步]  以繼續。

   要套用原則之使用者的裝置將會接受更新合規性的評估。 此原則也支援無使用者的裝置。

7. 在 [檢閱 + 建立]  索引標籤上檢閱設定，然後在準備儲存您的 iOS/iPadOS 更新原則時選取 [建立]  。 新原則會顯示在 iOS/iPadOS 的更新原則清單中。

如需來自 Intune 支援小組的指引，請參閱 [Delay visibility of software updates in Intune for supervised devices](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753) (延遲軟體更新在 Intune 中對受監督裝置的可見性)。

> [!NOTE]
> Apple MDM 不允許您強制裝置依特定時間或日期安裝更新。 您可以使用 Intune 軟體更新原則來降級裝置上的 OS 版本。

## <a name="edit-a-policy"></a>編輯原則

您可以編輯現有的原則，包括變更受限時間：

1. 選取 [裝置]   > [更新 iOS 的原則]  。 選取您要編輯的原則。

2. 檢視原則 [屬性]  時，請選取您要修改之原則頁面的 [編輯]  。

   ![編輯原則](./media/software-updates-ios/edit-policy.png)

3. 引進變更之後，請選取 [檢閱並儲存]   > [儲存]  以儲存您的編輯，然後返回原則 [屬性]  。

> [!NOTE]
> 如果 [開始時間]  與 [結束時間]  均設定為上午 12 點，則 Intune 不會檢查更新安裝時間限制。 這表示會忽略針對**選取時間以避免更新安裝**使用的任何設定，因此隨時可以安裝更新。

## <a name="monitor-device-installation-failures"></a>監視裝置安裝的錯誤

<!-- 1352223 -->
[軟體更新]   > [iOS 裝置的安裝失敗]  會顯示要套用更新原則、嘗試更新及無法更新的受監督 iOS/iPadOS 裝置清單。 針對每部裝置，您可以檢視狀態，以了解為何尚未自動更新裝置。 此清單中不會顯示狀況良好的最新裝置。 「最新」裝置包含裝置本身可支援的最新更新。

## <a name="next-steps"></a>後續步驟

[監視其狀態](../configuration/device-profile-monitor.md)。
