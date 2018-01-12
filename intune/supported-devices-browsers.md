---
title: "支援的裝置 - Microsoft Intune"
description: "列出 Intune 裝置管理所支援的裝置平台及瀏覽器"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 01/03/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 56516562b9a7510020475d226c74bf719bdd33a3
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2018
---
# <a name="supported-devices-and-browsers"></a>支援的裝置與瀏覽器

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

本文適用於負責管理企業裝置的系統管理員。 如需在手機上安裝 Intune 方面的協助，請參閱 [Using managed devices to get work done](/intune-user-help/company-portal-frequently-asked-questions) (使用受管理的裝置完成工作)。

開始設定 Microsoft Intune 之前，請先檢閱下列需求︰

- [支援的裝置和電腦](#intune-supported-devices)
- [支援使用 Intune 的網頁瀏覽器清單](#intune-supported-web-browsers)

您也應該進一步熟悉 [Intune 網路頻寬用量](network-bandwidth-use.md) ([傳統入口網站](/intune-classic/get-started/network-bandwidth-use))。

## <a name="intune-supported-devices"></a>支援 Intune 的裝置

您可以使用 Intune 行動裝置管理來管理下列裝置：

[!INCLUDE[mdm-supported-devices](./includes/mdm-supported-devices.md)]

### <a name="supported-samsung-knox-standard-devices"></a>支援的 Samsung Knox Standard 裝置

公司入口網站應用程式僅會在 MDM 註冊期間嘗試啟用 Samsung Knox (如果[支援的 Knox 裝置清單](https://www.samsungknox.com/knox-supported-devices/knox-workspace) \(英文\) 中包含該裝置的話)。 這有助於避免 Knox 啟用錯誤而導致 MDM 註冊失敗。 如果裝置不支援 Samsung Knox 啟用，則會註冊為標準 Android 裝置。 相同 Samsung 裝置的某些型號可能支援 Knox，而其他則不支援。 在您購買及部署 Samsung 裝置之前，請先跟裝置轉銷商確認 Knox 相容性。

> [!NOTE]
> 註冊 Samsung Knox 裝置可能會需要[啟用針對 Samsung 伺服器的存取](https://support.samsungknox.com/hc/articles/115013833108-Our-corporate-devices-are-behind-a-firewall-How-do-I-enable-Knox-Workspace-devices-to-contact-Samsung-servers) \(英文\)。 

下列清單中的 Samsung 裝置型號不支援 Knox，因此 Android 版公司入口網站應用程式會將其註冊為原生 Android 裝置：

| **裝置名稱** | **裝置型號** |
| --- | --- |
| Galaxy Avant | SM-G386T |
| Galaxy Core 2/Core 2 Duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime Value Edition | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Galaxy J1 Ace | SM-J110F<br>SM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200H<br>SM-J210F |
| Galaxy J3 | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002<br>SM-N9009 |
| Galaxy Note 7/Note 7 Duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730A<br>SM-G730V |
| Galaxy S3 Neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W |
| Galaxy S6 Edge | 404SC |
| Galaxy Tab A 7.0&quot; | SM-T280<br>SM-T285 |
| Galaxy Tab 3 7&quot;/Tab 3 Lite 7&quot; | SM-T116<br>SM-T210<br>SM-T211 |
| Galaxy Tab 3 8.0&quot; | SM-T311 |
| Galaxy Tab 3 10.1&quot; | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |

Intune 無法用於管理 Windows Server 作業系統。

### <a name="windows-pc-software-client"></a>Windows 電腦軟體用戶端

[Intune 軟體用戶端](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune)可以部署並安裝在 Windows 電腦上當作替代的註冊方法。 只有使用 Intune 傳統入口網站時才提供這項功能。 您可以使用 Intune 軟體用戶端來管理 Windows 7 與更新版的電腦 (除了 Windows 10 家用版以外)。

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Intune 支援網頁瀏覽器

執行不同的系統管理工作時，您必須使用下列其中一個系統管理網站。

- [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Azure 入口網站](https://portal.azure.com/)

以下是這些入口網站支援的瀏覽器：
- Microsoft Edge (最新版本)
- Microsoft Internet Explorer 11
- Safari (最新版本，僅限 Mac)
- Chrome (最新版本)
- Firefox (最新版本)

### <a name="intune-classic-portal"></a>Intune 傳統入口網站

Intune 傳統專屬功能只在 Intune 傳統入口網站 (https://manage.microsoft.com) 中提供，例如 Intune 電腦軟體用戶端及與 Mobile Threat Defense 合作夥伴之間的整合。 Intune 傳統入口網站需要 Silverlight 瀏覽器支援。

下列 Silverlight 瀏覽器支援 Intune 主控台：
- Internet Explorer 10 或更新版本
- Google Chrome (42 版之前的版本)
- 啟用 Silverlight 的 Mozilla Firefox [深入了解](https://go.microsoft.com/fwlink/?linkid=836872)

> [!Note]
> 因為 Microsoft Edge 和行動瀏覽器不支援 [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx) \(英文\)，所以 Intune 傳統入口網站不予支援。

唯有具有服務系統管理員權限的使用者，或是具有全域系統管理員角色的租用戶系統管理員，才能登入此入口網站。 若要存取管理主控台，您的帳戶必須擁有使用 Intune 的授權，且登入狀態必須為 [已允許]。
