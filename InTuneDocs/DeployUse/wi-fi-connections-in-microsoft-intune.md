---
title: "Wi-Fi 連線 | Microsoft Intune"
description: "使用 Wi-Fi 設定檔協助使用者連線至您的 Wi-Fi 網路。"
keywords: 
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.date: 10/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 27ba29f57bba1f3807c4b593ecac8c0af0851962
ms.openlocfilehash: 7b49b7d9b6054f7d153359c1ee1b6cf5875fba32


---

# 將裝置設為連接至您的公司 Wi-Fi 網路

使用 Microsoft Intune Wi-Fi 設定檔，將無線網路設定部署給您組織中的使用者與裝置。 若您部署 Wi-Fi 設定檔，您的使用者不需要自行設定即可存取您公司的 Wi-Fi。

例如，您安裝名為 **Contoso Wi-fi** 的新 Wi-fi 網路，而且想要將所有 iOS 裝置都設定為連線至此網路。 程序如下︰

![Wi-Fi 設定檔程序摘要](..\media\wi-fi-process-diagram.png) 

1.   建立 Wi-Fi 設定檔，內含連線到 **Contoso Wi-Fi** 無線網路所需的設定。

2.   將設定檔部署至具備 iOS 裝置的使用者群組。

3.   使用者在無線網路清單中發現新的 **Contoso Wi-Fi** 網路，而且可以輕鬆地連線到這個網路。


## 如何建立 Wi-Fi 設定檔

您可以將 Wi-Fi 設定檔部署到下列平台：

-   Android 4.0 及更新版本

-   Android for Work   

-   iOS 8.0 和更新版本

-   Mac OS X 10.9 及更新版本

針對執行 Windows 8.1 或 Windows 10 Desktop 或行動裝置版的裝置，您可以匯入先前匯出至檔案的 Wi-Fi 組態設定檔。 如需詳細資料，請參閱 [匯出或匯入 Windows 裝置的 Wi-Fi 設定檔](#export-or-import-a-wi-fi-configuration-profile-for-windows-devices)。

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com) 中按一下 [原則] &gt; [新增原則]。

2.  選取下列原則類型的其中一項，然後按一下 [建立原則] ：

    -   Wi-Fi 設定檔 (Android 4 和更新版本)

    -   Wi-Fi 設定檔 (Android for Work)

    -   Wi-Fi 設定檔 (iOS 8.0 和更新版本)

    -   Wi-Fi 設定檔 (Mac OS X 10.9 及更新版本)
    
    
    沒有針對此原則類型的建議設定。 您必須建立自訂原則。

3.  提供設定檔的名稱和說明。

4. 指定 [網路連線]  值。
 - **SSID (服務組識別元)**︰使用者會看見網路名稱，而非 SSID。
 - **在網路未廣播其名稱 (SSID) 時進行連線**選取此選項，使裝置能在網路未列於網路清單時 (因為網路已隱藏且未廣播其名稱) 仍可連線到網路。
 
5. 設定所選平台的 [安全性設定]  。 可用的設定取決於您選取的安全性類型，並詳述於[安全性設定](#security-settings)。

6. (僅限 iOS 和 MAC OS X) 設定 **Proxy 設定**

    |設定名稱|詳細資訊|使用時機：|
    |----------------|-------------------|-------------|
    |**此 Wi-Fi 連線的 Proxy 設定**|選擇 Proxy 設定類型：<br /><br />-   **無** (預設值)<br />-   **手動** -   手動指定 Proxy 伺服器的 URL 和連接埠號碼。<br />-   **自動** - 使用設定檔來設定 Proxy 伺服器。|永遠|
    |[Proxy 伺服器位址] 和 [連接埠號碼]|指定 Proxy 伺服器的 URL 和連接埠編號。|[此 Wi-Fi 連線的 Proxy 設定] 設為 [手動]|
    |**Proxy 伺服器 URL**|指定包含 Proxy 伺服器設定之檔案的 URL。|[此 Wi-Fi 連線的 Proxy 設定] 設為 [自動]|

7.  儲存 Wi-Fi 設定檔

新的原則會顯示在 [原則] 工作區的 [設定原則] 節點中。 如需部署設定檔的資訊，請參閱**後續步驟**。

## 匯出或匯入 Windows 裝置的 Wi-Fi 設定檔
 
針對執行 Windows 8.1 或 Windows 10 Desktop 或行動裝置版的裝置，您可以匯入先前匯出至檔案的 Wi-Fi 組態設定檔。 

### 匯出 Wi-Fi 設定檔
在 Windows 中，您可以使用 **netsh wlan** 公用程式，將現有的 Wi-Fi 設定檔匯出至可由 Intune 讀取的 XML 檔案。 在已安裝必要 Wi-Fi 設定檔的 Windows 電腦上，請遵循下列程序。

1.  建立所匯出 W-Fi 設定檔的本機資料夾，例如 c:\WiFi

2.  以系統管理員身分開啟命令提示字元。

3.  執行命令 `netsh wlan show profiles`，並記下您想要匯出的設定檔名稱。  在此範例中，設定檔名稱是 *WiFiName*。

4.  執行這個命令︰`netsh wlan export profile name="ProfileName" folder=c:\Wifi`。這會在目標資料夾中建立名為 “Wi-Fi-WiFiName.xml” 的 Wi-Fi 設定檔。

### 匯入 Wi-Fi 設定檔
使用 [Windows Wi-Fi 匯入原則] 匯入一組 Wi-Fi 設定，然後您可將其部署至所需的使用者或裝置群組。


1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com) 中按一下 [原則] &gt; [新增原則]。

