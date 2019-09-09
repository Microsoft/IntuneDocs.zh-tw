---
title: 針對 Microsoft Intune 憑證連接器和事件識別碼進行疑難排解 |Microsoft Docs
description: 藉由檢閱事件識別碼和描述來針對 Microsoft Intune 憑證連接器進行疑難排解，並檢閱 Intune 連接器服務的診斷碼。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/01/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a282662032fe77cbf39da279c587bff31ad9e24
ms.sourcegitcommit: cf40f641af4746a1e34edd980dc6ec96fd040126
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70123220"
---
# <a name="intune-certificate-connector-events-and-diagnostic-codes"></a>Intune 憑證連接器事件和診斷碼

從 6.1806.x.x 版開始，Intune 連接器服務會在 [事件檢視器] ([應用程式及服務記錄檔] > [Microsoft Intune 連接器]) 中記錄事件。 您可以使用這些事件來協助對 Intune 連接器設定中的潛在問題進行疑難排解。 這些事件會記錄作業的成功與失敗，還會包含診斷碼及訊息，以協助 IT 系統管理員進行疑難排解。

> [!TIP]  
> 若要針對問題進行疑難排解及驗證 Intune 連接器設定，請參閱 [Certificate Authority script samples](https://aka.ms/intuneconnectorverificationscript) (憑證授權單位指令碼範例)。

## <a name="event-ids-and-descriptions"></a>事件識別碼和描述

| 事件識別碼      | 事件名稱    | 事件描述 | 相關的診斷碼 |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | 已啟動連接器服務 | 0x00000000、0x0FFFFFFF |
| 10020 | StoppedConnectorService  | 已停止連接器服務 | 0x00000000、0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | 已成功更新連接器註冊憑證 | 0x00000000、0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | 連接器註冊憑證無法更新。 請重新安裝連接器。 | 0x00000000、0x00000405、0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | 無法從登錄中擷取連接器註冊憑證。 請檢閱與此事件相關之憑證指紋的事件詳細資料。 | 0x00000000、0x00000404、0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | 檢查事件詳細資料中的診斷資訊。 | 0x00000000、0x00000403、0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | 已成功發行 PKCS 憑證。 請檢閱與此事件相關之裝置識別碼、使用者識別碼、CA 名稱、憑證範本名稱和憑證指紋的事件詳細資料。 | 0x00000000、0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | 無法發行 PKCS 憑證。 請檢閱與此事件相關之裝置識別碼、使用者識別碼、CA 名稱、憑證範本名稱和憑證指紋的事件詳細資料。 | 0x00000000、0x00000400、0x00000401、0x0FFFFFFF |
| 20200 | RevokeCert_Success  | 已成功撤銷憑證。 請檢閱與此事件相關之裝置識別碼、使用者識別碼、CA 名稱、憑證序號的事件詳細資料。 | 0x00000000、0x0FFFFFFF |
| 20202 | RevokeCert_Failure | 無法撤銷憑證。 請檢閱與此事件相關之裝置識別碼、使用者識別碼、CA 名稱、憑證序號的事件詳細資料。 如需額外資訊，請參閱 NDES SVC 記錄檔。   | 0x00000000、0x00000402、0x0FFFFFFF |
| 20300 | Upload_Success | 已成功上傳憑證的要求或撤銷資料。 請檢閱上傳詳細資料的事件詳細資料。 | 0x00000000、0x0FFFFFFF |
| 20302 | Upload_Failure | 無法上傳憑證的要求或撤銷資料。 請檢閱事件詳細資料 > 上傳狀態，以判斷失敗點。| 0x00000000、0x0FFFFFFF |
| 20400 | Download_Success | 已成功下載簽署憑證、下載用戶端憑證或撤銷憑證的要求。 請檢閱下載詳細資料的事件詳細資料。  | 0x00000000、0x0FFFFFFF |
| 20402 | Download_Failure | 無法下載簽署憑證、下載用戶端憑證或撤銷憑證的要求。 請檢閱下載詳細資料的事件詳細資料。 | 0x00000000、0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | 憑證登錄點已成功驗證用戶端挑戰 | 0x00000000、0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | 憑證登錄點已完成，但拒絕要求。 請參閱診斷碼和訊息，以取得詳細資料。 | 0x00000000、0x00000411、0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | 憑證登錄點無法驗證用戶端挑戰。 請參閱診斷碼和訊息，以取得詳細資料。 請參閱對應至挑戰之裝置識別碼的事件訊息詳細資料。 | 0x00000000、0x00000408、0x00000409、0x00000410、0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | 憑證登錄點已成功完成通知程序，並已將憑證傳送到用戶端裝置。 | 0x00000000、0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | 憑證登錄點無法完成通知程序。 請參閱事件訊息詳細資料，以取得要求的相關資訊。 請驗證 NDES 伺服器與 CA 之間的連線。 | 0x00000000、0x0FFFFFFF |

## <a name="diagnostic-codes"></a>診斷碼

| 診斷碼 | 診斷名稱 | 診斷訊息 |
| -------------   | -------------   | -------------      |
| 0x00000000 | 成功  | 成功 |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | 憑證授權單位無效或無法連線。 請確認憑證授權單位可用，且您的伺服器可以與其通訊。 |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | 本機憑證存放區中找不到 Symantec 用戶端驗證憑證。 請參閱[安裝 Symantec 註冊驗證憑證](https://docs.microsoft.com/intune/certificates-symantec-configure#install-the-symantec-registration-authorization-certificate)一文，以取得詳細資料。  |
| 0x00000402 | RevokeCert_AccessDenied  | 指定的帳戶無權撤銷來自 CA 的憑證。 請參閱事件訊息詳細資料中的 CA 名稱欄位，以判斷發行的 CA。  |
| 0x00000403 | CertThumbprint_NotFound  | 找不到符合您輸入的憑證。 請註冊憑證連接器，然後再試一次。 |
| 0x00000404 | Certificate_NotFound  | 找不到符合所提供輸入的憑證。 請重新註冊憑證連接器，然後再試一次。 |
| 0x00000405 | Certificate_Expired  | 憑證已過期。 請重新註冊憑證連接器以更新憑證，然後再試一次。 |
| 0x00000408 | CRPSCEPCert_NotFound  | 找不到 CRP 加密憑證。 請確認 NDES 和 Intune 連接器已正確設定。 |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | 無法擷取簽署憑證。 請確認 Intune 連接器服務已設定正確，且 Intune 連接器服務正在執行。 另請確認憑證下載事件已成功。 |
| 0x00000410 | CRPSCEPDeserialize_Failed  | 無法還原序列化 SCEP 挑戰要求。 請確認 NDES 和 Intune 連接器已正確設定。 |
| 0x00000411 | CRPSCEPChallenge_Expired  | 由於憑證挑戰過期，已拒絕要求。 用戶端裝置可以在從管理伺服器取得新挑戰之後重試。 |
| 0x0FFFFFFFF | Unknown_Error  | 我們無法完成您的要求，因為發生伺服器端錯誤。 請再試一次。 |


## <a name="next-steps"></a>後續步驟
如需其他協助，請使用[針對 Microsoft Intune 中的 SCEP 憑證設定檔部署進行疑難排解](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune)指南。
