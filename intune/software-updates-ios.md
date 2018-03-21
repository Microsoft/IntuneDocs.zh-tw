---
title: "在 Microsoft Intune 中設定 iOS 更新原則"
titlesuffix: 
description: "設定 iOS 更新原則，強制受監督的 iOS 裝置自動安裝最新可用的軟體更新。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.openlocfilehash: 6ba354fb3b39544f09363651abfd9e1a5c0f6154
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="configure-ios-update-policies-in-microsoft-intune"></a>在 Microsoft Intune 中設定 iOS 更新原則
設定 iOS 更新原則，強制受監督的 iOS 裝置自動安裝最新可用的軟體更新。 當您不想要裝置安裝更新時，可以選擇設定星期幾和時間。

## <a name="configure-the-ios-update-policy"></a>設定 iOS 更新原則
1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [監視 + 管理] 區段。
2. 在 [Intune] 窗格中，選擇 [軟體更新] > [iOS 更新原則]。
4. 在 [原則] 窗格中，選擇 [建立]，然後輸入原則的名稱和描述。
5. 選取 [設定] > [設定]，輸入不強制 iOS 裝置安裝最新更新時的詳細資料。
6. 選擇 [確定] 儲存這項設定。 現在您已回到 [建立更新原則] 窗格。 選擇 [建立] 建立原則並儲存您的設定。

設定檔隨即建立，並出現在 [iOS 更新原則] 清單窗格上。

## <a name="assign-an-ios-update-policy-to-users"></a>將 iOS 更新原則指派給使用者
若要將 iOS 更新原則指派給使用者，請選擇您已設定的原則。 現有的原則位於 [軟體更新] > [iOS 更新原則] 窗格中。
1. 選擇您想要指派給使用者的原則，然後選擇 [指派]。 窗格會隨即開啟，使您能夠選取 Azure Active Directory 安全性群組，並將其指派至原則。
2. 選擇 [選取群組] 會開啟窗格顯示 Azure AD 安全性群組。
3. 選擇 [儲存] 將原則部署給使用者。

您已對使用者套用此原則。 要套用原則之使用者的裝置將會接受更新合規性評估。

## <a name="change-the-restricted-days-for-the-policy"></a>變更原則限於星期幾
1. 在 [軟體更新] 窗格中，選擇 [iOS 更新原則]。
2. 選取您想要更新的 iOS 更新原則。
3. 選取 [屬性] > [設定] 更新限制天數的資訊。

## <a name="monitor-ios-devices-with-older-ios-versions"></a>監視舊版 iOS 的 iOS 裝置
<!-- 1352223 -->
您可從 [軟體更新] > [iOS 更新原則] 窗格取得**過期的 iOS 裝置**報表。 在此報表中，您可以檢視受監督的 iOS 裝置清單，這些是 iOS 更新原則之前鎖定且無法更新的裝置。 針對每部裝置，您可以檢視狀態，以了解為何尚未自動更新裝置。
