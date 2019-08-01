---
title: 設定 Microsoft Intune 內部部署 Exchange 連接器
titleSuffix: Microsoft Intune
description: 使用內部部署 Exchange 連接器，根據 Intune 註冊狀況和 Exchange Active Sync (EAS) 來管理裝置對 Exchange 信箱的存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5cf6299f46ed8db4fdca02947ce15a920816d110
ms.sourcegitcommit: c715c93bb242f4fe44bbdf2fd585909854ed72b6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68660951"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune"></a>在 Microsoft Intune 中設定 Intune 內部部署 Exchange 連接器
本文中資訊可協助您安裝適用於 Intune 的 Exchange Active Sync 內部部署連接器，並在安裝後進行監視。  您可以使用 Intune 內部部署 Exchange 連接器，搭配您的[條件式存取原則來允許或封鎖存取 Exchange 內部部署信箱](conditional-access-exchange-create.md)。 

當裝置嘗試存取內部部署 Exchange 時，Exchange 連接器會將 Exchange Server 中的 Exchange Active Sync (EAS) 記錄對應到 Intune 記錄，以檢查裝置是否已向 Intune 註冊且符合裝置合規性政策的規範。 根據您的條件式存取原則來允許存取或封鎖裝置。 如需詳細資訊，請參閱[搭配 Intune 使用條件式存取的常見方式為何？](conditional-access-intune-common-ways-use.md)

Intune 支援針對每個訂閱安裝多個內部部署 Exchange 連接器。 如果您有多個內部部署 Exchange 組織，則可以為每個 Exchange 組織設定個別的連接器。 不過，每個 Exchange 組織只能安裝要使用的一個連接器。 

下列是讓 Intune 與內部部署 Exchange Server 通訊之連線設定的一般步驟：

1. 從 Intune 入口網站下載 Intune 內部部署 Exchange 連接器。
2. 在內部部署 Exchange 組織中的電腦上安裝和設定 Exchange 連接器。
3. 驗證 Exchange 連線。
4. 針對您要連線到 Intune 的每個額外 Exchange 組織重複這些步驟。

## <a name="intune-on-premises-exchange-connector-requirements"></a>Intune 內部部署 Exchange 連接器需求
您需要具有 Intune 權限的帳戶，以供連接器用來連線到 Exchange。 當您安裝連接器時便會指定此帳戶。  

下表列出安裝內部部署 Exchange 連接器之電腦的需求。  

|  需求  |   詳細資訊     |
|---------------|------------------------|
|  作業系統        | 在執行任何版本的 Windows Server 2008 SP2 64 位元、Windows Server 2008 R2、Windows Server 2012、Windows Server 2012 R2 或 Windows Server 2016 的電腦上，Intune 皆支援內部部署 Exchange 連接器。<br /><br />任何 Server Core 安裝都不支援此 Connector。  |
| Microsoft Exchange          | 內部部署連接器需要 Microsoft Exchange 2010 SP3 或更新版本，或是舊版 Exchange Online Dedicated。 若要判斷您的 Exchange Online Dedicated 環境為<strong>新</strong>或<strong>舊版</strong>設定，請連絡您的帳戶管理員。 |
| 行動裝置管理授權單位           | [將行動裝置管理授權單位設定為 Intune](mdm-authority-set.md)。 |
| 硬體              | 安裝連接器的電腦需要 1.6 GHz CPU、2 GB RAM 和 10 GB 可用磁碟空間。 |
|  Active Directory 同步處理             | 您必須[設定 Active Directory 同步處理](users-add.md)，以便將本機使用者和安全性群組與您的 Azure Active Directory 執行個體同步處理，才能使用連接器將 Intune 連線到您的 Exchange Server。 |
| 其他軟體         | 託管連接器的電腦必須安裝 Microsoft .NET Framework 4.5 和 Windows PowerShell 2.0 的完整安裝。 |
| Network (網路)               | 安裝連接器的電腦所在的網域，必須與託管 Exchange Server 的網域有信任關係。<br /><br />電腦需要設定，使其能夠在連接埠 80 和 443 上，透過防火牆和 Proxy 伺服器來存取 Intune 服務。 Intune 使用的網域包括 manage.microsoft.com、&#42;manage.microsoft.com 和 &#42;.manage.microsoft.com。 |

