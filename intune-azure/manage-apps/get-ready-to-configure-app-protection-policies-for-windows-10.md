---
title: "準備好設定適用於 Windows 10 的應用程式保護原則 | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "設定 Azure AD 中的行動應用程式管理 (MAM) 提供者"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 9490951b2953f8b8c6fe3d38824053bbe75f9af1
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017


---

# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>準備好設定適用於 Windows 10 的應用程式保護原則

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

在建立 Windows 10 應用程式保護原則之前，您必須在 Azure AD 中設定 MAM 提供者，以啟用適用於 Windows 10 的行動應用程式管理 (MAM)。 此設定可讓您在使用 Intune 建立新的 Windows 資訊保護 (WIP) 原則時，定義註冊狀態。

> [!NOTE]
> 註冊狀態可以是 MAM 或行動裝置管理 (MDM)。

## <a name="to-configure-the-mam-provider"></a>設定 MAM 提供者

1.  移至 [Azure 入口網站](https://portal.azure.com/)，並使用您的 Intune 認證登入。

2.  從左功能表中，選擇 [Azure Active Directory]。

    ![MAM 提供者設定](../media/AppManagement/mam-provider-sc-1.png)

3.  [Azure AD] 刀鋒視窗隨即開啟，選擇 [行動性 (MDM 與 MAM)]，然後按一下 [Microsoft Intune]。

    ![行動性 (MDM 與 MAM)](../media/AppManagement/mam-provider-sc-1.png)

4.  設定刀鋒視窗隨即開啟，首先選擇 [還原預設的 MAM URL]，然後設定下列各項︰

    a.  MAM 使用者範圍︰您可以使用 MAM 保護使用 Windows 10 裝置之特定使用者群組，或是所有使用者的公司資料。

    b。  MAM 使用規定 URL：MAM 服務之使用規定端點的 URL。 這是用來向使用者顯示 MAM 服務規定。

    c.  MAM 探索 URL：這是裝置在需要套用應用程式保護原則時會尋找的 URL。

    d.  MAM 合規性 URL：

5.  一旦您設定了這些設定，請選擇 [儲存]。

## <a name="next-steps"></a>後續步驟

[建立 WIP 應用程式保護原則 (英文)](https://docs.microsoft.comcreate-windows-information-protection-policy-with-intune.md)

