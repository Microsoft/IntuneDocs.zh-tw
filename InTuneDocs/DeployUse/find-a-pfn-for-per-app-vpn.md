---
title: "尋找每個應用程式 VPN 的套件系列名稱 (PFN) | Microsoft Intune"
description: "找到 PFN，以讓您設定每個應用程式 VPN。"
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 74643d1d-4fd9-4cff-ac79-1a42281d2f76
ms.reviewer: tycast
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7b16c19c95384655e170c199597dd6bd31afb90d
ms.openlocfilehash: 026bb4c8bf90bbe1af93513df46f0ec21f82509b


---

# 尋找每個應用程式 VPN 設定的套件系列名稱 (PFN)

有兩種方式可找到 PFN，以讓您設定每個應用程式 VPN。

## 找到 Windows 10 電腦上已安裝應用程式的 PFN

如果您正在使用的應用程式已經安裝在 Windows 10 電腦上，則可以使用 [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) PowerShell Cmdlet 來取得 PFN。

Get-AppxPackage 的語法如下︰

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> 注意︰您可能必須以系統管理員身分執行 PowerShell，才能擷取 PFN。

例如，若要取得電腦上安裝之所有通用應用程式的資訊，請使用 `Get-AppxPackage`。

若要取得您知道名稱或局部名稱之應用程式的資訊，請使用 `Get-AppxPackage *<app_name>`。 請注意萬用字元的使用，如果您不確定應用程式的完整名稱，則這特別有用。 例如，若要取得 OneNote 的資訊，請使用 `Get-AppxPackage *OneNote`。


以下是針對 OneNote 所擷取的資訊︰

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## 如果電腦上未安裝應用程式，請尋找 PFN。

1.  移至 https://www.microsoft.com/en-us/store/apps
2.  在搜尋列中輸入應用程式的名稱。 在這個範例中，搜尋 OneNote。
3.  按一下應用程式的連結。 請注意，您所存取之 URL 的結尾會有一系列的字母。 在這個範例中，URL 看起來如下︰
`https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`
4.  在不同的索引標籤中，貼上下列 URL：`https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`，並將 `<app id>` 取代為您從 https://www.microsoft.com/en-us/store/apps 取得的應用程式識別碼 - 步驟 3 中 URL 結尾的那一系列字母。 在 OneNote 範例中，您將貼上：`https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`。

在 Edge 中，會顯示您想要的資訊；在 Internet Explorer 中，按一下 [開啟] 以查看資訊。 PFN 值會出現在第一行。 以下是這個範例的結果︰


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`



<!--HONumber=Aug16_HO1-->