### <a name="exchange-cmdlet-requirements"></a>Exchange Cmdlet 需求

建立內部部署 Exchange 連接器將使用的 Active Directory 使用者帳戶。 帳戶必須具有執行下列必要 Windows PowerShell Exchange Cmdlet 的權限：


- Get-ActiveSyncOrganizationSettings、Set-ActiveSyncOrganizationSettings
- Get-CasMailbox、Set-CasMailbox
- Get-ActiveSyncMailboxPolicy、Set-ActiveSyncMailboxPolicy、New-ActiveSyncMailboxPolicy、Remove-ActiveSyncMailboxPolicy
- Get-ActiveSyncDeviceAccessRule、Set-ActiveSyncDeviceAccessRule、New-ActiveSyncDeviceAccessRule、Remove-ActiveSyncDeviceAccessRule
- Get-ActiveSyncDeviceStatistics
- Get-ActiveSyncDevice
- Get-ExchangeServer
- Get-ActiveSyncDeviceClass
- Get-Recipient
- Clear-ActiveSyncDevice、Remove-ActiveSyncDevice
- Set-ADServerSettings
- Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>下載內部部署 Exchange 連接器軟體安裝套件

1. 在內部部署 Exchange 連接器支援的 Windows Server 作業系統上，開啟 [Azure 入口網站](https://portal.azure.com)，並使用在內部部署 Exchange Server 中為系統管理員且有權使用 Exchange Server 的使用者帳戶登入。

2. 移至 [Intune]   > [Exchange 存取]   

3. 在 [設定]  下，選擇 [Exchange ActiveSync 內部部署連接器]  ，然後選取 [新增]  。

4. 在 [新增連接器]  頁面中，選取 [下載內部部署連接器]  。 內部部署 Exchange Connector 位於可開啟或儲存的壓縮 (.zip) 資料夾中。 在 [檔案下載]  對話方塊中，選擇 [儲存]  ，將壓縮資料夾儲存到安全的位置。

    > [!IMPORTANT]
    > 請不要重新命名或移動內部部署 Exchange 連接器資料夾內的檔案。 移動或重新命名資料夾的內容會造成 Exchange 連接器安裝失敗。

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>安裝和設定 Intune 內部部署 Exchange 連接器
請執行下列步驟來安裝 Intune 內部部署 Exchange 連接器。 如果您有多個 Exchange 組織，請針對每個您想要設定的其他 Exchange 連接器重複這些步驟。

1. 在內部部署 Exchange 連接器支援的作業系統上，將 **Exchange_Connector_Setup.zip** 中的檔案解壓縮到安全位置。

2. 在檔案解壓縮之後，請開啟解壓縮的資料夾，然後按兩下 **Exchange_Connector_Setup.exe** 安裝內部部署 Exchange 連接器。

   > [!IMPORTANT]
   > 如果目的地資料夾不是安全的位置，您應該在完成安裝內部部署連接器後刪除 **MicrosoftIntune.accountcert** 憑證檔案。

3. 在 [Microsoft Intune Exchange Connector]  對話方塊中，選取 [內部部署 Microsoft Exchange Server]  或 [託管 Microsoft Exchange Server]  。

   ![顯示可從何處選擇 Exchange 伺服器類型的影像](./media/intune-sa-exchange-connector-config.png)

   如果是 On-Premises Exchange Connector，請提供主控 **Client Access Server** 角色之 Exchange 伺服器的伺服器名稱或完整網域名稱。

   如果是託管 Exchange 伺服器，請提供 Exchange 伺服器位址。 若要尋找託管 Exchange 伺服器 URL：

   1. 開啟 Office 365 的 Outlook 網頁版。

   2. 選擇左上方的 **？** 圖示，然後選取 [關於]  。

   3. 找到 [POP 外部伺服器]  值。

   4. 選擇 [Proxy 伺服器]  ，以便指定託管 Exchange 伺服器的 Proxy 伺服器設定。
       1. 選取 [同步處理行動裝置資訊時使用 Proxy 伺服器]  。

       2. 輸入用來存取伺服器的 [Proxy 伺服器名稱]  和 [連接埠號碼]  。

       3. 如果需要提供使用者認證才能存取 Proxy 伺服器，請選取 [使用認證來連線至 Proxy 伺服器]  。 然後輸入 [網域\使用者]  和 [密碼]  。

       4. 選擇 [確定]  。

4. 在 [使用者 (網域\使用者)]  和 [密碼]  欄位中，輸入連線至 Exchange Server 所需的認證。 您指定的帳戶必須具有授權才能使用 Intune。 

5. 提供傳送通知給使用者 Exchange Server 信箱所需的認證。 此使用者可專作收發通知之用。 通知使用者需要 Exchange 信箱，才能夠透過電子郵件傳送通知。 您可以在 Intune 中使用條件式存取原則來設定這些通知。  

   請確定自動探索服務和 Exchange Web 服務是在 Exchange Client Access Server 上設定。 如需詳細資訊，請參閱 [Client Access Server](https://technet.microsoft.com/library/dd298114.aspx)。

6. 在 [密碼]  欄位中提供此帳戶的密碼，以便 Intune 能夠存取 Exchange Server。

7. 選擇 [連線]  。

   > [!NOTE]
   > 設定連線可能需要幾分鐘的時間。

在設定期間，Exchange 連接器會儲存 Proxy 設定，讓您可存取網際網路。 如果您的 Proxy 設定發生變更，您必須重新設定 Exchange Connector，以便將更新的 Proxy 設定套用到 Exchange Connector。

在 Exchange 連接器設定連線之後，與 Exchange 中受控使用者建立關聯的行動裝置便會自動同步處理並新增到 Exchange 連接器。 此同步處理可能需要一些時間才能完成。

> [!NOTE]
> 如果您已安裝內部部署 Exchange 連接器，而且在某個階段刪除 Exchange 連線，您必須從已安裝內部部署 Exchange 連接器的電腦解除安裝該軟體。



## <a name="install-connectors-for-multiple-exchange-organizations"></a>為多個 Exchange 組織安裝連接器
Intune 支援每個訂閱有多個內部部署 Exchange 連接器。 針對具有多個 Exchange 組織的租用戶，您可以為每個 Exchange 組織設定一個連接器，但任何一個組織只能使用一個連接器。 

如果您要安裝連接器以連線到多個 Exchange 組織，請下載 .zip 資料夾一次，然後針對您所安裝每個連接器重複使用該相同的下載。 針對每個額外的連接器，請遵循上一節中的步驟將安裝程式解壓縮，並在 Exchange 組織中的伺服器上執行。

每個連線到 Intune 的 Exchange 組織都支援下列各節所述高可用性、監視和手動同步功能。

## <a name="on-premises-exchange-connector-high-availability-support"></a>內部部署 Exchange Connector 高可用性支援 
內部部署 Exchange 連接器的高可用性表示，如果連接器所使用的 Exchange Client Access Server (CAS) 變成無法使用，連接器可以切換為使用該 Exchange 組織中的不同 CAS。 Exchange 連接器本身不支援高可用性。 如果連接器失敗，則不會進行自動容錯移轉，因此您必須[安裝新的連接器](#reinstall-the-on-premises-exchange-connector)來取代該連接器。 

為了完成容錯移轉，在連接器使用所指定 CAS 建立與 Exchange 的連線之後，連接器會探索該 Exchange 組織中是否有其他 CAS。 掌握其他 CAS 資訊可讓連接器容錯移轉到另一個 CAS (如果有的話)，直到有可用的主要 CAS 為止。 預設不會啟用其他 CAS 的探索。 您可以使用下列程序來關閉容錯移轉：  
1. 在安裝 Exchange 連接器的伺服器上，移至 %*ProgramData*%\Microsoft\Windows Intune Exchange Connector。 
2. 使用文字編輯器，開啟 **OnPremisesExchangeConnectorServiceConfiguration.xml**。
3. 將 &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; 變更為 &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; 以停用該功能。  
 
## <a name="optional-performance-tuning-for-the-exchange-connector"></a>Exchange Connector 的選用效能調整  

當您透過 Exchange ActiveSync 支援 5,000 部以上的裝置時，您可以設定選用設定來改善連接器的效能。 藉由啟用 Exchange 以使用 PowerShell 命令執行空間的多個執行個體，可達到更高的效能。 

在您進行此變更之前，請確認您用來執行 Exchange Connector 的帳戶並未用於其他 Exchange 管理用途。 這是因為 Exchange 每個帳戶有受限的執行空間的限制，其中大部分都將由連接器使用。 

這種效能變更不適用於在較舊或較慢硬體上執行的連接器。  

1. 在安裝連接器的伺服器上開啟連接器安裝目錄。  預設位置為 *C:\ProgramData\Microsoft\Windows Intune Exchange Connector*。 
2. 編輯 *OnPremisesExchangeConnectorServiceConfiguration.xml* 檔案。
3. 找出 **EnableParallelCommandSupport** 並將值設定為 **true**：  
     
   \<EnableParallelCommandSupport>true\</EnableParallelCommandSupport>
4. 儲存檔案，然後重新啟動 Microsoft Intune Exchange Connector 服務。

## <a name="reinstall-the-on-premises-exchange-connector"></a>重新安裝內部部署 Exchange 連接器
您可能需要重新安裝 Exchange 連接器。 由於支援將單一連接器連線到每個 Exchange 組織，因此如果您為組織安裝第二個連接器，您所安裝的新連接器就會取代原始連接器。

1. 使用[安裝和設定 Intune 內部部署 Exchange 連接器](#install-and-configure-the-intune-on-premises-exchange-connector)中的步驟，來開始安裝新的連接器。 
2. 出現提示時，選取 [取代]  以安裝新的連接器。  
   ![取代連接器的設定提示](./media/exchange-connector-install/prompt-to-replace.png)

3. 繼續使用上一個程序中的步驟，然後重新登入 Intune。
4. 當您看到最後一個畫面時，選取 [關閉]  以完成安裝。  
   ![完成設定](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-the-exchange-connector-activity"></a>監視 Exchange Connector 活動

順利設定 Exchange 連接器之後，即可檢視連線和上次成功同步處理嘗試的狀態。 若要驗證 Exchange 連接器的連線：

1. 在 Intune 儀表板中，選擇 [Exchange 存取]  。
2. 選取 [Exchange 內部部署存取]  來驗證每個 Exchange 連接器的連線狀態。

您也可以查看上次嘗試同步作業成功的時間和日期。
--> 

### <a name="system-center-operations-manager-management-pack"></a>System Center Operations Manager 管理組件

從 Intune 1710 版開始，您可以使用[適用於 Exchange Connector 和 Intune 的 Operations Manager 管理組件](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True)。 使用管理組件可在您需要針對問題進行疑難排解時，為您提供不同方式來監視 Exchange 連接器。

## <a name="manually-force-a-quick-sync-or-full-sync"></a>手動強制執行快速同步處理或完整同步處理
內部部署 Exchange Connector 會定期自動同步處理 EAS 和 Intune 的裝置記錄。 如果裝置的合規性狀態變更，自動同步程序會定期更新記錄，以便封鎖或允許裝置存取。

- **快速同步處理**會定期執行，一天進行數次。 快速同步處理會針對上次同步處理後已變更之 Intune 授權的使用者和以內部部署 Exchange 條件式存取為目標的使用者，擷取裝置資訊。

- **完整同步處理**預設每天將執行一次。 完整同步處理會針對所有 Intune 授權的使用者和以內部部署 Exchange 條件式存取為目標的使用者，擷取裝置資訊。 完整同步處理還會擷取 Exchange Server 資訊，並確保 Intune 在 Azure 入口網站中指定的設定已在 Exchange Server 上更新。 


您可以執行下列步驟，藉由在 Intune 儀表板中使用 [快速同步處理]  或 [完整同步處理]  選項，強制連接器執行同步處理：

   1. 在 Intune 儀表板中，選擇 [Exchange 存取]  。
   2. 選取 [Exchange 內部部署存取]  。
   3. 選取您想要同步處理的連接器，然後選擇 [快速同步處理]  或 [完整同步處理]  。

## <a name="next-steps"></a>後續步驟
[為 Exchange 內部部署建立條件式存取原則](conditional-access-exchange-create.md)
