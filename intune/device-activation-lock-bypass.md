---
title: "使用 Intune 略過 iOS 啟用鎖定"
titlesuffix: Azure portal
description: "了解如何使用 Intune 略過 iOS 啟用鎖定，來存取鎖定的裝置。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/22/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e3cd1c7d68cba09c3483cd346772e9791d66c490
ms.sourcegitcommit: 001577b700f634da2fec0b44af2a378150d1f7ac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2017
---
# <a name="bypass-activation-lock-on-supervised-ios-devices-with-intune"></a>使用 Intune 在受監督的 iOS 裝置上略過啟用鎖定


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune 可以協助您管理 iOS 啟用鎖定，這是 iOS 8.0 和更新版本裝置之「尋找我的 iPhone」應用程式中的一項功能。 當使用者在裝置上開啟「尋找我的 iPhone」應用程式時，啟用鎖定會自動啟用。 啟用之後，就必須輸入使用者的 Apple ID 和密碼，才能夠讓所有人：

- 關閉「尋找我的 iPhone」
- 清除裝置
- 重新啟動裝置

## <a name="how-activation-lock-affects-you"></a>啟用鎖定對您的影響

雖然啟用鎖定可以協助保護 iOS 裝置，並提高裝置遺失或遭竊時的復原機會，但是這項功能可能會為身為 IT 系統管理員的您帶來一些挑戰。 例如：

- 一位使用者在裝置上設定啟用鎖定。 使用者之後離職並歸還裝置。 如果沒有使用者的 Apple ID 和密碼，就無法重新啟動裝置。
- 您需要一份啟用鎖定已啟用之所有裝置的報表。
- 在重新整理組織中的裝置期間，您想要將某些裝置重新指派給不同的部門。 您只能重新指派啟用鎖定未啟用的裝置。

為了協助解決這些問題，Apple 在 iOS 7.1 中引進了啟用鎖定略過。 啟用鎖定略過可讓您從沒有使用者的 Apple ID 和密碼的受監督裝置移除啟用鎖定。 受監督的裝置會產生裝置特定啟用鎖定略過碼，並儲存在 Apple 啟用伺服器上。

>[!TIP]
>iOS 裝置的受監督模式可讓您使用 Apple Configurator 鎖定裝置，並將功能限制在特定商務用途。 受監督的模式僅用於屬公司擁有的裝置。

您可以在 [Apple 網站](https://support.apple.com/HT201365) \(英文\) 上深入了解「啟用鎖定」。

## <a name="how-intune-helps-you-manage-activation-lock"></a>Intune 如何協助您管理啟用鎖定
Intune 可以要求執行 iOS 8.0 和更新版本之受監督裝置的啟用鎖定狀態。 僅針對受監督的裝置，Intune 可以擷取啟用鎖定略過碼並直接發給裝置。 如果已抹除裝置，您可以使用空白使用者名稱和代碼作為密碼，進而直接存取裝置。

**使用 Intune 管理啟用鎖定對公司的好處包括：**

- 使用者可以獲得「尋找我的 iPhone」應用程式的安全性優點。
- 您可以讓使用者執行工作，並使其知道在需要重新規劃裝置時，您可將裝置淘汰或解除鎖定。

## <a name="before-you-start"></a>開始之前
在您可以略過裝置上的啟用鎖定之前，必須先遵循下列指示啟用它：

1. 使用[如何設定裝置限制設定](/intune-azure/configure-devices/how-to-configure-device-restrictions)中的資訊，來設定適用於 iOS 的 Intune 裝置限制設定檔。
2. 在 [iOS 的裝置限制設定](device-restrictions-ios.md) 中，於 [一般] 設定下，啟用 [啟用鎖定] 選項。
3. 儲存設定檔，然後將它[指派](device-profile-assign.md)給您想要管理啟用鎖定略過的裝置。


## <a name="how-to-use-activation-lock-bypass"></a>如何使用啟用鎖定略過

>[!IMPORTANT]
>略過裝置上的啟用鎖定之後，如果「尋找我的 iPhone」應用程式處於開啟狀態，則會自動套用新的啟用鎖定。 因此，**您應該實際擁有裝置，才能執行這個程序**。

Intune 的**略過啟用鎖定**遠端裝置動作即使沒有使用者的 Apple ID 及密碼，也可以從 iOS 裝置移除啟用鎖定。 當您略過啟用鎖定之後，裝置會在 [尋找我的 iPhone] 應用程式會啟動再次開啟啟用鎖定。 僅當您能夠實際使用裝置時，才略過啟用鎖定。

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。
5. 從您管理的裝置清單中，選擇受監督的 iOS 裝置，然後選擇 [略過啟用鎖定] 裝置遠端動作。

## <a name="next-steps"></a>後續步驟

您可以在 [管理裝置] 工作負載中，於裝置的詳細資料頁面上，檢查解除鎖定要求的狀態。
