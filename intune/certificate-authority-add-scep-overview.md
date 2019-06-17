---
title: 在 Microsoft Intune 中搭配使用協力廠商憑證授權單位 (CA) 與 SCEP - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，您可以新增廠商或協力廠商憑證授權單位 (CA)，以使用 SCEP 通訊協定核發憑證給行動裝置。 在此概觀中，Azure Active Directory (Azure AD) 應用程式會提供 Microsoft Intune 權限來驗證憑證。 然後，在設定 SCEP 伺服器以核發憑證時，使用 AAD 應用程式的應用程式識別碼、驗證金鑰及租用戶識別碼。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5124796166f27823b7a13b0f3dd239446f778850
ms.sourcegitcommit: 337b554f9becc40cdea2f5f47a4a129ac491f64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66713857"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>使用 SCEP 在 Intune 中新增協力廠商憑證授權單位

在 Microsoft Intune 中，您可以新增協力廠商憑證授權單位 (CA)。 這些 CA 可以使用簡單憑證註冊通訊協定 (SCEP) 將憑證傳遞給行動裝置。 這項功能可以在 Windows、iOS、Android 和 macOS 裝置上核發新憑證和更新憑證。

使用這項功能分成兩部分：開放原始碼 API 和 Intune 系統管理員工作。

**第 1 部分 - 使用開放原始碼 API**  
Microsoft 建立了 API，可以整合 Intune 以便驗證憑證、傳送成功或失敗通知，以及使用 SSL，特別是 SSL 通訊端 Factory，來與 Intune 通訊。

API 提供於 [Intune SCEP API 公用 GitHub 存放庫](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)，供您下載並用於解決方案。 使用此 API 搭配協力廠商 SCEP 伺服器，對 Intune 執行自訂挑戰驗證，然後才傳遞憑證給裝置。

[與 Intune SCEP 管理解決方案整合](scep-libraries-apis.md)提供使用 API、其方法和測試您建置之解決方案的更多詳細資料。

**第 2 部分 - 建立應用程式和設定檔**  
使用 Azure Active Directory (Azure AD) 應用程式，您可以委派權限，讓 Intune 處理來自裝置的 SCEP 要求。 Azure AD 應用程式包含應用程式識別碼和驗證金鑰值，可在開發人員建立的 API 解決方案內使用。 然後，系統管理員就可以使用 Intune 建立和部署 SCEP 憑證設定檔。 您也可以檢視裝置上部署狀態的報告。

本文從系統管理員的觀點，提供這項功能的概觀，包括建立 Azure AD 應用程式。

## <a name="overview"></a>概觀

下列步驟提供在 Intune 核發 SCEP 憑證的概觀：

1. 在 Intune 中，系統管理員會建立 SCEP 憑證設定檔，然後將設定檔的目標設為使用者或裝置。
2. 裝置簽入至 Intune。
3. Intune 會建立唯一的 SCEP 挑戰。 它也會新增額外的完整性檢查資訊，例如預期的主體和 SAN 應該是什麼。
4. Intune 會加密並簽署挑戰和完整性檢查資訊，然後將此資訊以 SCEP 要求傳送到裝置。
5. 裝置會根據從 Intune 推送的 SCEP 憑證設定檔，在裝置上產生憑證簽署要求 (CSR) 和公開/私密金鑰組。
6. CSR 與加密/簽署的挑戰會傳送給協力廠商 SCEP 伺服器端點。
7. SCEP 伺服器將 CSR 與挑戰傳送至 Intune。 Intune 接著驗證簽章、將內容解密，並比較 CSR 與完整性檢查資訊。
8. Intune 將回應傳送回去給 SCEP 伺服器，指出挑戰驗證是否已成功。  
9. 如果已成功驗證挑戰，SCEP 伺服器會核發憑證給裝置。

下圖顯示協力廠商 SCEP 與 Intune 整合的詳細流程：

