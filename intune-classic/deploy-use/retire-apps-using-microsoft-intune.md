---
title: "淘汰應用程式"
description: "了解如何使用 Intune 停用或解除安裝應用程式。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6fbf0805-1144-4e08-bafd-4f181d932bf2
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1851fa03d36ffe42a49fd557cdd0c2c6250726f4
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="retire-apps-using-microsoft-intune"></a>使用 Microsoft Intune 淘汰應用程式

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

若要淘汰應用程式，只要將它解除安裝即可。 當您使用 Intune 來部署和管理應用程式時，行動裝置和 Windows 電腦的應用程式解除安裝程序都一樣。 應用程式必須支援解除安裝流程，這個程序才能順利完成。

## <a name="uninstall-an-app"></a>解除安裝應用程式

1.  在 [Microsoft Intune 系統管理主控台](https://manage.microsoft.com)中，選擇 [應用程式] &gt;[應用程式]。

2.  選取您要解除安裝的應用程式 (先前已部署的應用程式)，然後選擇 [管理部署]。

3.  在 [部署動作]  頁面上，從 [核准]  欄中選取 [解除安裝]  。

當裝置或電腦接著檢查應用程式時，即會解除安裝應用程式。

### <a name="see-also"></a>另請參閱
[在 Microsoft Intune 中新增應用程式](add-apps.md)
