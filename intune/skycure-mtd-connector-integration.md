---
title: 設定 Symantec 與 Microsoft Intune 整合
titleSuffix: Microsoft Intune
description: 如何使用 Microsoft Intune 設定 Symantec Endpoint Protection Mobile 解決方案，來控制行動裝置對公司資源的存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/21/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 359448d9-2384-42ac-a21c-a25148c20a7b
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9b44164ff31be89e01eb895a8b889e07bb3f704f
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569697"
---
# <a name="set-up-symantec-endpoint-protection-mobile-integration-with-intune"></a>設定 Symantec Endpoint Protection Mobile 與 Intune 整合

完成下列步驟以將 Symantec Endpoint Protection Mobile (SEP Mobile) 解決方案與 Intune 整合。 您必須將 SEP Mobile 應用程式新增至 Azure AD，才能使用單一登入功能。

## <a name="before-you-begin"></a>開始之前

### <a name="azure-ad-account-used-to-integrate-intune-and-sep-mobile"></a>用來整合 Intune 與 SEP Mobile 的 Azure AD 帳戶

-   在開始 SEP Mobile 基本設定程序之前，請確定您已經在 [Symantec Endpoint Protection Mobile 管理主控台](https://aad.skycure.com)中正確設定 Azure AD 帳戶。
- Azure AD 帳戶必須是全域系統管理員帳戶才能執行整合。
### <a name="network-setup"></a>網路設定

您可以參閱 Symantec 文章[設定您的網路設定](https://portal.skycure.com/articles/Documentation/Setting-up-your-network-configuration-26-8-2016)，確定您的網路是否已正確設定，以便與 SEP Mobile 設定整合。

### <a name="full-integration-vs-read-only"></a>完整整合與唯讀

SEP Mobile 支援兩種與 Intune 整合的模式：

-   **唯讀整合 (基本設定)：** 僅清查來自 Azure Active Directory 的裝置，並將它們填入 Symantec Endpoint Protection Mobile 管理主控台。
<br>
    -   如果未在 Symantec Endpoint Protection Mobile 管理主控台中選取 [向 Intune 報告裝置的健全狀況和風險] 和 [也向 Intune 報告安全性事件] 方塊，則整合將會是唯讀，並因此一律不會變更 Intune 中的裝置狀態 (符合規範或不符合規範)。
<br></br>
-   **完整整合：** 允許 SEP Mobile 向 Intune 報告裝置的風險和安全性事件詳細資料，這會在兩個雲端服務之間建立雙向通訊。

### <a name="how-are-the-sep-mobile-apps-used-with-azure-ad-and-intune"></a>SEP Mobile 應用程式如何與 Azure AD 和 Intune 搭配使用？

-   **iOS 應用程式：** 允許終端使用者使用 iOS 應用程式登入 Azure AD。

-   **Android 應用程式：** 允許終端使用者使用 Android 應用程式登入 Azure AD。

-   **管理應用程式：** 這是 SEP Mobile Azure AD 多租用戶應用程式，可啟用與 Intune 的服務對服務通訊。

## <a name="to-set-up-the-read-only-integration-between-intune-and-sep-mobile"></a>設定 Intune 和 SEP Mobile 之間的唯讀整合

> [!IMPORTANT]
> SEP Mobile 系統管理員認證必須是屬於 Azure Active Directory 中有效使用者的電子郵件帳戶，否則登入將會失敗。 SEP Mobile 會使用 Azure Active Directory，透過單一登入 (SSO) 來驗證它的系統管理員。

1.  移至 [Symantec Endpoint Protection Mobile 管理主控台](https://aad.skycure.com)。

2.  輸入您的 **SEP Mobile 系統管理員認證**，然後選擇 [繼續]。

3.  移至 [設定]，在 [Intune 整合] 底下選擇 [基本設定]。

4.  在 [iOS 應用程式] 旁，選擇 [新增至 Active Directory]。

    ![Symantec Endpoint Protection Mobile 管理主控台影像](./media/symantec-portal-basic-add.png)

5.  當登入頁面開啟時，輸入您的 Intune 認證，然後選擇 [接受]。

    ![iOS 應用程式 Intune 登入提示的影像](./media/symantec-portal-basic-accept.png)

6.  應用程式新增至 Azure AD 之後，您會看到已成功新增應用程式的指示。

    ![iOS 應用程式完成畫面的影像](./media/symantec-portal-basic-added.png)

7. 針對 [SEP Mobile Android] 和 [管理] 應用程式重複這些步驟。

### <a name="add-an-azure-ad-security-group-into-sep-mobile"></a>將 Azure AD 安全性群組新增至 SEP Mobile

您需要新增包含所有執行 SEP Mobile 之裝置的 Azure AD 安全性群組。

-  請輸入並選取所有執行 SEP Mobile 之裝置的安全性群組，然後儲存變更。

    ![顯示 SEP Mobile 應用程式使用者群組的影像](./media/symantec-portal-basic-groups.png)   

SEP Mobile 會將執行其 Mobile Threat Defense 服務的裝置，與 Azure AD 安全性群組同步。

![SEP Mobile 管理主控台上的安全性群組設定影像](./media/symantec-portal-basic-status.png)

## <a name="to-set-up-the-full-integration-between-intune-and-sep-mobile"></a>設定 Intune 和 SEP Mobile 之間的完整整合

### <a name="retrieve-the-directory-id-in-azure-ad"></a>擷取 Azure AD 中的目錄識別碼

1. 登入 [Azure 入口網站](https://portal.azure.com)。

2. 在搜尋方塊中輸入「Azure Directory」，然後選取 [Azure Active Directory]。

3. 選擇 [內容]。

4. 在 [目錄識別碼] 旁邊，選擇複製圖示，然後將它貼到安全的位置。 您在稍後的步驟將需要此識別碼。

    ![在 Azure 入口網站中顯示目錄識別碼的影像](./media/symantec-azure-portal-directory-ID.png)

### <a name="optional-create-a-dedicated-security-group-for-devices-that-need-to-run-the-sep-mobile-apps"></a>(選擇性) 針對需要執行 SEP Mobile 應用程式的裝置建立專用的安全性群組
1. 在 [Azure 入口網站中](https://portal.azure.com)，選擇 [管理] 底下的 [使用者和群組]，然後選擇 [所有群組]。

2. 選擇 [新增] 按鈕。 輸入群組**名稱**。 在 [成員資格類型] 底下，選擇 [已指派]。

3. 在 [成員] 刀鋒視窗中，選取群組成員，然後選擇 [選取] 按鈕。

4. 在 [群組] 刀鋒視窗中，選擇 [建立]。

### <a name="set-up-the-integration-between-symantec-endpoint-protection-mobile-and-intune"></a>設定 Symantec Endpoint Protection Mobile 與 Intune 整合

1.  移至 [Symantec Endpoint Protection Mobile 管理主控台](https://aad.skycure.com)。

2.  輸入您的 **SEP Mobile 系統管理員認證**，然後選擇 [繼續]。

3.  移至 [設定] > [整合] > [Intune] > [EMM 整合選擇] 區段。

4. 在 [目錄識別碼] 方塊中，貼上您在上一小節中從 Azure Active Directory 複製的目錄識別碼，並儲存設定。

    ![在 SEP Mobile 入口網站中顯示目錄識別碼的影像](./media/symantec-portal-directory-ID.png)     

5. 移至 [設定] > [整合] > [Intune] > [基本設定] 區段。

6. 在 [iOS 應用程式] 旁，選擇 [新增至 Active Directory] 按鈕。

    ![顯示將 iOS 應用程式新增到 Active Directory 的影像](./media/symantec-portal-basic-add.png)   

7.  使用 Azure Active Directory 認證登入管理目錄的 Office 365 帳戶。

8.  選擇 [接受] 按鈕以將 SEP Mobile iOS 應用程式新增至 Azure Active Directory。

    ![顯示接受按鈕的影像](./media/symantec-portal-basic-accept.png)     

9.  針對 [Android 應用程式] 和 [管理應用程式] 重複相同程序。

10. 選取需要執行 SEP Mobile 應用程式的所有使用者群組，例如您在稍早建立的安全性群組。

    ![顯示 SEP Mobile 應用程式使用者群組的影像](./media/symantec-portal-basic-groups.png)   

11.  SEP Mobile 會同步處理所選取群組中的裝置，並開始向 Intune 報告資訊。 您可以在 [完整整合] 區段中檢視此資料。 移至 [設定] > [整合] > [Intune] > [完整整合] 區段。

     ![顯示完成 SEP Mobile 完整整合的影像](media/symantec-portal-basic-status.PNG)
## <a name="next-steps"></a>後續步驟

[設定 SEP Mobile 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)
