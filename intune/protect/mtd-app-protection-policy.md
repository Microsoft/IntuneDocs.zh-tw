---
title: 使用 Intune 建立 Mobile Threat Defense (MTD) 應用程式防護原則
titleSuffix: Microsoft Intune
description: 使用 Microsoft Intune 建立 Mobile Threat Defense (MTD) 應用程式防護原則。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 15d986bc5017a44571c6194f9c6b53167b671349
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794416"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>使用 Intune 建立 Mobile Threat Defense 應用程式防護原則

> [!NOTE] 
> 此文章適用於所有支援應用程式防護原則的行動威脅防護 (MTD) 合作夥伴：Better Mobile (Android)、Zimperium (iOS)、Lookout for Work (Android/iOS)。

搭配 MTD 的 Intune 可協助您偵測行動裝置上的威脅及評估其風險。 您可以建立評估風險的 Intune 應用程式防護原則規則，來判斷裝置是否受允許存取公司資料。 

## <a name="before-you-begin"></a>開始之前

在 MTD 的設定過程中，您已在 MTD 夥伴主控台中建立一項原則來將各種威脅分類為高、中和低。 您現在需要在 Intune 應用程式防護則中設定 Mobile Threat Defense 等級。

使用 MTD 建立應用程式防護原則的必要條件：

- 設定 MTD 與 Intune 整合。 若沒有此整合，MTD 應用程式防護原則將不會有作用。

## <a name="to-create-an-mtd-app-protection-policy"></a>建立 MTD 應用程式防護原則

1. 移至 [Azure 入口網站](https://portal.azure.com/)，並使用您的 Intune 認證登入。

2. 在 [Azure 儀表板]  中，選擇左功能表中的 [All services] (所有服務)  ，然後在文字方塊篩選中鍵入 **Intune**。

3. 選擇 [Intune]  ，即會開啟 [Intune 儀表板]  。

4. 在 [Intune 儀表板]  上，選擇 [用戶端應用程式]  ，然後選擇 [管理]  區段下的 [應用程式防護原則]  。

5. 選擇 [建立原則]  ，輸入**名稱**、**描述**，選取 [平台]  。 

6. 在 [條件式啟動]  窗格中，於 [裝置狀況]  表格下，從 [裝置威脅允許上限]  底下的下拉式清單選擇 [行動裝置威脅等級]。

    a.  **安全**：這個層級最安全。 裝置不能在具有任何威脅的同時還能存取公司資源。 發現任何威脅時，即會將裝置評估為不相容。

    b.  **低**︰如果只有低層級的威脅，則會將裝置評估為符合規範。 任何更高等級的威脅都會使裝置處於不相容狀態。

    c.  **中**︰如果在裝置上發現的威脅為低或中層級，則會將裝置評估為符合規範。 如果偵測到高層級的威脅，則會將裝置判斷為不相容。

    d.  **高**：這個層級最不安全。 這會允許所有威脅等級，並只將 Mobile Threat Defense 用於回報用途。 裝置必須要有使用此裝置啟用的 MTD 應用程式。

7. 按一下 [儲存]  兩次，然後選擇 [建立]  。

## <a name="to-assign-an-mtd-app-protection-policy"></a>指派 MTD 應用程式防護原則

若要將裝置合規性原則指派給使用者，請選擇您先前設定的原則。 現有的原則可以在 [裝置相容性 - 政策]  窗格中找到。

1. 選擇您想要指派給使用者的原則，然後選擇 [指派]  。 這個動作會開啟窗格讓您選取 [Azure Active Directory 安全性群組]  ，並將它們指派給原則。

2. 選擇 [選取要納入的群組]  會開啟顯示 Azure AD 安全性群組的窗格。 選擇 [選取]  會將原則部署給使用者。

> [!NOTE] 
> 您已對使用者套用此原則。 Intune 應用程式會評估原則目標使用者所使用的裝置，以在目標應用程式上存取公司資料。

## <a name="next-steps"></a>後續步驟  

- 深入了解 Microsoft Intune 中的 [Mobile Threat Defense](~/protect/mobile-threat-defense.md)。
