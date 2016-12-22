---
title: "支援的行動裝置和瀏覽器 | Microsoft Intune"
description: "列出支援執行 Intune 的裝置和瀏覽器"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/01/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aeeccfa4-0f14-447e-a3df-c8435c8a4bb2
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: b0eab195c00aae4b593fff535179a1b993c36dde


---

# <a name="supported-devices-and-web-browsers-for-intune"></a>Intune 支援的裝置和網頁瀏覽器

身為 Intune 系統管理員，您可以從網頁瀏覽器管理各種裝置。 本主題提供：

- [支援的裝置平台清單](#intune-supported-devices)
- [支援使用 Intune 的網頁瀏覽器清單](#intune-supported-web-browsers)

## <a name="intune-supported-devices"></a>支援 Intune 的裝置

您可以使用 Intune 行動裝置管理來管理下列裝置：

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

Intune 無法用於管理 Windows Server 作業系統。

Intune 裝置管理提供[這些功能](mobile-device-management-capabilities-in-microsoft-intune.md)。

### <a name="windows-pc-software-client"></a>Windows 電腦軟體用戶端

[Intune 軟體用戶端](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune)可以部署並安裝在 Windows 電腦上當作替代的註冊方法。 您可以使用 Intune 軟體用戶端來管理 Windows 7 與更新版的電腦 (除了 Windows 10 家用版以外)。 使用用戶端軟體管理電腦可提供[這些功能](windows-pc-management-capabilities-in-microsoft-intune.md)。

### <a name="exchange-activesync-management"></a>Exchange ActiveSync 管理

您可以從 Intune 主控台管理 [Exchange ActiveSync 裝置](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)。 相較於其他方法，此選項僅提供一組有限的管理功能。 如需支援裝置的清單，請參閱 [Office 365 中內建的行動裝置管理功能](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0)。

## <a name="intune-supported-web-browsers"></a>Intune 支援網頁瀏覽器

執行不同的系統管理工作時，您必須使用下列其中一個系統管理網站。

- [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Microsoft Intune 系統管理員主控台](https://admin.manage.microsoft.com/)

|Intune 功能 |支援的瀏覽器|
|---------|---------|
|**Intune 管理主控台**     |  Internet Explorer 10 或更新版本<br /><br />Google Chrome (42 版之前的版本)<br /><br />啟用 Silverlight 的 Mozilla Firefox<br />**注意：**Mozilla 將移除對 Silverlight 的支援並於 2017 年 3 月生效。 [深入了解](https://go.microsoft.com/fwlink/?linkid=836872)。 |
|**Office 365 管理入口網站**     |所有瀏覽器，包括行動瀏覽器及受管理的瀏覽器  |
|**公司入口網站**     |**在行動裝置上︰**使用每個受支援平台的預設網頁瀏覽器   <br /><br />**在 Windows 電腦上：**Internet Explorer 10 或更新版本，或者 Microsoft Edge<br /><br />**在 Mac OS X 10.9 或更新版本上︰**Apple Safari    |

> [!Note]
> 因為 Microsoft Edge 和行動瀏覽器不支援 [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx)，所以系統管理員主控台不予支援。 Intune 主控台在一段時間之後會從 Silverlight 經驗移動；最後，所有 Intune 的行動裝置和應用程式管理功能都可以在[新的 Microsoft Azure 入口網站中使用](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/)。


唯有具有服務系統管理員權限的使用者，或是具有全域系統管理員角色的租用戶系統管理員，才能登入此入口網站。 若要存取管理主控台，您的帳戶必須擁有使用 Intune 的授權，且登入狀態必須為 [已允許]。
>[!div class="step-by-step"]

>[&larr; **必要條件**](what-to-know-before-you-start-microsoft-intune.md)     [**網路** &rarr;](network-bandwidth-use.md)  



<!--HONumber=Dec16_HO2-->


