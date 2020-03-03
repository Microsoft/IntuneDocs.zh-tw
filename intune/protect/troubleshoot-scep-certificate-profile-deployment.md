---
title: 針對使用 Microsoft Intune 將 SCEP 憑證設定檔部署至裝置進行疑難排解 | Microsoft Docs
description: 針對使用 Intune 將 SCEP 憑證設定檔傳送至裝置進行疑難排解。
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
ms.openlocfilehash: 26eb6a5cb8e7aba01ce32ab8bec8ad917604a55c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514773"
---
# <a name="troubleshoot-deployment-of-a-scep-certificate-profile-to-devices-in-microsoft-intune"></a>針對 Microsoft Intune 中的 SCEP 憑證設定檔部署至裝置進行疑難排解

使用下列資訊以協助您針對使用 Intune 的簡單憑證註冊通訊協定 (SCEP) 憑證設定檔部署進行疑難排解。

此文章參考 [SCEP 通訊流程概觀](troubleshoot-scep-certificate-profiles.md)的步驟 1。


## <a name="android"></a>Android

適用於 Android 的 SCEP 憑證設定檔會以 SyncML 的形式部署至裝置，並記錄在 [OMADM 記錄](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)中。

### <a name="validate-that-the-android-device-was-sent-the-policy"></a>驗證是否已向 Android 裝置傳送原則

若要驗證是否已將設定檔傳送至您預期的裝置，請在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中移至 [疑難排解 + 支援]   > [疑難排解]  。  在 [疑難排解]  視窗中，將 [指派]  設定為 [組態設定檔]  然後驗證下列設定：

1. 指定應該接收 SCEP 憑證設定檔的使用者。

2. 檢閱使用者群組成員資格，以確保他們位於您搭配 SCEP 憑證設定檔使用的安全性群組中。

3. 檢閱裝置上次簽入 Intune 的時間。

![驗證原則](../protect/media/troubleshoot-scep-certificate-profile-deployment/validate-policy-android.png)

### <a name="validate-the-policy-reached-the-android-device"></a>驗證原則是否已傳送到 Android 裝置

檢閱[裝置 OMADM 記錄](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)。 尋找與下列項目類似的項目，這些項目會在裝置從 Intune 取得設定檔時記錄：

