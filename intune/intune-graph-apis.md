---
title: 如何在 Microsoft Graph 中使用 Azure AD 存取 Intune API
titlesuffix: Microsoft Intune
description: 描述應用程式使用 Azure AD 在 Microsoft Graph 中存取 Intune API 所需的步驟。
keywords: intune graphapi c# powershell 權限角色
author: dougeby
manager: dougeby
ms.author: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 79A67342-C06D-4D20-A447-678A6CB8D70A
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3ca5b09d415466d2ab6ce2f70a53f7fd8444d28f
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31835545"
---
# <a name="how-to-use-azure-ad-to-access-the-intune-apis-in-microsoft-graph"></a>如何在 Microsoft Graph 中使用 Azure AD 存取 Intune API

[Microsoft Graph API](https://developer.microsoft.com/graph/) 現在支援具有特定 API 和權限角色的 Microsoft Intune。  Microsoft Graph API 使用 Azure Active Directory (Azure AD) 進行驗證和存取控制。  
在 Microsoft Graph 中存取 Intune API 需要：

- 具有以下項目的應用程式識別碼：

    - 呼叫 Azure AD 和 Microsoft Graph API 的權限。
    - 與特定應用程式工作相關的權限範圍。

- 具有以下項目的使用者認證：

    - 存取與應用程式相關之 Azure AD 租用戶的權限。
    - 支援應用程式權限範圍所需的角色權限。

- 將權限授與應用程式以為其 Azure 租用戶執行應用程式工作的使用者。

這篇文章：

- 示範如何使用 Microsoft Graph API 和相關權限角色的存取權註冊應用程式。

- 描述 Intune API 權限角色。

- 提供 C# 和 PowerShell 的 Intune API 驗證範例。

- 描述如何支援多個租用戶。

如需詳細資訊，請參閱：

- [使用 OAuth 2.0 和 Azure Active Directory 授權存取 Web 應用程式](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)
- [開始使用 Azure AD 驗證](https://www.visualstudio.com/docs/integrate/get-started/auth/oauth) \(英文\)
- [整合應用程式與 Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)
- [了解 OAuth 2.0](https://oauth.net/2/) \(英文\)

## <a name="register-apps-to-use-the-microsoft-graph-api"></a>註冊應用程式以使用 Microsoft Graph API

註冊應用程式以使用 Microsoft Graph API：

1.  使用系統管理認證登入 [Azure 入口網站](https://portal.azure.com)。

    您可以視需要使用以下項目：
    - 租用戶管理帳戶。
    - 已啟用 [使用者可以註冊應用程式] 設定的租用戶使用者帳戶。

2.  從功能表中，選擇 [Azure Active Directory] &gt; [應用程式註冊]。

    <img src="./media/azure-ad-app-reg.png" width="157" height="170" alt="The App registrations menu command" />

3.  選擇 [新增應用程式註冊] 來建立新應用程式，或選擇現有應用程式。  (如果您選擇現有應用程式，請略過下一步)。

4.  在 [建立] 刀鋒視窗中，指定下列各項︰

    1.  應用程式的 [名稱] (於使用者登入時顯示)。

    2.  [應用程式類型] 和 [重新導向 URI] 值。

        這些值會因您的需求而不同。 例如，如果您使用 Azure AD [驗證程式庫](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL)，請將 [應用程式類型] 設定為 `Native`，並將 [重新導向 URI] 設定為 `urn:ietf:wg:oauth:2.0:oob`。

        <img src="media/azure-ad-app-new.png" width="209" height="140" alt="New app properties and values" />

        若要深入了解，請參閱 [Azure AD 的驗證案例](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)。

5.  從應用程式刀鋒視窗中：

    1.  記下 [應用程式識別碼] 值。

    2.  選擇 [設定] &gt; [API 存取權] &gt; [必要權限]。

    <img src="media/azure-ad-req-perm.png" width="483" height="186" alt="The Required permissions setting" />

6.  從 [必要權限] 刀鋒視窗中，選擇 [新增] &gt; [加入 API 存取權] &gt; [選取 API]。

    <img src="media/azure-ad-add-graph.png" width="436" height="140" alt="The Microsoft Graph setting" />

7.  從 [選取API] 刀鋒視窗中，選擇 [Microsoft Graph] &gt; [選取]。  [啟用存取] 刀鋒視窗即會開啟，並列出可供您應用程式使用的權限範圍。

    <img src="media/azure-ad-perm-scopes.png" width="489" height="248" alt="Intune Graph API permission scopes" />

    在相關名稱左邊勾選核取記號，選擇應用程式所需的角色。  若要深入了解特定 Intune 權限範圍，請參閱 [Intune 權限範圍](#intune-permission-scopes)。  若要深入了解其他圖形 API 權限範圍，請參閱 [Microsoft Graph 權限參考](https://developer.microsoft.com/graph/docs/concepts/permissions_reference) \(英文\)。

    為獲得最佳結果，請選擇實作應用程式所需的最少角色。

    完成後，請選擇 [選取] 和 [完成] 以儲存變更。

此時，您也可以：

- 選擇為要使用應用程式的所有租用戶帳戶授與權限，不需提供認證。  

    若要這樣做，請選擇 [授與權限] 並接受確認提示。

    當您第一次執行應用程式時，系統會提示您授與應用程式執行所選角色的權限。

    <img src="media/azure-ad-grant-perm.png" width="351" height="162" alt="The Grant permissions button" />

- 讓您租用戶以外的使用者能夠使用應用程式  (通常只有支援多個租用戶/組織的合作夥伴才需要這樣做)。  

    操作方法：

  1. 從應用程式刀鋒視窗中選擇 [資訊清單]，這樣可開啟 [編輯資訊清單] 刀鋒視窗。

     <img src="media/azure-ad-edit-mft.png" width="295" height="114" alt="The Edit manifest blade" />

  2. 將 `availableToOtherTenants` 的值變更為 `true`。

  3. 儲存您的變更。

## <a name="intune-permission-scopes"></a>Intune 權限範圍

Azure AD 和 Microsoft Graph 使用權限範圍來控制公司資源的存取權。  

權限範圍 (也稱為 _OAuth 範圍_) 可控制特定 Intune 實體和其內容的存取權。 本節摘要說明 Intune API 功能的權限範圍。

若要深入了解：
- [Azure AD 驗證](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication)
- [應用程式權限範圍](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-scopes)

當您將權限授與 Microsoft Graph 時，可以指定下列範圍來控制 Intune 功能的存取權：下表摘要說明 Intune API 權限範圍。  第一欄顯示了出現在 Azure 入口網站中的功能名稱，第二欄提供權限範圍名稱。

_啟用存取_設定 | 領域名稱
:--|:--
__在 Microsoft Intune 裝置上執行受使用者影響的遠端動作__ | [DeviceManagementManagedDevices.PrivilegedOperations.All](#mgd-po)
__讀取和寫入 Microsoft Intune 裝置__ | [DeviceManagementManagedDevices.ReadWrite.All](#mgd-rw)
__讀取 Microsoft Intune 裝置__ | [DeviceManagementManagedDevices.Read.All](#mgd-ro)
__讀取和寫入 Microsoft Intune RBAC 設定__ | [DeviceManagementRBAC.ReadWrite.All](#rac-rw)
__讀取 Microsoft Intune RBAC 設定__ | [DeviceManagementRBAC.Read.All](#rac=ro)
__讀取和寫入 Microsoft Intune 應用程式__ | [DeviceManagementApps.ReadWrite.All](#app-rw)
__讀取 Microsoft Intune 應用程式__ | [DeviceManagementApps.Read.All](#app-ro)
__讀取和寫入 Microsoft Intune 裝置設定和原則__ | [DeviceManagementConfiguration.ReadWrite.All](#cfg-rw)
__讀取 Microsoft Intune 裝置設定和原則__ | [DeviceManagementConfiguration.Read.All](#cfg-ro)
__讀取和寫入 Microsoft Intune 設定__ | [DeviceManagementServiceConfig.ReadWrite.All](#svc-rw)
__讀取 Microsoft Intune 設定__ | [DeviceManagementServiceConfig.Read.All](#svc-ra)

表格依照 Azure 入口網站中顯示的順序列出設定。 以下幾節依字母順序說明範圍。

此時，所有 Intune 權限範圍都需要系統管理員存取權。  這表示執行存取 Intune API 資源的應用程式或指令碼時，需要對應的認證。

### <a name="app-ro"></a>DeviceManagementApps.Read.All

- **啟用存取**設定：__讀取 Microsoft Intune 應用程式__

- 允許下列實體內容和狀態的讀取存取權：
    - 行動裝置應用程式
    - 行動裝置應用程式類別
    - 應用程式保護原則
    - 應用程式設定

### <a name="app-rw"></a>DeviceManagementApps.ReadWrite.All

- **啟用存取**設定：__讀取和寫入 Microsoft Intune 應用程式__

- 可允許與 __DeviceManagementApps.Read.All__ 相同的作業

- 也可允許變更下列實體：

    - 行動裝置應用程式
    - 行動裝置應用程式類別
    - 應用程式保護原則
    - 應用程式設定

### <a name="cfg-ro"></a>DeviceManagementConfiguration.Read.All

- **啟用存取**設定：__讀取 Microsoft Intune 裝置設定和原則__

- 允許下列實體內容和狀態的讀取存取權：
    - 裝置設定
    - 裝置合規性原則
    - 通知訊息

### <a name="cfg-ra"></a>DeviceManagementConfiguration.ReadWrite.All

- **啟用存取**設定：__讀取和寫入 Microsoft Intune 裝置設定和原則__

- 可允許與 __DeviceManagementConfiguration.Read.All__ 相同的作業

- 應用程式也可建立、指派、刪除及變更下列實體：
    - 裝置設定
    - 裝置合規性原則
    - 通知訊息

### <a name="mgd-po"></a>DeviceManagementManagedDevices.PrivilegedOperations.All

- **啟用存取**設定：__在 Microsoft Intune 裝置上執行受使用者影響的遠端動作__

- 允許在受管理的裝置上執行下列遠端動作：
    - 淘汰
    - 抹除
    - 重設/復原密碼
    - 遠端鎖定
    - 啟用/停用遺失模式
    - 清理電腦
    - 重新開機
    - 從共用的裝置刪除使用者

### <a name="mgd-ro"></a>DeviceManagementManagedDevices.Read.All

- **啟用存取**設定：__讀取 Microsoft Intune 裝置__

- 允許下列實體內容和狀態的讀取存取權：
    - 受管理的裝置
    - 裝置類別
    - 偵測到的應用程式
    - 遠端動作
    - 惡意程式碼資訊

### <a name="mgd-rw"></a>DeviceManagementManagedDevices.ReadWrite.All

- **啟用存取**設定：__讀取和寫入 Microsoft Intune 裝置__

- 可允許與 __DeviceManagementManagedDevices.Read.All__ 相同的作業

- 應用程式也可建立、刪除及變更下列實體：
    - 受管理的裝置
    - 裝置類別

- 此外，也允許下列遠端動作：
    - 尋找裝置
    - 略過啟用鎖定
    - 要求遠端協助

### <a name="rac-ro"></a>DeviceManagementRBAC.Read.All

- **啟用存取**設定：__讀取 Microsoft Intune RBAC 設定__

- 允許下列實體內容和狀態的讀取存取權：
    - 角色指派
    - 角色定義
    - 資源作業

### <a name="rac-rw"></a>DeviceManagementRBAC.ReadWrite.All

- **啟用存取**設定：__讀取和寫入 Microsoft Intune RBAC 設定__

- 可允許與 __DeviceManagementRBAC.Read.All__ 相同的作業

- 應用程式也可建立、指派、刪除及變更下列實體：
    - 角色指派
    - 角色定義

### <a name="svc-ro"></a>DeviceManagementServiceConfig.Read.All

- **啟用存取**設定：__讀取 Microsoft Intune 設定__

- 允許下列實體內容和狀態的讀取存取權：
    - 註冊裝置
    - Apple 推播通知憑證
    - Apple 裝置註冊方案
    - Apple 大量採購方案
    - Exchange Connector
    - 條款及條件
    - 電信費用管理
    - 雲端 PKI
    - 商標
    - Mobile Threat Defense

### <a name="svc-rw"></a>DeviceManagementServiceConfig.ReadWrite.All

- **啟用存取**設定：__讀取和寫入 Microsoft Intune 設定__

- 可允許與 DeviceManagementServiceConfig.Read.All_ 相同的作業

- 應用程式也可以設定下列 Intune 功能：
    - 註冊裝置
    - Apple 推播通知憑證
    - Apple 裝置註冊方案
    - Apple 大量採購方案
    - Exchange Connector
    - 條款及條件
    - 電信費用管理
    - 雲端 PKI
    - 商標
    - Mobile Threat Defense

## <a name="azure-ad-authentication-examples"></a>Azure AD 驗證範例

本節說明如何將 Azure AD 整合到您的 C# 和 PowerShell 專案中。

在每個範例中，您都必須指定至少具有 `DeviceManagementManagedDevices.Read.All` 權限範圍的應用程式識別碼 (稍早曾討論過)。

測試任一範例時，您可能會收到類似以下這樣的 HTTP 狀態 403 (禁止) 錯誤：

``` javascript
{
  "error": {
    "code": "Forbidden",
    "message": "Application is not authorized to perform this operation - Operation ID " +
       "(for customer support): 00000000-0000-0000-0000-000000000000 - " +
       "Activity ID: cc7fa3b3-bb25-420b-bfb2-1498e598ba43 - " +
       "Url: https://example.manage.microsoft.com/" +
       "Service/Resource/RESTendpoint?" +
       "api-version=2017-03-06 - CustomApiErrorPhrase: ",
    "innerError": {
      "request-id": "00000000-0000-0000-0000-000000000000",
      "date": "1980-01-0112:00:00"
    }
  }
}
```

如果發生這種情況，請確認：

- 您已將應用程式識別碼更新為已獲授權可使用 Microsoft Graph API 和 `DeviceManagementManagedDevices.Read.All` 權限範圍。

- 您的租用戶認證支援系統管理功能。

- 您的程式碼與所顯示的範例相似。


### <a name="authenticate-azure-ad-in-c"></a>在 C\# 中驗證 Azure AD

這個範例示範如何使用 C# 來擷取與您的 Intune 帳戶相關聯的裝置清單。

1.  啟動 Visual Studio，然後建立新的 Visual C# 主控台應用程式 (.NET Framework) 專案。

2.  輸入專案的名稱，然後依需要提供其他詳細資料。

    <img src="media/aad-auth-cpp-new-console.png" width="624" height="433" alt="Creating a C# console app project in Visual Studio"  />

3.  使用 [方案總管] 將 Microsoft ADAL NuGet 套件加入至專案。

    1.  在 [方案總管] 上按一下滑鼠右鍵。
    2.  選擇 [管理 NuGet 套件...] &gt; [瀏覽]。
    3.  然後依序選擇 `Microsoft.IdentityModel.Clients.ActiveDirectory` 和 [安裝]。

    <img src="media/aad-auth-cpp-install-package.png" width="624" height="458" alt="Selecting the Azure AD identity model module" />

4.  將下列陳述式加入至 **Program.cs** 頂端：

    ``` csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;</p>
    using System.Net.Http;
    ```

5.  加入建立授權標頭的方法：

    ``` csharp
    private static async Task<string> GetAuthorizationHeader()
    {
        string applicationId = "<Your Application ID>";
        string authority = "https://login.microsoftonline.com/common/";
        Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
        AuthenticationContext context = new AuthenticationContext(authority);
        AuthenticationResult result = await context.AcquireTokenAsync(
            "https://graph.microsoft.com",
            applicationId, redirectUri,
            new PlatformParameters(PromptBehavior.Auto));
        return result.CreateAuthorizationHeader();
    ```

    請記得變更 `application_ID` 的值以符合在至少 `DeviceManagementManagedDevices.Read.All` 權限範圍授與的內容，如前所述。

6. 加入擷取裝置清單的方法：

    ``` csharp
    private static async Task<string> GetMyManagedDevices()
    {
        string authHeader = await GetAuthorizationHeader();
        HttpClient graphClient = new HttpClient();
        graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
        return await graphClient.GetStringAsync(
            "https://graph.microsoft.com/beta/me/managedDevices");
    }
    ```

7.  更新 **Main** 以呼叫 **GetMyManagedDevices**：

    ``` csharp
    string devices = GetMyManagedDevices().GetAwaiter().GetResult();
    Console.WriteLine(devices);
    ```

8.  編譯並執行您的程式。  

當您第一次執行程式時，應該會收到兩個提示。  第一個提示會要求您提供認證，第二個提示會授與 `managedDevices` 要求的權限。  

如需參考，以下是已完成的程式：

``` csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System;
using System.Net.Http;
using System.Threading.Tasks;

namespace IntuneGraphExample
{
    class Program
    {
        static void Main(string[] args)
        {
            string devices = GetMyManagedDevices().GetAwaiter().GetResult();
            Console.WriteLine(devices);
        }

        private static async Task<string> GetAuthorizationHeader()
        {
            string applicationId = "<Your Application ID>";
            string authority = "https://login.microsoftonline.com/common/";
            Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
            AuthenticationContext context = new AuthenticationContext(authority);
            AuthenticationResult result = await context.AcquireTokenAsync("https://graph.microsoft.com", applicationId, redirectUri, new PlatformParameters(PromptBehavior.Auto));
            return result.CreateAuthorizationHeader();
        }

        private static async Task<string> GetMyManagedDevices()
        {
            string authHeader = await GetAuthorizationHeader();
            HttpClient graphClient = new HttpClient();
            graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
            return await graphClient.GetStringAsync("https://graph.microsoft.com/beta/me/managedDevices");
        }
    }
}
```

### <a name="authenticate-azure-ad-powershell"></a>驗證 Azure AD (PowerShell)

下列 PowerShell 指令碼使用 AzureAD PowerShell 模組來進行驗證。  若要深入了解，請參閱 [Azure Active Directory PowerShell 第 2 版](https://docs.microsoft.com/powershell/azure/install-adv2?view=azureadps-2.0) \(英文\) 和 [Intune PowerShell 範例](https://github.com/microsoftgraph/powershell-intune-samples) \(英文\)。

在此範例中，更新 `$clientID` 的值以符合有效的應用程式識別碼。

``` powershell
function Get-AuthToken {
    [cmdletbinding()]
    param
    (
        [Parameter(Mandatory = $true)]
        $User
    )

    $userUpn = New-Object "System.Net.Mail.MailAddress" -ArgumentList $User
    $tenant = $userUpn.Host

    Write-Host "Checking for AzureAD module..."

    $AadModule = Get-Module -Name "AzureAD" -ListAvailable
    if ($AadModule -eq $null) {
        Write-Host "AzureAD PowerShell module not found, looking for AzureADPreview"
        $AadModule = Get-Module -Name "AzureADPreview" -ListAvailable
    }

    if ($AadModule -eq $null) {
        write-host
        write-host "AzureAD Powershell module not installed..." -f Red
        write-host "Install by running 'Install-Module AzureAD' or 'Install-Module AzureADPreview' from an elevated PowerShell prompt" -f Yellow
        write-host "Script can't continue..." -f Red
        write-host
        exit
    }

    # Getting path to ActiveDirectory Assemblies
    # If the module count is greater than 1 find the latest version

    if ($AadModule.count -gt 1) {
        $Latest_Version = ($AadModule | select version | Sort-Object)[-1]
        $aadModule = $AadModule | ? { $_.version -eq $Latest_Version.version }
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    else {
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    [System.Reflection.Assembly]::LoadFrom($adal) | Out-Null
    [System.Reflection.Assembly]::LoadFrom($adalforms) | Out-Null

    $clientId = "<Your Application ID>"
    $redirectUri = "urn:ietf:wg:oauth:2.0:oob"
    $resourceAppIdURI = "https://graph.microsoft.com"
    $authority = "https://login.microsoftonline.com/$Tenant"

    try {
        $authContext = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext" -ArgumentList $authority
        # https://msdn.microsoft.com/library/azure/microsoft.identitymodel.clients.activedirectory.promptbehavior.aspx
        # Change the prompt behaviour to force credentials each time: Auto, Always, Never, RefreshSession
        $platformParameters = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.PlatformParameters" -ArgumentList "Auto"
        $userId = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.UserIdentifier" -ArgumentList ($User, "OptionalDisplayableId")
        $authResult = $authContext.AcquireTokenAsync($resourceAppIdURI, $clientId, $redirectUri, $platformParameters, $userId).Result
        # If the accesstoken is valid then create the authentication header
        if ($authResult.AccessToken) {
            # Creating header for Authorization token
            $authHeader = @{
                'Content-Type' = 'application/json'
                'Authorization' = "Bearer " + $authResult.AccessToken
                'ExpiresOn' = $authResult.ExpiresOn
            }
            return $authHeader
        }
        else {
            Write-Host
            Write-Host "Authorization Access Token is null, please re-run authentication..." -ForegroundColor Red
            Write-Host
            break
        }
    }
    catch {
        write-host $_.Exception.Message -f Red
        write-host $_.Exception.ItemName -f Red
        write-host
        break
    }   
}

$authToken = Get-AuthToken -User "<Your AAD Username>"

try {
    $uri = "https://graph.microsoft.com/beta/me/managedDevices"
    Write-Verbose $uri
    (Invoke-RestMethod -Uri $uri –Headers $authToken –Method Get).Value
}
catch {
    $ex = $_.Exception
    $errorResponse = $ex.Response.GetResponseStream()
    $reader = New-Object System.IO.StreamReader($errorResponse)
    $reader.BaseStream.Position = 0
    $reader.DiscardBufferedData()
    $responseBody = $reader.ReadToEnd();
    Write-Host "Response content:`n$responseBody" -f Red
    Write-Error "Request to $Uri failed with HTTP Status $($ex.Response.StatusCode) $($ex.Response.StatusDescription)"
    write-host
    break
}
```

## <a name="support-multiple-tenants-and-partners"></a>支援多個租用戶和合作夥伴

如果您的組織支援的組織具有自己的 Azure AD 租用戶，您可能會想要允許用戶端以其各自的租用戶使用應用程式。

操作方法：

1.  確認用戶端帳戶存在於目標 Azure AD 租用戶中。

2.  確認您的租用戶帳戶允許使用者註冊應用程式 (請參閱**使用者設定**)。

3.  建立每個租用戶之間的關聯性。  

    若要這樣做，請：

    a. 使用 [Microsoft 合作夥伴中心](https://partnercenter.microsoft.com/) 來定義與您的用戶端及其電子郵件地址之間的關聯性。

    b. 邀請使用者成為您租用戶的來賓。

若要邀請使用者成為您租用戶的來賓：

1.  從 [快速工作] 面板中選擇 [新增來賓使用者]。

    <img src="media/azure-ad-add-guest.png" width="448" height="138" alt="Use Quick Tasks to add a guest user" />

2.  輸入用戶端的電子郵件地址及 (選擇性) 新增用來邀請的個人化訊息。

    <img src="media/azure-ad-guest-invite.png" width="203" height="106" alt="Inviting an external user as a guest" />

3.  選擇 [邀請]。

這樣便會將邀請傳送給使用者。

   <img src="media/aad-multiple-tenant-invitation.png" width="624" height="523" alt="A sample guest invitation" />

   使用者需要選擇 [開始] 連結接受您的邀請。

建立關聯性 (或接受您的邀請) 之後，將使用者帳戶加入 [目錄角色]。

請記住要視需要將使用者加入其他角色。 比方說，若要允許使用者管理 Intune 設定，它們必須是**全域管理員**或 **Intune 服務管理員**。

此外：

- 您可以使用 https://portal.office.com，將 Intune 授權指派給您的使用者帳戶。

- 更新應用程式碼以驗證用戶端的 Azure AD 租用戶網域，而不只是您自己的網域。

    例如，假設您的租用戶網域為 `contosopartner.onmicrosoft.com`，用戶端的租用戶網域是 `northwind.onmicrosoft.com`，您會更新程式碼來驗證您用戶端的租用戶。

    若要根據先前的範例在 C# 應用程式中這樣做，您會變更 `authority` 變數的值：

    ``` csharp
    string authority = "https://login.microsoftonline.com/common/";
    ```

    至

    ``` csharp
    string authority = "https://login.microsoftonline.com/northwind.onmicrosoft.com/";
    ```
