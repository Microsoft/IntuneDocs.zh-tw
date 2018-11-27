---
title: 設定 Microsoft Intune 內部部署 Exchange 連接器
titleSuffix: ''
description: 使用內部部署 Exchange 連接器，根據 Intune 註冊狀況和 Exchange Active Sync (EAS) 來管理裝置對 Exchange 信箱的存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 019f09444f96d8bb3bca046ef5be20af373a3bff
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183702"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>在 Microsoft Intune Azure 中設定 Intune 內部部署 Exchange 連接器

在內部部署 Exchange Server 環境中，Intune 條件式存取可以用來允許或封鎖存取 Exchange 內部部署信箱。 請使用 Exchange Active Sync 內部部署連接器，將 Intune 連線到您的 Exchange 組織，並設定 Intune 條件式存取以及裝置合規性政策。 然後，當裝置試圖連線到 Exchange 時，Intune 會判斷裝置是否已在 Intune 中註冊且符合規範。 為了判斷哪些裝置已在 Intune 中註冊，內部部署 Exchange 連接器會將 Exchange Server 中的 Exchange Active Sync (EAS) 記錄對應到 Intune 記錄。 如需其運作方式的詳細資訊，請參閱[常見的 Intune 條件式存取使用方式為何？](conditional-access-intune-common-ways-use.md)

> [!IMPORTANT]
> Intune 現在支援每個訂閱有多個內部部署 Exchange 連接器。 如果您有多個內部部署 Exchange 組織，則可以為每個 Exchange 組織設定個別的連接器。

若要設定可讓 Microsoft Intune 與內部部署 Exchange Server 通訊的連線，一般步驟如下：

1.  從 Azure 入口網站下載 Intune 內部部署 Exchange連接器。
2.  在內部部署 Exchange 組織中的電腦上安裝和設定 Exchange 連接器。
3.  驗證 Exchange 連線。
4. 針對每個您想要連線至 Intune 的 Exchange 組織重複這些步驟。

## <a name="intune-on-premises-exchange-connector-requirements"></a>Intune 內部部署 Exchange 連接器需求
下表列出安裝內部部署 Exchange 連接器之電腦的需求。


