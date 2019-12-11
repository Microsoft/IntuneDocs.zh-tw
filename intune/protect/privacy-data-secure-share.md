---
title: Intune 中的資料安全性與共用
titleSuffix: Microsoft Intune
description: 了解如何在 Intune 中保護及共用個人資料。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 68921fd6-5f50-456c-a3af-83d7bc4b134b
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b17b87462b2c73e265f062c33a06a810e7c58bf8
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504340"
---
# <a name="data-security-and-sharing-in-intune"></a>Intune 中的資料安全性與共用


## <a name="data-security"></a>資料安全性

Microsoft Intune 是 Microsoft Enterprise Mobility 和 Security Suite 雲端服務供應項目的重要元件。 若要支援[資料控管策略](https://www.microsoft.com/en-us/TrustCenter/Security/default.aspx)，所有的 Microsoft 雲端服務都是使用 [Microsoft 隱私權](https://www.microsoft.com/en-us/trustcenter/privacy)和 [Microsoft 安全性](https://www.microsoft.com/en-us/trustcenter/security/)方法進行開發。  

Microsoft Intune 會遵循 Microsoft Azure 服務小組採用的相同技術和組織量值，以防止資料外洩程序。

如需詳細資訊，請參閱[服務信任入口網站](https://www.microsoft.com/en-us/TrustCenter/stp)。

Intune 會使用資料最小化技術，如

- aggregation
- 某些功能的選擇性資料收集
- 資料較不精確或敏感

Intune 也會使用 RBAC 和 JiT 安全性等技術來支援事件，以確保預設的資料保護。 

### <a name="data-breach-reporting"></a>資料外洩報告

識別出客戶可報告安全性事件 (CRSI) 時，客戶會收到通知。 此程序包括與 Microsoft O365 小組合作，使用 Intune 通知任何 Microsoft O365 客戶發生外洩。

## <a name="data-sharing"></a>資料共用

當租用戶管理員開啟特定功能 (例如 Apple 裝置註冊計劃) 時，Microsoft Intune 會取得管理員同意，以便與適當的協力廠商共用資料。 在這種情況下，Intune 可能與下列人員共用個人資料：

- 作為 Microsoft 代理商的協力廠商。
- 不會作為 Microsoft 代理商，但是只有在租用戶管理員明確授與 Intune 權限時才能這樣做的協力廠商。

作為 Microsoft 代理商的所有協力廠商都包含在[線上服務轉包商清單](https://aka.ms/Online_Serv_Subcontractor_List)中。

與這類實體共用資料是為了協助客戶和技術支援人員、服務維護和其他作業。

租用戶與協力廠商簽訂的合約會控管協力廠商服務中保留的 Intune 個人資料。 它也會授與 Intune 傳輸資料到協力廠商服務的權限。  

如需與特定協力廠商共用資料的資訊，請參閱下列文章：
- [Intune 傳送至 Apple 的資料](data-intune-sends-to-apple.md)
- [Intune 傳送至 Google 的資料](data-intune-sends-to-google.md)
- [Apple 傳送至 Intune 的資料](data-apple-sends-to-intune.md)
- [Google 傳送至 Intune 的資料](data-google-sends-to-intune.md)
- [Jamf Pro 傳送至 Intune 的資料](data-jamf-sends-to-intune.md)

### <a name="system-center-configuration-manager-data-sharing"></a>System Center Configuration Manager 資料共用

Microsoft Intune 不會與 System Center Configuration Manager 共用任何資料。 System Center Configuration Manager 是客戶直接部署、管理和操作的內部部署產品。 Configuration Manager 收集的診斷和使用方式資料僅用來改善未來版本的安裝體驗、品質及安全性。

若要進一步了解，請參閱 [SCCM 的診斷和使用方式資料](https://docs.microsoft.com/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data)。 


## <a name="next-steps"></a>後續步驟

了解如何[檢視及更正](privacy-data-view-correct.md) Intune.中的個人資料。
