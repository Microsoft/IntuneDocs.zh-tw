---
title: Wi-Fi 連線
description: 使用 Wi-Fi 設定檔協助使用者連線至您的 Wi-Fi 網路。
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5eebe251371d466421bfe936a1f991c988e490b0
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="configure-devices-to-connect-to-your-corporate-wi-fi-networks"></a>將裝置設為連接至您的公司 Wi-Fi 網路

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

使用 Microsoft Intune Wi-Fi 設定檔，將無線網路設定部署給您組織中的使用者與裝置。 當您部署 Wi-Fi 設定檔時，您的使用者不需要自行設定即可存取公司的 Wi-Fi。

例如，您安裝名為 **Contoso Wi-fi** 的新 Wi-fi 網路，而且想要將所有 iOS 裝置都設定為連線至此網路。 程序如下︰

![Wi-Fi 設定檔程序摘要](../media/wi-fi-process-diagram.png)

1.   建立 Wi-Fi 設定檔，內含連線到 **Contoso Wi-Fi** 無線網路所需的設定。

2.   將設定檔部署至具備 iOS 裝置的使用者群組。

3.   使用者在無線網路清單中發現新的 **Contoso Wi-Fi** 網路，而且可以輕鬆地連線到這個網路。


## <a name="create-a-wi-fi-profile"></a>建立 Wi-Fi 設定檔

您可以將 Wi-Fi 設定檔部署到下列平台：

-   Android 4.0 及更新版本

-   Android for Work   

-   iOS 8.0 和更新版本

-   Mac OS X 10.9 及更新版本

針對執行 Windows 8.1 或是 Windows 10 Desktop 或行動裝置版作業系統的裝置，您可以匯入先前匯出至檔案的 Wi-Fi 組態設定檔。 如需詳細資料，請參閱[匯出或匯入 Windows 裝置的 Wi-Fi 設定檔](#export-or-import-a-wi-fi-configuration-profile-for-windows-devices)。

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com) 中，選擇 [原則] &gt; [新增原則]。

2.  選取下列其中一個原則類型，然後選擇 [建立原則]：

    -   Wi-Fi 設定檔 (Android 4 和更新版本)

    -   Wi-Fi 設定檔 (Android for Work)

    -   Wi-Fi 設定檔 (iOS 8.0 和更新版本)

    -   Wi-Fi 設定檔 (Mac OS X 10.9 及更新版本)


沒有針對此原則類型的建議設定。 您必須建立自訂原則。

3. 提供設定檔的名稱和說明。

4. 指定 [網路連線]  值。
   - **SSID (服務組識別元)**︰如果您想讓使用者看到網路名稱而不是 SSID，請選取此選項。
   - **在網路未廣播其名稱 (SSID) 時進行連線**：選取此選項，使裝置能在網路未列於網路清單時 (因為網路已隱藏且未廣播其名稱) 仍可連線到該網路。

5. 設定所選平台的 [安全性設定]  。 可用的設定取決於您選取的安全性類型。 相關說明請參閱[安全性設定](#security-settings)。

6. 設定 「Proxy 設定」 (僅限 iOS 和 MAC OS X)。


   |                              設定名稱                              |                                                                                                                                詳細資訊                                                                                                                                 |                                            使用時機                                            |
   |------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
   |       <strong>此 Wi-Fi 連線的 Proxy 設定</strong>        | 選擇 Proxy 設定類型：<br /><br />-   <strong>無</strong> (預設)<br />-   <strong>手動</strong> - 手動指定 Proxy 伺服器的 URL 及連接埠號碼。<br />-   <strong>自動</strong> - 使用組態檔來設定 Proxy 伺服器。 |                                              永遠                                               |
   | [Proxy 伺服器位址] 和 [連接埠號碼] |                                                                                                              指定 Proxy 伺服器的 URL 和連接埠編號。                                                                                                               |  如果將 [此 Wi-Fi 連線的 Proxy 設定] 設為 [手動]   |
   |                   <strong>Proxy 伺服器 URL</strong>                    |                                                                                                      指定包含 Proxy 伺服器設定之檔案的 URL。                                                                                                       | 如果將 [此 Wi-Fi 連線的 Proxy 設定] 設為 [自動] |


7. 儲存 Wi-Fi 設定檔

新的原則會顯示在 [原則] 工作區的 [設定原則] 節點中。 如需部署設定檔的資訊，請參閱**後續步驟**。

## <a name="export-or-import-a-wi-fi-configuration-profile-for-windows-devices"></a>匯出或匯入 Windows 裝置的 Wi-Fi 設定檔

針對執行 Windows 8.1 或是 Windows 10 Desktop 或行動裝置版作業系統的裝置，您可以匯入先前匯出至檔案的 Wi-Fi 組態設定檔。

### <a name="export-a-wi-fi-profile"></a>匯出 Wi-Fi 設定檔
在 Windows 中，您可以使用 **netsh wlan** 公用程式，將現有的 Wi-Fi 設定檔匯出至 Intune 可讀取的 XML 檔案。 在已安裝必要 Wi-Fi 設定檔的 Windows 電腦上，採用下列步驟：

1.  為匯出的 W-Fi 設定檔建立本機資料夾。 例如，建立名為 **c:\WiFi** 的資料夾。

2.  以系統管理員身分開啟命令提示字元。

3.  執行命令 `netsh wlan show profiles`，並記下您想要匯出的設定檔名稱。  在此範例中，設定檔名稱是 **WiFiName**。

4.  執行這個命令︰`netsh wlan export profile name="ProfileName" folder=c:\Wifi`。這會在目標資料夾中建立名為 **Wi-Fi-WiFiName.xml** 的 Wi-Fi 設定檔。

### <a name="import-a-wi-fi-profile"></a>匯入 Wi-Fi 設定檔
使用 [Windows Wi-Fi 匯入原則] 匯入一組 Wi-Fi 設定，然後您可將其部署至所需的使用者或裝置群組。


1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com) 中按一下 [原則] &gt; [新增原則]。

