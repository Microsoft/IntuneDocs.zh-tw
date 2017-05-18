---
title: "抹除受管理的公司應用程式資料 | Microsoft Docs"
description: "深入了解如何以遠端方式，選擇性地從裝置移除公司資料。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2742e1d5-d2d5-42cd-b719-665dd6e0a0e9
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8a3e8634769b05e6639f7efb6394b7333d998f06
ms.openlocfilehash: 5d5cde748aa8fa464526d0dc2b2ef9ee460fff9d
ms.lasthandoff: 02/07/2017


---

# <a name="wipe-company-app-data-with-intune-mam"></a>使用 Intune MAM 抹除公司應用程式資料

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

當裝置遺失或遭竊，或者如果員工離職，您會想要確定公司應用程式資料已從裝置移除。 不過，您可能不想要移除裝置上的個人資料，特別是當該裝置為員工擁有的裝置時。

若要選擇性地移除公司應用程式資料，請使用本主題中的步驟建立抹除要求。 完成抹除要求之後，當裝置下一次執行應用程式時，即會從應用程式中移除公司資料。

>[!IMPORTANT]
> 移除直接從應用程式同步到原生通訊錄的連絡人。 無法清除從原生通訊錄同步處理到其他外部來源的任何連絡人。 目前只有 Microsoft Outlook 應用程式可使用此功能。

## <a name="create-a-wipe-request"></a>建立抹除要求

1.  登入 [Azure 入口網站](https://portal.azure.com)。

2.  選擇 [更多服務]，接著在 [篩選]文字方塊中輸入 **Intune**，然後選取 [Intune App Protection]\(Intune 應用程式保護)。 Intune [行動應用程式管理] 刀鋒視窗會隨即開啟。

    ![[新增抹除要求] 刀鋒視窗的螢幕擷取畫面](../media/AppManagement/wipe-request-mam-main-blade.png)

2.  在 [設定] 刀鋒視窗中選擇 [抹除要求]。

3.  選擇 [新增抹除要求]。 [新增抹除要求] 刀鋒視窗會隨即開啟。

    ![[新增抹除要求] 刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_NewWipeRequest.png)

4.  選擇 [使用者] 開啟 [使用者] 刀鋒視窗，然後選取您要抹除其應用程式資料的使用者。

5.  選擇 [裝置]。 這會開啟 [裝置] 刀鋒視窗，列出與所選使用者相關聯的所有裝置，並會提供兩個資料行，其中 [裝置名稱] 是使用者定義的易記名稱，而 [裝置類型] 則是其裝置平台。 選取您要抹除的裝置。

6.  現在您已回到 [新增抹除要求] 刀鋒視窗。 選擇 [確定] 以提出抹除要求。 

此服務會為裝置上每個受保護的應用程式建立個別的抹除要求，並加以追蹤，以及抹除要求相關聯的使用者。

>[!NOTE]
> 您也可以按一下 Intune [行動應用程式管理] 刀鋒視窗中的 [抹除要求] 磚來建立**抹除要求**。

## <a name="monitor-your-wipe-requests"></a>監視抹除要求

您可有摘要報表顯示抹除要求的整體狀態，以及暫止的要求數與失敗數。 若要取得更多詳細資訊，請遵循下列步驟︰

1.  在 Intune [行動應用程式管理] 刀鋒視窗中，按一下 [抹除要求] 磚。

2.  在 [抹除要求] 刀鋒視窗中，選擇 [抹除要求] 磚以開啟 [抹除要求] 刀鋒視窗。

3.  在 [抹除要求] 刀鋒視窗中，您可以看到您的要求清單 (依據使用者群組)。 由於系統會針對裝置上執行的每個受保護應用程式建立抹除要求，因此您可能會看到一名使用者具有多個要求的情況。 狀態指出抹除要求為**擱置**、**失敗**或**成功**。

    ![[新增抹除要求] 刀鋒視窗的螢幕擷取畫面](../media/AppManagement/wipe-request-status-1.png)

此外，您可以查看裝置名稱及其裝置類型，這對閱讀報表十分有幫助。

>[!IMPORTANT]
> 使用者必須開啟應用程式，抹除才會發生，並可能在發出要求後花費 30 分鐘的時間。

## <a name="delete-a-wipe-request"></a>刪除抹除要求

處於擱置狀態的抹除將會顯示，直到您手動將其刪除為止。  手動刪除抹除要求

1.  在 Intune [行動應用程式管理] 刀鋒視窗中，按一下 [抹除要求] 磚。

2.  在 [抹除要求] 刀鋒視窗中，選擇 [抹除要求] 磚以開啟 [抹除要求] 刀鋒視窗。

3.  在要刪除的抹除要求上按一下滑鼠右鍵，然後選擇 [刪除抹除要求]。

    ![[新增抹除要求] 刀鋒視窗的螢幕擷取畫面](../media/AppManagement/delete-wipe-request.png)

4.  當收到確認刪除的提示時，請選擇 [是] 或 [否]，然後按一下 [確定]。


### <a name="see-also"></a>請參閱
[使用行動應用程式管理原則保護應用程式資料](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[使用 Azure 入口網站](azure-portal-for-microsoft-intune-mam-policies.md)

