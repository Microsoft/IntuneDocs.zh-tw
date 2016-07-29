---
title: "針對行動應用程式管理準備應用程式 | Microsoft Intune"
description: "本主題中的資訊可協助您決定使用 App Wrapping Tool 和 App SDK 時機，以讓您的自訂企業營運應用程式得以使用行動應用程式管理員則。"
keywords: 
author: karthikaraman
manager: arob98
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2038ed6219a94dc4285891d71ce00fd51310f3e3
ms.openlocfilehash: a7aa32704a8eb33d20a3149941b3e6f2a91478a0


---

# 決定如何準備應用程式以使用 Microsoft Intune 進行行動應用程式管理
您可以使用 Intune App Wrapping Tool 或 Intune App SDK，讓應用程式使用行動應用程式管理原則。 使用這項資訊可了解這兩種方法和其使用時機。

## Intune App Wrapping Tool
App Wrapping Tool 主要用於內部企業營運 (LOB) 應用程式。 此工具是可建立應用程式包裝函式的命令列應用程式，因而可讓 Intune 行動應用程式管理原則管理應用程式。 您不需要原始程式碼即可使用工具，但需要簽署認證。  如需簽署認證的詳細資訊，請參閱 [Intune 部落格](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)。 如需 App Wrapping Tool 文件，請參閱 [Android App Wrapping Tool](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) 和 [iOS App Wrapping Tool](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)。

App Wrapping Tool 不支援 App 或 Play Store 中的應用程式或需要開發時間整合的功能 (請參閱下列功能比較表)。

如果已撰寫應用程式，或原始程式碼無法使用，則您應該使用 App Wrapping Tool，而不是 SDK。

## Intune App SDK
App SDK 的設計主要是針對 App 或 Play Store 中具有應用程式並想要可以使用 Intune 管理應用程式的客戶。 不過，任何應用程式都可以利用 SDK 的整合，即使它是 LOB 應用程式也是一樣。

若要深入了解 SDK，請參閱[概觀](/intune/develop/intune-app-sdk)。 若要開始使用 SDK，請參閱[開始使用 Microsoft Intune App SDK](/intune/develop/intune-app-sdk-get-started)。

## 功能比較
此表格列出您可以用於 App SDK 和 App Wrapping Tool 的設定。

> [!NOTE]
> 只有在使用 Intune 獨立版或 Intune (含 Configuration Manager) 時，才能使用 App Wrapping Tool。

|功能|App SDK|App Wrapping Tool|
|-----------|---------------------|-----------|
|限制要在公司管理的瀏覽器中顯示網頁內容|X|X|
|禁止 Android、iTunes 或 iCloud 備份|X|X|
|允許應用程式將資料傳送到其他應用程式|X|X|
|允許應用程式接收來自其他應用程式的資料|X|X|
|限制與其他應用程式的剪下、複製和貼上|X|X|
|需要簡單的 PIN 碼才能存取|X|X|
|將內建應用程式 PIN 取代為 Intune PIN|X||
|指定 PIN 重設之前的嘗試次數|X|X|
|需要指紋而不是 PIN (僅限 iOS)<br></br>**注意：**僅適用於僅 MAM 環境中。|X||
|需要公司認證才能存取|X|X|
|封鎖受管理的應用程式在已進行 JB 或 Root 破解的裝置上執行|X|X|
|加密應用程式資料|X|X|
|在指定的分鐘數之後重新檢查存取需求|X|X|
|指定離線寬限期|X|X|
|封鎖螢幕擷取 (僅限 Android)|X|X|
|完整抹除|X|X|
|選擇性抹除 <br></br>**注意：**對於 iOS，移除管理設定檔時，也會移除應用程式。|X||
|避免「另存新檔」 |X||
|支援多重身分識別|X||

### 請參閱
[Android App Wrapping Tool](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[iOS App Wrapping Tool](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[使用 SDK 讓應用程式進行行動應用程式管理](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Jul16_HO4-->