![協力廠商憑證授權單位 SCEP 如何與 Microsoft Intune 整合](./media/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>設定協力廠商 CA 整合

### <a name="validate-third-party-certification-authority"></a>驗證協力廠商憑證授權單位

在整合協力廠商憑證授權單位與 Intune 之前，請確認您使用的 CA 支援 Intune。 [協力廠商 CA 合作夥伴](#third-party-certification-authority-partners)　(在本文中) 包含一份清單。 您也可以檢查憑證授權單位的指引，以取得詳細資訊。 CA 可能會包含實作特定的設定指示。

### <a name="authorize-communication-between-ca-and-intune"></a>授權 CA 與 Intune 之間的通訊

若要讓協力廠商 SCEP 伺服器能執行與 Intune 的自訂挑戰驗證，請在 Azure AD 中建立應用程式。 此應用程式可提供委派權限給 Intune，以便驗證 SCEP 要求。

請確認您具有必要權限，才能註冊 Azure AD 應用程式。 請參閱 Azure AD 文件中的[必要權限](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions) \(部分機器翻譯\)。

#### <a name="create-an-application-in-azure-active-directory"></a>在 Azure Active Directory 中建立應用程式  

1. 在 [Azure 入口網站](https://portal.azure.com)中，移至 [Azure Active Directory]   > [應用程式註冊]  ，然後選取 [新增註冊]  。  

2. 在 [註冊應用程式]  頁面上，指定下列詳細資料：  
   - 在 [名稱]  區段中，輸入有意義的應用程式名稱。  
   - 針對 [支援的帳戶類型]  區段，選取 [任何組織目錄中的帳戶]  。  
   - 針對 [重新導向 URI]  保留 Web 的預設值，然後為協力廠商 SCEP 伺服器指定登入 URL。  

3. 選取 [註冊]  以建立應用程式，並開啟新應用程式的 [概觀] 頁面。  

4. 在應用程式的 [概觀]  頁面上，複製 [應用程式 (用戶端) 識別碼]  值，並加以記錄以供稍後使用。 您稍後將需用到此值。  

5. 在應用程式的瀏覽窗格中，移至 [管理]  下方的 [憑證及祕密]  。 選取 [新增用戶端密碼]  按鈕。 在 [描述] 中輸入值、針對 [到期]  選取任意選項，然後選擇 [新增]  以產生用戶端密碼的「值」  。 
   > [!IMPORTANT]  
   > 離開此頁面之前，複製用戶端密碼的值並加以記錄，以便稍後搭配您的協力廠商 CA 實作使用。 此值無法再次顯示。 務必檢閱您協力廠商 CA 的指引，以了解他們想要如何設定應用程式識別碼、驗證金鑰及租用戶識別碼。  

6. 記錄您的**租用戶識別碼**。 租用戶識別碼是您帳戶中 @ 符號之後的網域文字。 例如，如果您的帳號是 *admin@name.onmicrosoft.com* ，則您的租用戶識別碼是 **name.onmicrosoft.com**。  

7. 在應用程式的瀏覽窗格中，移至 [管理]  下方的 [API 權限]  ，然後選取 [新增權限]  。  

8. 在 [要求 API 權限]  頁面上，選取 [Intune]  ，然後選取 [應用程式權限]  。 選取 **scep_challenge_provider** 的核取方塊 (SCEP 查問驗證)。  

   選取 [新增權限]  以儲存此設定。  

9. 仍然在 [API 權限]  頁面上，選取 [代表 Microsoft 授與管理員同意]  ，然後選取 [是]  。  
   
   Azure AD 中的應用程式註冊程序已完成。





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>設定及部署 SCEP 憑證設定檔
以系統管理員身分，建立 SCEP 憑證設定檔以便將目標設為使用者或裝置。 然後，指派設定檔。

- [建立 SCEP 憑證設定檔](certificates-scep-configure.md#create-a-scep-certificate-profile)

- [指派憑證設定檔](certificates-scep-configure.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>移除憑證

當您取消註冊或抹除裝置時，會移除憑證。 不會撤銷憑證。

## <a name="third-party-certification-authority-partners"></a>協力廠商憑證授權單位合作夥伴
下列協力廠商憑證授權單位支援 Intune：

- [Entrust Datacard](http://www.entrustdatacard.com/resource-center/documents/documentation)
- [EJBCA GitHub 開放原始碼版本](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)
- [GlobalSign](https://downloads.globalsign.com/acton/attachment/2674/f-6903f60b-9111-432d-b283-77823cc65500/1/-/-/-/-/globalsign-aeg-microsoft-intune-integration-guide.pdf) \(英文\)
- [IDnomic](https://www.idnomic.com/) \(英文\)
- [Sectigo](https://sectigo.com/products) \(英文\)
- [DigiCert](https://knowledge.digicert.com/tutorials/microsoft-intune.html)

如果您是有興趣將產品與 Intune 整合的協力廠商 CA，請檢閱 API 指引：

- [Intune SCEP API GitHub 存放庫](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [協力廠商 CA 的 Intune SCEP API 指引](scep-libraries-apis.md)

## <a name="see-also"></a>請參閱

- [設定憑證設定檔](certificates-scep-configure.md)
- [Intune SCEP API GitHub 存放庫](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [協力廠商 CA 的 Intune SCEP API 指引](scep-libraries-apis.md)
