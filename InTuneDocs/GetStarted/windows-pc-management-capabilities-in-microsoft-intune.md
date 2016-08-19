---
title: "Windows 電腦管理功能 | Microsoft Intune"
description: "深入了解當您使用 Intune 用戶端軟體管理 Windows 電腦時，有關 Intune 的功能。"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 49a236359692a5bbccf9ee0bb263094434049a91
ms.openlocfilehash: f5ade985900e2387b19b4ed2786f22d8a216d8d8


---

# Windows 電腦管理功能 (使用 Microsoft Intune 電腦用戶端)
在大部分情況下，您將使用 Microsoft Intune 註冊您的裝置，其提供的功能集比 Intune 電腦用戶端更大。 不過，您也可以使用提供下列功能的 Intune 電腦用戶端來管理電腦︰

-   **管理軟體更新** - 您可以讓電腦保持在最新狀態，並管理套用更新的時間。

-   **Windows 防火牆原則** - 這有助於確保公司使用的電腦沒有處於非作用中狀態或設定不當的 Windows 防火牆。

-   **反惡意程式碼防護** - Intune 包含 Endpoint Protection，可協助您的電腦防範惡意程式碼。

-   **遠端協助** - Intune 可讓使用者連絡 IT 支援人員，該人員接著可以使用 Intune 隨附的遠端桌面功能提供協助 (需要 TeamViewer 軟體)。

-   **軟體授權管理** - 追蹤軟體有多少可用的授權數目，並且追蹤正在使用多少可用的授權。
-   **應用程式部署** - 將軟體部署到您所管理的電腦。 當您使用用戶端軟體管理電腦時，某些應用程式管理功能無法使用。


Intune 支援在最多 7000 部 Windows 裝置上安裝電腦用戶端軟體。

## 作業系統需求
Intune 可管理執行下列 Windows 版本 (x86 和 x64) 的電腦︰


-   **Windows Vista** - Business、Enterprise 和 Ultimate 版。

-   **Windows 7** - 專業版、企業版和旗艦版 (不含 Service Pack 或含 SP1)。

-   **Windows 8** - 專業版和企業版。

-   **Windows 8.1** - 專業版和企業版。

- **Windows 10** - 專業版、教育版和企業版。


## 最小硬體需求
以下列出安裝 Intune 電腦用戶端的最低硬體需求：

|需求|詳細資料|
|---------------|--------------------|
|Network (網路)|用戶端要求電腦必須具有網際網路連線。|
|處理器和記憶體|請參考電腦作業系統的處理器和 RAM 需求。|
|磁碟空間|安裝用戶端軟體之前需有 200 MB 的可用磁碟空間。|

## 進一步需求
以下列出安裝 Intune 電腦用戶端的硬體需求：

|需求|詳細資料|
|---------------|--------------------|
|系統管理權限|安裝用戶端軟體的帳戶必須擁有該電腦的本機系統管理員權限。|
|Windows Installer 3.1|電腦至少必須安裝 Windows Installer 3.1。|
|移除不相容的用戶端軟體|安裝 Intune 電腦用戶端軟體之前，您必須從該電腦解除安裝下列用戶端軟體：<br /><br />-   任何版本的 Configuration Manager<br />-   任何版本的 Microsoft Systems Management Server (SMS)|

### 請參閱
[Microsoft Intune 的行動裝置管理功能](./mobile-device-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Aug16_HO1-->


