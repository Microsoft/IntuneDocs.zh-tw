---
title: 準備好設定適用於 Windows 10 的應用程式保護原則
description: 在 Azure AD 中設定行動應用程式管理 (MAM) 提供者
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 04/18/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ebc7cfc8-40b9-47c2-8357-d392ebbb27c8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9b91d3740ead5815974d7ffee67c15b7769b0210
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>準備好設定適用於 Windows 10 的應用程式保護原則

[!INCLUDE [note for both-portals](../includes/note-for-both-portals.md)]

在建立 Windows 10 應用程式保護原則之前，您必須在 Azure AD 中設定 MAM 提供者，以啟用適用於 Windows 10 的行動應用程式管理 (MAM)。 此設定可讓您在使用 Intune 建立新的 Windows 資訊保護 (WIP) 原則時，定義註冊狀態。

> [!NOTE]
> 註冊狀態可以是 MAM 或行動裝置管理 (MDM)。

## <a name="to-configure-the-mam-provider"></a>設定 MAM 提供者

1.  移至 [Azure 入口網站](https://portal.azure.com/)，並使用您的 Intune 認證登入。

2.  從左功能表中，選擇 [Azure Active Directory]。

    ![MAM 提供者設定](../media/AppManagement/mam-provider-sc-1.png)

3.  [Azure AD] 刀鋒視窗隨即開啟，選擇 [行動性 (MDM 與 MAM)]，然後按一下 [Microsoft Intune]。

    ![行動性 (MDM 與 MAM)](../media/AppManagement/mam-provider-sc-2.png)

4.  設定刀鋒視窗隨即開啟，首先選擇 [還原預設的 MAM URL]，然後設定下列各項︰

    a.  MAM 使用者範圍︰您可以使用 MAM 保護使用 Windows 10 裝置之特定使用者群組，或是所有使用者的公司資料。

    b.  MAM 使用規定 URL：MAM 服務之使用規定端點的 URL。 這是用來向使用者顯示 MAM 服務規定。

    c.  MAM 探索 URL：這是裝置在需要套用應用程式保護原則時會尋找的 URL。

    d.  MAM 合規性 URL：

5.  一旦您設定了這些設定，請選擇 [儲存]。

## <a name="next-steps"></a>接下來的步驟

[建立 WIP 應用程式保護原則 (英文)](/intune-classic/deploy-use/create-windows-information-protection-policy-with-intune)
