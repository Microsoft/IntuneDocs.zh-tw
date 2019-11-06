---
title: Microsoft Intune 支援的作業系統和瀏覽器
titleSuffix: ''
description: 列出 Intune 裝置管理所支援的裝置平台及瀏覽器
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b58cbd0aa07babd36c7a7e5aa3dcc5b8d32d58a
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415047"
---
# <a name="supported-operating-systems-and-browsers-in-intune"></a>Intune 中支援的作業系統與瀏覽器

設定 Microsoft Intune 之前，請先檢閱支援的作業系統和瀏覽器。

如需在裝置上安裝 Intune 方面的協助，請參閱[使用受控裝置完成工作](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions)和 [Intune 網路頻寬用量](network-bandwidth-use.md)。

如需設定服務提供者支援的詳細資訊，請瀏覽[設定服務提供者參考](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) \(英文\)。

## <a name="intune-supported-operating-systems"></a>Intune 支援的作業系統

您可以管理執行下列作業系統的裝置：

[!INCLUDE [mdm-supported-devices](../includes/mdm-supported-devices.md)]

### <a name="supported-samsung-knox-standard-devices"></a>支援的 Samsung Knox Standard 裝置

若要避免導致 MDM 註冊失敗的 Knox 啟用錯誤，公司入口網站應用程式僅會在 MDM 註冊期間嘗試啟用 Samsung Knox (若[支援的 Knox 裝置清單](https://www.samsungknox.com/knox-supported-devices/knox-workspace) 中包含該裝置的話)。 如果裝置不支援 Samsung Knox 啟用，則會註冊為標準 Android 裝置。 相同 Samsung 裝置的某些型號可能支援 Knox，而其他則不支援。 在您購買及部署 Samsung 裝置之前，請先跟裝置轉銷商確認 Knox 相容性。

> [!NOTE]
> 註冊 Samsung Knox 裝置可能會需要[啟用針對 Samsung 伺服器的存取](https://support.samsungknox.com/hc/articles/115013833108-Our-corporate-devices-are-behind-a-firewall-How-do-I-enable-Knox-Workspace-devices-to-contact-Samsung-servers) \(英文\)。

下列 Samsung 裝置型號清單不支援 Knox。 適用於 Android 的公司入口網站應用程式會將它們註冊為原生 Android 裝置：

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

### <a name="windows-pc-software-client"></a>Windows 電腦軟體用戶端

[Intune 軟體用戶端](manage-windows-pcs-with-microsoft-intune.md)可以部署並安裝在 Windows 電腦上當作替代的註冊方法。 只有使用 Intune 傳統入口網站時才提供這項功能。 您可以使用 Intune 軟體用戶端來管理 Windows 7 與更新版的電腦 (除了 Windows 10 家用版以外)。

> [!Note]
> Microsoft 宣告 Windows 7 支援將於 2020 年 1 月 14 日結束。 在這一天，Intune 也會淘汰執行 Windows 7 的裝置支援。
>
> 如需詳細資訊，請參閱 [Intune 規劃變更：即將結束對 Windows 7 的支援](https://docs.microsoft.com/intune/fundamentals/whats-new#intune-plan-for-change-nearing-end-of-support-for-windows-7)
>
> Microsoft Intune 將在 2020 年 10 月 15 日淘汰對 Silverlight 型 Intune 主控台的支援。 此淘汰包括結束支援 Silverlight 主控台設定的電腦軟體用戶端 (也稱為「電腦代理程式」)
>
> 如需詳細資訊，請參閱 [Microsoft Intune 終止支援 Silverlight 型系統管理主控台](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Take-Action-Microsoft-Intune-ending-support-for-the-Silverlight/ba-p/916249) \(英文\)

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](../enrollment/device-enrollment.md#mobile-device-management-with-exchange-activesync-and-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Intune 支援網頁瀏覽器

執行不同的系統管理工作時，您必須使用下列其中一個系統管理網站。

- [Microsoft 365 系統管理中心](https://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Azure 入口網站](https://portal.azure.com/)

以下是這些入口網站支援的瀏覽器：

- Microsoft Edge (最新版本)
- Microsoft Internet Explorer 11
- Safari (最新版本，僅限 Mac)
- Chrome (最新版本)
- Firefox (最新版本)

### <a name="intune-classic-portal"></a>Intune 傳統入口網站

Intune 傳統入口網站僅用於管理已向 Intune 電腦軟體用戶端註冊的裝置 (https://manage.microsoft.com) )。 Intune 傳統入口網站需要 Silverlight 瀏覽器支援。

下列 Silverlight 瀏覽器支援 Intune 主控台：

- Internet Explorer 10 或更新版本
- Google Chrome (42 版之前的版本)
- 已啟用 Silverlight 的 Mozilla Firefox (早於 56 版的版本)

> [!Note]
> 因為 Microsoft Edge 和行動瀏覽器不支援 [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx) \(英文\)，所以 Intune 傳統入口網站不予支援。

唯有具有服務系統管理員權限的使用者，或是具有全域系統管理員角色的租用戶系統管理員，才能登入此入口網站。 若要存取管理主控台，您的帳戶必須擁有使用 Intune 的授權，且登入狀態必須為 [已允許]  。
