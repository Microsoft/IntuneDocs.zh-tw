---
title: "透過清查了解您的裝置"
description: "使用 Intune 以檢視有關您所管理之裝置的硬體資訊。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 2d2acab722c0a1f0c5757f6bbe75687cd8416485
ms.contentlocale: zh-tw
ms.lasthandoff: 06/08/2017


---

# <a name="understand-your-devices-with-inventory-in-microsoft-intune"></a>在 Microsoft Intune 透過清查了解您的裝置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 可讓您檢視已註冊裝置以及執行 Intune 用戶端軟體的 Windows 電腦。
Intune 通常會每 7 天收集一次受管理裝置的清查。 基於此原因，報表可能會延遲顯示任何最近的裝置變更結果，例如變更裝置名稱或可用的儲存空間。

## <a name="whats-collected-from-enrolled-devices"></a>從已註冊裝置收集的內容
若要檢視行動裝置所收集的清查，請執行[行動裝置清查報表](understand-microsoft-intune-operations-by-using-reports.md)。 Intune 會從註冊的裝置收集下列清查：

|屬性|收集依據|
|------------|-----------------------|
|**Name**|All 裝置|
|**作業系統**|All 裝置|
|**製造商**|All 裝置|
|**型號**|All 裝置|
|**管理通道**|All 裝置|
|**AAD 已登錄**|Mac OS X 以外的所有裝置|
|**相容性**|All 裝置|
|**EAS 已啟用**|Mac OS X 以外的所有裝置|
|**EAS 啟用識別碼**|Mac OS X 以外的所有裝置|
|**EAS 啟用時間**|Mac OS X 以外的所有裝置|
|**管理狀態**|All 裝置|
|**電子郵件地址**|All 裝置|
|**Exchange ActiveSync 識別碼**|All 裝置|
|**越獄或刷機**|僅限 iOS 和 Android 裝置|
|**唯一的裝置識別碼**|Exchange ActiveSync 以外的所有裝置|
|**序號**|iOS、Mac OS X、Android、Windows 8.1，以及 Windows 10 Desktop 裝置|
|**總儲存空間**|iOS、Mac OS X、Windows 8.1，以及 Windows 10 Desktop 和 Mobile 裝置|
|**可用儲存空間**|iOS、Mac OS X、Windows 8.1，以及 Windows 10 Desktop 裝置|
|**電話號碼**<br>分類為公司的電話現在會利用其完整電話號碼加以識別 (例如，當您執行行動裝置清查報表時)。 BYOD 電話號碼會以 &#42; 遮罩，且僅顯示最後 4 位數。|iOS、Android 和 Windows Phone 裝置|
|**IMEI**|Exchange ActiveSync、iOS、Android 和 Windows Phone 裝置|
|**MEID**<br>行動設備識別碼|僅限 iOS 裝置|
|**Wi-Fi MAC**|Exchange ActiveSync 以外的所有裝置|
|**用戶載波**|僅限 iOS 和 Android 裝置|
|**行動電話通訊技術**|僅限 iOS 和 Android 裝置|
|**受監督**|僅限 iOS 裝置|
|**啟用鎖定狀態**|僅限 iOS 裝置|
|**註冊日期**|All 裝置|
|**上次更新**。|All 裝置|
|**乙太網路 MAC**|僅限 Mac OS X 裝置|
|**啟用鎖定已啟用**|僅限 iOS 裝置|
|**加密已啟用**|All 裝置|

## <a name="whats-collected-from-windows-pcs"></a>從 Windows 電腦收集了什麼？
> [!IMPORTANT]
> 本節僅適用於執行 Intune Windows 電腦用戶端軟體。

若要檢視 Windows 電腦所收集的清查，請執行[電腦清查報表](understand-microsoft-intune-operations-by-using-reports.md)。 Intune 會從 Windows 電腦收集下列清查：

-   **Name**

-   **底座類型**

-   **製造商**

-   **型號**

-   **作業系統**

-   **TPM 版本**

-   **磁碟空間總計**

-   **已使用磁碟空間**

-   **可用磁碟空間**

-   **作業系統磁碟名稱**

-   **作業系統磁碟空間**

-   **作業系統磁碟可用空間**

-   **實體記憶體**

-   **處理器名稱**

-   **處理器架構**

-   **CPU 速度**

-   **IP 位址**

-   **序號**

-   **上次登入使用者**

-   **指派的使用者**

-   **上次更新**。

<!-- this section below belongs in the planning journey
### See Also
[Monitoring and reports with Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
-->

