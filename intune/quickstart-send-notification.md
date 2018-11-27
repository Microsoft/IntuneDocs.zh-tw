---
title: 快速入門 - 傳送通知到不符合規範的裝置
titlesuffix: Microsoft Intune
description: 您將在本快速入門中，使用 Microsoft Intune 將電子郵件通知傳送到不符合規範的裝置。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/09/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: af24e1c56e43fe2edfc6a9241c31600b7cfe61a7
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186251"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>快速入門：傳送通知到不符合規範的裝置

您將在本快速入門中，使用 Microsoft Intune 將電子郵件通知傳送給您具有不符合規範裝置的員工成員。

根據預設，當 Intune 偵測到不符合規範的裝置時，Intune 會立即將其標記為不符合規範。 Azure Active Directory (AAD) [條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)隨後會封鎖該裝置。 當裝置不符合規範時，Intune 允許您新增不符合規範時所採取的動作，這可讓您更靈活地決定該怎麼處置不符合規範的裝置。 例如，您可以為使用者提供寬限期，在封鎖不符合規範的裝置之前將其視為相容。

當裝置不符合規範時，可以採取的其中一個動作是傳送電子郵件給這些終端使用者。 您也可以自訂電子郵件通知，再將其傳送給終端使用者。 具體來說，您可以自訂收件者、主旨與郵件內文，包括公司標誌和連絡人資訊。 Intune 也會在電子郵件通知中包含不符合規範裝置的詳細資料。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必要條件
- 當您使用裝置合規性政策禁止裝置存取公司資源時，必須設定 AAD 條件式存取。 如果您已完成[建立裝置合規性政策](quickstart-set-password-length-android.md)快速入門，則表示您正在使用 Azure Active Directory。 如需 AAD 的詳細資訊，請參閱 [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)及[透過 Intune 使用條件式存取的常見方式](conditional-access-intune-common-ways-use.md)。

## <a name="sign-in-to-intune"></a>登入 Intune

請以[全域管理員](users-add.md#types-of-administrators)或 Intune [服務管理員](users-add.md#types-of-administrators)身分登入 [Intune](https://aka.ms/intuneportal) 入口網站。 

## <a name="create-a-notification-message-template"></a>建立通知訊息範本

若要傳送電子郵件給您的使用者，請建立通知訊息範本。 裝置不符合規範時，您在範本中輸入的詳細資料會顯示在傳送給您使用者的電子郵件裡。

1. 在 Intune 中，選取 [裝置合規性] > [通知] > [建立通知]。 
2. 輸入下列資訊：

   - **名稱**：Contoso 系統管理員
   - **主旨**：裝置合規性
   - **訊息**：您的裝置目前不符合我們組織的合規性需求。
   - **電子郵件標題 – 包含公司標誌**：設定為 [啟用] 來顯示您組織的標誌。
   - **電子郵件頁尾 – 包含公司名稱**：設定為 [啟用] 來顯示您組織的名稱。
   - **電子郵件頁尾 – 包含連絡人資訊**：設定為 [啟用] 來顯示您組織的連絡人資訊。

   ![在 Intune 中符合規範的通知訊息範例](./media/quickstart-send-notification-01.png)

3. 一旦您完成新增資訊，請選擇 [建立]。 通知訊息範本便可供使用。

    > [!NOTE]
    > 您也可以編輯先前建立的通知範本。

如需設定公司名稱、公司連絡資訊和公司標誌的詳細資料，請參閱[公司資訊和隱私權聲明](company-portal-app.md#company-information-and-privacy-statement)、[支援資訊](company-portal-app.md#support-information)及[公司識別商標自訂](company-portal-app.md#company-identity-branding-customization)。 

## <a name="add-a-noncompliance-policy"></a>新增不合規性政策

當您建立裝置合規性政策時，Intune 會針對不符合規範自動建立動作。 當裝置不符合合規性政策時，Intune會將該裝置自動標記為不符合規範。 您可以自訂將裝置標記為不符合規範的時間長度。 您也可以在建立合規性政策或更新現有合規性政策時，新增另一個動作。 

下列步驟將建立 Windows 10 裝置的合規性政策。

1. 在 Intune 中，選取 [裝置合規性]。
2. 選取 [政策] > [建立政策]。
3. 輸入下列資訊：

   - [名稱]：Windows 10 合規性
   - [描述]：Windows 10 合規性政策
   - [平台]：Windows 10 及更新版本

4. 選取 [設定] > [系統安全性] 顯示與裝置安全性相關的設定。
5. 將 [需要密碼才可解除鎖定行動裝置] 設定為 [必要]。 此設定指定使用者是否需要輸入密碼，才能獲得其行動裝置的資訊存取權。 
6. 將 [密碼長度下限] 設定為 **6**。 此設定指定密碼中的數字或字元數目下限。

    ![新合規性政策的 [系統安全性] 設定](./media/quickstart-send-notification-02.png) 

7. 依序按一下 [確定]、[確定] 及 [建立] 來建立合規性政策。
8. 選取新政策的名稱：**Windows 10 合規性**。
9. 選取 [內容] > [不符合規範時採取的動作] > [新增]。
10. 在 [動作] 下拉式清單方塊中，確認已選取 [傳送電子郵件給終端使用者]。
11. 選取 [郵件範本] > [Contoso 系統管理員] > [選取]，選取您稍早在本主題中建立的郵件範本。
12. 選取 [確定] > [確定] > [儲存] 儲存您的變更。

## <a name="assign-the-policy"></a>指派原則

您可以將合規性政策指派給指定的使用者群組或所有使用者。 當 Intune 辨識出裝置不符合規範時，使用者將會收到必須更新其裝置以符合合規性政策的通知。 下列步驟可讓您指派政策。

1. 選取您稍早建立的 [Windows 10 合規性] 政策。
2. 選取 [指派]。
3. 在 [指派給] 下拉式清單方塊中，選取 [所有使用者]。 這會選取所有使用者。 只要使用者擁有不符合此合規性政策的 **Windows 10 及更新版本**裝置，就會收到通知。

    > [!NOTE]
    > 您可以在指派合規性政策時包含及排除群組。

4. 按一下 **[儲存]**。

成功建立並儲存政策後，它會顯示在 [裝置合規性 - 政策] 清單中。 請注意，該清單中的 [已指派] 設定為 [是]。

## <a name="next-steps"></a>接下來的步驟

您已在本快速入門中，使用 Intune 為員工的 Windows 10 裝置建立及指派合規性政策，以要求長度至少為六個字元的密碼。 如需建立 Windows 裝置合規性政策的詳細資訊，請參閱[在 Intune 中為 Windows 裝置新增裝置合規性政策](compliance-policy-create-windows.md)。

若要遵循此 Intune 快速入門系列，請繼續前往下一個快速入門。

> [!div class="nextstepaction"]
> [快速入門：新增並指派用戶端應用程式](quickstart-add-assign-app.md)
