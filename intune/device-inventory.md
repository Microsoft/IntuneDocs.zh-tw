---
title: "檢視 Intune 裝置清查"
titleSuffix: Intune on Azure
description: "了解如何使用 Intune 檢視您管理的裝置，並了解其硬體和已安裝的應用程式。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/25/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dae92c117bcf8a4a8ff133ed613f9f77ea0c07c2
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-view-intune-device-inventory"></a>如何檢視 Intune 裝置清查


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**裝置**工作負載可讓您深入了解所管理的裝置，包括其硬體功能及安裝於其上的應用程式。 

檢視裝置清查：

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。

現在，請選擇下列其中一個選項：

- **概觀** - 取得您註冊的裝置及每部裝置執行之作業系統的資訊。
- **管理** - 選擇 [所有裝置] 可檢視您所管理之所有裝置的清單。
    從清單中選取其中一部裝置，以開啟 [<*裝置名稱*>  概觀] 刀鋒視窗，從中選取下列其中一項︰
    - **概觀** - 查看裝置的一般資訊，包括其名稱、擁有者、是否為 BYOD 裝置及簽入的時間等等。
    ![裝置概觀](./media/device-overview.png)
    - **硬體** - 查看更多裝置相關資訊，包括其可用儲存空間、型號及製造商等等。
    ![受管理的裝置硬體清查](./media/hardware-inventory.png)
    - **探索到的應用程式** - 顯示 Intune 找到已在裝置上安裝的所有應用程式清單。
    ![探索到的應用程式節點](./media/detected-applications.png)
    - **裝置合規性** - 顯示所有已指派給裝置之合規性原則的合規性狀態。
    - **裝置設定** - 顯示所有已指派給裝置之裝置設定原則的合規性狀態。
- **監視** - 選擇 [裝置動作] 可查看內含已對您管理之裝置執行的裝置動作，以及其目前狀態的清單。
- **安裝程式** > **TeamViewer 連接器** - 可讓您使用 TeamViewer 軟體在裝置上設定遠端管理。 如需詳細資料，請參閱[對 Intune 管理的 Android 裝置提供遠端協助](/intune/device-profile-android-teamviewer)。


