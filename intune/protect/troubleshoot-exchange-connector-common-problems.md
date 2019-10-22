---
title: 針對 Intune Exchange connector 的常見問題進行疑難排解
titleSuffix: Microsoft Intune
description: 針對內部部署 Microsoft Intune Exchange connector 的常見問題進行疑難排解並加以解決。
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9542212e1b75d97c96c024eed20e20e610e2b5d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503641"
---
# <a name="resolve-common-problems-with-the-intune-exchange-connector"></a>解決 Intune Exchange connector 的常見問題
 
本文可協助 Intune 管理員解決 Intune Exchange connector 操作的常見問題。  

開始進行疑難排解之前，請先參閱針對[Intune 內部部署 Exchange connector 進行疑難排解](troubleshoot-exchange-connector.md)，以取得連接器的基本資訊。 另請參閱連接器設定的常見問題。 

## <a name="an-exchange-activesync-device-isnt-discovered-from-exchange"></a>無法從 Exchange 探索 Exchange ActiveSync 裝置

當 exchange ActiveSync 裝置不是從 Exchange 探索時，請[監視 exchange connector 活動](exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support)，以查看 exchange connector 是否正在與 exchange server 進行同步處理。 如果裝置加入後未進行同步處理，請收集同步處理記錄，並將它們附加至支援要求。 如果自裝置加入後已順利完成完整同步或快速同步處理，請檢查下列問題： 

- 請確定使用者具有 Intune 授權。 如果沒有，Exchange connector 將不會探索他們的裝置。  

- 如果使用者的主要 SMTP 位址和其在 Azure Active Directory (Azure AD) 中的使用者主體名稱 (UPN) 不同，Exchange Connector 將無法探索該使用者的任何裝置。 修正主要 SMTP 位址以解決問題。  

- 如果您的環境中同時有 Exchange 2010 和 Exchange 2013 信箱伺服器，建議將 Exchange Connector 指向 Exchange 2013 CAS (Client Access Server)。 如果 Exchange Connector 設定為與 Exchange 2010 CAS 通訊，Exchange Connector 將不會探索任何 Exchange 2013 使用者裝置。  

- 針對 Exchange Online 專用環境，在初始設定期間，您必須將 Exchange connector 指向專用環境中的 Exchange 2013 CA （而非 Exchange 2010 CA）。 只有在執行 PowerShell Cmdlet 時，連接器才會與 Exchange 2013 CA 通訊。  


## <a name="problems-with-the-notification-email-message"></a>通知電子郵件訊息的問題  

若要在未執行 Android Knox 的裝置上支援內部部署信箱的條件式存取，請確定 Intune 註冊是從 Intune Exchange connector 所傳送的「立即開始使用」電子郵件訊息開始。 從訊息開始註冊可確保裝置會在所有平臺（Exchange、Azure AD、Intune）之間收到唯一的 ActiveSyncID。  

使用者可能不會收到通知電子郵件訊息，因為：  

- 通知帳戶設定錯誤。
- 通知帳戶的自動探索失敗。
- 傳送電子郵件訊息的 Exchange Web 服務（EWS）要求失敗。

請參閱下列各節，以疑難排解電子郵件通知問題。

### <a name="check-the-notification-account-that-retrieves-autodiscover-settings"></a>檢查會抓取自動探索設定的通知帳戶
1. 請確定已在 Exchange 用戶端存取服務上設定自動探索服務和 EWS。 如需詳細資訊，請參閱[Exchange Server 中](https://docs.microsoft.com/Exchange/architecture/client-access/autodiscover?view=exchserver-2019)的[用戶端存取服務](https://docs.microsoft.com/Exchange/architecture/client-access/client-access)和自動探索服務。


2. 確認您的通知帳戶符合下列需求：

   - 此帳戶具有由您的 Exchange 內部部署伺服器主控的作用中信箱。  

   - 帳戶 UPN 符合 SMTP 位址。

3. 自動探索需要 DNS 伺服器，其具有指向您 Exchange Client Access server 的**Autodiscover.SMTPdomain.com** （例如 Autodiscover.contoso.com）的 dns 記錄。 若要檢查記錄，請指定您的 FQDN 來取代*Autodiscover.SMTPdomain.com* ，並遵循下列步驟：

   1. 在命令提示字元中，輸入*NSLOOKUP*。  

   2. 輸入*Autodiscover.SMTPdomain.com*。 輸出應該類似下圖：  
      ![Nslookup 結果 ](./media/troubleshoot-exchange-connector-common-problems/nslookup-results.png
)

   您也可以在 https://testconnectivity.microsoft.com 從網際網路測試自動探索服務。 或者，使用 Microsoft Connectivity Analyzer 工具，從本機網域進行測試。 如需詳細資訊，請參閱[Microsoft Connectivity Analyzer 工具](https://docs.microsoft.com/en-us/previous-versions/office/exchange-remote-connectivity/jj851141(v=exchg.80))。 如有必要，請[下載 Microsoft Connectivity Analyzer 工具](https://go.microsoft.com/fwlink/?LinkID=313782)。


### <a name="check-autodiscovery"></a>檢查自動搜索  

如果自動探索失敗，請嘗試下列步驟：
1. [設定有效的自動探索 DNS 記錄](https://docs.microsoft.com/previous-versions/exchange-server/exchange-150/mt473798(v=exchg.150))。 

2. 在 Intune Exchange connector 設定檔中將 EWS URL 硬式編碼：

   1. 決定 EWS URL。 Exchange 的預設 EWS URL 是 `https://<mailServerFQDN>/ews/exchange.asmx` 的，但您的 URL 可能不同。 請洽詢 Exchange 系統管理員，為您的環境驗證正確的 URL。

   2. 編輯 *OnPremisesExchangeConnectorServiceConfiguration.xml* 檔案。 根據預設，此檔案位於執行 Exchange connector 之電腦上的 *%ProgramData%\Microsoft\Windows Intune Exchange Connector* 。 在文字編輯器中開啟檔案，然後變更下列這一行，以反映您環境的 EWS URL： `<ExchangeWebServiceURL> https://<YourExchangeHOST>/EWS/Exchange.asmx</ExchangeWebServiceURL>`
    

3. 儲存檔案，然後重新啟動電腦或 Microsoft Intune Exchange Connector 服務。

>[!NOTE]
> 在此設定中，Intune Exchange connector 會停止使用自動探索，而改為直接連接到 EWS URL。

## <a name="next-steps"></a>後續步驟  

如需特定錯誤的說明，請嘗試[解決 Intune Exchange connector 的常見錯誤](troubleshoot-exchange-connector-common-errors.md)。

若要取得支援，或從 Intune 社區取得協助：
- 請參閱[取得支援](../fundamentals/get-support.md)以使用 Intune 主控台進行問題的疑難排解，或向 Microsoft 開啟支援案例。 
- 在[Microsoft Intune 論壇](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)中張貼您的問題。  
