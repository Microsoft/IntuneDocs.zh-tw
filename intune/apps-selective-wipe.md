---
title: 如何只抹除應用程式中的公司資料
titleSuffix: Microsoft Intune
description: 了解如何使用 Microsoft Intune 選擇性抹除應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a063d43ff242a00ff89fd16cc05fd0eaa1af3484
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>如何只抹除 Intune 管理之應用程式中的公司資料

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

當裝置遺失或遭竊，或者如果員工離職，您會想要確定公司應用程式資料已從裝置移除。 不過，您可能不想要移除裝置上的個人資料，特別是當該裝置為員工擁有的裝置時。

>[!NOTE]
> iOS 和 Android 平台是目前支援的兩個平台，可從 Intune 管理的應用程式抹除公司資料。

若要選擇性地移除公司應用程式資料，請使用本主題中的步驟建立抹除要求。 完成抹除要求之後，當裝置下一次執行應用程式時，即會從應用程式中移除公司資料。

>[!IMPORTANT]
> 移除直接從應用程式同步到原生通訊錄的連絡人。 無法清除從原生通訊錄同步處理到其他外部來源的任何連絡人。 目前只有 Microsoft Outlook 應用程式可使用此功能。

## <a name="create-a-wipe-request"></a>建立抹除要求

1.  登入 [Azure 入口網站](https://portal.azure.com)。

2.  選擇 [所有服務]，接著在 [篩選] 文字方塊中鍵入 **Intune**，然後選取 [Intune]。 當 [Intune] 窗格開啟時，選擇 [行動應用程式] 窗格。

    ![Microsoft Intune 窗格的螢幕擷取畫面](./media/apps-selective-wipe01.png)

3.  在 [行動應用程式] 窗格中選擇 [應用程式選擇性抹除]。

4.  選擇 [新增抹除要求]。 [新增抹除要求] 窗格會隨即開啟。

    ![[新增抹除要求] 窗格的螢幕擷取畫面](./media/AzurePortal_MAM_NewWipeRequest.png)

5.  選擇使用者，然後選擇 [選取] 來選取您要抹除其應用程式資料的使用者。

6.  接下來，從 [新增抹除要求] 窗格中選擇 [裝置]。 這會開啟 [選取裝置] 窗格，列出與所選使用者建立關聯的所有裝置，並會提供兩個資料行，其中 [裝置名稱] 是使用者定義的易記名稱，而 [裝置類型] 則是其裝置平台。 選取您要抹除的裝置。

7.  現在您已回到 [新增抹除要求] 窗格。 選擇 [確定] 以提出抹除要求。

此服務會為裝置上每個受保護的應用程式建立個別的抹除要求，並加以追蹤，以及抹除要求相關聯的使用者。

## <a name="monitor-your-wipe-requests"></a>監視抹除要求

您可有摘要報表顯示抹除要求的整體狀態，以及暫止的要求數與失敗數。 若要取得更多詳細資訊，請遵循下列步驟︰

1.  [行動應用程式 - 應用程式選擇性抹除] 窗格中會依使用者分組列出您的要求清單。 由於系統會針對裝置上執行的每個受保護應用程式建立抹除要求，因此您可能會看到一名使用者具有多個要求的情況。 狀態指出抹除要求為**擱置**、**失敗**或**成功**。

    ![[應用程式選擇性抹除] 窗格中抹除要求狀態的螢幕擷取畫面](./media/wipe-request-status-1.png)

此外，您可以查看裝置名稱及其裝置類型，這對閱讀報表十分有幫助。

>[!IMPORTANT]
> 使用者必須開啟應用程式，抹除才會發生，並可能在發出要求後花費 30 分鐘的時間。

## <a name="delete-a-wipe-request"></a>刪除抹除要求

處於擱置狀態的抹除將會顯示，直到您手動將其刪除為止。 若要手動刪除抹除要求：

1.  在 [行動應用程式 - 應用程式選擇性抹除] 窗格中。

2.  在清單中，以滑鼠右鍵按一下要刪除的抹除要求，然後選擇 [刪除抹除要求]。

    ![[應用程式選擇性抹除] 窗格中抹除要求清單的螢幕擷取畫面](./media/delete-wipe-request.png)

3.  當收到確認刪除的提示時，請選擇 [是] 或 [否]，然後按一下 [確定]。

### <a name="see-also"></a>另請參閱
[什麼是應用程式保護原則](app-protection-policy.md)

[什麼是應用程式管理](app-management.md)
