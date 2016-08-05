---
title: "條件式存取的疑難排解 | Microsoft Intune"
description: "您的使用者無法透過 Intune 條件式存取取得資源的存取權時該怎麼辦。"
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 433fc32c-ca9c-4bad-9616-852c72faf996
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9915b275101e287498217c4f35e1c0e56d2425c2
ms.openlocfilehash: f5feb4d660693344cf7df38402f14c60007284b4


---

# 條件式存取的疑難排解

一般而言，使用者嘗試存取電子郵件或 SharePoint，並收到註冊的提示。 該提示會將使用者引導至公司入口網站。

本主題說明您的使用者無法透過 Intune 條件式存取取得資源的存取權時該怎麼辦。


## 成功進行條件式存取的基本概念

為了讓條件式存取能運作，您需要下列條件︰

-   裝置必須由 Intune 管理
-   裝置必須向 Azure Active Directory (AAD) 註冊。 在正常情況下，此註冊會在 Intune 註冊期間自動進行
-   裝置必須符合裝置和裝置使用者的 Intune 相容性原則規定。  如果沒有相容性原則，進行 Intune 註冊即可。
-   如果使用者透過裝置的原生郵件用戶端而不是透過 Outlook 來擷取郵件的話，則必須在裝置上啟用 Exchange ActiveSync。     這在 iOS、Windows Phone 及 Android/KNOX 裝置都會自動進行。
-   您的 Intune Exchange Connector 應該會正確設定。 如需詳細資訊，請參閱[為 Microsoft Intune 中的 Exchange Connector 進行疑難排解](troubleshoot-exchange-connector.md)。

在 Azure 管理入口網站和裝置清查報表中，可以檢視每個裝置的這些狀況。

## 註冊問題

 -  裝置未註冊，因此註冊可以解決此問題。
 -  使用者已註冊裝置，但無法加入工作地點。 使用者應該從公司入口網站更新註冊。

## 相容性問題

 -  裝置不符合 Intune 原則。 常見的問題是加密與密碼的需求。 使用者會被重新導向到公司入口網站，在這裡他們可以設定其裝置，讓它相容。
 -  可能需要一些時間，來註冊裝置的相容性資訊。 請稍候幾分鐘，然後再試一次。
 -  對於 iOS 裝置：
     -   使用者建立的現有電子郵件設定檔會封鎖 Intune 系統管理員所建立設定檔的部署作業。 這是常見的問題，因為 iOS 使用者通常會建立電子郵件設定檔，然後註冊。 公司入口網站會通知使用者，他們因為手動設定電子郵件設定檔而不相容，並且會提示使用者移除該設定檔。使用者應該移除其電子郵件設定檔，以便可以部署 Intune 設定檔。 若要避免問題，請指示使用者進行註冊，而不要安裝電子郵件設定檔，並允許 Intune 部署設定檔。
     -   iOS 裝置可能會卡在檢查相容性狀態，造成使用者無法起始另一個簽入。 重新啟動公司入口網站可能會解決這個問題，而相容性狀態會反映出 Intune 中的裝置狀態。 從裝置同步作業中收集所有資料之後，相容性檢查會快速完成，平均不用半秒的時間。

        一般而言，裝置一直處於此狀態的原因，是因為裝置無法連線到服務，或是同步處理花費很長的時間。  如果問題在不同的網路組態 (行動數據，Wi-Fi、VPN) 持續發生，請將裝置重新啟動，並在確認裝置上的 SSP 處於最新狀態之後，依照[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)所述來連絡 Microsoft 支援服務。

## 原則問題

當您建立相容性原則，並將它連結至電子郵件原則時，這兩個原則都必須部署給相同的使用者，因此請小心規劃哪些原則部署給哪些群組。 只有套用一個原則的使用者可能會發現他們的裝置不相容。


## Exchange ActiveSync 問題

### 相容的 Android 裝置收到隔離通知
- 已註冊且相容的 Android 裝置在嘗試存取公司資源時，可能仍然會出現隔離通知。 選擇 [開始] 連結之前，使用者應該確定當他們嘗試存取資源時未開啟公司入口網站。 使用者應該關閉公司入口網站，請重試存取資源，然後選擇 [開始] 連結。

### 已淘汰的裝置可以繼續存取。
- 使用 Exchange Online 時，已淘汰的裝置可能在淘汰之後數小時內仍可繼續存取。 這是因為 Exchange 會快取存取權限長達 6 小時。 在此案例中，請考慮其他方法來保護已淘汰裝置上的資料。

### 裝置相容並已向 AAD 註冊，但仍遭到封鎖
- 有時候，將 Exchange ActiveSync 識別碼 (EASID) 佈建至 AAD 會有所延遲。 此問題的常見原因是節流處理，因此請稍候幾分鐘，然後再試一次。

### 裝置遭到封鎖

裝置可能是遭到條件式存取封鎖，而沒有收到啟用電子郵件。

- 是否有預設的 Exchange 規則會將裝置隔離或封鎖？ 如果預設規則將裝置封鎖或隔離，裝置即無法從 Exchange Connector 收到啟用電子郵件。 這是預設設計。
- 通知帳戶是否依照基本組態中所述適當地設定？
- 裝置是否在 Intune 管理主控台中顯示為 Exchange ActiveSync 裝置？ 如果沒有，可能是該裝置探索失敗，Exchange Connector 同步處理問題可能是起因。 請參閱＜無法從 Exchange 探索 Exchange ActiveSync 裝置＞。
- 檢查 Exchange Connector 記錄檔中的 sendemail 活動，並檢查是否有錯誤。 所要搜尋命令的範例是從通知帳戶至 useremail 的 SendEmail。
- Exchange Connector 封鎖裝置之前，它會傳送啟用電子郵件。 如果裝置已離線，它可能不會收到啟用電子郵件。 檢查裝置的電子郵件用戶端是否使用推送來擷取電子郵件，而不是輪詢，因為這也會造成使用者遺漏電子郵件。 切換到輪詢後，再查看裝置是否收到電子郵件。

