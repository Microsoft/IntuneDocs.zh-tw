---
title: Microsoft Intune 的包含與排除應用程式指派
titlesuffix: ''
description: 了解如何使用 Microsoft Intune 來包含與排除應用程式指派。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1ec9a45ca09ddff5aa10cc7283444cf96c8153f6
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905405"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Microsoft Intune 的包含與排除應用程式指派

在 Intune 中，您可以藉由指派要包含或排除的使用者群組，來決定誰可以存取應用程式。 在您將群組指派給應用程式之前，必須先設定應用程式的指派類型。 指派類型可使應用程式成為可用、必要，或解除安裝應用程式。 

若要設定應用程式的可用性，您可使用包含與排除群組指派的組合，指派包含與排除應用程式的使用者或裝置群組。 當您藉由包含大型群組提供應用程式，同時再透過排除較小的群組以縮減選取的使用者時，這項功能很有用。 較小的群組可能是測試群組或執行群組。 

當您從應用程式指派排除群組時，必須只排除使用者群組或只排除裝置群組。 您無法排除使用者群組和裝置群組的混合。 

Intune 在排除群組時，不考慮使用者對裝置的關聯。 包含使用者群組的同時排除裝置群組，不可能產生您所要的結果。 包含會優先於排除。 例如，如果您將 iOS 應用程式的目標設定為**所有使用者**，然後排除**所有 iPad**，則最後的結果是任何使用 iPad 的使用者仍會取得該應用程式。 但若您的目標是讓**所有裝置**取得 iOS 應用程式，但要排除**所有 iPad**，部署就會成功。  

> [!NOTE]
> 設定應用程式的群組指派時，[不適用] 類型已被排除群組功能所取代。 
>
> Intune 在主控台中提供預先建立的 [所有使用者] 和 [所有裝置] 群組。 群組提供您便利的最佳化選項。 強烈建議您使用這些群組針對所有使用者和所有裝置，而不是您自行建立的任何「所有使用者」或「所有裝置」群組。  
>
> Android 企業支援包含和排除群組。 您可以利用內建的 [所有使用者] 和 [所有裝置] 群組來進行 Android 企業應用程式指派。 


## <a name="include-and-exclude-groups-when-assigning-apps"></a>在指派應用程式時排除和包含群組 
若要使用包含和排除指派將應用程式指派給群組：
1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務] > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 功能表中，選取 [行動應用程式]。
4. 在 [行動應用程式] 窗格中，選取 [應用程式]。 已新增應用程式清單隨即顯示。
5. 選取您要指派的應用程式。 儀表板會顯示應用程式的相關資訊。 
6. 在功能表的 [管理] 區段中，選取 [指派]。 

    ![Intune 應用程式指派](./media/apps-inc-exl-01.png)
7. 選取 [新增群組] 新增獲指派應用程式的使用者群組。 
8. 從 [新增群組] 窗格中，從可用的指派類型中選取 [指派類型]。
9. 選取 [無論註冊與否均可使用] 為指派類型。

    ![Intune 應用程式指派 - 新增群組](./media/apps-inc-exl-02.png)
10. 選取 [包含的群組] 來選取您想要提供此應用程式的使用者群組。

    > [!NOTE]
    > 當您新增群組時，如果有任何其他群組已經包含於特定的指派類型，則會預先選取該應用程式，且無法修改為其他包含指派類型。 已經使用的群組無法當作包含的群組。

11. 選取 [是] 向所有使用者提供此應用程式。

    ![Intune 應用程式指派 - 包含群組](./media/apps-inc-exl-03.png)
12. 選取 [確定] 來設定要包含的群組。
13. 選取 [排除的群組] 來選取您不要提供此應用程式的使用者群組。 
14. 選取要排除的群組。 這麼做會提供此應用程式給那些群組。

    ![Intune 應用程式指派 - 排除群組](./media/apps-inc-exl-04.png)
15. 選取 [選取] 來完成您的群組選取項目。
16. 在 [新增群組] 窗格中，選取 [確定]。 應用程式 [指派] 清單隨即顯示。
17. 按一下 [儲存] 啟用應用程式的群組指派。

當您進行群組指派時，已經指派的群組無法進行修改。 如果您要選取的群組目前無法使用，請先將應用程式從應用程式的指派清單移除。 

若要編輯指派，請在應用程式 [指派] 清單中，選取包含您要變更之特定指派的列。 您也可以藉由選取位在列結尾的省略符號 (**...**)，然後選取 [移除] 來移除指派。 若要變更 [指派] 清單的檢視，可依 [指派類型] 或 [包含/排除] 分組。

![Intune 應用程式指派 - 完成](./media/apps-inc-exl-05.png)

## <a name="next-steps"></a>接下來的步驟

- 如需應用程式的包含和排除群組指派的詳細資訊，請參閱 [Microsoft Intune 部落格](https://aka.ms/new_app_assignment_process) \(英文\)。
- 了解如何[監視應用程式資訊和指派](apps-monitor.md)。
