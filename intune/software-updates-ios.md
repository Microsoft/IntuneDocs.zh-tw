---
title: 在 Microsoft Intune 中設定 iOS 軟體更新原則 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中建立或新增設定原則，以限制在 Intune 管理或監督的 iOS 裝置上自動安裝軟體更新的時間。 您可以選擇未安裝更新的日期與時間。 您也可以將此原則指派給群組、使用者或裝置，並檢查是否有任何安裝失敗。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: cce77976ea0cb31596ca0a1fd6c4becc9e3cee34
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55833594"
---
# <a name="configure-ios-update-policies-in-intune"></a>在 Intune 中設定 iOS 更新原則

軟體更新原則可讓您強制受監督的 iOS 裝置自動安裝最新可用的 OS 更新。 這項功能僅適用於受監督的裝置。 設定原則時，您可以新增不希望裝置安裝更新的天數和時間。 

裝置大約每隔 8 小時簽入 Intune 一次。 如果有更新可用，而且不在限制期間內，則裝置會下載並安裝最新的 OS 更新。 更新裝置不需要任何使用者互動。 原則不會阻止使用者手動更新 OS。

這項功能支援執行 iOS 10.3 和更新版本的裝置。 iOS 11.3 和更新版本提供延遲設定。

## <a name="configure-the-policy"></a>設定原則
1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [軟體更新] > [iOS 更新原則] > [建立]。
4. 為原則輸入名稱和描述。
5. 選取 [設定]。 

    輸入不強制 iOS 裝置安裝最新更新時的詳細資料。 這些設定會建立受限制的時間範圍。 您可以設定 [星期幾]、[時區]、[開始時間] 和 [結束時間]，以及是否要使用 [軟體更新的延遲可見度 (天)] 來輸入使用者。 您可以選取 1 到 90 天的軟體更新延遲範圍。 當延遲到期時，使用者會收到通知，以更新為觸發延遲時可用的最舊版 OS。 若要退出設定軟體更新延遲，請輸入 0。 這些更新設定只會套用到受監督的 iOS 裝置。
  
    例如，如果 **1 月 1 日**提供 iOS 12.a，且您將 [Delay OS Updates] \(延遲 OS 更新\) 設定為 **5 天**，該特定版本將不會在任何指派給該設定檔之終端使用者裝置上顯示為可用的更新。 在發行後的**第六天**，該更新將會顯示為可用，且所有終端使用者都可以自由起始更新。


6. 按一下 [確定] 以儲存您的變更。 選取 [建立] 來建立原則。

設定檔隨即建立，並顯示在原則清單中。 Apple MDM 不允許您強制裝置依特定時間或日期安裝更新。 

## <a name="change-the-restricted-times-for-the-policy"></a>變更原則的限定時間

1. 在 [軟體更新] 中，選取 [iOS 更新原則]。
2. 選擇現有的原則 > [屬性]。
3. 更新受限制的時間：
    
    1. 選擇每星期幾
    2. 選擇會套用此原則的時區
    3. 輸入列入封鎖清單時段的開始與結束時間

    > [!NOTE]
    > 如果 [開始時間] 和 [結束時間] 都設為上午 12 點，則會關閉維護時間檢查。

## <a name="assign-the-policy-to-users"></a>指派原則給使用者

現有的原則會指派給群組、使用者或裝置。 指派後即會套用原則。

1. 在 [軟體更新] 中，選取 [iOS 更新原則]。
2. 選擇現有的原則 > [指派]。 
3. 選取要包含或排除此原則的 Azure Active Directory 群組、使用者或裝置。
4. 選擇 [儲存] 將原則部署至群組。

要套用原則之使用者的裝置將會接受更新合規性的評估。 此原則也支援無使用者的裝置。

## <a name="monitor-device-installation-failures"></a>監視裝置安裝的錯誤
<!-- 1352223 -->
[軟體更新] > [iOS 裝置的安裝失敗] 會顯示要套用更新原則、嘗試更新及無法更新的受監督 iOS 裝置清單。 針對每部裝置，您可以檢視狀態，以了解為何尚未自動更新裝置。 此清單中不會顯示狀況良好的最新裝置。 「最新」裝置包含裝置本身可支援的最新更新。