2.  設定類型的原則：[Windows] &gt; [Wi-Fi 匯入 (Windows 8.1 及更新版本)]。

    這個原則可以套用至執行 Windows 8.1 以及 Windows 10 Desktop 和行動裝置版作業系統的裝置。

    您只能建立和部署自訂的 Windows Wi-Fi 匯入原則。 沒有建議的設定。

3.  指定下列的 Windows Wi-Fi 匯入原則一般值：

    |設定名稱|詳細資訊|
    |----------------|--------------------|
    |**名稱**|輸入 Wi-Fi 設定檔的唯一名稱，協助您在 Intune 主控台中識別該 Wi-Fi 設定檔。|
    |**描述**|提供 Wi-Fi 設定檔的描述以及協助您找到它的其他相關資訊。|

4.  指定下列的 [自訂 Wi-Fi 設定檔] 標題值：

    |設定名稱|詳細資訊|
    |----------------|--------------------|
    |**組態設定檔**|選擇 [匯入]，以選取包含您想匯入 Intune 之 Wi-Fi 設定檔的 XML 檔案。|
    |**自訂組態設定檔名稱 (對使用者顯示)**|選擇將如何顯示 Wi-Fi 設定檔的名稱，如同使用者裝置上所顯示。|
    |**組態設定檔詳細資料**|選擇如何顯示您所選擇之組態設定檔的 XML 程式碼。|

5.  完成之後，請選擇 [儲存原則]。

6.  新的原則會顯示在 [原則]  工作區的 [設定原則]  節點中。

## <a name="deploy-the-profile"></a>部署設定檔

由於設定檔是一種原則類型，您可以使用 [原則] 工作區加以部署。

1.  在 [原則] 工作區中，選取您要部署的原則，然後選擇 [管理部署]。

2.  在 [管理部署]  對話方塊中：

    -   **若要部署原則**：選取要部署原則的一個或多個群組。 然後選擇 [新增] &gt; [確定]。

    -   **若要關閉對話方塊而不加以部署**：按一下 [取消]。


[原則] 工作區的 [概觀] 頁面會顯示需要您特別注意的原則問題。 此外，狀態摘要還會顯示在 [儀表板] 工作區中。

## <a name="security-settings"></a>安全性設定
這些資料表有安全性設定的詳細資料，可供 Android、iOS 及 Mac OS X Wi-Fi 設定檔使用。

### <a name="security-settings-for-android-devices"></a>Android 裝置的安全性設定

  |設定名稱|詳細資訊|使用時機|
