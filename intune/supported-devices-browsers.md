---
title: "支援的裝置 - Microsoft Intune"
description: "列出 Intune 裝置管理所支援的裝置平台及瀏覽器"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: df9c4c0a0a23740bf9df4c13e34b8752838aa99a
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="supported-devices-and-browsers"></a>支援的裝置與瀏覽器

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

本文適用於負責管理企業裝置的系統管理員。 如需在手機上安裝 Intune 方面的協助，請參閱 [Using managed devices to get work done](/intune-user-help/company-portal-frequently-asked-questions) (使用受管理的裝置完成工作)。

開始設定 Microsoft Intune 之前，請先檢閱下列需求︰

- [支援的裝置和電腦](#intune-supported-devices)
- [支援使用 Intune 的網頁瀏覽器清單](#intune-supported-web-browsers)

您也應該進一步熟悉 [Intune 網路頻寬用量](network-bandwidth-use.md) ([傳統主控台](/intune-classic/get-started/network-bandwidth-use))。

## <a name="intune-supported-devices"></a>支援 Intune 的裝置

您可以使用 Intune 行動裝置管理來管理下列裝置：

[!INCLUDE[mdm-supported-devices](./includes/mdm-supported-devices.md)]

Intune 無法用於管理 Windows Server 作業系統。

### <a name="windows-pc-software-client"></a>Windows 電腦軟體用戶端

[Intune 軟體用戶端](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune)可以部署並安裝在 Windows 電腦上當作替代的註冊方法。 只有使用 Intune 傳統主控台時才提供這項功能。 您可以使用 Intune 軟體用戶端來管理 Windows 7 與更新版的電腦 (除了 Windows 10 家用版以外)。

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Intune 支援網頁瀏覽器

執行不同的系統管理工作時，您必須使用下列其中一個系統管理網站。

- [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Intune 入口網站](https://portal.azure.com/)

以下是這些入口網站支援的瀏覽器：
- Microsoft Edge (最新版本)
- Microsoft Internet Explorer 11
- Safari (最新版本，僅限 Mac)
- Chrome (最新版本)
- Firefox (最新版本)

### <a name="intune-classic-portal"></a>Intune 傳統入口網站

Intune 傳統專屬功能只在 Intune 傳統入口網站 (https://manage.microsoft.com) 中提供，例如 Intune 電腦軟體用戶端及與 Mobile Threat Defense 合作夥伴之間的整合。 傳統 Intune 主控台需要 Silverlight 瀏覽器支援。

下列 Silverlight 瀏覽器支援傳統 Intune 主控台：
- Internet Explorer 10 或更新版本
- Google Chrome (42 版之前的版本)
- 啟用 Silverlight 的 Mozilla Firefox [深入了解](https://go.microsoft.com/fwlink/?linkid=836872)

> [!Note]
> 因為 Microsoft Edge 和行動瀏覽器不支援 [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx)，所以 Intune 傳統主控台不予支援。


唯有具有服務系統管理員權限的使用者，或是具有全域系統管理員角色的租用戶系統管理員，才能登入此入口網站。 若要存取管理主控台，您的帳戶必須擁有使用 Intune 的授權，且登入狀態必須為 [已允許]。
