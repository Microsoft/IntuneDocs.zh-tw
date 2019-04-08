---
title: Windows 電腦的防火牆原則
titleSuffix: Microsoft Intune
description: Intune 有數種方式可協助您保護使用 Intune 用戶端管理的電腦，包括協助您設定 Windows Firewall 防火牆設定。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: b5edcfedcd03492d8634549147b70be14ffb742e
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798870"
---
# <a name="help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune"></a>在 Microsoft Intune 中使用 Windows 防火牆原則協助保護 Windows 電腦

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Microsoft Intune 有數種方式可協助您保護使用 Intune 用戶端管理的 Windows 電腦。 其中一項方式為提供可讓您在電腦上設定 Windows 防火牆設定的原則。

如果您尚未在電腦上安裝 Intune Windows 電腦用戶端，請參閱[使用 Microsoft Intune 安裝 Windows 電腦用戶端](install-the-windows-pc-client-with-microsoft-intune.md)。

使用以下各節中的資訊可協助您設定、部署及監視 Windows 電腦上的 Windows 防火牆原則。

## <a name="use-intune-policies-to-manage-windows-firewall"></a>使用 Intune 原則管理 Windows 防火牆
Windows 防火牆原則可讓您建立及部署在受管理電腦上控制 Windows 防火牆的設定。 您不能管理 Windows 防火牆的自訂例外狀況，且這些設定不會影響協力廠商防火牆。

> [!NOTE]
> 如果設定以 Microsoft Intune 原則及群組原則管理同一台電腦的相同設定，群組原則設定會覆寫 Microsoft Intune 原則設定。 如需如何避免 Intune 原則與群組原則產生衝突的詳細資訊，請參閱[解決 GPO 和 Microsoft Intune 原則衝突](resolve-gpo-and-microsoft-intune-policy-conflicts.md)。
>
> 如果您想將 Windows 防火牆設定部署到執行 Windows Vista 的電腦，則必須先在這些電腦上安裝 [Hotfix KB971800](http://support2.microsoft.com/kb/971800)。

> [!IMPORTANT]
> 若要使用 Intune 管理 Windows 防火牆，請確定您所管理的電腦上已啟用下列兩項服務：
>
> -   Windows 防火牆
> -   IPsec 原則代理

## <a name="configure-a-windows-firewall-policy"></a>設定 Windows 防火牆原則

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/) 中，選擇 [原則] &gt; [新增原則]。

2.  設定並部署 **Windows 防火牆設定** 原則。 您可以使用建議的設定或自訂設定。 如需如何建立和部署原則的詳細資訊，請參閱[使用 Microsoft Intune 電腦用戶端的一般 Windows 電腦管理工作](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)。

    下節列出您可以在原則中設定的值，以及在不自訂原則的情況下將使用的預設值。

部署 Windows 防火牆原則之後，即可在 [原則] 工作區的 [所有原則] 頁面上檢視其狀態。

## <a name="specify-policy-settings-for-windows-firewall"></a>指定 Windows 防火牆的原則設定

### <a name="turn-on-windows-firewall"></a>開啟 Windows 防火牆

這些原則設定會為符合下列項目的受管理電腦啟用 Windows 防火牆︰
- 已連接至網域 (例如在工作場所中)
- 已連接至私用 (受信任) 的網路 (例如家用網路)
- 已連接至不受信任的公用網路 (例如咖啡廳)

所有這些設定的預設值都是 [是]，亦即最安全的值。



### <a name="block-all-incoming-connections-including-those-in-the-list-of-allowed-programs"></a>阻擋所有連入連線，包括允許之程式清單中的連線

這些原則設定會為符合下列項目的受管理電腦將 Windows 防火牆設為封鎖連入網路流量︰
- 已連接至網域 (例如在工作場所中)
- 已連接至私用 (受信任) 的網路 (例如家用網路)
- 已連接至不受信任的公用網路 (例如咖啡廳)

所有這些設定的預設值都是 [是]，亦即最安全的值。

