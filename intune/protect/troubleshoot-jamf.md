---
title: 針對 Jamf Pro 與 Microsoft Intune 的整合進行疑難排解
titleSuffix: Microsoft Intune
description: 當您將 Jamf Pro for Mac 裝置與 Microsoft Intune 整合時，針對其中一些最常見的問題進行疑難排解的建議。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e92e3442e1347cb1a2cd1c737078912b74f075c9
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71817634"
---
# <a name="troubleshoot-integration-of-jamf-pro-with-microsoft-intune"></a>針對 Jamf Pro 與 Microsoft Intune 的整合進行疑難排解

本文可協助 Intune 系統管理員瞭解並疑難排解 Jamf Pro for macOS 與 Intune 整合的問題。

> [!TIP]  
> 本文中的大部分資訊都是在[您將 Jamf 與 support.microsoft.com 上的 Microsoft Intune 整合時，在疑難排解問題](https://support.microsoft.com/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune)中出現。

## <a name="prerequisites"></a>必要條件

開始進行疑難排解之前，請先收集一些基本資訊來澄清問題，並縮短尋找解決方案的時間。 例如，當您遇到 Jamf-Intune 整合相關的問題時，請務必確認必要條件已符合。 開始進行疑難排解之前，請先參閱下列考慮：

- 請參閱[整合 Jamf Pro 與 Intune](conditional-access-integrate-jamf.md#prerequisites)的必要條件。
- 所有使用者都必須擁有 Microsoft Intune 和 Microsoft AAD Premium P1 授權 
- 您必須在 Jamf Pro 主控台中擁有具有 Microsoft Intune 整合許可權的使用者帳戶。
- 您必須具有在 Azure 中具有全域系統管理員許可權的使用者帳戶。


調查 Jamf Pro 與 Intune 的整合時，請考慮下列資訊： 
- 確切錯誤訊息為何？
- 錯誤訊息在哪裡？
- 問題何時開始發生？  Jamf Pro 與 Intune 的整合是否有作用？
- 有多少使用者受到影響？ 所有使用者都會受到影響，還是只有部分？
- 有多少裝置受到影響？ 所有裝置是否受到影響，或只是部分？
 

## <a name="common-problems"></a>常見問題 

下列資訊可協助您在設定 Intune 和 Jamf Pro 整合之後，識別並解決裝置的常見問題。  

| 問題   | 詳細資訊                  |
|-----------------|--------------------------|
| **Jamf Pro 中的裝置會標示為沒有回應**  | [裝置無法使用 Jamf Pro 或 Azure AD 簽入](#devices-are-marked-as-unresponsive-in-jamf-pro) |
| **當您開啟應用程式裝置無法註冊時，Mac 裝置會提示您進行 keychain 登入**  | [系統會提示使用者輸入密碼，以允許應用程式向 Azure AD 註冊](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app)。 |
| **裝置無法註冊**  | 下列原因可能會適用： <br> **-** [***會導致 1*** -Azure 中的 Jamf Pro 應用程式具有不正確的許可權](#cause-1) <br> **-** [***會導致 2*** -在 Azure AD 中有*Jamf Native macOS 連接器*的問題](#cause-2) <br> **-** [***原因 3*** -使用者沒有有效的 Intune 或 Jamf 授權](#cause-3) <br> **-** [***會導致 4*** -使用者未使用 Jamf 自助服務來啟動公司入口網站應用程式](#cause-4) <br> **-** [***會導致 5*** -Intune 整合已關閉](#cause-5) <br> **-** [***會導致 6*** -裝置先前已在 Intune 中註冊，或使用者已嘗試多次註冊裝置](#cause-6) <br> **-** [***會導致 7*** JamfAAD 要求從使用者的 keychain 存取「Microsoft Workplace Join 金鑰」](#cause-7) |
|  **Mac 裝置在 Intune 中顯示為符合規範，但在 Azure 中不相容** | [裝置註冊問題](#mac-device-shows-compliant-in-intune-but-noncompliant-in-azure) |
| **使用 Jamf 註冊的 Mac 裝置的 Intune 主控台中出現重複的專案** | [相同裝置的多個註冊](#duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf) |
| **合規性政策無法評估裝置** | [原則目標裝置群組](#compliance-policy-fails-to-evaluate-the-device) |
| **無法取得 Microsoft Graph API 的存取權杖** | 下列原因可能會適用： <br> [在 Azure 中 Jamf Pro 應用程式](#theres-a-permission-issue-with-the-jamf-pro-application-in-azure)的 - 許可權 <br> -  已[過期的 Jamf 或 Intune 授權](#a-license-required-for-jamf-intune-integration-has-expired) <br> **-** [埠未開啟](#the-required-ports-arent-open-on-your-network)|
 

### <a name="devices-are-marked-as-unresponsive-in-jamf-pro"></a>Jamf Pro 中的裝置會標示為沒有回應  

**原因**：下列是 Jamf Pro 將裝置標示為*沒有回應*的常見原因：

- 裝置無法使用 Jamf Pro 簽入。  
  Jamf Pro 預期裝置每隔15分鐘會檢查一次。 當裝置無法在24小時內進行檢查時，Jamf 會將其標示為沒有回應。  

- 裝置無法使用 Azure AD 簽入。  
  成功註冊至 Azure AD 之後，macOS 裝置會收到 Azure 權杖：
  - 此權杖每12小時會重新整理一次。   
  - 當令牌重新整理失敗24小時或以上時，Jamf Pro 會將裝置標示為沒有回應。  
  - 如果 Azure 權杖過期，系統會提示使用者登入 Azure 以取得新的權杖。 Azure 存取的重新整理權杖會每七天產生一次。

**解決方法**  
當 Jamf Pro 將裝置標示為*沒有回應*之後，裝置的已註冊使用者必須登入，以更正未回應的狀態。 它必須是已加入工作的使用者，因為他們在登入 keychain 中具有 Intune 的身分識別。



### <a name="mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app"></a>當您開啟應用程式時，Mac 裝置會提示您進行 keychain 登入  

設定 Intune 和 Jamf Pro 整合並部署條件式存取原則之後，使用 Jamf Pro 所管理之裝置的使用者會在開啟 Microsoft Office 365 應用程式（例如小組、Outlook 和其他需要 Azure 的應用程式）時提示輸入密碼AD 驗證。 

例如，開啟 Microsoft 團隊時，會出現類似下列範例的文字提示：

``` 
  Microsoft Teams wants to sign using key “Microsoft Workplace Join Key” in your keychain.  
  To allow this, enter the “login” keychain password 
```

**原因**： Jamf Pro 會針對需要 Azure AD 註冊的每個適用應用程式產生這些提示。 

**解決方法**   
在提示字元中，使用者必須提供其裝置密碼，才能登入 Azure AD。 這些選項包括：
- **拒絕**-不要登入，也不要使用應用程式。
- **允許**-一次登入。 下次開啟應用程式時，它會提示您重新登入。
- **一律允許**-快取應用程式的登入認證。 下次應用程式開啟時，不會提示您登入。  

選取 [*永遠允許*一個應用程式] 只會核准該應用程式以供未來登入。 其他應用程式會提示您進行驗證，直到它們也設定為 [*永遠允許*] 為止。 一個應用程式的快取認證無法供另一個應用程式使用。  

### <a name="devices-fail-to-register"></a>裝置無法註冊  

無法註冊的 Mac 裝置有數個常見的原因。  

#### <a name="cause-1"></a>原因 1  

**Azure 中的 Jamf Pro 企業應用程式具有錯誤的許可權，或具有一個以上的許可權**  

  當您在 Azure 中建立應用程式時，您必須移除所有預設 API 許可權，然後將*update_device_attributes*的單一許可權指派給 Intune。 

  **解決方法**  
  請檢查並視需要修正您在 Azure AD 中建立之 Jamf 應用程式的許可權。 請參閱[在 Azure AD 中建立應用程式以進行 Jamf 的程式](conditional-access-integrate-jamf.md#create-an-application-in-azure-active-directory)。 

#### <a name="cause-2"></a>原因 2  

**未在您的 Azure AD 租使用者中建立**Jamf Native MacOS 連接器**應用程式，或同意連接器已由沒有全域系統管理員許可權的帳戶簽署**  

  **解決方法**  
  請參閱 < 在 docs.jamf.com 上[整合 Microsoft Intune](https://docs.jamf.com/10.13.0/jamf-pro/administrator-guide/Integrating_with_Microsoft_Intune.html)中的設定*macOS Intune 整合*一節。 

#### <a name="cause-3"></a>原因 3

**使用者沒有有效的 Intune 或 Jamf 授權**  

  缺少有效的授權可能會導致下列錯誤，這表示 Jamf 授權已過期：  
  ```
    Unable to connect to Microsoft Intune.  
    
    Check your Microsoft Intune Integration configuration.
  ```  

  **解決方法**
  - Jamf 授權：聯絡 Jamf 以取得 Jamf 的新授權的協助。  
  - Intune 授權：為使用者指派有效的授權，或洽詢 Microsoft 或您的合作夥伴，以取得如何取得目前授權的相關資訊。

#### <a name="cause-4"></a>原因 4  

**使用者未使用*Jamf 自助服務*來啟動公司入口網站應用程式**

若要讓裝置透過 Jamf 成功註冊並向 Intune 註冊，使用者必須使用 Jamf 自助服務來開啟 Intune 公司入口網站。 如果使用者手動開啟公司入口網站，則裝置會註冊並註冊，而不會連線到 Jamf。  

若要判斷裝置用來註冊和註冊的服務，請查看裝置上的公司入口網站應用程式。 透過 Jamf 註冊時，您應該會收到開啟自助應用程式以進行變更的通知。

在公司入口網站應用程式中，使用者可能會看到 **`Not registered`** ，而公司入口網站記錄中可能會出現類似下列範例的專案：  

```
   Line 7783: <DATE> <IP ADDRESS> INFO com.microsoft.ssp.application TID=1  
 
   WelcomeViewController.swift: 253 (startLogin()) Portal launched without WPJ only arg while account is under partner management
```

**解決方法**  
若要將註冊來源從 Intune 變更為 Jamf：
1. [從 Intune 取消註冊 macOS 裝置](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-macos)。 為避免從 Intune 完全移除的裝置有更多的複雜性，請參閱這份原因清單中的[*原因 6*](#cause-6) 。  

2. 在裝置上，使用 Jamf 自助服務開啟公司入口網站應用程式，然後向 Intune 註冊裝置。 這項工作需要您[使用 Jamf 來部署適用于 macOS 的公司入口網站應用程式](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)，並[在 Jamf Pro 中建立了向 Azure AD 註冊使用者裝置的原則](conditional-access-assign-jamf.md#create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory)。  

3. 當入口網站開啟時，您看到的第一個畫面會提示您登入。 使用公司或學校帳戶  

4. 公司入口網站會確認您的帳戶資訊，並顯示您的裝置註冊和裝置合規性狀態。 黃色三角形醒目提示您需要採取以保護學校或公司用 macOS 裝置的動作。 按一下 [開始] 開始註冊。  

5. 如果出現提示，請鍵入您電腦的登入資訊。  
     
註冊裝置管理可能需要幾分鐘的時間。 在此期間，您可以在裝置上執行其他事項。 完成公司存取設定之後，您會收到一則訊息，讓您知道已完成。

#### <a name="cause-5"></a>原因 5  

**Intune 整合已關閉**

如果關閉 Intune 整合，當使用者嘗試註冊裝置時，會在公司入口網站中收到快顯視窗，並顯示下列訊息：  

```
   Invalid command line input
   
   Registration-only command line flag (-r) can only be used when partner management is enabled in Intune. Please contact your IT admin.
```  

當整合關閉時，Jamf Pro 伺服器會將脈衝傳送至 Intune 伺服器，告知 Intune 已停用整合。 

**解決方法**  
重新啟用 Jamf Pro 中的 Intune 整合。 請參閱[在 Jamf Pro 中設定 Microsoft Intune 整合](conditional-access-integrate-jamf.md#enable-intune-to-integrate-with-jamf-pro)。


#### <a name="cause-6"></a>原因 6  

**裝置先前已在 Intune 中註冊，或使用者已嘗試多次註冊裝置**

如果裝置是從 Jamf 取消註冊，但未從 Intune 中正確移除，或已嘗試進行多次註冊，您可能會在入口網站中看到相同裝置的多個實例。 這會導致 Jamf 註冊失敗。

**解決方法**  
1. 在 Mac 上，啟動 [**終端**機]。
2. 執行**SUDO JAMF removemdmprofile**。
3. 執行**SUDO JAMF removeFramework**。
4. 在 JAMF Pro 伺服器上，刪除電腦的清查記錄。
5. 從 AzureAD 刪除裝置。
6. 刪除裝置上的下列檔案（如果有的話）：
   - /Library/application support Support/CompanyPortal. usercoNtext. 資訊
   - /Library/application support Support/CompanyPortal
   - /Library/application support Support/jamfsoftware. selfservice. mac
   - /Library/Saved 應用程式
   - State/jamfsoftware. selfservice. savedState
   - /Library/Saved 應用程式狀態/CompanyPortal. savedState
   - /Library/Preferences/com.microsoft.CompanyPortal.plist
   - /Library/Preferences/com.jamfsoftware.selfservice.mac.plist
   - /Library/Preferences/com.jamfsoftware.management.jamfAAD.plist
   - /Users/<username>/Library/Cookies/.com. CompanyPortal. binarycookies
   - /Users/<username>/Library/Cookies/jamf. jamfAAD. binarycookies
   - CompanyPortal
   - CompanyPortal. HockeySDK
   - enterpriseregistration.windows.net
   - https://device.login.microsoftonline.com
   - https://device.login.microsoftonline.com/
   - Microsoft 會話傳輸金鑰（公開和私密金鑰）
   - Microsoft Workplace Join 金鑰（公開和私密金鑰）
7. 從參照*Microsoft*、 *Intune*或*公司入口網站*的裝置上的 keychain 中移除任何專案，包括 DeviceLogin.microsoft.com 憑證。 移除*JAMF*參考，但不包括 JAMF 公開和私密金鑰。 
   > [!IMPORTANT]  
   > 移除公開和私密金鑰將會中斷裝置註冊。

8. 刪除您發現的下列任何專案：  
   - 種類：應用程式密碼;帳戶： workplacejoin.exe. 指紋
   - 種類：應用程式密碼;帳戶： workplacejoin.exe. registeredUserPrincipalName
   - 種類： Certificate;簽發者： MS-組織存取
   - 種類：身分識別喜好設定;名稱（ADFS STS URL （如果有的話）： https://adfs\<DNSName>.com/adfs/ls
   - 種類：身分識別喜好設定;名稱： https://enterpriseregistration.windows.net
   - 種類：身分識別喜好設定;名稱： https://enterpriseregistration.windows.net/  
9. 重新開機 Mac 裝置。
10. 從裝置卸載公司入口網站。
11. 請移至 portal.manage.microsoft.com，並刪除 Mac 裝置的所有實例。 請至少等候30分鐘，再移至下一個步驟。
12. 在 JAMF Pro 中重新註冊裝置。
13. 重新開啟自助服務並啟動註冊原則。


#### <a name="cause-7"></a>原因 7  

**JamfAAD 會要求從使用者的 keychain 存取「Microsoft Workplace Join 金鑰」**

在註冊期間，macOS 裝置的使用者會收到下列提示，允許從其 keychain 存取金鑰的 JamfAAD： 

```
   JamfAAD wants to access key “Microsoft Workplace Join Key" in your keychain. 
    
   To allow this, enter the “login” keychain password
```

**解決方法**  
若要使用 Azure AD 成功註冊裝置，Jamf 會要求使用者提供其帳戶密碼，然後選取 [**允許**]。

這項要求類似于[您在開啟應用程式時，keychain 登入的 Mac 裝置要求提示](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app)，請參閱本文稍早的。  

 
### <a name="mac-device-shows-compliant-in-intune-but-noncompliant-in-azure"></a>Mac 裝置在 Intune 中顯示為符合規範，但在 Azure 中不相容  

**原因**：下列情況可能會導致裝置在 Intune 中顯示為符合規範，但在 Azure 中不符合規範：  
- 裝置未正確註冊。  
- 已多次註冊裝置，但沒有必要的清除。

**解決方法**  
若要解決此問題，請遵循本文稍早所述的「*裝置無法註冊*的[*原因 6*](#cause-6) 」的解決方法。 


### <a name="duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf"></a>使用 Jamf 註冊的 Mac 裝置的 Intune 主控台中出現重複的專案  
 
**原因**：裝置已多次向 intune 註冊，通常會在從 Intune 移除之後重新註冊。  

當裝置從 Intune 和 Jamf Pro 整合中移除時，某些資料可能會遺留下來，而可能導致後續的註冊建立重複的專案。  

**解決方法**  
若要解決此問題，請遵循本文稍早所述的「*裝置無法註冊*的[*原因 6*](#cause-6) 」的解決方法。 

### <a name="compliance-policy-fails-to-evaluate-the-device"></a>合規性政策無法評估裝置  

**原因**： Jamf 與 Intune 整合不支援以裝置群組為目標的合規性政策。 

**解決方法**  
修改要指派給使用者群組之 macOS 裝置的相容性原則。 


### <a name="could-not-retrieve-the-access-token-for-microsoft-graph-api"></a>無法取得 Microsoft Graph API 的存取權杖

您會收到下列錯誤：

```
   Could not retrieve the access token for Microsoft Graph API. Check the configuration for Microsoft Intune Integration.
```   

此錯誤的來源可能是下列其中一個原因： 

#### <a name="theres-a-permission-issue-with-the-jamf-pro-application-in-azure"></a>Azure 中的 Jamf Pro 應用程式發生許可權問題

在 Azure 中註冊 Jamf Pro 應用程式時，發生下列其中一種情況：  
- 應用程式收到一個以上的許可權。
- 未選取 [ ***\<your 公司 >*** ] 選項的 [授與系統管理員同意]。  

**解決方法**  
請參閱本文稍早的針對[裝置無法註冊](#devices-fail-to-register)的原因1的解決方式。

#### <a name="a-license-required-for-jamf-intune-integration-has-expired"></a>Jamf 所需的授權-Intune 整合已過期

**解決**方式：請參閱原因3的解決方式，[裝置無法註冊](#devices-fail-to-register)。 

#### <a name="the-required-ports-arent-open-on-your-network"></a>未在您的網路上開啟所需的埠

**解決**方式：請參閱整合 Jamf Pro 與 Intune 的[必要條件](conditional-access-integrate-jamf.md#prerequisites)中的網路埠資訊。


## <a name="next-steps"></a>後續步驟
深入瞭解如何[整合 Jamf Pro 與 Intune](conditional-access-integrate-jamf.md)