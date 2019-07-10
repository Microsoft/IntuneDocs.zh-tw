---
title: 設定用於 Intune Connector for Active Directory 的 Proxy 設定
description: 說明如何設定 Intune Connector for Active Directory，來使用現有的內部部署 Proxy 伺服器。
keywords: ''
author: master11218
ms.author: tanvira
manager: smantri
ms.date: 4/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tanvira
ms.suite: ems
search.appverid: ''
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: f91ec3124d8fab067ec32194a68508762c6cef33
ms.sourcegitcommit: 1dc9d4e1d906fab3fc46b291c67545cfa2231660
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735252"
---
# <a name="work-with-existing-on-premises-proxy-servers"></a>使用現有的內部部署 Proxy 伺服器

本文說明如何設定 Intune Connector for Active Directory，來使用輸出 Proxy 伺服器。 它適用於網路環境具有現有 Proxy 的客戶。

如需連接器運作方式的詳細資訊，請參閱[了解 Azure AD 應用程式 Proxy 連接器](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-connectors)。

## <a name="bypass-outbound-proxies"></a>略過輸出 Proxy

連接器有基礎的 OS 元件，可發出輸出要求。 這些元件會自動嘗試使用 Web Proxy 自動探索 (WPAD)，在網路上尋找 Proxy 伺服器。

OS 元件會藉由對 wpad.domainsuffix 執行 DNS 查閱，嘗試尋找 Proxy 伺服器。 如果查閱在 DNS 中解決，便會對 wpad.dat 的 IP 位址提出 HTTP 要求。 此要求會成為您環境中的 Proxy 設定指令碼。 連接器會使用此指令碼，選取輸出 Proxy 伺服器。 不過，連接器流量可能仍然無法通過，因為 Proxy 上需要其他組態設定。

您可以設定連接器以略過內部部署 Proxy，確保它對 Azure 服務使用直接連線。 只要您的網路原則允許，我們會建議使用這種方法，因為這表示您要維護的設定會少一項。

若要停用連接器的輸出 Proxy 使用，請編輯 C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorUI\ODJConnectorUI.exe.config 檔案，並在此程式碼範例所示的區段中新增 Proxy 位址和 Proxy 連接埠：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="mscorlib" publicKeyToken="b77a5c561934e089" culture="neutral"/>
                <bindingRedirect oldVersion="0.0.0.0-2.0.0.0" newVersion="4.6.0.0" />
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="SignInURL" value="https://portal.manage.microsoft.com/Home/ClientLogon"/>
        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
    </appSettings>
</configuration>
```

若要確保連接器更新程式服務也會略過 Proxy，請對 C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config 進行類似的變更。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="BaseServiceAddress" value="https://manage.microsoft.com/" />
    </appSettings>
</configuration>
```

請務必複製原始檔案，以防您需要還原為預設的 .config 檔案。

一旦修改設定檔，您必須重新啟動 Intune Connector 服務。 

1. 開啟 **services.msc**。
2. 尋找並選取 [Intune ODJConnector Service]  。
3. 選取 [重新啟動]  。

![重新啟動服務的螢幕擷取畫面](media/autopilot-hybrid-connector-proxy/service-restart.png)


## <a name="next-steps"></a>後續步驟

[管理您的裝置](device-management.md)