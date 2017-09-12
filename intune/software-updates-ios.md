---
title: "設定 iOS 更新原則"
titlesuffix: Azure portal
description: "設定 iOS 更新原則，強制受監督的 iOS 裝置自動安裝最新可用的軟體更新。"
keywords: 
author: dougeby
manager: dougeby
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6334421-85e1-4457-9c44-e5db8d4ee00e
ms.openlocfilehash: a119f00cc8a92aa6cf7a1009f910df817593e0e8
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2017
---
# <a name="configure-ios-update-policies"></a>設定 iOS 更新原則
設定 iOS 更新原則，強制受監督的 iOS 裝置自動安裝最新可用的軟體更新。 當您不想要裝置安裝更新時，可以選擇設定星期幾和時間。

## <a name="configure-the-ios-update-policy"></a>設定 iOS 更新原則
1. 請前往 Azure 入口網站的 [Intune] 刀鋒視窗。
2. 在 [Intune] 刀鋒視窗中，選擇 [軟體更新] > [iOS 更新原則]。
4. 在 [原則] 刀鋒視窗中，選擇 [建立]，然後輸入原則的名稱和描述。
5. 選取 [設定] > [設定]，輸入不強制 iOS 裝置安裝最新更新時的詳細資料。
6. 選擇 [確定] 儲存這項設定。 現在您已回到 [建立更新原則] 刀鋒視窗。 選擇 [建立] 建立原則並儲存您的設定。

設定檔隨即建立，並出現在 [iOS 更新原則] 清單刀鋒視窗上。

## <a name="assign-an-ios-update-policy-to-users"></a>將 iOS 更新原則指派給使用者
若要將 iOS 更新原則指派給使用者，請選擇您已設定的原則。 現有的原則位於 [軟體更新] > [iOS 更新原則] 刀鋒視窗中。
1. 選擇您想要指派給使用者的原則，然後選擇 [指派]。 這會開啟刀鋒視窗讓您選取 Azure Active Directory 安全性群組，並將其指派給原則。
2. 選擇 [選取群組] 會開啟刀鋒視窗顯示 Azure AD 安全性群組。 選擇 [選取] 將原則部署給使用者。

您已對使用者套用此原則。 要套用原則之使用者的裝置將會接受更新合規性評估。

## <a name="change-the-restricted-days-for-the-policy"></a>變更原則限於星期幾
1. 在 [軟體更新] 刀鋒視窗中，選擇 [iOS 更新原則]。
2. 選取您想要更新的 iOS 更新原則。
3. 選取 [屬性] 更新限於星期幾的資訊。
