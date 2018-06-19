---
title: 為執行 Android 的裝置設定 Microsoft Intune Wi-Fi 設定
titleSuffix: ''
description: 了解執行 Android 和 Android for Work 之裝置上的 Intune Wi-Fi 組態設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ee82da997a794bb2f65929a6fd9e0de0cc776a6e
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31831056"
---
# <a name="configure-wi-fi-settings-in-microsoft-intune-for-devices-running-android-and-android-for-work"></a>在 Microsoft Intune 中設定執行 Android 和 Android for Work 之裝置的 Wi-Fi 設定  

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文將說明可在 Microsoft Intune 中，為執行 Android 和 Android for Work 的裝置設定的 Wi-Fi 設定。

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>適用於基本設定檔與企業設定檔的 Wi-Fi 設定

下列 Wi-Fi 設定適用於 Android 和 Android for Work 裝置：

- **網路名稱** - 輸入此 Wi-Fi 連線的名稱。 這是使用者瀏覽裝置上的可用連線清單時所見到的名稱。
- **SSID** - 簡短的服務組識別元。 這是裝置要連線之無線網路的實際名稱。 但當使用者選擇此連線時，只會看到您設定的網路名稱。
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
|**憑證伺服器名稱**|指定您信任之憑證授權單位 (CA) 核發行的憑證中所用的一或多個通用名稱。 如有提供此資訊，可以略過連線到此 Wi-Fi 網路時，使用者裝置上顯示的動態信任對話方塊。|EAP 類型是 **EAP-TLS** 或 **EAP-TTLS**|
|**伺服器驗證時使用的根憑證**|選擇信任的根憑證設定檔來驗證連線。 |EAP 類型是 **EAP-TLS**、**EAP-TTLS** 或 **PEAP**|
|**識別隱私權 (外部識別)**|指定在回應 EAP 識別要求時傳送的文字。 此文字可以是任何值。 在驗證期間，一開始會先傳送此匿名識別，隨後以安全通道傳送真正的識別。|EAP 類型是 **PEAP**|


#### <a name="client-authentication"></a>用戶端驗證


|                                     設定名稱                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       詳細資訊                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                            使用時機                            |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| <strong>用戶端驗證時使用的用戶端憑證 (識別憑證)</strong> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       選擇 SCEP 或 PKCS 憑證設定檔，以驗證連線。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |              EAP 類型是 <strong>EAP-TLS</strong>              |
|                        <strong>驗證方法</strong>                        | 選取連線的驗證方法：<br>- <strong>憑證</strong> - 選取 SCEP 或 PKCS 用戶端憑證作為提供給伺服器的身分識別憑證。<br><br>- <strong>使用者名稱及密碼</strong> - 指定不同的驗證方式。 <br><br>若選取 [使用者名稱及密碼]，請設定︰<br><br>-  <strong>非 EAP 方法 (內部識別)</strong>，然後選取驗證連線的方式︰<br>- <strong>無</strong><br>- <strong>未加密的密碼 (PAP)</strong><br>- <strong>Challenge Handshake 驗證通訊協定 (CHAP)</strong><br>- <strong>Microsoft CHAP (MS-CHAP)</strong><br>- <strong>Microsoft CHAP 第 2 版 (MS-CHAP v2)</strong><br>可用的選項取決於您所選取的 EAP 類型。<br><br><strong>及</strong><br><br>- <strong>識別隱私權 (外部識別)</strong> - 指定回應 EAP 識別要求時所要傳送的文字。 此文字可以是任何值。 在驗證期間，一開始會先傳送此匿名識別，隨後以安全通道傳送真正的識別。 | EAP 類型是 <strong>EAP-TTLS</strong> 或 <strong>PEAP</strong> |

