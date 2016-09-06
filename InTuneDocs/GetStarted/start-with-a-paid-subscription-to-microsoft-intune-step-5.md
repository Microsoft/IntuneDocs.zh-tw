---
title: "建立群組來組織使用者和裝置 | Microsoft Intune"
description: "說明如何為您的 Intune 訂閱建立使用者和群組"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5fdf98c8-fe67-4d7a-9837-ed1234348014
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6d1c7c670341692d4ea0c823e4a9a96746b83067
ms.openlocfilehash: 07a2de6922f6b3f3a2b56dfc6bbe4e5f09c7d976


---


# 建立群組來組織使用者和裝置
Intune 中的群組讓您在管理裝置和使用者時有絕佳的彈性。 您可以設定群組，使其符合組織的需求 (例如依據地理位置、部門或硬體特性設定)，並且使用它們來執行各種管理工作，從部署一組使用者的原則至部署一組裝置的應用程式皆可。

裝置和使用者群組都是在 Intune 系統管理主控台的 [群組] 工作區中建立。

![系統管理主控台群組工作區](./media/groups.png)


> [!TIP]
> 若要深入了解如何使用群組，請參閱[利用 Microsoft Intune，使用群組管理使用者和裝置](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune)。


## 建立裝置群組
使用裝置群組來部署 App 和更新，並設定其他功能。 例如，使用下列步驟設定「我的裝置」群組：

1.  在 [Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [群組]  >  [概觀]  >  [建立群組]。

2.  在 [群組名稱] 中輸入「我的裝置」，從父群組清單選取 [所有裝置]，然後選擇 [下一步]。

3.  在 [定義成員資格準則]  頁面上，選取 [所有裝置]  ，以指出群組同時包含行動裝置和電腦。

4.  在 [定義直接成員資格] 頁面上，選擇 [下一步] 。 若您先前建立的群組不含所有的裝置，並想要新增特定裝置到新群組，可以在此步驟中執行。

5.  在 [摘要] 頁面上，檢閱將要採取的動作，然後選擇 [完成]。

您可以在 [群組] 工作區之 [所有裝置] 下的 [群組] 清單中，找到新建立的群組。 您也可以從這裡編輯或刪除該群組。

## 建立使用者群組
以使用者群組來部署軟體和裝置原則。 例如，使用下列步驟設定「Intune 使用者」群組：

1.  在 [Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [群組]  >  [概觀]  >  [建立群組]。

2.  在 [群組名稱] 中輸入「Intune 使用者」，從父群組清單選取 [所有使用者]，然後選擇 [下一步]。

3.  在 [定義成員資格準則]  頁面上，將 [群組成員資格啟動方式]  設定為 [父群組中的所有使用者] 。

4.  在 [排除這些安全性群組中的成員] 旁，選擇 [瀏覽]，然後選取 [公司系統管理員]。 此排除動作可讓您管理 Intune 使用者群組，同時又不影響公司系統管理員帳戶 (也稱為租用戶系統管理員)。

5.  在 [定義直接成員資格] 頁面上，選擇 [下一步] 。 由於您要讓 Intune 使用者群組包含除了公司系統管理員以外的所有使用者，因此在此步驟不需要執行任何動作。

6.  在 [摘要] 頁面上，檢閱將要採取的動作，然後選擇 [完成]。

您可以在 [群組] 工作區之 [所有使用者] 下的 [群組] 清單中，找到新建立的群組。 您也可以從這裡編輯或刪除該群組。



### 後續步驟
恭喜！ 您剛完成 *Intune 快速入門指南*的步驟 5。

>[!div class="step-by-step"]

>[&larr; **管理 Intune 授權**](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)       [**建立原則和應用程式** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)  



<!--HONumber=Aug16_HO4-->