2.  設定類型的原則：[Windows] &gt; [Wi-Fi 匯入 (Windows 8.1 及更新版本)]。

    這個原則可以套用至 Windows 8.1 和 Windows 10 Desktop 和行動裝置版。

    您只能建立和部署自訂的 Windows Wi-Fi 匯入原則。 沒有建議的設定。

3.  指定下列的 Windows Wi-Fi 匯入原則一般值：

    |設定名稱|詳細資訊|
    |----------------|--------------------|
    |**Name**|輸入 Wi-Fi 設定檔的唯一名稱，協助您在 Intune 主控台中識別該 Wi-Fi 設定檔。|
    |**說明**|提供 Wi-Fi 設定檔的描述以及協助您找到它的其他相關資訊。|

4.  指定下列的 [自訂 Wi-Fi 設定檔] 標題值：

    |設定名稱|詳細資訊|
    |----------------|--------------------|
    |**組態設定檔**|按一下 [匯入] 選取包含您想匯入 Intune 之 Wi-Fi 設定檔的 XML 檔案。|
    |**自訂組態設定檔名稱 (會向使用者顯示)**|它將會顯示 Wi-Fi 設定檔的名稱，如同使用者裝置上所顯示的。|
    |**組態設定檔詳細資料**|顯示您所選取組態設定檔的 XML 程式碼。|

5.  完成之後，請按一下 [儲存原則] 。

6.  新的原則會顯示在 [原則]  工作區的 [設定原則]  節點中。

## 部署設定檔

設定檔是一種原則類型，因此使用 [原則] 工作區加以部署。

1.  在 [原則]  工作區中，選取您要部署的原則，然後按一下 [管理部署] 。

2.  在 [管理部署]  對話方塊中：

    -   **部署原則** - 選取您要部署原則的一或多個群組，然後按一下 [新增] &gt; [確定]。

    -   **關閉對話方塊但不加以部署** - 按一下 [取消]。


在 [原則]  工作區的 [概觀]  頁面上，狀態摘要和警示可識別需要注意的原則問題。 此外，狀態摘要還會顯示在 [儀表板] 工作區中。

## 安全性設定
這些資料表有安全性設定的詳細資料，可供 Android、iOS 及 Mac OS X Wi-Fi 設定檔使用。 

### Android 裝置的安全性設定

  |設定名稱|詳細資訊|使用時機：|
|----------------|--------------------|-------------|
|**安全性類型**|選取無線網路的安全性通訊協定：<br /><br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   如果使用無安全性網路，選取 [不驗證 (開放)]。|永遠|
|**EAP 類型**|選擇用來驗證安全無線連線的可延伸驗證通訊協定 (EAP) 類型：<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TTLS**|您已選取 [WPA-Enterprise/WPA2-Enterprise] 安全性類型。|
|**選取根憑證以進行伺服器驗證**|按一下 [選取] ，然後選擇受信任的根憑證設定檔，用來驗證連線。 **重要事項：**若要建立受信任的根憑證設定檔，請參閱[利用憑證設定檔安全存取公司資源](secure-resource-access-with-certificate-profiles.md)。|已選取所有 [EAP 類型]  。|
|**驗證方法**|選取連線的驗證方法：<br /><br />-   [憑證] 用來指定用戶端憑證<br />-   [使用者名稱和密碼] 用來指定不同的驗證方法|[EAP 類型] 是 [PEAP] 或 [EAP-TTLS]。|
|**選取非 EAP 驗證方法 (內部識別)**|選取您驗證連線的方式：<br /><br />-   **無**<br />-   **未加密的密碼 (PAP)**<br />-   **Challenge Handshake 驗證通訊協定 (CHAP)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP 版本 2 (MS-CHAP v2)**<br /><br />可用的選項取決於您所選取的 EAP 類型。|[驗證方法]  是 [使用者名稱和密碼] 。|
|**啟用識別隱私權 (外部識別)**|指定在回應 EAP 識別要求時傳送的文字。 此文字可以是任何值。 在驗證期間，一開始會先傳送此匿名識別，隨後以安全通道傳送真正的識別。|[EAP 類型] 是 [PEAP] 或 [EAP-TTLS]。|
|**選取用戶端憑證以進行用戶端驗證 (識別憑證)**|按一下 [選取] ，然後選擇 SCEP 憑證設定檔，用來驗證連線。 **重要事項：**若要建立 SCEP 憑證設定檔，請參閱[利用憑證設定檔安全存取公司資源](secure-resource-access-with-certificate-profiles.md)。|本安全性類型是 [WPA-Enterprise/WPA2-Enterprise]，且已選取所有 [EAP 類型]。|

