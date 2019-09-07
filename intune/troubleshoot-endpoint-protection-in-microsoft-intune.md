---
title: Microsoft Intune 中常見的 Endpoint Protection 訊息 - Azure | Microsoft Docs
description: 查看在 Microsoft Intune 中使用及疑難排解 Endpoint Protection 和 Windows Defender 時的常見訊息與可能的解決方案。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/26/2019
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
ms.openlocfilehash: c76466acb375fe49afefc542606350733970f416
ms.sourcegitcommit: 18be0ccc6e51073af32c44abeba421d69a5ae21a
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302340"
---
# <a name="endpoint-protection-issues-and-possible-solutions-in-microsoft-intune"></a>Microsoft Intune 中的 Endpoint Protection 問題和可能的解決方案

本文將針對一些錯誤與警告列出並說明可能的原因及解決方案。 利用該資訊來協助解決使用 Endpoint Protection 時的問題。

## <a name="windows-defender-error-codes"></a>Windows Defender 錯誤碼

檢閱事件記錄檔和錯誤碼以[使用 Windows Defender AV 來進行問題的疑難排解](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus) \(部分機器翻譯\)。

## <a name="common-intune-errors-and-possible-resolutions"></a>常見的 Intune 錯誤和可能的解決方式

### <a name="endpoint-protection-engine-unavailable"></a>Endpoint Protection 引擎無法使用

**可能的原因**：Intune Endpoint Protection 引擎已損毀或刪除。

**可能的解決方案**：

- 如果 Endpoint Protection 已損毀或將不會更新，則請更新或重新安裝程式。
- 強制立即更新。 在 Endpoint Protection 用戶端程式 (可能位於工作列) 中，選擇 [更新]  。
- 在 [控制台] > [程式] 中，選取 [Microsoft Intune Endpoint Protection 代理程式]  。 解除安裝應用程式。
- 下一次更新同步處理期間，Microsoft Online Management 更新管理員將會偵測到程式遺失，並在排定的安裝時間重新安裝它。

### <a name="features-are-disabled"></a>功能已停用

您可能會收到一則訊息，指出某些功能已停用。 如果系統管理員使用組態設定檔來停用 Intune Endpoint Protection 或 Windows Defender，可能就會產生這些訊息。 或者，終端使用者已在裝置上停用功能。 可能的訊息：

`Endpoint Protection disabled`  
`Real-time protection disabled`  
`Download scanning disabled`  
`File and program activity monitoring disabled`  
`Behavior monitoring disabled`  
`Script scanning disabled`  
`Network Inspection System disabled`  

**可能的解決方案**：啟用這些功能。 如需指引，請參閱：

- [新增 Endpoint Protection 設定](endpoint-protection-configure.md)
- [Windows Defender 防毒軟體](device-restrictions-windows-10.md#microsoft-defender-antivirus)
- [終端使用者：開啟即時保護以存取公司資源](/intune-user-help/turn-on-defender-windows)

### <a name="malware-definitions-out-of-date"></a>惡意程式碼定義已過期

當裝置上的惡意程式碼定義過期達 14 天以上時，就會顯示此狀態。 例如，如果裝置中斷網際網路的連線，或惡意程式碼定義已過時，可能就會顯示此訊息。

**可能的解決方案**：如果惡意程式碼定義已過期，請使用 [Windows Defender 防毒軟體](device-restrictions-windows-10.md#microsoft-defender-antivirus)來更新定義。

### <a name="full-scan-overdue-or-quick-scan-overdue"></a>完整掃描逾期或快速掃描逾期

已有 14 天未曾完成完整掃描或快速掃描。 如果在完整掃描期間重新啟動裝置，就會發生此情況。

**可能的解決方案**：如果掃描已逾期，您可以執行一次性掃描或排程週期性掃描。 請參閱 [Windows Defender 防毒軟體](device-restrictions-windows-10.md#microsoft-defender-antivirus)。

### <a name="another-endpoint-protection-application-running"></a>其他 Endpoint Protection 應用程式正在執行

其他 Endpoint Protection 應用程式正在執行且裝置狀況良好。

**可能的解決方案**：如果已安裝其他 Endpoint Protection 應用程式，且 Intune 偵測到該應用程式，則裝置可能會變得不穩定。

## <a name="next-steps"></a>後續步驟

取得[來自 Microsoft 的支援說明](get-support.md)或使用[社群論壇](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)。
