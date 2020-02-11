---
title: 設定 Microsoft Intune Exchange 連接器
titleSuffix: Microsoft Intune
description: 使用內部部署 Intune Exchange 連接器，根據 Intune 註冊狀況和 Exchange ActiveSync (EAS) 來管理裝置對 Exchange 信箱的存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/24/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d00fec5efd9caa54c7f481389e3993e9797699c
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755713"
---
# <a name="set-up-the-on-premises-intune-exchange-connector"></a>安裝內部部署 Intune Exchange 連接器

為了協助保護對 Exchange 的存取，Intune 依賴一個內部部署元件，也就是 Microsoft Intune Exchange 連接器。 在 Intune 主控台的某些位置中，此連接器也稱為 *Exchange ActiveSync 內部部署連接器*。

此文章中的資訊可協助您安裝及監視 Intune Exchange 連接器。 您可以使用連接器，搭配您的[條件式存取原則](conditional-access-exchange-create.md)來允許或封鎖存取 Exchange 內部部署信箱。

連接器會在您的內部部署硬體上安裝及執行。 它會探索連線至 Exchange 的裝置，並向 Intune 服務告知裝置資訊。 連接器會依據裝置是否已註冊且合規來決定要允許或封鎖裝置。 這些通訊採用 HTTPS 通訊協定。

當裝置嘗試存取內部部署 Exchange Server 時，Exchange 連接器會將 Exchange Server 中的 Exchange Active Sync (EAS) 記錄對應到 Intune 記錄，以確保裝置已向 Intune 註冊且符合裝置原則。 系統會根據您的條件式存取原則來允許裝置存取或將它封鎖。 如需詳細資訊，請參閱[常見的 Intune 條件式存取使用方式為何？](conditional-access-intune-common-ways-use.md)

「探索」  和「允許及封鎖」  作業都是使用標準 Exchange PowerShell Cmdlet 完成的。 這些作業使用最初安裝 Exchange 交換器時所提供的服務帳戶。

Intune 支援針對每個訂閱安裝多個 Intune Exchange 連接器。 如果您有多個內部部署 Exchange 組織，則可以為每個 Exchange 組織設定個別的連接器。 不過，每個 Exchange 組織只能安裝一個連接器。  

請依照下列一般步驟，設定可讓 Intune 與內部部署 Exchange Server 通訊的連線：

1. 從 Intune 入口網站下載內部部署連接器。
2. 在內部部署 Exchange 組織中的電腦上安裝和設定 Exchange 連接器。
3. 驗證 Exchange 連線。
4. 針對您要連線到 Intune 的每個額外 Exchange 組織重複這些步驟。

## <a name="intune-exchange-connector-requirements"></a>Intune Exchange 連接器需求

若要連線至 Exchange，您需要具有 Intune 權限的帳戶，以供連接器用來連線。 當您安裝連接器時便會指定此帳戶。  

下表列出安裝 Intune Exchange 連接器時的電腦需求。  

|  需求  |   更多資訊     |
|---------------|------------------------|
|  作業系統        | 在執行任何版本的 Windows Server 2008 SP2 64 位元、Windows Server 2008 R2、Windows Server 2012、Windows Server 2012 R2 或 Windows Server 2016 的電腦上，Intune 皆支援 Intune Exchange 連接器。<br /><br />任何 Server Core 安裝都不支援此 Connector。  |
| Microsoft Exchange          | 內部部署連接器需要 Microsoft Exchange 2010 SP3 或更新版本，或是舊版 Exchange Online Dedicated。 若要判斷您的 Exchange Online Dedicated 環境為*新*或*舊版*設定，請連絡您的帳戶管理員。 |
| 行動裝置管理授權單位           | [將行動裝置管理授權單位設定為 Intune](../fundamentals/mdm-authority-set.md)。 |
| 硬體              | 安裝連接器的電腦需要 1.6 GHz CPU、2 GB RAM 和 10 GB 可用磁碟空間。 |
|  Active Directory 同步處理             | 在您使用連接器連接 Intune 和 Exchange Server 之前，請先[設定 Active Directory 同步作業](../fundamentals/users-add.md)。 您的本機使用者及安全性群組必須與您的 Azure Active Directory 執行個體進行同步處理。 |
| 其他軟體         | 裝載連接器的電腦必須具備 Microsoft .NET Framework 4.5 和 Windows PowerShell 2.0 的完整安裝。 |
| Network (網路)               | 安裝連接器的電腦所在的網域，必須與裝載 Exchange Server 的網域有信任關係。<br /><br />請設定電腦，使它能夠在連接埠 80 和 443 上，透過防火牆和 Proxy 伺服器來存取 Intune 服務。 Intune 會使用以下網域： <br> - manage.microsoft.com <br> - \*manage.microsoft.com<br> - \*.manage.microsoft.com <br><br> Intune Exchange 連接器會與下列服務通訊： <br> - Intune 服務：HTTPS 連接埠 443 <br> - Exchange Client Access Server (CAS)：WinRM 服務連接埠 443<br> - Exchange Autodiscover 443<br> - Exchange Web Services (EWS) 443  |

