---
title: 使用應用程式防護原則的存取動作抹除資料
titleSuffix: Microsoft Intune
description: 了解如何在 Microsoft Intune 中，使用應用程式防護原則的存取動作選擇性地抹除資料。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: cd323fce7f7bdbf17697c82935a9d2d5f47bb7ee
ms.sourcegitcommit: 6e07c35145f70b008cf170bae57143248a275b67
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66804675"
---
# <a name="selectively-wipe-data-using-app-protection-policy-access-actions-in-intune"></a>在 Intune 中使用應用程式防護原則的存取動作選擇性地抹除資料

使用 Intune 應用程式防護原則，您可以進行一些設定，以封鎖終端使用者存取公司應用程式或帳戶。 這些設定的目標是資料重新配置和存取需求，您的組織會針對已進行 JB 破解的裝置和最低 OS 版本等項目設定這些需求。
 
您可以使用這些設定，明確地選擇從終端使用者的裝置中抹除貴公司的公司資料，作為不符合規範時所要採取的動作。 在某些設定中，您可以設定多個動作，例如根據不同的指定值封鎖存取及抹除資料。

## <a name="create-an-app-protection-policy-using-access-actions"></a>使用存取動作建立應用程式防護原則

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在 [Intune]  窗格中，選取 [用戶端應用程式]   > [應用程式保護原則]  。
4. 按一下 [新增原則]  (您也可以編輯現有的原則)。 
5. 按一下 [設定必要設定]  ，以查看可針對原則設定的設定清單。 
6. 藉由在 [設定] 窗格中向下捲動，您會看到標題為 [存取動作]  的區段與可編輯的資料表。

    ![Intune 應用程式防護存取動作的螢幕擷取畫面](./media/apps-selective-wipe-access-actions01.png)

7. 選取 [設定]  ，並輸入使用者必須符合以登入公司應用程式的 [值]  。 
8. 選取使用者不符合您的需求時要採取的 [動作]  。 在某些情況下，您可以針對單一設定指定多個動作。 如需詳細資料，請參閱[如何建立及指派應用程式防護原則](app-protection-policies.md)。

>[!NOTE]
> 若要使用 [裝置型號] 或 [裝置製造商]  設定，請輸入以分號分隔的型號識別碼清單。 避免在多個值的清單中有空格。 這些值不會區分大小寫。 

## <a name="policy-settings"></a>原則設定 

應用程式防護原則設定資料表包含 [設定]  、[值]  和 [動作]  資料行。

### <a name="ios-policy-settings"></a>iOS 原則設定
針對 iOS，您能夠使用 [設定]  下拉式清單設定下列設定的動作：
-  PIN 碼嘗試次數上限
-  離線寬限期
-  已進行 JB 或 Root 破解的裝置
-  最低 OS 版本
-  最低應用程式版本
-  最低 SDK 版本
-  裝置型號

