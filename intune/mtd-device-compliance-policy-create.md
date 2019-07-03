---
title: 使用 Microsoft Intune 建立 MTD 裝置相容性原則
titleSuffix: Microsoft Intune
description: 建立使用您 MTD 夥伴威脅層級的 Intune 裝置相容性原則，判斷行動裝置是否可以存取公司資源。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b58ee82e44e8aa8d68c0fb00c4497cc0455ed21d
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67528634"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>使用 Intune 建立 Mobile Threat Defense (MTD) 裝置合規性原則

> [!NOTE] 
> 此資訊適用於所有 Mobile Threat Defense 合作夥伴。

搭配 MTD 的 Intune 可協助您偵測行動裝置上的威脅及評估其風險。 您可以建立評估風險的 Intune 裝置合規性原則規則，來判斷裝置是否符合規範。 接著，您可以使用[條件式存取原則](create-conditional-access-intune.md)，根據裝置合規性來封鎖對服務的存取。

## <a name="before-you-begin"></a>開始之前

在 MTD 的設定過程中，您已在 MTD 夥伴主控台中建立一項原則來將各種威脅分類為高、中和低。 您現在需要在 Intune 裝置合規性原則中設定 Mobile Threat Defense 等級。

搭配 Intune 建立裝置合規性原則的必要條件：

-   設定 MTD 與 Intune 整合

## <a name="to-create-an-mtd-device-compliance-policy"></a>建立 MTD 裝置合規性原則

1.  移至 [Azure 入口網站](https://portal.azure.com/)，並使用您的 Intune 認證登入。

2.  在 [Azure 儀表板]  中，選擇左功能表中的 [All services] (所有服務)  ，然後在文字方塊篩選中鍵入 **Intune**。

3.  選擇 [Intune]  ，即會開啟 [Intune 儀表板]  。

4. 在 [Intune 儀表板]  上，選擇 [裝置合規性]  ，然後選擇 [管理]  區段下的 [原則]  。

5.  選擇 [建立原則]  ，輸入裝置合規性 [名稱]  、[描述]  ，選取 [平台]  ，然後選擇 [設定]  區段下的 [設定]  。

6.  在 [相容性原則]  窗格中，選擇 [裝置健全狀況]  。

7.  在 [裝置健全狀況]  窗格中，從 [Require the device to be at or under the Device Threat Level] (需要裝置層級不高於裝置威脅等級)  下方的下拉式清單中選擇行動威脅等級。

    a.  **安全**：這個層級最安全。 裝置不能在具有任何威脅的同時還能存取公司資源。 發現任何威脅時，即會將裝置評估為不相容。

    b.  **低**︰如果只有低層級的威脅，則會將裝置評估為符合規範。 任何更高等級的威脅都會使裝置處於不相容狀態。

    c.  **中**︰如果在裝置上發現的威脅為低或中層級，則會將裝置評估為符合規範。 如果偵測到高層級的威脅，則會將裝置判斷為不相容。

    d.  **高**：這個層級最不安全。 這會允許所有威脅等級，並只將 Mobile Threat Defense 用於回報用途。 裝置必須要有使用此裝置啟用的 MTD 應用程式。

8.  按一下 [確定]  兩次，然後選擇 [建立]  。

> [!IMPORTANT]
> 如果您針對 Office 365 或其他服務建立條件式存取原則，就會評估裝置合規性評估，並封鎖不符合規範的裝置，使其無法存取公司資源，直到裝置中的威脅獲得解決為止。

## <a name="to-assign-an-mtd-device-compliance-policy"></a>指派 MTD 裝置合規性原則

若要將裝置合規性原則指派給使用者，請選擇您先前設定的原則。 現有的原則可以在 [裝置相容性 - 政策]  窗格中找到。

1. 選擇您想要指派給使用者的原則，然後選擇 [指派]  。 這個動作會開啟窗格讓您選取 **Azure Active Directory 安全性群組**，並將其指派給原則。

2. 選擇 [Select groups to include] (選取要包含的群組)  會開啟顯示 Azure AD 安全性群組的窗格。  選擇 [選取]  會將原則部署給使用者。

    > [!NOTE] 
    > 您已對使用者套用此原則。 要套用原則之使用者的裝置將會接受相容性評估。

## <a name="next-steps"></a>後續步驟

- [使用 Intune 來啟用 MTD](mtd-connector-enable.md)
