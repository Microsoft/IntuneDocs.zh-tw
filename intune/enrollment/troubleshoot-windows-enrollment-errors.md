---
title: 針對 Microsoft Intune 中的 Windows 裝置註冊問題進行疑難排解
titleSuffix: Microsoft Intune
description: 針對在 Intune 中註冊 Windows 裝置時的一些最常見問題進行疑難排解的建議。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 46012b11cdb458243658e858b53c2dfb1a69dc88
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991793"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>針對 Microsoft Intune 中的 Windows 裝置註冊問題進行疑難排解

本文可協助 Intune 系統管理員瞭解並疑難排解在 Intune 中註冊 Windows 裝置時的問題。

## <a name="prerequisites"></a>必要條件
開始進行疑難排解之前，請務必收集一些基本資訊。 此資訊可協助您進一步瞭解問題，並縮短尋找解決方案的時間。

收集與問題相關的下列資訊：
- 是否已將有效的 Intune 授權指派給使用者？ 使用者必須先獲指派所需的授權，才可以註冊其裝置。
- Windows 裝置上是否已安裝最新的更新？ Intune 中的某些功能僅適用于最新版本的 Windows。 透過 Windows Update 可取得的已知問題有許多修正。 套用所有最新的更新通常會修正 Windows 裝置註冊問題。 
- 確切錯誤訊息為何？
- 您會在哪裡看到錯誤訊息？
- 問題何時開始發生？ 註冊是否曾經有作用？ 
- 哪個平臺（Android、iOS、Windows）有問題？
- 有多少使用者受到影響？ 所有使用者都會受到影響，還是只有部分？
- 有多少裝置受到影響？ 所有裝置是否受到影響，或只是部分？
- 什麼是 MDM 授權單位？ 如果 System Center Configuration Manager，您使用的是哪一版的 Configuration Manager？
- 如何執行註冊？ 它是「攜帶您自己的裝置」（BYOD）或 Apple 裝置註冊計劃（DEP）與註冊設定檔嗎？

## <a name="error-messages"></a>錯誤訊息

### <a name="this-user-is-not-authorized-to-enroll"></a>此使用者未獲授權，無法註冊。

錯誤0x801c003：「此使用者未獲授權，無法註冊。 您可以再試一次，或洽詢您的系統管理員，並提供錯誤碼（錯誤碼為0x801c0003）。
錯誤 80180003：「發生問題。 此使用者未獲授權，無法註冊。 您可以再試一次，或洽詢您的系統管理員，錯誤碼80180003。」

**原因：** 下列任何一項條件： 

- 使用者已註冊 Intune 中允許的裝置數目上限。    
- 裝置會受到裝置類型限制的封鎖。    
- 電腦正在執行 Windows 10 家用版。 不過，只有在 Windows 10 專業版和更新版本上，才支援在 Intune 中註冊或加入 Azure AD。

#### <a name="resolution"></a>解決方案
此問題有幾種可能的解決方式：

##### <a name="remove-devices-that-were-enrolled"></a>移除已註冊的裝置
1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。    
2. 前往 [**使用者**] > [**所有使用者**]。    
3. 選取受影響的使用者帳戶，然後按一下 [**裝置**]。    
4. 選取任何未使用或不想要的裝置，然後按一下 [**刪除**]。 

##### <a name="increase-the-device-enrollment-limit"></a>提高裝置註冊限制

> [!NOTE]
> 這個方法會增加所有使用者的裝置註冊限制，而不只是受影響的使用者。

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 移至 **裝置** > **註冊限制** > **預設值**（在 **裝置限制** 下） >**屬性** > **編輯** （**裝置限制** 旁） > 增加 **裝置限制** （最多15個） >**評論 + 儲存**。    
 

