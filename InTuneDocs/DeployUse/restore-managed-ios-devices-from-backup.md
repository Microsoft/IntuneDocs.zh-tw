---
title: "從備份還原受 Intune 管理的 iOS 裝置 | Microsoft Intune"
description: "提供指引給使用者，說明從備份還原後如何重新註冊其裝置。"
keywords: "還原, 受管理, iOS"
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a19e5612-8805-4bd7-a86a-b734bde293ae
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e6bb539c87c4a13a490ba98c016d814bea5c7bbc
ms.openlocfilehash: 6395e50b3e4c06e7363acc136b5ed9eb2ef75abd


---

# 從備份還原受 Intune 管理的 iOS 裝置

您或您的使用者有時必須從備份還原 iOS 裝置，例如當使用者取得新裝置時。 本主題說明為了在還原裝置後設定 Intune 管理所可能必須採取的其他步驟。

## 將備份還原至相同的裝置

如果將備份還原至相同的裝置，也會還原該裝置上的註冊狀態， 而不需要執行其他動作。

## 將備份還原至不同的裝置

如果將備份還原至不同的裝置，則不會自動還原新裝置上的註冊狀態。 使用者必須遵循公司入口網站應用程式之應用程式 2.1.22 版或更新版本的標準註冊步驟，才能[在 Intune 註冊其 iOS 裝置](/Intune/EndUser/enroll-your-device-in-intune-ios)。

> [!NOTE]
> 如果您要設定條件式存取原則的目標使用者，這些使用者必須重新註冊，才能存取公司電子郵件。

> [!TIP]
> 使用者的通訊範例可能如下所示︰若要在您的新裝置上註冊，請確定公司入口網站應用程式為 2.1.22 版或更新版本。 若要檢查版本，請開啟公司入口網站應用程式，點選右上方的功能表按鈕，然後點選 [關於]。 如果您使用舊版，請結束公司入口網站應用程式，然後開啟 App Store。 點選右下角的 [更新] 按鈕，然後點選清單中 [公司入口網站] 項目旁的 [更新] 按鈕。 更新完成之後，請啟動公司入口網站應用程式，並[在 Intune 註冊您的 iOS 裝置](/Intune/EndUser/enroll-your-device-in-intune-ios)。

## 解決已知的還原問題

如果使用者在仍有公司入口網站 2.1.21 版或以前版本時還原其裝置並啟動公司入口網站應用程式，則可能會發生問題。 針對使用者的狀況採取適當的步驟，就可以解決這些問題。

### 只會使用新裝置的使用者
啟動公司入口網站應用程式，並選取目前裝置磚並點選 [移除] 按鈕來取消註冊。 移除之後，請遵循[在 Intune 註冊 iOS 裝置](/Intune/EndUser/enroll-your-device-in-intune-ios)的標準註冊步驟。

### 使用新舊裝置的使用者
點選 [設定] > [Safari] > [Clear History and Website Data] (清除歷程記錄和網站資料)，以從 Safari 清除 Cookie。 清除之後，解除安裝並重新安裝公司入口網站應用程式，然後遵循[在 Intune 註冊 iOS 裝置](/Intune/EndUser/enroll-your-device-in-intune-ios)的標準註冊步驟。



<!--HONumber=Oct16_HO3-->