### <a name="exchange-cmdlet-requirements"></a>Exchange Cmdlet 需求

您必須建立 Intune Exchange 連接器的 Active Directory 使用者帳戶。 帳戶必須具有執行下列 Windows PowerShell Exchange Cmdlet 的權限：  

- `Get-ActiveSyncOrganizationSettings`、`Set-ActiveSyncOrganizationSettings`
- `Get-CasMailbox`、`Set-CasMailbox`
- `Get-ActiveSyncMailboxPolicy`、`Set-ActiveSyncMailboxPolicy`、`New-ActiveSyncMailboxPolicy`、`Remove-ActiveSyncMailboxPolicy`
- `Get-ActiveSyncDeviceAccessRule`、`Set-ActiveSyncDeviceAccessRule`、`New-ActiveSyncDeviceAccessRule`、`Remove-ActiveSyncDeviceAccessRule`
- `Get-ActiveSyncDeviceStatistics`
- `Get-ActiveSyncDevice`
- `Get-ExchangeServer`
- `Get-ActiveSyncDeviceClass`
- `Get-Recipient`
- `Clear-ActiveSyncDevice`、`Remove-ActiveSyncDevice`
- `Set-ADServerSettings`
- `Get-Command`

## <a name="download-the-installation-package"></a>下載安裝套件

在可支援 Intune Exchange 連接器的 Windows 伺服器上：

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。  使用在內部部署 Exchange Server 中擔任系統管理員，並且具備 Exchange Server 使用授權的帳戶。

2. 選取 [租用戶系統管理]   > [Exchange 存取]  。

3. 在 [設定]  下，選擇 [Exchange ActiveSync 內部部署連接器]  ，然後選取 [新增]  。

   > [!div class="mx-imgBorder"]
   > ![新增 Exchange ActiveSync 內部部署連接器](./media/exchange-connector-install/add-connector.png)

4. 在 [新增連接器]  頁面中，選取 [下載內部部署連接器]  。 Intune Exchange 連接器位於可開啟或儲存的壓縮 (.zip) 資料夾中。 在 [檔案下載]  對話方塊中，選擇 [儲存]  ，將壓縮資料夾儲存到安全的位置。

## <a name="install-and-configure-the-intune-exchange-connector"></a>安裝和設定 Intune Exchange 連接器

請依照下列步驟安裝 Intune Exchange 連接器。 如果您有多個 Exchange 組織，請針對每個您想要設定的 Exchange 連接器重複這些步驟。

1. 在 Intune Exchange 連接器支援的作業系統上，將 **Exchange_Connector_Setup.zip** 中的檔案解壓縮到安全位置。
   > [!IMPORTANT]
   > 請不要重新命名或移動 *Exchange_Connector_Setup* 資料夾內的檔案。 因為這些變更會導致連接器安裝失敗。

2. 在檔案解壓縮之後，請開啟解壓縮的資料夾，然後按兩下 **Exchange_Connector_Setup.exe** 安裝連接器。

   > [!IMPORTANT]
   > 如果目的地資料夾不是安全的位置，請在完成安裝內部部署連接器後刪除 *MicrosoftIntune.accountcert* 憑證檔案。

3. 在 [Microsoft Intune Exchange Connector]  對話方塊中，選取 [內部部署 Microsoft Exchange Server]  或 [託管 Microsoft Exchange Server]  。

   ![顯示可從何處選擇 Exchange 伺服器類型的影像](./media/exchange-connector-install/intune-sa-exchange-connector-config.png)

   如果是 On-Premises Exchange Connector，請提供主控 **Client Access Server** 角色之 Exchange 伺服器的伺服器名稱或完整網域名稱。

   如果是託管 Exchange 伺服器，請提供 Exchange 伺服器位址。 若要尋找託管 Exchange 伺服器 URL：

   1. 開啟 Office 365 的 Outlook。

   2. 選擇左上方的 **？** 圖示，然後選取 [關於]  。

   3. 找到 [POP 外部伺服器]  值。

   4. 選擇 [Proxy 伺服器]  ，以便指定託管 Exchange 伺服器的 Proxy 伺服器設定。

       1. 選取 [同步處理行動裝置資訊時使用 Proxy 伺服器]  。

       1. 輸入用來存取伺服器的 [Proxy 伺服器名稱]  和 [連接埠號碼]  。

       1. 如果需要使用者認證才能存取 Proxy 伺服器，請選取 [使用認證來連線至 Proxy 伺服器]  。 然後輸入 [網域\使用者]  和 [密碼]  。

       1. 選擇 [確定]  。

