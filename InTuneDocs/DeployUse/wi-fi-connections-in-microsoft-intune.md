---
# required metadata

title: Wi-Fi 連線 | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 中的 Wi-Fi 連線
使用 Microsoft Intune Wi-Fi 設定檔，將無線網路設定部署給您組織中的使用者與裝置。 這些設定可簡化無線網路的使用者連線。

例如，您安裝名為 Contoso Wi-fi 的新 Wi-fi 網路，而且想要將所有 iOS 裝置都設定為連線至此網路。 程序如下︰

1.   建立 Wi-Fi 設定檔，內含連線到 Contoso Wi-Fi 無線網路所需的設定。

2. 將設定檔部署至具備 iOS 裝置的使用者群組。

3.   使用者在無線網路清單中發現新的 Contoso Wi-Fi 網路，而且可以輕鬆地連線到這個網路。

您可以將 Wi-Fi 設定檔部署到下列平台：

-   Android 4.0 及更新版本

-   iOS 7.1 和更新版本

-   Mac OS X 10.9 及更新版本

針對執行 Windows 8.1 和更新版本的裝置，您可以匯入先前匯出至檔案的 Wi-Fi 組態設定檔。 如需詳細資料，請參閱本主題稍後的匯入 Wi-fi 設定檔。

## 如何建立 Wi-Fi 設定檔

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，按一下 [原則] &gt; [新增原則]

2.  選取下列原則類型的其中一項，然後按一下 [建立原則] ：

    -   **Wi-Fi 設定檔 (Android 4 和更新版本)**

    -   **Wi-Fi 設定檔 (iOS 7.1 和更新版本)**

    -   **Wi-Fi 設定檔 (Mac OS X 10.9 及更新版本)**

    沒有針對此原則類型的建議設定。 您必須建立自訂原則。

3.  提供設定檔的名稱和說明。

4. 指定 [網路連線]  值：

  |設定|詳細資訊| 網路名稱|指定無線網路的描述性名稱。 這是選擇無線網路時將顯示在使用者裝置上的名稱。|

5. SSID (服務組識別元)|指定您想讓裝置連線的無線網路 (SSID)。 SSID 區分大小寫，且不會向使用者顯示。|

  #### 當這個網路在範圍內時自動連線|選取此選項，當無線網路位於範圍內時自動將裝置連線至該網路。|

  在網路未廣播其名稱 (SSID) 時進行連線|選取此選項，使裝置能在網路未列於網路清單時 (因為網路已隱藏且未廣播其名稱) 仍可連線到網路。|<br /><br />-   **設定所選平台的 [安全性設定]  。**<br />-   可用的設定取決於您選取的安全性類型。<br /><br />-   **Android 裝置**<br />-   **|設定名稱|詳細資訊|使用時機：|**<br />-   安全性類型|選取無線網路的安全性通訊協定： WPA-Enterprise/WPA2-Enterprise<br /><br />-   無驗證 (開放) 如果網路不安全。|一律|<br />-   EAP 類型|選擇用來驗證安全無線連線的可延伸驗證通訊協定 (EAP) 類型：<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TTLS|您已選取 [WPA-Enterprise/WPA2-Enterprise] 安全性類型。|**<br />-   **選取根憑證以進行伺服器驗證|按一下 [選取]，然後選擇受信任的根憑證設定檔，用來驗證連線。**<br />-   **重要事項：若要建立受信任的根憑證設定檔，請參閱[利用憑證設定檔安全存取公司資源](secure-resource-access-with-certificate-profiles.md)。|選取任何 EAP 類型。|**<br /><br />驗證方法|選取連線的驗證方法： [憑證] 用來指定用戶端憑證 使用者名稱和密碼可指定不同的驗證方法|EAP 類型 為 PEAP 或 EAP-TTLS 選取非 EAP 方法進行驗證 (內部識別)|選取驗證連線的方式︰

  #### 無

  未加密的密碼 (PAP)<br /><br />-   **Challenge Handshake 驗證通訊協定 (CHAP)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP 版本 2 (MS-CHAP v2)**<br />-   可用的選項取決於您所選取的 EAP 類型。|驗證方法是使用者名稱和密碼<br /><br />-   **啟用識別隱私權 (外部識別)|指定回應 EAP 識別要求時傳送的文字。**<br />-   **此文字可以是任何值。**<br />-   **在驗證期間，一開始會先傳送此匿名識別，隨後以安全通道傳送真正的識別。|EAP 類型為 PEAP 或 EAP-TTLS**<br />-   **選取用戶端憑證以進行用戶端驗證 (識別憑證)|按一下 [選取]，然後選擇用來驗證連線的 SCEP 憑證設定檔。**<br />-   **重要︰若要建立 SCEP 憑證設定檔，請參閱[使用憑證設定檔保護資源存取](secure-resource-access-with-certificate-profiles.md)。|安全性類型是 WPA-Enterprise/WPA2-Enterprise，且選取任何 EAP 類型。|**<br />-   iOS 和 Mac OS X 裝置 |設定名稱|詳細資訊|使用時機：| 安全性類型|選取無線網路安全性通訊協定：<br /><br />WPA-Personal/WPA2-Personal<br /><br /><ul><li>WPA-Enterprise/WPA2-Enterprise</li><li>WEP<br /><br /><ul><li>**無驗證 (開放) 如果網路不安全。|一律|**</li><li>**EAP 類型|選擇用來驗證安全無線連線的可延伸驗證通訊協定 (EAP) 類型：**</li><li>**EAP-TLS**</li><li>**PEAP**</li><li>**EAP-TLS**</li><li>**EAP-AST**</li></ul></li></ul>LEAP EAP-SIM|您已選取 WPA-Enterprise/WPA2-Enterprise 安全性類型 受信任的伺服器憑證名稱|選取受信任的根憑證設定檔，用來驗證連線。<br /><br />重要：若要建立受信任的根憑證設定檔，請參閱[利用憑證設定檔安全存取公司資源](secure-resource-access-with-certificate-profiles.md)。|您已選取 EAP-TLS、PEAP、EAP-TTLS 或 EAP-FAST 的 EAP 類型