> [!IMPORTANT]
> 如果您環境中包含執行 Window Vista 但未安裝 Service Pack 的電腦，則您必須安裝與 Miscrosoft 知識庫中[文章 971800](http://go.microsoft.com/fwlink/?LinkId=188405) 的相關更新，或是停用部署到該電腦之原則中的 [封鎖所有連入連線] 原則設定。

### <a name="notify-the-user-when-windows-firewall-blocks-a-new-program"></a>當 Windows 防火牆阻擋新程式時通知使用者

這些原則設定會為符合下列項目的受管理電腦判斷 Windows 防火牆是否會在封鎖連入網路流量時通知電腦使用者︰
- 已連接至網域 (例如在工作場所中)
- 已連接至私用 (受信任) 的網路 (例如家用網路)
- 已連接至不受信任的公用網路 (例如咖啡廳)

所有這些設定的預設值都是 [是]。


### <a name="configure-predefined-exceptions"></a>設定預先定義的例外狀況

您可以設定例外狀況，允許特定類型的網路流量通過防火牆，無論您先前設定的值為何。 這些設定根據預設皆不會設定。

|設定名稱|詳細資料|
|------------------|--------------------|
|**BranchCache - 內容擷取**<br>(Windows 7 或更新版本)|可讓 BranchCache 用戶端使用 HTTP 在分散模式下自其他 BranchCache 用戶端擷取內容，並在託管快取模式下從託管快取擷取內容。 這項設定使用 HTTP。|
|**BranchCache - 託管快取用戶端**<br>(Windows 7 或更新版本)|可讓 BranchCache 用戶端使用託管快取。 這項設定使用 HTTPS。|
|**BranchCache - 託管快取伺服器**|可讓 BranchCache 用戶端使用託管快取與其他用戶端通訊。 這項設定使用 HTTPS。|
|**BranchCache - 同儕節點探索**<br>(Windows 7 或更新版本)|可讓 BranchCache 用戶端使用 Web 服務動態探索 (WS-Discovery) 通訊協定，查詢本機子網路上的內容可用性。|
|**BITS 對等快取**|可讓用戶端使用背景智慧型傳送服務 (BITS)，在相同子網路中的用戶端上尋找及共用儲存在 BITS 快取的檔案。 這項設定使用裝置上的 Web 服務 (WSDAPI) 及遠端程序呼叫 (RPC)。|
|**連線到網路投影機**|可讓使用者透過有線或無線網路，連線到投影機來投影簡報。 這項設定使用 WSDAPI。|
|**核心網路功能**|可讓用戶端使用 IPv4 和 IPv6 連線到網路資源。|
|**分散式交易協調器**|可讓受管理電腦協調更新受交易保護之資源 (例如資料庫、訊息佇列和檔案系統) 的交易。|
|**檔案及印表機共用**|可讓使用者與網路上的其他使用者共用本機檔案和印表機。 這項設定使用 NetBIOS、連結本機多點傳送名稱解析 (LLMNR)、伺服器訊息區 (SMB) 通訊協定及 RPC。|
|**HomeGroup**<br>(Windows 7 或更新版本)|可讓受管理電腦加入 HomeGroup 網路。|
|**iSCSI 服務**|可讓受管理電腦連線到 iSCSI 伺服器和裝置。|
|**金鑰管理服務**|可讓您計算企業環境中電腦的授權相容。|
|**Media Center Extenders**|可讓 Media Center Extender 與執行 Windows Media Center 的電腦通訊。 這項設定使用簡易服務探索通訊協定 (SSDP) 及 qWave。|
|**Netlogon 服務**|設定網域用戶端和網域控制站之間的安全性通道，以驗證使用者和服務。 這項設定使用 RPC。|
|**網路探索**|可讓電腦探索其他裝置，並被網路上的其他裝置探索。 這項設定使用功能探索裝載與發佈服務，以及 SSDP、NetBIOS、LLMNR 和 UPnP 網路通訊協定。|
|**效能記錄檔及警示**|可讓您從遠端管理效能記錄檔及警示服務。 這項設定使用 RPC。|
|**遠端系統管理**|可允許對電腦進行遠端系統管理。|
|**遠端協助**|可讓受管理電腦的使用者要求網路上的其他使用者提供遠端協助。 這項設定使用 SSDP、對等名稱解析通訊協定 (PNRP)、Teredo 和 UPnP 網路通訊協定。|
|**遠端桌面**|可讓電腦使用遠端桌面來存取其他電腦。|
|**遠端事件記錄檔管理**|可讓您從遠端檢視及管理用戶端事件記錄檔。 這項設定使用具名管道和 RPC。|
|**遠端排程工作管理**|可允許對工作排定服務進行遠端管理。 這項設定使用 RPC。|
|**遠端服務管理**|可允許對用戶端上的本機服務進行遠端管理。 這項設定使用具名管道和 RPC。|
|**遠端磁碟區管理**|可允許進行遠端軟體及硬體磁碟區管理。 這項設定使用 RPC。|
|**路由及遠端存取**|可允許傳入 VPN 及遠端存取連線連到電腦。|
|**安全通訊端通道通訊協定**|可允許使用安全通訊端通道通訊協定 (SSTP) 連到受管理電腦的傳入 VPN 連線。 這項設定使用 HTTPS。|
|**SNMP 陷阱**|可讓受管理電腦接收簡易網路管理通訊協定 (SNMP) 陷阱服務流量。|
|**UPnP 架構**|在電腦上設定 UPnP 架構服務，讓電腦可探索並使用經過 UPnP 認證的裝置。|
|**Windows 共用檢視電腦名稱登錄服務**|可讓電腦透過 SSDP 及 PNRP 尋找其他電腦並與之通訊。|
|**Windows Media Player**|可讓使用者透過使用者資料包通訊協定 (UDP) 接收串流媒體。|
|**Windows Media Player 網路共用服務**|可讓使用者透過網路共用媒體。 這項設定使用 SSDP、qWave 和 UPnP 網路通訊協定。|
|**Windows Media Player 網路共用服務 (網際網路)**<br>(Windows 7 或更新版本)|可讓使用者透過網際網路共用家用媒體。|
|**Windows 會議空間**|可讓使用者透過網路執行協同作業，以共用文件、程式及其桌面。 這項設定使用分散式檔案系統複寫 (DFSR) 及 P2P。|
|**Windows Peer to Peer Collaboration Foundation**|設定各種點對點程式及技術，以允許其連線。 這項設定使用 SSDP 和 PNRP。|
|**Windows 遠端管理 (相容性)**|可允許使用 WS-Management (Web 服務通訊協定，用於作業系統和裝置的遠端管理) 對受管理電腦進行遠端管理。|
|**Windows 遠端管理**<br>(Windows 8 或更新版本)|可允許使用 WS-Management (Web 服務通訊協定，用於作業系統和裝置的遠端管理) 對受管理電腦進行遠端管理。|
|**Windows Virtual PC**<br>(Windows 7 或更新版本)|可讓虛擬機器與其他電腦通訊。|
|**無線可攜式裝置**|可允許使用媒體傳輸通訊協定 (MTP)，將媒體從支援網路存取的相機或媒體裝置傳送到受管理電腦。 這項設定使用 SSDP 和 UPnP 網路通訊協定。|

### <a name="see-also"></a>另請參閱
[保護 Windows 電腦的原則](policies-to-protect-windows-pcs-in-microsoft-intune.md)
