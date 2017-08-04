---
title: "開始使用應用程式"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 71093f8ac17fc6d6938f5c263a40204f89419726
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2017
---
# <a name="getting-started-with-apps"></a>開始使用應用程式

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 支援一些不同的方式，讓您將應用程式部署到您公司的裝置：

* **軟體安裝程式**：您上傳的檔案會下載到使用者的裝置
* __外部連結__：適用於當您有應用程式在公用應用程式存放區或 webapp
* **受管理應用程式**：適用於 iOS 裝置，您必須套用其他行動應用程式管理到在 App Store 裡提供的應用程式

您即將藉由指派公用市集應用程式，體驗其中一種更快速的應用程式部署方法。

__如何指派公用市集應用程式？__

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 使用 [搜尋資源]，搜尋 **Intune**。
3. 選取 [行動應用程式]，然後選取 [應用程式]。
4. 選取 [新增]，然後選取 [iOS 市集應用程式] 作為 [應用程式類型]。
5. 在文字方塊中，搜尋要指派給裝置的應用程式。 選擇應用程式，然後選取 [確定]。
6. 在 [新增應用程式] 刀鋒視窗中，選取 [應用程式資訊]，然後確定所有應用程式資訊都已填入。 您可以新增其他選用的詳細資料，以協助您組織此應用程式，例如 [擁有者]、[備忘稿]、[開發人員] 和貴公司隱私權原則的 [隱私權 URL]。
7. 確定您針對 [將此顯示為公司入口網站中的精選應用程式] 已選取 [是]，然後選取 [確定]。
8. 選取 [新增] 來新增應用程式。 這會帶您前往該應用程式的 [概觀]。 選擇 [指派]，然後按一下 [選取群組] 將它指派給您的測試群組。 讓應用程式成為 [可用] 下載。 應用程式應該會在測試裝置上顯示為 [精選應用程式]。