6. 使用保護存取認證 (PAC)|請選取此項目，以使用受保護的存取認證，用來建立用戶端與驗證伺服器之間已驗證的通道。

    |會使用現有的 PAC 檔案 (如果有的話)。|EAP 類型為 EAP-FAST|佈建 PAC|佈建 PAC 檔案到您的裝置。|使用時，您也可以選取 [匿名佈建 PAC]  以確保 PAC 檔案已佈建，而不需驗證伺服器。|已選取使用保護存取認證 (PAC)。||
    |----------------|-------------------|-------------|
    |**驗證方法|選取用來連線的驗證方法：**|[憑證] 用來指定用戶端憑證<br /><br />-   [使用者名稱和密碼] 用來指定下列非 EAP 方法的其中一種以進行驗證 (也稱為內部識別)：<br />-   無<br />-   未加密的密碼 (PAP)|Challenge Handshake 驗證通訊協定 (CHAP)|
    |Microsoft CHAP (MS-CHAP)|Microsoft CHAP 版本 2 (MS-CHAP v2)|EAP-TLS|
    |**|EAP 類型是 PEAP 或 EAP-TTLS。**|選取用戶端憑證以進行用戶端驗證 (識別憑證)|選取用來驗證連線的 SCEP 憑證設定檔。|重要︰若要建立 SCEP 憑證設定檔，請參閱[使用憑證設定檔保護資源存取](secure-resource-access-with-certificate-profiles.md)。|當安全性類型是 WPA-Enterprise/WPA2-Enterprise，且 EAP 類型為 EAP-TLS、PEAP 或 EAP-TTLS 時|

7.  啟用識別隱私權 (外部識別)|指定回應 EAP 識別要求時傳送的文字。

此文字可以是任何值。 在驗證期間，一開始會先傳送此匿名識別，隨後以安全通道傳送真正的識別。|當 EAP 類型為 PEAP、EAP-TTLS 或 EAP-FAST 時

## (僅限 iOS 和 MAC OS X) 設定 Proxy 設定

### 設定名稱
詳細資訊 使用時機：

1.  此 Wi-Fi 連線的 Proxy 設定

2.  選擇 Proxy 設定類型：

3.  無 (預設值)  手動 -   手動指定 Proxy 伺服器的 URL 和連接埠號碼。

4.  自動 - 使用設定檔來設定 Proxy 伺服器。

## 永遠
[Proxy 伺服器位址] 和 [連接埠號碼] 指定 Proxy 伺服器的 URL 和連接埠編號。

1.  [此 Wi-Fi 連線的 Proxy 設定] 設為 [手動]

2.  Proxy 伺服器 URL

    指定包含 Proxy 伺服器設定之檔案的 URL。 [此 Wi-Fi 連線的 Proxy 設定] 設為 [自動]

3.  儲存 Wi-Fi 設定檔

    |新的原則會顯示在 [原則] 工作區的 [設定原則] 節點中。|如需部署設定檔的資訊，請參閱後續步驟。|
    |----------------|--------------------|
    |**匯出或匯入 Wi-Fi 設定檔 (僅當使用 Windows 8.1 和更新版本時)**|匯出 Wi-Fi 設定檔|
    |**在 Windows 中，您可以使用 netsh wlan 公用程式，將現有的 Wi-Fi 設定檔匯出至可由 Intune 讀取的 XML 檔案。**|在已安裝必要 Wi-Fi 設定檔的 Windows 電腦上，請遵循下列程序。|

4.  建立所匯出 W-Fi 設定檔的本機資料夾，例如 c:\WiFi

    |以系統管理員身分開啟命令提示字元。|執行命令 `netsh wlan show profiles`，並記下您想要匯出的設定檔名稱。|
    |----------------|--------------------|
    |**在此範例中，設定檔名稱是 WiFiName**|執行這個命令︰`netsh wlan export profile name="ProfileName" folder=c:\Wifi`。這會在目標資料夾中建立名為 “Wi-Fi-WiFiName.xml” 的 Wi-Fi 設定檔。|
    |**匯入 Wi-Fi 設定檔**|使用 [Windows Wi-Fi 匯入原則] 匯入一組 Wi-Fi 設定，然後您可將其部署至所需的使用者或裝置群組。|
    |**Wi-Fi 設定檔的匯出程序描述於**|在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，按一下 [原則] &gt; [新增原則]|

5.  設定類型的原則，請按 [Windows]  &gt;  [Windows Wi-Fi 匯入原則]

6.  您只能建立和部署自訂 Windows Wi-Fi 匯入原則。

## 沒有建議的設定。

1.  指定下列的 Windows Wi-Fi 匯入原則一般值：

2.  設定名稱

    -   詳細資訊

    -   Name


輸入 Wi-Fi 設定檔的唯一名稱，協助您在 Intune 主控台中識別該 Wi-Fi 設定檔。 說明


<!--HONumber=May16_HO2-->


