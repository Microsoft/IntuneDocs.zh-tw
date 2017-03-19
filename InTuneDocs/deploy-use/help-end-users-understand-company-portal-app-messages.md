---
title: "使用者可能在 Android 上看見的公司入口網站訊息 | Microsoft Docs"
description: "描述 Intune 使用者可能會看見的公司入口網站應用程式訊息。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0936051b5c33a2e98f275ef7a3a32be2e8f5a8b0
ms.openlocfilehash: 3d5245e809263c2e5d76402ae9adc72baf7c7924
ms.lasthandoff: 03/10/2017


---

# <a name="help-end-users-understand-company-portal-app-messages"></a>幫助使用者了解公司入口網站應用程式訊息

> [!NOTE]
> 下列資訊僅適用於 Android 6.0 和更新版本的裝置。

在註冊程序中的不同時間點，使用者會看見兩個可能要留意的不同訊息。

- __是否允許公司入口網站進行和管理通話？__
- __是否允許公司入口網站存取裝置上的相片、媒體和檔案？__

## <a name="allow-company-portal-to-make-and-manage-phone-calls"></a>是否允許公司入口網站進行和管理通話？

### <a name="where-it-appears"></a>出現的位置
當使用者註冊其裝置，而在公司入口網站應用程式中點選 [註冊] 時，會出現訊息 [是否允許公司入口網站進行和管理通話?]。

### <a name="what-it-means"></a>代表的意義
一旦接受此提示，使用者即允許將其裝置電話號碼和 IMEI 編號傳送到 Intune 服務。 這些資訊會顯示在系統管理員主控台的 [硬體] 頁面上。

> [!NOTE]
> **一律不要讓公司入口網站應用程式進行或管理通話！** 由 Google 控制此訊息文字，且無法變更。

若要查看 [硬體] 頁面，請移至 [群組] > [所有行動裝置] > [裝置]。 選取使用者的裝置，然後移至 **[檢視內容]** > **[硬體]**。

### <a name="what-happens-if-users-deny-access"></a>如果使用者拒絕存取會怎樣
如果使用者拒絕存取，他們還是可以繼續使用公司入口網站應用程式並註冊其裝置。 不過，系統管理員主控台 [硬體] 頁面上的裝置電話號碼及 IMEI 編號將會是空白。 拒絕存取後，當使用者再次登入公司入口網站應用程式時，訊息會顯示 [不要再詢問] 核取方塊，以供使用者選取停止提示。

若使用者在允許之後又拒絕存取，則訊息會在使用者註冊後下一次登入公司入口網站應用程式時出現。

如果使用者稍後決定允許存取，他們可以移至 [設定] > [應用程式] > [公司入口網站] > [權限] > [電話]，然後將它開啟。

### <a name="how-to-explain-this-to-your-users"></a>如何對使用者說明
將使用者移至[在 Intune 註冊 Android 裝置](/Intune/EndUser/enroll-your-device-in-intune-android)，以提供詳細資訊。

## <a name="allow-company-portal-to-access-your-contacts"></a>允許公司入口網站存取您的連絡人？

### <a name="where-it-appears"></a>出現的位置
當使用者註冊其裝置，而在公司入口網站應用程式中點選 [註冊] 時，會出現訊息 [是否允許公司入口網站存取您的連絡人?]。

### <a name="what-it-means"></a>代表的意義
一旦接受此提示，使用者即允許 Intune 建立其工作帳戶，並管理為使用者在該裝置上註冊的 Azure Active Directory 身分識別。

> [!NOTE]
> **Microsoft 永遠不會存取您的連絡人！** 由 Google 控制此訊息文字，且無法變更。

### <a name="what-happens-if-users-deny-access"></a>如果使用者拒絕存取會怎樣
如果使用者拒絕存取，他們的裝置將不會在 Intune 中註冊，而且無法進行管理。 拒絕存取後，當使用者再次登入公司入口網站應用程式時，訊息會顯示 [不要再詢問] 核取方塊，以供使用者選取停止提示。

若使用者在允許之後又拒絕存取，則訊息會在使用者註冊後下一次登入公司入口網站應用程式時出現。

如果使用者稍後決定允許存取，他們可以移至 [設定] > [應用程式] > [公司入口網站] > [權限] > [電話]，然後將它開啟。

### <a name="how-to-explain-this-to-your-users"></a>如何對使用者說明
將使用者移至[在 Intune 註冊 Android 裝置](/Intune/EndUser/enroll-your-device-in-intune-android)，以提供詳細資訊。

## <a name="allow-company-portal-to-access-photos-media-and-files-on-your-device"></a>是否允許公司入口網站存取相片、媒體和裝置上的檔案？

### <a name="where-it-appears"></a>出現的位置
訊息 [是否允許公司入口網站存取裝置上的相片、媒體和檔案?] 會在使用者點選 [傳送資料] 以將記錄檔傳送給 IT 系統管理員時出現。

### <a name="what-it-means"></a>代表的意義
一旦接受此提示，使用者即允許其裝置將資料記錄檔寫入裝置的 SD 記憶卡，以及使用 USB 纜線來移動那些記錄檔。   

> [!NOTE]
> **一律不要讓公司入口網站應用程式存取使用者的相片、媒體和檔案！** 由 Google 控制此訊息文字，且無法變更。

### <a name="what-happens-if-users-deny-access"></a>如果使用者拒絕存取會怎樣
如果使用者拒絕存取，他們仍然可以透過電子郵件傳送資料記錄檔，但記錄檔無法複製到裝置的 SD 記憶卡。

使用者拒絕存取後並再次登入公司入口網站應用程式時，訊息會顯示 **不要再詢問** 核取方塊，使用者可選取該核取方塊讓訊息不再顯示。 若使用者在允許之後又拒絕存取，則訊息會在使用者下一次嘗試傳送記錄檔時出現。 如果使用者稍後決定允許存取，他們可以移至 [設定] > [應用程式] > [公司入口網站] > [權限] > [儲存體]，然後開啟權限。


### <a name="how-to-explain-this-to-your-users"></a>如何對使用者說明
將使用者移至[使用電子郵件將記錄檔傳送給 IT 系統管理員](/Intune/EndUser/send-logs-to-your-it-admin-by-email-android)。 如果要讓使用者比較這兩個方法，您也可以將使用者移至[使用纜線將記錄檔傳送給 IT 系統管理員](/Intune/EndUser/send-logs-to-your-it-admin-by-cable-android)。


### <a name="see-also"></a>請參閱
[告知使用者有關使用 Intune 的事項](/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)

