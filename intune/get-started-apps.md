---
title: 開始在 Microsoft Intune 中使用應用程式
titlesuffix: ''
description: 找到應用程式，並將其新增至裝置，讓您的員工可以完成工作。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5d99812c57596e10d0cdfa2c0f4504f8a6ac583c
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>開始在 Microsoft Intune 中新增應用程式

您必須先將應用程式新增至 Intune，才可以指派、監視、設定或保護它們。 Intune 支援數種不同的應用程式類型。 而且，每種應用程式類型的可用選項都不相同。

Intune 可讓您將下列應用程式類型新增和指派至公司裝置：
- **市集的應用程式** - 適用於裝置，您必須將其他行動應用程式管理套用至 App Store 中所提供的應用程式。
- **內部撰寫的應用程式 (企業營運)** - 您上傳的檔案會下載至使用者裝置。
- **內建應用程式** - 將 Office 365 應用程式這類受控應用程式指派給 iOS 和 Android 裝置。
- **網站上的應用程式** - Intune 會在裝置主畫面上建立 Web 應用程式捷徑。

## <a name="how-do-i-assign-a-public-store-app"></a>如何指派公用市集應用程式？

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 選取 [行動應用程式]，然後選取 [應用程式]。
4. 選取 [新增]，然後選取 [iOS] 作為 [應用程式類型]。
5. 選擇 [選取應用程式] 顯示 [Search the App Store] (搜尋應用程式市集) 窗格。
6. 在文字方塊中，搜尋要指派給裝置的應用程式。 選擇應用程式，然後按一下 [選取]。
7. 在 [新增應用程式] 窗格中，選取 [應用程式資訊]，然後確定所有應用程式資訊都已填入。 您可以新增其他選用的詳細資料，以協助您組織此應用程式，例如 [擁有者]、[備忘稿]、[開發人員] 和貴公司隱私權原則的 [隱私權 URL]。
8. 確定您針對 [Display this as a featured app in the Company Portal] \(將此顯示為公司入口網站中的精選應用程式) 已選取 [是]，然後選取 [確定]。
9. 從 [新增應用程式] 窗格選取 [新增]，以新增應用程式。 這個動作會帶您前往該應用程式的 [概觀]。 選擇 [指派]，然後按一下 [新增群組] 將它指派給您的測試群組。 讓應用程式成為 [可用] 下載。 應用程式應該會在測試裝置上顯示為 [精選應用程式]。


- [如何將應用程式指派到群組](apps-deploy.md)

## <a name="learn-more"></a>深入了解

* [什麼是使用 Intune 進行應用程式管理？](app-management.md)
* [應用程式生命週期的概觀](app-lifecycle.md)
* [什麼是應用程式保護原則？](app-protection-policy.md)
