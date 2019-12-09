---
title: Microsoft Intune 的包含與排除應用程式指派
titleSuffix: ''
description: 了解如何使用 Microsoft Intune 來包含與排除應用程式指派。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40cbb62a620d6e174ab8acb76798ba53080b78cf
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563968"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Microsoft Intune 的包含與排除應用程式指派

在 Intune 中，您可以藉由指派要包含或排除的使用者群組，來決定誰可以存取應用程式。 在您將群組指派給應用程式之前，必須先設定應用程式的指派類型。 指派類型可使應用程式成為可用、必要，或解除安裝應用程式。 

若要設定應用程式的可用性，您可使用包含與排除群組指派的組合，指派包含與排除應用程式的使用者或裝置群組。 當您藉由包含大型群組提供應用程式，同時再透過排除較小的群組以縮減選取的使用者時，這項功能很有用。 較小的群組可能是測試群組或執行群組。 

最佳做法是特別針對您的使用者群組建立並指派應用程式，且針對裝置群組個別地指派。 如需群組的詳細資訊，請參閱[新增群組來組織使用者與裝置](~/fundamentals/groups-add.md)。  

包含或排除應用程式指派時，存在重要情節：

- 在下列相同群組類型案例中，排除的優先順序高於包含：
    - 指派應用程式時，包含使用者群組且排除使用者群組
    - 指派應用程式時，包含裝置群組且排除裝置群組

    例如，如果您將裝置群組指派給**所有公司使用者使用者**群組，但排除**資深管理人員**使用者群組中的成員，除了**資深管理人員**以外的**所有公司使用者**都會受到指派，因為這兩個群組都是使用者群組。
- Intune 不會評估使用者對裝置群組關聯性。 如果您將應用程式指派給混合群組，結果可能不是您想要或預期的。

    例如，如果您將裝置群組指派給**所有使用者**使用者群組，但排除**所有個人裝置**裝置群組。 在此混合群組應用程式指派中，**所有使用者**會取得應用程式。 排除不適用。

因此，不建議將應用程式指派給混合群組。

> [!NOTE]
> 設定應用程式的群組指派時，[不適用]  類型已被排除群組功能所取代。 
>
> Intune 在主控台中提供預先建立的 [所有使用者]  和 [所有裝置]  群組。 群組提供您便利的最佳化選項。 強烈建議您使用這些群組針對所有使用者和所有裝置，而不是您自行建立的任何「所有使用者」或「所有裝置」群組。  
>
> Android 企業支援包含和排除群組。 您可以利用內建的 [所有使用者]  和 [所有裝置]  群組來進行 Android 企業應用程式指派。 

## <a name="include-and-exclude-groups-when-assigning-apps"></a>在指派應用程式時排除和包含群組 
若要使用包含和排除指派將應用程式指派給群組：
1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [所有應用程式]  。 已新增應用程式清單隨即顯示。
3. 選取您要指派的應用程式。 儀表板會顯示應用程式的相關資訊。 
4. 在功能表的 [管理]  區段中，選取 [指派]  。 

    ![在指派應用程式時包含應用程式指派](./media/apps-inc-exl-assignments/apps-inc-exl-01.png)

5. 選取 [新增群組]  新增獲指派應用程式的使用者群組。 
6. 從 [新增群組]  窗格中，從可用的指派類型中選取 [指派類型]  。
7. 選取 [無論註冊與否均可使用]  為指派類型。

    ![Intune 應用程式指派 - 新增群組](./media/apps-inc-exl-assignments/apps-inc-exl-02.png)
8. 選取 [包含的群組]  來選取您想要提供此應用程式的使用者群組。

    > [!NOTE]
    > 當您新增群組時，如果有任何其他群組已經包含於特定的指派類型，則會預先選取該應用程式，且無法修改為其他包含指派類型。 已經使用的群組無法當作包含的群組。

9. 選取 [是]  向所有使用者提供此應用程式。

    ![Intune 應用程式指派 - 包含群組](./media/apps-inc-exl-assignments/apps-inc-exl-03.png)
10. 選取 [確定]  來設定要包含的群組。
11. 選取 [排除的群組]  來選取您不要提供此應用程式的使用者群組。 
12. 選取要排除的群組。 這麼做會提供此應用程式給那些群組。

    ![Intune 應用程式指派 - 排除群組](./media/apps-inc-exl-assignments/apps-inc-exl-04.png)
13. 選取 [選取]  來完成您的群組選取項目。
14. 在 [新增群組]  窗格中，選取 [確定]  。 應用程式 [指派]  清單隨即顯示。
15. 按一下 [儲存]  啟用應用程式的群組指派。

當您進行群組指派時，已經指派的群組無法進行修改。 如果您要選取的群組目前無法使用，請先將應用程式從應用程式的指派清單移除。 

若要編輯指派，請在應用程式 [指派]  清單中，選取包含您要變更之特定指派的列。 您也可以藉由選取位在列結尾的省略符號 ( **...** )，然後選取 [移除]  來移除指派。 若要變更 [指派]  清單的檢視，可依 [指派類型]  或 [包含/排除]  分組。

![Intune 應用程式指派 - 完成](./media/apps-inc-exl-assignments/apps-inc-exl-05.png)

## <a name="next-steps"></a>後續步驟

- 如需應用程式的包含和排除群組指派的詳細資訊，請參閱 [Microsoft Intune 部落格](https://aka.ms/new_app_assignment_process) \(英文\)。
- 了解如何[監視應用程式資訊和指派](apps-monitor.md)。
