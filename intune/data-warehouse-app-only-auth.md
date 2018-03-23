---
title: 僅限 Intune 資料倉儲應用程式的驗證
titleSuffix: Microsoft Intune
description: 本主題描述僅限資料倉儲應用程式的驗證。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d7166563-6bb5-4624-b8c8-6b300a997c3a
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e926d3d9e9dfbf6025fb36fd54e64f28b662fc89
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2018
---
# <a name="intune-data-warehouse-application-only-authentication"></a>僅限 Intune 資料倉儲應用程式的驗證

您可以使用 Azure Active Directory (Azure AD) 來設定應用程式並向 Intune 資料倉儲驗證。 針對應用程式不應該有使用者認證存取權的網站、應用程式和背景處理序，此流程十分有用。 您可以使用以下步驟，以 OAuth 2.0 透過 Azure AD 來驗證應用程式。

## <a name="authorization"></a>授權

Azure Active Directory (Azure AD) 採用 OAuth 2.0，可讓您授予 Azure AD 租用戶中之 Web 應用程式和 Web API 的存取權。 本指南說明如何使用 C# 來驗證應用程式。 OAuth 2.0 規格的第 4.1 節描述了 OAuth 2.0 授權碼流程。 如需詳細資訊，請參閱[使用 OAuth 2.0 和 Azure Active Directory 授權存取 Web 應用程式](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)。


## <a name="azure-keyvault"></a>Azure KeyVault

