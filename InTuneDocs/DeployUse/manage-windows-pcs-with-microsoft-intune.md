---
title: "使用 Intune 用戶端管理 Windows 電腦 | Microsoft Intune"
description: "安裝 Intune 用戶端軟體管理 Windows 電腦。"
keywords: 
author: nathbarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: aa1d6105a5be9c329c75681857a9d6e553088b65
ms.openlocfilehash: be45b2ffb99eb75e71c0d591fc84089b83735905


---

# 使用 Intune 電腦用戶端軟體管理 Windows 電腦
不同於[將 Windows 電腦註冊為行動裝置](set-up-windows-device-management-with-microsoft-intune.md)，您可以透過安裝 Intune 用戶端軟體來管理 Windows 電腦。

Intune 使用原則來管理 Windows 電腦，其管理方式類似 Windows Server Active Directory 網域服務 (AD DS) 群組原則物件 (GPO)。 如果您想要使用 Intune 來管理已加入 Active Directory 網域的電腦，您應該[確定 Intune 原則不會與組織中任何現有的 GPO 衝突](resolve-gpo-and-microsoft-intune-policy-conflicts.md)。

雖然 Intune 用戶端透過管理軟體更新、Windows 防火牆以及 Endpoint Protection 支援[協助保護電腦的原則](policies-to-protect-windows-pcs-in-microsoft-intune.md)，但使用 Intune 用戶端管理的電腦無法做為其他 Intune 原則的目標。

> [!NOTE]
> 執行 Windows 8.1 或更新版本的裝置可以使用 Intune 用戶端來管理，或是註冊成行動裝置。 以下資訊適用於執行 Intune 用戶端的電腦。 不支援安裝 Intune 電腦用戶端與註冊 Windows 裝置進行行動裝置管理。

## Intune 電腦用戶端管理的需求

**硬體：**以下列出安裝 Intune 用戶端的最低硬體需求：

|需求|詳細資訊|
|---------------|--------------------|
|網路|用戶端要求電腦必須具有網際網路連線。|
|處理器和記憶體|請參考電腦作業系統的處理器和 RAM 需求。|
|磁碟空間|安裝用戶端軟體之前需有 200 MB 的可用磁碟空間。|

**軟體**：下表列出安裝用戶端的軟體需求：

|需求|詳細資訊|
|---------------|--------------------|
|作業系統 | 執行 Windows 7 或更新版本的 Windows 裝置。 |
|系統管理權限|安裝用戶端軟體的帳戶必須擁有該裝置的本機系統管理員權限。|
|Windows Installer 3.1|電腦至少必須有 Windows Installer 3.1。<br /><br />若要檢視電腦上的 Windows Installer 版本：<br /><br />-   在電腦上，在 **%windir%\System32\msiexec.exe** 上按一下滑鼠右鍵，然後按一下 [內容]。<br /><br />您可以從 Microsoft Developer Network (MSDN) 網站上的 [Windows Installer Redistributables (Windows Installer 可轉散發套件)](http://go.microsoft.com/fwlink/?LinkID=234258) 下載最新版的 Windows Installer。|
|移除不相容的用戶端軟體|安裝 Intune 用戶端軟體之前，您必須從該電腦解除安裝任何 Configuration Manager 或 System Management Server 用戶端軟體。|

## 安裝 Intune 電腦用戶端
Intune 用戶端軟體可以下列其中一種方式安裝：

-   [手動部署 Microsoft Intune 用戶端軟體](install-the-windows-pc-client-with-microsoft-intune.md#to-manually-deploy-the-client-software)。 在這種部署類型中，系統管理員會下載 Intune 用戶端軟體，並在每部電腦上以手動方式進行安裝。

  若要下載 Intune 用戶端軟體，請開啟 [Intune 管理主控台](https://manage.microsoft.com)並選擇 [管理員] > [用戶端軟體下載]，然後按一下 [下載用戶端軟體]。

-   您可以使用為了手動安裝 Intune 用戶端所下載的相同檔案，[使用 Active Directory GPO 將用戶端部署到已加入網域的電腦](install-the-windows-pc-client-with-microsoft-intune.md#to-automatically-deploy-the-client-software-by-using-group-policy)。

-   最後，您也可以在[作業系統部署](install-the-windows-pc-client-with-microsoft-intune.md#install-the-microsoft-intune-client-software-as-part-of-an-image)過程中，將 Intune 用戶端軟體部署到電腦。

## 使用 Intune 電腦用戶端管理電腦
安裝 Intune 用戶端之後，用戶端軟體會啟用數項電腦管理功能，包括：[應用程式管理](deploy-apps-in-microsoft-intune.md)、Endpoint Protection、硬體和軟體清查、遠端控制 (透過遠端協助要求)、軟體更新，以及相容性設定報告。

電腦用戶端所啟用的數項電腦管理工作會透過 Intune 原則來管理，例如：

-   在受管理電腦上設定 [Windows 防火牆設定](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)。

-   設定受管理電腦的[軟體更新設定](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)，以檢查並下載必要的軟體更新。

-   透過[即時監視和 Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) 管理，協助保護受管理的電腦，以免受到潛在威脅和惡意軟體的攻擊。

除了在個別電腦本機所採取的 Intune 用戶端代理程式動作之外，您也可以使用 Intune 管理主控台，在安裝用戶端的 Windows 電腦上執行其他[一般電腦管理工作](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)，以便：

-   檢視有關受管理電腦的硬體和軟體清查資訊

-   從遠端重新啟動電腦

-   淘汰電腦以解除安裝用戶端軟體，並從 Intune 的管理中移除

-   將使用者連結到特定的受管理電腦

-   回應遠端協助要求

Intune 用戶端代理程式通常是在背景中以無訊息模式執行，不需要太多使用者互動或疑難排解。 不過，如果您需要協助以解決電腦管理問題，有幾個可[協助您解決問題的資源](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune)。



<!--HONumber=Aug16_HO1-->