4. 在 [使用者 (網域\使用者)]  和 [密碼]  欄位中，輸入認證以連線至 Exchange Server。 您指定的帳戶必須具有授權才能使用 Intune。

5. 請提供認證以傳送通知至使用者的 Exchange Server 信箱。 此使用者可專作收發通知之用。 通知使用者需要 Exchange 信箱，才能夠透過電子郵件傳送通知。 您可以在 Intune 中使用條件式存取原則來設定這些通知。

   請確定已在 Exchange CAS 上設定自動探索服務和 Exchange Web 服務。 如需詳細資訊，請參閱 [Client Access Server](https://technet.microsoft.com/library/dd298114.aspx)。

6. 在 [密碼]  欄位中提供此帳戶的密碼，以便 Intune 能夠存取 Exchange Server。

   > [!NOTE]
   > 您用來登入租用戶的帳戶必須至少是 Intune 服務管理員。 如果沒有此管理員帳戶，連線將會失敗並顯示「遠端伺服器傳回一個錯誤:(400) 不正確的要求。」

7. 選擇 [連線]  。

   > [!NOTE]
   > 設定連線可能需要幾分鐘的時間。

在設定期間，Exchange 連接器會儲存 Proxy 設定，讓您可存取網際網路。 如果您的 Proxy 設定發生變更，請重新設定 Exchange Connector，以便將更新的 Proxy 設定套用到 Exchange Connector。

在 Exchange 連接器設定連線之後，與受 Exchange 管理的使用者建立關聯的行動裝置便會自動同步處理並新增到 Exchange 連接器。 這項同步處理可能需要一些時間才能完成。

> [!NOTE]
> 如果您安裝 Intune Exchange 連接器，而且稍後需要刪除 Exchange 連線，您必須從安裝 Intune Exchange 連接器的電腦解除安裝連接器。

## <a name="install-connectors-for-multiple-exchange-organizations"></a>為多個 Exchange 組織安裝連接器

Intune 支援每個訂閱可以有多個 Intune Exchange 連接器。 針對具有多個 Exchange 組織的租用戶，您只能為每個 Exchange 組織設定一個連接器。

若要安裝連接器以連線到多個 Exchange 組織，請下載 .zip 資料夾一次。 然後針對您安裝的每個連接器重複使用該相同的下載。 針對每個額外的連接器，請遵循上一節中的步驟將安裝程式解壓縮，並在 Exchange 組織中的伺服器上執行。

每個連線到 Intune 的 Exchange 組織都支援高可用性、監視和手動同步功能。下列各節會說明這些功能。

## <a name="on-premises-intune-exchange-connector-high-availability-support"></a>內部部署 Intune Exchange 連接器高可用性支援  

針對內部部署連接器，高可用性表示如果連接器所使用的 Exchange CAS 變成無法使用，連接器可以切換為使用該 Exchange 組織中其他的 CAS。 Exchange 連接器本身不支援高可用性。 如果連接器失敗，則不會進行自動容錯移轉，因此您必須[安裝新的連接器](#reinstall-the-intune-exchange-connector)來取代失敗的連接器。

為進行容錯移轉，連接器會使用指定的 CAS 建立與 Exchange 的連線。 然後它就會探索該 Exchange 組織的其他 CAS。 此探索可讓連接器容錯移轉到另一個 CAS (如果有的話)，直到有可用的主要 CAS 為止。

預設不會啟用其他 CAS 的探索。 如果您需要關閉容錯移轉：

1. 在安裝 Exchange 連接器的伺服器上，移至 **%*ProgramData*%\Microsoft\Windows Intune Exchange Connector**。

2. 使用文字編輯器，開啟 **OnPremisesExchangeConnectorServiceConfiguration.xml**。

3. 將 **\<IsCasFailoverEnabled>*true*\</IsCasFailoverEnabled>** 變更為 **\<IsCasFailoverEnabled>*false*\</IsCasFailoverEnabled>** 。

## <a name="performance-tune-the-exchange-connector-optional"></a>Exchange 連接器的效能調整 (選用)

當 Exchange ActiveSync 支援 5,000 部以上的裝置時，您可以設定選用設定來改善連接器的效能。 您可以啟用 Exchange 以使用 PowerShell 命令執行空間的多個執行個體，進而提升效能。

在您進行此變更之前，請確認您用來執行 Exchange Connector 的帳戶並未用於其他 Exchange 管理用途。 Exchange 帳戶的執行空間數量有限，其中大部分將由連接器使用。

效能調整不適用於在較舊或較慢硬體上執行的連接器。

若要提升 Exchange 連接器效能：

1. 在安裝連接器的伺服器上開啟連接器的安裝目錄。  預設位置為 *C:\ProgramData\Microsoft\Windows Intune Exchange Connector*。

2. 編輯 *OnPremisesExchangeConnectorServiceConfiguration.xml* 檔案。

3. 找出 **EnableParallelCommandSupport** 並將值設定為 **true**：

   \<EnableParallelCommandSupport>true\</EnableParallelCommandSupport>

4. 儲存檔案，然後重新啟動 Microsoft Intune Exchange Connector 服務。

## <a name="reinstall-the-intune-exchange-connector"></a>重新安裝 Intune Exchange 連接器

您可能需要重新安裝 Intune Exchange 連接器。 由於只能有一個連接器連線到每個 Exchange 組織，因此如果您為組織安裝第二個連接器，您所安裝的新連接器就會取代原來的連接器。

1. 若要安裝新的連接器，請依照[安裝和設定 Exchange 連接器](#install-and-configure-the-intune-exchange-connector)一節中的步驟進行。

2. 出現提示時，選取 [取代]  以安裝新的連接器。
   ![取代連接器的設定警告](./media/exchange-connector-install/prompt-to-replace.png)

3. 繼續進行[安裝和設定 Exchange 連接器](#install-and-configure-the-intune-exchange-connector)一節中的步驟，並再次登入 Intune。

4. 在最後一個視窗中，選取 [關閉]  以完成安裝。
   ![完成設定](./media/exchange-connector-install/successful-reinstall.png)

## <a name="monitor-an-exchange-connector"></a>監視 Exchange Connector

順利設定 Exchange 連接器之後，您可以檢視連線狀態與上次成功的同步處理嘗試：

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [租用戶系統管理]   > [Exchange 存取]  。

3. 選取 [Exchange ActiveSync 內部部署連接器]  ，然後選取您要檢視的連接器。

4. 主控台會顯示您選取之連接器的詳細資料，您可以在其中檢視 [狀態]  以及上次成功同步處理的日期和時間。

除了主控台內狀態以外，您還可以使用[適用於 Exchange 連接器和 Intune 的 System Center Operations Manager 管理組件](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True) \(英文\)。 管理組件可在您需要針對問題進行疑難排解時，為您提供不同方式來監視 Exchange 連接器。

## <a name="manually-force-a-quick-sync-or-full-sync"></a>手動強制執行快速同步處理或完整同步處理

Intune Exchange 連接器會定期自動同步處理 EAS 和 Intune 的裝置記錄。 如果裝置的合規性狀態變更，自動同步程序會定期更新記錄，以便封鎖或允許裝置存取。

- **快速同步處理**會定期執行，一天進行數次。 快速同步處理會針對 Intune 授權的使用者，和以內部部署 Exchange 條件式存取為目標且自上次同步處理之後已有所變更的使用者，擷取裝置資訊。

- **完整同步處理**預設每天將執行一次。 完整同步處理會針對所有 Intune 授權的使用者和以內部部署 Exchange 條件式存取為目標的使用者，擷取裝置資訊。 完整同步處理還會擷取 Exchange Server 資訊，並確保 Intune 在 Azure 入口網站中指定的設定已在 Exchange Server 上更新。

您可以透過使用 Intune 儀表板上的 [快速同步處理]  或 [完整同步處理]  選項，強制連接器執行同步處理：

   1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

   2. 選取 [租用戶系統管理]   > [Exchange 存取]   >  [Exchange ActiveSync 內部部署連接器]  。

   3. 選取您要同步處理的連接器，然後選擇 [快速同步處理] 或 [完整同步處理]。

   > [!div class="mx-imgBorder"]
   > ![連接器詳細資料的範例螢幕擷取畫面](./media/exchange-connector-install/connector-details.png)

## <a name="next-steps"></a>後續步驟

建立[內部部署 Exchange Server 的條件式存取原則](conditional-access-exchange-create.md)。