### iOS 及 Mac OS X 裝置的安全性設定

  |設定名稱|詳細資訊|使用時機：|
|----------------|--------------------|-------------|
|**安全性類型**|選取無線網路安全性通訊協定：<br /><br />-   **WPA-Personal/WPA2-Personal**<br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **WEP**<br />-   如果使用無安全性網路，選取 [不驗證 (開放)]。|永遠|
|**EAP 類型**|選擇用來驗證安全無線連線的可延伸驗證通訊協定 (EAP) 類型：<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TLS**<br />-   **EAP-AST**<br />-   **LEAP**<br />-   **EAP-SIM**|您已選取 [WPA-Enterprise/WPA2-Enterprise] 安全性類型。|
|**受信任的伺服器憑證名稱**|選取受信任的根憑證設定檔，用來驗證連線。 **重要事項：**若要建立受信任的根憑證設定檔，請參閱[利用憑證設定檔安全存取公司資源](secure-resource-access-with-certificate-profiles.md)。|您已選取 [EAP-TLS]、[PEAP]、[EAP-TTLS] 或 [EAP-FAST] 的其中一種 EAP 類型。|
|**使用保護存取認證 (PAC)**|請選取此項目，以使用受保護的存取認證，用來建立用戶端與驗證伺服器之間已驗證的通道。 會使用現有的 PAC 檔案 (如果有的話)。|[EAP 類型] 是 [EAP-FAST]。|
|**佈建 PAC**|佈建 PAC 檔案到您的裝置。<br /><br />使用時，您也可以選取 [匿名佈建 PAC]  以確保 PAC 檔案已佈建，而不需驗證伺服器。|已選取 [使用受保護的存取認證 (PAC)] 。|
|**驗證方法**|選取連線的驗證方法：<br /><br /><ul><li>[憑證] 用來指定用戶端憑證</li><li>[使用者名稱和密碼] 用來指定下列非 EAP 方法的其中一種以進行驗證 (也稱為內部識別)：<br /><br /><ul><li>**無**</li><li>**未加密的密碼 (PAP)**</li><li>**Challenge Handshake 驗證通訊協定 (CHAP)**</li><li>**Microsoft CHAP (MS-CHAP)**</li><li>**Microsoft CHAP 版本 2 (MS-CHAP v2)**</li><li>**EAP-TLS**</li></ul></li></ul>|[EAP 類型] 是 [PEAP] 或 [EAP-TTLS]。|
|**選取用戶端憑證以進行用戶端驗證 (識別憑證)**|選取用來驗證連接的 SCEP 憑證設定檔。 **重要事項：**若要建立 SCEP 憑證設定檔，請參閱[利用憑證設定檔安全存取公司資源](secure-resource-access-with-certificate-profiles.md)。|當安全性類型是 [WPA-Enterprise/WPA2-Enterprise]，且 [EAP 類型] 是 [EAP-TLS]、[PEAP] 或 [EAP-TTLS]。|
|**啟用識別隱私權 (外部識別)**|指定在回應 EAP 識別要求時傳送的文字。 此文字可以是任何值。<br /><br />在驗證期間，一開始會先傳送此匿名識別，隨後以安全通道傳送真正的識別。|當 [EAP 類型] 設為 [PEAP]、[EAP-TTLS] 或 [EAP-FAST]。|


### 請參閱
在[預先共用金鑰 Wi-Fi 設定檔](pre-shared-key-wi-fi-profile.md)中了解如何使用預先共用金鑰來建立 Wi-Fi 設定檔



<!--HONumber=Oct16_HO2-->


