---
title: "使用預先共用金鑰建立 Wi-Fi 設定檔"
titleSuffix: Azure portal
description: "使用 Intune 自訂設定檔建立附有預先共用金鑰的 Wi-Fi 設定檔。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 11/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 395a7136630a9393f44037c65e3c8db760149c38
ms.sourcegitcommit: b982f9d50da4f958fb0c48c56ba46c8ef71500c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="use-a-custom-device-profile-to-create-a-wi-fi-profile-with-a-pre-shared-key"></a>使用自訂裝置設定檔建立包含預先共用金鑰的 Wi-Fi 設定檔
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

以下是如何使用 Intune 的**自訂裝置設定檔**建立附有預先共用金鑰的 Wi-Fi 設定檔。 此主題也包含如何建立 EAP 型 Wi-Fi 設定檔的範例。

> [!NOTE]
-   您可能會發現從連線到該網路的電腦複製程式碼較輕鬆，如下所述。
- 若是 Android，您也可以選擇使用 Johnathon Biersack 提供的這個 [Android PSK 產生器](http://intunepskgenerator.johnathonb.com/)。
-   您可以新增更多 OMA URI 設定，以新增多個網路和金鑰。
-  若為 iOS，請使用 Mac 站上的 Apple Configurator 來設定設定檔。 或者，使用 Johnathon Biersack 提供的這個 [iOS PSK 行動設定產生器](http://intunepskgenerator.johnathonb.com/)。


1.  若要為 Android 或 Windows 建立附有預先共用金鑰的 Wi-Fi 設定檔或或採用 EAP Wi-Fi 設定檔，請在建立裝置設定檔時，為該裝置平台 (而不是 Wi-Fi 設定檔) 選擇 [自訂]。

2.  提供名稱和描述。
3.  加入新的 OMA-URI 設定︰

   a.   輸入此 Wi-Fi 網路設定的名稱。

   b。   輸入 OMA-URI 設定的描述，或者保留空白。

   c.   **資料類型**︰設為 [字串]。

   d.   **OMA-URI**：

    - **適用於 Android**：./Vendor/MSFT/WiFi/Profile/<SSID>/Settings
    - **適用於 Windows**：./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml

    > [!NOTE]
開頭務必包含點號字元。

    SSID 是您要建立原則的 SSID。 例如，`./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`

  e. **值欄位**是貼上 XML 程式碼的位置。 範例如下。 每個值應該適用於您的網路設定。 請參閱程式碼的註解區段，以取得一些指示。
4. 選擇 [確定]並儲存，然後指派原則。

    > [!NOTE]
    > 此原則僅能指派給使用者群組。

每個裝置下一次簽入時，將套用此原則，並將裝置上建立 Wi-Fi 設定檔。 裝置可以自動連線到網路。

## <a name="android-or-windows-wi-fi-profile"></a>Android 或 Windows Wi-Fi 設定檔

Android 或 Windows 的 Wi-Fi 設定檔 XML 程式碼範例如下︰

> [!IMPORTANT]
>
> `<protected>false</protected>` 必須設定為 **false**，因為 **true** 可能會使裝置預期收到加密的密碼，而嘗試將它解密；這會導致連線失敗。
>
>  `<hex>53534944</hex>` 應設定為 `<name><SSID of wifi profile></name>` 的十六進位值。
>  Windows 10 裝置可能會傳回誤報的 *0x87D1FDE8 補救失敗*錯誤，但仍會使用設定檔進行佈建。

```
<!--
<Name of wifi profile> = Name of profile
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Password to connect to the network
x>53534944</hex> should be set to the hexadecimal value of <name><SSID of wifi profile></name>
-->
<WLANProfile
xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
  <name><Name of wifi profile></name>
  <SSIDConfig>
    <SSID>
      <hex>53534944</hex>
 <name><SSID of wifi profile></name>
    </SSID>
    <nonBroadcast>false</nonBroadcast>
  </SSIDConfig>
  <connectionType>ESS</connectionType>
  <connectionMode>auto</connectionMode>
  <autoSwitch>false</autoSwitch>
  <MSM>
    <security>
      <authEncryption>
        <authentication><Type of authentication></authentication>
        <encryption><Type of encryption></encryption>
        <useOneX>false</useOneX>
      </authEncryption>
      <sharedKey>
        <keyType>networkKey</keyType>
        <protected>false</protected>
        <keyMaterial>MyPassword</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

## <a name="eap-based-wi-fi-profile"></a>EAP 型 Wi-Fi 設定檔
EAP 型 Wi-Fi 設定檔的 XML 程式碼範例如下︰

```
    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                <EapMethod>
                  <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
                  <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
                  <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
                  <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
                </EapMethod>
                <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                  <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
                    <Type>13</Type>
                    <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
                      <CredentialsSource>
                        <CertificateStore>
                          <SimpleCertSelection>true</SimpleCertSelection>
                        </CertificateStore>
                      </CredentialsSource>
                      <ServerValidation>
                        <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
                        <ServerNames></ServerNames>
                      </ServerValidation>
                      <DifferentUsername>false</DifferentUsername>
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>
```

## <a name="create-the-xml-file-from-an-existing-wi-fi-connection"></a>從現有的 Wi-Fi 連線建立 XML 檔案
您也可以從現有的 Wi-Fi 連線建立 XML 檔案：
1. 在連線到或最近已連線到無線網路的電腦上，開啟下列資料夾 ︰C:\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}。

    最好使用未連線至許多無線網路的電腦，因為您必須搜尋每個設定檔才能找到正確檔案。
3.     搜尋 XML 檔案，找出名稱正確的檔案。
4.     找到正確的 XML 檔案後，將 XML 程式碼複製並貼入 OMA-URI 設定頁面的 [資料] 欄位。

## <a name="best-practices"></a>最佳做法
以 PSK 部署 Wi-Fi 設定檔之前，請確認裝置可以直接連接至端點。

當輪替金鑰 (密碼或複雜密碼) 時，預期據此部署停機時間和規劃。 請考慮在非工作時間推送新的 Wi-Fi 設定檔。 此外，警告使用者連線可能會受到影響。

為確保轉換順利，請確定使用者的裝置具備其他網際網路連線。 例如，使用者必須能夠切換回客體 WiFi (或某些其他 WiFi 網路)，或能夠使用行動電話與 Intune 連線通訊。 當裝置更新公司的 WiFi 設定檔時，這可讓使用者繼續接收原則更新。
