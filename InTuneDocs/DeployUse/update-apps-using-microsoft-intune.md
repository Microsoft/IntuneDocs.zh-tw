---
title: "更新應用程式 | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b
ms.reviewer: mghadial
ms.suite: ems
ms.sourcegitcommit: 0581d1476fba5bedcdd4446df20f8f92b151f41b
ms.openlocfilehash: 9e5b8f4a467e8e58cc2f8fa495b5f008eee7e35b


---

# 使用 Microsoft Intune 更新應用程式
Microsoft Intune 可協助您管理應用程式更新。 使用本主題中的資訊可了解如何更新需要新版本的應用程式。

## 如何更新應用程式
發行您所部署之應用程式的新版本時，Intune 可讓您更新和部署應用程式的較新版本。 您只能將部署取代為相同應用程式的較新版本 (使用相同的識別項)。 您無法使用應用程式更新來更新不同的應用程式套件的部署。

> [!IMPORTANT]
> 當您使用 [需要的安裝]  部署動作來部署應用程式，但稍後又將部署動作變更為 [可用安裝] ，則應用程式的更新不會自動安裝在變更部署前安裝應用程式的裝置上。 若要修正此問題，您可以執行下列作業：
> 
> -   請裝置的使用者前往公司入口網站，選取已安裝的應用程式，並請他們選擇 [安裝]。
> -   變更部署動作以 [解除安裝] ，並在解除安裝應用程式之後，用 [可用安裝] 部署動作重新部署應用程式。

### 更新應用程式

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [應用程式] &gt; [應用程式]。

2.  從 [應用程式] 清單中，選取您要更新的應用程式，然後選擇 [編輯]。

3.  在 [編輯軟體]  精靈中，提供應用程式套件的新詳細資料。

4.  完成之後，選擇 [更新]。

當裝置下次檢查有無可用應用程式時，會自動將應用程式更新為最新版本。
針對從應用程式套件安裝的應用程式 (企業營運應用程式)，應用程式將會自動升級以進行必要和可用的部署，只要應用程式有相同的識別碼即可。
針對部署為存放區連結的應用程式，更新是由應用程式所源自的存放區進行管理。






<!--HONumber=Jun16_HO3-->


