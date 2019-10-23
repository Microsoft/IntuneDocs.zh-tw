---
title: 使用 Intune 略過 iOS 啟用鎖定
titleSuffix: Microsoft Intune
description: 了解如何使用 Intune 略過 iOS 啟用鎖定，來存取鎖定的裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7a813d3bb574ae940b0003ac451b6e76638a0dd0
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508657"
---
# <a name="bypass-activation-lock-on-supervised-ios-devices-with-intune"></a>使用 Intune 在受監督的 iOS 裝置上略過啟用鎖定


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

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
2. 在 [iOS 的裝置限制設定](../configuration/device-restrictions-ios.md) 中，於 [一般]  設定下，啟用 [啟用鎖定]  選項。
3. 儲存設定檔，然後將它[指派](../configuration/device-profile-assign.md)給您想要管理啟用鎖定略過的裝置。


## <a name="how-to-use-activation-lock-bypass"></a>如何使用啟用鎖定略過

>[!IMPORTANT]
>如有啟動「尋找我的 iPhone」應用程式，則當您略過裝置上的啟用鎖定之後，將會自動套用新的啟用鎖定。 因此，**您應該實際擁有裝置，才能執行這個程序**。

Intune 的**略過啟用鎖定**遠端裝置動作無需使用者的 Apple ID 及密碼，就能移除 iOS 裝置的啟用鎖定。 當您略過啟用鎖定之後，裝置會在 [尋找我的 iPhone] 應用程式啟動時，再次開啟啟用鎖定。 您必須能夠在裝置上實機操作，才能略過啟用鎖定。

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在 [Intune]  刀鋒視窗中，選取 [裝置]  。
4. 在 [裝置]  刀鋒視窗中，選取 [所有裝置]  。
5. 在您管理的裝置清單中，選取 [略過啟用鎖定]  裝置遠端動作。
6. 移至裝置的 [硬體] 區段，然後再複製 [條件式存取]  下方的 [Activation Lock bypass code] (啟用鎖定略過碼)  值。

    >[!NOTE]
    >請先複製略過碼，再抹除裝置。 若未先複製略過碼，就重設裝置設定，將會從 Azure 中移除該略過碼。

7. 移至裝置的 [概觀]  刀鋒視窗，然後選取 [抹除]  。
8. 裝置重設之後，會提示您輸入 *Apple ID* 及*密碼*。 將 [識別碼]  欄位保留空白，然後在 [密碼]  中輸入**略過碼**。 這會從裝置移除帳戶。 


## <a name="next-steps"></a>後續步驟

您可以在 [管理裝置]  工作負載中，於裝置的詳細資料頁面上，檢查解除鎖定要求的狀態。
