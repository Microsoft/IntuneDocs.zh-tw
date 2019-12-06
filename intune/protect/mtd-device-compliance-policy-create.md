---
title: 使用 Microsoft Intune 建立 MTD 裝置相容性原則
titleSuffix: Microsoft Intune
description: 建立使用您 MTD 夥伴威脅層級的 Intune 裝置相容性原則，判斷行動裝置是否可以存取公司資源。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 504c77fb56918cf97312e70f50b38356f9f7efef
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409706"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>使用 Intune 建立 Mobile Threat Defense (MTD) 裝置合規性原則

搭配 MTD 的 Intune 可協助您偵測行動裝置上的威脅及評估其風險。 您可以建立評估風險的 Intune 裝置合規性原則規則，來判斷裝置是否符合規範。 接著，您可以使用[條件式存取原則](create-conditional-access-intune.md)，根據裝置合規性來封鎖對服務的存取。

> [!NOTE]
> 此資訊適用於所有 Mobile Threat Defense 合作夥伴。

## <a name="before-you-begin"></a>開始之前

在 MTD 的設定過程中，您已在 MTD 夥伴主控台中建立一項原則來將各種威脅分類為高、中和低。 您現在需要在 Intune 裝置合規性原則中設定 Mobile Threat Defense 等級。

搭配 Intune 建立裝置合規性原則的必要條件：

- 設定 MTD 與 Intune 整合

## <a name="to-create-an-mtd-device-compliance-policy"></a>建立 MTD 裝置合規性原則

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [裝置]   > [合規性原則]   > [建立原則]  。

3. 指定裝置合規性原則的 [名稱]  、[描述]  ，選取 [平台]  ，然後選取 [設定]  區段下的 [設定]  。

4. 在 [相容性原則]  窗格中，選擇 [裝置健全狀況]  。

5. 在 [裝置健全狀況]  窗格中，從 [裝置須等於或低於裝置威脅等級]  的下拉式清單中選擇行動威脅等級。

   - **安全**：這個層級最安全。 裝置不能在具有任何威脅的同時還能存取公司資源。 發現任何威脅時，即會將裝置評估為不相容。

   - **低**︰如果只有低層級的威脅，則會將裝置評估為符合規範。 任何更高等級的威脅都會使裝置處於不相容狀態。

   - **中**︰如果在裝置上發現的威脅為低或中層級，則會將裝置評估為符合規範。 如果偵測到高層級的威脅，則會將裝置判斷為不相容。

   - **高**：這個層級最不安全。 這會允許所有威脅等級，並只將 Mobile Threat Defense 用於回報用途。 裝置必須要有使用此裝置啟用的 MTD 應用程式。

6. 選取 [確定]  兩次，然後選取 [建立]  來建立原則。

> [!IMPORTANT]
> 如果您針對 Office 365 或其他服務建立條件式存取原則，就會評估裝置合規性評估，並封鎖不符合規範的裝置，使其無法存取公司資源，直到裝置中的威脅獲得解決為止。

## <a name="to-assign-an-mtd-device-compliance-policy"></a>指派 MTD 裝置合規性原則

將裝置合規性原則指派給使用者：

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [裝置]   > [合規性原則]  。

3. 選取您想要指派給使用者的原則，然後選取 [指派]  。 使用可用的選項來「包括」  及「排除」  接收此原則的群組。  

4. 選取 [儲存] 以完成指派。 當您儲存指派時，原則便會部署至選取的使用者，且系統會針對他們的裝置進行合規性評估。

## <a name="next-steps"></a>後續步驟

[使用 Intune 來啟用 MTD](mtd-connector-enable.md)
