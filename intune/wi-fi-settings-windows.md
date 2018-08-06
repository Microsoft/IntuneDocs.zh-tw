---
title: Microsoft Intune 中適用於 Windows 10 裝置的 Wi-Fi 設定 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，使用適用於 Windows 10 和更新版本之裝置的 Wi-Fi 設定，新增或建立 Wi-Fi 組態設定檔。 您可以設定基本設定或企業層級設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f6532c63612b806f9824f5b9ca98f1ebbbc943f
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321624"
---
## <a name="wi-fi-settings-for-windows-10-and-later-devices-in-intune"></a>Intune 中適用於 Windows 10 和更新版本之裝置的 Wi-Fi 設定

Wi-Fi 設定用於組態設定檔，而組態設定檔則會套用至執行 Windows 10 和更新版本的裝置。 選項包含：

- 基本
- 企業

## <a name="before-you-begin"></a>開始之前

[建立裝置設定檔](device-profile-create.md)。

## <a name="settings-for-basic-and-enterprise-profiles"></a>適用於基本設定檔與企業設定檔的設定

- **Wi-Fi 名稱 (SSID)**：服務組識別元的簡稱。 此值是裝置要連線之無線網路的實際名稱。 但當使用者選擇此連線時，只會看到您設定的**連線名稱**。
- **連線名稱**：輸入此 Wi-Fi 連線的使用者易記名稱。 您輸入的文字是使用者瀏覽其裝置上可用連線時所見到的名稱。
- **在範圍內時自動連線**：如果為 [是]，裝置會於位在此網路範圍內時自動連線。 如果為 [否]，裝置不會自動連線。
  - **可用時連線到更慣用的網路**：如果裝置位在更慣用的網路範圍內，則選擇 [是] 以使用慣用的網路。 選擇 [否] 即會在此組態設定檔中使用 Wi-Fi 網路。

    例如，您可以建立 **ContosoCorp** Wi-Fi 網路，並在此組態設定檔內使用 **ContosoCorp**。 您也可以在範圍內包含 **ContosoGuest** Wi-Fi 網路。 當您的公司裝置位在範圍內時，您希望它們自動連線到 **ContosoCorp**。 在此案例中，請將 [可用時連線到更慣用的網路] 屬性設定為 [否]。

  - **即使未廣播其 SSID 也連線到此網路**：選擇 [是] ，即使網路是隱藏的 (亦即，未公開廣播其 SSID)，也讓組態設定檔自動連線到您的網路。 如果不想要這個組態設定檔連線到隱藏的網路，請選擇 [否]。

- **公司 Proxy 設定**：選擇使用您組織內的 Proxy 設定。 選項包括：
  - **無**：不設定任何 Proxy 設定。
  - **手動設定**：輸入 [Proxy 伺服器 IP 位址] 及其 [連接埠號碼]。
  - **自動設定**：輸入指向 Proxy 自動設定 (PAC) 指令碼的 URL。 例如，輸入 `http://proxy.contoso.com/proxy.pac`。

## <a name="settings-for-basic-profiles-only"></a>僅適用於基本設定檔的設定

- **無線安全性類型**：輸入用來驗證網路上裝置的安全性通訊協定。 選項包括：
  - **開放 (無驗證)**：只有在網路不安全時才使用此選項。
  - **WPA/WPA2-Personal**

## <a name="settings-for-enterprise-profiles-only"></a>僅適用於企業設定檔的設定

- **單一登入 (SSO)**：可讓您設定單一登入 (SSO)，其中認證會共用以進行電腦和 Wi-Fi 網路登入。 選項包括：
  - **停用**：停用 SSO 行為。 使用者必須分別向網路進行驗證。
  - **在使用者登入裝置之前啟用**：在使用者登入處理序之前，使用 SSO 向網路進行驗證。
  - **在使用者登入裝置之後啟用**：在使用者登入處理序完成之後，使用 SSO 立即向網路進行驗證。
  - **要在逾時之前驗證的時間上限**：輸入在向網路進行驗證之前要等待的秒數上限 (從 1 到 120 秒)。
  - **允許 Windows 提示使用者提供其他的驗證認證**：選擇 [是] 可讓 Windows 系統提示使用者提供驗證方法需要的其他認證。 選擇 [否] 即會隱藏這些提示。

