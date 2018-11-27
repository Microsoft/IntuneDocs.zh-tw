---
title: 在 Microsoft Intune 中設定 Identity Protection 設定 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中新增裝置設定檔，設定 Windows 10 裝置上的 Windows Hello 企業版設定
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: f9d0db8e15e6de1241984f98bf651fcff1578033
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188621"
---
# <a name="configure-identity-protection-settings-in-microsoft-intune"></a>在 Microsoft Intune 中設定 Identity Protection 設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Identity Protection 設定檔控制如何在 Windows 10 受控裝置上佈建及設定 Windows Hello 企業版。 建立此設定檔可設定：  
* 裝置和使用者的 Windows Hello 企業版可用性。
* 裝置 PIN 需求。
* 使用者可以與無法登入裝置的筆勢。  

 您可以將此設定檔指派給選取的使用者和裝置群組，或所有使用者和所有裝置。 當群組簽入 Intune 時，他們會收到 Identity Protection 設定檔。    

請使用本文中的資訊，建立 Identity Protection 設定檔。 然後[指派您的設定檔](device-profile-assign.md)給使用者和裝置群組。

此功能適用於執行下列版本的裝置：  
- Windows 10 及更新版本
- Windows Holographic for Business  

## <a name="create-a-device-profile-with-identity-protection-settings"></a>建立包含 Identity Protection 設定的裝置設定檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
4. 輸入 Identity Protection 設定檔的 [名稱] 和 [描述]。
5. 從 [平台] 下拉式清單中，選取 [Windows 10 及更新版本]。 只有執行 Windows 10 和更新版本的裝置支援 Windows Hello 企業版。
6. 從 [設定檔類型] 下拉式清單中，選擇 [Identity Protection]。
7. 在 [Windows Hello 企業版] 窗格上，從 [設定 Windows Hello 企業版] 的下列選項中選擇：
    * 停用。 如果您不想要使用 Windows Hello 企業版，請選取此設定。 螢幕上的所有其他設定也都無法停用。
    * 已啟用。 如果您想要設定 Windows Hello 企業版設定，請選取此設定。  

8. 如果在前一步驟選取了 [啟用]，請設定將套用到已註冊之 Windows 10 與 Windows 10 行動裝置版目標裝置和使用者所需的設定。

> [!NOTE]
> 只將 Identity Protection 設定檔指派給使用者時，裝置內容預設為 [未設定]。  

   - **最小 PIN 長度**/**最大 PIN 長度**。 設定裝置以使用您指定的最小和最大 PIN 長度，協助確保安全的登入。 預設的 PIN 長度為 6 個字元，但您可以強制執行最小長度 (4 個字元)。 PIN 長度上限為 127 個字元。  

   - **PIN 的小寫字母**/**PIN 的大寫字母**/**PIN 的特殊字元**。 您可以要求在 PIN 中使用大寫字母、小寫字母及特殊字元，以強制使用強度更高的 PIN。 從下列選項進行選擇：

     - **允許**。 使用者可在其 PIN 中使用字元類型，但不是強制性。

     - **必要**。 使用者必須在其 PIN 中包含至少一個字元類型。 比方說，是常見的作法是需要至少一個大寫字母和一個特殊字元。

     - **不允許** (預設)。 使用者不得在其 PIN 中使用這些字元  (即使未進行設定，也會發生此行為)。<br>特殊字元包含：**! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

   - **PIN 到期 (天數)**。 建議為 PIN 指定到期時間，使用者必須在該時間後變更 PIN。 預設為 41 天。

   - **記住 PIN 記錄**。 限制重複使用先前用過的 PIN。 預設為不能重複使用最後 5 個 PIN。  
   - **啟用 PIN 復原**：允許使用者使用 Windows Hello 企業版 PIN 復原服務來變更其 PIN。 
       - **啟用**。 雲端服務會加密 PIN 復原祕密以儲存在裝置上。 如有需要，使用者可以變更 PIN。  
       - **未設定** (預設)。 不會建立或儲存 PIN 復原祕密。 如果忘記使用者的 PIN，取得新 PIN 的唯一方法為刪除現有的 PIN，然後建立新的 PIN。 使用者必須向提供舊 PIN 存取權的任何服務重新註冊。  
   
   - **使用信賴平台模組 (TPM)**。 TPM 晶片提供額外一層資料安全性。 選擇下列其中一個值：  
     - **啟用**。 只有能存取 TPM 的裝置可以佈建 Windows Hello 企業版。
     - **未設定**。 所有裝置都可以佈建 Windows Hello 企業版，即使沒有可使用的 TPM。 裝置會先嘗試使用 TPM，但如果沒有 TPM，則裝置可以使用軟體加密。  

   - **允許生物識別驗證**。 啟用生物識別驗證 (例如臉部辨識或指紋) 以替代 Windows Hello 企業版的 PIN。 使用者仍然必須設定公司 PIN 以免生物識別驗證失敗。 從下列選項進行選擇：

     - **啟用**。 Windows Hello 企業版允許生物識別驗證。
     - **未設定** (預設)。 Windows Hello 企業版防止生物識別驗證 (針對所有帳戶類型)。

   - **使用增強的防詐騙功能 (如其可用)**。 設定是否在支援 Windows Hello 反詐騙功能的裝置上使用該功能 (例如，偵測臉正面相片而非真正的臉孔)。
       - **啟用**。 Windows 要求所有使用者在功能支援的情況下，使用臉部特徵防詐騙。  
       - **未設定** (預設)。 Windows 會接受裝置上的防詐騙設定。

   - **內部部署資源的憑證**。 
       - **啟用**。 允許 Windows Hello 企業版使用憑證來驗證內部部署資源。
       - **未設定** (預設)。 防止 Windows Hello 企業版使用憑證來驗證內部部署資源。  
9. 按一下 [確定]，儲存您的設定檔。  

設定檔隨即建立，並出現在 [裝置設定 - 設定檔] 清單中。 若想繼續將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。  

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
