---
title: "如何使用 Intune 設定憑證"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何使用 Intune 來建立及指派憑證，協助您保護 Wi-Fi、VPN 與其他連線的安全。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 364534ad788466f8b268b4091decee5326b94163
ms.lasthandoff: 02/16/2017


---

# <a name="how-to-configure-certificates-in-microsoft-intune"></a>如何在 Microsoft Intune 中設定憑證

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

當您授與使用者透過 VPN、Wi-Fi 或電子郵件設定檔來存取公司資源的權限時，可以使用安裝在每部使用者裝置上的憑證，保護存取的安全。 大略的工作流程如下：

1. 確定您已備妥正確的憑證基礎結構。 您可使用 [SCEP 憑證](configure-certificate-infrastructure-for-scep.md) 與 [PKCS 憑證](configure-certificate-infrastructure-for-pfx.md)。
2. 在每部裝置上安裝根憑證或中繼憑證授權單位 (CA) 憑證，讓裝置可以辨識 CA 的合法性。 若要執行此作業，請建立並指派**信任的憑證設定檔**。 當您指派此設定檔時，您以 Intune 管理的裝置就會要求並收到根憑證。 每個平台必須分別建立各自的設定檔。 提供以下這些平台的受信任憑證設定檔︰
    - iOS 8.0 和更新版本
    - macOS 10.9 及更新版本
    - Android 4.0 及更新版本 <!--Android for Work --->
    - Windows 8.1 及更新版本
    - Windows Phone 8.1 和更新版本
    - Windows 10 及更新版本
3. 建立憑證設定檔，讓每個裝置要求一個用於驗證 VPN、Wi-Fi 和電子郵件存取的憑證。 您可為執行這些平台的裝置，建立並部署 **PKCS** 或 **SCEP** 憑證設定檔︰
    - iOS 8.0 和更新版本
    - Android 4.0 及更新版本
    - Android for Work
    - Windows 10 (桌面版和行動裝置版) 和更新版本

    只有這些平台才可使用 SCEP 憑證設定檔：

-     macOS 10.9 及更新版本
-     Windows Phone 8.1 和更新版本

您必須為每個裝置平台建立自己的設定檔。 當您建立設定檔時，請將該設定檔與您已建立之受信任的根憑證設定檔相關聯。

### <a name="further-considerations"></a>進一步考量

- 如果沒有企業憑證授權單位，您必須建立一個。
- 如果您決定 (根據裝置平台) 使用簡單憑證註冊通訊協定 (SCEP) 設定檔，您也需要設定網路裝置註冊服務 (NDES) 伺服器。
- 無論是否預計會使用 SCEP 或 PKCS 設定檔，您都必須下載及設定 Microsoft Intune 憑證連接器。

## <a name="before-you-start"></a>開始之前


### <a name="if-you-want-to-use-scep-certificates"></a>若要使用 SCEP 憑證

請完成 [Certificate infrastructure for SCEP](/intune-azure/configure-devices/configure-certificate-infrastructure-for-scep) (SCEP 的憑證基礎結構) 中必要的先決條件。

### <a name="if-you-want-to-use-pkcs-certificates"></a>若要使用 PKCS 憑證

請完成[Certificate infrastructure for PKCS](/intune-azure/configure-devices/configure-certificate-infrastructure-for-pfx) (PKCS 的憑證基礎結構) 中必要的先決條件。

## <a name="task-1-export-the-trusted-root-ca-certificate"></a>工作 1：匯出受可信任的根 CA 憑證
從發行 CA 或信任發行 CA 的任何裝置，將可信任的根憑證授權單位匯出為 **.cer** 檔案。 不要匯出私密金鑰。

當您設定受信任的憑證設定檔時，會匯入此憑證。

## <a name="task-2-create-trusted-certificate-profiles"></a>工作 2：建立受信任的憑證設定檔
您必須先建立受信任的憑證設定檔，然後才可建立 SCEP 或 PKCS 憑證設定檔。 每個裝置平台都需要一個受信任的憑證設定檔以及 SCEP 或 PKCS 設定檔。

### <a name="to-create-a-trusted-certificate-profile"></a>建立信任的憑證設定檔

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中選擇 [設定裝置]。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
3. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗中，為受信任的憑證設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取此受信任憑證的裝置平台。 您目前可選擇下列平台之一，進行裝置限制設定︰
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更新版本**
    - **Windows 10 及更新版本**
6. 從 [設定檔類型] 下拉式清單中，選擇 [受信任的憑證]。
7. 瀏覽至您於工作 1 中所儲存的憑證，然後按一下 [確定]。
8. 僅適用於 Windows 8.1 與 Windows 10 裝置，請為來自以下位置的受信任憑證，選取 [目的地存放區]︰
    - **電腦憑證存放區 - 根**
    - **電腦憑證存放區 - 中繼**
    - **使用者憑證存放區 - 中繼**
