---
title: "Exchange ActiveSync 原則設定 | Microsoft Intune"
description: "使用 Intune Exchange ActiveSync 原則進行設定，讓您能夠控制由 Exchange ActiveSync 所管理之裝置上的特性與功能。"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9cbb826-b155-4df6-abf3-60c6f05b2783
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 72e6bcd3fd480c1ed8558fefd3958b4bbf3184c2
ms.openlocfilehash: 39a844db56edf18f25996c1aaf52223ac80f8071


---

# Microsoft Intune 的 Exchange ActiveSync 原則設定
使用 Microsoft Intune **Exchange ActiveSync** 原則進行設定，進而控制 Exchange ActiveSync 所管理之裝置上的各種特性與功能。


## 密碼設定

|設定名稱|詳細資料
|----------------|
|**需要密碼來解除鎖定行動裝置**|指定是否必須使用密碼鎖定裝置。<br>(不適用於執行 Windows RT 的裝置)。|
|**所需的密碼類型**|指定必要密碼的類型，例如只可包含數字，或必須是英數字元等等。|
|**密碼長度下限**|指定裝置密碼所需的字元數下限。|
|**允許簡單密碼**|指定您是否可以使用簡單密碼，包括 '0000' 與 '1234'。|
|**抹除裝置前允許的重複登入失敗次數**|指定抹除裝置前允許使用者輸入錯誤密碼的次數。|
|**密碼到期 (天數)**|指定在幾天之後必須變更該裝置的密碼。
|**記住密碼歷程記錄**|指定是否不允許使用先前使用過的密碼。|
|**記住密碼歷程記錄** - **不得重複使用以前用過的密碼**|指定不得重複使用先前使用過的密碼數目。|
|**要求密碼前的閒置分鐘數**|指定裝置必須閒置多少時間，才會鎖定螢幕。

## 加密設定

|設定名稱|詳細資料|
|----------------|
|**在行動裝置上要求加密**<sup>1</sup>|要求在受支援時加密裝置上的資料。<br><br>對於 Windows Phone 8 裝置，您必須將此項目設定為 [是] 。<br /><br />若要在 iOS 裝置上啟用加密，可啟用 **[需要密碼才可將行動裝置解除鎖定]** 設定。|
|**儲存卡需要加密**|需要加密外部儲存體 (例如 SD 記憶卡) 上所儲存的資料 (在支援的裝置上)。
<sup>1</sup> 執行 Windows 8.1 之裝置的其他資訊

-   若要在執行 Windows 8.1 的裝置上強制加密，您必須在每個裝置上安裝 [2014 年 12 月適用於 Windows 的 MDM 用戶端更新](http://support.microsoft.com/kb/3013816)。

-   如果您針對 Windows 8.1 裝置啟用此設定，則裝置的所有使用者必須都具有 Microsoft 帳戶。

-   若要在 Windows 8.1 裝置上進行加密，裝置必須符合 Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) 硬體認證需求。

-   當您在 Windows 8.1 裝置上強制加密時，就只能從使用者的 Microsoft 帳戶存取修復金鑰，該帳戶是從使用者的 OneDrive 帳戶進行存取。 您無法代表使用者修復此金鑰。

## 電子郵件設定

|設定名稱|詳細資料
|----------------|
|**允許使用者下載電子郵件附件**|指定是否可以將電子郵件附件下載到裝置。|
|**電子郵件同步處理時段**|指定將收到的電子郵件同步處理到裝置的天數。
|**允許不完全支援 Exchange ActiveSync 設定的行動裝置與 Exchange 進行同步處理**|指定是否允許不支援一個或多個 Exchange ActiveSync 設定之裝置上的 Exchange 存取。

## 瀏覽器設定

|設定名稱|詳細資料
|----------------|-
|**允許網頁瀏覽器**|指定是否可以使用裝置上的網頁瀏覽器<br>(不適用於 Windows RT 或 Windows Phone)。

## 硬體設定

|設定名稱|詳細資料
|----------------|
|**允許相機**|指定是否可以使用裝置上的相機<br>(不適用於 Windows RT 或 Windows Phone)。



### 請參閱
[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Jul16_HO5-->