- **啟用成對主鑰 (PMK) 快取**：選取 [是] 以快取驗證中使用的 PMK。 此快取通常可讓網路的驗證更快完成。 選擇 [否] 即會在每次連線到 Wi-Fi 網路時，強制驗證交握。

  - **PMK 儲存在快取中的最長時間**：輸入成對主鑰 (PMK) 儲存在快取中的分鐘數 (從 5 到 1440 分鐘)。
  - **PMK 儲存在快取中的數目上限**：輸入儲存在快取中的金鑰數目 (從 1 到 255)。

- **啟用預先驗證**：預先驗證可讓設定檔在連線之前，向設定檔中的所有網路存取點進行驗證。 在存取點之間移動時，預先驗證可更快速地重新連線使用者或裝置。 對設定檔選擇 [是]，即會向此網路中位於範圍內的所有存取點進行驗證。 選擇 [否] 則會要求使用者或裝置個別向每個存取點進行驗證。

  - **預先驗證嘗試次數上限**：輸入要預先驗證的嘗試次數 (從 1 到 16)。

- **EAP 類型**：選擇用來驗證安全無線連線的可延伸驗證通訊協定 (EAP) 類型。 選項包括：

  - **EAP-SIM**
  - **EAP-TLS**
  - **EAP-TTLS**
  - **受保護的 PEAP** (PEAP)

### <a name="more-options-when-you-choose-the-eap-type"></a>選擇 EAP 類型時的其他選項

> [!NOTE]
> 目前，使用 EAP 類型時只支援 SCEP 憑證設定檔。 不支援 PKCS 憑證設定檔。 每當要求使用者輸入憑證時，請務必選擇 SCEP 憑證。

#### <a name="server-trust"></a>伺服器信任

|設定名稱|詳細資訊|使用時機|
|--------------|-------------|----------|
|**憑證伺服器名稱**|輸入您信任之憑證授權單位 (CA) 核發的憑證中所使用的一或多個通用名稱。 如有輸入此資訊，可以略過連線到此 Wi-Fi 網路時，使用者裝置上顯示的動態信任對話方塊。|EAP 類型是 **EAP-TLS**、**EAP-TTLS** 或 **PEAP**|
|**伺服器驗證時使用的根憑證**|選擇信任的根憑證設定檔來驗證連線。 |EAP 類型是 **EAP-TLS**、**EAP-TTLS** 或 **PEAP**|
|**識別隱私權 (外部識別)**|輸入在回應 EAP 識別要求時傳送的文字。 此文字可以是任何值。 在驗證期間，一開始會先傳送此匿名識別，隨後以安全通道傳送真正的識別。|EAP 類型是 **PEAP**|

#### <a name="client-authentication"></a>用戶端驗證

| 設定名稱 | 詳細資訊 | 使用時機 |
|---|---|---|
| **用戶端驗證時使用的用戶端憑證 (識別憑證)** |  選擇用來驗證連線的 SCEP 憑證設定檔。 | EAP 類型是 **EAP-TLS** |
| **驗證方法** | 選取連線的驗證方法：<br><br>- **憑證**：選取 SCEP 用戶端憑證作為提供給伺服器的識別憑證。<br><br>- **使用者名稱和密碼**：輸入**非 EAP 方法 (內部識別)** 方法進行驗證。 選項包括：<br><br>- **未加密的密碼 (PAP)**<br>- **Challenge Handshake (CHAP)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP 第 2 版 (MS-CHAP v2)**<br><br>- **識別隱私權 (外部識別)**：指定回應 EAP 識別要求時所要傳送的文字。 此文字可以是任何值。 在驗證期間，一開始會先傳送此匿名識別，隨後以安全通道傳送真正的識別。 | EAP 類型是 **EAP-TTLS** |

## <a name="use-an-imported-settings-file"></a>使用匯入的設定檔

針對 Intune 中無法使用的任何設定，您可以從另一部 Windows 裝置匯出 Wi-Fi 設定。 這項匯出會建立具有所有設定的 XML 檔案。 然後，將此檔案匯入至 Intune，並使用它作為 Wi-Fi 設定檔。 請參閱[匯出和匯入 Windows 裝置的 Wi-Fi 設定](wi-fi-settings-import-windows-8-1.md)。

## <a name="next-steps"></a>接下來的步驟
[在 Intune 中設定 Wi-Fi 設定](wi-fi-settings-configure.md)
