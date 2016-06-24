---
# required metadata

title: 使用 Intune 管理 Windows 電腦 | Microsoft Intune
description:
keywords:
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 管理 Windows 電腦
除了註冊裝置，您也可以使用 Intune 來管理使用 Intune Windows PC 用戶端軟體執行支援作業系統的 Windows 電腦。 執行電腦用戶端的硬體和軟體需求很低，基本上支援所有能夠執行 Windows 7 或更新版本的系統。  這個用戶端軟體也可輕易安裝在已加入網域的電腦 (任何網域) 或未加入網域的電腦上。

Intune 使用原則來管理 Windows 電腦，其管理方式類似 Windows Server Active Directory 網域服務 (AD DS) 群組原則物件 (GPO)。 如果您想要使用 Intune 來管理已加入 Active Directory 網域的電腦，您應該[確定 Intune 原則不會與組織中任何現有的 GPO 衝突](resolve-gpo-and-microsoft-intune-policy-conflicts.md)。

> [!NOTE]
> Microsoft Intune 以獨立服務的形式提供這些用來管理電腦的功能。 執行 Windows 8.1 的裝置可以使用 Intune 用戶端來管理，或是註冊成行動裝置。 以下資訊適用於執行 Intune 用戶端的電腦。

## Intune 電腦管理的需求

硬體：

|以下列出安裝 Intune 用戶端的最低硬體需求：|需求|
|---------------|--------------------|
|詳細資訊|網路|
|用戶端要求電腦必須具有網際網路連線。|處理器和記憶體|
|請參考電腦作業系統的處理器和 RAM 需求。|磁碟空間|

安裝用戶端軟體之前需有 200 MB 的可用磁碟空間。

|軟體：|以下列出安裝用戶端的最低硬體需求：|
|---------------|--------------------|
|需求|詳細資訊|
|系統管理權限|安裝用戶端軟體的帳戶必須擁有該電腦的本機系統管理員權限。<br /><br />Windows Installer 3.1<br /><br />電腦至少必須有 Windows Installer 3.1。<br /><br />若要檢視電腦上的 Windows Installer 版本：|
|-   在電腦上，在 %windir%\System32\msiexec.exe 上按一下滑鼠右鍵，然後按一下 [內容]|您可以從 Microsoft Developer Network (MSDN) 網站上的 [Windows Installer Redistributables (Windows Installer 可轉散發套件)](http://go.microsoft.com/fwlink/?LinkID=234258) 下載最新版的 Windows Installer。|

## 移除不相容的用戶端軟體
安裝 Intune 用戶端軟體之前，您必須從該電腦解除安裝任何 Configuration Manager 或 System Management Server 用戶端軟體。 安裝 Intune 電腦用戶端

-   使用 Intune 管理 Windows 電腦的第一個步驟是安裝用戶端。 如果電腦已註冊到 Intune 服務的管理，則可以使用下列其中一個方法來安裝用戶端軟體：

    您可以[手動部署 Microsoft Intune 用戶端軟體](install-the-windows-pc-client-with-microsoft-intune.md#to-manually-deploy-the-client-software)。 在這種部署類型中，系統管理員會下載 Intune 用戶端軟體，並在每部電腦上以手動方式進行安裝。

-   若要下載 Intune 用戶端軟體，請開啟 Intune 系統管理主控台，然後在 [用戶端軟體下載] 區域中下載用戶端軟體封裝。

-   安裝用戶端軟體之後，Intune 會視需要自動安裝其他軟體來管理電腦。 您可以使用為了手動安裝 Intune 用戶端所下載的相同檔案，[使用 Active Directory GPO 將用戶端部署到已加入網域的電腦](install-the-windows-pc-client-with-microsoft-intune.md#to-automatically-deploy-the-client-software-by-using-group-policy)

-   [使用者可以透過 Intune 公司入口網站自行註冊每一部電腦](install-the-windows-pc-client-with-microsoft-intune.md#how-users-can-self-enroll-their-computers)。

## 註冊過的每一部電腦會接著自動連結到用來安裝 Intune 用戶端軟體的使用者帳戶。
最後，您也可以在[作業系統部署](install-the-windows-pc-client-with-microsoft-intune.md#install-the-microsoft-intune-client-software-as-part-of-an-image)過程中，將 Intune 用戶端軟體部署到電腦

使用 Intune 電腦用戶端管理電腦

-   安裝 Intune 用戶端之後，用戶端軟體會啟用數項電腦管理功能，包括：[應用程式管理](deploy-apps-in-microsoft-intune.md)、Endpoint Protection、硬體和軟體清查、遠端控制 (透過遠端協助要求)、軟體更新，以及相容性設定報告。

-   電腦用戶端所啟用的數項電腦管理工作會透過 Intune 原則來管理，例如：

-   在受管理電腦上設定 [Windows 防火牆設定](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)。

設定受管理電腦的[軟體更新設定](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)，以檢查並下載必要的軟體更新。

-   透過[即時監視和 Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) 管理，協助保護受管理的電腦，以免受到潛在威脅和惡意軟體的攻擊。

-   除了在個別電腦本機所採取的 Intune 用戶端代理程式動作之外，您也可以使用 Intune 管理主控台，在安裝用戶端的 Windows 電腦上執行其他[一般電腦管理工作](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)，以便：

-   檢視有關受管理電腦的硬體和軟體清查資訊

-   從遠端重新啟動電腦

-   淘汰電腦以解除安裝用戶端軟體，並從 Intune 的管理中移除

將使用者連結到特定的受管理電腦 回應遠端協助要求


<!--HONumber=May16_HO2-->


