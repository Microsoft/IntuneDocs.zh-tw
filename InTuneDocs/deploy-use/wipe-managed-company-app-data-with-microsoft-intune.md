---
title: "抹除受管理的公司應用程式資料 | Microsoft Intune"
description: "深入了解如何以遠端方式，選擇性地從裝置移除公司資料。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2742e1d5-d2d5-42cd-b719-665dd6e0a0e9
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: d32a66ee283906586e25173e736c02ee8bf23042


---

# <a name="wipe-managed-company-app-data-with-microsoft-intune"></a>使用 Microsoft Intune 抹除受管理的公司應用程式資料
當裝置遺失或遭竊，或者如果員工離職，您會想要確定公司應用程式資料已從裝置移除。 不過，您可能不想要移除裝置上的個人資料，特別是當該裝置為員工擁有的裝置時。

若要選擇性地移除公司應用程式資料，請使用本主題中的步驟建立抹除要求。 完成抹除要求之後，當裝置下一次執行應用程式時，即會從應用程式中移除公司資料。
>[!NOTE]
> 移除直接從應用程式同步到原生通訊錄的連絡人。 無法清除從原生通訊錄同步處理到其他外部來源的任何連絡人。 目前這僅適用於 Microsoft Outlook 應用程式。



## <a name="create-a-wipe-request"></a>建立抹除要求

1.  在 [Intune 行動應用程式管理] 刀鋒視窗中，選擇 [抹除要求] 磚。

    ![內含 [摘要] 磚的 Intune 行動應用程式管理刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_WipeRequests.png)

2.  選擇 [新的抹除要求]。 這會開啟 [新增抹除要求] 刀鋒視窗。

    ![[新增抹除要求] 刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_NewWipeRequest.png)

3.  選擇 [使用者] 開啟 [使用者] 刀鋒視窗，然後選取您要抹除其應用程式資料的使用者。

4.  選擇 [裝置]。  隨即開啟 [裝置]  刀鋒視窗，其中列出與所選使用者相關聯的所有裝置。  選取您要抹除的裝置。

5.  現在您已回到 [新增抹除要求] 刀鋒視窗。 選擇 [確定] 以提出抹除要求。 針對裝置上的每個受保護應用程式，服務會建立並追蹤個別抹除要求。


![[抹除要求] 磚的螢幕擷取畫面 ](../media/AppManagement/AzurePortal_MAM_WipeRequestsSummary.png)

## <a name="monitor-your-wipe-requests"></a>監視抹除要求
在 [Intune 行動應用程式管理]  刀鋒視窗中的 [抹除要求]  磚上有提供摘要報告。  它會顯示整體狀態，並包括擱置的要求以及失敗的數目。 您可以遵循這些步驟取得更多詳細資料︰

1.  在 [Intune 行動應用程式管理] 刀鋒視窗中，選擇 [抹除要求] 磚，以開啟 [抹除要求] 刀鋒視窗。

2.  在 [抹除要求] 刀鋒視窗中，您可以看到您的要求清單 (依據使用者群組)。 由於系統會針對裝置上執行的每個受保護應用程式建立抹除要求，因此您可能會看到一名使用者具有多個要求的情況。 狀態指出抹除要求為**擱置**、**失敗**或**成功**。

使用者必須開啟應用程式，抹除才會發生，並可能在發出要求後花費 30 分鐘的時間。

處於擱置狀態的抹除將會顯示，直到您手動將其刪除為止。  若要手動刪除抹除要求，請以滑鼠右鍵按一下並選擇 [刪除]。

### <a name="see-also"></a>請參閱
[使用行動應用程式管理原則保護應用程式資料](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[使用 Azure 入口網站](azure-portal-for-microsoft-intune-mam-policies.md)



<!--HONumber=Dec16_HO2-->


