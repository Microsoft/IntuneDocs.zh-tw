---

title: "Android for Work 原則設定 | Microsoft Intune"
description: "建立可以在您使用 Intune 管理的 Android for Work 裝置上控制設定及功能的原則。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 35a53076-74d6-486d-b201-e0da2e170008
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 32bded5047b1a08738418e3e36382eeae1a5f3b4
ms.openlocfilehash: f7c676b25f5dd5b7ee1d1d7c1b51b75a41b5c102


---

# Microsoft Intune 的 Android for Work 原則設定

Intune 提供一系列您可以在 Android for Work 裝置上設定的內建一般設定。

## 一般組態原則

您可以使用 Intune **Android for Work 一般設定原則**，為您的 Android for Work 裝置設定安全性和工作設定檔設定。

若此主題未包含您所需的設定，您可以使用 Android 自訂原則加以建立，讓您能夠使用 OMA-URI 設定來控制裝置。 如需詳細資訊，請移至本主題稍後的[自訂原則設定](#custom-policy-settings)。

> [!TIP]
> 當您佈建工作設定檔時，裝置會自動加密。 您無法變更此設定。

### 密碼設定

|設定名稱|詳細資料|
|----------------|-|
|**需要密碼來解除鎖定行動裝置**|指定受管理的裝置是否需要密碼。 從下列選項進行選擇：<br><br>- **複雜字集** - 至少需要一個字母、數字和符號<br>- **英數** - 至少需要一個數字和一個字母字元<br>- **字母** - 至少需要字母或符號<br>- **數字複雜字集** - 需要不重複或連續的數字字元<br>- **數字**<br><br>如果未啟用此設定，則沒有複雜性需求。|
|**密碼長度下限**|指定密碼中字元或數字的數目下限。|
|**在停止活動幾分鐘後鎖定裝置**|指定裝置自動鎖定之前，需停止使用者活動達幾分鐘。|
|**允許 Smart Lock 和其他信任代理程式**<br>(Android 6 及更新版本)|讓您在相容的 Android 裝置上控制 Smart Lock 功能。 此電話功能 (有時也稱為信任代理程式) 可讓您在裝置位於受信任的位置 (例如連線到特定的藍牙裝置或靠近 NFC 標記) 時，停用或略過裝置鎖定畫面密碼。您可以使用此設定來防止使用者設定 Smart Lock。|
|**移除工作設定檔前的重複登入失敗次數**|指定移除裝置上的工作設定檔前允許的登入失敗次數。 這不會執行完整裝置抹除。|
|**記住密碼歷程記錄**|防止重複使用先前用過的密碼。|
|**記住密碼歷程記錄** - **不得重複使用以前用過的密碼**|指定要記憶先前使用過的密碼數目。|
|**密碼到期 (天數)**|指定必須變更裝置密碼的天數。|
|**允許指紋解除鎖定**<br>(Android 6 及更新版本)|可讓您使用指紋解除鎖定具有此功能的裝置。|


### 工作設定檔設定

|設定名稱|詳細資料|
|----------------|-|
|**允許工作和個人設定檔間的資料共用**|可讓工作設定檔中的應用程式與使用者個人設定檔中的應用程式共用資料。 從下列選項進行選擇：<br><br>- **禁止邊界之間共用**<br>- **工作設定檔中的應用程式可以處理來自個人設定檔的共用要求**<br>- **共用無限制**|
|**當裝置處於鎖定狀態時，隱藏工作設定檔通知**<br>(Android 6 及更新版本)|控制當裝置處於鎖定狀態時，是否要顯示工作設定檔中的任何通知。|
|**設定預設應用程式權限原則**<br>(Android 6 及更新版本)|設定工作設定檔中所有應用程式的預設權限原則。|




## 自訂原則設定
使用 Microsoft Intune **Android for Work 自訂設定原則**來部署 OMA-URI 設定，此設定可用來控制 Android for Work 裝置上的功能。 這些是許多行動裝置製造商用來控制裝置功能的標準設定。

此功能的目的是讓您部署無法使用 Intune 原則設定的 Android 設定。

> [!NOTE]
> Android 自訂原則目前只支援針對包含預先共用金鑰的 Android 裝置設定 Wi-Fi 設定。

### 一般設定

|設定名稱|詳細資料|
    |----------------|--------------------|
    |**Name**|輸入 Android 自訂原則的唯一名稱，有助於您在 Intune 主控台中識別該原則。|
    |**說明**|提供可給予 Android 自訂原則概觀的說明，以及可協助您找到該說明的其他相關資訊。|

### OMA-URI 設定

   |設定名稱|詳細資料|
    |--------|--------------------|
    |**設定名稱**|輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。|
    |**設定說明**|提供可給予設定概觀的說明，以及可協助您找到該說明的其他相關資訊。|
    |**資料類型**|選取您要在其中指定這個 OMA-URI 設定的日期類型。 選擇 [字串]、[字串 (XML)]、[日期和時間]、[整數]、[浮點數] 或 [布林值]。|
    |**OMA-URI (區分大小寫)**|指定您想要提供設定的 OMA-URI。|
    |**值**|指定要與您先前指定的 OMA-URI 產生關聯的值。|

### 範例

- [使用預先共用金鑰建立 Wi-Fi 設定檔](pre-shared-key-wi-fi-profile.md)
- [使用自訂原則來建立 Android 裝置的個別應用程式 VPN 設定檔](per-app-vpn-for-android-pulse-secure.md)

### 請參閱
[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)


<!--HONumber=Oct16_HO2-->


