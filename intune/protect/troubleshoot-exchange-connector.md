---
title: Exchange Connector 疑難排解
titleSuffix: Microsoft Intune
description: 針對與 Intune On-Premises Exchange Connector 相關的問題進行疑難排解。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 962e66a9fdf6d8abcf6855f645775026ee4db850
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72508849"
---
# <a name="troubleshoot-the-intune-exchange-connector"></a>為 Intune Exchange Connector 進行疑難排解

本文描述如何針對與 Intune Exchange Connector 相關的問題進行疑難排解。

## <a name="before-you-start"></a>在您開始使用 Intune 之前

在您開始針對 Intune 中的 Exchange Connector 問題進行疑難排解之前，請先收集一些基本資訊，讓您能夠使用穩固的基礎。 這種方法可協助您更瞭解問題的本質，並更快速地解決問題。

- 確認您的處理常式符合安裝需求。 請參閱[安裝內部部署 Intune Exchange 連接器](exchange-connector-install.md)。
- 確認您的帳戶同時具有 Exchange 和 Intune 管理員的許可權。
- 請注意完整和確切的錯誤訊息正文、詳細資料，以及訊息的顯示位置。
- 判斷問題何時開始： 
  - 您是第一次設定連接器嗎？ 
  - 連接器是否正常運作，然後失敗？
  - 如果運作正常，Intune 環境、Exchange 環境或執行連接器軟體的電腦上發生哪些變更？
- 什麼是 MDM 授權單位？ 如果 System Center Configuration Manager，您會使用哪個版本的 Configuration Manager？
- 您使用哪一版的 Exchange？

### <a name="use-powershell-to-get-more-data-on-exchange-connector-issues"></a>使用 PowerShell 取得 Exchange Connector 問題的更多資料

- 若要取得信箱的所有行動裝置清單，請使用 `Get-ActiveSyncDeviceStatistics -mailbox mbx`
- 若要取得信箱的 SMTP 地址清單，請使用 `Get-Mailbox -Identity user | select emailaddresses | fl`
- 若要取得有關裝置存取狀態的詳細資訊，請使用 `Get-CASMailbox <upn> | fl`

## <a name="review-the-connector-configuration"></a>檢查連接器設定

請檢查內部[部署 Exchange connector 需求](exchange-connector-install.md#intune-exchange-connector-requirements)，以確定您的環境和連接器已正確設定。 

### <a name="general-considerations-for-the-connector"></a>連接器的一般考慮

- 請確定您的防火牆和 proxy 伺服器允許在裝載 Intune Exchange Connector 和 Intune 服務的伺服器之間進行通訊。

- 裝載 Intune Exchange Connector 和 Exchange Client Access Server （CAS）的電腦應已加入網域且位於相同的 LAN 上。 請確定已針對 Intune Exchange connector 所使用的帳戶新增必要的許可權。

- 通知帳戶用來取出*自動*探索設定。 如需有關在 Exchange 中 Autodisover 的詳細資訊，請參閱[Exchange Server 中的自動探索服務](https://docs.microsoft.com/exchange/architecture/client-access/autodiscover?view=exchserver-2016)。

- Intune Exchange Connector 會使用通知帳號憑證，將要求傳送至 EWS URL，並將通知電子郵件訊息連同 [*開始*使用] 連結（在 Intune 中註冊）。 Android 非 Knox 裝置的需求是使用 [*開始*使用] 連結進行註冊。 否則，條件式存取將會封鎖這些裝置。

### <a name="common-issues-for-connector-configurations"></a>連接器設定的常見問題

- **帳戶權限**：在 [Microsoft Intune Exchange Connector] 對話方塊中，確定已指定具有適當權限的使用者帳戶執行[必要的 Windows PowerShell Exchange Cmdlet](exchange-connector-install.md#exchange-cmdlet-requirements)。
- **通知電子郵件訊息**：啟用通知並指定通知帳戶。
- **用戶端存取伺服器同步**處理：設定 Exchange connector 時，請指定對裝載 Exchange connector 的伺服器具有最低網路延遲的 ca。 CAS 與 Exchange Connector 之間的通訊延遲，可能會延遲裝置探索，尤其是在使用 Exchange Online Dedicated 時。
- **同步處理排程**：新註冊裝置的使用者在取得存取權時，可能會因 Exchange Connector 與 Exchange CAS 同步處理而延遲。 完整同步會一天執行一次，而差異 (快速) 同步則會一天執行多次。 您可以[手動強制執行快速同步或完整同步](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync)將延遲降到最低。

## <a name="next-steps"></a>後續步驟
下列文章可協助解決常見的問題和特定錯誤：

- [解決 Intune Exchange Connector 的常見問題](troubleshoot-exchange-connector-common-problems.md)。
- [解決 Intune Exchange Connector 的常見錯誤](troubleshoot-exchange-connector-common-errors.md)。

尋求支援或 Intune 社區的協助：

- 請參閱[取得支援](../fundamentals/get-support.md)以使用 Intune 主控台來協助疑難排解問題，或向 Microsoft 開啟支援案例。 
- 在[Microsoft Intune 論壇](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)中張貼您的問題。  
