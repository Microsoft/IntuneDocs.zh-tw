---
title: 在 Microsoft Intune 中設定 iOS 軟體更新原則
titlesuffix: ''
description: 設定 iOS 更新原則，強制受監督的 iOS 裝置自動安裝最新可用的軟體更新。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.openlocfilehash: 39432d09bea822c25ca9e11181a11a1e2298dfef
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="configure-ios-update-policies-in-microsoft-intune"></a>在 Microsoft Intune 中設定 iOS 更新原則

軟體更新原則能讓您強制受監督的 iOS 裝置執行 iOS 10.3 及更新版本，以自動安裝最新可用的 OS 更新。 這項功能僅適用於受監督的裝置。 當您不想要裝置安裝更新時，可以選擇設定星期幾和時間。 

當裝置簽入時，約每隔 8 小時，如果沒有可用的更新，而且不在受限制的期間，裝置會嘗試下載並安裝最新的 OS 更新。 更新裝置不需要任何使用者互動。 原則不會阻止使用者更新 OS。

## <a name="configure-the-ios-update-policy"></a>設定 iOS 更新原則
1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [軟體更新] > [iOS 更新原則]。
4. 在 [原則] 窗格中，選擇 [建立]，然後輸入原則的名稱和描述。
5. 選取 [設定] > [設定]，輸入不強制 iOS 裝置安裝最新更新時的詳細資料。 您可以設定每星期幾、時區、開始時間和結束時間。
6. 選擇 [確定] 儲存這項設定。 現在您已回到 [建立更新原則] 窗格。 選擇 [建立] 建立原則並儲存您的設定。

設定檔隨即建立，並出現在 [iOS 更新原則] 清單窗格上。 Apple MDM 不允許強制裝置依特定時間或日期安裝更新的能力。 

## <a name="change-the-restricted-times-for-the-policy"></a>變更原則的限定時間

1.  在 [軟體更新] 刀鋒視窗中，選擇 [iOS 更新原則]。
2.  選取您想要更新的 iOS 更新原則。
3.  選取 [屬性] 並更新限制的時間資訊。
4.  選擇每星期幾
5.  此原則會套用的時區
6.  列入封鎖清單時段的開始與結束時間

## <a name="assign-an-ios-update-policy-to-users"></a>將 iOS 更新原則指派給使用者

若要將 iOS 更新原則指派給使用者，請選擇您已設定的原則。 現有的原則位於 [軟體更新] > [iOS 更新原則] 窗格中。

1. 選擇您想要指派給使用者的原則，然後選擇 [指派]。 窗格會隨即開啟，使您能夠選取 Azure Active Directory 安全性群組，並將其指派至原則。
2. 選擇 [選取群組] 以開啟顯示 Azure AD 安全性群組的窗格。 透過指派要包含以及排除的群組，決定誰可以存取原則。
3. 選擇 [儲存] 將原則部署給使用者。

您已對使用者或裝置套用此原則。 要套用原則之使用者的裝置將會接受更新合規性評估。 此原則也支援無使用者的裝置。

## <a name="monitor-ios-device-installation-failures"></a>監視 iOS 裝置安裝的錯誤
<!-- 1352223 -->
[軟體更新] 窗格提供 [iOS 裝置安裝錯誤] 報表。 在此報表中，您可以檢視受監督的 iOS 裝置清單，這些是 iOS 更新原則之前鎖定、嘗試更新但無法更新的裝置。 針對每部裝置，您可以檢視狀態，以了解為何尚未自動更新裝置。 此清單中不會顯示狀況良好的最新裝置。 我們將最新定義為裝置本身可支援的最新更新。
