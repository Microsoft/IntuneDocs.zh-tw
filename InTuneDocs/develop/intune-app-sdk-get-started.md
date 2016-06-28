---
title: "開始使用 Microsoft Intune App SDK | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: b7f62c5ee18d8f69fa174f09a1c46b6925c7517c
ms.openlocfilehash: a042f0c6206e9aaf4ec0eb012a70930aa95ecc47


---

# 開始使用 Microsoft Intune App SDK

本入門指南可協助您使用 Microsoft Intune 快速啟用行動應用程式的行動應用程式管理功能。 若能先了解 [Intune App SDK 概觀](intune-app-sdk.md)中所列舉的 Intune App SDK 優點，可能會對您很有幫助。

本指南的主要步驟，可逐步引導您使用 Microsoft Intune 啟用應用程式的行動應用程式管理功能。 Intune App SDK 支援跨平台的類似案例，而且能為 IT 系統管理員建立跨平台的一致體驗。 不過，由於平台限制，因此針對特定功能的支援有些微差異。

# 快速入門

## 註冊 Microsoft Connect

Intune App SDK 目前可透過 Microsoft Connect 存取，並需要註冊。 若要這樣做，請使用公司電子郵件註冊 [Microsoft 帳戶](https://connect.microsoft.com/ConfigurationManagervnext/InvitationUse.aspx?ProgramID=8967&InvitationID=8967-YJYJ-8G6X)。

在 Intune 小組檢閱您的要求之前，您的註冊會處於擱置狀態。 一般的回應時間為 2-3 個工作天內。 一旦核准之後，您會收到電子郵件通知，其中含有連結可下載您的平台適用的 Intune App SDK 和所有相關指南。 您也可以前往 MSDN 網站存取這些指南。

## 向 Microsoft Intune 註冊您的市集應用程式

**如果啟用的應用程式是不會在 Apple 或 Google App Store 中提供的公司內部應用程式**：您就不需要註冊應用程式。 針對這類內部應用程式，IT 系統管理員可將它們直接載入 Microsoft Intune 主控台以進行部署，Intune 即會偵測到應用程式已使用 SDK 建置，並提供 IT 系統管理員套用 MAM 原則的選項。 您可以跳到標題為[使用 SDK 啟用 iOS 或 Android 行動應用程式的 MAM](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk) 這一節。

**如果您是 ISV，且開發的應用程式可透過 Apple 或 Google App Store 提供給客戶**：您必須先向 Microsoft Intune 註冊應用程式並同意註冊條款。 此時，您可以提供應用程式的深層連結。 之後，IT 系統管理員即可將 Intune MAM 原則套用至應用程式。 等到註冊已完成且 Microsoft Intune 小組確認之後，應用程式深層連結的管理主控台中就不會有可套用 MAM 原則的選項。 Microsoft 也會維護 Microsoft Intune 合作夥伴網站 (應用程式在此註冊)，以讓客戶知道此網站支援 Microsoft Intune MAM 原則。

若要開始註冊程序，請**檢閱並簽署** [Microsoft Intune 合作夥伴協議](https://connect.microsoft.com/ConfigurationManagervnext/Survey/Survey.aspx?SurveyID=17806)。 本協議說明相關條款，您的公司必須先接受這些條款，才能成為 Microsoft Intune 應用程式合作夥伴。 您必須登入才能檢視這份文件。 您可以在 [問卷] 索引標籤下或此處的 Intune App SDK Microsoft Connect 網站中找到協議。 您必須提供應用程式名稱、公司名稱以及應用程式的 Google 或 iTunes 商店深層連結。

![Microsoft Connect](../media/microsoft-connect.png)

我們將使用您註冊的電子郵件地址，以確認並完成註冊程序回條。 此外，如果有任何疑慮，我們也會使用您註冊的電子郵件地址與您連絡。

**註冊程序的相關作業**：提交表單之後，Microsoft 會透過您註冊的電子郵件地址連絡您，以確認成功回條或要求其他資訊以完成註冊。 此外，當您的應用程式成功向 Microsoft Intune 註冊，以及當 Microsoft Intune 合作夥伴的網站上將您的應用程式顯示為精選應用程式時也會連絡您。 確認資訊回條之後，下一次的每月 Intune 服務更新中就會包含您的應用程式深層連結。 例如，如果在 7 月完成註冊資訊，將於 8 月中支援應用程式深層連結。 如果未來您的市集應用程式深層連結有所變更，則必須重新註冊應用程式。 此外，如果您使用新版 Intune App SDK 更新您的應用程式，也務必通知我們。

**注意**：上述表單中收集的所有資訊，以及與 Intune 小組的電子郵件通訊都會遵循 [Microsoft 隱私權聲明](https://www.microsoft.com/en-us/privacystatement/default.aspx)的原則。

## 使用 SDK 啟用 iOS 或 Android 行動應用程式的 MAM

若要啟用 iOS 行動應用程式，您需要下列項目：

1. **[Intune App SDK for iOS 開發人員指南](intune-app-sdk-ios.md)**：本文件將逐步引導您使用 Intune App SDK 來啟用 iOS 行動應用程式。 您可在隨附於已下載之 Intune App SDK 套件的文件資料夾中找到這份文件。
2. **iOS 的 Intune App SDK**：隨附於從 Microsoft Intune 下載的 Intune App SDK 套件中，您可找到名稱為 “Intune App SDK for iOS” 的已簽署資料夾。 此資料夾含有 iOS 的 Intune App SDK 的所有內容。

若要使用 Intune App SDK 啟用 Android 行動應用程式，您需要下列項目：

1. **[Intune App SDK for Android 開發人員指南](intune-app-sdk-android.md)**：本文件將逐步引導您使用 Intune App SDK 啟用 Android 行動應用程式。 您可在隨附於已下載之 Intune App SDK 套件的文件資料夾中找到這份文件。
2. **Android 的 Intune App SDK**：隨附於從 Microsoft Intune 下載的 Intune App SDK 套件中，您可找到名稱為 “Intune App SDK for Android” 的已簽署資料夾。 此資料夾含有 Android 的 Intune App SDK 的所有內容。

## 關閉應用程式的遙測功能

**iOS 的 Intune App SDK**：SDK 預設會記錄使用事件的相關 SDK 遙測資料。 這些資料會傳送到 Microsoft Intune。

如果您選擇不要將 SDK 遙測資料從應用程式傳送至 Microsoft Intune，您**必須停用** SDK 遙測傳輸，方法是在 `IntuneMAMSettings` 中，將 `MAMTelemetryDisabled` 屬性設定為 ‘YES’。

**Android 的 Intune App SDK**：不會透過 SDK 記錄 SDK 遙測資料。

## 使用 Microsoft Intune 測試啟用 MAM 的應用程式

當您完成啟用 iOS 或 Android Intune App SDK 的必要步驟 (整合 Intune App SDK) 後，您必須確定對使用者和 IT 系統管理員來說，所有應用程式管理原則皆已啟用且正常運作。 若要測試已啟用功能的應用程式，您需要下列項目：

1. **使用 Microsoft Intune 測試啟用 MAM 的應用程式**：本文件將逐步引導您使用 Microsoft Intune 測試啟用 MAM 的 iOS 或 Android 應用程式。 您可在隨附於已下載之 Intune App SDK 套件的文件資料夾中找到這份文件。
2. **Microsoft Intune 帳戶**：若要使用 Microsoft Intune 測試啟用 MAM 的應用程式，您必須具備 Microsoft Intune 帳戶。 如果您是啟用 MAM 的 iOS 或 Android 市集應用程式的 ISV，完成註冊步驟中所述的 Microsoft Intune 註冊後，即會收到促銷代碼。 促銷代碼可讓您註冊 Microsoft Intune 試用版，以延續使用一年。 如果您開發的是不會傳送至商店的商務應用程式，則應該透過組織來存取 Microsoft intune。 您也可以註冊 [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) 以獲得 1 個月免費試用版。




<!--HONumber=May16_HO2-->


