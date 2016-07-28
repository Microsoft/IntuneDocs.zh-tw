---
title: "使用 Microsoft Intune 監視 MAM 原則 | Microsoft Intune"
description: "查看有多少使用者擁有原則，向下鑽研以了解更多詳細資料。"
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 07/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c72c8e1a764af73ba4d421ca6637ee91ab7bca0a
ms.openlocfilehash: 1efbecc33e33e5e4864bcc2417ebed1e8a5b5826


---

# 使用 Microsoft Intune 監視行動應用程式管理原則
在您設定 MAM 原則並將原則套用到使用者之後，您可以在 [Azure 入口網站](https://portal.azure.com)上監視相容性狀態。 Azure 入口網站包含原則所影響之使用者相關資訊、符合性狀態，以及您的使用者可能發生的任何問題。
## 摘要檢視
在 [Intune 行動應用程式管理] 刀鋒視窗中，您可以看到如下所述的相容性狀態的摘要︰


![Intune 行動應用程式管理刀鋒視窗上的摘要磚](../media/mam-azure-portal-user-status-summary.png)

-   **使用者︰**公司中使用與原則相關聯應用程式的使用者總數。

-   **由原則管理︰**工作環境中已使用至少其中一個應用程式的使用者數目。

-   **沒有任何原則︰**使用與原則相關聯應用程式，但不是原則之目標的使用者數目。  您可以考慮將這些使用者加入至您的原則。

- **標有旗標的使用者︰**遇到問題的使用者數目。 目前只有使用已進行 JB 破解之裝置的使用者，會被報告為**標有旗標的使用者**。


## 詳細檢視
在 [使用者狀態] 磚和 [標有旗標的使用者] 磚上按一下，即可進入摘要的詳細檢視。

### 使用者狀態
您可以搜尋單一使用者，並查看該使用者的符合性狀態。 [應用程式報告] 刀鋒視窗會顯示所選使用者的下列資訊︰
- 與使用者帳戶相關聯的裝置
- 裝置上 MAM 原則的應用程式
- 狀態：

  **已簽入︰**這表示原則已部署至使用者，而且在在工作環境中至少使用一次應用程式。

  **未簽入：**這表示原則已部署至使用者，但是從那時起並未在工作環境中使用應用程式。

>[!NOTE]
> 如果您搜尋的使用者沒有部署 MAM 原則，您會看見一則訊息，通知您該使用者不針對任何應用程式原則。

若要查看使用者的報告，請遵循下列步驟︰

**步驟 1：**若要選取使用者，請按一下 [摘要] 磚，或在 [設定] 刀鋒視窗中選擇 [使用者應用程式報告] 選項，如下所示︰

![設定刀鋒視窗上的應用程式報告選項](../media/mam-azure-portal-app-reporting-by-user-settings-blade.png)

**步驟 2：**這會開啟 [應用程式報告] 刀鋒視窗。 選擇 [選取使用者] 來搜尋 Azure Active Directory 使用者。

![在 [應用程式報告] 刀鋒視窗上選取使用者選項](../media/mam-azure-portal-app-reporting-select-user.png)

**步驟 3：**從清單中選取使用者之後，您會看到該使用者符合性狀態的詳細資料。

![應用程式報告詳細資料](../media/mam-azure-portal-app-reporting-by-user.png)
### 標有旗標的使用者
詳細的檢視會顯示錯誤訊息、在錯誤發生時存取的應用程式、裝置的平台和時間戳記。  

### 請參閱
[管理 iOS 應用程式之間的資料傳輸](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

[啟用 MAM 應用程式的使用者經驗](end-user-experience-for-mam-enabled-apps-with-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->


