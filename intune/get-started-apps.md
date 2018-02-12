---
title: "開始使用應用程式"
titlesuffix: Azure portal
description: "找到應用程式，並將其新增至裝置，讓您的員工可以完成工作。"
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c1838f1d856efdebb7e2114cb61dd8d88ca100f7
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="get-started-with-adding-apps"></a>開始新增應用程式

Intune 支援一些不同的方式，讓您將應用程式部署到您公司的裝置：

* **軟體安裝程式**：您上傳的檔案會下載到使用者的裝置
* __外部連結__：適用於當您有應用程式在公用應用程式存放區或 webapp
* **受管理應用程式**：適用於 iOS 裝置，您必須套用其他行動應用程式管理到在 App Store 裡提供的應用程式

您即將藉由指派公用市集應用程式，體驗其中一種更快速的應用程式部署方法。

## <a name="how-do-i-assign-a-public-store-app"></a>如何指派公用市集應用程式？

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 使用 [搜尋資源]，搜尋 **Intune**。
3. 選取 [行動應用程式]，然後選取 [應用程式]。
4. 選取 [新增]，然後選取 [市集應用程式] 下的 [iOS] 作為 [應用程式類型]。
5. 選擇 [選取應用程式] 顯示 [Search the App Store] \(搜尋應用程式市集) 刀鋒視窗。
6. 在文字方塊中，搜尋要指派給裝置的應用程式。 選擇應用程式，然後按一下 [選取]。
7. 在 [新增應用程式] 刀鋒視窗中，選取 [應用程式資訊]，然後確定所有應用程式資訊都已填入。 您可以新增其他選用的詳細資料，以協助您組織此應用程式，例如 [擁有者]、[備忘稿]、[開發人員] 和貴公司隱私權原則的 [隱私權 URL]。
8. 確定您針對 [Display this as a featured app in the Company Portal] \(將此顯示為公司入口網站中的精選應用程式) 已選取 [是]，然後選取 [確定]。
9. 從 [新增應用程式] 刀鋒視窗選取 [新增]，以新增應用程式。 這會帶您前往該應用程式的 [概觀]。 選擇 [指派]，然後按一下 [選取群組] 將它指派給您的測試群組。 讓應用程式成為 [可用] 下載。 應用程式應該會在測試裝置上顯示為 [精選應用程式]。

## <a name="learn-more"></a>進一步了解

* [什麼是使用 Intune 進行應用程式管理？](app-management.md)
* [應用程式生命週期的概觀](app-lifecycle.md)
* [什麼是應用程式保護原則？](app-protection-policy.md)
