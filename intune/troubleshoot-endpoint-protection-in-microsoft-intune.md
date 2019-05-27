---
title: 在 Intune 中針對端點保護進行疑難排解 - Azure | Microsoft Docs
description: 在使用 Microsoft Intune Endpoint Protection 的同時解決問題。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: ec655a53018c2e45d1cb771c1ce9c0aad376b2b1
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66040161"
---
# <a name="troubleshoot-endpoint-protection-in-intune"></a>Intune 中的 Endpoint Protection 問題疑難排解

請在使用 Endpoint Protection 時利用資訊協助解決問題。 您也可以[使用 Windows Defender AV 檢閱事件記錄檔和錯誤碼進行問題疑難排解](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus)。

如果這項資訊對您沒有幫助，您也可以[取得 Microsoft Intune 支援](get-support.md)。

### <a name="error-messages"></a>錯誤訊息
本節針對下列錯誤與警告，說明可能的原因及解決方案。

|狀態項目|可能原因|可能的解決方案|
|---------------|--------------------|-----------------------|
|**Endpoint Protection 引擎無法使用**|Intune Endpoint Protection 引擎已損毀或刪除。|如果 Intune Endpoint Protection 引擎損毀，您可以嘗試更新或重新安裝軟體。<br /><br />若要強制立即更新，請在 Endpoint Protection 用戶端軟體中選擇 **[更新]** (可以在受管理電腦上的工作列中找到)。<br /><br />如果無法更新引擎，您必須重新安裝 Endpoint Protection 引擎。<br /><br />在受管理電腦上的 [控制台] 中，於已安裝的程式清單中，尋找 [Microsoft Intune Endpoint Protection 代理程式]，然後解除安裝該應用程式。<br /><br />下一次更新同步處理期間，Microsoft Online Management 更新管理員將會偵測到程式遺失，並在排定的安裝時間重新安裝它。|
|**已停用 Endpoint Protection**|Intune Endpoint Protection 已由系統管理員 (使用組態設定檔) 或由受管理電腦上的使用者停用。|啟用 Endpoint Protection。 請參閱 Intune 中的[新增 Endpoint Protection 設定](endpoint-protection-configure.md)，或[開啟 Windows Defender 來存取公司資源](/intune-user-help/turn-on-defender-windows)。|
|**已停用即時保護**|即時保護已由系統管理員 (使用設定檔) 或由受管理電腦上的使用者停用。|啟用 Endpoint Protection。 請參閱 Intune 中的 [Windows Defender 防毒軟體](device-restrictions-windows-10.md#windows-defender-antivirus)，或[開啟即時保護來存取公司資源](/intune-user-help/turn-on-defender-windows)。 |
|**已停用下載掃描**|下載掃描已由系統管理員 (使用設定檔) 或由受管理電腦上的使用者停用。|啟用掃描。 請參閱 Intune 中的 [Windows Defender 防毒軟體](device-restrictions-windows-10.md#windows-defender-antivirus)，或[開啟即時保護來存取公司資源](/intune-user-help/turn-on-defender-windows)。 |
|**已停用檔案與程式活動監視**|檔案與程式活動監視已由系統管理員 (使用設定檔) 或由受管理電腦上的使用者停用。|啟用檔案與程式活動。 請參閱 Intune 中的 [Windows Defender 防毒軟體](device-restrictions-windows-10.md#windows-defender-antivirus)，或[開啟即時保護來存取公司資源](/intune-user-help/turn-on-defender-windows)。 |
|**已停用行為監視**|行為監視已由系統管理員 (使用設定檔) 或由受管理電腦上的使用者停用。|啟用行為監視。 請參閱 Intune 中的 [Windows Defender 防毒軟體](device-restrictions-windows-10.md#windows-defender-antivirus)，或[開啟即時保護來存取公司資源](/intune-user-help/turn-on-defender-windows)。 |
|**已停用指令碼掃描**|指令碼掃描已由系統管理員 (使用設定檔) 或由受管理電腦上的使用者停用。|啟用指令碼掃描。 請參閱 Intune 中的 [Windows Defender 防毒軟體](device-restrictions-windows-10.md#windows-defender-antivirus)，或[開啟即時保護來存取公司資源](/intune-user-help/turn-on-defender-windows)。 |
|**已停用網路檢查系統**|網路檢查系統已由系統管理員 (使用設定檔) 或由受管理電腦上的使用者停用。|啟用網路檢查系統 (NIS)。 請參閱 Intune 中的 [Windows Defender 防毒軟體](device-restrictions-windows-10.md#windows-defender-antivirus)，或[開啟即時保護來存取公司資源](/intune-user-help/turn-on-defender-windows)。 |
|**惡意程式碼定義已過期**|電腦可能長時間中斷網際網路連線，且其惡意程式碼定義可能尚未更新。 當電腦上的惡意程式碼定義過期達 14 天以上時，就會出現此狀態。|如果惡意程式碼定義已過期，您可以使用 [Windows Defender 防毒軟體](device-restrictions-windows-10.md#windows-defender-antivirus)更新定義。|
|**完整掃描逾期**|完整掃描已完成 14 天。 原因可能是電腦在完整掃描期間重新啟動。|若完整掃描已逾期，您可以執行一次性的完整掃描或排定週期性完整掃描。 請參閱 [Windows Defender 防毒軟體](device-restrictions-windows-10.md#windows-defender-antivirus)。 |
|**快速掃描逾期**|已有 14 天完成未完成快速掃描。 原因可能是在快速掃描期間重新啟動。|若快速掃描已逾期，您可以執行一次性的快速掃描或排定週期性快速掃描。 請參閱 [Windows Defender 防毒軟體](device-restrictions-windows-10.md#windows-defender-antivirus)。|
|**其他 Endpoint Protection 應用程式正在執行**|其他 Endpoint Protection 應用程式正在執行且電腦狀況良好。|根據預設，如果已安裝其他 Endpoint Protection 應用程式，且 Intune 偵測到該應用程式，裝置可能會變得不穩定。|

### <a name="next-steps"></a>後續步驟
如果這項資訊對您沒有幫助，您也可以[取得 Microsoft Intune 支援](get-support.md)。