```
Time    VERB    Event     com.microsoft.omadm.syncml.SyncmlSession     9595        9    <?xml version="1.0" encoding="utf-8"?><SyncML xmlns="SYNCML:SYNCML1.2"><SyncHdr><VerDTD>1.2</VerDTD><VerProto>DM/1.2</VerProto><SessionID>1</SessionID><MsgID>6</MsgID><Target><LocURI>urn:uuid:UUID</LocURI></Target><Source><LocURI>https://a.manage.microsoft.com/devicegatewayproxy/AndroidHandler.ashx</LocURI></Source><Meta><MaxMsgSize xmlns="syncml:metinf">524288</MaxMsgSize></Meta></SyncHdr><SyncBody><Status><CmdID>1</CmdID><MsgRef>6</MsgRef><CmdRef>0</CmdRef><Cmd>SyncHdr</Cmd><Data>200</Data></Status><Replace><CmdID>2</CmdID><Item><Target><LocURI>./Vendor/MSFT/Scheduler/IntervalDurationSeconds</LocURI></Target><Meta><Format xmlns="syncml:metinf">int</Format><Type xmlns="syncml:metinf">text/plain</Type></Meta><Data>28800</Data></Item></Replace><Replace><CmdID>3</CmdID><Item><Target><LocURI>./Vendor/MSFT/EnterpriseAppManagement/EnterpriseIDs</LocURI></Target><Data>contoso.onmicrosoft.com</Data></Item></Replace><Exec><CmdID>4</CmdID><Item><Target><LocURI>./Vendor/MSFT/EnterpriseAppManagement/EnterpriseApps/ClearNotifications</LocURI></Target></Item></Exec><Add><CmdID>5</CmdID><Item><Target><LocURI>./Vendor/MSFT/CertificateStore/Root/{GUID}/EncodedCertificate</LocURI></Target><Data>Data</Data></Item></Add><Add><CmdID>6</CmdID><Item><Target><LocURI>./Vendor/MSFT/CertificateStore/Enroll/ModelName=AC_51…%2FLogicalName_39907…%3BHash=-1518303401/Install</LocURI></Target><Meta><Format xmlns="syncml:metinf">xml</Format><Type xmlns="syncml:metinf">text/plain</Type></Meta><Data>&lt;CertificateRequest&gt;&lt;ConfigurationParametersDocument&gt;&amp;lt;ConfigurationParameters xmlns="http://schemas.microsoft.com/SystemCenterConfigurationManager/2012/03/07/CertificateEnrollment/ConfigurationParameters"&amp;gt;&amp;lt;ExpirationThreshold&amp;gt;20&amp;lt;/ExpirationThreshold&amp;gt;&amp;lt;RetryCount&amp;gt;3&amp;lt;/RetryCount&amp;gt;&amp;lt;RetryDelay&amp;gt;1&amp;lt;/RetryDelay&amp;gt;&amp;lt;TemplateName /&amp;gt;&amp;lt;SubjectNameFormat&amp;gt;{ID}&amp;lt;/SubjectNameFormat&amp;gt;&amp;lt;SubjectAlternativeNameFormat&amp;gt;{ID}&amp;lt;/SubjectAlternativeNameFormat&amp;gt;&amp;lt;KeyStorageProviderSetting&amp;gt;0&amp;lt;/KeyStorageProviderSetting&amp;gt;&amp;lt;KeyUsage&amp;gt;32&amp;lt;/KeyUsage&amp;gt;&amp;lt;KeyLength&amp;gt;2048&amp;lt;/KeyLength&amp;gt;&amp;lt;HashAlgorithms&amp;gt;&amp;lt;HashAlgorithm&amp;gt;SHA-1&amp;lt;/HashAlgorithm&amp;gt;&amp;lt;HashAlgorithm&amp;gt;SHA-2&amp;lt;/HashAlgorithm&amp;gt;&amp;lt;/HashAlgorithms&amp;gt;&amp;lt;NDESUrls&amp;gt;&amp;lt;NDESUrl&amp;gt;https://breezeappproxy-contoso.msappproxy.net/certsrv/mscep/mscep.dll&amp;lt;/NDESUrl&amp;gt;&amp;lt;/NDESUrls&amp;gt;&amp;lt;CAThumbprint&amp;gt;{GUID}&amp;lt;/CAThumbprint&amp;gt;&amp;lt;ValidityPeriod&amp;gt;2&amp;lt;/ValidityPeriod&amp;gt;&amp;lt;ValidityPeriodUnit&amp;gt;Years&amp;lt;/ValidityPeriodUnit&amp;gt;&amp;lt;EKUMapping&amp;gt;&amp;lt;EKUMap&amp;gt;&amp;lt;EKUName&amp;gt;Client Authentication&amp;lt;/EKUName&amp;gt;&amp;lt;EKUOID&amp;gt;1.3.6.1.5.5.7.3.2&amp;lt;/EKUOID&amp;gt;&amp;lt;/EKUMap&amp;gt;&amp;lt;/EKUMapping&amp;gt;&amp;lt;/ConfigurationParameters&amp;gt;&lt;/ConfigurationParametersDocument&gt;&lt;RequestParameters&gt;&lt;CertificateRequestToken&gt;PENlcnRFbn... Hash: 1,010,143,298&lt;/CertificateRequestToken&gt;&lt;SubjectName&gt;CN=name&lt;/SubjectName&gt;&lt;Issuers&gt;CN=FourthCoffee CA; DC=fourthcoffee; DC=local&lt;/Issuers&gt;&lt;SubjectAlternativeName&gt;&lt;SANs&gt;&lt;SAN NameFormat="ID" AltNameType="2" OID="{OID}"&gt;&lt;/SAN&gt;&lt;SAN NameFormat="ID" AltNameType="11" OID="{OID}"&gt;john@contoso.onmicrosoft.com&lt;/SAN&gt;&lt;/SANs&gt;&lt;/SubjectAlternativeName&gt;&lt;NDESUrl&gt;https://breezeappproxy-contoso.msappproxy.net/certsrv/mscep/mscep.dll&lt;/NDESUrl&gt;&lt;/RequestParameters&gt;&lt;/CertificateRequest&gt;</Data></Item></Add><Get><CmdID>7</CmdID><Item><Target><LocURI>./Vendor/MSFT/CertificateStore/SCEP</LocURI></Target></Item></Get><Add><CmdID>8</CmdID><Item><Target><LocURI>./Vendor/MSFT/GCM</LocURI></Target><Data>Data</Data></Item></Add><Replace><CmdID>9</CmdID><Item><Target><LocURI>./Vendor/MSFT/GCM</LocURI></Target><Data>Data</Data></Item></Replace><Get><CmdID>10</CmdID><Item><Target><LocURI>./Vendor/MSFT/NodeCache/SCConfigMgr</LocURI></Target></Item></Get><Get><CmdID>11</CmdID><Item><Target><LocURI>./Vendor/MSFT/NodeCache/SCConfigMgr/CacheVersion</LocURI></Target></Item></Get><Get><CmdID>12</CmdID><Item><Target><LocURI>./Vendor/MSFT/NodeCache/SCConfigMgr/ChangedNodes</LocURI></Target></Item></Get><Get><CmdID>13</CmdID><Item><Target><LocURI>./DevDetail/Ext/Microsoft/LocalTime</LocURI></Target></Item></Get><Get><CmdID>14</CmdID><Item><Target><LocURI>./Vendor/MSFT/DeviceLock/DevicePolicyManager/IsActivePasswordSufficient</LocURI></Target></Item></Get><Get><CmdID>15</CmdID><Item><Target><LocURI>./Vendor/MSFT/WorkProfileLock/DevicePolicyManager/IsActivePasswordSufficient</LocURI></Target></Item></Get><Final /></SyncBody></SyncML>
```