|----------------|--------------------|-------------|
|**安全性類型**|選取無線網路的安全性通訊協定：<br /><br />-   **WPA-Enterprise/WPA2-Enterprise**<br />若為不安全的網路，請選取 [不驗證 (開放)]-   。|永遠|
|**EAP 類型**|選擇用來驗證安全無線連線的可延伸驗證通訊協定 (EAP) 類型：<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TTLS**|如果您已選取 [WPA-Enterprise/WPA2-Enterprise] 安全性類型。|
|**選取伺服器驗證用的根憑證**|選擇 [選取]，然後選擇受信任的根憑證設定檔，以用來驗證連線。 如需建立受信任的根憑證設定檔的詳細資訊，請參閱[使用憑證設定檔保護資源存取](secure-resource-access-with-certificate-profiles.md)。|如果您已選取任一種 [EAP 類型]。|
|**驗證方法**|選取用於連線的驗證方法：<br /><br />用以指定用戶端憑證的-   **憑證**<br />用以指定其他驗證方法的-   **使用者名稱及密碼**|[EAP 類型] 是 [PEAP] 或 [EAP-TTLS]。|
|**選取 EAP 以外的方法進行驗證 (內部識別)**|選取您驗證連線的方式：<br /><br />-   **無**<br />-   **未加密的密碼 (PAP)**<br />-   **Challenge Handshake 驗證通訊協定 (CHAP)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP 第 2 版 (MS-CHAP v2)**<br /><br />可用的選項取決於您所選取的 EAP 類型。|[驗證方法]  是 [使用者名稱和密碼] 。|
|**啟用識別隱私權 (外部識別)**|指定在回應 EAP 識別要求時傳送的文字。 此文字可以是任何值。 在驗證期間，最初會傳送此匿名身分識別。 然後在安全通道中傳送真實的身分識別。|如果 [EAP 類型] 是 [PEAP] 或 [EAP-TTLS]。|
|**選取用戶端驗證的用戶端憑證 (身分識別憑證)**|選擇 [選取]，然後選擇 SCEP 憑證設定檔，以用來驗證連線。 如需建立 SCEP 憑證設定檔的詳細資訊，請參閱[使用憑證設定檔保護資源存取](secure-resource-access-with-certificate-profiles.md)。|如果安全性類型是 [WPA-Enterprise/WPA2-Enterprise]，且已選取任一種 [EAP 類型]。|

### <a name="security-settings-for-ios-and-mac-os-x-devices"></a>iOS 及 Mac OS X 裝置的安全性設定

  |設定名稱|詳細資訊|使用時機|
|----------------|--------------------|-------------|
|**安全性類型**|選取無線網路安全性通訊協定：<br /><br />-   **WPA-Personal/WPA2-Personal**<br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **WEP**<br />若為不安全的網路，請選取 [不驗證 (開放)]-   。|永遠|
|**EAP 類型**|選擇用來驗證安全無線連線的可延伸驗證通訊協定 (EAP) 類型：<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TLS**<br />-   **EAP-AST**<br />-   **LEAP**<br />-   **EAP-SIM**|如果您已選取 [WPA-Enterprise/WPA2-Enterprise] 安全性類型。|
|**信任的伺服器憑證名稱**|選取受信任的根憑證設定檔，以用來驗證連線。 如需建立受信任的根憑證設定檔的詳細資訊，請參閱[使用憑證設定檔保護資源存取](secure-resource-access-with-certificate-profiles.md)。|如果您已選取 [EAP-TLS]、[PEAP]、[EAP-TTLS] 或 [EAP-FAST] 的其中一種 EAP 類型。|
|**使用受保護的存取認證 (PAC)**|請選取此項目，以使用受保護的存取認證，用來建立用戶端與驗證伺服器之間已驗證的通道。 會使用現有的 PAC 檔案 (如果有的話)。|如果 [EAP 類型] 是 [EAP-FAST]。|
|**佈建 PAC**|在您的裝置上設定 PAC 檔案。<br /><br />使用時，您也可以選取 [匿名佈建 PAC]  以確保 PAC 檔案已設定，而不需驗證伺服器。|如果已選取 [使用受保護的存取認證 (PAC)]。|
|**驗證方法**|選取用於連線的驗證方法：<br /><br /><ul><li>[憑證] 用來指定用戶端憑證</li><li>[使用者名稱和密碼] 用來指定下列非 EAP 方法的其中一種以進行驗證 (也稱為內部識別)：<br /><br /><ul><li>**無**</li><li>**未加密的密碼 (PAP)**</li><li>**Challenge Handshake 驗證通訊協定 (CHAP)**</li><li>**Microsoft CHAP (MS-CHAP)**</li><li>**Microsoft CHAP 第 2 版 (MS-CHAP v2)**</li><li>**EAP-TLS**</li></ul></li></ul>|如果 [EAP 類型] 是 [PEAP] 或 [EAP-TTLS]。|
|**選取用戶端驗證的用戶端憑證 (身分識別憑證)**|選取用來驗證連線的 SCEP 憑證設定檔。 如需建立 SCEP 憑證設定檔的詳細資訊，請參閱[使用憑證設定檔保護資源存取](secure-resource-access-with-certificate-profiles.md)。|如果安全性類型是 [WPA-Enterprise/WPA2-Enterprise]，且 [EAP 類型] 是 [EAP-TLS]、[PEAP] 或 [EAP-TTLS]。|
|**啟用識別隱私權 (外部識別)**|指定在回應 EAP 識別要求時傳送的文字。 此文字可以是任何值。<br /><br />在驗證期間，最初會傳送此匿名身分識別。 然後在安全通道中傳送真實的身分識別。|如果 [EAP 類型] 設為 [PEAP]、[EAP-TTLS] 或 [EAP-FAST]。|


### <a name="see-also"></a>另請參閱
在[預先共用金鑰 Wi-Fi 設定檔](pre-shared-key-wi-fi-profile.md)中，了解如何使用預先共用的金鑰來建立 Wi-Fi 設定檔。
