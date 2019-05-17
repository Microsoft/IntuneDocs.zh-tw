---
title: 建立包含預先共用金鑰的 Wi-Fi 設定檔 - Microsoft Intune - Azure | Micrososft Docs
description: 使用自訂設定檔建立包含預先共用金鑰的 Wi-Fi 設定檔，在 Microsoft Intune 中取得 Android、Windows 和 EAP 型 Wi-Fi 設定檔的範例 XML 程式碼
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7bf859075e675ef0205b24e0575fca5ab74f312c
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "59566980"
---
# <a name="use-a-custom-device-profile-to-create-a-wifi-profile-with-a-pre-shared-key---intune"></a>使用自訂裝置設定檔建立包含預先共用金鑰的 Wi-Fi 設定檔 - Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

預先共用的金鑰 (PSK) 通常用來驗證 WiFi 網路或無線區域網路的使用者。 使用 Intune，您可以建立使用預先共用金鑰的 WiFi 設定檔。 若要建立設定檔，請使用 Intune 中的**自訂裝置設定檔**功能。 本文也包含如何建立 EAP 型 Wi-Fi 設定檔的一些範例。

> [!IMPORTANT]
>- 搭配 Windows 10 使用預先共用金鑰會導致在 Intune 中出現補救錯誤。 發生這種情況時，系統會將 Wi-Fi 設定檔適當地指派給裝置，而該設定檔將如預期般運作。
>- 如果您要匯出包含預先共用金鑰的 Wi-Fi 設定檔，請確定該檔案受到保護。 該金鑰會採用存文字格式，因此您需負責保護該金鑰。

## <a name="before-you-begin"></a>開始之前

- 從連線到該網路的電腦複製程式碼可能比較容易，如本文稍後所述。
- 您可以新增更多 OMA URI 設定，以新增多個網路和金鑰。
- 若為 iOS，請使用 Mac 站上的 Apple Configurator 來設定設定檔。
- PSK 需要 64 個十六進位數字的字串，或是 8 到 63 個可列印 ASCII 字元的複雜密碼。 不支援某些字元，例如星號 (*)。

## <a name="create-a-custom-profile"></a>建立自訂設定檔
您可以為 Android、Windows 或 EAP 型 Wi-Fi 設定檔建立包含預先共用金鑰的自訂設定檔。 若要使用 Azure 入口網站建立設定檔，請參閱[建立自訂裝置設定](custom-settings-configure.md)。 當您建立裝置設定檔時，請選擇 [自訂] 您的裝置平台。 請勿選取 Wi-Fi 設定檔。 當您選擇自訂時，請務必： 

1. 輸入設定檔的名稱和描述。
2. 新增具有下列屬性的新 OMA-URI 設定： 

   a. 輸入此 Wi-Fi 網路設定的名稱。

   b. (選擇性) 輸入 OMA-URI 設定的描述，或者保留空白。

   c. 將 [資料類型] 設定為 **String**。

   d. **OMA-URI**：

   - **適用於 Android**：./Vendor/MSFT/WiFi/Profile/SSID/Settings
   - **適用於 Windows**：./Vendor/MSFT/WiFi/Profile/SSID/WlanXml

     > [!NOTE]
     > 開頭務必包含點號字元。

     SSID 是您要建立原則的 SSID。 例如，輸入 `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`。

   e. **值欄位**是貼上 XML 程式碼的位置。 請參閱本文中的範例。 更新每個值使符合您的網路設定。 程式碼的註解區段包含一些指標。
3. 選取 [確定] 並儲存，然後指派原則。

    > [!NOTE]
    > 此原則僅能指派給使用者群組。

每個裝置下一次簽入時，都會套用此原則，並在裝置上建立 Wi-Fi 設定檔。 然級裝置就可以自動連線到網路。

## <a name="android-or-windows-wi-fi-profile-example"></a>Android 或 Windows Wi-Fi 設定檔範例

下例包含 Android 或 Windows Wi-Fi 設定檔的 XML 程式碼。 提供此範例是為了顯示適當的格式，並提供更多的詳細資料。 它只是範例，不適合作為您環境的建議設定。

> [!IMPORTANT]
>
> - `<protected>false</protected>` 務必設定為 **false**。 設定為 **true** 時，可能會使裝置預期有加密的密碼，然後嘗試將它解密，而導致連線失敗。
>
> - `<hex>53534944</hex>` 應設定為 `<name><SSID of wifi profile></name>` 的十六進位值。
>  Windows 10 裝置可能會傳回誤報的 *0x87D1FDE8 補救失敗*錯誤，但將置仍會包含設定檔。
>
> - XML 包含特殊字元，例如：`&` (& 符號)。 使用特殊字元可能會導致 XML 無法如預期般運作。 

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
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial>password</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

## <a name="eap-based-wi-fi-profile-example"></a>EAP 型 Wi-Fi 設定檔範例
下例包含 EAP 型 Wi-Fi 設定檔的 XML 程式碼：提供此範例是為了顯示適當的格式，並提供更多的詳細資料。 它只是範例，不適合作為您環境的建議設定。


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
您也可以使用下列步驟，從現有的 Wi-Fi 連線建立 XML 檔案： 

1. 在已連線到或最近已連線到無線網路的電腦上，開啟 `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}` 資料夾。

   最好使用未連線至太多無線網路的電腦。 否則，您可能必須搜尋每個設定檔才能找到正確的設定檔。

2. 搜尋 XML 檔案，找出有名稱正確的檔案。
3. 找到正確的 XML 檔案後，將 XML 程式碼複製並貼入 OMA-URI 設定頁面的 [資料] 欄位。

## <a name="best-practices"></a>最佳作法
- 以 PSK 部署 Wi-Fi 設定檔之前，請確認裝置可以直接連接至端點。

- 當輪替金鑰 (密碼或複雜密碼) 時，預期據此停機和規劃您的部署。 請考慮在非工作時間推送新的 Wi-Fi 設定檔。 此外，警告使用者連線可能會受到影響。

- 為確保轉換順利，請確定使用者的裝置具備其他網際網路連線。 例如，使用者必須能夠切換回客體 WiFi (或某些其他 WiFi 網路)，或能夠使用行動電話與 Intune 連線通訊。 當裝置更新公司的 WiFi 設定檔時，額外的連線可讓使用者接收原則更新。
