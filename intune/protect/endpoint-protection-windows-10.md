---
title: Microsoft Intune 中 Windows 10 裝置的保護設定 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，於 Windows 10 裝置上，使用或設定 Endpoint Protection 設定以啟用 Windows Defender 功能，包括「應用程式防護」、「防火牆」、SmartScreen、加密和 BitLocker、「惡意探索防護」、「應用程式控制」、「資訊安全中心」，以及本機裝置上的安全性。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: karthig
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 22e3779cd0772753ccd8843cd1f1ff38617298d6
ms.sourcegitcommit: 884654da8e72a63bfaea6b5def6c7891b065f251
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163573"
---
# <a name="windows-10-and-later-settings-to-protect-devices-using-intune"></a>使用 Intune 保護裝置的 Windows 10 (及更新版本) 設定  

[!INCLUDE [azure_portal](../includes/azure_portal.md)]  

Microsoft Intune 包含許多設定，可協助保護您的裝置。 本文描述您可以在 Windows 10 及更新版本裝置中啟用及設定的所有設定。 這些設定是為了控制安全性而在 Intune 的 Endpoint Protection 組態設定檔中建立，包括 BitLocker 和 Windows Defender。  

若要設定 Windows Defender 防毒軟體，請參閱 [Windows 10 裝置限制](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)。  

## <a name="before-you-begin"></a>開始之前  

[建立 Endpoint Protection 裝置組態設定檔](endpoint-protection-configure.md)。  

如需設定服務提供者（Csp）的詳細資訊，請參閱設定[服務提供者參考](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)。  

## <a name="windows-defender-application-guard"></a>Windows Defender 應用程式防護  

使用 Microsoft Edge 時，Windows Defender 應用程式防護可保護您的環境免受組織不信任之網站的影響。 當使用者瀏覽未列在隔離之網路界限中的網站時，這些網站將在 Hyper-V 虛擬瀏覽工作階段中開啟。 信任的網站是由網路界限定義，並在 [裝置設定] 中進行設定。  

應用程式防護只適用於 Windows 10 (64 位元) 裝置。 使用此設定檔會安裝 Win32 元件，以啟動應用程式防護。  