|            需求             |                                                                                                                                                                                                        詳細資訊                                                                                                                                                                                                        |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         作業系統          |                                                               在執行任何版本的 Windows Server 2008 SP2 64 位元、Windows Server 2008 R2、Windows Server 2012、Windows Server 2012 R2 或 Windows Server 2016 的電腦上，Intune 皆支援內部部署 Exchange 連接器。<br /><br />任何 Server Core 安裝都不支援此連接器。                                                                |
|         Microsoft Exchange         |                                                                           內部部署連接器需要 Microsoft Exchange 2010 SP3 或更新版本，或是舊版 Exchange Online Dedicated。 若要判斷您的 Exchange Online Dedicated 環境為<strong>新</strong>或<strong>舊版</strong>設定，請連絡您的帳戶管理員。                                                                           |
| 行動裝置管理授權單位 |                                                                                                                              [將行動裝置管理授權單位設定為 Intune](https://docs.microsoft.com/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-mdm-authority-set)。                                                                                                                               |
|              硬體              |                                                                                                                                                     安裝連接器的電腦需要 1.6 GHz CPU、2 GB RAM 和 10 GB 可用磁碟空間。                                                                                                                                                      |
|  Active Directory 同步處理  |                                                                                      您必須[設定 Active Directory 同步處理](users-add.md)，以便將本機使用者和安全性群組與您的 Azure Active Directory 執行個體同步處理，才能使用連接器將 Intune 連線到您的 Exchange Server。                                                                                      |
|        其他軟體         |                                                                                                                                           託管連接器的電腦必須安裝 Microsoft .NET Framework 4.5 和 Windows PowerShell 2.0 的完整安裝。                                                                                                                                           |
|              Network (網路)               | 安裝連接器的電腦所在的網域，必須與託管 Exchange Server 的網域有信任關係。<br /><br />電腦需要設定，使其能夠在連接埠 80 和 443 上，透過防火牆和 Proxy 伺服器來存取 Intune 服務。 Intune 使用的網域包括 manage.microsoft.com、&#42;manage.microsoft.com 和 &#42;.manage.microsoft.com。 |

### <a name="exchange-cmdlet-requirements"></a>Exchange Cmdlet 需求

您必須建立內部部署 Exchange 連接器所使用的 Active Directory 使用者帳戶。 帳戶必須具有執行下列必要 Windows PowerShell Exchange Cmdlet 的權限：


 -   Get-ActiveSyncOrganizationSettings、Set-ActiveSyncOrganizationSettings
 -   Get-CasMailbox、Set-CasMailbox
 -   Get-ActiveSyncMailboxPolicy、Set-ActiveSyncMailboxPolicy、New-ActiveSyncMailboxPolicy、Remove-ActiveSyncMailboxPolicy
 -   Get-ActiveSyncDeviceAccessRule、Set-ActiveSyncDeviceAccessRule、New-ActiveSyncDeviceAccessRule、Remove-ActiveSyncDeviceAccessRule
 -   Get-ActiveSyncDeviceStatistics
 -   Get-ActiveSyncDevice
 -   Get-ExchangeServer
 -   Get-ActiveSyncDeviceClass
 -   Get-Recipient
 -   Clear-ActiveSyncDevice、Remove-ActiveSyncDevice
 -   Set-ADServerSettings
 -   Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>下載內部部署 Exchange 連接器軟體安裝套件

1. 在內部部署 Exchange 連接器支援的 Windows Server 作業系統上，開啟 [Azure 入口網站](http://portal.azure.com)，並使用在內部部署 Exchange Server 中為系統管理員且有權使用 Exchange Server 的使用者帳戶登入。

2. 選擇左功能表中的 [All services] (所有服務)，然後在文字方塊篩選中鍵入 **Intune**。

3. 選擇 [Intune]，在在開啟 Intune 儀表板後，選擇 [內部部署存取]。

4. 在 [安裝] 下選擇 [Exchange ActiveSync 連接器]，然後選擇 [下載內部部署連接器]。

5.  內部部署 Exchange 連接器包含在可以開啟或儲存的壓縮 (.zip) 資料夾中。 在 [檔案下載] 對話方塊中，選擇 [儲存]，將壓縮資料夾儲存到安全的位置。

    > [!IMPORTANT]
    > 請不要重新命名或移動內部部署 Exchange 連接器資料夾內的檔案。 移動或重新命名資料夾的內容會造成 Exchange 連接器安裝失敗。

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>安裝和設定 Intune 內部部署 Exchange 連接器
請執行下列步驟來安裝 Intune 內部部署 Exchange 連接器。 如果您有多個 Exchange 組織，請針對每個您想要設定的其他 Exchange 連接器重複這些步驟。

1. 在內部部署 Exchange 連接器支援的作業系統上，將 **Exchange_Connector_Setup.zip** 中的檔案解壓縮到安全位置。

2. 在檔案解壓縮之後，請開啟解壓縮的資料夾，然後按兩下 **Exchange_Connector_Setup.exe** 安裝內部部署 Exchange 連接器。

   > [!IMPORTANT]
   > 如果目的地資料夾不是安全的位置，您應該在完成安裝內部部署連接器後刪除 **MicrosoftIntune.accountcert** 憑證檔案。

3. 在 [Microsoft Intune Exchange Connector] 對話方塊中，選取 [內部部署 Microsoft Exchange Server] 或 [託管 Microsoft Exchange Server]。

   ![顯示可從何處選擇 Exchange 伺服器類型的影像](./media/intune-sa-exchange-connector-config.png)

   如果是內部部署 Exchange Server，請提供主控 **Client Access Server** 角色之 Exchange Server 的伺服器名稱或完整網域名稱。

   如果是託管 Exchange 伺服器，請提供 Exchange 伺服器位址。 若要尋找託管 Exchange 伺服器 URL：

   1. 開啟 Office 365 的 Outlook 網頁版。

   2. 選擇左上方的 **？** 圖示，然後選取 [關於]。

   3. 找到 [POP 外部伺服器]  值。

   4. 選擇 [Proxy 伺服器]，以便指定託管 Exchange 伺服器的 Proxy 伺服器設定。
       1. 選取 [同步處理行動裝置資訊時使用 Proxy 伺服器] 。

       2. 輸入用來存取伺服器的 [Proxy 伺服器名稱]  和 [連接埠號碼]  。

       3. 如果需要提供使用者認證才能存取 Proxy 伺服器，請選取 [使用認證來連線至 Proxy 伺服器]。 然後輸入 [網域\使用者] 和 [密碼]。

       4. 選擇 [確定]。

   5. 在 [使用者 (網域\使用者)] 和 [密碼] 欄位中，輸入連線至 Exchange Server 所需的認證。

   6.  提供傳送通知給使用者 Exchange Server 信箱所需的認證。 此使用者可專作收發通知之用。 通知使用者需要 Exchange 信箱，才能夠透過電子郵件傳送通知。 您可以在 Intune 中使用條件式存取原則來設定這些通知。  

       請確定自動探索服務和 Exchange Web 服務是在 Exchange Client Access Server 上設定。 如需詳細資訊，請參閱 [Client Access Server](https://technet.microsoft.com/library/dd298114.aspx)。

   7.  在 [密碼] 欄位中提供此帳戶的密碼，以便 Intune 能夠存取 Exchange Server。

   8. 選擇 [連線]。

   > [!NOTE]
   > 設定連線可能需要幾分鐘的時間。

在設定期間，Exchange 連接器會儲存 Proxy 設定，讓您可存取網際網路。 如果您的 Proxy 設定發生變更，您必須重新設定 Exchange 連接器，以便將更新的 Proxy 設定套用到 Exchange 連接器。

在 Exchange 連接器設定連線之後，與 Exchange 中受控使用者建立關聯的行動裝置便會自動同步處理並新增到 Exchange 連接器。 這項同步處理可能需要一些時間才能完成。

> [!NOTE]
> 如果您已安裝內部部署 Exchange 連接器，而且在某個階段刪除 Exchange 連線，您必須從已安裝內部部署 Exchange 連接器的電腦解除安裝該軟體。

## <a name="install-connectors-for-multiple-exchange-organizations"></a>為多個 Exchange 組織安裝連接器
Intune 支援每個訂閱有多個內部部署 Exchange 連接器。 對於具有多個 Exchange 組織的租用戶，您可以為每個 Exchange 組織設定一個連接器。 下載 .zip 資料夾一次，然後針對每個 Exchange 組織遵循前一節中的步驟，擷取安裝程式並在組織中的伺服器上執行。

每個連線至 Intune 的 Exchange 組織都支援下列各節所述的高可用性、監視和手動同步處理。

## <a name="on-premises-exchange-connector-high-availability-support"></a>內部部署 Exchange Connector 高可用性支援 
在 Exchange Connector 使用指定的 CAS 建立與 Exchange 的連線之後，連接器便能夠探索其他 CAS。 如果無法使用主要的 CAS，連接器將容錯移轉至另一個 CAS (如果有的話)，直到有可用的主要 CAS 為止。 這項功能預設為開啟。 您可以使用下列程序來關閉此功能：
1. 在安裝 Exchange Connector 的伺服器上，移至 %*ProgramData*%\Microsoft\Windows Intune Exchange Connector。 
2. 使用文字編輯器，開啟 **OnPremisesExchangeConnectorServiceConfiguration.xml**。
3. 將 &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; 變更為 &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; 以停用該功能。    


## <a name="monitor-the-exchange-connector-activity"></a>監視 Exchange Connector 活動

成功設定 Exchange 連接器之後，即可檢視連線和上次成功同步處理嘗試的狀態。 驗證 Exchange 連接器連線：

1. 在 Intune 儀表板中，選擇 [內部部署存取]。
2. 在 [安裝] 下，選取 [Exchange ActiveSync 連接器] 來確認每個 Exchange 連接器的連線狀態。

您也可以查看上次嘗試同步作業成功的時間和日期。

### <a name="system-center-operations-manager-scom-management-pack"></a>System Center Operations Manager (SCOM) 管理組件

從 Intune 1710 版開始，您可以使用[適用於 Exchange connector 和 Intune 的 SCOM 管理組件](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True)。 這可在您需要針對問題進行疑難排解時，為您提供不同方式來監視 Exchange Connector。

## <a name="manually-force-a-quick-sync-or-full-sync"></a>手動強制執行快速同步處理或完整同步處理
內部部署 Exchange 連接器會定期自動同步處理 EAS 和 Intune 的裝置記錄。 如果裝置的合規性狀態變更時，自動同步處理程序會定期更新記錄，讓裝置存取可以據以封鎖或允許。

   - **快速同步處理**會定期執行，一天進行數次。 快速同步處理會針對上次同步處理後已變更之 Intune 授權的使用者和以內部部署 Exchange 條件式存取為目標的使用者，擷取裝置資訊。

   - **完整同步處理**預設每天將執行一次。 完整同步處理會針對所有 Intune 授權的使用者和以內部部署 Exchange 條件式存取為目標的使用者，擷取裝置資訊。 完整同步處理還會擷取 Exchange Server 資訊，並確保 Intune 在 Azure 入口網站中指定的設定已在 Exchange Server 上更新。 

您可以執行下列步驟，藉由在 Intune 儀表板中使用 [快速同步處理] 或 [完整同步處理] 選項，強制連接器執行同步處理：

   1. 在 Intune 儀表板中，選擇 [內部部署存取]。
   2. 在 [安裝] 下，選擇 [Exchange Active Sync 連接器]。
   3. 選取您想要同步處理的連接器，然後選擇 [快速同步處理] 或 [完整同步處理]。

## <a name="next-steps"></a>接下來的步驟
[建立 Exchange 內部部署的條件存取原則](conditional-access-exchange-create.md)