若要使用 [裝置型號]  設定，請輸入以分號分隔的 iOS 型號識別碼清單。 您可以在 [HockeyApp 支援文件](https://support.hockeyapp.net/kb/client-integration-ios-mac-os-x-tvos/ios-device-types)中的 [裝置類型] 欄下方找到 iOS 機型識別碼。<br>
範例輸入：*iPhone5,2; iPhone5,3*

在使用者裝置上，Intune 用戶端將會根據應用程式防護原則在 Intune 中指定的裝置型號字串來進行簡單比對，藉以採取動作。 比對完全取決於裝置所報告的型號。 建議您 (即 IT 系統管理員) 根據各種不同的裝置製造商和型號，並以少數的使用者群組為目標測試此設定，以確保會出現預期的行為。 預設值是**未設定**。<br>
設定下列其中一個動作： 
- 允許指定 (封鎖非指定)
- 允許指定 (抹除非指定)

**針對相同 Intune 使用者的相同應用程式，如果 IT 系統管理員在多個原則之間輸入不同的 iOS 型號識別碼清單，會發生什麼事？**<br>
當設定值的兩個應用程式保護原則之間發生衝突時，Intune 通常會採用最嚴格的方法。 因此，傳送給目標 Intune 使用者所開啟目標應用程式的結果原則，將是以相同應用程式/使用者組合為目標之*原則 A* 和*原則 B* 中所列出的 iOS 型號識別碼的交集。 例如，*原則 A* 指定 "iPhone5,2;iPhone5,3"，而*原則 B* 指定 "iPhone5,3"，則*原則 A* 和*原則 B* 的目標 Intune 使用者結果原則會是 "iPhone5,3"。 

### <a name="android-policy-settings"></a>Android 原則設定

針對 Android，您能夠使用 [設定]  下拉式清單設定下列設定的動作：
-  PIN 碼嘗試次數上限
-  離線寬限期
-  已進行 JB 或 Root 破解的裝置
-  最低 OS 版本
-  最低應用程式版本
-  最低修補程式版本
-  裝置製造商
-  SafetyNet 裝置證明
-  對應用程式進行威脅掃描

若要使用 [裝置製造商]  設定，請輸入以分號分隔的 Android 製造商清單。 您可以在 [裝置設定] 下找到裝置的 Android 製造商。<br>
範例輸入：*製造商 A;製造商 B* 

>[!NOTE]
> 這些是使用 Intune 從裝置回報的一些常見製造商，您可將它們作為輸入項目：Asus;Blackberry;Bq;Gionee;Google;Hmd global;Htc;Huawei;Infinix;Kyocera;Lemobile;Lenovo;Lge;Motorola;Oneplus;Oppo;Samsung;Sharp;Sony;Tecno;Vivo;Vodafone;Xiaomi;Zte;Zuk

在使用者裝置上，Intune 用戶端將會根據應用程式防護原則在 Intune 中指定的裝置型號字串來進行簡單比對，藉以採取動作。 比對完全取決於裝置所報告的型號。 建議您 (即 IT 系統管理員) 根據各種不同的裝置製造商和型號，並以少數的使用者群組為目標測試此設定，以確保會出現預期的行為。 預設值是**未設定**。<br>
設定下列其中一個動作： 
- 允許指定 (封鎖非指定)
- 允許指定 (抹除非指定)

**針對相同 Intune 使用者的相同應用程式，如果 IT 系統管理員在多個原則之間輸入不同的 Android 製造商清單，會發生什麼事？**<br>
當設定值的兩個應用程式保護原則之間發生衝突時，Intune 通常會採用最嚴格的方法。 因此，傳送給目標 Intune 使用者所開啟目標應用程式的結果原則，將是以相同應用程式/使用者組合為目標之*原則 A* 和*原則 B* 中所列出的 Android 製造商的交集。 例如，*原則 A* 指定 "Google;Samsung"，而*原則 B* 指定 "Google"，則*原則 A* 和*原則 B* 的目標 Intune 使用者結果原則會是 "Google"。 

### <a name="additional-settings-and-actions"></a>額外的設定和動作 

若 [需要 PIN 碼才可存取]  設定設為 [是]  ，則根據預設，資料表將包含填入的資料列作為針對 [離線寬限期]  和 [PIN 碼嘗試次數上限]  設定的設定。
 
若要進行設定，請從 [設定]  資料行底下的下拉式清單中選取某個設定。 選取設定之後，如果必須設定值，可編輯的文字方塊就會在相同資料列的 [值]  資料行底下變成啟用狀態。 此外，下拉式清單會在 [動作]  資料行底下變成啟用狀態，其中包含一組適用於該設定的條件式啟動動作。 

下列清單提供常見的動作清單：
-  **封鎖存取** – 封鎖終端使用者存取公司應用程式。
-  **抹除資料** – 從終端使用者的裝置抹除公司資料。
-  **警告** – 提供對話方塊向終端使用者顯示警告訊息。

在某些情況下，例如 [最低 OS 版本]  設定，您可以進行此設定，根據不同的版本號碼來執行所有適用的動作。 

![應用程式保護存取動作的螢幕擷取畫面 - 最小 OS 版本](./media/apps-selective-wipe-access-actions05.png)

進行完整設定之後，資料列就會顯示在唯讀檢視中，而且可以隨時加以編輯。 此外，該資料列在 [設定]  資料行中似乎有可供選擇的下拉式清單。 已設定但不允許多個動作的設定將無法在下拉式清單中選取。

## <a name="next-steps"></a>後續步驟

了解 Intune 應用程式防護原則的詳細資訊，請參閱：
- [如何建立及部署應用程式保護原則](app-protection-policies.md)
- [iOS 應用程式防護原則設定](app-protection-policy-settings-ios.md)
- [Microsoft Intune 的 Android 應用程式防護原則設定](app-protection-policy-settings-android.md) 
