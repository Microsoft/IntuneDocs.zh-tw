---
title: JAMF Pro 傳送至 Intune 的資料
titleSuffix: Microsoft Intune
description: 當您整合 Jamf Pro 以使用 Intune 管理 Mac 時，請檢閱 Jamf Pro 傳送給 Microsoft Intune 的資料清單。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4bf6df44335f3375d58d3c2c11da7cb3f982b3e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502412"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Jamf Pro 傳送至 Intune 的資料

當您搭配 Intune 使用 [Jamf Pro](https://www.jamf.com) 來管理終端使用者的 Mac 時，Jamf Pro 會擷取受控 macOS 裝置的清查資訊。 

## <a name="data"></a>資料  
如需 Jamf Pro 與 Intune 所共用資料的清單，請參閱 Jamf Pro 技術文件中的[附錄：與 Microsoft Intune 共用的清查資訊](https://docs.jamf.com/technical-papers/jamf-pro/microsoft-intune/10.9.0/Appendix__Inventory_Information_Shared_with_Microsoft_Intune.html) \(英文\)。 

<!--  
Jamf Pro reports the following information to Intune:  

* Device Azure AD ID
* JAMF Inventory State (inventory state of a computer checked in with Jamf Pro within the last 24 hours)
* OS Version
* User Azure AD ID
* Encrypted (FileVault 2)
* Gatekeeper Status
* Password: minimum number of character sets
* Password expiration (days)
* Password Type - simple, alphanumeric, or unknown
* Prevent Auto Login
* Required Passcode Length
* Password: number of previous passwords to prevent reuse
* System Integrity Protection
* Last Check-In Time
* Architecture Type
* Available RAM Slots
* Battery Capacity
* Boot ROM
* Bus Speed
* Cache Size
* Device Name
* Domain Join
* Jamf ID
* MAC address
* Make
* Model
* Model Identifier
* NIC Speed
* Number of Cores
* Number of Processors
* OS
* Platform
* Processor Speed
* Processor Type
* Secondary MAC Address
* Serial Number
* SMC Version
* Total RAM
* UDID
* User Email
--> 

<!-- 
You can remove a Jamf-managed device from the Intune console by selecting **Delete** in the **All devices** view. Bulk device deletion can be enabled by selecting multiple devices and clicking **Delete**.
-->

## <a name="next-steps"></a>後續步驟
在 Jamf Pro 文件中取得如何[移除 Jamf 受控裝置](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)的相關資訊。您也可以透過 [Jamf 支援](https://www.jamf.com/support/)提出支援票證，以取得其他支援。 

