---
title: "使用 Intune 管理裝置"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何查看您使用 Intune 管理的裝置，以及對這些裝置執行各種動作。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/13/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 24498abc504f05bd22dc7309bc22948292f9b1e6
ms.openlocfilehash: 731d57859474276b51c0cb0b17a3354eaec17348
ms.lasthandoff: 04/13/2017


---

# <a name="what-is-microsoft-intune-device-management"></a>什麼是 Microsoft Intune 裝置管理？ 


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

**裝置**工作負載可讓您深入了解您所管理的裝置，並讓您從遠端對這些裝置執行工作。 若要存取工作負載︰

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。

現在，請選擇下列其中一項：

- **概觀** - 取得您註冊的裝置及每部裝置執行之作業系統的資訊。
- **管理** - 選擇 [所有裝置] 可檢視您所管理之所有裝置的清單。
    從清單中選取其中一部裝置，以開啟 [<*裝置名稱*>  概觀] 刀鋒視窗，從中選取下列其中一項︰
    - **概觀** - 檢視裝置的一般資訊，包括其名稱、其擁有者、其是否為 BYOD 裝置、其上次簽入的時間等等。 
                
    - **硬體** - 檢視更多裝置相關資訊，包括其可用儲存空間、型號、製造商等等。
    ![受管理的裝置硬體清查](./media/hardware-inventory.png)
    - **偵測到的應用程式** - 顯示 Intune 找到已在裝置上安裝的所有應用程式清單。
    ![偵測到的應用程式節點](./media/detected-applications.png)
- **監視** - 選擇 [裝置動作] 可檢視內含已對您管理之裝置執行的裝置動作，以及這些動作目前的狀態的清單。
![監視裝置動作](./media/monitor-device-actions.png)
- **說明及支援** - 顯示疑難排解與支援文件的連結。

## <a name="available-device-actions"></a>可執行的裝置動作

此外，您也可對裝置執行下列遠端動作 (並非所有平台都支援所有的動作)︰

### <a name="remove-company-data"></a>**移除公司資料**
只移除 Intune 管理的公司資料。 裝置上的個人資料不會移除。 這類裝置將不再由 Intune 管理，而且也無法再存取公司資源 (不適用於加入 Azure Active Directory 的 Windows 裝置)。

### <a name="factory-reset"></a>**重設為原廠設定**
將裝置回復成預設設定。 這類裝置將不再由 Intune 管理，而且公司與個人資料皆會移除。 您無法復原此動作。

### <a name="remote-lock"></a>**遠端鎖定**
鎖定裝置。 裝置擁有者必須使用其密碼才能解除裝置鎖定。 您只可從遠端鎖定具有 PIN 碼或密碼設定的裝置。

### <a name="reset-passcode"></a>**重設密碼**
為裝置產生新的密碼。新密碼會顯示在 [<裝置名稱> 概觀] 刀鋒視窗中。

### <a name="bypass-activation-lock"></a>**略過啟用鎖定**
不使用使用者的 Apple ID 和密碼從 iOS 裝置移除啟用鎖定。 當您略過啟用鎖定之後，裝置會在 [尋找我的 iPhone] 應用程式會啟動再次開啟啟用鎖定。 僅當您能夠實際使用裝置時，才略過啟用鎖定。

### <a name="lost-mode"></a>**遺失模式**
如果 iOS 裝置遺失或遭竊，您可以啟用遺失模式。 這可讓您指定的訊息及電話號碼顯示在裝置的鎖定畫面上。 若要做到這一點，請執行下列動作：
1.    在 iOS 裝置的 [屬性] 刀鋒視窗上，選擇 [更多]  >  [遺失模式]。
2.    在 [遺失模式] 刀鋒視窗中，啟用遺失模式，輸入將顯示的訊息和連絡電話號碼 (選擇性)。
3.    按一下 [ **確定**]。
當您啟用遺失模式時，就會封鎖裝置的所有使用。 使用者無法存取裝置，直到您停用遺失模式。 啟用遺失模式時，您可以使用**尋找裝置**動作找出裝置所在之處。
若要使用遺失模式，裝置必須是透過 DEP 註冊之公司擁有的 iOS 裝置，且處於受監督模式。

### <a name="locate-device"></a>**尋找裝置**
使用這個遠端動作在地圖上顯示遺失或遭竊 iOS 裝置的位置。 裝置必須是透過 DEP 註冊之公司擁有的 iOS 裝置，且處於受監督模式。 使用此動作之前，必須已將裝置設置為遺失模式。
1.    在 iOS 裝置的 [屬性] 刀鋒視窗上，選擇 [更多]  >  [尋找裝置]。
2.    找到裝置之後，它的位置會顯示在 [尋找裝置] 刀鋒視窗上。 
    ![尋找裝置刀鋒視窗](./media/locate-device.png)

>[!NOTE]
>基於隱私權之目的，您能將地圖放大的距離將會受到限制。

### <a name="restart"></a>**重新啟動**
強制裝置重新開機。 重新啟動時不會自動通知裝置擁有者，因此將會遺失工作。


## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>遺失模式的安全性與隱私權資訊以及尋找裝置動作
- 直到您啟用這個動作，裝置位置資訊才會傳送至 Intune。
- 當您使用尋找裝置動作時，裝置的緯度和經度座標會傳送至 Intune，並顯示在 Azure 入口網站中。
- 資料會儲存 24 小時，然後移除。 您無法手動移除位置資料。
- 位置資料在儲存和傳送時皆會加密。
- 當您設定遺失模式時，我們建議您輸入的鎖定畫面顯示訊息包含可以判斷裝置位置的資訊。