##### <a name="check-device-type-restrictions"></a>檢查裝置類型限制
1. 使用全域系統管理員帳戶登入[Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 移至 [**裝置**] > [**註冊限制**]，然後在 [**裝置類型限制**] 下選取**預設**限制。    
3. 選取 [**平臺**]，然後選取 [**允許** **Windows （MDM）** ]。

    > [!IMPORTANT]
    > 如果目前的設定已**允許**，請將它變更為 [**封鎖**]，儲存設定，然後將它變更回 [**允許**]，然後再次儲存設定。 這會重設註冊設定。

4. 等候約15分鐘，然後再次註冊受影響的裝置。    

##### <a name="upgrade-windows-10-home"></a>升級 Windows 10 家用版
[將 windows 10 首頁升級至 windows 10 專業](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro)版或更高版本。 



### <a name="this-user-is-not-allowed-to-enroll"></a>不允許此使用者註冊。

錯誤錯誤碼為0x801c0003：「不允許此使用者註冊。 您可以再試一次，或洽詢您的系統管理員，錯誤碼801c0003。」

**原因：** [**使用者可以將裝置加入 Azure AD** ] 設定設為 [**無**]。 這可防止新使用者將其裝置加入 Azure AD。 因此，Intune 註冊會失敗。

#### <a name="resolution"></a>解決方案
1. 以系統管理員身分登入 [Azure 入口網站](https://portal.azure.com/)。    
2. 移至 [ **Azure Active Directory** ] [ > **裝置**] > [**裝置設定**]。    
3. 將 [使用者可以將裝置加入 Azure AD]  設定為 [全部]  。    
4. 重新註冊裝置。   

### <a name="the-device-is-already-enrolled"></a>已註冊該裝置。

錯誤8018000a：「發生問題。 已註冊該裝置。  您可以與系統管理員聯繫，錯誤碼8018000a。」

**原因：** 下列其中一個條件成立：
- 不同的使用者已在 Intune 中註冊裝置，或已將裝置加入至 Azure AD。 若要判斷是否為這種情況，請移至 [**設定**] > [**帳戶**] > [**公司存取**]。 尋找與下列類似的訊息：「系統上的另一個使用者已連線至公司或學校。 請移除該公司或學校的連線，然後再試一次。」    
- 電腦上已安裝 Configuration Manager 用戶端代理程式。    

#### <a name="resolution"></a>解決方案

使用下列方法來解決此問題：

##### <a name="remove-the-other-work-or-school-account"></a>移除其他工作或學校帳戶
1. 登出 Windows，然後使用已註冊或已加入裝置的其他帳戶登入。    
2. 移至 [**設定**] > [**帳戶**] > [**公司存取**]，然後移除工作或學校帳戶。
3. 登出 Windows，然後使用您的帳戶登入。    
4. 在 Intune 中註冊裝置，或將裝置加入至 Azure AD。 

##### <a name="remove-the-configuration-manager-client"></a>移除 Configuration Manager 用戶端
移除 Configuration Manager 用戶端，然後再次註冊裝置。



### <a name="this-account-is-not-allowed-on-this-phone"></a>此電話不允許此帳戶。

錯誤：「此電話上不允許此帳戶。 請確定您提供的資訊正確，然後再試一次，或向您的公司要求支援。」

**原因：** 嘗試註冊裝置的使用者沒有有效的 Intune 授權。

#### <a name="resolution"></a>解決方案
將有效的 Intune 授權指派給使用者，然後註冊裝置。


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>看起來像是未正確設定 MDM 使用規定端點。

**原因：** 下列其中一個條件成立： 
 - 您在租使用者上同時使用適用于 Office 365 和 Intune 的行動裝置管理（MDM），而嘗試註冊裝置的使用者沒有有效的 Intune 授權或 Office 365 授權。     
- Azure AD 中的 MDM 條款及條件為空白或未包含正確的 URL。    

#### <a name="resolution"></a>解決方案

若要修正此問題，請使用下列其中一種方法： 
 
##### <a name="assign-a-valid-license-to-the-user"></a>指派有效的授權給使用者
移至[Microsoft 365 系統管理中心](https://portal.office.com/adminportal/home)，然後將 Intune 或 Office 365 授權指派給使用者。

##### <a name="correct-the-mdm-terms-of-use-url"></a>更正 MDM 使用規定 URL
  1. 登入 [Azure 入口網站](https://portal.azure.com/)，然後選取 [Azure Active Directory]  。    
  2. 選取 **[行動性（MDM 與 MAM）** ]，然後按一下 [ **Microsoft Intune**]。    
  3. 選取 [**還原預設的 Mdm url**]，確認 [ **MDM 使用規定 URL** ] 已設定為 [ **https://portal.manage.microsoft.com/TermsofUse.aspx** ]。    
  4. 選擇 [儲存]  。    


### <a name="something-went-wrong"></a>發生問題。

錯誤 80180026：「發生問題。 請確認您使用的是正確的登入資訊，而且您的組織使用這項功能。 您可以再試一次，或洽詢您的系統管理員，錯誤碼80180026。」

**原因：** 當您嘗試將 Windows 10 電腦加入 Azure AD，而且下列兩個條件都成立時，就會發生此錯誤： 
- Azure 中已啟用 MDM 自動註冊。    
- Intune 電腦用戶端（Intune PC 代理程式）或 Configuration Manager 用戶端代理程式已安裝在 Windows 10 電腦上。

#### <a name="resolution"></a>解決方案
使用下列其中一個方法來解決此問題：

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>停用 Azure 中的 MDM 自動註冊。
1. 登入 [Azure 入口網站](https://portal.azure.com/)。    
2. 請移至**Azure Active Directory** > **行動性（MDM 與 MAM）**  > **Microsoft Intune**。    
3. 將 [ **MDM 使用者範圍**] 設定為 [**無**]，然後按一下 [**儲存**]。    
     
##### <a name="uninstall"></a>解除安裝
卸載電腦上的 Intune 電腦用戶端或 Configuration Manager 用戶端代理程式。    

### <a name="the-software-cannot-be-installed"></a>無法安裝軟體。

錯誤：「無法安裝軟體，0x80cf4017。」

**原因：** 用戶端軟體已過期。

#### <a name="resolution"></a>解決方案
1. 登入 [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)。    
2. 移至 [系統**管理**] > [**用戶端軟體下載**]，然後按一下 [**下載用戶端軟體**]。    
3. 儲存安裝套件，然後再安裝用戶端軟體。 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>帳戶憑證無效，而且可能已經過期。

錯誤：「此帳戶憑證無效，而且可能已經過期，0x80cf4017。」

**原因：** 用戶端軟體已過期。

#### <a name="resolution"></a>解決方案
1. 登入 [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)。    
2. 移至 [系統**管理**] > [**用戶端軟體下載**]，然後按一下 [**下載用戶端軟體**]。    
3. 儲存安裝套件，然後再安裝用戶端軟體。    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>您的組織不支援此版本的 Windows。 

錯誤：「發生問題。 您的組織不支援此版本的 Windows。  （顯示0x80180014） "

**原因：** Intune 租使用者中的 Windows MDM 註冊已停用。

#### <a name="resolution"></a>解決方案
若要在獨立的 Intune 環境中修正此問題，請遵循下列步驟： 
 
1. 在[Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選擇 [**裝置**] > **註冊限制**] > 選擇 [裝置類型] [限制]。    
2. 選擇 **屬性** > **編輯** （在 **平臺設定** 旁） >**允許** **Windows （MDM）** 。    
3. 按一下 [**審核] + [儲存**]。    
 
若要在具有 Intune 和 Configuration Manager 的混合式 MDM 中修正此問題，請遵循下列步驟： 
1. 開啟 Configuration Manager 主控台。    
2. 選取 [系統**管理**]，然後選取 [**雲端服務**]。    
3. 以滑鼠右鍵按一下 [ **Microsoft Intune 訂**用帳戶]，然後選取 [**設定 > Windows 的平臺**]。    
4. 勾選 **啟用 Windows 註冊** ** > 套用** > **確定**。  


### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>大量註冊期間發生安裝程式失敗。

**原因：** 個別布建套件的帳戶套件（Package_GUID）中的 Azure AD 使用者帳戶不允許將裝置加入 Azure AD。 當您使用 Windows 設定設計工具（WCD）或「設定學校電腦」應用程式來設定布建套件時，系統會自動建立 Azure AD 這些帳戶，而這些帳戶接著會用來將裝置加入 Azure AD。

#### <a name="resolution"></a>解決方案
1. 以系統管理員身分登入 [Azure 入口網站](https://portal.azure.com/)。    
2. 移至 [Azure Active Directory] [ **> 裝置] > [裝置設定**]。    
3. 將 [使用者可以將裝置加入 Azure AD]  設定為 [全部]  或 [已選取]  。

   如果您選擇 **[已選取]** ，請按一下 [**選取**]，然後按一下 [**新增成員**]，將可加入其裝置的所有使用者新增至 Azure AD。 請確定已新增布建套件的所有 Azure AD 帳戶。
 
如需如何為 Windows 設定設計工具建立布建套件的詳細資訊，請參閱[建立適用于 windows 10 的布建套件](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package)。

如需設定 School Pc 應用程式的詳細資訊，請參閱[使用安裝學校電腦應用程式](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app)。


### <a name="auto-mdm-enroll-failed"></a>自動 MDM 註冊：失敗 

當您嘗試使用群組原則自動註冊 Windows 10 裝置時，您會遇到下列問題： 
- 在工作排程器中，在**Microsoft** > **Windows** > **EnterpriseMgmt**下，**由註冊用戶端為從 AAD 工作自動註冊的排程所建立**的最後一個執行結果如下：**事件76自動 MDM 註冊：失敗（未知的 Win32 錯誤碼：0x8018002b）**       
- 在事件檢視器中，下列事件會記錄在 **應用程式和服務記錄檔/Microsoft/Windows/-企業-診斷-提供者/系統管理員** 底下：   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**原因：** 下列其中一個條件成立： 
- UPN 包含未驗證或無法路由傳送的網域，例如 local （如 joe@contoso.local）。    
- [ **MDM 使用者範圍**] 設定為 [**無**]。 

#### <a name="resolution"></a>解決方案
如果 UPN 包含未驗證或無法路由傳送的網域，請遵循下列步驟： 

1. 在 Active Directory Domain Services （AD DS）執行的伺服器上，在 **執行** 對話方塊中輸入**dsa.msc** ，然後按一下**確定**，以開啟**Active Directory 使用者和電腦**。    
2. 按一下 [網域] 底下的 [**使用者**]，然後執行下列動作：  
    - 如果只有一個受影響的使用者，請在使用者**上按一下滑鼠**右鍵，然後按一下 [內容]。 在 [**帳戶**] 索引標籤的 [**使用者登入名稱**] 底下的 [upn 尾碼] 下拉式清單中，選取有效的 UPN 尾碼，例如 Contoso.com，然後按一下 **[確定]** 。    
    - 如果有多個受影響的使用者，請選取使用者，然後在 [**動作**] 功能表中按一下 [**屬性**]。 在 [**帳戶**] 索引標籤上，選取 [ **UPN 尾碼**] 核取方塊，在下拉式清單中選取有效的 UPN 尾碼，例如 Contoso.com，然後按一下 **[確定]** 。
3. 等候下一個同步處理，或在已提升許可權的 PowerShell 提示字元中執行下列命令，以強制同步處理伺服器的差異同步處理：
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

如果 [ **MDM 使用者範圍**] 設定為 [**無**]，請遵循下列步驟： 
 
1. 登入 [Azure 入口網站](https://portal.azure.com/)，然後選取 [Azure Active Directory]  。
2. 選取 **[行動性（MDM 與 MAM）** ]，然後選取 [ **Microsoft Intune**]。    
3. 將 [ **MDM 使用者範圍**] 設定為 [**全部**]。 或者，將 [ **MDM 使用者範圍**] 設定為 [**部分**]，然後選取可以自動註冊其 Windows 10 裝置的群組。    
4. 將 [ **MAM 使用者範圍**] 設定為 [**無**]。


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>建立 Autopilot 設定檔時發生錯誤。

**原因：** 裝置名稱範本的指定命名格式不符合需求。 例如，您對序列宏使用小寫，例如% 序列%，而不是% 序列%。

#### <a name="resolution"></a>解決方案

請確定命名格式符合下列需求：

- 為您的裝置建立唯一名稱。 名稱必須是 15 個字元或更少，而且可以包含字母 (a-z、A-Z)、數字 (0-9) 與連字號 (‐)。
- 名稱不可以全部為數字。
- 名稱不能包含空格。
- 使用 %SERIAL% 巨集新增硬體特定序號。 或者，使用% RAND： < # of 數位 >% 宏來新增數位的隨機字串，字串會包含 > 位數 < 位數。 例如，MYPC-% RAND：6% 會產生 MYPC-123456 之類的名稱。

### <a name="something-went-wrong-oobeidps"></a>發生問題。 OOBEIDPS.

**原因：** 如果有 proxy、防火牆或其他網路裝置封鎖對識別提供者（IdP）的存取，就會發生此問題。

#### <a name="resolution"></a>解決方案
請確定不會封鎖 Autopilot 的網際網路服務所需的存取權。 如需詳細資訊，請參閱[Windows Autopilot 網路需求](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network)。


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>正在註冊您的裝置以進行行動管理（失敗：3，0x801C03EA）。

**原因：** 裝置具有支援2.0 版但尚未升級至2.0 版的 TPM 晶片。

#### <a name="resolution"></a>解決方案
將 TPM 晶片升級至2.0 版。

如果問題持續發生，請檢查相同的裝置是否在兩個指派的群組中，並將不同的 Autopilot 設定檔指派給每個群組。 如果它是在兩個群組中，請決定應套用至裝置的 Autopilot 設定檔，然後移除另一個設定檔的指派。

如需有關如何使用 Autopilot 在 kiosk 模式中部署 Windows 裝置的詳細資訊，請參閱[使用 Windows Autopilot 部署 kiosk](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/)。


### <a name="securing-your-hardware-failed-0x800705b4"></a>保護您的硬體（失敗：0x800705b4）。

錯誤800705b4： 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**原因：** 目標 Windows 裝置不符合下列任一需求：

- 裝置必須具有實體 TPM 2.0 晶片。 具有虛擬 Tpm （例如，Hyper-v Vm）或 TPM 1.2 晶片的裝置無法與自我部署模式搭配使用。
- 裝置必須執行下列其中一個 Windows 版本：
    - Windows 10 組建1703或更新版本。
    - 如果使用混合式 Azure AD Join，則為 Windows 10 組建1809或更新版本。


#### <a name="resolution"></a>解決方案
請確定目標裝置符合「**原因**」一節中所述的兩個需求。

如需有關如何使用 Autopilot 在 kiosk 模式中部署 Windows 裝置的詳細資訊，請參閱[使用 Windows Autopilot 部署 kiosk](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/)。


### <a name="something-went-wrong-error-code-80070774"></a>發生問題。 錯誤碼koError Code 80070774。

錯誤0x80070774：發生問題。 請確認您使用的是正確的登入資訊，而且您的組織使用這項功能。 您可以再試一次，或洽詢您的系統管理員，錯誤碼80070774。

當裝置在初始登入畫面期間超時時，通常會在混合式 Azure AD Autopilot 案例中重新開機裝置之前發生此問題。 這表示因為連線問題，所以找不到或無法成功連線到網域控制站。 或者，裝置已進入無法加入網域的狀態。

**原因：** 最常見的原因是正在使用混合式 Azure AD Join，且已在 Autopilot 設定檔中設定 [指派使用者] 功能。 使用 [指派使用者] 功能會在初始登入畫面期間，于裝置上執行 Azure AD 聯結，讓裝置處於無法加入內部部署網域的狀態。 因此，[指派使用者] 功能只應用於標準 Azure AD 聯結 Autopilot 案例。  混合式 Azure AD Join 案例中不應使用此功能。

#### <a name="resolution"></a>解決方案

1. 在[Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，選擇 [>**裝置**] > **windows** > **windows 裝置**]。
2. 選取發生問題的裝置 > 按一下最右側的省略號（...）。
3. 選取 [**取消指派使用者**]，並等候進程完成。
4. 請先確認已指派混合式 Azure AD Autopilot 設定檔，再重新嘗試 OOBE。

#### <a name="second-resolution"></a>第二個解決方案
如果問題持續發生，請在裝載離線網域的伺服器上加入 Intune 連接器，檢查事件識別碼30312是否已記錄在 ODJ 連接器服務記錄內。 事件30312如下所示：

```
Log Name:      ODJ Connector Service
Source:        ODJ Connector Service Source
Event ID:      30132
Level:         Error
Description:
{
          "Metric":{
                   "Dimensions":{
                             "RequestId":"<RequestId>",
                             "DeviceId":"<DeviceId>",
                             "DomainName":"contoso.com",
                             "ErrorCode":"5",
                             "RetryCount":"1",
                              "ErrorDescription":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation",
                              "InstanceId":"<InstanceId>",
                              "DiagnosticCode":"0x00000800",
                              "DiagnosticText":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation [Exception Message: \"DiagnosticException: 0x00000800. Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation\"] [Exception Message: \"Failed to call NetProvisionComputerAccount machineName=<ComputerName>\"]"
                   },
                   "Name":"RequestOfflineDomainJoinBlob_Failure",
                   "Value":0
          }
}
```

此問題的原因通常是因為不正確地將許可權委派給建立 Windows Autopilot 裝置的組織單位。 如需詳細資訊，請參閱[增加組織單位中的電腦帳戶限制](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit)。

1. 開啟 [Active Directory 使用者和電腦 (DSA.msc)]  。
2. 以滑鼠右鍵按一下您將用來建立混合式 Azure AD 聯結電腦的組織單位 > [委派控制]  。
3. 在 [委派控制精靈]  中，選取 [下一步]   > [新增]   > [物件類型]  。
4. 在 [物件類型]  窗格中，選取 [電腦]  核取方塊 > [確定]  。
5. 在 [選取使用者、電腦或群組]    窗格的 [輸入要選取的物件名稱]  方塊中，輸入要安裝連接器的電腦名稱。
6. 選取 **檢查名稱** 以驗證您的專案 > **確定** > **下一步**。
7. 選取 [建立自訂工作來委派]   > [下一步]  。
8. 選取 [只有在這個資料夾內的下列物件]  核取方塊，然後依序選取 [電腦物件]  、[將選取的物件建立到這個資料夾中]  和 [刪除在這個資料夾中選取的物件]  核取方塊。
9. 選取 [下一步]  。
10. 在 [權限]  下，選取 [完全控制]  核取方塊。 此動作會選取所有其他選項。
11. 選取**下一步** ** > 完成**。

## <a name="next-steps"></a>後續步驟

- [疑難排解 Intune 的裝置註冊問題](../troubleshoot-device-enrollment-in-intune.md)
- [在 Intune 論壇中發問](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [查看 Microsoft Intune 支援小組部落格](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess) \(英文\)
- [查看 Microsoft Enterprise Mobility 與安全性小組部落格](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210) \(英文\)
- [取得 Microsoft Intune 支援](../fundamentals/get-support.md)
- [尋找共同管理註冊錯誤](https://docs.microsoft.com/sccm/comanage/how-to-monitor#enrollment-errors)
