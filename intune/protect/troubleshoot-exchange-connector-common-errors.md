---
title: 針對 Intune Exchange connector 的常見錯誤進行疑難排解
titleSuffix: Microsoft Intune
description: 針對內部部署 Microsoft Intune Exchange Connector 的常見錯誤進行疑難排解並加以解決
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
ms.openlocfilehash: b30a7e843850d6918abc2e76f84397a1f197516f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508852"
---
# <a name="resolve-common-errors-for-the-intune-exchange-connector"></a>解決 Intune Exchange Connector 的常見錯誤

本文可協助 Intune 管理員解決有關 Intune Exchange Connector 操作的特定錯誤和訊息。  

## <a name="configuration-failed-and-returned-error-code-0x0000001"></a>設定失敗，傳回錯誤碼0x0000001

**問題**：  
當您嘗試設定 Microsoft Intune Exchange Connector 時，您會收到下列錯誤訊息：

```
   The Microsoft Intune Exchange Connector cannot connect to the Microsoft Exchange server.  
   The following Microsoft Exchange Server address could not be reached <Exchange server Name FQDN>  
   Verify that the FQDN of the exchange server address and credentials that you entered is correct and the server is running. The Microsoft Intune Exchange Connector does not support Exchange server arrays.  
   Error code: 0x0000001  
```

如果網際網路 proxy 設定不正確，可能會發生此問題。

**解決方案**：  
進行 Proxy 設定：
1. 請洽詢區域網路管理員，以確定已正確設定 proxy 設定。 
2. 使用**Netsh winHTTP**命令來設定 proxy 伺服器，並新增必要的排除清單。 例如：  

   ```
   Netsh winhttp set proxy proxy-server="http=proxy.corp.domain.com" bypass-list"34*.*;134.132.*.*;10.*.*;localhost;*.corp.domain.com;*.staging.domain.com"
   ```

## <a name="configuration-failed-and-returned-error-code-0x000000b"></a>設定失敗，傳回錯誤碼0x000000b   

**問題**：  
當您嘗試設定 Microsoft Intune Exchange Connector 時，您會收到下列錯誤訊息：  

```
   The Microsoft Intune Exchange Connector experienced an error:  
   CertEnroll::CX509PrivateKey::Create: The system cannot find the file specified. 0x80070002 (WIN32: 2  
   ERROR_FILE_NOT_FOUND  
   Error code: 0x000000b  
```
如果您用來登入 Intune 的帳戶不是 Intune 全域系統管理員帳戶，就可能發生此問題。

**解決方案**：  
使用全域管理員帳戶登入 Intune，或將您的帳戶新增至全域管理員群組。 如需詳細資訊，請參閱[以角色為基礎的系統管理 (RBAC) 搭配 Microsoft Intune](../fundamentals/role-based-access-control.md)。

## <a name="configuration-failed-and-returned-error-code-0x0000006"></a>設定失敗，傳回錯誤碼0x0000006

**問題**：  
當您嘗試設定 Microsoft Intune Exchange Connector 時，您會收到下列錯誤訊息：  

```  
   The Microsoft Intune Exchange Connector cannot connect to Microsoft Intune  
   Verify that you are connected to the Internet, check the Microsoft Intune Service Status, and try to connect again.  
   Error code: 0x00000006  
```  
如果使用 proxy 伺服器來連線到網際網路，並封鎖對 Intune 服務的流量，就會發生此錯誤。 若要判斷 proxy 是否正在使用中，請移至 [**控制台** **]  > ** -1 [**網際網路選項**]，選取 [連線] 索引標籤，然後按一下 [**區域網路設定**]。

**解決方案**：  

- **選項 1** -移除 proxy 設定以允許電腦連線到網際網路，而不經過 proxy。  

- **選項 2** -將您的 proxy 伺服器設定為允許與 intune 服務通訊，如[Intune Exchange Connector 需求](exchange-connector-install.md#intune-exchange-connector-requirements)中所述。



## <a name="event-7000-or-7041-microsoft-intune-exchange-connector-service-wont-start"></a>事件7000或7041： Microsoft Intune Exchange Connector 服務無法啟動

**問題**：  
IOS 裝置無法在 Intune 中註冊，並會產生下列其中一個錯誤訊息：  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Task Category: None
   Level:               Error
   Keywords:        Classic
   User:                N/A
   Computer:      <computer>
   Description:
   The Microsoft Intune Exchange Connector Service service failed to start because of the following error:  
   The service did not start because of a logon failure.
```  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Event ID:          7041
   Task Category: None
   Level:               Error   
   Keywords:        Classic
   User:                N/A
   Computer:       <computer>
   Description:
   The WIEC service was unable to log on as .\WIEC_USER with the currently configured password because of the following error:
   Logon failure: the user has not been granted the requested logon type at this computer.
   Service: WIEC
   Domain and account: .\WIEC_USER
   This service account does not have the required user right "Log on as a service."  
```
如果**WIEC_User**帳戶在本機原則中沒有 [**以服務方式登**入] 使用者權限，就會發生此問題。

**解決方案**：  
在執行 Intune Exchange Connector 的電腦上，將 [**以服務方式登**入] 使用者權限指派給**WIEC_User**服務帳戶。 如果電腦是叢集中的節點，請務必將叢集內所有節點上的叢集服務帳戶的 [以*服務方式登*入] 使用者權限指派給該叢集。  

若要將 [以**服務方式登**入] 使用者權限指派給電腦上的**WIEC_User**服務帳戶，請遵循下列步驟：

1. 以系統管理員或 Administrators 群組成員的身分登入電腦。
2. 執行**secpol.msc**以開啟本機安全性原則。
3. 移至 **安全性設定**  > **本機原則**，然後選取 **使用者權限指派**。
4. 在右側窗格中，連按兩下 [以服務方式登入]  。
5. 選取 [**新增使用者或群組**]，將**WIEC_USER**新增至原則，然後選取 **[確定]** 兩次。

如果已將 [**以服務方式登**入] 使用者權限指派給**WIEC_User** ，但後來又移除，請洽詢網域系統管理員，以判斷群組原則設定是否會覆寫它。  

## <a name="next-steps"></a>後續步驟  

下列文章可協助解決特定的錯誤：
- [解決 Intune Exchange Connector 的常見問題](troubleshoot-exchange-connector-common-problems.md)。 git 

尋求支援或 Intune 社區的協助。
- 請參閱[取得支援](../fundamentals/get-support.md)以使用 Intune 主控台來協助疑難排解問題，或向 Microsoft 開啟支援案例。 
- 在[Microsoft Intune 論壇](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)中張貼您的問題。  
