---
title: "包含與排除應用程式指派"
titlesuffix: Microsoft Intune
description: "了解如何使用 Intune 來包含與排除應用程式指派。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ca1f45c3203645dc474fcb6411a8ad598ff83714
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Microsoft Intune 的包含與排除應用程式指派

使用 Intune，您可以指派包含以及排除的群組，決定誰可以存取應用程式。 使用包含與排除群組指派的組合，指派包含與排除應用程式的使用者或裝置群組。 選取應用程式之後，您可以選擇如何指派應用程式。 當您藉由包含大型群組提供應用程式，同時再透過排除較小的群組以縮減選取的使用者時，這項功能很有用。 較小的群組可能是測試群組或執行群組。 

當您從指派排除群組時，必須只排除使用者群組或只排除裝置群組，不能排除混合的群組。 Intune 在排除群組時，不考慮使用者與裝置的關聯性。 包含使用者群組的同時排除裝置群組，不可能產生您所要的結果，因為包含優先於排除。 例如，如果您的目標是讓**所有使用者**取得 iOS 應用程式，但要排除**所有 iPad**，最終結果會是任何使用 iPad 的使用者仍會收到應用程式。 但若您的目標是讓**所有裝置** 取得 iOS 應用程式，但要排除**所有 iPad**，部署就會成功。  

>[!NOTE]
>設定應用程式的群組指派時，**不適用**類型已被排除群組功能所取代。 
>
>Intune 會在主控台中提供預先建立的**所有使用者**和**所有裝置**群組，附有內建的最佳化方便您使用。 強烈建議您使用這些群組針對所有使用者和所有裝置，而不是您自行建立的任何「所有使用者」或「所有裝置」群組。  

## <a name="including-and-excluding-groups-when-assigning-apps"></a>指派應用程式時包含與排除群組 
使用包含與排除指派將應用程式指派給群組：
1. 在 [Microsoft Intune] 刀鋒視窗上選取 [Mobile Apps]。
2. 在 [Mobile Apps] 刀鋒視窗上選取 [應用程式]。 已新增應用程式清單隨即出現。
3. 選取您要指派的應用程式。 隨即顯示與應用程式相關的儀表板。 
4. 選取 [管理] 區段下的 [指派]。 

    ![Intune 應用程式指派](./media/apps-inc-exl-01.png)
5. 選取 [新增群組] 新增獲指派應用程式的使用者群組。 
6. 從 [新增群組] 刀鋒視窗的可用指派類型中選取一項**指派類型**。
7. 選取 [Available with or without enrollment] (可用，無論是否註冊) 為指派類型。

    ![Intune 應用程式指派 - 新增群組](./media/apps-inc-exl-02.png)
8. 選取 [Included Groups] (包含的群組) 選取您想要提供此應用程式的使用者群組。

    >[!NOTE]
    >新增群組時，如已包含任何其他群組用於指定的指派類型，就會預先選取且無法針對其他包含指派類型進行變更。 因此，已使用的該群組，不能用為包含的群組。

9. 選取 [是] 向所有使用者提供此應用程式。

    ![Intune 應用程式指派 - 包含群組](./media/apps-inc-exl-03.png)
10. 按一下 [確定] 設定要包含的群組。
11. 選取 [Excluded Groups] (排除的群組) 選取您不想提供此應用程式的使用者群組。 
12. 選取要排除的群組，不提供此應用程式。

    ![Intune 應用程式指派 - 排除群組](./media/apps-inc-exl-04.png)
13. 按一下 [選取] 完成選取群組。
14. 按一下 [新增群組] 刀鋒視窗的 [確定]。 應用程式 [指派] 清單隨即顯示。
15. 按一下 [儲存] 啟用應用程式的群組指派。

指派群組時，會停用已指派或選取的群組。 如果想要選取目前停用的群組，請將它移除應用程式的指派清單。 您可以選取包含想要變更之特定指派的資料列，在應用程式 [指派] 清單中編輯指派。 此外，您可以按一下資料列結尾的省略符號 (…)，選取 [移除] 來移除指派。 您也可以選擇依**指派類型**或依**包含/排除**分組，變更 [指派] 清單的檢視。

![Intune 應用程式指派 - 完成](./media/apps-inc-exl-05.png)

## <a name="next-steps"></a>接下來的步驟

* 如需應用程式的包含與排除群組指派的詳細資訊，請參閱 [Microsoft Intune 部落格](https://aka.ms/new_app_assignment_process)。
