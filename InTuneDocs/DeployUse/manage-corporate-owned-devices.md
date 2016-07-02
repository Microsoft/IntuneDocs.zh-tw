---
title: "管理公司裝置 | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 69cf07aa0747448e0ef3384b5b5132e0e76aed45
ms.openlocfilehash: e07053b9b26afacc03e45f2cb104eda6088a1e05


---

# 使用 Microsoft Intune 註冊公司擁有的裝置
根據裝置、購買方式和組織需求，Intune 可以透過各種不同的方式管理組織或公司所擁有的裝置 (COD)。

## 公司擁有的 iOS 裝置
這些註冊方法適合「選擇您自己的裝置」(CYOD) 案例，其中組織會為使用者購買裝置，但想要保有對裝置的管理。 如果您的組織有購買的 iOS 裝置，您可以預先設定註冊，使得裝置在使用者第一次開啟裝置時即受到管理。 Intune 支援透過 [Apple 的裝置註冊程式 (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) 註冊或使用 Mac 電腦上執行的 Apple Configurator 進行[直接](ios-direct-enrollment-in-microsoft-intune.md)或[設定助理](ios-setup-assistant-enrollment-in-microsoft-intune.md)註冊。

[註冊公司擁有的 iOS 裝置](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## 裝置註冊管理員
組織可以使用 Intune，透過稱為裝置註冊管理員帳戶的單一使用者帳戶來管理大量的行動裝置。 建立裝置註冊管理員帳戶後，管理員可以使用該帳戶來註冊多於對一般使用者預設允許的標準五個裝置。 使用裝置註冊管理員來註冊裝置僅適用於特定使用者未使用的裝置。 比方說，這些裝置都適合銷售點或公用程式應用程式，但對於需要電子郵件或公司資源的存取權的使用者而言則不適合。

[使用裝置註冊管理員註冊公司所擁有的裝置](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## 國際行動設備識別 (IMEI)
唯一的國際行動設備識別碼 (IMEI) 號碼是許多行動裝置製造商的通用裝置屬性。 Intune 系統管理員可以匯入公司擁有之裝置的 IMEI 號碼。 當裝置變成由 Intune 管理時，可以將它標記為公司擁有的裝置，並使用適當的原則為目標。

[使用國際行動設備識別碼 (IMEI) 號碼來指定公司擁有的裝置](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)



<!--HONumber=Jun16_HO5-->


