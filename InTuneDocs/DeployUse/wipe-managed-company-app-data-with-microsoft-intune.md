---
title: "抹除受管理的公司應用程式資料 | Microsoft Intune"
description: "深入了解如何以遠端方式，選擇性地從裝置移除公司資料。"
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2742e1d5-d2d5-42cd-b719-665dd6e0a0e9
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: be1ebcdf2514e45d383dd49890e0e21acf6ede44
ms.openlocfilehash: 3d52345b043115185e667c41d3f09d8257792002


---

# 使用 Microsoft Intune 抹除受管理的公司應用程式資料
當裝置遺失或遭竊，或者如果員工離職，您會想要確定公司應用程式資料已從裝置移除。 不過，您可能不想要移除裝置上的個人資料，特別是當該裝置為員工擁有的裝置時。

若要選擇性地移除公司應用程式資料，請使用本主題中**建立抹除要求**一節所述的步驟來建立抹除要求。  完成抹除要求之後，當裝置下一次執行應用程式時，即會從應用程式中移除公司資料。
>[!NOTE]
> 移除直接從應用程式同步到原生通訊錄的連絡人。 無法清除從原生通訊錄同步處理到其他外部來源的任何連絡人。 目前這僅適用於 Microsoft Outlook 應用程式。



## 建立抹除要求

1.  在 [Intune 行動應用程式管理] 刀鋒視窗中，選擇 [抹除要求] 磚。

    ![內含 [摘要] 磚的 Intune 行動應用程式管理刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_WipeRequests.png)

2.  選擇 [新的抹除要求]。

    ![[新增抹除要求] 刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_NewWipeRequest.png)

3.  在 [新增抹除要求] 刀鋒視窗中，選擇 [使用者] 以開啟 [使用者] 刀鋒視窗，然後選取您要抹除其應用程式資料的使用者。

4.  選擇 [裝置]。  隨即開啟 [裝置]  刀鋒視窗，其中列出與所選使用者相關聯的所有裝置。  選取您要抹除的裝置。

5.  現在您已回到 [新增抹除要求] 刀鋒視窗。 選擇 [確定] 以提出抹除要求。 針對裝置上的每個受保護應用程式，服務會建立並追蹤個別抹除要求。


![[抹除要求] 磚的螢幕擷取畫面 ](../media/AppManagement/AzurePortal_MAM_WipeRequestsSummary.png)

## 監視抹除要求
在 [Intune 行動應用程式管理]  刀鋒視窗中的 [抹除要求]  磚上有提供摘要報告。  它會顯示整體狀態，並包括擱置的要求以及失敗的數目。 您可以藉由遵循下方所述步驟來取得更多詳細資料︰

1.  在 [Intune 行動應用程式管理] 刀鋒視窗中，選擇 [抹除要求] 磚，以開啟 [抹除要求] 刀鋒視窗。

2.  在 [抹除要求]  刀鋒視窗中，您可以看到您的要求清單 (依據使用者群組)。  由於系統會針對裝置上執行的每個受保護應用程式建立抹除要求，因此您可能會看到一名使用者具有多個要求的情況。  狀態指出抹除要求是否仍然 **擱置**、 **失敗**或 **成功**。

### 請參閱
[使用行動應用程式管理原則保護應用程式資料 ](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[使用 Azure 入口網站](azure-portal-for-microsoft-intune-mam-policies.md)



<!--HONumber=Jul16_HO5-->