以下流程使用私用方法來處理及轉換應用程式金鑰。 此私用方法已命名為 SecureString。 或者，您可以使用 Azure KeyVault 來儲存應用程式金鑰。 如需詳細資訊，請參閱 [Key Vault](https://azure.microsoft.com/services/key-vault/)。

## <a name="create-a-web-app"></a>建立 Web 應用程式

在本節中，您將提供要指向 Intune 的 Web 應用程式詳細資料。 Web 應用程式是主從式應用程式。 伺服器提供了 Web 應用程式，其中包括 UI、內容和功能。 這種類型的應用程式在網站上會分開維護。 您使用 Intune 來授與 Web 應用程式對 Intune 的存取權。 資料流是由 Web 應用程式起始的。 

1.  登入 [Azure 入口網站](https://portal.azure.com)。
2.  使用 Azure 入口網站頂端附近的 [搜尋資源、服務及文件] 欄位，搜尋 **Azure Active Directory**。
3.  在下拉式功能表中，選取 [服務] 下的 [Azure Active Directory]。
4.  選取 [應用程式註冊]。
5.  按一下 [新增應用程式註冊] 以顯示 [建立] 刀鋒視窗。
6.  在 [建立] 刀鋒視窗中，新增您的應用程式詳細資訊：

    - 應用程式名稱，例如 *Intune App-Only Auth*。
    - [應用程式類型]。 選取 [Web 應用程式/API] 以新增代表 Web 應用程式、Web API 或兩者的應用程式。
    - 應用程式的 [登入 URL]。 這是使用者在驗證流程期間會自動前往的位置。 系統會要求使用者證明其所宣稱的身分。 如需詳細資訊，請參閱[什麼是搭配 Azure Active Directory 的應用程式存取和單一登入？](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)

7.  按一下 [建立] 刀鋒視窗底端的 [建立]。

    >[!NOTE] 
    > 複製 [註冊的應用程式] 中的 [應用程式識別碼] 以供稍後使用。

## <a name="create-a-key"></a>建立金鑰

在本節中，Azure AD 會為您的應用程式產生金鑰值。

1.  在 [應用程式註冊] 刀鋒視窗上，選取新建立的應用程式，以顯示應用程式刀鋒視窗。
2.  選取刀鋒視窗頂端附近的 [設定]，以顯示 [設定] 刀鋒視窗。
3.  選取 [設定] 刀鋒視窗上的 [金鑰]。
4.  新增金鑰 [描述]、[到期日] 持續時間，及金鑰的 [值]。
5.  按一下 [儲存] 來儲存及更新應用程式的金鑰。
6.  您必須複製產生的金鑰值 (Base64 編碼)。

    >[!NOTE] 
    > 金鑰值會在您離開 [金鑰] 刀鋒視窗之後消失。 您之後便無法從此刀鋒視窗擷取金鑰。 複製金鑰以供稍後使用。

## <a name="grant-application-permissions"></a>授與應用程式權限

在本節中，您將授與應用程式權限。

1.  在 [設定] 刀鋒視窗上，選取 [必要權限]。
2.  按一下 [加入] 。
3.  選取 [新增 API] 以顯示 [選取 API] 刀鋒視窗。
4.  選取 [Microsoft Intune API (MicrosoftIntuneAPI)]，然後按一下 [選取 API] 刀鋒視窗中的 [選取]。 選取了 [選取權限] 步驟，並顯示 [啟用存取] 刀鋒視窗。
5.  選擇 [應用程式權限] 區段中的 [從 Microsoft Intune 取得資料倉儲資訊] 選項。
6.  按一下 [啟用存取] 刀鋒視窗中的 [選取]。
7.  按一下 [新增 API 存取] 刀鋒視窗中的 [完成]。
8.  按一下 [必要權限] 刀鋒視窗中的 [授與權限]。當系統提示更新此應用程式所擁有的任何現有權限時，請按一下 [是]。

## <a name="generate-token"></a>產生權杖

使用 Visual Studio，建立支援 .NET Framework 並使用 C# 作為程式設計語言的主控台應用程式 (.NET Framework) 專案。

1.  選取 [檔案] > [新增] > [專案] 以顯示 [新增專案] 對話方塊。
2.  選取左側的 [Visual C#] 以顯示所有 .NET Framework 專案。
3.  選取 [主控台應用程式 (.NET Framework)]、新增應用程式名稱，然後按一下 [確定] 以建立應用程式。
4.  在 [方案總管] 中，選取 [Program.cs] 以顯示程式碼。
5.  在快顯功能表中，選取 [新增] > [新增項目]。 [新增項目] 對話方塊隨即顯示。
6.  選取左側 [Visual C#] 之下的 [程式碼]。
7.  選取 [類別]、將類別的名稱變更為 *IntuneDataWarehouseClass.cs*，然後按一下 [新增]。
8.  在 <code>Main</code> 方法中新增下列程式碼：

    ``` csharp
         var applicationId = ConfigurationManager.AppSettings["appId"].ToString();
         SecureString applicationSecret = ConvertToSecureStr(ConfigurationManager.AppSettings["appKey"].ToString()); // Load as SecureString from configuration file or secret store (i.e. Azure KeyVault)
         var tenantDomain = ConfigurationManager.AppSettings["tenantDomain"].ToString();
         var adalContext = new AuthenticationContext($"https://login.windows.net/" + tenantDomain + "/oauth2/token");
    
         AuthenticationResult authResult = adalContext.AcquireTokenAsync(
             resource: "https://api.manage.microsoft.com/",
             clientCredential: new ClientCredential(
                 applicationId,
                 new SecureClientSecret(applicationSecret))).Result;
    ``` 

9. 在程式碼檔案的頂端新增下列程式碼，以新增其他命名空間：

    ``` csharp
     using System.Security;
     using Microsoft.IdentityModel.Clients.ActiveDirectory;
     using System.Configuration;
    ``` 

10. 在 <code>Main</code> 方法後，新增下列私用方法以處理及轉換應用程式金鑰：

    ``` csharp
    private static SecureString ConvertToSecureStr(string appkey)
    {
        if (appkey == null)
            throw new ArgumentNullException("AppKey must not be null.");
    
        var secureAppKey = new SecureString();
    
        foreach (char c in appkey)
            secureAppKey.AppendChar(c);
    
        secureAppKey.MakeReadOnly();
        return secureAppKey;
    }
    ```

11. 在 [方案總管] 中，以滑鼠右鍵按一下 [參考]，然後選取 [管理 NuGet 套件]。
12. 搜尋 *Microsoft.IdentityModel.Clients.ActiveDirectory*，並安裝相關的 Microsoft NuGet 套件。
13. 在 [方案總管] 中，選取並開啟 *App.config* 檔案。
14. 新增 <code>appSettings</code> 區段，使 xml 看起來如下：

    ``` xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup> 
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <appSettings>
          <add key="appId" value="App ID created from 'Create a Web App' procedure"/>
          <add key="appKey" value="Key created from 'Create a key' procedure" />
          <add key="tenantDomain" value="contoso.onmicrosoft.com"/>
        </appSettings>
    </configuration>
    ``` 

15. 更新 <code>appId</code>、<code>appKey</code> 和 <code>tenantDomain</code> 的值，使之符合您唯一的應用程式相關值。
16. 建置應用程式。

    >[!NOTE] 
    > 若要查看額外的實作程式碼，請參閱 [Intune 資料倉儲程式碼範例](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/CSharp )。

## <a name="next-steps"></a>後續步驟
若要深入了解 Azure Key Vault，請檢閱[何謂 Azure Key Vault？](https://docs.microsoft.com/azure/key-vault/key-vault-whatis)。

