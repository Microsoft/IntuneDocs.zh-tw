---
title: "開始在 Microsoft Intune 中使用應用程式"
titlesuffix: 
description: "找到應用程式，並將其新增至裝置，讓您的員工可以完成工作。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 3/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0185eebbe436da73e1920d7cd834f0897a143894
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>開始在 Microsoft Intune 中新增應用程式

您必須先將應用程式新增至 Intune，才可以指派、監視、設定或保護它們。 Intune 支援數種不同的應用程式類型。 而且，每種應用程式類型的可用選項都不相同。

Intune 可讓您將下列應用程式類型新增和指派至公司裝置：
- **市集的應用程式** - 適用於裝置，您必須將其他行動應用程式管理套用至 App Store 中所提供的應用程式。
- **內部撰寫的應用程式 (企業營運)** - 您上傳的檔案會下載至使用者裝置。
- **內建應用程式** - 將 Office 365 應用程式這類受控應用程式指派給 iOS 和 Android 裝置。 
- **網站上的應用程式** - Intune 會在裝置主畫面上建立 Web 應用程式捷徑。

## <a name="how-do-i-assign-a-public-store-app"></a>如何指派公用市集應用程式？

下列範例會逐步引導您如何在 Microsoft Intune 中新增 iOS 應用程式。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [監視 + 管理] 區段。
3. 在 [Intune] 刀鋒視窗上，選擇 [行動應用程式]。
4. 在 [Mobile Apps] 工作負載中，選擇 [管理] 區段下的 [應用程式]。
5. 選擇 [應用程式] 窗格右側的 [新增]。
6. 在 [應用程式類型] 清單中，選取可用 [市集應用程式] 類型下的 [iOS]。
6. 選擇 [Search the App Store] (搜尋應用程式市集)。
7. 在 [Search the App Store] (搜尋應用程式市集) 刀鋒視窗中，先選取 App Store 國家地區設定。
8. 在 [搜尋] 方塊中鍵入名稱 (或部分名稱)。 Intune 會搜尋市集，並傳回一份相關的結果。
9. 請從清單中，選擇您想要的應用程式，然後按一下 [選取]。
10. 選取 [應用程式資訊] 來設定應用程式資訊。
11. (選用) 新增詳細資料，以協助您組織此應用程式，例如 [擁有者]、[備忘稿]、[開發人員] 和 [隱私權 URL] (指向公司隱私權原則)。
12. 已針對 [Display this as a featured app in the Company Portal] (將此顯示為公司入口網站中的精選應用程式) 選項選取 [是]。 
13. 新增所有必要應用程式資訊之後，請按一下 [確定]。
14. 按一下 [新增應用程式] 刀鋒視窗中的 [新增]這會帶您前往該應用程式的 [概觀]。 

## <a name="next-steps"></a>後續步驟

現在您已在 Intune 中新增應用程式，就可以指派可在其裝置上包含應用程式的員工群組。

- [如何將應用程式指派到群組](apps-deploy.md)
- 
## <a name="learn-more"></a>深入了解

* [什麼是使用 Intune 進行應用程式管理？](app-management.md)
* [應用程式生命週期的概觀](app-lifecycle.md)
* [什麼是應用程式保護原則？](app-protection-policy.md)
