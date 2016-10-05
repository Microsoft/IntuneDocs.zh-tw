---
title: "適用於內部部署 EAS 的 Exchange Connector | Microsoft Intune"
description: "使用 Connector 工具啟用 Intune 管理主控台和內部部署 Exchange Server 之間的通訊，以進行 Exchange ActiveSync MDM。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 41ff4212-a6f5-4374-8731-631f7560cff1
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: 07ed8c922d53169839bba50547f56bbc979d58ac


---

# 安裝 Intune On-Premises Exchange Connector


若要設定連線，讓 Microsoft Intune 能夠與主控行動裝置信箱的 Exchange Server 通訊，您必須從 Intune 管理主控台下載並設定 On-Premises Connector 工具。 Intune 僅支援每個訂用帳戶一個任一種類的 Exchange Connector 連線。

## 適用於 On-Premises Connector 的需求
下表列出安裝 On-Premises Exchange Connector 之電腦的需求。

|需求|詳細資訊|
|---------------|--------------------|
|作業系統|在執行任何版本的 Windows Server 2008 SP2 64 位元、Windows Server 2008 R2、Windows Server 2012 或 Windows Server 2012 R2 的電腦上，Intune 支援 On-Premises Exchange Connector。<br /><br />任何 Server Core 安裝都不支援此連接器。|
|Microsoft Exchange 版本|On-Premises Connector 需要 Microsoft Exchange 2010 SP1 或更新版本，或是舊版 Exchange Online Dedicated。 若要判斷您的 Exchange Online Dedicated 環境為**新**或**舊版**設定，請連絡您的帳戶管理員。|
|行動裝置管理授權單位| [將行動裝置管理授權單位設定為 Intune](prerequisites-for-enrollment.md#set-mobile-device-management-authority)。|
|硬體|安裝連接器的電腦至少需配備 1.6 GHz CPU、2 GB RAM 和 10 GB 可用硬碟空間的硬體。|
|設定 Active Directory 同步處理。|使用其中任一 Connector 將 Intune 連線到您的 Exchange Server 之前，您必須先[設定 Active Directory 同步處理](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3)，以便將本機使用者和安全性群組與您的 Azure Active Directory 執行個體同步處理。|
|其他軟體|託管連接器的電腦必須安裝 Microsoft .NET Framework 4 和 Windows PowerShell 2.0 的完整安裝。|
|Network (網路)|安裝連接器的電腦所在的網域，必須與託管 Exchange Server 的網域有信任關係。<br /><br />電腦需要設定，使其能夠在連接埠 80 和 443 上，透過防火牆和 Proxy 伺服器來存取 Intune 服務。 Intune 使用的網域包括 manage.microsoft.com、&#42;manage.microsoft.com 和 &#42;.manage.microsoft.com。|
|已設定並執行託管 Exchange|如需詳細資訊，請參閱 [Exchange Server 2016](https://technet.microsoft.com/library/mt170645.aspx)。 |

### Exchange Cmdlet 需求

您必須建立 Intune Exchange Connector 所使用的 Active Directory 使用者帳戶。 帳戶必須具有執行下列必要 Windows PowerShell Exchange Cmdlet 的權限：


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

## 下載 On-Premises Exchange Connector 軟體安裝套件

1. 在內部部署 Exchange Connector 支援的 Windows Server 作業系統上，利用使用者帳戶開啟 [Microsoft Intune 管理主控台](http://manage.microsoft.com) (http://manage.microsoft.com)，這個使用者帳戶是 Exchange 租用戶中具有使用 Exchange Server 之授權的系統管理員。
![開啟設定 Exchange 連線](../media/ExchangeConnector.gif)

2.  在工作區捷徑窗格中，選擇 [系統管理]，選擇 [行動裝置管理]  >  [Microsoft Exchange]，然後選擇 [設定 Exchange 連線]。

3.  在 [設定 Exchange 連線] 頁面上，選擇 [下載 On-Premises Connector]。

4.  On-Premises Exchange Connector 包含在可以開啟或儲存的壓縮 (.zip) 資料夾中。 在 [檔案下載] 對話方塊中，選擇 [儲存]，將壓縮資料夾儲存到安全的位置。

> [!IMPORTANT]
> 請不要重新命名或移動 On-Premises Exchange Connector 資料夾內的檔案。 移動或重新命名資料夾的內容將會中斷安裝。

## 安裝和設定 Intune On-Premises Exchange Connector
請執行下列步驟來安裝 Intune On-Premises Exchange Connector。 每個 Intune 訂閱只可安裝 On-Premises Exchange Connector 一次，而且只可安裝在一部電腦上。 如果您嘗試設定另一個 On-Premises Exchange Connector，則新連線會取代原始連線。

1.  在 On-Premises Connector 支援的作業系統上，將 **Exchange_Connector_Setup.zip** 中的檔案解壓縮到安全位置。

2.  在檔案解壓縮之後，請開啟解壓縮的資料夾，然後按兩下 **Exchange_Connector_Setup.exe** 安裝 On-Premises Exchange Connector。

    > [!IMPORTANT]
    > 如果目標資料夾不是安全的位置，您應該在安裝 On-Premises Connector 之後刪除 **WindowsIntune.accountcert** 憑證檔案。

3.  在 [Exchange Server] 欄位中，選取您的 Exchange 伺服器環境類型是 [內部部署 Microsoft Exchange Server] 或 [託管 Microsoft Exchange Server]。

  ![選擇 Exchange Server 類型](../media/IntuneSA1dconfigureExchConnector.png)

  如果是 On-Premises Exchange Connector，請提供主控 **Client Access Server** 角色之 Exchange 伺服器的伺服器名稱或完整網域名稱。

  如果是託管 Exchange 伺服器，請提供 Exchange 伺服器位址。 若要尋找託管 Exchange 伺服器 URL：

      1.  開啟適用於 Office 365 的 Outlook Web App。

      2.  選擇左上方的 “?” 圖示，然後選取 [關於] 。

      3.  找到 [POP 外部伺服器]  值。

      4.  選擇 [Proxy 伺服器]，以便指定託管 Exchange 伺服器的 Proxy 伺服器設定。
        1.  選取 [同步處理行動裝置資訊時使用 Proxy 伺服器] 。

        2.  輸入用來存取伺服器的 [Proxy 伺服器名稱]  和 [連接埠號碼]  。

        3.  如果需要提供使用者認證才能存取 Proxy 伺服器，請選取 [使用認證連線到 Proxy 伺服器]，然後輸入**網域\使用者**和**密碼**。

        4.  選擇 [確定]。

5.  提供連線至 Exchange 伺服器所需的認證、「使用者 (網域\使用者)」和「密碼」。

6.  提供傳送通知給使用者 Exchange 信箱所需的系統管理認證。 這些通知可使用 Intune 透過條件性存取原則來設定。

    請確定自動探索服務和 Exchange Web 服務是在 Exchange Client Access Server 上設定。 如需詳細資訊，請參閱 [Client Access Server](https://technet.microsoft.com/library/dd298114.aspx)。

7.  在 [密碼] 欄位中提供此帳戶的密碼，以便 Intune 能夠存取 Exchange Server。

8. 選擇 [連線]。

    設定連線可能需要幾分鐘的時間。

在設定期間，Exchange Connector 會儲存 Proxy 設定，讓您可存取網際網路。 如果您的 Proxy 設定發生變更，您必須重新設定 Exchange Connector，以便將更新的 Proxy 設定套用到 Exchange Connector。

在 Exchange Connector 設定連線之後，與 Exchange Connector 中受管理使用者相關聯的行動裝置便會自動同步處理並新增到 Exchange Connector。 這項同步作業可能需要一些時間才能完成。

> [!NOTE]
> 如果您已安裝 On-Premises Exchange Connector，而且在某個階段刪除 Exchange 連線，您必須從已安裝 On-Premises Exchange Connector 的電腦解除安裝該軟體。

## 驗證 Exchange 連線

順利設定 Exchange Connector 之後，即可檢視連線和上次成功同步處理嘗試的狀態。 在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，選擇 [管理] 工作區，然後在 [行動裝置管理] 下方選擇 [Microsoft Exchange]，並確認您提供的詳細資料是否出現在 [Exchange 連線資訊] 下方。


您也可以查看上次嘗試同步作業成功的時間和日期。



<!--HONumber=Sep16_HO4-->


