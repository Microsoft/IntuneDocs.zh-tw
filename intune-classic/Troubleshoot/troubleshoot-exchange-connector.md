---
title: Exchange Connector 疑難排解
description: 與 Intune Exchange Connector 相關的疑難排解問題。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/26/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c5cb5465-fd8e-4524-83b9-ccdf3393b6dc
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0eef4e2ae3792c601bd4a32cd041d7d041091cca
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31015025"
---
# <a name="troubleshoot-the-exchange-connector"></a>為 Exchange Connector 進行疑難排解

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

本主題描述如何針對可能與 Intune Exchange Connector 相關的問題進行疑難排解。

## <a name="steps-for-checking-the-connector-configuration"></a>檢查 Connector 設定的步驟 

檢查 Exchange Connector 的設定，然後查看是否已將問題解決。

- 請務必在初始設定 Exchange Connector 時，指定通知帳戶。
- Exchange Connector 服務帳戶必須具有適當的權限，才能執行 Exchange Connector 所使用的 PowerShell Cmdlet。
- 設定 Exchange Connector 時，指定的用戶端存取伺服器 (CAS) 要儘可能靠近裝載 Exchange Connector 的伺服器。 CAS 與 Exchange Connector 之間的通訊延遲，可能會導致裝置探索延遲，尤其是在使用 O365 專用時。
- 請注意 Exchange Connector 同步處理與 Exchange CAS 之間，在時間上會有延遲。 完整同步處理會一天執行一次，而差異 (快速) 同步處理則是每兩小時執行一次。 使用新註冊裝置的使用者進行存取時，很可能會遇到延遲。
- 
  ## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>無法從 Exchange 探索 Exchange ActiveSync 裝置
  檢查 Exchange Connector 是否正在與 Exchange Server 進行同步處理。 若要這樣做，請找出完整同步處理或差異同步處理的記錄檔。請參閱＜Exchange Connector 記錄檔＞。 如果自裝置加入之後已順利完成完整同步處理或差異同步處理，這就不會是問題來源。 如果尚未進行任何同步處理，請收集同步處理記錄檔，並附加到您的支援要求中。

- 如果使用者沒有 Intune 授權，Exchange Connector 將不會探索他們的裝置。
- 如果使用者的主要 SMTP 位址和他們在 AAD 中的 UPN 不同，Exchange Connector 將無法探索該 Intune/AAD 使用者的任何裝置。 修正主要 SMTP 位址。
- 如果 Exchange Connector 在探索期間與之通訊的 CAS 是 Exchange 2010 CAS，而您同時有 Exchange 2010 和 2013 信箱伺服器，Exchange Connector 將無法探索任何 Exchange 2013 使用者的裝置。 若要解決這個問題，請將 Exchange Connector 設定為指向 Exchange 2013 CAS。  雖然這個問題主要和 O365 專用拓撲有關，但我們仍建議您最好指向其他拓撲中的 Exchange 2013 CAS。
- 在 Exchange 專用 (O365 專用) 環境中，您必須在初始設定時將 Exchange Connector 指向專用環境中的 Exchange 2013 (而非 2010) CAS，因為在執行 Powershell Cmdlet 時，它只會與此 CAS 通訊。


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>使用 Powershell 取得 Exchange Connector 問題的更多資料
- 若要取得信箱所有行動裝置的清單，可使用 Get-ActiveSyncDeviceStatistics -mailbox mbx
- 若要取得信箱 SMTP 位址的清單，可使用 Get-Mailbox -Identity user | select emailaddresses | fl。
- 若要取得有關裝置存取狀態的詳細資訊，可使用 Get-CASMailbox <upn> | fl

### <a name="next-steps"></a>接下來的步驟
如果此疑難排解資訊對您沒有幫助，請連絡 Microsoft 支援服務 (如[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)中所述)。