- **應用程式防護**  
  **預設**：未設定  
   應用程式防護 CSP：[設定/AllowWindowsDefenderApplicationGuard](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#allowwindowsdefenderapplicationguard)  

  - **為 Edge 啟用** - 開啟此功能，這會在 Hyper-V 虛擬化瀏覽容器中開啟未受信任的網站。  
  - **未設定**-任何網站（受信任和未受信任）都可以在裝置上開啟。  

- **剪貼簿行為**  
  **預設**：未設定  
   應用程式防護 CSP：[設定/ClipboardSettings](https://go.microsoft.com/fwlink/?linkid=872351)  

  選擇要在本機電腦和應用程式防護虛擬瀏覽器之間允許的複製與貼上動作。  
  - **未設定**  
  - **僅允許從電腦複製並貼到瀏覽器**  
  - **僅允許從瀏覽器複製並貼上至 PC**  
  - **允許在電腦與瀏覽器之間進行複製和貼上**  
  - **封鎖電腦與瀏覽器之間的複製和貼上**  

- **剪貼簿內容**  
  只有當 [*剪貼簿行為*] 設為 [*允許*] 設定之一時，才能使用此設定。  
  **預設**：未設定  
  應用程式防護 CSP：[設定/ClipboardFileType](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#clipboardfiletype)  

  選取允許的剪貼簿內容。  
  - **未設定**  
  - **Text**  
  - **影像**  
  - **文字和影像**  

- **在企業網站上的外部內容**  
  **預設**：未設定  
  應用程式防護 CSP：[設定/BlockNonEnterpriseContent](https://go.microsoft.com/fwlink/?linkid=872352)  

  - **封鎖** - 封鎖載入來自未經核准網站的內容。  
  - **未設定** - 非企業網站可在裝置上開啟。  
 
- **從虛擬瀏覽器列印**  
  **預設**：未設定  
  應用程式防護 CSP：[設定/PrintingSettings](https://go.microsoft.com/fwlink/?linkid=872354)  

  - **允許**-允許從虛擬瀏覽器列印選取的內容。  
  - **未設定**停用所有列印功能。  

  當您*允許*列印時，您可以設定下列設定：
  - **列印類型**選取下列一個或多個選項：  
    - PDF  
    - XPS  
    - 本機印表機
    - 網路印表機  

- **收集記錄**  
  **預設**：未設定  
  應用程式防護 CSP： [Audit/AuditApplicationGuard](https://go.microsoft.com/fwlink/?linkid=872418)  

  - **允許** - 收集應用程式防護瀏覽工作階段內發生的事件記錄檔。  
  - **未設定** - 不會收集瀏覽工作階段內的任何記錄。  

- **保留使用者產生的瀏覽器資料**  
  **預設**：未設定  
  應用程式防護 CSP：[設定/AllowPersistence](https://go.microsoft.com/fwlink/?linkid=872419)  

  - **允許** 儲存於應用程式防護虛擬瀏覽工作階段期間建立的使用者資料 (例如密碼、我的最愛和 Cookie)。  
  - **未設定** 在裝置重新啟動或使用者登出時，捨棄使用者下載的檔案和資料。  

- **圖形加速**  
 **預設**：未設定  
  應用程式防護 CSP：[設定/AllowVirtualGPU](https://go.microsoft.com/fwlink/?linkid=872420)  
      
  - **啟用** - 可透過取得對虛擬圖形處理器的存取權，加快載入高圖形效能需求網站和視訊的速度。  
  - **未設定**針對圖形使用裝置的 CPU;請勿使用虛擬圖形處理單元。  

- **將檔案下載到主機檔案系統**  
  **預設**：未設定  
  應用程式防護 CSP：[設定/SaveFilesToHost](https://go.microsoft.com/fwlink/?linkid=872421)  

  - **啟用** - 使用者可以將檔案從虛擬化瀏覽器下載到主機作業系統。  
  - **未設定** - 會將檔案保留在本機裝置上，而不將檔案下載到主機檔案系統。  

## <a name="windows-defender-firewall"></a>Windows Defender 防火牆  
 
### <a name="global-settings"></a>全域設定  

這些設定適用於所有網路類型。  

- **檔案傳輸通訊協定**  
  **預設**：未設定  
   防火牆 CSP： [MdmStore/Global/DisableStatefulFtp](https://go.microsoft.com/fwlink/?linkid=872536)  

  - **封鎖** - 停用可設定狀態的 FTP。  
  - **未設定** - 防火牆會執行可設定狀態的 FTP 篩選來允許次要連線。  

- **刪除前的安全性關聯閒置時間**  
  **預設值**：*未設定*  
   防火牆 CSP： [MdmStore/Global/SaIdleTime](https://go.microsoft.com/fwlink/?linkid=872539)  

   指定刪除安全性關聯之後的閒置時間（以秒為單位）。   

- **預先共用金鑰的編碼**  
  **預設**：未設定  
   防火牆 CSP： [MdmStore/Global/PresharedKeyEncoding](https://go.microsoft.com/fwlink/?linkid=872541)  

   - **啟用**-使用 utf-8 編碼 presheared 索引鍵。  
   - **未設定**-使用本機存放區值來編碼 presheared 的索引鍵。  

- **IPsec 豁免**  
  **預設值**：已*選取 0*  
   防火牆 CSP： [MdmStore/Global/IPsecExempt](https://go.microsoft.com/fwlink/?linkid=872547)

   選取下列一或多個要豁免 IPsec 的流量類型：  
   - **芳鄰探索 IPv6 的 ICMP 類型代碼**  
   - **ICMP**  
   - **路由器探索 IPv6 的 ICMP 類型代碼**  
   - **IPv4 和 IPv6 的 DHCP 網路流量**  

- **憑證撤銷清單驗證**  
  **預設**：未設定  
  防火牆 CSP： [MdmStore/Global/CRLcheck](https://go.microsoft.com/fwlink/?linkid=872548)  

  選擇裝置驗證憑證撤銷清單的方式。 這些選項包括：  
  - **停用 CRL 驗證**  
  - **只有撤銷的憑證上的 CRL 驗證失敗**  
  - **因發生任何錯誤而導致 CRL 驗證失敗**。  
 

- **視情況按各金鑰產製模組比對驗證機**  
  **預設**：未設定  
  防火牆 CSP： [MdmStore/Global/OpportunisticallyMatchAuthSetPerKM](https://go.microsoft.com/fwlink/?linkid=872550)  
  
  - **啟用** - 金鑰處理模組必須只忽略不支援的驗證套件。  
  - **未設定** - 如果金鑰處理模組不支援驗證組中指定的所有驗證套件，則必須忽略整個驗證組。  


- **封包佇列**  
  **預設**：未設定  
  防火牆 CSP： [MdmStore/Global/EnablePacketQueue](https://go.microsoft.com/fwlink/?linkid=872551)  

  指定接收端軟體縮放如何用於 IPsec 通道閘道情節的加密接收與純文字轉送。 此設定會確認保留封包順序。 這些選項包括：  
  - **未設定**  
  - **停用所有封包佇列**  
  - **僅將輸入加密封包排入佇列**  
  - **執行解密後的佇列封包僅供轉送之用**  
  - **設定輸入和輸出封包**  

### <a name="network-settings"></a>網路設定  

這篇文章中的每個設定都是一次，但全都適用于三種特定的網路類型：  
- **網域（工作場所）網路**  
- **私用（可探索）網路**  
- **公用（不可探索）網路**  

#### <a name="general-settings"></a>一般設定  

- **Windows Defender 防火牆**  
  **預設**：未設定  
  防火牆 CSP： [os.enablefirewall](https://go.microsoft.com/fwlink/?linkid=872558)  
  
  - **啟用** - 開啟防火牆和進階安全性。 
  - **未設定** - 允許所有網路流量，而不論任何其他原則設定為何。  

- **隱形模式**  
  **預設**：未設定  
  防火牆 CSP： [DisableStealthMode](https://go.microsoft.com/fwlink/?linkid=872559)  
  - **未設定**  
  - **封鎖-防火牆**在隱形模式下無法運作。 封鎖隱形模式可讓您也封鎖 **IPsec 安全封包豁免**。  
  - **允許**-防火牆在隱形模式下運作，這有助於防止探查要求的回應。  

- **具有隱形模式的 IPsec 安全封包豁免**  
  **預設**：未設定  
  防火牆 CSP： [DisableStealthModeIpsecSecuredPacketExemption](https://go.microsoft.com/fwlink/?linkid=872560)  

  如果 [*隱形模式]* 設定為 [*封鎖*]，則會忽略此選項。  

  - **未設定**  
  - **封鎖**-受 IPSec 保護的封包不會收到豁免。  
  - **允許**-啟用豁免。 防火牆的隱形模式不能防止主機電腦回應受 IPsec 保護的未經要求網路流量。  

- **受防護**  
  **預設**：未設定  
  防火牆 CSP：[受防護](https://go.microsoft.com/fwlink/?linkid=872561)  
    - **未設定**  
    - **封鎖**-當 Windows Defender 防火牆開啟且此設定設為 [*封鎖*] 時，不論其他原則設定為何，所有連入流量都會遭到封鎖。 
    - **允許**-設定為 [*允許*] 時，會關閉此設定，並根據其他原則設定允許傳入流量。

- **多點傳送廣播的單點回應**  
  **預設**：未設定  
  防火牆 CSP： [DisableUnicastResponsesToMulticastBroadcast](https://go.microsoft.com/fwlink/?linkid=872562)  
  
  一般而言，您不希望接收對多點傳送或廣播訊息的單點傳播回應。 這些回應可能表示拒絕服務 (DOS) 的攻擊，或者攻擊者嘗試探查已知的即時電腦。  
  - **未設定**  
  - **禁止** - 停用多點傳送廣播的單點回應。  
  - **允許** - 允許多點傳送廣播的單點回應。  

- **輸入通知**  
  **預設**：未設定  
  防火牆 CSP： [DisableInboundNotifications](https://go.microsoft.com/fwlink/?linkid=8725630)  

  - **未設定**  
  - **封鎖**-隱藏當應用程式被封鎖而無法接聽埠時，所要使用的通知。  
  - **允許** - 啟用此設定可在封鎖應用程式接聽連接埠期間向使用者顯示通知。  

- **輸出連線的預設動作**  
  **預設**：未設定  
  防火牆 CSP： [DefaultOutboundAction](https://aka.ms/intune-firewall-outboundaction)  
  
  設定防火牆在輸出連線上執行的預設動作。 此設定將套用至 Windows 1809 版和更新版本。  

  - **未設定**  
  - **封鎖**-預設防火牆動作不會在輸出流量上執行，除非明確指定不封鎖。  
  - **允許**-在輸出連線上執行的預設防火牆動作。  

- **輸入連線的預設動作**  
  **預設**：未設定  
  防火牆 CSP： [DefaultInboundAction](https://go.microsoft.com/fwlink/?linkid=872564)  
 
  - **未設定**  
  - **封鎖** - 不會對輸入連線執行預設防火牆動作。  
  - **允許**-預設防火牆動作會在輸入連線上執行。  

#### <a name="rule-merging"></a>規則合併  

- **來自本機存放區的授權應用程式 Windows Defender 防火牆規則**  
  **預設**：未設定  
  防火牆 CSP： [AuthAppsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872565)  

  - **未設定**  
  - **封鎖** - 忽略且不會強制執行本機存放區中的已授權應用程式防火牆規則。  
  - **允許** -
   選擇 [啟用] **** 可套用本機存放區中要辨識並強制執行的防火牆規則。  

- **來自本機存放區的全域連接埠 Windows Defender 防火牆規則**  
  **預設**：未設定  
  防火牆 CSP： [GlobalPortsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872566)  

  - **未設定**  
  - **封鎖**-已忽略且不會強制執行本機存放區中的全域埠防火牆規則。  
  - **允許** - 套用本機存放區中要辨識並強制執行的全域連接埠防火牆規則。  

- **來自本機存放區的 Windows Defender 防火牆規則**  
  **預設**：未設定  
  防火牆 CSP： [AllowLocalPolicyMerge](https://go.microsoft.com/fwlink/?linkid=872567)  

  - **未設定**  
  - **封鎖**-來自本機存放區的防火牆規則會被忽略且不會強制執行。
  - **允許** - 套用本機存放區中要辨識並強制執行的防火牆規則。  

- **來自本機存放區的 IPsec 規則**  
  **預設**：未設定  
  防火牆 CSP： [AllowLocalIpsecPolicyMerge](https://go.microsoft.com/fwlink/?linkid=872568)  

  - **未設定**  
  - **封鎖** - 忽略且不會強制執行來自本機存放區的連線安全性規則，而不論結構描述版本和連線安全性規則版本為何。  
  - **允許** - 套用來自本機存放區的連線安全性規則，而不論結構描述或連線安全性規則版本為何。  

### <a name="firewall-rules"></a>防火牆規則  

您可以**新增**一或多個自訂防火牆規則。 如需詳細資訊，請參閱[新增適用于 Windows 10 裝置的自訂防火牆規則](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices)。  

自訂防火牆規則支援下列選項：  

#### <a name="general-settings"></a>一般設定：  

- **名稱**  
  **預設值**：*沒有名稱*  

  指定規則的易記名稱。 這個名稱會出現在規則清單中，以協助您識別它。  

- **描述**  
  **預設值**：*沒有描述*  

  提供規則的描述。  

- **方向**   
  **預設**：未設定  
  防火牆 CSP： [FirewallRules/*FirewallRuleName*/Direction](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#direction)  
  
  指定此規則要套用至**輸入**或**輸出**流量。 當設為 [**未**設定] 時，此規則會自動套用至輸出流量。  

- **動作**  
  **預設**：未設定  
  防火牆 CSP： [FirewallRules/*FirewallRuleName*/Action](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#action)和[FirewallRules/*FirewallRuleName*/Action/Type](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#type)  

  選取 [**允許**] 或 [**封鎖**]。 設為 [**未**設定] 時，規則預設為允許流量。  

- **網路類型**  
  **預設值**：已選取0  
  防火牆 CSP： [FirewallRules/*FirewallRuleName*/Profiles](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#profiles)  

  最多可選取此規則所屬的三種類型的網路類型。 選項包括 [**網域**]、[**私**用] 和 [**公用**]。  如果未選取任何網路類型，規則會套用至所有三種網路類型。  

#### <a name="application-settings"></a>應用程式設定  

- **應用程式**  
  **預設**：全部  

  控制應用程式或程式的連接。 選取下列其中一個選項，然後完成其他設定：  
  - **套件系列名稱**–指定套件系列名稱。 若要尋找套件系列名稱，請使用 PowerShell 命令**add-appxpackage**。   
    防火牆 CSP： [FirewallRules/*FirewallRuleName*/App/PackageFamilyName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#packagefamilyname)  
 
  - 檔案**路徑**–您必須在用戶端裝置上指定應用程式的檔案路徑，這可以是絕對路徑或相對路徑。 例如： C:\Windows\System\Notepad.exe 或%WINDIR%\Notepad.exe。  
    防火牆 CSP： [FirewallRules/*FirewallRuleName*/App/FilePath](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#filepath)  

  - **Windows 服務**–指定 windows 服務簡短名稱（如果它是服務），而不是傳送或接收流量的應用程式。 若要尋找服務的簡短名稱，請使用 PowerShell 命令**Get-服務**。  
    防火牆 CSP： [FirewallRules/*FirewallRuleName*/App/ServiceName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#servicename)  

  - **全部**–*不提供其他*設定。  

#### <a name="ip-address-settings"></a>IP 位址設定  

指定要套用此規則的本機和遠端位址。  

- **本機位址**    
  **預設值**：任何位址  
  防火牆 CSP： [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  

  選取**任何位址**或**指定的位址**。  

  當您使用*指定的位址*時，您會將一或多個位址新增為規則所涵蓋的本機地址清單（以逗號分隔）。 有效的權杖包括：  
  - 針對*任何*本機位址使用星號 "*"。 如果您使用星號，它必須是您唯一使用的權杖。  
  - 若要指定子網，請使用子網路遮罩或網路首碼標記法。 如果未指定子網路遮罩或網路首碼，則子網路遮罩會預設為255.255.255.255。  
  - 有效的 IPv6 位址。  
  - 格式為「起始位址-結束位址」的 IPv4 位址範圍，未包含任何空格。  
  - 格式為「起始位址-結束位址」的 IPv6 位址範圍，未包含任何空格。  

- **遠端位址**  
  **預設值**：任何位址  
  防火牆 CSP： [FirewallRules/*FirewallRuleName*/RemoteAddressRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteaddressranges)  
 
  選取**任何位址**或**指定的位址**。  

  當您使用*指定的位址*時，您會將一或多個位址新增為規則所涵蓋的遠端地址清單（以逗號分隔）。 標記不區分大小寫。 有效的權杖包括：  
  - 針對*任何*遠端位址使用星號 "*"。 如果您使用星號，它必須是您唯一使用的權杖。  
  - Defaultgateway  
  - "DHCP"  
  - "DNS"  
  - "WINS"  
  - 「內部網路」（Windows 1809 版和更新版本支援）  
  - "RmtIntranet" （在 Windows 1809 和更新版本上支援）  
  - "Internet" （Windows 1809 版和更新版本支援）  
  - "Ply2Renders" （在 Windows 1809 和更新版本上支援）  
  - "LocalSubnet" 表示本機子網上的任何本機位址。  
  - 若要指定子網，請使用子網路遮罩或網路首碼標記法。 如果未指定子網路遮罩或網路首碼，則子網路遮罩會預設為255.255.255.255。  
  - 有效的 IPv6 位址。  
  - 格式為「起始位址-結束位址」的 IPv4 位址範圍，未包含任何空格。  
  - 格式為「起始位址-結束位址」的 IPv6 位址範圍，未包含任何空格。  

#### <a name="port-and-protocol-settings"></a>埠和通訊協定設定  
指定要套用此規則的本機和遠端埠。  

- **通訊協定**  
  **預設值**：任何  
  防火牆 CSP： [FirewallRules/*FirewallRuleName*/Protocol](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#protocol)  
  選取下列內容，然後完成任何必要的設定：  
  - **全部**–不提供其他設定。  
  - **TCP** –設定本機和遠端埠。 這兩個選項都支援所有埠或指定的埠。 使用逗號分隔清單來輸入指定的埠。  
    - **本機埠**-防火牆 CSP： [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **遠端埠**-防火牆 CSP： [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **UDP** –設定本機和遠端埠。 這兩個選項都支援所有埠或指定的埠。 使用逗號分隔清單來輸入指定的埠。  
    - **本機埠**-防火牆 CSP： [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **遠端埠**-防火牆 CSP： [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **自訂**–指定從0到255的自訂**通訊協定**編號。  

#### <a name="advanced-configuration"></a>進階設定  
- **介面類型**  
  **預設值**：已選取0  
  防火牆 CSP： [FirewallRules/*FirewallRuleName*/InterfaceTypes](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#interfacetypes)  

  從下列選項選取：  
  - **遠端存取**  
  - **無線**  
  - **區域網路**  

- **只允許來自這些使用者的連接**  
  **預設值**：所有使用者 *（未指定任何清單時，預設為全部使用）*  
  防火牆 CSP： [FirewallRules/*FirewallRuleName*/LocalUserAuthorizationList](https://aka.ms/intunefirewallauthorizedusers)  

  指定此規則的授權本機使用者清單。 若此規則適用于 Windows 服務，則無法指定授權使用者的清單。  


## <a name="windows-defender-smartscreen-settings"></a>Windows Defender SmartScreen 設定  
 
裝置上必須安裝 Microsoft Edge。  

- **應用程式及檔案適用的 SmartScreen**  
  **預設**：未設定  
   SmartScreen CSP： [smartscreen/EnableSmartScreenInShell](https://go.microsoft.com/fwlink/?linkid=872784)  

  - **未設定**-停用 SmartScreen。  
  - **啟用** - 針對檔案執行和執行中的應用程式啟用 Windows SmartScreen。 SmartScreen 是雲端式防網路釣魚和反惡意程式碼元件。  

- **未經驗證檔案的執行**  
  **預設**：未設定  
   SmartScreen CSP： [smartscreen/PreventOverrideForFilesInShell](https://go.microsoft.com/fwlink/?linkid=872783)

  - **未設定** - 停用此功能，並讓終端使用者執行尚未驗證的檔案。  
  - **封鎖** - 防止終端使用者執行 Windows SmartScreen 尚未驗證的檔案。  

## <a name="windows-encryption"></a>Windows 加密  
 
### <a name="windows-settings"></a>Windows 設定  

這些加密設定適用于所有版本的 Windows 10。  

- **加密裝置**  
  **預設**：未設定  
  BitLocker CSP： [RequireDeviceEncryption](https://go.microsoft.com/fwlink/?linkid=872523)  

  - **需要** - 提示使用者啟用裝置加密。 根據 Windows 版本和系統設定，可能會要求使用者：  
    - 確認未啟用來自其他提供者的加密。  
    - 必須關閉 BitLocker 磁碟機加密，然後重新開啟 BitLocker。  
  - **未設定**  
  
  如果已在另一種加密方法為使用中時開啟 Windows 加密，裝置可能會變得不穩定。  

- **加密儲存卡 (僅行動裝置)**  
  此設定只適用於 Windows 10 行動裝置版。   
  **預設**：未設定  
  BitLocker CSP： [RequireStorageCardEncryption](https://go.microsoft.com/fwlink/?linkid=872524)  

  - [需要]  表示加密裝置使用的任何抽取式儲存卡。  
  - **未設定** - 不需要儲存卡加密，而且不會提示使用者將它開啟。  

### <a name="bitlocker-base-settings"></a>BitLocker 基本設定  

基底設定是適用於所有資料磁碟機類型的通用 BitLocker 設定。 這些設定會管理終端使用者在所有資料磁碟機類型上可以修改的磁碟機加密工作或設定選項。  

- **其他磁碟加密的警告**  
  **預設**：未設定  
  BitLocker CSP： [AllowWarningForOtherDiskEncryption](https://go.microsoft.com/fwlink/?linkid=872525)  

  - **封鎖** - 可在裝置上有其他磁碟加密服務時，停用警告提示。  
  - **未設定**-允許顯示其他磁片加密的警告。  

  當設定為 [*封鎖*] 時，您可以進行下列設定：  

  - **允許標準使用者在 Azure AD Join 時啟用加密**  
    *這項設定只適用于已加入 Azure Active Directory （Azure 形容詞）裝置，且取決於先前的設定，`Warning for other disk encryption`。*  
    **預設**：未設定  
    BitLocker CSP： [AllowStandardUserEncryption](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowstandarduserencryption)

     - **允許**標準使用者（非系統管理員）可以在登入時啟用 BitLocker 加密。  
     - **未設定** - 只有系統管理員可以在裝置上啟用 BitLocker 加密。  

- **設定加密方法**  
  **預設**：未設定  
  BitLocker CSP： [EncryptionMethodByDriveType](https://go.microsoft.com/fwlink/?linkid=872526)  

  - **啟用** - 設定作業系統、資料和抽取式磁碟機的加密演算法。  
  - **未設定** - BitLocker 會使用 XTS-AES 128 位元作為預設加密方法，或使用任何安裝指令碼指定的加密方法。  

  當設定為 [啟用]  時，您可以設定下列設定：  

  - **作業系統磁碟機的加密**  
    **預設值**： XTS-AES 128 位  
   
    選擇作業系統磁碟機的加密方法。 建議您使用 XTS-AES 演算法。  
    - **AES-CBC 128 位**  
    - **AES-CBC 256 位**  
    - **XTS-AES 128 位**  
    - **XTS-AES 256 位**  

  - **固定式資料磁碟機的加密**  
    **預設值**： AES-CBC 128 位  
   
    選擇固定式 (內建) 資料磁碟機的加密方法。 建議您使用 XTS-AES 演算法。  
    - **AES-CBC 128 位**  
    - **AES-CBC 256 位**  
    - **XTS-AES 128 位**  
    - **XTS-AES 256 位**  

  - **抽取式磁碟機的加密**  
    **預設值**： AES-CBC 128 位  

    選擇抽取式資料磁碟機的加密方法。 如果抽取式磁碟機與不是執行 Windows 10 的裝置搭配使用，則建議您使用 AES-CBC 演算法。  
    - **AES-CBC 128 位**  
    - **AES-CBC 256 位**  
    - **XTS-AES 128 位**  
    - **XTS-AES 256 位**  

### <a name="bitlocker-os-drive-settings"></a>BitLocker 作業系統磁碟機設定  

這些設定只套用在作業系統資料磁碟機。  

- **啟動時的額外驗證**  
  **預設**：未設定  
  BitLocker CSP： [SystemDrivesRequireStartupAuthentication](https://go.microsoft.com/fwlink/?linkid=872527)  

  - **需要** - 設定電腦啟動時的驗證需求，包括使用信賴平台模組 (TPM)。  
  - **未設定**-僅在具有 TPM 的裝置上設定基本選項。  

  當設定為 [需要]  時，您可以設定下列設定：  

  - **具有不相容 TPM 晶片的 BitLocker**  
    **預設**：未設定  

    - **封鎖** - 當裝置沒有相容的 TPM 晶片時停用 BitLocker。  
    - **未設定** - 使用者可在不含相容 TPM 晶片的情形下使用 BitLocker。 BitLocker 可能需要密碼或啟動金鑰。  

  - **相容 TPM 啟動**  
    **預設**：允許 TPM  

    設定是否允許、需要或不允許 TPM。  

    - **允許 TPM**  
    - **不允許 TPM**  
    - **需要 TPM**  

  - **相容 TPM 啟動 PIN**  
    **預設值**：允許使用 TPM 的啟動 PIN  

    選擇允許、不允許，或需要搭配 TPM 晶片使用啟動 PIN。 啟用啟動 PIN 需要與終端使用者互動。  

    - **允許使用 TPM 的啟動 PIN**  
    - **不允許使用 TPM 的啟動 PIN**  
    - **需要使用 TPM 的啟動 PIN**

  - **相容 TPM 啟動金鑰**  
    **預設值**：允許使用 TPM 的啟動金鑰  

    選擇允許、不允許，或需要搭配 TPM 晶片使用啟動金鑰。 啟用啟動金鑰需要與終端使用者互動。  

    - **允許使用 TPM 的啟動金鑰**  
    - **不允許使用 TPM 的啟動金鑰**  
    - **需要使用 TPM 的啟動金鑰**  

  - **相容 TPM 啟動金鑰及 PIN**  
    **預設值**：允許使用 TPM 的啟動金鑰和 PIN  

    選擇允許、不允許，或需要搭配 TPM 晶片使用啟動金鑰及 PIN。 啟用啟動金鑰及 PIN 需要與終端使用者互動。  
    - **允許使用 TPM 的啟動金鑰和 PIN**  
    - **不允許使用 TPM 的啟動金鑰和 PIN**  
    - **需要使用 TPM 的啟動金鑰和 PIN**   

- **PIN 長度下限**  
    **預設**：未設定  
    BitLocker CSP： [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)   

    - **啟用**設定 TPM 啟動 PIN 的最小長度。  
    - **未設定** - 使用者可以設定介於 6 到 20 位數之任意長度的啟動 PIN。  

  當設定為 [啟用]  時，您可以設定下列設定：  

  - **字元數下限**  
    **預設值**：*未設定*BitLocker CSP： [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)  

    輸入啟動 PIN 所需的字元數 (**4**-**20**)。  

- **OS 磁碟機修復**  
  **預設**：未設定   
  BitLocker CSP： [SystemDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872529)  

  - **啟用** - 控制在未提供必要的啟動資訊時，受 BitLocker 保護的作業系統磁碟機如何復原。  
  - **未設定** - BitLocker 修復支援預設修復選項。 預設允許 DRA，這是使用者選擇的修復選項，包括修復密碼和修復金鑰，以及未備份到 AD DS 的修復資訊。  

  當設定為 [啟用]  時，您可以設定下列設定：  

  - **以憑證為基礎的資料修復代理程式**  
    **預設**：未設定  
     
    - **封鎖**-防止使用資料修復代理與受 BitLocker 保護的 OS 磁片磁碟機。  
    - **未設定**-允許資料修復代理與受 BitLocker 保護的作業系統磁片磁碟機搭配使用。  

  - **使用者的修復密碼建立**  
    **預設值**：允許48位數的修復密碼  

    選擇是否允許、需要還是不允許使用者產生 48 位數的修復密碼。  
    - **允許48位數的修復密碼**  
    - **不允許48位數的修復密碼**  
    - **需要48位數的修復密碼**  

  - **使用者的修復金鑰建立**  
    **預設值**：允許256位修復金鑰  

    選擇是否允許、需要還是不允許使用者產生 256 位元的修復金鑰。  
    - **允許256位修復金鑰**  
    - **不允許256位的修復金鑰**  
    - **需要256位的修復金鑰**  

  - **BitLocker 安裝精靈的修復選項**  
    **預設**：未設定  

    - **封鎖** - 使用者無法看到及變更修復選項。 設定為時 
    - **未設定** - 使用者可以在開啟 BitLocker 時看到及變更修復選項。 
 
  - **將 BitLocker 修復資訊儲存至 Azure Active Directory**  
    **預設**：未設定  

    - **啟用** - 將 BitLocker 修復資訊儲存到 Azure Active Directory (Azure AD)。  
    - **未設定**-BitLocker 修復資訊不會儲存在 AAD 中。  

  - **儲存到 Azure Active Directory 的 BitLocker 修復資訊**  
    **預設**：備份修復密碼和金鑰封裝  

    設定 BitLocker 修復資訊的哪些部分會儲存在 Azure AD 中。 從下列選項進行選擇：  
    - **備份修復密碼和金鑰封裝**  
    - **只備份修復密碼**  

  - **用戶端驅動的修復密碼輪替**  
    **預設值**：為已加入 Azure AD 的裝置啟用金鑰輪替  
    BitLocker CSP： [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    此設定會在 OS 磁片磁碟機復原（使用 bootmgr 或 WinRE）之後，起始用戶端驅動的修復密碼輪替。  

    - 尚未設定  
    - 金鑰輪替已停用  
    - 已啟用 Azure AD 聯結裝置的金鑰輪替  
    - 已針對 Azure AD 和已加入混合式裝置啟用金鑰輪替  

  - **先將修復資訊儲存在 Azure Active Directory 中，然後再啟用 BitLocker**  
    **預設**：未設定  
 
     防止使用者啟用 BitLocker，除非電腦已成功將 BitLocker 修復資訊備份到 Azure Active Directory。  

    - **需要** - 阻止使用者開啟 BitLocker，除非 BitLocker 修復資訊成功儲存在 Azure AD 中。  
    - **未設定** - 使用者可以開啟 BitLocker，即使修復資訊未成功儲存在 Azure AD 中也一樣。  

- **開機前的修復訊息及 URL**  
  **預設**：未設定  
  BitLocker CSP： [SystemDrivesRecoveryMessage](https://go.microsoft.com/fwlink/?linkid=872530)  

  - **啟用**-設定在開機前金鑰修復畫面上顯示的訊息和 URL。  
  - **未設定** - 停用此功能。  
  
  當設定為 [啟用]  時，您可以設定下列設定：  
  - **開機前修復訊息**  
    **預設**：使用預設修復訊息及 URL   
 
    設定如何向使用者顯示開機前修復訊息。 從下列選項進行選擇：  
    - **使用預設修復訊息及 URL**  
    - **使用空白修復訊息及 URL**  
    - **使用自訂修復訊息**  
    - **使用自訂修復 URL**  

### <a name="bitlocker-fixed-data-drive-settings"></a>BitLocker 固定式資料磁碟機設定  

這些設定會特別適用于固定資料磁片磁碟機。  

- **未受 BitLocker 保護的固定式資料磁碟機寫入權限**  
  **預設**：未設定  
  BitLocker CSP： [FixedDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872534)  

  - **封鎖** - 提供不受 BitLocker 保護資料磁碟機的唯讀權限。  
  - **未設定**-根據預設，不會加密之資料磁片磁碟機的讀取和寫入存取權。  

- **固定式磁碟機修復**  
  **預設**：未設定  
  BitLocker CSP： [FixedDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872538)  

  - **啟用** - 控制當未提供必要的啟動資訊時，受 BitLocker 保護的固定式磁碟機如何復原。  
  - **未設定** - 停用此功能。  

  當設定為 [啟用]  時，您可以設定下列設定：  

  - **資料修復代理程式**  
    **預設**：未設定  
 
    - **封鎖** - 防止使用資料修復代理程式搭配受 BitLocker 保護的固定式磁碟機原則編輯器。 
    - **未設定** - 可以使用資料修復代理程式搭配受 BitLocker 保護的固定式磁碟機。  

  - **使用者的修復密碼建立**  
    **預設值**：允許48位數的修復密碼  

    選擇是否允許、需要還是不允許使用者產生 48 位數的修復密碼。  
    - **允許48位數的修復密碼**  
    - **不允許48位數的修復密碼**  
    - **需要48位數的修復密碼**  

  - **使用者的修復金鑰建立**  
    **預設值**：允許256位修復金鑰

    選擇是否允許、需要還是不允許使用者產生 256 位元的修復金鑰。
    - **允許256位修復金鑰**  
    - **不允許256位的修復金鑰**  
    - **需要256位的修復金鑰**  

  - **BitLocker 安裝精靈的修復選項**  
    **預設**：未設定  

    - **封鎖** - 使用者無法看到及變更修復選項。 設定為時 
    - **未設定** - 使用者可以在開啟 BitLocker 時看到及變更修復選項。
 
  - **將 BitLocker 修復資訊儲存至 Azure Active Directory**  
    **預設**：未設定  

    - **啟用** - 將 BitLocker 修復資訊儲存到 Azure Active Directory (Azure AD)。  
    - **未設定**-BitLocker 修復資訊不會儲存在 AAD 中。

  - **儲存到 Azure Active Directory 的 BitLocker 修復資訊**  
    **預設**：備份修復密碼和金鑰封裝  

    設定 BitLocker 修復資訊的哪些部分會儲存在 Azure AD 中。 從下列選項進行選擇：  
    - **備份修復密碼和金鑰封裝**  
    - **只備份修復密碼**  

  - **用戶端驅動的修復密碼輪替**  
    **預設值**：為已加入 Azure AD 的裝置啟用金鑰輪替  
    BitLocker CSP： [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    此設定會在 OS 磁片磁碟機復原（使用 bootmgr 或 WinRE）之後，起始用戶端驅動的修復密碼輪替。  

    - 尚未設定  
    - 金鑰輪替已停用  
    - 已啟用 Azure AD 聯結裝置的金鑰輪替  
    - 已針對 Azure AD 和已加入混合式裝置啟用金鑰輪替  

  - **先將修復資訊儲存在 Azure Active Directory 中，然後再啟用 BitLocker**  
    **預設**：未設定  
 
    防止使用者啟用 BitLocker，除非電腦已成功將 BitLocker 修復資訊備份到 Azure Active Directory。  

    - **需要** - 阻止使用者開啟 BitLocker，除非 BitLocker 修復資訊成功儲存在 Azure AD 中。  
    - **未設定** - 使用者可以開啟 BitLocker，即使修復資訊未成功儲存在 Azure AD 中也一樣。  

### <a name="bitlocker-removable-data-drive-settings"></a>BitLocker 抽取式資料磁碟機設定  

這些設定會特別適用于卸載式資料磁片磁碟機。  

- **未受 BitLocker 保護的抽取式資料磁碟機寫入權限**  
  **預設**：未設定  
  BitLocker CSP： [RemovableDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872540)  

  - **封鎖** - 提供不受 BitLocker 保護資料磁碟機的唯讀權限。  
  - **未設定**-根據預設，不會加密之資料磁片磁碟機的讀取和寫入存取權。  

  當設定為 [啟用]  時，您可以設定下列設定：  

  - **設定在其他組織中的裝置寫入權限**  
    **預設**：未設定  

    - **封鎖** - 封鎖在其他組織中設定之裝置的寫入權限。  
    - **未設定**-拒絕寫入權限。  
 
## <a name="windows-defender-exploit-guard"></a>Windows Defender 惡意探索防護  

使用[惡意探索保護](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/exploit-protection)來管理及減少員工所使用應用程式的受攻擊面。  

### <a name="attack-surface-reduction"></a>攻擊表面縮減  

攻擊表面縮減規則有助於防止惡意程式碼經常用來感染惡意程式碼電腦的行為。  

#### <a name="attack-surface-reduction-rules"></a>受攻擊面縮小規則  

- **標記對 Windows 本機安全性授權子系統進行的認證竊取**  
  **預設**：未設定  
  規則：[從 Windows 規則：封鎖竊取自 Windows 本機安全性授權子系統 (lsass.exe) 的認證](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-credential-stealing-from-the-windows-local-security-authority-subsystem-lsassexe) \(部分機器翻譯\)

  協助預防搜尋惡意程式碼探索通常用來感染電腦的動作與應用程式。  

  - **未設定**  
  - **啟用** - 從 Windows 本機安全性授權子系統設立認證 (lsass.exe) 竊取旗標。  
  - **僅稽核**  

- **從 Adobe Reader 建立進程（搶鮮版（Beta））**  
  **預設**：未設定  
  規則：[封鎖 Adobe Reader 建立子進程](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-adobe-reader-from-creating-child-processes)  

  - **未設定**  
  - **啟用**-封鎖從 Adobe Reader 建立的子進程。  
  - **僅稽核**  

#### <a name="rules-to-prevent-office-macro-threats"></a>預防 Office 巨集威脅的規則  

禁止 Office 應用程式採取下列動作：  

- **Office 應用程式插入其他處理序 (沒有例外狀況)**  
  **預設**：未設定  
  規則：[禁止 Office 應用程式將程式碼插入其他處理序](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-injecting-code-into-other-processes) \(部分機器翻譯\)  

  - **未設定**  
  - **封鎖**-封鎖 Office 應用程式插入其他進程。  
  - **僅稽核**  

- **Office 應用程式/巨集建立可執行檔內容**  
  **預設**：未設定  
  規則：[禁止 Office 應用程式建立可執行的內容](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-creating-executable-content) \(部分機器翻譯\)  

  - **未設定**  
  - **封鎖**-封鎖 Office 應用程式和宏建立可執行檔內容。  
  - **僅稽核**  

- **Office 應用程式啟動子處理序**  
  **預設**：未設定  
  規則：[封鎖所有 Office 應用程式建立子進程](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-all-office-applications-from-creating-child-processes)  

  - **未設定**  
  - **封鎖**-封鎖 Office 應用程式啟動子進程。  
  - **僅稽核**  
  
- **Win32 從 Office 巨集程式碼匯入**  
  **預設**：未設定  
  規則：[封鎖來自 Offeie 巨集的 Win32 API 呼叫](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-win32-api-calls-from-office-macros) \(部分機器翻譯\)  

  - **未設定**  
  - **封鎖**-封鎖從 Office 中的宏程式碼匯入 Win32。  
  - **僅稽核**  
  
- **從 Office 通訊產品建立進程**  
  **預設**：未設定  
  規則：[封鎖 Office 通訊應用程式建立子進程](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-communication-application-from-creating-child-processes)  

  - **未設定**  
  - **啟用**-封鎖從 Office 通訊應用程式建立的子進程。  
  - **僅稽核**  

#### <a name="rules-to-prevent-script-threats"></a>預防指令碼威脅的規則  

請封鎖下列項目以協助防止指令碼威脅：  

- **混淆的 js/vbs/ps/巨集程式碼**  
  **預設**：未設定  
  規則：[禁止執行潛在的混淆指令碼:](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-execution-of-potentially-obfuscated-scripts) \(部分機器翻譯\)    

  - **未設定**  
  - **封鎖**-封鎖任何模糊的 js/vbs/ps/宏程式碼。  
  - **僅稽核**  

- **js/vbs 從網際網路執行裝載下載 (無例外狀況)**  
  **預設**：未設定  
  規則：[禁止 JavaScript 與 VBScript 啟動下載的可執行內容](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-javascript-or-vbscript-from-launching-downloaded-executable-content) \(部分機器翻譯\)  

  - **未設定**  
  - **區塊**-區塊 js/vbs 執行從網際網路下載的內容。  
  - **僅稽核**  

- **從 PSExec 與 WMI 命令建立的程序**  
  **預設**：未設定  
  規則：[封鎖來自 PSExec 與 WMI 命令的處理序建立](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-process-creations-originating-from-psexec-and-wmi-commands) \(部分機器翻譯\)  

  - **未設定**  
  - **封鎖** - 封鎖源自 PSExec 和 WMI 命令的處理序建立。  
  
  - **僅稽核**  

- **從 USB 執行的未受信任及未簽署程序**  
  **預設**：未設定  
  規則：[封鎖從 USB 執行的不信任與未簽署處理序](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-untrusted-and-unsigned-processes-that-run-from-usb) \(部分機器翻譯\)    

  - **未設定**  
  - **封鎖** - 封鎖從 USB 執行的未受信任和未簽署處理序。  
  - **僅稽核**  
  
- **未符合普遍性、年齡或受信任清單準則的可執行檔**  
  **預設**：未設定  
  [封鎖](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) - 封鎖執行可執行檔，除非它們符合普遍性、存留期或受信任清單的條件。    

  - **未設定**  
  - **封鎖** - 封鎖執行可執行檔，除非它們符合普遍性、存留期或受信任清單的條件。  
  - **僅稽核**  

#### <a name="rules-to-prevent-email-threats"></a>預防電子郵件威脅的規則  

請封鎖下列項目以協助防止電子郵件威脅：  

- **執行自電子郵件 (webmail/郵件用戶端) 卸除的可執行檔內容 (exe、dll、ps、js、vbs 等) (沒有例外狀況)**  
  **預設**：未設定  
  規則：[封鎖來自電子郵件用戶端及網路郵件的可執行內容](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-content-from-email-client-and-webmail) \(部分機器翻譯\)  

  - **未設定**  
  - **封鎖** - 封鎖執行自電子郵件 (webmail/郵件用戶端) 卸除的可執行檔內容 (exe、dll、ps、js、vbs 等)。  
  - **僅稽核**  

#### <a name="rules-to-protect-against-ransomware"></a>可預防勒索軟體的規則  

- **進階勒索軟體保護**  
  預設：未設定  
  規則：[對勒索軟體使用進階保護](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#use-advanced-protection-against-ransomware) \(部分機器翻譯\)  

  - **未設定**  
  - **啟用** - 使用積極的勒索軟體防護。  
  - **僅稽核**  

#### <a name="attack-surface-reduction-exceptions"></a>攻擊表面縮減例外狀況

- **要從攻擊面縮減規則中排除的檔案和資料夾**  
  Defender CSP： [AttackSurfaceReductionOnlyExclusions](https://go.microsoft.com/fwlink/?linkid=872981)  

  - 匯**入**包含檔案和資料夾的 .csv 檔案，以排除攻擊面縮減規則。  
  - 手動**新增**本機檔案或資料夾。  

> [!IMPORTANT]  
> 為了允許正確安裝並執行 LOB Win32 應用程式，反惡意程式碼設定應該排除下列目錄不要進行掃描：  
> **在 X64 用戶端電腦上**：  
> *C:\Program Files (x86)\Microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  
>  
> **在 X86 用戶端電腦上**：  
> *C:\Program Files\Microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  

### <a name="controlled-folder-access"></a>受控資料夾存取權  

協助[保護寶貴的資料](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/controlled-folders)不受惡意應用程式和威脅侵害，例如勒索軟體。  

- **資料夾保護**  
  **預設**：未設定  
  Defender CSP： [EnableControlledFolderAccess](https://go.microsoft.com/fwlink/?linkid=872614)  

  保護檔案和資料夾免於惡意應用程式未經授權的變更。  

  - **未設定**  
  - **啟用**  
  - **僅稽核**  
  - **禁止磁碟修改**  
  - **稽核磁碟修改**  

  當您選取 [*未設定*] 以外的設定時，您可以設定：  
  - **可存取受保護資料夾的應用程式清單**  
    Defender CSP： [ControlledFolderAccessAllowedApplications](https://go.microsoft.com/fwlink/?linkid=872616)  

    - 匯**入**包含應用程式清單的 .csv 檔案。  
    - 以手動方式將應用程式**新增**到此清單。  

  - **需要保護的其他資料夾清單**  
    Defender CSP： [ControlledFolderAccessProtectedFolders](https://go.microsoft.com/fwlink/?linkid=872617)  

    - 匯**入**包含資料夾清單的 .csv 檔案。  
    - 以手動方式**將資料夾新增**到此清單。  

### <a name="network-filtering"></a>網路篩選  

封鎖來自任何應用程式的輸出連線，以及低信譽的 IP 位址或網域。 「Audit」和「封鎖」模式都支援網路篩選。  

- **網路保護**  
  **預設**：未設定  
  Defender CSP： [EnableNetworkProtection](https://go.microsoft.com/fwlink/?linkid=872618)  

  此設定的目的是要保護使用者免于應用程式存取網路釣魚詐騙、惡意探索網站，以及網際網路上的惡意內容。 它也會防止協力廠商瀏覽器連接到危險的網站。  

  - **未設定** - 停用此功能。 使用者和應用程式不會遭到封鎖而無法連接到危險的網域。 系統管理員無法在 Windows Defender 資訊安全中心看到此活動。  
  - **啟用**-開啟網路保護，並封鎖使用者和應用程式，使其無法連線到危險的網域。 系統管理員可以在 Windows Defender 資訊安全中心看到此活動。  
  - **僅限 Audit**：-使用者和應用程式不會遭到封鎖而無法連線到危險的網域。 系統管理員可以在 Windows Defender 資訊安全中心看到此活動。  

### <a name="exploit-protection"></a>惡意探索保護  
 

- **上傳 XML**  
  **預設值**：*未設定*  

  若要使用惡意探索保護來[保護裝置免于入侵](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)，請建立 XML 檔案，其中包含您想要的系統和應用程式緩和設定。 有兩種方法可以建立 XML 檔案：  

  - *PowerShell* - 使用一或多個 *Get-ProcessMitigation*、*Set-ProcessMitigation* 和 *ConvertTo-ProcessMitigationPolicy* PowerShell Cmdlet。 Cmdlet 會設定安全防護功能設定，並匯出它們的 XML 表示法。  

  - 「Windows Defender 資訊安全中心 UI」  - Windows Defender 資訊安全中心，按一下 [App 與瀏覽器控制]，然後捲動至結果畫面的底部，找到 [惡意探索保護]。 首先，使用 [系統設定] 與 [程式設定] 索引標籤來進行低風險的設定。 然後，在畫面底部找到 [匯出設定] 連結，匯出它們的 XML 表示。  

- **使用者編輯惡意探索保護介面**  
  **預設**：未設定  
  ExploitGuard CSP： [ExploitProtectionSettings](https://go.microsoft.com/fwlink/?linkid=872887)  


  - **封鎖**-上傳可讓您設定記憶體、控制流程和原則限制的 XML 檔案。 XML 檔案中的設定可用來封鎖惡意探索應用程式。  
  - **未設定**-未使用任何自訂設定。  

## <a name="windows-defender-application-control"></a>Windows Defender 應用程式控制  

選擇需要進行審核的其他應用程式，或可由 Windows Defender 應用程式控制執行信任。 Windows 元件和所有 Windows 市集的應用程式都自動受信任執行。  


- **應用程式控制程式碼完整性原則**  
  **預設**：未設定  
   CSP： [APPLOCKER CSP](https://go.microsoft.com/fwlink/?linkid=874543)  

  - **強制執行**-為使用者的裝置選擇應用程式控制程式碼完整性原則。  
  
    在裝置上啟用應用程式控制之後，就只能透過將模式從 [強制]  變更為 [僅稽核]  來停用。 從*強制*變更為*未設定*模式的結果會是在指派的裝置上繼續強制使用應用程式控制。  

  - **未設定**-應用程式控制不會新增至裝置。 不過，先前新增的設定會繼續在指派的裝置上強制執行。 
 
  - **僅限 Audit** -不會封鎖應用程式。 所有事件都會記錄在本機用戶端的記錄中。  

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard  

Windows Defender Credential Guard 可防止認證遭竊的攻擊。 它會隔離機密資料，因此只有特殊權限的系統軟體可以存取它們。  

- **Credential Guard**  
  **預設值**：停用  
  [DeviceGuard CSP](https://go.microsoft.com/fwlink/?linkid=872424)  

  - **停用** - 如果先前是以 [在不含 UEFI 鎖定情況下啟用]  選項開啟 Credential Guard，此選項就會從遠端關閉它。  

  - **連同 UEFI 鎖定一起啟用** - 此選項無法使用登錄機碼或群組原則從遠端停用 Credential Guard。  

    > [!NOTE]
    > 如果您使用此設定，而稍後想要停用 Credential Guard，則必須將群組原則設定為 [停用]  。 此外，從每一部電腦實際清除 UEFI 設定資訊。 只要 UEFI 設定持續存在，就會啟用 Credential Guard。  

  - **連同 UEFI 鎖定一起啟用** - 此選項可使用群組原則從遠端停用 Credential Guard。 使用此設定的裝置必須執行 Windows 10 1511 版及更新版本。  

  當您「啟用」  Credential Guard 時，也會啟用下列必要的功能：  
  
  - **虛擬化型安全性** (VBS)  
    在下次重新開機期間開啟。 虛擬化型安全性會使用 Windows Hypervisor 來提供安全性服務的支援。  
  - **使用直接記憶體存取進行安全開機**  
    使用安全開機和直接記憶體存取 (DMA) 保護開啟 VBS。 DMA 保護需要硬體支援，而且只能在正確設定的裝置上啟用。  

## <a name="windows-defender-security-center"></a>Windows Defender 資訊安全中心  

Windows Defender 資訊安全中心是以個別的應用程式或各個功能的處理序運行。 它會透過重要訊息中心顯示通知。 它充當收集器，或查看狀態及執行每項功能一些設定的單一位置。 詳細資訊請參閱 [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) 文件。  

### <a name="windows-defender-security-center-app-and-notifications"></a>Windows Defender 資訊安全中心應用程式和通知  

封鎖使用者對「Windows Defender 資訊安全中心」應用程式之各種區域的存取。 隱藏區段也會封鎖相關通知。  

- **病毒與威脅防護**  
  **預設**：未設定  
  WindowsDefenderSecurityCenter CSP： [DisableVirusUI](https://go.microsoft.com/fwlink/?linkid=873662)  

  設定終端使用者是否可以在 Windows Defender 資訊安全中心中查看 [病毒與威脅防護] 區域。 隱藏此區段也會封鎖與病毒和威脅防護相關的所有通知。  

  - **未設定**  
  - [隱藏]   

- **勒索軟體保護**  
  **預設**：未設定  
  WindowsDefenderSecurityCenter CSP： [HideRansomwareDataRecovery](https://go.microsoft.com/fwlink/?linkid=873664)  

  設定終端使用者是否可以在 Windows Defender 資訊安全中心中查看勒索軟體保護區域。 隱藏此區段也會封鎖所有與勒索軟體保護相關的通知。  

  - **未設定**  
  - [隱藏]   

- **帳戶保護**  
  **預設**：未設定  
  WindowsDefenderSecurityCenter CSP： [DisableAccountProtectionUI](https://go.microsoft.com/fwlink/?linkid=873666)  

  設定終端使用者是否可以在 Windows Defender 資訊安全中心中查看 [帳戶保護] 區域。 隱藏此區段也會封鎖與帳戶保護相關的所有通知。  

  - **未設定**  
  - [隱藏]   

- **防火牆與網路保護**  
  **預設**：未設定  
  WindowsDefenderSecurityCenter CSP： [DisableNetworkUI](https://go.microsoft.com/fwlink/?linkid=873668)  

  設定終端使用者是否可以在 Windows Defender 安全性中心內查看 [防火牆和網路保護] 區域。 隱藏此區段也會封鎖與防火牆和網路保護相關的所有通知。  

  - **未設定**  
  - [隱藏]   

- **應用程式與瀏覽器控制**  
  **預設**：未設定  
  WindowsDefenderSecurityCenter CSP： [DisableAppBrowserUI](https://go.microsoft.com/fwlink/?linkid=873669)  

  設定終端使用者是否可以在 Windows Defender 安全性中心內查看應用程式和瀏覽器控制區域。 隱藏此區段也會封鎖與應用程式和瀏覽器控制項相關的所有通知。  

  - **未設定**  
  - [隱藏]   

- **硬體保護**  
  **預設**：未設定  
  WindowsDefenderSecurityCenter CSP： [DisableDeviceSecurityUI](https://go.microsoft.com/fwlink/?linkid=873670)  

  設定終端使用者是否可以在 Windows Defender 資訊安全中心中查看硬體保護區域。 隱藏此區段也會封鎖與硬體保護相關的所有通知。  

  - **未設定**  
  - [隱藏]   

- **裝置效能與健全狀況**  
  **預設**：未設定  
  WindowsDefenderSecurityCenter CSP： [DisableHealthUI](https://go.microsoft.com/fwlink/?linkid=873671)  

  設定終端使用者是否可以在 Windows Defender 安全性中心內查看裝置效能和健全狀況區域。 隱藏此區段也會封鎖與裝置效能和健全狀況相關的所有通知。  
  
  - **未設定**  
  - [隱藏]   

- **家長監護選項**  
  **預設**：未設定  
  WindowsDefenderSecurityCenter CSP： [DisableFamilyUI](https://go.microsoft.com/fwlink/?linkid=873673)  

  設定終端使用者是否可以在 Windows Defender 安全性中心內查看 [系列選項] 區域。 隱藏此區段也會封鎖與系列選項相關的所有通知。  
  
  - **未設定**  
  - [隱藏]   

- **應用程式顯示區的通知**  
  **預設**：未設定  
  WindowsDefenderSecurityCenter CSP： [DisableNotifications](https://go.microsoft.com/fwlink/?linkid=873675)  

  選擇要向終端使用者顯示的通知。 非重大通知包括 Windows Defender 防毒軟體活動摘要，包括掃描完成時的通知。 所有其他通知都被視為重大通知。  

  - **未設定**  
  - **封鎖非重大通知**  
  - **封鎖所有通知**  

- **系統匣中的 Windows 資訊安全中心圖示**  
  **預設**：未設定  

  設定通知區域控制項的顯示。 使用者必須登出再登入或重新開機電腦，這項設定才會生效。  
  
  - **未設定**  
  - [隱藏]   

- **[清除 TPM] 按鈕**  
  **預設**：未設定  

  設定 [清除 TPM] 按鈕的顯示。  
  
  - **未設定**  
  - **停用**  

- **TPM 固件更新警告**  
  **預設**：未設定  
  
  設定在偵測到易受攻擊的固件時，更新 TPM 固件的顯示。  

  - **未設定**  
  - [隱藏]   

- **防篡改保護**  
  **預設**：未設定

  開啟或關閉裝置上的防篡改保護。 若要使用防篡改保護，您必須將[Microsoft Defender Advanced 威脅防護與 Intune 整合](advanced-threat-protection.md)，並擁有[Enterprise Mobility + Security E5 授權](../fundamentals/licenses.md)。  
  - **未設定**-裝置設定不會進行任何變更。
  - [**已啟用**]-[篡改保護] 已開啟，並在裝置上強制執行限制。
  - **已停用**-防篡改保護已關閉，而且不會強制執行限制。

### <a name="it-contact-information"></a>IT 連絡人資訊  

提供要顯示在「Windows Defender 資訊安全中心」應用程式和應用程式通知中的 IT 連絡人資訊。  

您可以選擇 [Display in app and in notifications] \(在應用程式和通知中顯示)  、[Display only in app] \(只在應用程式中顯示)  、[Display only in notifications] \(只在通知中顯示)  或 [Don't display] \(不顯示)  。 輸入 **IT 組織名稱**，以及至少下列其中一個連絡選項：  


- **IT 連絡人資訊**  
  **預設值**：不顯示  
  WindowsDefenderSecurityCenter CSP： [EnableCustomizedToasts](https://go.microsoft.com/fwlink/?linkid=873676)  
  
  設定要向使用者顯示 IT 連絡人資訊的位置。  
  
  - **在應用程式和通知中顯示**  
  - **僅顯示在應用程式中**  
  - **只在通知中顯示**  
  - **不要顯示**  

  當設定為顯示時，您可以設定下列設定：  

  - **IT 組織名稱**  
    **預設值**：*未設定*  
    WindowsDefenderSecurityCenter CSP：[公司名稱](https://go.microsoft.com/fwlink/?linkid=873677)  

  - **IT 部門電話號碼或 Skype 識別碼**  
    **預設值**：*未設定*  
    WindowsDefenderSecurityCenter CSP：[電話](https://go.microsoft.com/fwlink/?linkid=873678) 

  - **IT 部門電子郵件地址**  
    **預設值**：*未設定*  
    WindowsDefenderSecurityCenter CSP：[電子郵件](https://go.microsoft.com/fwlink/?linkid=873679)  

  - **IT 支援網站 URL**  
    **預設值**：*未設定*  
    WindowsDefenderSecurityCenter CSP： [URL](https://go.microsoft.com/fwlink/?linkid=873680)  
 
## <a name="local-device-security-options"></a>本機裝置安全性選項  

您可以使用這些選項來設定 Windows 10 裝置上的本機安全性設定。  

### <a name="accounts"></a>帳戶  

- **新增 Microsoft 帳戶**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [Accounts_BlockMicrosoftAccounts](https://go.microsoft.com/fwlink/?linkid=867916)  


  - **封鎖** 防止使用者在裝置上新增 Microsoft 帳戶。  
  - **未設定**-使用者可以在裝置上使用 Microsoft 帳戶。  

- **不使用密碼從遠端登入**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867890)  


   - **封鎖** - 僅允許具有空白密碼之本機帳戶使用裝置的鍵盤登入。  
   - **未設定** - 允許具有空白密碼的本機帳戶從實體裝置以外的位置登入。  

#### <a name="admin"></a>系統管理員  

- **本機管理員帳戶**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867850)  


  - **封鎖**避免使用本機系統管理員帳戶。  
  - **未設定**  

- **為管理員帳戶重新命名**  
  **預設值**：*未設定*  
  LocalPoliciesSecurityOptions CSP： [Accounts_RenameAdministratorAccount](https://go.microsoft.com/fwlink/?linkid=867917)  
 

  定義要與 "Administrator" 帳戶安全性識別碼 (SID) 建立關聯的其他帳戶名稱。  

 #### <a name="guest"></a>Guest  

- **來賓帳戶**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [LocalPoliciesSecurityOptions](https://go.microsoft.com/fwlink/?linkid=867853)  

  - **封鎖**-防止使用來賓帳戶。  
  - **未設定**  

- **為來賓帳戶重新命名**  
  **預設值**：*未設定*  
  LocalPoliciesSecurityOptions CSP： [Accounts_RenameGuestAccount](https://go.microsoft.com/fwlink/?linkid=867918)  
  
  定義要與 "Guest" 帳戶安全性識別碼 (SID) 建立關聯的其他帳戶名稱。  

### <a name="devices"></a>裝置  

- **不登入即卸除裝置**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [Devices_AllowUndockWithoutHavingToLogon](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-devices-allowundockwithouthavingtologon)  

  
  - **封鎖** - 使用者可以按停駐可攜式裝置的實體退出按鈕，安全地卸除裝置。  
  - **未設定**-使用者必須登入裝置，並接收移除裝置的許可權。  

- **安裝共用印表機的印表機驅動程式**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [Devices_PreventUsersFromInstallingPrinterDriversWhenConnectingToSharedPrinters](https://go.microsoft.com/fwlink/?linkid=867921)  


  - **已啟用** - 任何使用者都可以安裝印表機驅動程式作為連線到共用印表機的一部分。  
  - **未設定** - 只有系統管理員可以安裝印表機驅動程式作為連線到共用印表機的一部分。  

- **限制本機動態使用者對 CD-ROM 的存取**  
  **預設**：未設定  
  CSP： [Devices_RestrictCDROMAccessToLocallyLoggedOnUserOnly](https://go.microsoft.com/fwlink/?linkid=867922)  


  - **已啟用** - 只有以互動方式登入的使用者可以使用 CD-ROM 媒體。 如果啟用此原則，而且沒有任何人以互動方式登入，則會透過網路存取 CD-ROM。  
  - **未設定**-任何人都可以存取 cd-rom。  

- **格式化及退出抽取式媒體**  
  **預設值**：系統管理員  
  CSP： [Devices_AllowedToFormatAndEjectRemovableMedia](https://go.microsoft.com/fwlink/?linkid=867920)  
 

  定義可以格式化並退出抽取式 NTFS 媒體的人員：  
  - **未設定**  
  - **系統管理員**  
  - **系統管理員與進階使用者**  
  - **系統管理員和互動式使用者**  

### <a name="interactive-logon"></a>互動式登入  

- **鎖定畫面閒置，直到螢幕保護裝置啟動的分鐘數**  
  **預設值**：*未設定*  
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_MachineInactivityLimit](https://go.microsoft.com/fwlink/?linkid=867891)  


  輸入互動式桌面登入畫面閒置，直到螢幕保護裝置啟動的最長分鐘數。 (**0** - **99999**)  

- **需要 CTRL+ALT+DEL 才能登入**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_DoNotRequireCTRLALTDEL](https://go.microsoft.com/fwlink/?linkid=867951)  


  - **啟用** - 使用者不需要按 CTRL+ALT+DEL 就能登入。  
  - **未設定** - 需要使用者按 CTRL+ALT+DEL 才能登入 Windows。  

- **智慧卡移除行為**  
  **預設值**：鎖定工作站   
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_SmartCardRemovalBehavior](https://go.microsoft.com/fwlink/?linkid=868437)  
    
  判斷從智慧卡讀卡機中移除登入使用者的智慧卡時會發生的情況。 選項包括：  

  - **鎖定工作站** - 移除智慧卡時鎖定工作站。 此選項可讓使用者離開該區域、攜帶智慧卡，並且仍然維持受保護的工作階段。  
  - **沒有動作**  
  - **強制登出** - 移除智慧卡時，使用者會自動登出。  
  - **若是遠端桌面服務工作階段則中斷連線** - 移除智慧卡會中斷工作階段的連線，但無需登出使用者。 此選項可讓使用者插入智慧卡並在稍後繼續工作階段，或在另一部配備智慧卡讀取器的電腦上，而不需要再次登入。 如果工作階段是本機，則此原則的功能與鎖定工作站相同。  

#### <a name="display"></a>顯示  

- **鎖定螢幕上的使用者資訊**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_DisplayUserInformationWhenTheSessionIsLocked](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-displayuserinformationwhenthesessionislocked)  

  設定在工作階段鎖定時顯示的使用者資訊。 如果未設定，則會顯示使用者顯示名稱、網域及使用者名稱。  

  - **未設定**  
  - **使用者顯示名稱、網域及使用者名稱**  
  - **僅使用者顯示名稱**  
  - **不顯示使用者資訊**  

- **隱藏最後登入的使用者**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_DoNotDisplayLastSignedIn](https://go.microsoft.com/fwlink/?linkid=868437)  
  
  
  - **啟用**-隱藏使用者名稱。  
  - **未設定**-顯示最後的使用者名稱。  

- **在**登入時隱藏使用者名稱 
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_DoNotDisplayUsernameAtSignIn](https://go.microsoft.com/fwlink/?linkid=867959)  

  
  - **啟用**-隱藏使用者名稱。  
  - **未設定**-顯示最後的使用者名稱。  

- **登入訊息標題**  
  **預設值**：*未設定*  
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_MessageTitleForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867964)  

  設定給登入使用者的訊息標題。  

- **登入訊息文字**  
  **預設值**：*未設定*  
  LocalPoliciesSecurityOptions CSP： [InteractiveLogon_MessageTextForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867962)  

  設定給登入使用者的訊息文字。  
  
### <a name="network-access-and-security"></a>網路存取與安全性

- **匿名存取具名管道與共用**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [NetworkAccess_RestrictAnonymousAccessToNamedPipesAndShares](https://go.microsoft.com/fwlink/?linkid=868432)  

  - **未設定** - 會限制共用和具名管道設定的匿名存取。 適用於可以匿名存取的設定。  
  - **封鎖**-停用此原則，讓匿名存取可供使用。  

- **匿名列舉 SAM 帳戶**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [NetworkAccess_DoNotAllowAnonymousEnumerationOfSAMAccounts](https://go.microsoft.com/fwlink/?linkid=868434)  
  
  - **未設定**-匿名使用者可以列舉 SAM 帳戶。  
  - **封鎖** - 防止 SAM 帳戶的匿名列舉。  

- **匿名列舉 SAM 帳戶與共用**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [NetworkAccess_DoNotAllowAnonymousEnumerationOfSamAccountsAndShares](https://go.microsoft.com/fwlink/?linkid=868435)  

  - **未設定** - 匿名使用者可以列舉網域帳戶和網路共用的名稱。  
  - **封鎖** - 防止 SAM 帳戶的匿名列舉和共用。 

- **密碼變更時儲存 LAN Manager 雜湊值**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [NetworkSecurity_DoNotStoreLANManagerHashValueOnNextPasswordChange](https://go.microsoft.com/fwlink/?linkid=868431)  
   
  判斷密碼的雜湊值是否會在下次密碼變更時儲存。 
  - **未設定**-雜湊值不會儲存  
  - **封鎖**-LAN MANAGER （LM）儲存新密碼的雜湊值。  

- **PKU2U 驗證要求**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [NetworkSecurity_AllowPKU2UAuthenticationRequests](https://go.microsoft.com/fwlink/?linkid=867892)  

  - **未設定**-允許 PU2U 要求。  
  - **封鎖**-封鎖對裝置的 PKU2U authentication 要求。  

- **限制 SAM 的遠端 RPC 連線**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [NetworkAccess_RestrictClientsAllowedToMakeRemoteCallsToSAM](https://go.microsoft.com/fwlink/?linkid=867893)  
  
  - **未設定**-使用預設的安全描述項，這可能會允許使用者和群組對 SAM 進行遠端 RPC 呼叫。
  - **允許**-拒絕使用者和群組對安全性帳戶管理員（SAM）進行遠端 RPC 呼叫，這會儲存使用者帳戶和密碼。 [**允許**] 也可讓您變更預設安全描述項定義語言（SDDL）字串，以明確允許或拒絕使用者和群組進行這些遠端呼叫。  

    - **安全性描述元**  
      **預設值**：*未設定*  
    
- **NTLM SSP 為主之用戶端的最小工作階段安全性**  
  **預設值**：無  
  LocalPoliciesSecurityOptions CSP： [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedClients](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedclients)  
  
  此安全性設定允許伺服器要求 128 位元加密和/或 NTLMv2 工作階段安全性的交涉。  

  - **無**  
  - **要求 NTLMv2 工作階段安全性**  
  - **要求 128 位元加密**  
  - **NTLMv2 和 128 位元加密**  
 
- **NTLM SSP 為主之伺服器的最小工作階段安全性**  
  **預設值**：無  
  LocalPoliciesSecurityOptions CSP： [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedServers](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedservers)  

  此安全性設定可決定用於網路登入的挑戰/回應驗證通訊協定。  

  - **無**  
  - **要求 NTLMv2 工作階段安全性**  
  - **要求 128 位元加密**  
  - **NTLMv2 和 128 位元加密**  

- **LAN Manager 驗證層級**  
  **預設值**： LM 和 NTLM  
  LocalPoliciesSecurityOptions CSP： [NetworkSecurity_LANManagerAuthenticationLevel](https://aka.ms/policy-csp-localpoliciessecurityoptions-lanmanagerauthenticationlevel)  


  - **LM 和 NTLM**  
  - **LM、NTLM 和 NTLMv2**  
  - **NTLM**  
  - **NTLMv2**  
  - **NTLMv2 而非 LM**  
  - **NTLMv2，而不是 LM 或 NTLM**  
  
- **不安全的來賓登入**  
  **預設**：未設定  
  LanmanWorkstation CSP： [LanmanWorkstation](https://aka.ms/policy-csp-lanmanworkstation-enableinsecureguestlogons)  

  如果您啟用此設定，SMB 用戶端將會拒絕不安全的來賓登入。  

  - **未設定**  
  - **封鎖**-SMB 用戶端會拒絕不安全的來賓登入。  

### <a name="recovery-console-and-shutdown"></a>修復主控台和關閉  

- **在關機時清除虛擬記憶體分頁檔**  
  **預設**：未設定  
   LocalPoliciesSecurityOptions CSP： [Shutdown_ClearVirtualMemoryPageFile](https://go.microsoft.com/fwlink/?linkid=867914)  


  - **啟用** - 在裝置關機時清除虛擬記憶體分頁檔。  
  - **未設定** - 不會清除虛擬記憶體。  

- **未登入關閉**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [Shutdown_AllowSystemToBeShutDownWithoutHavingToLogOn](https://go.microsoft.com/fwlink/?linkid=867912)  

  
  - **封鎖** - 隱藏 Windows 登入畫面上的關機選項。 使用者必須登入裝置，再關機。  
  - **未設定** - 允許使用者從 Windows 登入畫面關閉裝置。  

### <a name="user-account-control"></a>使用者帳戶控制  

- **未使用安全位置的 UIA 完整性**  
  **預設值**：尚未設定  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867897)  
  
  - **封鎖**-位於檔案系統中安全位置的應用程式，只會以 UIAccess 完整性執行。  
  - **未設定** - 讓應用程式能以 UIAccess 完整性執行，即使應用程式不在檔案系統的安全位置中也一樣。  

- **將檔案與登錄寫入失敗虛擬化到各自位置**  
  **預設值**：尚未設定  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_VirtualizeFileAndRegistryWriteFailuresToPerUserLocations](https://go.microsoft.com/fwlink/?linkid=867900)  

  - **已啟用** - 將資料寫入保護位置的應用程式會失敗。  
  - **未設定** - 應用程式寫入失敗會在執行階段重新導向至檔案系統和登入的已定義使用者位置。  

- **僅提高經簽署及驗證的可執行檔權限**  
  **預設值**：尚未設定  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867965)  

  - **已啟用** - 對可執行檔強制執行 PKI 憑證路徑驗證之後，該可執行檔才能執行。  
  - **未設定** - 不會強制執行 PKI 憑證路徑驗證，可執行檔就能執行。  

#### <a name="uia-elevation-prompt-behavior"></a>UIA 提高權限提示的行為  

- **管理員的提高權限提示**  
  **預設**：提示要求同意非 Windows 二進位檔案  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_BehaviorOfTheElevationPromptForAdministrators](https://go.microsoft.com/fwlink/?linkid=867895)  

  在管理員核准模式中定義系統管理員提高權限提示的行為。  

  - **未設定**  
  - **提高權限而不提示**  
  - **在安全桌面提示輸入認證**  
  - **提示輸入認證**  
  - **提示決定是否同意**  
  - **提示同意非 Windows 二進位檔**  


- **標準使用者的提高權限提示**  
  **預設**：提示輸入認證  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_BehaviorOfTheElevationPromptForStandardUsers](https://go.microsoft.com/fwlink/?linkid=867896)  

  定義標準使用者提高權限提示的行為。  

  - **未設定**  
  - **自動拒絕提高權限要求**  
  - **在安全桌面提示輸入認證**  
  - **提示輸入認證**  

- **將提高權限提示路由到使用者的互動式桌面**  
  **預設值**：尚未設定  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_SwitchToTheSecureDesktopWhenPromptingForElevation](https://go.microsoft.com/fwlink/?linkid=867899)  


  - [**已啟用**]-所有提高許可權的要求，以移至互動式使用者的桌面，而不是安全桌面。 系統會使用系統管理員和標準使用者的任何提示行為原則設定。  
  - **未設定** - 會強制所有提高權限要求前往安全桌面，而不論系統管理員和標準使用者的任何提示行為原則設定為何。

- **應用程式安裝的提高權限提示**  
  **預設值**：尚未設定  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_DetectApplicationInstallationsAndPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867901)  

   - **已啟用** - 不會偵測應用程式安裝套件或提示提高權限。
   - **未設定** - 若應用程式安裝套件需要較高的權限，則會提示使用者輸入系統管理使用者名稱和密碼。

- **未使用安全桌面的 UIA 提高權限提示**  
  **預設值**：尚未設定  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_AllowUIAccessApplicationsToPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867894)  

- **啟用** - 允許 UIAccess 應用程式不使用安全桌面來提示提高權限。  
- **未設定**-提高許可權提示會使用安全桌面。  

#### <a name="admin-approval-mode"></a>管理員核准模式  

- **內建的 Administrator 管理員核准模式**  
  **預設值**：尚未設定  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_UseAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867902)  

  - **已啟用** - 允許內建系統管理員帳戶使用管理員核准模式。 任何需要提高權限的作業會提示使用者核准該作業。  
  - **未設定** - 以完整管理員權限執行所有應用程式。  

- **在管理員核准模式中執行所有管理員**  
  **預設值**：尚未設定  
  LocalPoliciesSecurityOptions CSP： [UserAccountControl_RunAllAdministratorsInAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867898)  


  - [**已啟用**]-啟用管理核准模式。  
  - **未設定** - 停用管理員核准模式及所有相關 UAC 原則設定。  

### <a name="microsoft-network-client"></a>Microsoft 網路用戶端  

- **數位簽署通訊 (若伺服器同意)**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [MicrosoftNetworkClient_DigitallySignCommunicationsIfServerAgrees](https://go.microsoft.com/fwlink/?linkid=868423)  

  判斷 SMB 用戶端是否會交涉 SMB 封包簽署。  
  - **封鎖**-smb 用戶端永遠不會協調 smb 封包簽署。
  - **未設定** - Microsoft 網路用戶端會要求伺服器在工作階段設定期間執行 SMB 封包簽署。 如果在伺服器上啟用封包簽署，則會交涉封包簽署。  

- **傳送未加密的密碼給第三方 SMB 伺服器**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [MicrosoftNetworkClient_SendUnencryptedPasswordToThirdPartySMBServers](https://go.microsoft.com/fwlink/?linkid=868426)  


  - **封鎖** - 伺服器訊息區 (SMB) 重新導向程式可將純文字密碼傳送給驗證期間不支援密碼加密的非 Microsoft SMB 伺服器。  
  - **未設定**-封鎖純文字密碼的傳送。 密碼會加密。  

- **數位簽署通訊 (一律)**  
  **預設**：未設定  
  LocalPoliciesSecurityOptions CSP： [MicrosoftNetworkClient_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868425)  


  - **啟用** - Microsoft 網路用戶端不會與 Microsoft 網路伺服器通訊，除非該伺服器同意 SMB 封包簽署。  
  - **未設定**-SMB 封包簽署會在用戶端與伺服器之間進行協商。  

### <a name="microsoft-network-server"></a>Microsoft 網路伺服器  
  
- **數位簽署通訊 (若用戶端同意)**  
  **預設**：未設定  
  CSP： [MicrosoftNetworkServer_DigitallySignCommunicationsIfClientAgrees](https://go.microsoft.com/fwlink/?linkid=868429)  

  - **啟用** - Microsoft 網路伺服器會根據用戶端要求的交涉 SMB 封包簽署。 就是說，如果用戶端已啟用封包簽署，則會交涉封包簽署。  
  - **未設定**-smb 用戶端永遠不會協調 smb 封包簽署。  

- **數位簽署通訊 (一律)**  
  **預設**：未設定  
  CSP： [MicrosoftNetworkServer_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868428)  

  - **啟用** - Microsoft 網路伺服器不會與 Microsoft 網路用戶端通訊，除非該用戶端同意 SMB 封包簽署。  
  - **未設定**-SMB 封包簽署會在用戶端與伺服器之間進行協商。  

## <a name="xbox-services"></a>Xbox 服務

- **Xbox 遊戲儲存工作**  
  **預設**：未設定  
  CSP： [TaskScheduler/EnableXboxGameSaveTask](https://go.microsoft.com/fwlink/?linkid=875480)  
   
  此設定可決定是否啟用或停用 Xbox 遊戲儲存工作。  
  - **Enabled**
  - **未設定**

- **Xbox 配件管理服務**  
  **預設值**：手動  
  CSP： [SystemServices/ConfigureXboxAccessoryManagementServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875481)  

  此設定會決定 [配件管理] 服務的 [啟動類型]。  
  - **手動**
  - **自動**
  - **停用**

- **Xbox Live Auth Manager 服務**  
  **預設值**：手動  
  CSP： [SystemServices/ConfigureXboxLiveAuthManagerServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875482)  
 
  此設定會決定 Live Auth Manager 服務的啟動類型。  
  - **手動**
  - **自動**
  - **停用**
 
- **Xbox Live 遊戲儲存服務**  
  **預設值**：手動  
  CSP： [SystemServices/ConfigureXboxLiveGameSaveServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875483)  

  此設定會決定 Live 遊戲儲存服務的啟動類型。  
  - **手動**
  - **自動**
  - **停用**

- **Xbox Live 網路服務**  
  **預設值**：手動  
  CSP： [SystemServices/ConfigureXboxLiveNetworkingServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875484)  

  此設定會決定網路服務的啟動類型。  
  - **手動**
  - **自動**
  - **停用**

## <a name="next-steps"></a>後續步驟

設定檔已建立，但還不會執行任何動作。 接下來，[指派設定檔](../configuration/device-profile-assign.md)並[監視其狀態](../configuration/device-profile-monitor.md)。  

設定 [macOS](endpoint-protection-macos.md) 裝置上的 Endpoint Protection 設定。  
