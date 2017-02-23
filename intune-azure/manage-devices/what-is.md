---
title: "使用 Intune 管理裝置 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解如何檢視您使用 Intune 管理的裝置，以及對這些裝置執行各種動作。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 040c4e18d87110ab7380a64540d08127574a7c46
ms.openlocfilehash: 5a967cc1be387f83f95591186f786db61d3debcd


---

# <a name="what-is-device-management"></a>什麼是裝置管理？ 


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

**裝置和群組**工作負載可讓您深入了解您所管理的裝置，並讓您從遠端對這些裝置執行工作。 若要存取工作負載︰

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置和群組]。

    ![裝置和群組工作負載](./media/devices-and-groups-workload.png)

現在，請選擇下列其中一項：

- **概觀** - 取得您註冊的裝置及每部裝置執行之作業系統的資訊。
- **管理** - 選擇 [所有裝置] 可檢視您所管理之所有裝置的清單。
    從清單中選取其中一部裝置，以開啟 [<*裝置名稱*>  概觀] 刀鋒視窗，從中選取下列其中一項︰
    - **概觀** - 檢視裝置的一般資訊，包括其名稱、其擁有者、其是否為 BYOD 裝置、其上次簽入的時間等等。 此外，您也可對裝置執行下列遠端動作 (並非所有平台都支援所有的動作)︰
        - **移除公司資料** - 只移除 Intune 管理的公司資料。 裝置上的個人資料不會移除。 這類裝置將不再由 Intune 管理，而且也無法再存取公司資源 (不適用於加入 Azure Active Directory 的 Windows 裝置)。
        - **恢復出廠預設值** - 將裝置回復成預設設定。 這類裝置將不再由 Intune 管理，而且公司與個人資料皆會移除。 您無法復原此動作。
        - **遠端鎖定** - 鎖定裝置。 裝置擁有者必須使用其密碼才能解除裝置鎖定。 您只可從遠端鎖定具有 PIN 碼或密碼設定的裝置。
        - **重設密碼** - 為裝置產生新的密碼。新密碼會顯示在 [裝置名稱] >  [概觀] 刀鋒視窗中。
        - **略過啟用鎖定** - 即使沒有 Apple ID 及密碼，也可從 iOS 裝置移除啟用鎖定。 當您略過啟用鎖定之後，裝置會在 [尋找我的 iPhone] 應用程式會啟動再次開啟啟用鎖定。 僅當您能夠實際使用裝置時，才略過啟用鎖定。
        - **遺失模式** - 您可以在裝置遭竊時啟用遺失模式。 這可讓您指定的訊息及電話號碼顯示在裝置的鎖定畫面上。
        - **重新啟動** - 強制重新啟動裝置重。 重新啟動時不會自動通知裝置擁有者，因此將會遺失工作。
        ![裝置概觀](http://i.imgur.com/4Rx4VXm.png)
        
    - **硬體** - 檢視更多裝置相關資訊，包括其可用儲存空間、型號、製造商等等。
    ![受管理的裝置硬體清查](./media/hardware-inventory.png)
    - **偵測到的應用程式** - 顯示 Intune 找到已在裝置上安裝的所有應用程式清單。
    ![偵測到的應用程式節點](./media/detected-applications.png)
- **監視** - 選擇 [裝置動作] 可檢視內含已對您管理之裝置執行的裝置動作，以及這些動作目前的狀態的清單。
![監視裝置動作](./media/monitor-device-actions.png)



<!--HONumber=Feb17_HO1-->


