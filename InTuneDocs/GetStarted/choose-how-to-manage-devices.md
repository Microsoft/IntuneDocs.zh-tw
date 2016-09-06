---
title: "選擇如何管理裝置 | Microsoft Intune"
description: "了解您可以註冊和管理裝置的各種方式。"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 770aad50-fd7a-4cf1-a793-f95fe47fc3f8
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c329bd08aaf72ae2acaa03dcb12c911d84b46b4e
ms.openlocfilehash: cfd9df3814d0d306a254a5566155a91ce5d0ca16


---

# 選擇如何管理裝置
Intune 可讓您向服務註冊某個範圍的裝置來管理這些裝置。 使用者接著可以使用*公司入口網站*來執行各種作業，例如註冊其裝置、瀏覽及安裝應用程式、確定他們的裝置與公司原則相容，及連絡其 IT 支援。

## 管理行動裝置的方式
Intune 可以管理下列裝置平台︰

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

> [!NOTE]
> 如果您先前註冊的裝置所執行的 iOS 版本比支援的版本還舊，則裝置會維持為註冊。 請檢查文件，確認這項功能支援的 iOS 版本。

Intune 可以管理使用者的裝置，也就是一般熟知的「攜帶您自己的裝置」(BYOD)。 其也可以管理公司擁有的裝置，包括以下情境：公司提供一系列使用者可以從中選擇的裝置，稱為「選擇您自己的裝置」 (CYOD)。

### 註冊裝置進行管理
針對包括 iOS、Android 和 Windows Phone 的行動裝置作業系統，您永遠必須註冊裝置。 如何依據組織需求選擇註冊裝置的方式︰

|註冊類型|BYOD|CYOD|具有管理員帳戶的共用裝置|沒有使用者帳戶的共用裝置|
|-------------------|--------|--------|--------------------------------------|----------------------------------------|
|**說明**|使用 Microsoft Intune 註冊的個人裝置|單一使用者的公司所擁有的裝置|使用許多使用者共用之管理員帳戶所管理的公司所擁有的裝置|許多使用者所使用的公司所擁有的無使用者裝置。|
|**裝置的使用者**|Owner|指派的使用者|沒有使用者特定的帳戶|沒有特定的使用者|
|**註冊者？**|Owner|系統管理員|裝置管理員|任何人|
|**取消註冊者？**|擁有者或系統管理員|平台 |系統管理員或使用者|系統管理員或使用者|
|**可重設者？**|擁有者或系統管理員|系統管理員|系統管理員|系統管理員|

如需其他指引，請參閱 [choose how to enroll mobile devices](/intune/get-started/choose-how-to-enroll-devices1) (選擇註冊行動裝置的方式)。

> [!NOTE]
> 請參閱[行動裝置管理功能](mobile-device-management-capabilities-in-microsoft-intune.md)以取得註冊裝置提供之功能的完整清單。

## 如何管理 Windows 電腦
Intune 可以使用 Intune 電腦用戶端來管理 Windows Vista 和更新版本的 Windows 電腦。 不過，若為 Windows 電腦，您可以選擇註冊它們，或安裝 Intune 電腦用戶端軟體來提供註冊裝置時無法使用的一些功能。 在大部分情況下，您將使用 Intune 註冊 Windows 裝置，提供比電腦用戶端更大的功能集。

當您想要執行下列工作時，請考慮使用 Intune 電腦用戶端︰

- 使用任何 Microsoft Intune 電腦用戶端啟用的功能來管理您的 Windows 電腦
- 管理執行不支援註冊之作業系統的 Windows 電腦

> [!NOTE]
> 如需在支援的 Windows 電腦上安裝 Intune 電腦用戶端的完整功能清單，請參閱 [Windows PC 管理功能](windows-pc-management-capabilities-in-microsoft-intune.md)。

## Exchange ActiveSync 管理
您也可以使用 Exchange ActiveSync 來管理裝置。 這需要您安裝 On-Premises Connector 或使用內建的 Service to Service Connector 連線到您的 Exchange Server。

若要了解安裝 On-Premises Connector 的軟硬體需求，請參閱[適用於 On-Premises Connector 的需求](/intune/deploy-use/intune-on-premises-exchange-connector#requirements-for-the-on-premises-connector)。

若要了解如何使用 On-premises Connector 或 Service to Service Connector 與 Exchange，請參閱[使用 Exchange ActiveSync 和 Microsoft Intune 的行動裝置管理](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)。



## 後續步驟
現在您已經發現使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 註冊裝置時可使用的一些功能。 接下來，您需要[註冊您的裝置](/intune/deploy-use/enroll-devices-in-microsoft-intune)。 註冊裝置之後，您可以利用您已在本主題中閱讀的所有功能。 <!--lindavr: There's a logical flaw in our "get to know/get started" content. You can take the path in this topic or you can take the path in the What to know before your get started topic. And they don't cover the same ground. -->



<!--HONumber=Aug16_HO3-->


