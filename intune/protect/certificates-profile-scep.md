---
title: 搭配 Microsoft Intune 使用 SCEP 憑證設定檔 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 建立並指派簡單憑證註冊通訊協定 (SCEP) 憑證設定檔。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4e28db0d24101ae65ff8c5e49febd0ff5dddc6e2
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585425"
---
# <a name="create-and-assign-scep-certificate-profiles-in-intune"></a>在 Intune 中建立並指派 SCEP 憑證設定檔

在您[設定基礎結構](certificates-scep-configure.md)以支援簡單憑證註冊通訊協定 (SCEP) 憑證之後，您可以建立 SCEP 憑證設定檔，然後將其指派給 Intune 中的使用者和裝置。

> [!IMPORTANT]  
> 將使用 SCEP 憑證設定檔之裝置必須信任您的受信任根憑證授權 (CA)，您才能建立 SCEP 憑證設定檔。 使用 Intune 中的*受信任憑證設定檔*，將受信任的根 CA 憑證佈建給使用者與裝置。如需受信任憑證設定檔的資訊，請參閱＜在 Intune 中使用憑證以進行驗證＞  中的[＜匯出受信任的根 CA 憑證＞](certificates-configure.md#export-the-trusted-root-ca-certificate)和[＜建立受信任的憑證設定檔＞](certificates-configure.md#create-trusted-certificate-profiles)。


## <a name="create-a-scep-certificate-profile"></a>建立 SCEP 憑證設定檔

1. 登入 [Intune 入口網站](https://aka.ms/intuneportal)。
2. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
3. 輸入 SCEP 憑證設定檔的 [名稱]  與 [描述]  。
4. 從 [平台]  下拉式清單中，選取此 SCEP 憑證[受支援的裝置平台](certificates-configure.md#supported-platforms-and-certificate-profiles)。 
5. 從 [設定檔類型]  下拉式清單中，選取 [SCEP 憑證]  。  
   
   針對 **Android Enterprise** 平台，「設定檔類型」  會分為兩個類別：「僅限裝置擁有者」  和「僅限工作設定檔」  。 請務必為您管理的裝置選取正確的 SCEP 憑證設定檔。  

   適用於「僅限裝置擁有者」  設定檔的 SCEP 憑證設定檔具有下列限制：  

   1. 不支援下列變數：  

      - CN={{OnPrem_Distinguished_Name}}  
      - CN={{onPremisesSamAccountName}}  

   2. 在 [監視] 下方，憑證報告不適用於「裝置擁有者」SCEP 憑證設定檔。
   
   3. 您無法使用 Intune 撤銷由 SCEP 憑證設定檔為裝置擁有者所佈建的憑證。 您可以透過外部程序或直接使用憑證授權單位單位來管理撤銷。 

6. 選取 [設定]  ，然後完成下列設定：

   - **憑證類型**：   
     *(適用於：Android、Android Enterprise、iOS、macOS、Windows 8.1 和更新版本，以及 Windows 10 和更新版本。)*  

      根據您要使用憑證設定檔的方式來選取類型：
      - **使用者**：[使用者]  憑證可在憑證的主旨與 SAN 中包含使用者屬性和裝置屬性。  
      - **裝置**：[裝置]  憑證只能在憑證的主旨與 SAN 中包含裝置屬性。  
      
        針對無使用者裝置 (例如 kiosk 或 Windows 裝置) 等情況使用 [裝置]  。 在 Windows 裝置上，憑證會放在本機電腦憑證存放區中。  

   - **主體名稱格式**：  
     選取 Intune 在憑證要求中自動建立主體名稱的方式。 主體名稱格式的選項，取決於您選取的憑證類型 ([使用者]  或 [裝置]  )。  

     > [!NOTE]  
     > 當產生的憑證簽署要求 (CSR) 中的主體名稱包含下列其中一個字元作為逸出字元 (以反斜線 \\ 開頭) 時，使用 SCEP 取得憑證有一個[已知問題](#avoid-certificate-signing-requests-with-escaped-special-characters)：
     > - \+
     > - ;
     > - 、
     > - =

     - **使用者憑證類型**  
       「主體名稱格式」  的格式選項包括：  
       - **未設定**
       - **一般名稱**
       - **包括電子郵件的一般名稱**
       - **一般名稱及電子郵件地址**
       - **IMEI (國際行動設備識別)**
       - **序號**
       - **自訂**：選取此選項時，會一併顯示 [自訂]  文字方塊。 您可以使用此欄位來輸入自訂主體名稱格式，包括變數。 自訂格式支援兩個變數：**一般名稱 (CN)** 和**電子郵件 (E)** 。 **一般名稱 (CN)** 可以設定為下列任何變數：

         - **CN={{UserName}}** ：使用者的使用者主體名稱，例如 janedoe@contoso.com。
         - **CN={{AAD_Device_ID}}** ：您在 Azure Active Directory (AD) 中註冊裝置時所指派的識別碼。 此識別碼通常用於向 Azure AD 驗證。
         - **CN={{SERIALNUMBER}}** ：製造商通常用來識別裝置的唯一序號 (SN)。
         - **CN={{IMEINumber}}** ：用來識別行動電話的國際行動設備識別碼 (IMEI)。
         - **CN={{OnPrem_Distinguished_Name}}** ：以逗號分隔的相對辨別名稱序列，例如 *CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com*。

           若要使用 *{{OnPrem_Distinguished_Name}}* 變數，請務必使用 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 將 *onpremisesdistinguishedname* 使用者屬性同步至您的 Azure AD。

         - **CN={{onPremisesSamAccountName}}** ：系統管理員可使用 Azure AD 連線到稱為 *onPremisesSamAccountName* 的屬性，將 Active Directory 的 samAccountName 屬性與 Azure AD 同步。 Intune 可將該變數替換為憑證主體中憑證發行要求的一部分。 samAccountName 屬性是使用者登入名稱，用於支援舊版 Windows 客戶端和伺服器 (Windows 2000 以前的版本)。 使用者登入名稱格式為：*DomainName\testUser*，或僅 *testUser*。

            若要使用 *{{onPremisesSamAccountName}}* 變數，請務必使用 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 將 *onPremisesSamAccountName* 使用者屬性同步至您的 Azure AD。

         您可以結合使用一或多個這些變數和靜態字串，建立自訂的主體名稱格式，如下：  
         - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**
            
        該範例包含使用 CN 和 E 變數的主體名稱格式，以及組織單位、組織、位置、縣/市及國家/地區值的字串。 [CertStrToName 函式](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) 說明此函式和它支援的字串。

      - **裝置憑證類型**  
        主體名稱格式的格式選項包括下列變數： 
        - **{{AAD_Device_ID}}**
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{AzureADDeviceId}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}** *(僅適用於 Windows 和已加入網域的裝置)*
        - **{{MEID}}**

        您可以在文字方塊中指定這些變數，後接變數的文字。 例如，名為 *Device1* 的裝置一般名稱可以新增為 **CN={{DeviceName}}Device1**。

        > [!IMPORTANT]  
        > - 當您指定變數時，請將變數名稱括在大括弧 { } 中 (如範例所示)，以避免發生錯誤。  
        > - 裝置憑證的「主體」  或 *SAN* 中所使用裝置屬性 (例如 **IMEI**、**SerialNumber** 和 **FullyQualifiedDomainName**)，這些屬性可由具有裝置存取權的人員來偽造。
        > - 裝置必須支援憑證設定檔中指定的所有變數，才能在該裝置上安裝該設定檔。  例如，如果 SCEP 設定檔的主體名稱中使用 **{{IMEI}}** ，但該設定檔指派給沒有 IMEI 編號的裝置，則設定檔安裝將會失敗。  

   - **主體別名**：  
     選取 Intune 在憑證要求中自動建立主體別名 (SAN) 的方式。 SAN 的選項取決於所選憑證類型 ([使用者]  或 [裝置]  )。  

      - **使用者憑證類型**  
        從可用的屬性中選取：  
        - **電子郵件地址**
        - **使用者主體名稱 (UPN)** 

        例如，使用者憑證類型可以在主體別名中包含使用者主體名稱 (UPN)。 如果用戶端憑證是用來驗證網路原則伺服器，您必須將主體別名設定為 UPN。

      - **裝置憑證類型**  
        使用 [屬性]  下拉式清單並選取屬性、指派**值**，並將其**新增**至憑證設定檔。 您可以藉由選取其他屬性來新增多個值。  

        可用的屬性包括：
        - **電子郵件地址**
        - **使用者主體名稱 (UPN)**
        - **DNS**

        透過 [裝置]  憑證類型，您可以使用下列裝置憑證變數作為值：  

        - **{{AAD_Device_ID}}**
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{AzureADDeviceId}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}**
        - **{{MEID}}**

        若要指定屬性的值，請將變數名稱加上大括弧，後接該變數的文字。 例如，DNS 屬性的值可以新增 **{{AzureADDeviceId}}.domain.com**，其中的 *.domain.com* 為文字。 針對名為 *User1* 的使用者，電子郵件地址可能會顯示為 {{FullyQualifiedDomainName}}User1@Contoso.com。  

        > [!IMPORTANT]  
        > - 當您使用裝置憑證變數時，請用大括弧 { } 將變數名稱括住。  
        > - 請不要在變數後面的文字中使用大括弧 **{ }** 、管線符號 **|** 和分號 **;** 。  
        > - 裝置憑證的「主體」  或 *SAN* 中所使用裝置屬性 (例如 **IMEI**、**SerialNumber** 和 **FullyQualifiedDomainName**)，這些屬性可由具有裝置存取權的人員來偽造。  
        > - 裝置必須支援憑證設定檔中指定的所有變數，才能在該裝置上安裝該設定檔。  例如，如果 SCEP 設定檔的 SAN 中使用 **{{IMEI}}** ，但該設定檔指派給沒有 IMEI 編號的裝置，則設定檔安裝將會失敗。

   - **憑證有效期間**：  
     您可以輸入一個比憑證範本中指定的有效期間更低，而不是更高的值。 如果您已將憑證範本設定為[支援可從 Intune 主控台內設定的自訂值](certificates-scep-configure.md#modify-the-validity-period-of-the-certificate-template)，請使用此設定來指定憑證到期之前的剩餘時間量。  

     例如，如果憑證範本中的憑證有效期間為兩年，您可以輸入一年而不是五年的值。 該值也必須低於發行 CA 憑證的剩餘有效期。

   - **金鑰儲存提供者 (KSP)** ：  
     *(適用於：Windows 8.1 和更新版本，以及 Windows 10 和更新版本)*  
     
     指定儲存憑證金鑰的位置。 選擇下列值：  
     - **註冊至受信任平台模組 (TPM) KSP (如果存在)，否則註冊至軟體 KSP**
     - **註冊至信賴平台模組 (TPM) KSP，否則失敗**
     - **註冊至 Passport，否則失敗 (Windows 10 及更新版本)**
     - **註冊至軟體 KSP**

   - **金鑰使用方法**：  
     選取憑證的金鑰使用方法選項：

     - **數位簽章**：只有在有數位簽章協助保護金鑰時，才允許交換金鑰。
     - **金鑰編密**：只有在已將金鑰加密時，才允許交換金鑰。  

   - **金鑰大小 (位元)** ：  
     選取金鑰中包含的位元數。  

   - **雜湊演算法**：  
     *(適用於 Android、Android enterprise、Windows Phone 8.1、Windows 8.1 和更新版本，以及 Windows 10 和更新版本)*  

     選取其中一種可用的雜湊演算法類型，以搭配此憑證使用。 選取連線中裝置所支援的最強安全性層級。

   - **根憑證**：  
     選取您先前設定並指派給此 SCEP 憑證設定檔所適用使用者和裝置的「受信任憑證設定檔」  。 受信任憑證設定檔用於使用受信任的根 CA 憑證來佈建使用者和裝置。 如需受信任憑證設定檔的資訊，請參閱＜在 Intune 中使用憑證以進行驗證＞  中的[＜匯出受信任的根 CA 憑證＞](certificates-configure.md#export-the-trusted-root-ca-certificate)和[＜建立受信任的憑證設定檔＞](certificates-configure.md#create-trusted-certificate-profiles)。 如果您有根憑證授權單位與發行憑證授權單位，請選取與發行憑證授權單位建立關聯的受信任根憑證設定檔。

   - **擴充金鑰使用方法**：  
     針對憑證的使用目的新增值。 在大部分情況下，憑證需要「用戶端驗證」  ，使用者或裝置才能向伺服器進行驗證。 您可以視需要新增其他金鑰使用方法。

   - **更新閾值 (%)** ：  
     輸入裝置要求更新憑證之前，剩餘的憑證存留時間百分比。 例如，如果您輸入 20，則憑證會在 80% 過期時會嘗試更新。 系統會繼續嘗試更新，直到更新成功。 更新會產生新的憑證，而這會產生新的公開/私密金鑰組。

   - **SCEP 伺服器 URL**：  
     輸入一或多個透過 SCEP 發行憑證的 NDES 伺服器 URL。 例如，輸入類似 *https://ndes.contoso.com/certsrv/mscep/mscep.dll* 的內容。 您可以視需要新增額外的 SCEP URL 來進行負載平衡，因為 URL 會隨機推送至具有設定檔的裝置。 如果其中一個 SCEP 伺服器不可用，則 SCEP 要求將會失敗，且可能會在稍後的裝置簽入中對已關閉的相同伺服器提出憑證要求。

7. 選取 [確定]  ，然後選取 [建立]  。 設定檔隨即建立，並會出現在 [裝置設定 - 設定檔]  清單上。

### <a name="avoid-certificate-signing-requests-with-escaped-special-characters"></a>避免使用具有已逸出之特殊字元的憑證簽署要求
當 SCEP 和 PKCS 憑證要求包含具有一或多個下列特殊字元作為逸出字元的主體名稱 (CN) 時，有一個已知問題。 包含其中一個特殊字元作為逸出字元的主體名稱會導致 CSR 的主體名稱不正確。 不正確的主體名稱會導致 Intune SCEP 挑戰驗證失敗，且不會簽發任何憑證。

特殊字元為：
- \+
- 、
- ;
- =

當您的主體名稱包含其中一個特殊字元時，請使用下列其中一個選項來因應此限制：  
- 使用引號括住包含特殊字元的 CN 值。  
- 將特殊字元從 CN 值移除。  

**例如**，您有顯示為 *Test user (TestCompany, LLC)* 的主體名稱。  若 CSR 包含之 CN 中的 *TestCompany* 與 *LLC* 之前有逗點，則會發生問題。  使用引號括住整個 CN，或移除 *TestCompany* 與 *LLC* 之間的逗號，即可避免此問題：
- **加上引號**：*CN=* ”Test User (TestCompany, LLC)”,OU=UserAccounts,DC=corp,DC=contoso,DC=com*
- **移除逗號**：*CN=Test User (TestCompany LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

 不過，嘗試使用反斜線字元來逸出逗號將會失敗，而且 CRP 記錄中會記錄錯誤：  
- **逸出的逗號**：*CN=Test User (TestCompany\\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

錯誤與下列錯誤類似： 

```
Subject Name in CSR CN="Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com" and challenge CN=Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com do not match  

  Exception: System.ArgumentException: Subject Name in CSR and challenge do not match

   at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

Exception:    at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

   at Microsoft.ConfigurationManager.CertRegPoint.Controllers.CertificateController.VerifyRequest(VerifyChallengeParams value
```

## <a name="assign-the-certificate-profile"></a>指派憑證設定檔
請使用與您為其他用途[部署裝置設定檔](../configuration/device-profile-assign.md)的相同方式，來指派 SCEP 憑證設定檔。 不過，在繼續之前請先考慮下列事項：

- 當您指派 SCEP 憑證設定檔給群組時，受信任根 CA 憑證檔案 (如同在「受信任憑證設定檔」  中所指定) 即會安裝在裝置上。 裝置會使用 SCEP 憑證設定檔來建立該受信任根 CA 憑證的憑證要求。  

- SCEP 憑證設定檔只會安裝在執行您建立憑證設定檔時所指定平台的裝置上。

- 您可以將憑證設定檔指派到使用者集合或裝置集合。

- 若要在裝置註冊之後快速將憑證發行至裝置，請將憑證設定檔指派到使用者群組，而不是裝置群組。 如果您將它指派至裝置群組，便必須先執行完整的裝置註冊，裝置才能接收原則。  

- 如果您針對 Intune 和 Configuration Manager 使用共同管理，請在 Configuration Manager 中，將資源存取原則的[工作負載滑桿設定為](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads) [Intune]  或 [試驗 Intune]  。 此設定可讓 Windows 10 用戶端啟動要求憑證的流程。

- 雖然您會分別建立及指派受信任的憑證設定檔和 SCEP 憑證設定檔，但兩者都必須受指派。 如果裝置上未安裝這兩者，SCEP 憑證原則將會失敗。 請確定所有受信任根憑證設定檔都會部署到與 SCEP 設定檔相同的群組。


> [!NOTE]
> 在 iOS 裝置上，當 SCEP 憑證設定檔與額外設定檔 (例如 Wi-Fi 或 VPN 設定檔) 關聯時，裝置會接受那些每個額外設定檔的憑證。 這會導致 iOS 裝置具有多個由 SCEP 憑證要求提供的憑證。  如果需要單一憑證，您必須使用 PKCS 憑證，而不是 SCEP 憑證。  這是因為 SCEP 和 PKCS 憑證傳遞至裝置的方式有所差異。


## <a name="next-steps"></a>後續步驟  

[指派設定檔](../configuration/device-profile-assign.md)  
