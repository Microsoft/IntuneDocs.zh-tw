---
title: 使用 Microsoft Intune 重設 Windows 10 裝置 - Azure | Microsoft Docs
description: 使用 [全新開始] 在 Windows 10 電腦上使用 Microsoft Intune 移除或解除安裝應用程式。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cd2320e4c3935c4865d785bbb2461bba20afffdb
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188733"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>透過 Intune 使用「重新開始」重設 Windows 10 裝置


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

[全新開始] 裝置動作會移除安裝在執行 Windows 10 1703 版或更新版本之電腦上的任何應用程式。 [全新開始] 有利於移除一般新電腦會有的預先安裝 (OEM) 應用程式。  

1. 登入 [Azure 入口網站](https://portal.azure.com) 並移至 > [Microsoft Intune] > [裝置] > [所有裝置]。
2. 從您管理的裝置清單中，選擇 Windows 10 電腦裝置。
3. 按一下 [全新開始]。 
4. 選取 [保留此裝置上的使用者資料] 到：
   * 維持裝置 Azure AD 加入網域的狀態
    * 維持裝置註冊行動裝置管理的狀態 
    * 保留裝置使用者的主資料夾內容，並移除應用程式與設定。  
  > [!IMPORTANT]
 > 若您不保留使用者資料，裝置將還原為出廠預設值。 它將會從 Azure AD 與行動裝置管理取消註冊。 
 
5. 按一下 [確定]。   
6. 若要查看此動作的狀態，請返回 [裝置] 並按一下 [裝置動作]。  
