---
title: "部署 App"
description: "本主題說明您在開始使用 Intune 部署應用程式之前必須了解的概念。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 13c4046ed431dc25bda9a2facc59dbcb6d3e5ab5
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="deploy-apps-with-microsoft-intune"></a>使用 Microsoft Intune 部署應用程式

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主題說明在開始使用 Microsoft Intune 部署應用程式之前，您必須了解的一些概念。


## <a name="app-deployment-actions"></a>應用程式部署動作
當您部署應用程式時，可以選擇下列其中一個部署動作：

-   **必要安裝** - 應用程式會安裝到裝置，而且無須使用者介入。

    > [!TIP]
    > 針對未處於受監督模式的 iOS 裝置，以及針對所有 Android 裝置，使用者必須在安裝之前接受應用程式提供。
    >
    >  如果使用者解除安裝您部署為必要安裝的應用程式，Intune 會在下一個清查週期 (通常是每七天發生) 之後自動重新安裝應用程式。

-   **可用安裝** - 應用程式會顯示在公司入口網站中，讓使用者隨需安裝。

-   **解除安裝** - 應用程式會從裝置解除安裝。

-   **不適用** - 應用程式不會顯示在公司入口網站上，也不會安裝在任何裝置上。

#### <a name="understand-which-deployment-actions-are-available-for-each-installer-type"></a>了解每種安裝程式類型可用的部署動作

|安裝程式類型|必要安裝|可用安裝|解除安裝|不適用|
|------------------|--------------------|---------------------|-------------|------------------|
|Windows 應用程式套件 (部署到使用者群組)|是|是|是|是|
|Windows 應用程式套件 (部署到裝置群組)|是|否|是|是|
|行動裝置應用程式套件 (部署到使用者群組)|是|是|是|是|
|行動裝置應用程式套件 (部署到裝置群組)|是|否|是|是|
|Windows Installer (部署到使用者群組)|否|是|否|是|
|Windows Installer (部署到裝置群組)|是|否|是|是|
|外部連結 (部署到使用者群組)|否|是|否|是|
|外部連結 (部署到裝置群組)|否|否|否|否|
|App Store 中的受管理 iOS 應用程式 (部署到使用者群組)|是|是|是|是|
|App Store 中的受管理 iOS 應用程式 (部署到裝置群組)|是|否|是|是|
> [!TIP]
> 當您部署應用程式時，如果選取使用者和裝置群組，則可以只將應用程式部署為 [可用安裝]。

## <a name="deployment-conflicts"></a>部署衝突
當裝置收到兩個具有相同部署動作的部署時，適用下列規則：

-   部署到裝置群組的優先順序高於部署到使用者群組。 不過，如果應用程式部署到具有部署動作 [可用] 的使用者群組，而且相同的應用程式也部署到具有部署動作 [不適用] 的裝置群組，則在公司入口網站中會將應用程式設為可供使用者安裝。

-   安裝動作的優先順序高於解除安裝動作。

-   若裝置同時收到必要及可用安裝，表示兩個動作皆須執行。 也就是說，使用者可以在必要的安裝開始之前，從公司入口網站安裝可用的應用程式。


## <a name="next-steps"></a>後續步驟

深入了解如何[在 Microsoft Intune 中部署應用程式](deploy-apps-in-microsoft-intune.md)。
