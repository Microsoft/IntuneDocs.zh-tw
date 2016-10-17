---
title: "從備份還原受 Intune 管理的 iOS 裝置 | Microsoft Intune"
description: "提供指引給使用者，說明從備份還原後如何重新註冊其裝置。"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a19e5612-8805-4bd7-a86a-b734bde293ae
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 612b0954a81de1ee8d4a1e96c7440239437dec14
ms.openlocfilehash: 5fc4423f8fd0c5829be5fe6c96949e126991e430


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



<!--HONumber=Oct16_HO2-->


