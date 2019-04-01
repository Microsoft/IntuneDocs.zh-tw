---
title: Microsoft Intune 中的 Windows Hello 企業版設定 - Azure | Microsoft Docs
description: 查看身分識別保護設定檔中的所有 PIN、生物特徵辨識和防詐騙設定清單，以便在 Microsoft Intune 中的 Windows 10 裝置上使用和設定 Windows Hello 企業版。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: 308a730737612f39863160952409ab92670f9153
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "58068906"
---
# <a name="windows-10-device-settings-to-enable-windows-hello-for-business-in-intune"></a>用以啟用 Intune 中 Windows Hello 企業版的 Windows 10 裝置設定

本文列出並描述您可以在 Intune 中的 Windows 10 裝置上控制的 Windows Hello 企業版設定。 身為 Intune 管理員，則可以設定，並將這些設定指派給 Windows 10 裝置中，為您的行動裝置管理 (MDM) 解決方案的一部分。 

您可以找到這些設定的其他資訊[設定 Windows Hello for Business 原則設定](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings)，WIndows Hello 文件中。


若要深入了解 Intune 中的 Windows Hello 企業版設定檔，請參閱[設定身分識別保護](identity-protection-configure.md)。

## <a name="before-you-begin"></a>開始之前

[建立組態設定檔](identity-protection-configure.md#create-the-device-profile)。

## <a name="windows-hello-for-business"></a>Windows Hello 企業版

- **設定 Windows hello 企業版**： 若要使用這項功能，並設定其設定，選擇**啟用**。
- **PIN 長度下限**：輸入您想要在裝置上允許的 PIN 長度下限。 預設的 PIN 長度為六個字元。 PIN 長度下限為四 (4) 個字元。
- **PIN 長度上限**：輸入您想要在裝置上允許的 PIN 長度上限。 預設的 PIN 長度為六 (6) 個字元。 PIN 長度上限為 127 個字元。  
- **PIN 中需要小寫字母**：您可藉由要求終端使用者包含小寫字母，強制執行更強的 PIN。 選項包括：

  - **不允許**（預設值）： 禁止使用者在 PIN 中使用小寫字母。 如果未設定此設定，也會發生此行為。
  - **允許**：允許使用者在 PIN 中使用小寫字母，但並非必要。
  - **必要**：使用者必須在 PIN 中至少包含一個小寫字元。 比方說，是常見的作法是需要至少一個大寫字母和一個特殊字元。

- **PIN 中需要大寫字母**：您可藉由要求終端使用者包含大寫字母，強制執行更強的 PIN。 選項包括：

  - **不允許**（預設值）： 禁止使用者在 PIN 中使用大寫字母。 如果未設定此設定，也會發生此行為。
  - **允許**：允許使用者在 PIN 中使用大寫字母，但並非必要。
  - **必要**：使用者必須在 PIN 中至少包含一個大寫字元。 比方說，是常見的作法是需要至少一個大寫字母和一個特殊字元。

- **PIN 中需要特殊字元**：您可藉由要求終端使用者包含特殊字元，強制執行更強的 PIN。 選項包括：

  - **不允許**（預設值）： 禁止使用者在 PIN 中使用特殊字元。 如果未設定此設定，也會發生此行為。
    特殊字元包含：`! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`
  - **允許**：允許使用者在 PIN 中使用大寫字母，但並非必要。
  - **必要**：使用者必須在 PIN 中至少包含一個大寫字元。 比方說，是常見的作法是需要至少一個大寫字母和一個特殊字元。

- **PIN 到期 (天數)**：建議為 PIN 指定到期時間，使用者必須在該時間後變更 PIN。 預設為 41 天。

- **記住 PIN 歷程記錄**： 限制重複使用先前用過的 pin。 預設不能重複使用最後 5 個 PIN。  
- **啟用 PIN 復原**：允許使用者使用 Windows Hello 企業版 PIN 復原服務來變更其 PIN。

       - **Enable**: The cloud service encrypts a PIN recovery secret to store on the device. The user can change their PIN if needed.  
       - **Not configured** (default): A PIN recovery secret is not created or stored. If the user's PIN is forgotten, the only way to get a new PIN is by deleting the existing PIN and creating a new one. The user will need to re-register with any services the old PIN provided access to.  

- **使用信賴平台模組 (TPM)**：TPM 晶片提供額外一層資料安全性。 選擇下列其中一個值：  
  - **啟用**：只有能存取 TPM 的裝置可以佈建 Windows Hello 企業版。
  - **未設定**：所有裝置都可以佈建 Windows Hello 企業版，即使沒有可使用的 TPM。 裝置會先嘗試使用 TPM，但如果沒有 TPM，則裝置可以使用軟體加密。  

- **允許生物識別驗證**：啟用生物識別驗證 (例如臉部辨識或指紋) 以替代 Windows Hello 企業版的 PIN。 使用者仍然必須設定公司 PIN 以免生物識別驗證失敗。 從下列選項進行選擇：

  - **啟用**：Windows Hello 企業版允許生物識別驗證。
  - **未設定** (預設)：Windows Hello 企業版會防止生物識別驗證 (針對所有帳戶類型)。

- **使用增強型防詐騙功能，可以使用**： 如果選擇的防詐騙功能支援的裝置上使用 Windows hello 的功能。 例如，偵測臉部的相片而非實際的臉部。

  - **啟用**：Windows 要求所有使用者在功能支援的情況下，使用臉部特徵防詐騙。  
  - **未設定**（預設值）： Windows 會接受在裝置上的防詐騙功能的組態。

- **內部部署資源的憑證**： 

  - **啟用**：允許 Windows Hello 企業版使用憑證來驗證內部部署資源。
  - **未設定** (預設)：防止 Windows Hello 企業版使用憑證來驗證內部部署資源。 相反地，裝置會使用的預設行為*金鑰信任內部部署驗證*。 如需詳細資訊，請參閱 <<c0> [ 內部部署驗證的使用者憑證](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication)Windows Hello 文件中。  
## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
