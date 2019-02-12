---
title: 在 Microsoft Intune 中使用範圍標籤篩選原則 - Azure | Microsoft Docs
description: 使用範圍標籤將組態設定檔篩選至特定角色。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9441f1c69e3d445d6174521ad2c9ef5c7a6db2be
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835532"
---
# <a name="use-scope-tags-to-filter-policies"></a>使用範圍標籤篩選原則

範圍標籤可讓您透過所建立的自訂標籤來篩選原則。 您可以將範圍標籤套用至角色和應用程式。

例如，建立稱為「工程部門」的範圍標籤，並指派給與工程部門相關的組態設定檔。 將該相同的標籤指派給「工程管理員」角色。 他們只會看到具有「工程部門」標籤的原則。

## <a name="to-create-a-scope-tag"></a>建立範圍標籤

選擇 [角色] > [範圍 (標籤)] > [建立]。

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>將範圍標籤新增至組態設定檔

選擇 [裝置設定] > [設定檔] > 選擇設定檔 > [屬性] > [範圍 (標籤)]。

## <a name="to-assign-a-scope-tag-to-a-role"></a>將範圍標籤指派給角色

選擇 [角色] > [所有角色] > [Policy and Profile Manager] \(原則和設定檔管理員\) > [指派] > [範圍 (標籤)]。

## <a name="to-assign-a-scope-tag-to-an-app"></a>將範圍標籤指派給應用程式

選擇 [用戶端應用程式] > [應用程式] > 選擇應用程式 > [內容] > [範圍 (標籤)] > [新增] > 選擇標籤 > **選取**  > [確定] > [儲存]。


## <a name="next-steps"></a>後續步驟

管理您的[角色](role-based-access-control.md)和[設定檔](device-profile-assign.md)。

