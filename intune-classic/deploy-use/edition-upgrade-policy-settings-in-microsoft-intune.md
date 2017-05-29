---
title: "Windows 版本升級原則設定 | Microsoft Docs"
description: "了解如何透過 Intune 自動將 Windows 10 裝置升級到不同的版本。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 81061f032ef2079695f45e54e99cbb6479252bed
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="windows-edition-upgrade-policy-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Windows 版本升級原則設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune「版本升級原則」可讓您自動將執行下列 Windows 10 版本之一的裝置升級至不同的版本：
* Windows 10 Desktop
* Windows 10 Holographic
* Windows 10 Mobile

支援下列升級路徑：
- 從 Windows 10 Pro 到 Windows 10 Enterprise
- 從 Windows 10 Home 到 Windows 10 Education
- 從 Windows 10 Mobile 到 Windows 10 Mobile Enterprise
- 從 Windows 10 Holographic Pro 到 Windows 10 Holographic Enterprise

## <a name="before-you-start"></a>開始之前
在開始將裝置升級至最新版本之前，您需要下列其中一項：
* 可以在您以原則設為目標的所有裝置上 (適用於 Windows 10 Desktop 版本)，安裝新版本 Windows 的有效產品金鑰。 您可以使用多次啟用金鑰 (MAK) 或金鑰管理伺服器 (KMS) 金鑰。
**或**來自 Microsoft 的授權檔案，其中包含在您以原則設為目標的所有裝置上 (適用於 Windows 10 行動裝置版和 Windows 10 全像攝影版)，安裝新版本 Windows 的授權資訊。
* 必須在 Microsoft Intune 中註冊您的目標 Windows 10 裝置。 您無法將版本升級原則和執行 Intune 電腦用戶端軟體的電腦搭配使用。

## <a name="edition-upgrade-policy-settings"></a>版本升級原則設定

|設定名稱|詳細資料|
|-|-|
|**Name**|輸入版本升級原則的名稱。|
|**說明**|選擇性地輸入可協助您在 Intune 主控台中識別該原則的描述。
|**升級的目標版本**|從下拉式清單選取您想將目標裝置升級到的 Windows 10 Desktop、Windows 10 Holographic 或 Windows 10 Mobile 版本。
|**產品金鑰**|指定您從 Microsoft 取得的產品金鑰，可用來升級所有 Windows 10 Desktop 目標裝置。<br>建立包含產品金鑰的原則之後，您便無法在稍後編輯產品金鑰。 這是因為金鑰基於安全性考量而隱藏。 若要變更產品金鑰，您必須再次輸入完整金鑰。
|**授權檔**|選擇 [瀏覽] 以選取您從 Microsoft 取得的授權檔，包含要將目標裝置升級到的 Windows 全像攝影版或 Windows 10 行動裝置版的授權資訊。

### <a name="see-also"></a>請參閱
[使用 Microsoft Intune 原則管理裝置的設定及功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