金鑰項目的範例：

- `ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c%3BHash=-1518303401`
- `NDESUrls&amp;gt;&amp;lt;NDESUrl&amp;gt;https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll&amp;lt;/NDESUrl&amp;gt;&amp;lt;/NDESUrls`

## <a name="iosipados"></a>iOS/iPadOS

### <a name="validate-that-the-iosipados-device-was-sent-the-policy"></a>驗證是否已向 iOS/iPadOS 裝置傳送原則

若要驗證是否已將設定檔傳送至您預期的裝置，請在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中移至 [疑難排解 + 支援]   > [疑難排解]  。  在 [疑難排解]  視窗中，將 [指派]  設定為 [組態設定檔]  然後驗證下列設定：

1. 指定應該接收 SCEP 憑證設定檔的使用者。

2. 檢閱使用者群組成員資格，以確保他們位於您搭配 SCEP 憑證設定檔使用的安全性群組中。

3. 檢閱裝置上次簽入 Intune 的時間。

![驗證原則](../protect/media/troubleshoot-scep-certificate-profile-deployment/validate-policy-ios.png)

### <a name="validate-the-policy-reached-the-ios-or-ipados-device"></a>驗證原則是否已傳送到 iOS 或 iPadOS 裝置

檢閱[裝置偵錯記錄](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices)。 尋找與下列項目類似的項目，這些項目會在裝置從 Intune 取得設定檔時記錄：

```
debug    18:30:54.638009 -0500    profiled    Adding dependent ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 to parent 636572740000000000000012 in domain PayloadDependencyDomainCertificate to system\
```

金鑰項目的範例：

- `ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295`
- `PayloadDependencyDomainCertificate`

## <a name="windows"></a>Windows

### <a name="validate-that-the-windows-device-was-sent-the-policy"></a>驗證是否已向 Windows 裝置傳送原則

若要驗證是否已將設定檔傳送至您預期的裝置，請在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)[Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)移至 [疑難排解 + 支援]   > [疑難排解]  。  在 [疑難排解]  視窗中，將 [指派]  設定為 [組態設定檔]  然後驗證下列設定：

1. 指定應該接收 SCEP 憑證設定檔的使用者。

2. 檢閱使用者群組成員資格，以確保他們位於您搭配 SCEP 憑證設定檔使用的安全性群組中。

3. 檢閱裝置上次簽入 Intune 的時間。

![驗證原則](../protect/media/troubleshoot-scep-certificate-profile-deployment/validate-policy-windows.png)

### <a name="validate-the-policy-reached-the-windows-device"></a>驗證原則是否已傳送到 Windows 裝置

設定檔的原則抵達會記錄在 Windows 裝置的 *DeviceManagement-Enterprise-Diagnostics-Provider* > **Admin** 記錄中，事件識別碼為 **306**。 

開啟記錄檔：

1. 在裝置上，執行 **eventvwr.msc** 以開啟 Windows 事件檢視器。

2. 展開 [應用程式及服務記錄檔]   > [Microsoft]   > [Windows]   > [DeviceManagement-Enterprise-Diagnostic-Provider]   > [Admin]  。

3. 尋找事件 **306**，其類似於下列範例：

   ```
   Event ID:      306
   Task Category: None
   Level:         Information
   User:          SYSTEM
   Computer:      <Computer Name>
   Description:
   SCEP: CspExecute for UniqueId : (ModelName_<ModelName>_LogicalName_<LogicalName>_Hash_<Hash>) InstallUserSid : (<UserSid>) InstallLocation : (user) NodePath : (clientinstall)  KeyProtection: (0x2) Result : (Unknown Win32 Error code: 0x2ab0003).
   ```

   錯誤碼 **0x2ab0003** 會轉譯為 **DM_S_ACCEPTED_FOR_PROCESSING**。

   不成功的錯誤碼可能會提供根本問題的指示。

## <a name="next-steps"></a>後續步驟

如果設定檔傳送到裝置，下一個步驟就是檢閱[裝置對 NDES 伺服器通訊](troubleshoot-scep-certificate-device-to-ndes.md)。
