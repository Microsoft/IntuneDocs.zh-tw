---
title: 在 Microsoft Intune 中使用協力廠商 CA 與 SCEP - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，您可以新增廠商或協力廠商憑證授權單位 (CA)，以使用 SCEP 通訊協定核發憑證給行動裝置。 在此概觀中，Azure Active Directory (Azure AD) 應用程式會提供 Microsoft Intune 權限來驗證憑證。 然後，在設定 SCEP 伺服器以核發憑證時，使用 AAD 應用程式的應用程式識別碼、驗證金鑰及租用戶識別碼。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ee5a39ee8a146fbc6a85a9f4438b8e14a408a735
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321621"
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

請確認您具有必要權限，才能註冊 Azure AD 應用程式。 [必要權限](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions)列出步驟。

**步驟 1：建立 Azure AD 應用程式**

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [Azure Active Directory] > [應用程式註冊] > [新增應用程式註冊]。
3. 輸入名稱並登入 URL。 針對應用程式類型，選取 [Web 應用程式/API]。
4. 選取 [建立]。

[整合應用程式與 Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)包含關於建立應用程式的一些指引，包括 URL 及名稱的祕訣。

**步驟 2：提供權限**

建立應用程式之後，請提供 Microsoft Intune API 必要權限：

1. 在您的 Azure AD 應用程式中，開啟 [設定] > [必要權限]。  
2. 選取 [新增] > 選取 API > 選取 [Microsoft Intune API] > [選取]。
3. 在 [選取權限] 中，選擇 [SCEP 挑戰驗證] > [選取]。
4. 按一下 [完成] 以儲存您的變更。

**步驟 3：取得應用程式識別碼和驗證金鑰**

接下來，取得 Azure AD 應用程式的識別碼和金鑰值。 需要下列值：

- 應用程式識別碼
- 驗證金鑰
- 租用戶識別碼

**取得應用程式識別碼和驗證金鑰**：

1. 在 Azure AD 中，選取您的新應用程式 ([應用程式註冊])。
2. 複製 [應用程式識別碼]，並將它儲存在應用程式碼中。
3. 接下來產生驗證金鑰。 在您的 Azure AD 應用程式中，開啟 [設定] > [金鑰]。
4. 在 [密碼] 中，輸入描述，然後選擇金鑰的持續時間。 [儲存] 變更。 複製並儲存顯示的值。

    > [!IMPORTANT]
    > 複製並立即儲存此金鑰，因為它不會再次顯示。 協力廠商 CA 實作需要這個金鑰值。 請務必檢閱他們想要的應用程式識別碼、驗證金鑰及租用戶識別碼設定指引。

**租用戶識別碼**是您帳戶的 @ 符號之後的網域文字。 例如，如果您的帳號是 `admin@name.onmicrosoft.com`，則您的租用戶識別碼是 **name.onmicrosoft.com**。

[取得應用程式識別碼和驗證金鑰](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key)列出取得這些值的步驟，並提供關於 Azure AD 應用程式的更多詳細資料。

### <a name="configure-and-deploy-a-scep-certificate-profile"></a>設定及部署 SCEP 憑證設定檔
以系統管理員身分，建立 SCEP 憑證設定檔以便將目標設為使用者或裝置。 然後，指派設定檔。

- [建立 SCEP 憑證設定檔](certificates-scep-configure.md#create-a-scep-certificate-profile)

- [指派憑證設定檔](certificates-scep-configure.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>移除憑證

當您取消註冊或抹除裝置時，會移除憑證。 不會撤銷憑證。

## <a name="third-party-certification-authority-partners"></a>協力廠商憑證授權單位合作夥伴
下列協力廠商憑證授權單位支援 Intune：

- [Entrust Datacard](http://www.entrustdatacard.com/resource-center/documents/documentation)

如果您是有興趣將產品與 Intune 整合的協力廠商 CA，請檢閱 API 指引：

- [Intune SCEP API GitHub 存放庫](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [協力廠商 CA 的 Intune SCEP API 指引](scep-libraries-apis.md)

## <a name="see-also"></a>另請參閱

- [設定憑證設定檔](certificates-scep-configure.md)
- [Intune SCEP API GitHub 存放庫](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [協力廠商 CA 的 Intune SCEP API 指引](scep-libraries-apis.md)
