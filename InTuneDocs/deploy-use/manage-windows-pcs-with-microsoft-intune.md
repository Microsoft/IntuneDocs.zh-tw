---
title: "使用用戶端軟體管理電腦 | Microsoft Docs"
description: "安裝 Intune 用戶端軟體管理 Windows 電腦。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: c66226b7fc31f91669c4f4f0693ccbd7c679189f
ms.openlocfilehash: 74f2848dcd2863022dac44cf302b330a99cf1a55
ms.lasthandoff: 03/29/2017


---

# <a name="manage-windows-pcs-with-intune-pc-client-software"></a>使用 Intune 電腦用戶端軟體管理 Windows 電腦
[將 Windows 電腦註冊為行動裝置](set-up-windows-device-management-with-microsoft-intune.md)是將 Windows 電腦註冊到 Intune 的慣用方法，但身為 IT 系統管理員，您也可以選擇透過安裝 Intune 用戶端軟體來註冊和管理 Windows 電腦 (如本主題中所述)。 作為行動裝置註冊的方式不支援 Intune 軟體用戶端。

Intune 使用原則來管理 Windows 電腦，其管理方式類似 Windows Server Active Directory 網域服務 (AD DS) 群組原則物件 (GPO)。 如果您想要使用 Intune 來管理已加入 Active Directory 網域的電腦，請[確定 Intune 原則不會與組織中任何現有的 GPO 衝突](resolve-gpo-and-microsoft-intune-policy-conflicts.md)。 您可以深入了解 [Gpo](https://technet.microsoft.com/library/hh147307.aspx)。

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>Intune 軟體用戶端的原則和應用程式部署

雖然 Intune 用戶端軟體透過管理軟體更新、Windows 防火牆和 Endpoint Protection 支援[協助保護電腦的管理功能](policies-to-protect-windows-pcs-in-microsoft-intune.md)，但使用 Intune 用戶端軟體管理的電腦無法作為其他 Intune 原則的目標，包括那些專用於行動裝置管理的 **Windows** 原則設定。

當您使用 Intune 用戶端軟體管理 Windows 電腦時，可以只使用 [電腦管理] 區段下的原則。

  ![為新的 Windows 電腦原則選取範本](../media/select-template-for-pc-policy.png)

如需您可以設定之原則的詳細說明，請參閱︰

- [使用原則協助保護執行 Intune 用戶端軟體的 Windows 電腦](https://docs.microsoft.com/intune/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)
- [利用 Microsoft Intune 讓 Windows 電腦的軟體更新保持在最新狀態](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)
- [在 Microsoft Intune 中使用 Windows 防火牆原則協助保護 Windows 電腦](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)
- [使用 Microsoft Intune 的 Endpoint Protection 協助保護 Windows 電腦](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

此外在部署應用程式時，可以只使用 Windows Installer (.exe、.msi)。

  ![選取用戶端軟體檔案的平台及位置](../media/select-platform-of-software-files-for-pc-agent.png)

> [!NOTE]
> 您可以使用 Intune 用戶端軟體將 Windows 8.1 或更新版本的裝置作為電腦管理，或使用行動裝置管理 (MDM) 功能將其作為行動裝置管理。 因為這兩種方法無法同時並用，所以在決定使用 Intune 用戶端軟體管理電腦之前，請詳加考慮。 本主題僅適用於執行 Intune 用戶端軟體來管理電腦電腦。

## <a name="requirements-for-intune-pc-client-management"></a>Intune 電腦用戶端管理的需求

**硬體：**以下列出安裝 Intune 用戶端軟體的最低硬體需求：

|需求|詳細資訊|
|---------------|--------------------|
|網路|用戶端要求電腦必須具有網際網路連線。|
|處理器和記憶體|請參考電腦作業系統的處理器和 RAM 需求。|
|磁碟空間|安裝用戶端軟體之前需有 200 MB 的可用磁碟空間。|

**軟體**：下列是安裝用戶端軟體的軟體需求：

|需求|詳細資訊|
|---------------|--------------------|
|作業系統 | 執行 Windows Vista 或更新版本的 Windows 裝置。 </br></br>**不支援家用版本。**|
|系統管理權限|安裝用戶端軟體的帳戶必須擁有該裝置的本機系統管理員權限。|
|Windows Installer 3.1|電腦至少必須有 Windows Installer 3.1。<br /><br />若要檢視電腦上的 Windows Installer 版本：<br /><br />  在電腦上，以滑鼠右鍵按一下 **%windir%\System32\msiexec.exe**，然後按一下 [內容]。<br /><br />您可以從 Microsoft Developer Network (MSDN) 網站上的 [Windows Installer Redistributables (Windows Installer 可轉散發套件)](http://go.microsoft.com/fwlink/?LinkID=234258) 下載最新版的 Windows Installer。|
|移除不相容的用戶端軟體|安裝 Intune 用戶端軟體之前，請從該電腦解除安裝任何 Configuration Manager、Operations Manager、Operations Management Suite 和 Service Manager 用戶端軟體。|

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>Intune 用戶端軟體的電腦管理功能

安裝 Intune 用戶端軟體之後，管理功能包含：

- [應用程式管理](deploy-apps-in-microsoft-intune.md)

- [即時監視和 Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) - Endpoint Protection 即是 Windows Defender。 Endpoint Protection 適用於 Windows 7 與 Windows 8。 對於 Windows 10 及更新版本，此產品名稱已變更為 Windows Defender。

- [Windows 防火牆設定管理](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)、硬體和軟體清查、遠端控制 (透過遠端協助要求)

- [軟體更新設定](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)

- 相容性設定報告

在 Intune 系統管理主控台中，某些區段只在您使用 Intune 用戶端軟體註冊裝置之後才會出現，例如 [更新]、[保護] 及 [授權]。

  ![只有電腦用戶端才會出現的系統管理主控台項目](../media/admin-console-settings-only-for-pc-agent.png)

您也可以使用 Intune 系統管理主控台在安裝此用戶端的 Windows 電腦上，執行其他一般電腦管理工作︰

-   檢視有關受管理電腦的硬體和軟體清查資訊
-   從遠端重新啟動電腦
-   淘汰電腦以解除安裝用戶端軟體，並從 Intune 的管理中移除
-   將使用者連結到特定的受管理電腦
-   回應遠端協助要求

如需上述工作的詳細資訊，請參閱[一般電腦管理工作](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)。

## <a name="management-limitations-of-the-intune-client-software"></a>Intune 用戶端軟體的管理限制

有一些可以用於將電腦視為行動裝置加以管理的管理選項，無法在 Intune 用戶端軟體所管理的電腦上使用︰

-   完整抹除 (可使用選擇性抹除)

-   條件式存取

## <a name="help-with-troubleshooting"></a>協助疑難排解問題

Intune 用戶端軟體通常是在背景中以無訊息模式執行，不需要太多使用者互動或疑難排解。 如需要解決電腦管理問題，可以查看記錄檔。 Intune 用戶端軟體和對應的記錄會安裝在 %Program Files%\Microsoft\OnlineManagement 目錄下。

您也可以檢閱[Microsoft Intune 的用戶端設定疑難排解](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune)，查看可能會發生的問題，以及有無任何解決方法或因應措施。

