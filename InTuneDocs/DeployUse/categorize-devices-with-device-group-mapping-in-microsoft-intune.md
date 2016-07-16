---
title: "使用裝置群組對應分類裝置 | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e
ms.reviewer: sumitp
ms.suite: ems
ms.sourcegitcommit: bb30b8e61a768b15e2f09993f4dceae8f4e1bd8a
ms.openlocfilehash: 55f811153bf37048a4fcdfc6da301a5f181700c3


---

# 在 Microsoft Intune 使用裝置群組對應分類裝置
使用 Microsoft Intune **裝置群組對應**將裝置分組成定義的類別，以便讓您更輕鬆地管理這些裝置。 

裝置群組對應會使用下列工作流程︰
1. 為想要使用的每個類別建立 Intune 裝置群組。
2. 您會設定裝置群組對應規則，對應您為建立的裝置群組所選擇的類別。
3. 當使用者註冊其裝置時，他們必須從您設定的類別中選擇一個類別。 選擇之後，他們的裝置會自動加入至您建立的對應裝置群組。
4. 您接著可在部署原則和應用程式時使用這些裝置群組。

以下是可能的類別範例︰
* 個人
* 銷售點裝置
* 示範裝置
* 銷售額
* 帳戶處理
* Manager

不過，您可以設定任何想要的類別。

## 如何設定裝置群組對應
1. 對於想要使用的每個裝置類別，建立一個 Intune 裝置群組。 如需如何建立群組的資訊，請參閱[在 Microsoft Intune 中使用群組來管理使用者和裝置](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)。
2. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 **[系統管理]**。
3. 在 [系統管理] 工作區中，展開 [行動裝置管理]，然後選擇 [裝置群組對應]。
4. 在 [裝置群組對應] 頁面上，啟用裝置群組對應。
5. 選擇 [新增] 建立新的對應規則。
6. 在 [新增裝置群組對應規則] 對話方塊中，輸入您想要建立的類別名稱，然後從下拉式清單中，選擇要將此類別對應到的裝置集合。 完成時，選擇 [新增]。
7. 完成新增類別和群組時，選擇 [儲存]。

現在當使用者註冊其裝置時，他們會看到您設定的類別清單。 選擇類別並完成註冊後，他們的裝置會加入到與其所選類別相對應的裝置群組。

### 請參閱
[利用 Microsoft Intune，使用群組管理使用者和裝置](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)


<!--HONumber=Jun16_HO3-->


