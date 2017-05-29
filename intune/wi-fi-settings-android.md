---
title: "Android 裝置的 Intune Wi-Fi 設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解您可用於設定 Android 裝置之 Wi-Fi 連線的 Intune 設定。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 103e17a4-2993-4359-b340-73e2acf4cf7d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 0dd0b8c4e4cf6733c20282817cba99d8379ef24e
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="wi-fi-settings-for-android-devices-in-microsoft-intune"></a>Microsoft Intune 中 Android 裝置的 Wi-Fi 設定

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>適用於基本設定檔與企業設定檔的 Wi-Fi 設定

- **網路名稱** - 輸入此 Wi-Fi 連線的名稱。 這是使用者瀏覽裝置上的可用連線清單時所見到的名稱。
- **SSID** - 簡短的服務組識別元。 這是裝置要連線之無線網路的實際名稱。 但當使用者選擇此連線時，只會看到您所建立的上列網路名稱。
- **自動連線** - 當裝置進入此網路的範圍內時自動連線。
- **隱藏的網路** - 禁止此網路顯示在裝置的可用網路清單中。


## <a name="wi-fi-settings-for-enterprise-profiles-only"></a>僅適用於企業設定檔的 Wi-Fi 設定

- **EAP 類型** - 選擇可延伸驗證通訊協定 (EAP) 類型，以驗證下列類型的安全無線連線：
    - **EAP-TLS**
    - **EAP-TTLS**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>當您選擇 EAP 類型的其他選項

#### <a name="server-trust"></a>伺服器信任



|設定名稱|詳細資訊|使用時機|
|-------------|---------------|-----------|
|**憑證伺服器名稱**|指定您信任之憑證授權單位 (CA) 核發行的憑證中所用的一或多個通用名稱。 如有提供此資訊，可以略過連線到此 Wi-fi 網路時，使用者裝置上顯示的動態信任對話方塊。|EAP 類型是 **EAP-TLS** 或 **EAP-TTLS**|
|**伺服器驗證時使用的根憑證**|選擇信任的根憑證設定檔來驗證連線。 |EAP 類型是 **EAP-TLS**、**EAP-TTLS** 或 **PEAP**|
|**識別隱私權 (外部識別)**|指定在回應 EAP 識別要求時傳送的文字。 此文字可以是任何值。 在驗證期間，一開始會先傳送此匿名識別，隨後以安全通道傳送真正的識別。|EAP 類型是 **PEAP**|


#### <a name="client-authentication"></a>用戶端驗證


|設定名稱|詳細資訊|使用時機|
|----------|--------------|----------|
|**用戶端驗證時使用的用戶端憑證 (識別憑證)**|選擇 SCEP 或 PKCS 憑證設定檔，以驗證連線。|EAP 類型是 **EAP-TLS**|
|**驗證方法**|選取連線的驗證方法：<br>- **憑證** - 選取 SCEP 或 PKCS 用戶端憑證作為提供給伺服器的身分識別憑證。<br><br>- **使用者名稱及密碼** - 指定不同的驗證方式。 <br><br>若選取 [使用者名稱及密碼]，請設定︰<br><br>-  **非 EAP 方法 (內部識別)**，然後再選取驗證連線的方式︰<br>- **無**<br>- **未加密的密碼 (PAP)**<br>- **Challenge Handshake 驗證通訊協定 (CHAP)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP 第 2 版 (MS-CHAP v2)**<br>可用的選項取決於您所選取的 EAP 類型。<br><br>**及**<br><br>- **識別隱私權 (外部識別)** - 指定回應 EAP 識別要求時所要傳送的文字。 此文字可以是任何值。 在驗證期間，一開始會先傳送此匿名識別，隨後以安全通道傳送真正的識別。|EAP 類型是 **EAP-TTLS** 或 **PEAP**|