8. 完成後，請選擇 [確定]返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。
若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](how-to-assign-device-profiles.md)。


> [!Note]
> Android 裝置會顯示協力廠商已安裝受信任憑證的通知。

## <a name="task-3-create-scep-or-pkcs-certificate-profiles"></a>工作 3：建立 SCEP 或 PKCS 憑證設定檔
建立受信任的憑證設定檔之後，請為您要使用的每個平台，建立 SCEP 或 PKCS 憑證設定檔。 建立 SCEP 憑證設定檔時，必須為該相同的平台指定受信任的憑證設定檔。 如此即會連結兩個憑證設定檔，但您仍然必須分別指派每個設定檔。

### <a name="to-create-an-scep-certificate-profile"></a>建立 SCEP 憑證設定檔

1. 在 Azure 入口網站中，選取 [設定裝置] 工作負載。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
3. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗中，為 SCEP 憑證設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取此 SCEP 憑證的裝置平台。 您目前可選擇下列平台之一，進行裝置限制設定︰
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更新版本**
    - **Windows 10 及更新版本**
6. 從 [設定檔類型] 下拉式清單中，選擇 [SCEP 憑證]。
7. 在 [SCEP 憑證] 刀鋒視窗上，進行以下設定：
    - **憑證有效期間** - 如果您已在發行 CA 上執行 **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** 命令，允許自訂有效期間，則可以指定憑證到期之前的剩餘時間長度。<br>您可以指定一個比憑證範本中指定之有效期間更低，而不是更高的值。 舉例來說，如果憑證範本中的憑證有效期間為兩年，您可以指定一年而不是五年的值。 該值也必須低於發行 CA 憑證的剩餘有效期。 
    - **金鑰儲存提供者 (KSP)** (Windows Phone 8.1、Windows 8.1、Windows 10) - 指定儲存金鑰的憑證位置。 選擇下列其中一個值：
        - **註冊至受信任平台模組 (TPM) KSP (如果存在)，否則註冊至軟體 KSP**
        - **註冊至信賴平台模組 (TPM) KSP，否則失敗**
        - **註冊至 Passport，否則失敗 (Windows 10 及更新版本)**
        - **註冊至軟體 KSP**
    - **主體名稱格式**從清單中選取 Intune 如何自動在憑證要求中建立主體名稱。 如果憑證是針對使用者，您也可以在主體名稱中包含使用者的電子郵件地址。 從下列選項進行選擇：
        - **未設定**
        - **一般名稱**
        - **包括電子郵件的一般名稱**
        - **一般名稱及電子郵件地址**
    - **主體別名**指定 Intune 如何在憑證要求中，自動建立主體別名 (SAN) 的值。 舉例來說，如果您選擇使用者憑證類型，您可以在主體別名中包含使用者主體名稱 (UPN)。 如果用戶端憑證將用來驗證網路原則伺服器，您必須將主體別名設定成 UPN。 
    - **金鑰使用方式** - 指定憑證的金鑰使用方式選項。 您可以選擇下列選項： 
        - **金鑰編密：**只允許在金鑰加密後交換金鑰。 
        - **數位簽章：**只允許在以數位簽章協助保護金鑰後交換金鑰。 
    - **金鑰大小 (位元)** - 金鑰中要包含的位元數。 
    - **雜湊演算法：** (Android、Windows Phone 8.1、Windows 8.1、Windows 10) - 選取其中一種可用的雜湊演算法類型，搭配此憑證使用。 選取連線中裝置所支援的最強安全性層級。 
    - **根憑證** - 選擇先前所設定並指派到使用者或裝置的根 CA 憑證設定檔。 此 CA 憑證必須是將發行憑證 (您在此憑證設定檔中設定) 之 CA 的根憑證。 
    - **擴充金鑰使用方法** - 選擇 [新增] 以新增憑證使用目的值。 在大部分情況下，憑證需要 [用戶端驗證]  ，使用者或裝置才能向伺服器進行驗證。 不過，您可以視需要新增任何其他金鑰使用方式。 
    - **註冊設定**
        - **更新閾值 (%)** - 指定裝置要求憑證更新之前，剩餘的憑證存留時間百分比。
        - **SCEP 伺服器 URL** - 指定一或多個將透過 SCEP 發行憑證的 NDES 伺服器 URL。 
8. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。

遵循設定檔設定頁面的指示來設定 SCEP 憑證設定檔設定。
>[!Note]
> 僅限 iOS 裝置：在 [主體名稱格式] 下，選取 [自訂]，以輸入自訂主體名稱格式。
> 自訂格式目前支援的兩個變數為「一般名稱 (CN)」和「電子郵件 (E)」。 您可使用這些變數與靜態字串的組合，建立自訂主體名稱格式，例如此︰**CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**在此範例中，您建立了主體名稱格式，除了 CN 與 E 變數之外，為組織單位、組織、位置、狀態與國家/地區值使用字串。 [本主題](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx)會顯示 **CertStrToName** 函式與其支援的字串。


