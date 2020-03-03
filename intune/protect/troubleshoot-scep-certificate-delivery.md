---
title: 當您搭配 Microsoft Intune 使用 SCEP 時，針對裝置的憑證傳遞進行疑難排解 | Microsoft Docs
description: 使用 SCEP 憑證設定檔搭配 Intune 來部署憑證時，針對從 CA 將憑證傳遞至裝置進行疑難排解。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40075ad3c90f9ce5131d88780d15eec5c258e276
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515249"
---
# <a name="troubleshoot-the-delivery-of-certificates-provisioned-by-scep-to-devices-in-microsoft-intune"></a>在 Microsoft Intune 中針對將 SCEP 佈建的憑證傳遞至裝置進行疑難排解

當您使用簡單憑證註冊通訊協定 (SCEP) 在 Intune 中佈建憑證時，請使用此文章中的資訊來協助您調查裝置的憑證傳遞。 在網路裝置註冊服務 (NDES) 伺服器從憑證授權單位 (CA) 收到裝置的要求憑證之後，其會將該憑證傳回到裝置。

此文章適用於 [SCEP 通訊工作流程](troubleshoot-scep-certificate-profiles.md)的步驟 5；將憑證傳遞到提交憑證要求的裝置。

## <a name="review-the-certification-authority"></a>檢閱憑證授權單位

當 CA 發行憑證時，您會在 CA 上看到類似下列範例的項目：

![已發行的憑證範例](../protect/media/troubleshoot-scep-certificate-delivery/certificate-authority.png)

## <a name="review-the-device"></a>檢閱裝置

### <a name="android"></a>Android

針對裝置系統管理員註冊的裝置，您會看到類似下圖的通知，該通知會提示您安裝憑證：

![Android 通知](../protect/media/troubleshoot-scep-certificate-delivery/android-notification.png)

針對 Android Enterprise 或 Samsung Knox，憑證安裝為自動且無訊息。

若要在 Android 上檢視已安裝的憑證，請使用協力廠商憑證檢視應用程式。

您也可以檢閱[裝置 OMADM 記錄](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)。 尋找與下列項目類似的項目，這些項目會在安裝憑證時記錄：

**根憑證**：

```
2018-02-27T04:50:52.1890000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        9    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALL_REQUESTED
2018-02-27T04:53:31.1300000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        0    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T04:53:32.0390000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595       14    Root cert '17…' state changed from CERT_INSTALLING to CERT_INSTALL_SUCCESS
```

**透過 SCEP 佈建的憑證**

```
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    There are 1 requests
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    Trying to enroll certificate request: ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787
2018-02-27T05:16:20.6150000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:20.6530000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:21.7460000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.7890000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:28.0340000    VERB    Event     org.jscep.transaction.EnrollmentTransaction    18327       10    Response: org.jscep.message.CertRep@3150777b[failInfo=<null>,pkiStatus=SUCCESS,recipientNonce=Nonce [GUID],messageData=org.spongycastle.cms.CMSSignedData@27cc8998,messageType=CERT_REP,senderNonce=Nonce [GUID],transId=TRANSID]
2018-02-27T05:16:28.2440000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       10    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ENROLLED to CERT_INSTALL_REQUESTED
2018-02-27T05:18:44.9820000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327        0    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T05:18:45.3460000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       14    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALLING to CERT_ACCESS_REQUESTED
2018-02-27T05:20:15.3520000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       21    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ACCESS_REQUESTED to CERT_ACCESS_GRANTED
```

### <a name="iosipados"></a>iOS/iPadOS

在 iOS/iPadOS 或 iPadOS 裝置上，您可以在 [裝置管理設定檔] 下檢視憑證。 向下鑽研以檢視已安裝之憑證的詳細資料。

![iOS 憑證](../protect/media/troubleshoot-scep-certificate-delivery/ios-certificate.png)

您也可以在 [iOS 偵錯記錄](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices)中尋找如下項目：

```
Debug 18:30:53.691033 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\  
Debug 18:30:54.640644 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
Debug 18:30:55.487908 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQG 
Debug 18:30:57.285730 -0500 profiled Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 in domain ManagedProfileToManagingProfile to system\ 
Default 18:30:57.320616 -0500 profiled Profile \'93www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295\'94 installed.\ 
```

### <a name="windows"></a>Windows

在 Windows 裝置上，確認憑證已傳遞：

- 執行 **eventvwr.msc** 以開啟事件檢視器。 移至 [應用程式及服務記錄檔]   > [Microsoft]   > [Windows]   > [DeviceManagement-Enterprise-Diagnostic-Provider]   > [Admin]  ，並尋找**事件 39**。 此事件應具有下列一般描述：**SCEP：已成功安裝憑證。**

   ![Windows 應用程式記錄檔中的事件 39](../protect/media/troubleshoot-scep-certificate-delivery/device-app-log.png)

若要在裝置上檢視憑證，請執行 **certmgr.msc** 以開啟 [憑證 MMC]，並確認已在裝置上的個人存放區中正確安裝根憑證與 SCEP 憑證：

   1. 移至 [憑證 (本機電腦)]   > [信任的根憑證授權單位]   > [憑證]  ，並確認 CA 的根憑證存在。 「發出給」  與「發行者」  的值將會相同。
   2. 在 [憑證 MMC] 中，移至 [憑證 - 目前的使用者]   > [個人]   > [憑證]  ，然後確認要求的憑證存在，且憑證的「發行者」  等於 CA 的名稱。

## <a name="troubleshoot-failures"></a>針對失敗進行疑難排解

### <a name="android"></a>Android

若要針對此步驟進行疑難排解，請檢閱 OMA DM 記錄中記錄的錯誤。

### <a name="iosipados"></a>iOS/iPadOS

若要針對此步驟進行疑難排解，請檢閱裝置偵錯記錄中記錄的錯誤。

### <a name="windows"></a>Windows

若要針對未安裝在裝置上的憑證問題進行疑難排解，請查看 Windows 事件記錄檔中是否有建議問題的錯誤：

- 在裝置上，執行 **eventvwr.msc** 以開啟事件檢視器，然後移至 [應用程式及服務記錄檔]   > [Microsoft]   > [Windows]   > [DeviceManagement-Enterprise-Diagnostic-Provider > Admin]   。

憑證傳遞和憑證安裝到裝置的錯誤通常與 Windows 作業相關，而與 Intune 無關。

## <a name="next-steps"></a>後續步驟

當憑證成功部署到裝置，但 Intune 未回報成功時，請參閱 [NDES 報告至 Intune](troubleshoot-scep-certificate-reporting.md) 以針對報告進行疑難排解。