## 未封鎖不相容的裝置

如果您遇到不相容但可以繼續存取的裝置，請採取下列步驟。

- 檢閱您的目標和排除群組。 如果使用者不在正確的目標群組，或不在排除群組中，即不會遭到封鎖。 只會檢查目標群組中使用者的裝置相容性。
- 確定已探索到該裝置。 Exchange Connector 指向 Exchange 2010 CAS，但使用者卻在 Exchange 2013 伺服器上？ 在此情況下，如果預設 Exchange 規則為 [允許]，即使是目標群組中的使用者，Intune 仍無法知道該裝置的 Exchange 連線。
- 檢查 Exchange 中的裝置存在/存取狀態︰
    - 使用這個 PowerShell Cmdlet，取得信箱的所有行動裝置清單："Get-ActiveSyncDeviceStatistics -mailbox mbx'。 如果裝置未列在其中，表示它並未存取 Exchange。
    - 如果列出該裝置，請使用 Get-CASmailbox -identity:’upn’ | fl Cmdlet，取得其存取狀態的詳細資訊，並將該資訊提供給 Microsoft 支援服務。

## 提出支援票證之前
如果這些疑難排解程序都不能解決問題，可能會要求您將像是 OWA 信箱記錄檔或 Exchange Connector 記錄檔的資訊，提供給 Microsoft 支援服務。

### 收集 OWA 信箱記錄

1. 透過 OWA 登入，並在右上角中選擇您的名稱旁邊的設定 (齒輪) 符號。
2. 選擇 [選項]。
3. 在左邊資料行中選擇 [電話] (可能是 [行動裝置])。
4. 從頂端功能表中，選擇 [行動裝置]。
5. 從清單中選擇您的裝置，然後選擇 [開始記錄]。
6. 出現提示時，在快顯對話方塊上選擇 [是]。
7. 執行造成問題的動作，以便重現問題。
8. 等候 1-2 分鐘，然後返回 OWA 中的電話清單。 請確定已在清單中選取您的電話，然後從頂端功能表中選擇 [擷取記錄]。
9. 您應會收到您自己所寄的電子郵件與附件。 當您提出支援票證時，請向 Microsoft 支援提供電子郵件的內容。

### Exchange Connector 記錄檔

#### 一般記錄檔資訊
若要檢視 Exchange Connector 記錄檔，使用 [伺服器追蹤檢視器工具](https://msdn.microsoft.com/en-us/library/ms732023(v=vs.110).aspx')。 這個工具需要您下載 Windows Server SDK。

>[!NOTE]
>記錄檔位於 C:\ProgramData\Microsoft\Windows Intune Exchange Connector\Logs。 一系列共包含 30 個檔案的記錄檔是以 *Connector0.log* 開始並在 *Connector29.log* 停止。 記錄檔會在累積 10MB 的資料後，換用另一個檔案。 一旦記錄檔達到 Connector29，將會覆寫先前的記錄檔，再次從 Connector0 開始。

#### 尋找同步記錄檔

-    搜尋「完整同步處理」，在記錄檔中尋找完整同步處理。 完整同步處理的開頭會標有此段文字︰

    「處理命令：為 <number> 個使用者取得行動裝置清單，但不含時間篩選器 (完整同步處理)」

    完整同步處理的記錄檔結尾看起來像這樣︰

    順利完成為 4 個使用者取得行動裝置清單，但不含時間篩選器 (完整同步處理)。 詳細資料: 清查命令結果 - 同步的裝置: 0 命令識別碼: commandIDGUID' Exchange 健全狀況: '伺服器健全狀況' 名稱: 'PowerShellExchangeServer: <Name=mymailservername>' 狀態: ’已連線','

-   搜尋「快速同步處理」，在記錄檔中尋找快速 (差異) 同步處理。

##### Get next 命令中的例外狀況
檢查 Exchange Connector 記錄檔中 **Get next 命令**的例外狀況，並將這些資訊提供給 Microsoft 支援服務。

#### 詳細資訊記錄

若要啟用詳細資訊記錄：

1.  開啟 Exchange Connector 追蹤組態檔。 該檔案位於︰ %ProgramData%\Microsoft\Windows Intune Exchange Connector\TracingConfiguration.xml。
2.  使用下列機碼來尋找 TraceSourceLine：OnPremisesExchangeConnectorService
3.  將 **SourceLevel** 節點值從 **警告 ActivityTracing** (預設值) 變更為 **Verbose ActivityTracing**，如下所示。

    <TraceSourceLine>
          <Key xsi:type="xsd:string">OnPremisesExchangeConnectorService</Key>
          <Value xsi:type="TraceSource">
            <SourceLevel>All</SourceLevel>
            <Listeners>
              <Listener>
                <ListenerType>CircularTraceListener</ListenerType>
                <SourceLevel>Verbose ActivityTracing</SourceLevel>
                <FileSizeQuotaInBytes>10000000</FileSizeQuotaInBytes>
                <FileName>Microsoft\Windows Intune Exchange Connector\Logs\Connector.svclog</FileName>
                <FileQuota>30</FileQuota>
              </Listener>
            </Listeners>
          </Value>
    </TraceSourceLine>



### 後續步驟
如果這項疑難排解資訊對您沒有幫助，請連絡 Microsoft 支援服務 (如[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)中所述)。



<!--HONumber=Jul16_HO4-->