### <a name="to-create-a-pkcs-certificate-profile"></a>建立 PKCS 憑證設定檔

在 Azure 入口網站中，選取 [設定裝置] 工作負載。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
3. 在 [設定檔] 刀鋒視窗中，按一下 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗中，為 PKCS 憑證設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取此 PKCS 憑證的來源裝置平台：
    - **Android**
    - **iOS**
    - **Windows 10 及更新版本**
6. 從 [設定檔類型] 下拉式清單中，選擇 [PKCS 憑證]。
7. 在 [PKCS 憑證] 刀鋒視窗上，進行以下設定：
    - **更新閾值 (%)** - 指定裝置要求憑證更新之前，剩餘的憑證存留時間百分比。
    - **憑證有效期間** - 如果您已在發行 CA 上執行 **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** 命令，允許自訂有效期間，則可以指定憑證到期之前的剩餘時間長度。<br>您可以指定一個比憑證範本中指定之有效期間更低，而不是更高的值。 舉例來說，如果憑證範本中的憑證有效期間為兩年，您可以指定一年而不是五年的值。 該值也必須低於發行 CA 憑證的剩餘有效期。
    - **金鑰儲存提供者 (KSP)** (Windows 10) -
    - **憑證授權單位** -
    - **憑證授權單位名稱** -
    - **憑證範本名稱** - 輸入網路裝置註冊服務設定要使用且已新增至發行 CA 的憑證範本名稱。
    請確定該名稱完全符合執行網路裝置註冊服務的伺服器，於登錄中列出的其中一個憑證範本。 請確定您指定的是憑證範本的名稱，而非憑證範本的顯示名稱。 
    若要尋找憑證範本的名稱，請瀏覽至下列機碼：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP。 您將會看見憑證範本已列為 [EncryptionTemplate] 、[GeneralPurposeTemplate] 和 [SignatureTemplate] 的值。 根據預示，這三個憑證範本的值是 [IPSECIntermediateOffline]，對應至 [IPSec (離線要求)] 的範本顯示名稱。 
    - **主體名稱格式**從清單中選取 Intune 如何自動在憑證要求中建立主體名稱。 如果憑證是針對使用者，您也可以在主體名稱中包含使用者的電子郵件地址。 從下列選項進行選擇：
        - **未設定**
        - **一般名稱**
        - **包括電子郵件的一般名稱**
        - **一般名稱及電子郵件地址**
    - **主體別名**指定 Intune 如何在憑證要求中，自動建立主體別名 (SAN) 的值。 舉例來說，如果您選擇使用者憑證類型，您可以在主體別名中包含使用者主體名稱 (UPN)。 如果用戶端憑證將用來驗證網路原則伺服器，您必須將主體別名設定成 UPN。
    - **擴充金鑰使用方法** (Android) - 選擇 [新增] 以新增憑證使用目的值。 在大部分情況下，憑證需要 [用戶端驗證]  ，使用者或裝置才能向伺服器進行驗證。 不過，您可以視需要新增任何其他金鑰使用方式。 
    - **根憑證**- 選擇先前所設定並指派到使用者或裝置的根 CA 憑證設定檔。 此 CA 憑證必須是將發行憑證 (您在此憑證設定檔中設定) 之 CA 的根憑證。
8. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。

## <a name="task-4-assign-certificate-profiles"></a>工作 4：指派憑證設定檔

將憑證設定檔指派給群組之前，請考慮下列事宜︰

- 當您指派憑證設定檔給群組時，來自受信任 CA 憑證設定檔的憑證檔案，即會安裝在裝置上。 裝置使用 SCEP 或 PKCS 憑證設定檔，建立裝置所要求的憑證。
- 憑證設定檔只會安裝在執行於您建立設定檔時所用的平台裝置上。
- 您可以將憑證設定檔部署到使用者集合或裝置集合。
- 若要在裝置註冊之後快速將憑證發行至裝置，請將憑證設定檔部署到使用者群組，而不是裝置群組。 如果您部署至裝置群組，必須先執行完整的裝置註冊，裝置才會接收原則。
- 雖然您會分別部署每個設定檔，但仍需部署可受信任的根 CA 與 SCEP 或 PKCS 設定檔。 否則，SCEP 或 PKCS 憑證原則會失敗。

## <a name="next-steps"></a>後續步驟
請參閱[如何指派裝置設定檔](how-to-assign-device-profiles.md)，以取得如何指派裝置設定檔的一般資訊。

