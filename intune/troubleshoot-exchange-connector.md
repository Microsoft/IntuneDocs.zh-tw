---
title: 針對 Exchange Connector 進行疑難排解 | Microsoft Intune
description: 針對與 Intune On-Premises Exchange Connector 相關的問題進行疑難排解。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 89611dd197c968df43cac6006d3982fe5f1ec5c2
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57232636"
---
# <a name="troubleshoot-the-intune-on-premises-exchange-connector"></a>針對 Intune On-Premises Exchange Connector 進行疑難排解

本文描述如何針對與 Intune On-Premises Exchange Connector 相關的問題進行疑難排解。

## <a name="steps-for-checking-the-connector-configuration"></a>檢查連接器設定的步驟 

檢查 [Intune On-Premises Exchange Connector 設定](exchange-connector-install.md)，確定已正確設定連接器。 以下是一些常見問題。 進行任何修正之後，請查看是否已解決問題。

 - 在 [Microsoft Intune Exchange Connector] 對話方塊中，確定已指定具有適當權限的使用者帳戶執行[必要的 Windows PowerShell Exchange Cmdlet](exchange-connector-install.md#exchange-cmdlet-requirements)。
- 啟用通知並指定通知帳戶。
 - 設定 Exchange Connector 時，指定的用戶端存取伺服器 (CAS) 要盡可能靠近裝載 Exchange Connector 的伺服器。 CAS 與 Exchange Connector 之間的通訊延遲，可能會延遲裝置探索，尤其是在使用 Exchange Online Dedicated 時。
 - 新註冊裝置的使用者在取得存取權時，可能會因 Exchange Connector 與 Exchange CAS 同步而延遲。 完整同步會一天執行一次，而差異 (快速) 同步則會一天執行多次。  您可以[手動強制執行快速同步或完整同步](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync)將延遲降到最低。
 
## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>無法從 Exchange 探索 Exchange ActiveSync 裝置
[監視 Exchange Connector 活動](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support)，以查看 Exchange Connector 是否正在與 Exchange Server 同步。 如果自裝置加入之後已順利完成完整同步或快速同步，您可以如下所列檢查是否有其他可能的問題。 如果尚未進行任何同步，請收集同步記錄，並附加到支援要求。

 - 確定使用者具有 Intune 授權，否則 Exchange Connector 將不會探索他們的裝置。
 - 如果使用者的主要 SMTP 位址和其在 Azure Active Directory (Azure AD) 中的 UPN 不同，Exchange Connector 將無法探索該使用者的任何裝置。 修正主要 SMTP 位址以解決問題。
 - 如果您的環境中同時有 Exchange 2010 和 Exchange 2013 信箱伺服器，建議將 Exchange Connector 指向 Exchange 2013 CAS。 否則，如果 Exchange Connector 設定為與 Exchange 2010 CAS 通訊，Exchange Connector 將無法探索任何 Exchange 2013 使用者裝置。 
- 在 Exchange Online Dedicated 環境中，您必須在初始設定時將 Exchange Connector 指向專用環境中的 Exchange 2013 CAS (而非 Exchange 2010 CAS)，因為在執行 Powershell Cmdlet 時，該連接器只會與此 CAS 通訊。


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>使用 Powershell 取得 Exchange Connector 問題的更多資料
- 若要取得信箱所有行動裝置的清單，可使用 Get-ActiveSyncDeviceStatistics -mailbox mbx
- 若要取得信箱 SMTP 位址的清單，可使用 Get-Mailbox -Identity user | select emailaddresses | fl
- 若要取得有關裝置存取狀態的詳細資訊，可使用 Get-CASMailbox <upn> | fl

### <a name="next-steps"></a>後續步驟
如果這項資訊對您沒有幫助，您也可以[取得 Microsoft Intune 支援](get-support.md)。
