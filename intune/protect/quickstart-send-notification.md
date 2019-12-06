---
title: 快速入門 - 傳送通知到不符合規範的裝置
titleSuffix: Microsoft Intune
description: 在本快速入門中，您會使用 Microsoft Intune 將電子郵件通知傳送到不符合規範的裝置。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6d89cfcafd5452b990509e0fa6fd431a614ee5c1
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410223"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>快速入門：傳送通知到不符合規範的裝置

在本快速入門中，您會使用 Microsoft Intune 將電子郵件通知傳送給具有不符合規範裝置的員工成員。

根據預設，當 Intune 偵測到不符合規範的裝置時，Intune 會立即將其標記為不符合規範。 Azure Active Directory (Azure AD) [條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)隨後會封鎖該裝置。 當裝置不符合規範時，Intune 允許您新增不符合規範時所採取的動作，這可讓您更靈活地決定該怎麼處置不符合規範的裝置。 例如，您可以為使用者提供寬限期，在封鎖不符合規範的裝置之前將其視為相容。

當裝置不符合規範時，其中一個可以採取的動作是傳送電子郵件給裝置使用者。 您也可以先自訂電子郵件通知再傳送它。 具體來說，您可以自訂收件者、主旨與郵件內文，包括公司標誌和連絡人資訊。 Intune 也會在電子郵件通知中包含不符合規範裝置的詳細資料。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](../fundamentals/free-trial-sign-up.md)。

## <a name="prerequisites"></a>必要條件

當您使用裝置合規性政策來禁止裝置存取公司資源時，必須設定 Azure AD 條件式存取。 如果您已完成[建立裝置合規性原則](quickstart-set-password-length-android.md)快速入門，則表示您正在使用 Azure Active Directory。 如需 Azure AD 的詳細資訊，請參閱 [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)及[透過 Intune 使用條件式存取的常見方式](../protect/conditional-access-intune-common-ways-use.md)。

## <a name="sign-in-to-intune"></a>登入 Intune

以[全域管理員](../fundamentals/users-add.md#types-of-administrators)或 Intune [服務管理員](../fundamentals/users-add.md#types-of-administrators)身分登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 如果您已建立 Intune 試用版訂閱，則用來建立訂閱的帳戶是全域管理員。

## <a name="create-a-notification-message-template"></a>建立通知訊息範本

若要傳送電子郵件給您的使用者，請建立通知訊息範本。 裝置不符合規範時，您在範本中輸入的詳細資料會顯示在傳送給您使用者的電子郵件裡。

1. 在 Intune 中，選取 [裝置]   > [合規性原則]   > [通知]   > [建立通知]  。
2. 輸入下列資訊：

   - **名稱**：Contoso 系統管理員 
   - **主旨**：*裝置合規性*
   - [訊息]  ：您的裝置目前不符合我們組織的合規性需求。 
   - [電子郵件標頭 – 包含公司標誌]  ：設定為 [已啟用]  以顯示您組織的標誌。
   - [電子郵件頁尾 – 包含公司名稱]  ：設定為 [已啟用]  以顯示您組織的名稱。
   - [電子郵件頁尾 – 包含連絡人資訊]  ：設定為 [已啟用]  以顯示您組織的連絡人資訊。

   ![在 Intune 中符合規範的通知訊息範例](./media/quickstart-send-notification/quickstart-send-notification-01.png)

3. 選取 [下一步]  並檢閱您的通知。 選取 [建立]  ，通知訊息範本便可供使用。

   > [!NOTE]
   > 您也可以編輯先前建立的通知範本。

如需設定公司名稱、公司連絡人資訊，以及公司標誌的詳細資料，請參閱下列文章：

- [公司資訊和隱私權聲明](../apps/company-portal-app.md#company-information-and-privacy-statement)
- [支援資訊](../apps/company-portal-app.md#support-information)
- [公司識別商標自訂](../apps/company-portal-app.md#company-identity-branding-customization)。

## <a name="add-a-noncompliance-policy"></a>新增不合規性政策

當您建立裝置合規性政策時，Intune 會針對不符合規範自動建立動作。 Intune 接著會在裝置無法符合您的合規性原則時，將它們標記為不符合規範。 您可以自訂將裝置標記為不符合規範的時間長度。 您也可以在建立合規性政策或更新現有合規性政策時，新增另一個動作。

下列步驟將建立 Windows 10 裝置的合規性政策。

1. 在 Intune 中，選取 [裝置]   > [合規性原則]   > [建立原則]  。

2. 輸入下列資訊：

   - **名稱**：*Windows 10 合規性*
   - **描述**：*Windows 10 合規性原則*
   - **平台**：Windows 10 及更新版本

3. 選取 [設定]   > [系統安全性]  顯示與裝置安全性相關的設定。

4. 設定下列選項：

   - 將 [需要密碼才可解除鎖定行動裝置]  設定為 [必要]  。 此設定指定使用者是否需要輸入密碼，才能獲得其行動裝置的資訊存取權。

   - 將 [密碼長度下限]  設定為 **6**。 此設定指定密碼中的數字或字元數目下限。

   ![新合規性政策的 [系統安全性] 設定](./media/quickstart-send-notification/system-security-settings-01.png)

5. 依序選取 [確定]   > [確定]   > [建立]  以建立您的合規性政策。

6. 選取 [內容]   > [不符合規範時採取的動作]   > [新增]  。

7. 在 [動作]  下拉式清單方塊中，確認已選取 [傳送電子郵件給終端使用者]  。

8. 選取 [訊息範本]  ，選取您稍早在本文中所建立的範本，然後選取 [選取]  以選取該訊息範本。

9. 選取 [新增]   > [確定]   > [儲存]  儲存您的變更。

## <a name="assign-the-policy"></a>指派原則

您可以將合規性政策指派給指定的使用者群組或所有使用者。 當 Intune 辨識出裝置不符合規範時，使用者會收到必須更新其裝置以符合合規性原則的通知。 使用下列步驟來指派原則。

1. 在 Intune 中，移至 [裝置]   > [合規性原則]  ，然後選取您先前所建立的 [Windows 10 合規性]  原則。

2. 選取 [指派]  。

3. 在 [指派給]  下拉式清單方塊中，選取 [所有使用者]  。 這會選取所有使用者。 只要使用者擁有不符合此合規性政策的 **Windows 10 及更新版本**裝置，就會收到通知。

    > [!NOTE]
    > 您可以在指派合規性政策時包含及排除群組。

4. 按一下 **[儲存]** 。

成功建立並儲存原則之後，它會顯示在 [合規性原則 - 原則]  清單中。 請注意，該清單中的 [已指派]  設定為 [是]  。

## <a name="next-steps"></a>後續步驟

您已在本快速入門中，使用 Intune 為員工的 Windows 10 裝置建立及指派合規性政策，以要求長度至少為六個字元的密碼。 如需建立 Windows 裝置合規性政策的詳細資訊，請參閱[在 Intune 中為 Windows 裝置新增裝置合規性政策](compliance-policy-create-windows.md)。

若要繼續參閱此 Intune 快速入門系列，請前往下一個快速入門。

> [!div class="nextstepaction"]
> [快速入門：新增並指派用戶端應用程式](../apps/quickstart-add-assign-app.md)
