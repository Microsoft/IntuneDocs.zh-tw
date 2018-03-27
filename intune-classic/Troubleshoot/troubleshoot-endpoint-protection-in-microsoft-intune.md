---
title: Endpoint Protection 疑難排解
description: 在使用 Microsoft Intune Endpoint Protection 的同時解決問題。
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 01/31/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: edfc9e4995610aaadfd12e8370a42bfcc15032e6
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="troubleshoot-endpoint-protection-in-microsoft-intune"></a>Troubleshoot Endpoint Protection in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

請使用本節中的資訊，協助您解決使用 Microsoft Intune Endpoint Protection 時的問題。 您也可以檢閱有關如何[對 Windows 10 中的 Windows Defender 進行疑難排解](https://technet.microsoft.com/itpro/windows/keep-secure/troubleshoot-windows-defender-in-windows-10)的資訊。

如果此資訊無法解決您的問題，請參閱[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)，以尋找更多方法來取得協助。

### <a name="endpoint-protection-error-messages"></a>Endpoint Protection 錯誤訊息
本節針對出現在 [Intune 管理主控台](https://manage.microsoft.com)的 **[Endpoint Protection 狀態]** 窗格中的下列錯誤與警告，說明可能的原因及解決方案。

|狀態項目|可能原因|可能的解決方案|
|---------------|--------------------|-----------------------|
|**Endpoint Protection 引擎無法使用**|Intune Endpoint Protection 引擎已損毀或刪除。|如果 Intune Endpoint Protection 引擎損毀，您可以嘗試更新或重新安裝軟體。<br /><br />若要強制立即更新，請在 Endpoint Protection 用戶端軟體中選擇 **[更新]** (可以在受管理電腦上的工作列中找到)。<br /><br />如果無法更新引擎，您必須重新安裝 Endpoint Protection 引擎。<br /><br />在受管理電腦上的 [控制台] 中，於已安裝的程式清單中，尋找 [Microsoft Intune Endpoint Protection 代理程式]，然後解除安裝該應用程式。<br /><br />下一次更新同步處理期間，Microsoft Online Management 更新管理員將會偵測到程式遺失，並在排定的安裝時間重新安裝它。|
|**已停用 Endpoint Protection**|Intune Endpoint Protection 已由系統管理員 (使用原則) 或由受管理電腦上的使用者停用。|如果已停用 Endpoint Protection，您可以從 [Intune 管理主控台](https://manage.microsoft.com)或從受管理電腦啟用它。 請執行下列其中一項動作：<br /><br />若要從 [Intune 管理主控台](https://manage.microsoft.com)啟用 Endpoint Protection，請開啟 [原則] 工作區，然後在套用到電腦的原則中變更 [啟用 Endpoint Protection] 設定。<br /><br />或者，<br /><br />若要從受管理電腦啟用 Endpoint Protection，請從通知區域啟動 Intune Endpoint Protection 用戶端，您將會收到啟用 Endpoint Protection 的提示。|
|**已停用即時保護**|即時保護已由系統管理員 (使用原則) 或由受管理電腦上的使用者停用。|如果已停用即時保護，您可以從 [Intune 管理主控台](https://manage.microsoft.com)或從受管理電腦啟用它。 請執行下列其中一項動作：<br /><br />若要從 [Intune 管理主控台](https://manage.microsoft.com)啟用即時保護，請開啟 [原則] 工作區，然後在適用於電腦的原則中，將 [啟用即時保護] 設定變更為 [是]。<br /><br />或者，<br /><br />若要從受管理電腦啟用即時保護，請從通知區域啟動 Endpoint Protection 用戶端軟體。 這時系統將會提示您啟用即時保護。|
|**已停用下載掃描**|下載掃描已由系統管理員使用原則加以停用，或由受管理電腦上的使用者停用。|如果已停用下載掃描，您可以從 [Intune 管理主控台](https://manage.microsoft.com)或從受管理電腦啟用它。 請執行下列其中一項動作：<br /><br />若要從 [Intune 管理主控台](https://manage.microsoft.com)啟用下載掃描，請開啟 [原則] 工作區，然後在適用於電腦的原則中，將 [掃描所有下載] 設定變更為 [是]。<br /><br />或者，<br /><br />若要從受管理電腦啟用下載掃描，請從通知區域啟動 Endpoint Protection 用戶端軟體。 依序選擇 **[設定]** 索引標籤和 **[即時保護]**，並選取 **[掃描所有下載]** 核取方塊，然後選擇 **[儲存變更]**。|
|**已停用檔案與程式活動監視**|檔案與程式活動監視已由使用原則的系統管理員或由受管理電腦上的使用者停用。|如果已停用檔案與程式活動監視，您可以從 [Intune 管理主控台](https://manage.microsoft.com)或從受管理電腦啟用它。 請執行下列其中一項動作：<br /><br />若要從 [Intune 管理主控台](https://manage.microsoft.com)啟用檔案與程式活動監視，請開啟 [原則] 工作區，然後在套用到電腦的原則中，將 [監視電腦上的檔案和程式活動] 設定變更為 [是]。<br /><br />或者，<br /><br />若要從受管理電腦啟用檔案與程式活動監視，請從通知區域啟動 Endpoint Protection 用戶端軟體。 依序選擇 **[設定]** 索引標籤和 **[即時保護]**，並選取 **[監視您電腦上的檔案及程式活動]** 核取方塊，然後選擇 **[儲存變更]**。|
|**已停用行為監視**|行為監視已系統管理員 (使用原則) 或由受管理電腦上的使用者停用。|如果已停用行為監視，您可以從 [Intune 管理主控台](https://manage.microsoft.com)或從受管理電腦啟用它。 請執行下列其中一項動作：<br /><br />若要從 [Intune 管理主控台](https://manage.microsoft.com)啟用行為監視，請開啟 [原則] 工作區，然後在套用到電腦的原則中，將 [啟用行為監視] 設定變更為 [是]，然後重新啟動受管理的電腦。<br /><br />或者，<br /><br />若要從受管理電腦啟用行為監視，請從通知區域啟動 Endpoint Protection 用戶端軟體。 依序選擇 **[設定]** 索引標籤和 **[即時保護]**，並選取 **[啟用行為監視]** 核取方塊，然後選擇 **[儲存變更]**。 接著再重新啟動電腦。|
|**已停用指令碼掃描**|指令碼掃描已由系統管理員 (使用原則) 或由受管理電腦上的使用者停用。|如果已停用指令碼掃描，您可以從 [Intune 管理主控台](https://manage.microsoft.com)或從受管理電腦啟用它。 請執行下列其中一項動作：<br /><br />若要從 [Intune 管理主控台](https://manage.microsoft.com)啟用指令碼掃描，請開啟 [原則] 工作區，然後在套用到電腦的原則中，將 [啟用指令碼掃描] 設定變更為 [是]。<br /><br />或者，<br /><br />若要從受管理電腦啟用指令碼掃描，請從通知區域啟動 Endpoint Protection 用戶端軟體。 依序選擇 **[設定]** 索引標籤和 **[即時保護]**，並選取 **[啟用指令碼掃描]** 核取方塊，然後選擇 **[儲存變更]**。|
|**已停用網路檢查系統**|網路檢查系統已由系統管理員使用原則加以停用，或由受管理電腦上的使用者加以停用。|如果已停用網路檢查系統，您可以從 [Intune 管理主控台](https://manage.microsoft.com)或從受管理電腦啟用它。 請執行下列其中一項動作：<br /><br />若要從 [Intune 管理主控台](https://manage.microsoft.com)啟用網路檢查系統，請開啟 [原則] 工作區，然後在套用到電腦的原則中，將 [啟用網路檢查系統] 設定變更為 [是]，然後重新啟動受管理的電腦。<br /><br />或者，<br /><br />若要從受管理電腦啟用網路檢查系統，請從通知區域啟動 Endpoint Protection 用戶端軟體。 依序選擇 **[設定]** 索引標籤和 **[即時保護]**，並選取 **[啟用網路檢查系統]** 核取方塊，然後選擇 **[儲存變更]**。 重新啟動電腦。|
|**惡意程式碼定義已過期**|電腦可能長時間中斷網際網路連線，且其惡意程式碼定義可能尚未更新。 當電腦上的惡意程式碼定義過期達 14 天以上時，就會出現此狀態。|如果惡意程式碼定義已過期，您可以從 [Intune 管理主控台](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)主題更新定義。|
|**完整掃描逾期**|完整掃描已完成 14 天。 原因可能是電腦在完整掃描期間重新啟動。|若完整掃描已逾期，您可以執行一次性的完整掃描，或從 [Intune 管理主控台](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)排定週期性完整掃描。|
|**快速掃描逾期**|已有 14 天完成未完成快速掃描。 原因可能是在快速掃描期間重新啟動。|若快速掃描已逾期，您可以執行一次性的快速掃描，或從 [Intune 管理主控台](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)排定週期性快速掃描。|
|**其他 Endpoint Protection 應用程式正在執行**|其他 Endpoint Protection 應用程式正在執行且電腦狀況良好。|根據預設，如果已安裝其他 Endpoint Protection 應用程式，且 Intune 偵測到該應用程式，Endpoint Protection 將會自動停用。 如果 Intune 偵測不到其他 Endpoint Protection 應用程式，Endpoint Protection 將保持啟用。 如需詳細資訊，請參閱[使用 Microsoft Intune 的 Endpoint Protection 協助保護 Windows 電腦](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)。|

### <a name="next-steps"></a>接下來的步驟
如果此疑難排解資訊對您沒有幫助，請連絡 Microsoft 支援服務 (如[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)中所述)。
