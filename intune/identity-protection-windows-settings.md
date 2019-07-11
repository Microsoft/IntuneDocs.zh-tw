---
title: Microsoft Intune 中的 Windows Hello 企業版設定 - Azure | Microsoft Docs
description: 查看身分識別保護設定檔中的所有 PIN、生物特徵辨識和防詐騙設定清單，以便在 Microsoft Intune 中的 Windows 10 裝置上使用和設定 Windows Hello 企業版。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: 5a8111d2542269441c7305aad0aad0b7c2162037
ms.sourcegitcommit: 1dc9d4e1d906fab3fc46b291c67545cfa2231660
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735623"
---
# <a name="windows-10-device-settings-to-enable-windows-hello-for-business-in-intune"></a>用以啟用 Intune 中 Windows Hello 企業版的 Windows 10 裝置設定

本文列出並描述您可以在 Intune 中的 Windows 10 裝置上控制的 Windows Hello 企業版設定。 身為 Intune 管理員，您可以設定和將這些設定指派給 Windows 10 裝置，作為您行動裝置管理 (MDM) 解決方案的一部分。 

您可以在 Windows Hello 文件中[設定 Windows Hello 企業版原則設定](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings)內找到這些設定的其他相關資訊。


若要深入了解 Intune 中的 Windows Hello 企業版設定檔，請參閱[設定身分識別保護](identity-protection-configure.md)。

## <a name="before-you-begin"></a>開始之前

[建立組態設定檔](identity-protection-configure.md#create-the-device-profile)。

## <a name="windows-hello-for-business"></a>Windows Hello 企業版
- **設定 Windows Hello 企業版**：
  - **尚未設定** - 如果您不想要使用 Intune 來控制 Windows Hello 企業版設定，請選取此設定。 不會變更 Windows 10 裝置上任何現有的 Windows Hello 企業版設定。 窗格上的所有其他設定，都無法使用。

  - **已停用** - 如果您不想要使用 Windows Hello 企業版，請選取此設定。 螢幕上的所有其他設定也都無法停用。
  - **已啟用** - 如果您想要設定 Windows Hello 企業版設定，請選取此設定。  
  
  **預設**：未設定

  當設定為 *[* 已啟用] 時, 可以使用下列設定:

  - **PIN 長度下限**  
    指定裝置的 PIN 長度下限, 以協助保護登入的安全。 Windows 裝置預設值為6個字元, 但這項設定可強制執行最少四到127個字元。 

    **預設值**：*未設定*

  - **PIN 長度上限**  
  指定裝置的 PIN 長度上限, 以協助保護登入的安全。 Windows 裝置預設值為6個字元, 但這項設定可強制執行最少四到127個字元。  

    **預設值**：*未設定*  

  - **PIN 中的小寫字母**  
    您可藉由要求終端使用者包含小寫字母，強制執行更強的 PIN。 選項包括：

    - **不允許** - 禁止使用者在 PIN 中使用小寫字母。 如果未設定此設定，也會發生此行為。
    - **允許** - 允許使用者在 PIN 中使用小寫字母，但並非必要。
    - **必要** - 使用者必須在 PIN 中至少包含一個小寫字母。 比方說，是常見的作法是需要至少一個大寫字母和一個特殊字元。

  - **PIN 中的大寫字母**  
    您可藉由要求終端使用者包含大寫字母，強制執行更強的 PIN。 選項包括：

    - **不允許** - 禁止使用者在 PIN 中使用大寫字母。 如果未設定此設定，也會發生此行為。
    - **允許** - 允許使用者在 PIN 中使用大寫字母，但並非必要。
    - **必要** - 使用者必須在 PIN 中至少包含一個大寫字母。 比方說，是常見的作法是需要至少一個大寫字母和一個特殊字元。

  - **PIN 中的特殊字元**  
    您可藉由要求終端使用者包含特殊字元，強制執行更強的 PIN。 特殊字元包含：`! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`  

    選項包括：
    - **不允許** - 禁止使用者在 PIN 中使用特殊字元。 如果未設定此設定，也會發生此行為。
    - **允許** - 允許使用者在 PIN 中使用大寫字母，但並非必要。
    - **必要** - 使用者必須在 PIN 中至少包含一個大寫字母。 比方說，是常見的作法是需要至少一個大寫字母和一個特殊字元。

    **預設**值: 不允許

  - **PIN 到期 (天數)**  
    建議為 PIN 指定到期時間，使用者必須在該時間後變更 PIN。 Windows 裝置預設值為41天。

    **預設值**：尚未設定

  - **記住 PIN 碼歷程記錄**  
    限制重複使用先前用過的 PIN。 Windows 裝置預設為避免重複使用最後五個 Pin。  

    **預設值**：尚未設定  

  - **啟用 PIN 復原**   
    允許使用者使用 Windows Hello 企業版 PIN 復原服務。 
    
    - **已**啟用-PIN 復原密碼會儲存在裝置上, 而且使用者可以視需要變更其 PIN。  
    - **已**停用-不會建立或儲存修復密碼。

    **預設**：未設定

  - **使用信賴平台模組 (TPM)**    
    TPM 晶片提供額外一層資料安全性。  

    - **啟用** - 只有能存取 TPM 的裝置可以佈建 Windows Hello 企業版。
    - **尚未設定** - 第一次嘗試使用 TPM 的裝置。 如果無法使用此值，則可以使用軟體加密。
    
    **預設**：未設定

  - **允許生物識別驗證**  
     啟用生物識別驗證 (例如臉部辨識或指紋) 以替代 Windows Hello 企業版的 PIN。 使用者仍然必須設定公司 PIN 以免生物識別驗證失敗。 從下列選項進行選擇：

    - **啟用** - Windows Hello 企業版允許生物識別驗證。
    - **未設定** - Windows Hello 企業版會防止生物識別驗證 (針對所有帳戶類型)。

    **預設**：未設定

  - **使用進階防詐騙 (如可使用)**  
    設定是否在支援 Windows Hello 反詐騙功能的裝置上使用該功能 (例如，偵測臉正面相片而非真正的臉孔)。  
    - **啟用** - Windows 要求所有使用者在功能支援的情況下，使用臉部特徵防詐騙。
    - [未設定]  - Windows 會接受裝置上的反詐騙設定。

    **預設**：未設定

  - **內部部署資源的憑證**  

    - **啟用** - 允許 Windows Hello 企業版使用憑證來驗證內部部署資源。
    - **未設定** - 防止 Windows Hello 企業版使用憑證來驗證內部部署資源。 裝置會改為使用「金鑰信任內部部署驗證」  的預設行為。 如需詳細資訊，請參閱 Windows Hello 文件中的[內部部署驗證的使用者憑證](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication)。  

  **預設**：未設定

- **使用安全性金鑰進行登入**  
  此設定適用于執行 Windows 10 1903 版或更新版本的裝置。 使用它來管理使用 Windows Hello 安全性金鑰進行登入的支援。  

  - **已**啟用-使用者可以使用 Windows Hello 安全性金鑰做為以此原則為目標之電腦的登入認證。 
  - **已**停用-安全性金鑰已停用, 而且使用者無法使用它們來登入電腦。   

  **預設**：未設定

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
