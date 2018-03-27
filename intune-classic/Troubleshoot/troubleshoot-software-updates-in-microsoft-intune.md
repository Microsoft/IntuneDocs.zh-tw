---
title: 軟體更新疑難排解
description: 解決 Microsoft Intune 的軟體更新問題。
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 36715859c4c4685aa8d0fc74b360efd2372ee6c2
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Microsoft Intune 的軟體更新疑難排解

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

請使用本節中的資訊，協助您解決 Microsoft Intune 的軟體更新問題。

如果此資訊無法解決您的問題，請參閱[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)，以尋找更多方法來取得協助。

## <a name="update-agent-error-codes"></a>更新代理程式錯誤碼

下表列出 intune **更新代理程式**錯誤碼。 如果您在這份表格中找不到特定錯誤碼，請參閱 [Windows Update Agent Result Codes (Windows Update 代理程式結果代碼)](http://go.microsoft.com/fwlink/?LinkID=221542)。

|錯誤碼|符號名稱|詳細資訊|
|--------------|-----------------|--------------------|
|**0x00cf0001**|OM_S_SERVICE_STOP|代理程式已順利停止。|
|**0x00cf0003**|OM_S_UPDATE_ERROR|作業已順利完成，但套用更新時發生錯誤。|
|**0x00cf0004**|OM_S_MARKED_FOR_DISCONNECT|已標示稍後要中斷連線回撥，因為在執行回撥時出現中斷連線作業的要求。|
|**0x00cf0005**|OM_S_REBOOT_REQUIRED|必須重新啟動系統才能完成更新安裝。|
|**0x00cf0006**|OM_S_ALREADY_INSTALLED|系統上已經安裝您要安裝的更新。|
|**0x00cf0007**|OM_S_ALREADY_UNINSTALLED|系統上並未安裝您要移除的更新。|
|**0x00cf2015**|OM_S_UH_INSTALLSTILLPENDING|更新安裝作業正在進行。|
|**0x80cf0001**|OM_E_NO_SERVICE|代理程式無法提供服務。|
|**0x80cf0002**|OM_E_MAX_CAPACITY_REACHED|已超過服務的容量上限。|
|**0x80cf0003**|OM_E_UNKNOWN_ID|找不到識別碼。|
|**0x80cf0004**|OM_E_NOT_INITIALIZED|無法初始化物件。|
|**0x80cf0007**|OM_E_INVALIDINDEX|集合的索引無效。|
|**0x80cf0008**|OM_E_ITEMNOTFOUND|找不到所查詢項目的機碼。|
|**0x80cf0009**|OM_E_OPERATIONINPROGRESS|衝突的作業正在進行中。 某些作業 (例如多重安裝) 不能同時執行。|
|**0x80cf000B**|OM_E_CALL_CANCELLED|已取消作業。|
|**0x80cf000C**|OM_E_NOOP|不需要任何操作。|
|**0x80cf000D**|OM_E_XML_MISSINGDATA|代理程式在更新的 XML 資料中找不到必要的資訊。|
|**0x80cf000E**|OM_E_XML_INVALID|代理程式在更新的 XML 資料中找到無效的資訊。|
|**0x80cf000F**|OM_E_CYCLE_DETECTED|在中繼資料中偵測到循環的更新關聯。|
|**0x80cf0010**|OM_E_TOO_DEEP_RELATION|更新關聯的巢狀結構太深，無法評估。|
|**0x80cf0011**|OM_E_INVALID_RELATIONSHIP|找到的更新關聯無效。|
|**0x80cf0012**|OM_E_REG_VALUE_INVALID|讀取到的登錄值無效。|
|**0x80cf0013**|OM_E_DUPLICATE_ITEM|作業嘗試在清單中新增重複的項目。|
|**0x80cf0014**|OM_E_INVALID_INSTALL_REQUESTED|呼叫者無法安裝已要求安裝的更新。|
|**0x80cf0016**|OM_E_INSTALL_NOT_ALLOWED|作業在其他安裝正在進行時嘗試安裝，或是系統尚有擱置中的強制重新啟動作業。|
|**0x80cf0017**|OM_E_NOT_APPLICABLE|未執行作業，因為沒有適用的更新。|
|**0x80cf0018**|OM_E_NO_USERTOKEN|作業失敗，因為遺漏必要的使用者 Token。|
|**0x80cf0019**|OM_E_EXCLUSIVE_INSTALL_CONFLICT|獨佔式更新不能同時與其他更新一起執行。|
|**0x80cf001A**|OM_E_POLICY_NOT_SET|未設定原則值。|
|**0x80cf001D**|OM_E_INVALID_UPDATE|更新包含無效的中繼資料。|
|**0x80cf001E**|OM_E_SERVICE_STOP|無法完成作業，因為服務或系統已關閉。|
|**0x80cf001F**|OM_E_NO_CONNECTION|無法完成作業，因為網路連線無法使用。|
|**0x80cf0020**|OM_E_NO_INTERACTIVE_USER|無法完成作業，因為沒有已登入的互動使用者。|
|**0x80cf0021**|OM_E_TIME_OUT|無法完成作業，因為作業已逾時。|
|**0x80cf0022**|OM_E_ALL_UPDATES_FAILED|所有更新的這項作業全部失敗。|
|**0x80cf0024**|OM_E_NO_UPDATE|沒有更新。|
|**0x80cf0025**|OM_E_USER_ACCESS_DISABLED|群組原則設定導致無法存取 Windows Update。|
|**0x80cf0026**|OM_E_INVALID_UPDATE_TYPE|更新類型無效。|
|**0x80cf0028**|OM_E_UNINSTALL_NOT_ALLOWED|無法解除安裝更新，因為要求不是來自 WSUS 伺服器。|
|**0x80cf0029**|OM_E_INVALID_PRODUCT_LICENSE|搜尋可能已漏掉某些更新，或是系統上可能有未授權的應用程式。|
|**0x80cf002C**|OM_E_BIN_SOURCE_ABSENT|無法安裝 Delta 壓縮格式的更新，因為這種更新需要來源。|
|**0x80cf002D**|OM_E_SOURCE_ABSENT|無法安裝完整檔案更新，因為這種更新需要來源。|
|**0x80cf002E**|OM_E_WU_DISABLED|不允許存取未受管理的伺服器。|
|**0x80cf002F**|OM_E_CALL_CANCELLED_BY_POLICY|已設定 **DisableWindowsUpdateAccess** 原則，因此無法完成操作。|
|**0x80cf0030**|OM_E_INVALID_PROXY_SERVER|Proxy 清單格式無效。|
|**0x80cf0031**|OM_E_INVALID_FILE|檔案的格式錯誤。|
|**0x80cf0032**|OM_E_INVALID_CRITERIA|搜尋條件字串無效。|
|**0x80cf0034**|OM_E_DOWNLOAD_FAILED|無法下載更新。|
|**0x80cf0035**|OM_E_UPDATE_NOT_PROCESSED|尚未處理更新。|
|**0x80cf0036**|OM_E_INVALID_OPERATION|物件目前的狀態不允許此作業。|
|**0x80cf0037**|OM_E_NOT_SUPPORTED|不支援此作業。|
|**0x80cf0038**|OM_E_WINHTTP_INVALID_FILE|下載的檔案包含非預期的內容類型。|
|**0x80cf0039**|OM_E_TOO_MANY_RESYNC|伺服器要求代理程式重新同步的次數太多。|
|**0x80cf0043**|OM_E_NO_UI_SUPPORT|不支援 WUA UI。|
|**0x80cf0044**|OM_E_PER_MACHINE_UPDATE_ACCESS_DENIED|只有系統管理員可以在個別電腦更新中執行這項作業。|
|**0x80cf0045**|OM_E_UNSUPPORTED_SEARCHSCOPE|嘗試以不支援的範圍進行搜尋。|
|**0x80cf0046**|OM_E_BAD_FILE_URL|URL 未指向檔案。|
|**0x80cf0047**|OM_E_NOTSUPPORTED|不支援要求的作業。|
|**0x80cf0049**|OM_E_OUTOFRANGE|資料超出範圍。|
|**0x80cf004A**|OM_E_INVALIDWUAVERSION|資料包含無效的版本。|
|**0x80cf004B**|OM_E_SEARCH_COMPLETED_WITH_SOME_FAILURES|搜尋呼叫已完成，但無法偵測某些更新。|
|**0x80cf004C**|OM_E_DOWNLOAD_COMPLETED_WITH_SOME_FAILURES|下載呼叫已完成，但無法下載某些更新。|
|**0x80cf004D**|OM_E_INSTALL_COMPLETED_WITH_SOME_FAILURES|安裝呼叫已完成，但無法安裝某些更新。|
|**0x80cf004E**|OM_E_WINUPDATE_CACHE_UNINITIALIZED|Windows Update 快取是空的，因為它尚未初始化。|
|**0x80cf0436**|OM_E_PT_CATALOG_SYNC_REQUIRED|伺服器不支援針對特定類別的搜尋。 必須改為發出完整類別搜尋。|
|**0x80cf0437**|OM_E_PT_SECURITY_VERIFICATION_FAILURE|向服務授權時發生問題。|
|**0x80cf0438**|OM_E_PT_ENDPOINT_UNREACHABLE|沒有連接端點的路由或網路連線。|
|**0x80cf0439**|OM_E_PT_INVALID_FORMAT|收到的資料不符合資料合約的預期結果。|
|**0x80cf043A**|OM_E_PT_INVALID_URL|URL 無效。|
|**0x80cf043B**|OM_E_PT_NWS_NOT_LOADED|無法載入 NWS 執行階段。|
|**0x80cf043C**|OM_E_PT_PROXY_AUTH_SCHEME_NOT_SUPPORTED|不支援 Proxy 驗證配置。|
|**0x80cf043D**|OM_E_SERVICEPROP_NOTAVAIL|要求的服務內容無法使用。|
|**0x80cf043E**|OM_E_PT_ENDPOINT_REFRESH_REQUIRED|端點提供者外掛程式需要線上重新整理。|
|**0x80cf043F**|OM_E_PT_ENDPOINTURL_NOTAVAIL|要求的服務端點 URL 無法使用。|
|**0x80cf0440**|OM_E_PT_ENDPOINT_DISCONNECTED|與服務端點的連線已終止。|
|**0x80cf0441**|OM_E_PT_INVALID_OPERATION|作業無效，因為通訊協定對談程式 (Protocol Talker) 的狀態不適當。|
|**0x80cf0FFF**|OM_E_UNEXPECTED|由於另一個錯誤碼未說明的原因，導致作業失敗。|
|**0x80cf1001**|OM_E_MSI_WRONG_VERSION|搜尋可能已漏掉某些更新，因為 Windows Installer 的版本低於 3.1 版。|
|**0x80cf1002**|OM_E_MSI_NOT_CONFIGURED|搜尋可能已漏掉某些更新，因為沒有設定 Windows Installer。|
|**0x80cf1003**|OM_E_MSP_DISABLED|搜尋可能已漏掉某些更新，因為原則已停用 Windows Installer 修補功能。|
|**0x80cf1004**|OM_E_MSI_WRONG_APP_CONTEXT|無法套用更新，因為應用程式是採用個人安裝的方式。|
|**0x80cf2000**|OM_E_UH_REMOTEUNAVAILABLE|無法完成遠端更新處理常式的要求，因為沒有遠端程序可以使用。|
|**0x80cf2001**|OM_E_UH_LOCALONLY|無法完成遠端更新處理常式的要求，因為處理常式只存在本機。|
|**0x80cf2003**|OM_E_UH_REMOTEALREADYACTIVE|已有遠端更新處理常式，因此無法建立。|
|**0x80cf2004**|OM_E_UH_DOESNOTSUPPORTACTION|無法完成處理常式安裝 (解除安裝) 更新的要求，因為更新不支援安裝 (解除安裝)。|
|**0x80cf2005**|OM_E_UH_WRONGHANDLER|無法完成作業，因為指定的處理常式不正確。|
|**0x80cf2006**|OM_E_UH_INVALIDMETADATA|無法完成處理常式作業，因為更新包含無效的中繼資料。|
|**0x80cf2007**|OM_E_UH_INSTALLERHUNG|無法完成作業，因為安裝程式已超過時間限制。 請檢查是否已核准部署需要使用者互動的更新。 在這種情況下，您必須修改更新安裝參數，讓它可以進行無訊息安裝。|
|**0x80cf2008**|OM_E_UH_OPERATIONCANCELLED|已取消更新處理常式正在執行的作業。|
|**0x80cf2009**|OM_E_UH_BADHANDLERXML|無法完成作業，因為處理常式特有的中繼資料無效。|
|**0x80cf200B**|OM_E_UH_INSTALLERFAILURE|安裝程式無法安裝 (解除安裝) 一或多項更新。|
|**0x80cf200D**|OM_E_UH_NEEDANOTHERDOWNLOAD|更新處理常式未安裝更新，因為必須再次下載更新。|
|**0x80cf200E**|OM_E_UH_NOTIFYFAILURE|更新處理常式無法傳送安裝 (解除安裝) 作業的狀態通知。|
|**0x80cf2014**|OM_E_UH_POSTREBOOTSTILLPENDING|更新的重新開機後續作業仍在進行中。|
|**0x80cf2015**|OM_E_UH_POSTREBOOTRESULTUNKNOWN|無法判斷更新的重新開機後續作業結果。|
|**0x80cf2016**|OM_E_UH_POSTREBOOTUNEXPECTEDSTATE|在更新完成重新開機後續作業後，其狀態與預期不符。|
|**0x80cf2017**|OM_E_UH_NEW_SERVICING_STACK_REQUIRED|在下載或安裝此更新前，必須先更新作業系統服務堆疊。|
|**0x80cf2018**|OM_E_UH_CALLED_BACK_FAILURE|回撥安裝程式回撥時發生錯誤。|
|**0x80cf2019**|OM_E_UH_CUSTOMINSTALLER_INVALID_SIGNATURE|自訂安裝程式簽章與更新需要的簽章不相符。|
|**0x80cf201A**|OM_E_UH_UNSUPPORTED_INSTALLCONTEXT|安裝程式不支援安裝設定。|
|**0x80cf201B**|OM_E_UH_INVALID_TARGETSESSION|安裝的目標工作階段無效。|
|**0x80cf2FFF**|OM_E_UH_UNEXPECTED|另一個 OM_E_UH_&#42; 代碼未涵蓋更新處理常式錯誤。|
|**0x80cf3FFD**|OM_E_NON_UI_MODE|在非 UI 模式下無法顯示 UI。 可能未安裝 Windows Update 用戶端 UI 模組。|
|**0x80cf3FFE**|OM_E_WUCLTUI_UNSUPPORTED_VERSION|不支援 WU 用戶端 UI 已匯出的函數版本。|
|**0x80cf3FFF**|OM_E_AUCLIENT_UNEXPECTED|發生另一個 OM_E_AUCLIENT_&#42; 錯誤碼未涵蓋的使用者介面錯誤。|
|**0x80cf4007**|OM_E_PT_SOAPCLIENT_SOAPFAULT|與 **SOAPCLIENT_SOAPFAULT** 相同。 SOAP 用戶端失敗，因為發生 **OM_E_PT_SOAP_&#42;** 錯誤碼類型的 SOAP 錯誤。|
|**0x80cf4008**|OM_E_PT_SOAPCLIENT_PARSEFAULT|與 **SOAPCLIENT_PARSEFAULT_ERROR** 相同。  SOAP 用戶端無法剖析 SOAP 錯誤。|
|**0x80cf400A**|OM_E_PT_SOAPCLIENT_PARSE|與 **SOAPCLIENT_PARSE_ERROR** 相同。  SOAP 用戶端無法剖析伺服器傳來的回應。|
|**0x80cf400B**|OM_E_PT_SOAP_VERSION|與 **SOAP_E_VERSION_MISMATCH** 相同。 SOAP 用戶端找到 SOAP 封套無法辨識的命名空間。|
|**0x80cf400C**|OM_E_PT_SOAP_MUST_UNDERSTAND|與 **SOAP_E_MUST_UNDERSTAND** 相同。 SOAP 用戶端無法解譯標頭。|
|**0x80cf400D**|OM_E_PT_SOAP_CLIENT|與 **SOAP_E_CLIENT** 相同。 SOAP 用戶端發現訊息格式錯誤。 請更正後再重新傳送。|
|**0x80cf400E**|OM_E_PT_SOAP_SERVER|與 **SOAP_E_SERVER** 相同。 因為發生伺服器錯誤，所以無法處理 SOAP 訊息。 請稍後再重新傳送。|
|**0x80cf4010**|OM_E_PT_EXCEEDED_MAX_SERVER_TRIPS|來回往返伺服器的次數已超過上限。|
|**0x80cf4012**|OM_E_PT_DOUBLE_INITIALIZATION|初始化作業失敗，因為物件已完成初始化。|
|**0x80cf4013**|OM_E_PT_INVALID_COMPUTER_NAME|無法判斷電腦名稱。|
|**0x80cf4015**|OM_E_PT_REFRESH_CACHE_REQUIRED|伺服器的回覆指出伺服器已變更或 Cookie 無效。 請重新整理內部快取後再重試。|
|**0x80cf4016**|OM_E_PT_HTTP_STATUS_BAD_REQUEST|與 **HTTP 狀態 400** 相同。 伺服器無法處理要求，因為語法無效。|
|**0x80cf4017**|OM_E_PT_HTTP_STATUS_DENIED|與 **HTTP 狀態 401** 相同。 要求的資源需要進行使用者驗證。|
|**0x80cf4018**|OM_E_PT_HTTP_STATUS_FORBIDDEN|與 **HTTP 狀態 403** 相同。 伺服器瞭解要求，但拒絕執行要求。|
|**0x80cf4019**|OM_E_PT_HTTP_STATUS_NOT_FOUND|與 **HTTP 狀態 404** 相同。 伺服器找不到要求的 URI (統一資源識別項)。|
|**0x80cf401A**|OM_E_PT_HTTP_STATUS_BAD_METHOD|與 **HTTP 狀態 405** 相同。 不允許 HTTP 方法。|
|**0x80cf401B**|OM_E_PT_HTTP_STATUS_PROXY_AUTH_REQ|與 **HTTP 狀態 407** 相同。 需要 Proxy 驗證。|
|**0x80cf401C**|OM_E_PT_HTTP_STATUS_REQUEST_TIMEOUT|與 **HTTP 狀態 408** 相同。 伺服器要求等待逾時。|
|**0x80cf401D**|OM_E_PT_HTTP_STATUS_CONFLICT|與 **HTTP 狀態 409** 相同。 無法完成要求，因為與資源目前的狀態衝突。|
|**0x80cf401E**|OM_E_PT_HTTP_STATUS_GONE|與 **HTTP 狀態 410** 相同。 伺服器不再提供要求的資源。|
|**0x80cf401F**|OM_E_PT_HTTP_STATUS_SERVER_ERROR|與 **HTTP 狀態 500** 相同。 伺服器內部錯誤導致要求無法執行。|
|**0x80cf4020**|OM_E_PT_HTTP_STATUS_NOT_SUPPORTED|與 **HTTP 狀態 500** 相同。 伺服器不支援執行要求所需的功能。|
|**0x80cf4021**|OM_E_PT_HTTP_STATUS_BAD_GATEWAY|與 **HTTP 狀態 502** 相同。 作為閘道或 Proxy 的伺服器從它在嘗試執行要求時所存取的上游伺服器收到無效的回應。|
|**0x80cf4022**|OM_E_PT_HTTP_STATUS_SERVICE_UNAVAIL|與 **HTTP 狀態 503** 相同。 服務暫時超載。|
|**0x80cf4023**|OM_E_PT_HTTP_STATUS_GATEWAY_TIMEOUT|與 **HTTP 狀態 503** 相同。 等待閘道時，要求逾時。|
|**0x80cf4024**|OM_E_PT_HTTP_STATUS_VERSION_NOT_SUP|與 **HTTP 狀態 505** 相同。 伺服器不支援用於要求的 HTTP 通訊協定版本。|
|**0x80cf4025**|OM_E_PT_FILE_LOCATIONS_CHANGED|由於檔案位置變更導致作業失敗。 請重新整理內部狀態後再重新傳送。|
|**0x80cf4027**|OM_E_PT_NO_AUTH_PLUGINS_REQUESTED|伺服器傳回空白的驗證資訊清單。|
|**0x80cf4028**|OM_E_PT_NO_AUTH_COOKIES_CREATED|代理程式無法建立任何有效的驗證 Cookie。|
|**0x80cf4029**|OM_E_PT_INVALID_CONFIG_PROP|設定內容值不正確。|
|**0x80cf402A**|OM_E_PT_CONFIG_PROP_MISSING|遺漏設定內容值。|
|**0x80cf402B**|OM_E_PT_HTTP_STATUS_NOT_MAPPED|無法完成 HTTP 要求，且原因沒有對應到任何 **OM_E_PT_HTTP_&#42;** 錯誤碼。|
|**0x80cf402C**|OM_E_PT_WINHTTP_NAME_NOT_RESOLVED|與 **ERROR_WINHTTP_NAME_NOT_RESOLVED** 相同。 無法解析 Proxy 伺服器或目的地伺服器名稱。|
|**0x80cf402F**|OM_E_PT_ECP_SUCCEEDED_WITH_ERRORS|外部 .cab 檔處理完成，但發生一些錯誤。|
|**0x80cf4030**|OM_E_PT_ECP_INIT_FAILED|外部 .cab 處理器初始化尚未完成。|
|**0x80cf4031**|OM_E_PT_ECP_INVALID_FILE_FORMAT|中繼資料檔案的格式無效。|
|**0x80cf4032**|OM_E_PT_ECP_INVALID_METADATA|外部 cab 處理器找到無效的中繼資料。|
|**0x80cf4033**|OM_E_PT_ECP_FAILURE_TO_EXTRACT_DIGEST|無法從外部 .cab 檔擷取檔案摘要。|
|**0x80cf4034**|OM_E_PT_ECP_FAILURE_TO_DECOMPRESS_CAB_FILE|無法解壓縮外部 .cab 檔。|
|**0x80cf4035**|OM_E_PT_ECP_FILE_LOCATION_ERROR|外部 .cab 處理器無法取得檔案位置。|
|**0x80cf4FFF**|OM_E_PT_UNEXPECTED|發生另一個 **OM_E_PT_&#42;** 錯誤碼未涵蓋的通訊錯誤。|
|**0x80cf6001**|OM_E_DM_URLNOTAVAILABLE|無法完成下載管理員作業，因為要求的檔案沒有 URL。|
|**0x80cf6002**|OM_E_DM_INCORRECTFILEHASH|無法完成下載管理員作業，因為無法辨識檔案摘要。|
|**0x80cf6003**|OM_E_DM_UNKNOWNALGORITHM|無法完成下載管理員作業，因為檔案中繼資料要求的雜湊演算法無法辨識。|
|**0x80cf6005**|OM_E_DM_NONETWORK|無法完成下載管理員作業，因為網路連線無法使用。|
|**0x80cf6007**|OM_E_DM_NOTDOWNLOADED|尚未下載更新。|
|**0x80cf6008**|OM_E_DM_FAILTOCONNECTTOBITS|下載管理員作業失敗，因為下載管理員無法連線到背景智慧型傳送服務 (BITS)。|
|**0x80cf6009**|OM_E_DM_BITSTRANSFERERROR|下載管理員作業失敗，因為發生未指定的背景智慧型傳送服務 (BITS) 傳輸錯誤。|
|**0x80cf600a**|OM_E_DM_DOWNLOADLOCATIONCHANGED|必須重新啟動下載，因為下載來源位置已經變更。|
|**0x80cf600B**|OM_E_DM_CONTENTCHANGED|必須重新啟動下載，因為新修訂中的更新內容已經變更。|
|**0x80cf6FFF**|OM_E_DM_UNEXPECTED|發生另一個 **OM_E_DM_&#42;** 錯誤碼未涵蓋的下載管理員錯誤。|
|**0x80cf7003**|OM_E_INVALID_EVENT_PAYLOAD|指定的事件承載量無效。|
|**0x80cf7004**|OM_E_INVALID_EVENT_PAYLOADSIZE|提交的事件承載量大小無效。|
|**0x80cf7005**|OM_E_SERVICE_NOT_REGISTERED|尚未登錄此服務。|
|**0x80cf8000**|OM_E_DS_SHUTDOWN|作業失敗，因為代理程式正在關閉。|
|**0x80cf8001**|OM_E_DS_INUSE|作業失敗，因為資料存放區正在使用中。|
|**0x80cf8002**|OM_E_DS_INVALID|資料存放區目前的狀態和預期的狀態不相符。|
|**0x80cf8003**|OM_E_DS_TABLEMISSING|資料存放區遺失一份表格。|
|**0x80cf8004**|OM_E_DS_TABLEINCORRECT|資料存放區包含的資料表有非預期的欄。|
|**0x80cf8005**|OM_E_DS_INVALIDTABLENAME|無法開啟表格，因為表格不在資料存放區中。|
|**0x80cf8006**|OM_E_DS_BADVERSION|資料存放區目前的版本和預期的版本不相符。|
|**0x80cf8007**|OM_E_DS_NODATA|要求的資訊不在資料存放區中。|
|**0x80cf8008**|OM_E_DS_MISSINGDATA|資料存放區遺漏必要的資訊，或是在需要非 null 值的表格欄中有 null 值存在。|
|**0x80cf8009**|OM_E_DS_MISSINGREF|資料存放區遺漏必要的資訊，或是有某個參照指向遺漏的授權條款、檔案、當地語系化內容或連結列。|
|**0x80cf800A**|OM_E_DS_UNKNOWNHANDLER|尚未處理更新，因為無法辨識它的更新處理常式。|
|**0x80cf800B**|OM_E_DS_CANTDELETE|未刪除更新，因為還有一或多項服務仍然參照此更新。|
|**0x80cf800C**|OM_E_DS_LOCKTIMEOUTEXPIRED|無法在指定的時間內鎖定資料存放區區段。|
|**0x80cf800E**|OM_E_DS_ROWEXISTS|未新增列，因為現有的列具有相同的主索引鍵。|
|**0x80cf800F**|OM_E_DS_STOREFILELOCKED|無法初始化資料存放區，因為其他程序已將它鎖定。|
|**0x80cf8010**|OM_E_DS_CANNOTREGISTER|目前的程序不允許將資料存放區登錄到 COM。|
|**0x80cf8011**|OM_E_DS_UNABLETOSTART|作業無法在其他程序中建立資料存放區物件。|
|**0x80cf8013**|OM_E_DS_DUPLICATEUPDATEID|伺服器使用兩個不同的修訂識別碼將相同的更新傳送到用戶端。|
|**0x80cf8014**|OM_E_DS_UNKNOWNSERVICE|無法完成作業，因為服務不在資料存放區中。|
|**0x80cf8015**|OM_E_DS_SERVICEEXPIRED|無法完成作業，因為服務的登錄已到期。|
|**0x80cf8016**|OM_E_DS_DECLINENOTALLOWED|已拒絕隱藏更新的要求，因為它是強制性更新或部署時已加上期限。|
|**0x80cf8017**|OM_E_DS_TABLESESSIONMISMATCH|未關閉表格，因為它與工作階段無關。|
|**0x80cf8018**|OM_E_DS_SESSIONLOCKMISMATCH|未關閉表格，因為它與工作階段無關。|
|**0x80cf8019**|OM_E_DS_NEEDWINDOWSSERVICE|已拒絕移除或取消登錄服務的要求，因為它是內建服務，或是因為自動更新無法切換回另一項服務。|
|**0x80cf801A**|OM_E_DS_INVALIDOPERATION|已拒絕要求，因為不允許此作業。|
|**0x80cf801B**|OM_E_DS_SCHEMAMISMATCH|目前資料存放區的架構與備份 XML 文件中表格的架構不相符。|
|**0x80cf801C**|OM_E_DS_RESETREQUIRED|資料存放區需要重設工作階段。 請釋放工作階段，並使用新的工作階段再試一次。|
|**0x80cf801D**|OM_E_DS_IMPERSONATED|無法完成資料存放區作業，因為要求作業時使用的是模擬身分識別。|
|**0x80cf8FFF**|OM_E_DS_UNEXPECTED|發生另一個 **OM_E_DS_&#42;** 代碼未涵蓋的資料存放區錯誤。|
|**0x80cfA000**|OM_E_AU_NOSERVICE|自動更新無法處理傳入的要求。|
|**0x80cfA004**|OM_E_AU_PAUSED|自動更新已暫停，因此無法處理傳入的要求。|
|**0x80cfA005**|OM_E_AU_NO_REGISTERED_SERVICE|尚未向自動服務登錄任何未受管理的服務。|
|**0x80cfA006**|OM_E_AU_DETECT_SVCID_MISMATCH|在搜尋過程中，向自動服務登錄的預設服務發生變更。|
|**0x80cfA007**|OM_E_AU_ALREADY_PROMPTING_FOR_REBOOT|自動更新已提示使用者重新啟動。|
|**0x80cfAFFF**|OM_E_AU_UNEXPECTED|發生另一個 **OM_E_AU &#42;** 代碼未涵蓋的自動更新錯誤。|
|**0x80cfE001**|OM_E_EE_UNKNOWN_EXPRESSION|無法完成運算式評估工具作業，因為無法辨識運算式。|
|**0x80cfE002**|OM_E_EE_INVALID_EXPRESSION|無法完成運算式評估工具作業，因為運算式無效。|
|**0x80cfE003**|OM_E_EE_MISSING_METADATA|無法完成運算式評估工具作業，因為運算式包含不正確的中繼資料節點數目。|
|**0x80cfE004**|OM_E_EE_INVALID_VERSION|無法完成運算式評估工具作業，因為序列運算式資料的版本無效。|
|**0x80cfE005**|OM_E_EE_NOT_INITIALIZED|無法初始化運算式評估工具。|
|**0x80cfE006**|OM_E_EE_INVALID_ATTRIBUTEDATA|無法完成運算式評估工具作業，因為屬性無效。|
|**0x80cfE007**|OM_E_EE_CLUSTER_ERROR|無法完成運算式評估工具作業，因為無法判斷電腦的叢集狀態。|
|**0x80cfEFFF**|OM_E_EE_UNEXPECTED|發生另一個 **OM_E_EE_&#42;** 錯誤碼未涵蓋的運算式評估工具錯誤。|
|**0x80cfF001**|OM_E_REPORTER_EVENTCACHECORRUPT|事件快取檔案已損壞。|
|**0x80cfF002**|OM_E_REPORTER_EVENTNAMESPACEPARSEFAILED|無法剖析事件命名空間描述元中的 XML。|
|**0x80cfF003**|OM_E_INVALID_EVENT|事件命名空間描述元中的 XML 無效。|
|**0x80cfF004**|OM_E_SERVER_BUSY|伺服器已拒絕事件，因為伺服器過於忙碌。|
|**0x80cfFFFF**|OM_E_REPORTER_UNEXPECTED|發生另一個錯誤碼未涵蓋的報告者錯誤|
|**0x80af0005**|OMC_E_INSTALL_NOT_ALLOWED_REBOOT_REQUIRED|安裝失敗，因為尚有擱置中的強制重新開機作業。|
|**0x80af0006**|OMC_E_DOWNLOAD_CANCELLED|已取消下載。|

## <a name="windows-7-based-computers-with-lots-of-superseded-updates-stop-reporting-to-the-microsoft-intune-console"></a>包含大量被取代更新的 Windows 7 電腦會停止回報到 Microsoft Intune 主控台
**問題**︰您可能會遇到下列情況，Microsoft Intune 用戶端遇到一或多個下列症狀︰
- 它們突然停止回報到 Microsoft 管理主控台。  
- 它們經歷高 CPU 使用率。
- 透過 Intune 入口網站安裝應用程式時，它們會緩慢安裝。
- Microsoft Intune Center 會觸發下列錯誤︰*更新您的電腦時發生錯誤。找到錯誤︰錯誤碼 0x800705b4*。
- 在 [Intune 管理主控台] > [群組] > [所有裝置] 下的 [狀態] 欄位會顯示︰*安裝至這台電腦的一或多個代理程式發生錯誤。此電腦的資訊可能不精確或者不是最新狀態*。

如果被取代的更新 (已被其他更新取代的更新) 未長時間拒絕，就可能會發生此問題。 在某些處理程序期間，例如安裝應用程式時，Windows 會依照順序檢查所有被取代的更新，以便更新和其後續更新可以正確對應。 如果被取代的更新清單成長至過大，這項檢查工作可能會因為處理負載和所需時間而導致高 CPU 使用率。 這由於可供 Windows 7 使用的大量被取代更新，個問題主要會影響正在執行 Windows 7 的用戶端。 Windows 8 和更新版的作業系統沒有這麼多可用的被取代更新，因此不容易發生此問題。

**解決方式**：若要解決此問題，請遵循下列步驟：
1. 登入 [Intune 管理主控台](https://manage.microsoft.com)。
2. 選取 **[更新]** > **[所有更新]**。
3. 使用上方工具列上的篩選選項，以篩選出被取代的更新。
4. 拒絕所有可能套用至 Windows 7 或套用至安裝於受影響用戶端上的應用程式 (例如，Microsoft Office) 的被取代更新。
5. 重新啟動受影響的用戶端。

此外，如果您執行 Windows 7，請確定您已安裝下列更新︰[3050265 Windows Update Client for Windows 7: June 2015](https://support.microsoft.com/kb/3050265) (3050265 適用於 Windows 7 的 Windows Update 用戶端：2015 年 6 月)。

### <a name="next-steps"></a>接下來的步驟
如果此疑難排解資訊對您沒有幫助，請連絡 Microsoft 支援服務 (如[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)中所述)。
