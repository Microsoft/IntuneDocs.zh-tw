---
title: "如何將應用程式指派到群組 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰將應用程式新增至 Intune 之後，要將它指派到使用者或裝置的群組中。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 638ad0d87c19c9e40e96b42d18e5c4342f40a156
ms.lasthandoff: 02/16/2017

---

# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>如何使用 Microsoft Intune 將應用程式指派給群組

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

將應用程式新增至 Intune 之後，要將它置入使用者及裝置中。 進行指派即可完成此作業。

不論應用程式是否由 Intune 管理，皆可指派到裝置。 使用下表有助於您了解將應用程式指派到使用者及裝置的各種選項︰

||||
|-|-|-|-|
|&nbsp;|註冊有 Intune 的裝置|未註冊有 Intune 的裝置|
|指派給使用者|是|是|
|指派給裝置|是|否|
|指派經包裝之應用程式或應用程式，與 Intune SDK (適用於應用程式保護原則) 合併運作|是|是|
|將應用程式指派為可用|是|是|
|將應用程式指派為必要項目|是|否|
|解除安裝應用程式|是|是|
|使用者從公司入口網站應用程式安裝可用的應用程式|是|否|
|使用者從 Web 架構入口網站安裝可用的應用程式|是|是|

> [!NOTE]
> 您目前可指派 iOS 與 Android 應用程式 (企業營運與市集購買兩者) 未註冊有 Intune 的裝置。

## <a name="how-to-assign-an-app"></a>如何指派應用程式

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 **Intune** 刀鋒視窗上選擇 [管理應用程式]。
1. 在 [管理應用程式] 工作負載中，選擇 [管理]  >  [應用程式]。
2. 在應用程式刀鋒視窗清單中，按一下想要指派的應用程式。
3. 在 <*應用程式名稱*> - [概觀] 刀鋒視窗中，選擇 [管理]  >  [指派]。
4. 選擇 [選取群組]然後，在 [選取群組] 刀鋒視窗中，選擇要指派該應用程式的 Azure AD 群組。
5. 為每個您選擇的應用程式，從以下項目選擇應用程式的 [指派類型]︰
    - **可用** - 使用者從公司入口網站應用程式或網站，安裝應用程式。
    - **不適用** - 公司入口網站中未安裝或未顯示此應用程式。
    - **必要** - 此應用程式安裝所選群組中的裝置上。
    - **解除安裝** - 此應用程式會從所選群組中的裝置上解除安裝。
    - **是否有註冊皆可用** - 將此應用程式指派到其裝置未註冊有 Intune 的使用者群組。 請參閱上表中的說明。
6. 完成之後，請選擇 [儲存]。

應用程式現已指到您所選的群組。

請參閱[如何監視應用程式](monitor-apps.md)，以取得協助您監視應用程式指派的資訊。

