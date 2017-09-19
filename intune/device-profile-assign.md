---
title: "如何使用 Intune 指派裝置設定檔"
titlesuffix: Azure portal
description: "建立 Intune 裝置設定檔之後，可使用本主題來了解如何將其指派給裝置。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ba1438fe9227e0c7933fda7e9a2b60c8d4a5dca4
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-assign-microsoft-intune-device-profiles"></a>如何指派 Microsoft Intune 裝置設定檔

## <a name="assign-a-device-profile"></a>指派裝置設定檔

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置設定]。
1. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
2. 在設定檔刀鋒視窗清單中，選擇您想要管理的設定檔，然後在<*設定檔名稱*>  [報表] 刀鋒視窗中，選擇 [管理]  > [指派]。
3. 在下一個刀鋒視窗中，選擇 [包含] (包含群組) 或 [排除] (排除群組)，然後選擇 [選取群組]。
![在設定檔指派中包含和排除群組。](./media/group-include-exclude.png)
4. 在 [選取群組] 刀鋒視窗中，選擇要在指派中包含或排除的 Azure AD 群組。 您可按住 **CTRL** 鍵以選取多個群組。
4. 完成之後，請在 [選取群組] 刀鋒視窗中，選擇 [選取]。



## <a name="how-to-exclude-groups-from-a-device-profile-assignment"></a>如何從裝置設定檔指派排除群組

Intune 裝置組態設定檔可讓您從原則指派排除群組。 例如，您可能會將裝置設定檔指派給**所有公司使用者**群組，但排除**資深管理層**群組的任何成員。

當您從指派排除群組時，只排除使用者或只排除裝置群組，不是排除混合的群組。 Intune 在排除群組時，不會考慮任何使用者與裝置關聯。 包含使用者群組的同時排除裝置群組，不可能產生您所要的結果。 萬一使用了混合群組，或有其他衝突，包含的優先順序高於排除。

例如，您想要將裝置設定檔指派給組織中 Kiosk 裝置以外的所有裝置。 您包含**所有使用者**群組，但是排除**所有裝置**群組。

在此情況下，所有的使用者及其裝置都受原則約束，即使使用者的裝置屬於**所有裝置**群組。 

排除只會評估群組的直屬成員，不包含與使用者建立關聯的裝置。 不過，沒有使用者的裝置不受原則約束，因為它們和**所有使用者**群組沒有任何關聯。 

如果您包含**所有裝置**但排除**所有使用者**，則所有裝置都會收到原則。 本例的目的是要排除此原則中有相關聯使用者的裝置。 不過，它做不到，因為排除功能只會比對直屬群組成員。 

>[!Tip]
>合規性政策或應用程式指派目前不提供排除項目。 若要從指派排除成員，您可以使用「可用」及「不適用」的指派意圖。 例如，您將應用程式指派給具有**可用**意圖的**所有公司使用者**，又指派給具有**不適用**意圖的**資深管理層**。 此應用程式會指派給所有使用者，但**資深管理層**群組的使用者「除外」。 如果您將應用程式指派給具有**必要**意圖的**所有公司使用者**，不會排除**資深管理層**群組的使用者。
 
    
## <a name="next-steps"></a>後續步驟
請參閱[如何監視裝置設定檔](device-profile-monitor.md)以取得資訊，協助您監視裝置的設定檔指派。
