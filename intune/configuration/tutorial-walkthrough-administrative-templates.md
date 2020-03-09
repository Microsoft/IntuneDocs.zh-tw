---
title: 逐步解說：在 Microsoft Intune 中建立系統管理範本 - Azure | Microsoft Docs
description: 本教學課程或逐步解說使用 Microsoft Intune 在 Windows 10 及更新版本的裝置上，設定 Office、Windows 與 Microsoft Edge ADMX 範本。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a96f291203e1513ab89196b26a7802856f90e048
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77688086"
---
# <a name="tutorial-use-the-cloud-to-configure-group-policy-on-windows-10-devices-with-admx-templates-and-microsoft-intune"></a>教學課程：使用雲端為具有 ADMX 範本及 Microsoft Intune 的 Windows 10 裝置上設定群組原則

> [!NOTE]
> 本教學課程依照 Microsoft Ignite 技術講習的形式建立。 相較於一般教學課程，在 Intune 與內部部署中使用及設定 ADMX 原則，本課程的必要條件比較多。

群組原則系統管理範本 (也稱為 ADMX 範本) 包含您可以在像是電腦等 Windows 10 裝置上設定的設定。 ADMX 範本設定由不同的服務提供。 這些設定由行動裝置管理 (MDM) 提供者使用，包括 Microsoft Intune。 例如，您可以在 PowerPoint 中起始設計構想、在 Microsoft Edge 中設定首頁、在 Internet Explorer 中封鎖 ActiveX 控制項等等。

ADMX 範本適用於下列服務：

- **Microsoft Edge**：下載 [ Microsoft Edge 原則檔案](https://www.microsoftedgeinsider.com/en-us/enterprise)。
- **Office**：下載 [Office 365 ProPlus、Office 2019 及 Office 2016 ](https://www.microsoft.com/download/details.aspx?id=49030)。
- **Windows**：內建於 Windows 10 作業系統。

如需 ADMX 原則的詳細資訊，請參閱[了解支援 ADMX 的原則](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies)。

在 Microsoft Intune 中，這些範本內建在 Intune 服務中，並以**系統管理範本**設定檔的形式提供。 在此設定檔中，您可以設定您想要加入的設定，然後再將此設定檔「指派」給您的裝置。

在本教學課程中，您將：

> [!div class="checklist"]
> * 認識 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
> * 建立使用者群組與裝置群組。
> * 比較 Intune 的設定與內部部署的 ADMX 的設定。
> * 建立不同的系統管理範本，並設定不同群組所應使用的設定。

當此實驗室結束時，您將具備開始使用 Intune 及 Microsoft 365 管理您的使用者，以及部署系統管理範本的技能。

本功能適用於：

- Windows 10 1703 版及更新版本

## <a name="prerequisites"></a>先決條件

- Microsoft 365 E3 或 E5 訂閱：包含 Intune 及 Azure Active Directory (AD) Premium。 若沒有 E3 或 E5 訂閱，可[免費試用](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365?view=o365-worldwide)。

  如需不同 Microsoft 365 授權之權益的詳細資訊，請參閱[透過 Microsoft 365 讓您的企業轉型](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans)。

- Microsoft Intune 已設定為 **Intune MDM 授權單位**。 如需詳細資訊，請參閱[設定行動裝置管理授權單位](../fundamentals/mdm-authority-set.md)。

  > [!div class="mx-imgBorder"]
  > ![在您的租用戶狀態中將 MDM 授權單位設定為 Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/tenant-status.png)

- 在內部部署 Active Directory 網域控制站 (DC) 上：

  1. 將下列 Office 及 Microsoft Edge 範本複製到[中央存放區 (SYSVOL 資料夾)](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra)：

      - [Office 系統管理範本](https://www.microsoft.com/download/details.aspx?id=49030)
      - [Microsoft Edge 系統管理範本 > 原則檔案](https://www.microsoftedgeinsider.com/en-us/enterprise)

  2. 建立群組原則，將這些範本推送到 DC 所在網域中的 Windows 10 企業版系統管理員電腦。 在本教學課程中：

      - 使用這些範本建立的群組原則，稱為 **OfficeandEdge**。 您將會在影像中看到此名稱。
      - 我們使用的 Windows 10 企業版系統管理員電腦，稱為**系統管理員電腦**。

      在有一些組織中，網域系統管理員有兩個帳戶：一般網域公司帳戶，以及另一個網域系統管理員帳戶，只用於網域系統管理員工作 (例如群組原則)。

      此**系統管理員電腦**的用途，在讓系統管理員能夠使用其網域系統管理員帳戶登入，以及存取專為管理群組原則所設計的工具。

- 在此**系統管理員電腦**上：

  - 使用網域系統管理員帳戶登入。

  - 安裝 **RSAT：群組原則管理工具**：

    1. 開啟 [設定]  應用程式 > [應用程式]   >  [選用功能]   >  [新增功能]  。
    2. 選取 **RSAT：群組原則管理工具** > **安裝**。

        等候 Windows 安裝功能。 完成時，其最終會顯示在 [Windows 系統管理工具]  應用程式中。

        > [!div class="mx-imgBorder"]
        > ![Windows 系統管理工具應用程式，包括群組原則管理應用程式](./media/tutorial-walkthrough-administrative-templates/windows-administrative-tools-app.png)

  - 請確定您能夠存取網際網路，並具有 Microsoft 365 訂閱 (包括端點管理員系統管理中心) 的系統管理員權利。

## <a name="open-the-endpoint-manager-admin-center"></a>Microsoft 端點管理員系統管理中心

1. 開啟 Chromium 網頁瀏覽器，例如 Microsoft Edge 77 版及更新版本。
2. 前往 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431) (https://devicemanagement.microsoft.com) )。 使用下列帳戶登入：

    **使用者**：輸入您 Microsoft 365 租用戶訂閱的系統管理員帳戶。  
    **密碼**：輸入密碼。

系統管理中心主要用於管理裝置，並包括 Azure 服務，例如 Azure AD 及 Intune。 您可能不會看到 **Azure Active Directory** 及 **Intune** 商標，但您正在使用。

您也可以從 [Microsoft 365 系統管理中心](https://admin.microsoft.com)開啟端點管理員系統管理中心：

1. 移至 [https://admin.microsoft.com](https://admin.microsoft.com)。
2. 使用您 Microsoft 365 租用戶訂閱的系統管理員帳戶登入。
3. 在**系統管理中心**中，選取 [所有系統管理中心]   >  [端點管理]  。 Microsoft 端點管理員系統管理中心會隨即開啟。

    > [!div class="mx-imgBorder"]
    > ![查看 Microsoft 365 系統管理中心中所有的系統管理中心](./media/tutorial-walkthrough-administrative-templates/microsoft365-admin-centers.png)

## <a name="create-groups-and-add-users"></a>建立群組，然後新增使用者

內部部署原則會依 LSDOU 順序，套用本機、網站、網域及組織單位 (OU)。 在此階層中，OU 原則會覆寫本機原則、網域原則會覆寫網站原則，依此類推。

在 Intune 中，原則會套用到您所建立的使用者及群組。 此處沒有階層。 若兩項原則更新同一項設定，該設定會顯示為衝突。 當兩項合規性原則發生衝突時，將會套用限制最嚴格的原則。 若是兩個設定檔發生衝突，將不會套用設定。 如需詳細資訊，請參閱[裝置原則與設定檔常見的問題、疑問與解決方法](device-profile-troubleshoot.md#if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied)。

在接下來的步驟中，您將建立安全性群組，以及將使用者新增至群組。 您可以將使用者新增至多個群組。 例如，使用者通常會有多部裝置，例如工作用 Surface Pro，以及私人用的 Android 行動裝置。 而且使用者通常也能從這些裝置存取組織資源。

1. 在 Microsoft 端點管理員系統管理中心中，選取 [群組]   >  [新增群組]  。

2. 輸入下列設定：

    - **群組類型**：選取 [安全性]  。
    - **群組名稱**：輸入**所有 Windows 10 學生版裝置**。
    - **成員資格類型**：選取 [已指派]  。

3. 選取 [成員]  ，然後新增一些裝置。

    您不一定需要新增裝置。 新增的目標在練習建立群組，並了解如何新增裝置。 若在生產環境中使用此教學課程，請注意您執行的作業。

4. [選取]   >  [建立]  ，以儲存您的變更。

    看不到您的群組嗎？ 選取 [重新整理]  。

5. 選取 [新增群組]  ，然後輸入下列內容：

    - **群組類型**：選取 [安全性]  。
    - **群組名稱**：輸入**所有 Windows 裝置**。
    - **成員資格類型**：選取 [動態裝置]  。
    - **動態裝置成員**：設定您的查詢：

        - **屬性**：選取 [deviceOSType]  。
        - **運算子**：選取 [等於]  。
        - **值**：輸入 **Windows**。

        1. 選取 [新增運算式]  。 您的運算式會顯示在 [規則語法]  中：

            > [!div class="mx-imgBorder"]
            > ![建立動態查詢，並在 Microsoft Intune 系統管理範本中新增運算式](./media/tutorial-walkthrough-administrative-templates/dynamic-group-query.png)

            當使用者或裝置符合您輸入的準則時，就會自動新增至動態群組。 在此範例中，當作業系統是 Windows 時，裝置就會自動新增至此群組。 若您在生產環境中使用此教學課程，請務必小心。 此課程的目的在練習建立動態群組。

        2. [儲存]   >  [建立]  ，以儲存您的變更。

6. 使用下列設定建立**所有老師**群組：

    - **群組類型**：選取 [安全性]  。
    - **群組名稱**：輸入**所有老師**。
    - **成員資格類型**：選取 [動態使用者]  。
    - **動態使用者成員**：設定您的查詢：

      - **屬性**：選取 [部門]  。
      - **運算子**：選取 [等於]  。
      - **值**：輸入**老師**。

        1. 選取 [新增運算式]  。 您的運算式會顯示在 [規則語法]  中。

            當使用者或裝置符合您輸入的準則時，就會自動新增至動態群組。 在此範例中，當使用者的部門為「老師」時，就會自動新增至此群組。 您可以在使用者新增至您的組織時，輸入部門及其他屬性。 若您在生產環境中使用此教學課程，請務必小心。 此課程的目的在練習建立動態群組。

        2. [儲存]   >  [建立]  ，以儲存您的變更。

### <a name="talking-points"></a>課程要點

- 動態群組是 Azure AD Premium 的功能之一。 若沒有 Azure AD Premium，則您的授權只能建立指派的群組。 如需動態群組的詳細資訊，請參閱：

  - [Azure Active Directory 中的動態群組成員資格 (第 1 部分)](https://blogs.technet.microsoft.com/pauljones/2017/08/28/dynamic-group-membership-in-azure-active-directory-part-1/)
  - [Azure Active Directory 中的動態群組成員資格 (第 2 部分)](https://blogs.technet.microsoft.com/pauljones/2017/08/29/dynamic-group-membership-in-azure-active-directory-part-2/)

- Azure AD Premium 包含管理應用程式和裝置時經常使用的其他服務，包括[多重要素驗證 (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) 及[條件式存取](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)。

- 許多系統管理員會詢問何時使用使用者群組，以及何時使用裝置群組。 如需相關指導，請參閱 [使用者群組與裝置群組](device-profile-assign.md#user-groups-vs-device-groups)。

- 請記住，一位使用者可以屬於多個群組。 您可以考慮一些您可以建立的其他動態使用者和裝置群組，例如：

  - 所有學生
  - 所有 Android 裝置
  - 所有 iOS/iPadOS 裝置
  - 行銷
  - 人力資源
  - 所有 Charlotte 員工
  - 所有 Redmond 員工
  - 西岸的 IT 系統管理員
  - 東岸的 IT 系統管理員

所建立的使用者與群組，也會顯示在 [Microsoft 365 系統管理中心](https://admin.microsoft.com)、Azure 入口網站中的 Azure AD，以及[ Azure 入口網站中的 Microsoft Intune ](https://go.microsoft.com/fwlink/?linkid=2090973) 之中。 您可以在您的租用戶訂閱中，為所有這些領域建立及管理群組。 **若您的目標是裝置管理，請使用 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)** 。

### <a name="review-group-membership"></a>檢閱群組成員資格

1. 在端點管理員系統管理中心，選取 [使用者]  > 選取任何現有使用者的名稱。

    > [!div class="mx-imgBorder"]
    > ![在端點管理員系統管理中心中選取使用者](./media/tutorial-walkthrough-administrative-templates/select-users-endpoint-manager-admin-center.png)

2. 檢閱一些您可以新增或變更的資訊。 舉例來說，查看您可以設定的屬性，例如工作職稱、部門、城市、辦公室位置等等。 當您在建立動態群組時，可以在您的動態查詢中使用這些屬性。
3. 選取 [群組]  ，以查看此使用者的成員資格。 您也可以從群組中移除使用者。
4. 選取一些其他選項，以查看更多資訊，以及您可以執行的動作。 例如查看指派的授權、使用者的裝置等等。

### <a name="what-did-i-just-do"></a>我剛剛做了些什麼？

您在端點管理員系統管理中心中，建立了新的安全性群組，並將現有的使用者與裝置新增至這些群組。 我們將在本教學課程之後的步驟中，使用這些群組。

## <a name="create-a-template-in-intune"></a>在 Intune 中建立範本

在本節中，我們會在 Intune 中建立系統管理範本、查看**群組原則管理**中的一些設定，以及比較 Intune 中的相同設定。 此課程的目的在展示群組原則中的設定，以及展示 Intune 中相同的設定。

1. 在**端點管理員系統管理中心**中，選取 [裝置] >   [組態設定檔]  >  [建立設定檔]  。
2. 輸入下列內容：

    - **名稱**：為設定檔輸入描述性名稱。 命名您的設定檔，以方便之後能輕鬆識別。 例如，輸入**系統管理範本 - Windows 10 學生版裝置**。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取 [Windows 10 及更新版本]  。
    - **設定檔類型**：選取 [系統管理範本]  。

3. 選取 [建立]  。 在 [選取類別]  下拉式清單中，選取 [所有產品]  。 顯示所有設定。 在這些設定中，請注意下列屬性：

    - 原則的**路徑**與群組原則管理或 GPEdit 相同。
    - 此設定適用於使用者或裝置。

### <a name="open-group-policy-management"></a>開啟群組原則管理

在本節中，我們會展示 Intune 中的原則，以及其在群組原則管理編輯器中的對應原則。

#### <a name="compare-a-device-policy"></a>比較裝置原則

1. 在**系統管理員電腦**上，開啟 [群組原則管理]  應用程式。

    此應用程式會隨 **RSAT 一起安裝：群組原則管理工具**：您可以選擇是否要在 Windows 上安裝此功能。 [必要條件](#prerequisites) (本文所列) 會列出安裝的步驟。

2. 展開 [網域]  > 選取您的網域。 例如選取 [contoso.net]  。
3. 以滑鼠右鍵按一下 [OfficeandEdge]  原則 > [編輯]  。 這會開啟群組原則管理編輯器。

    > [!div class="mx-imgBorder"]
    > ![以滑鼠右鍵按一下 Office 與 Edge ADMX 群組原則，然後選取 [編輯]](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management.png)

    **OfficeandEdge** 是包含 Office 及 Microsoft Edge ADMX 範本的群組原則。 此原則列在[必要條件](#prerequisites) (本文中)。

4. 展開 [電腦設定]   >  [原則]   >  [系統管理範本]   >  [控制台]   >  [個人化]  。 請注意您可以使用的設定。

    > [!div class="mx-imgBorder"]
    > ![在群組原則管理編輯器中展開 [電腦設定]，然後移至 [個人化]](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management-editor-admx-policy.png)

    按兩下 [防止啟用鎖定畫面相機]  ，然後查看可用的選項：

    > [!div class="mx-imgBorder"]
    > ![請參閱群組原則中的電腦組態設定](./media/tutorial-walkthrough-administrative-templates/prevent-enabling-lock-screen-camera-admx-policy.png)

5. 在裝置管理系統管理中心，移至您的**系統管理範本 - Windows 10 學生版裝置**範本。
6. 從下拉式清單中選取 [所有產品]  ，然後搜尋 [個人化]  ：

    > [!div class="mx-imgBorder"]
    > ![在 Microsoft Intune 中，搜尋系統管理範本中的個人化](./media/tutorial-walkthrough-administrative-templates/search-personalization-administrative-template.png)

    請注意您可以使用的設定。

    此設定類型為**裝置**，路徑為 **\Control Panel\Personalization**。 此路徑類似於您在群組原則管理編輯器中所見。 若開啟此設定，將會在群組原則管理編輯器中，看到 [未設定]  、[啟用]  和 [停用]  等相同的選項。

#### <a name="compare-a-user-policy"></a>比較使用者原則

1. 在您的系統管理員範本中，搜尋 [InPrivate 瀏覽]  。 請注意路徑，以及套用至使用者與裝置的設定。

2. 在**群組原則管理編輯器**中，尋找相符的使用者與裝置設定：

    - 裝置：展開 [電腦設定]   >  [原則]   >  [系統管理範本]   >  [Windows 元件]   >  [Internet Explorer]   >  [隱私權]   >  [關閉 InPrivate 瀏覽]  。
    - 使用者:展開 [使用者設定]   >  [原則]   >  [系統管理範本]   >  [Windows 元件]   >  [Internet Explorer]   >  [隱私權]   >  [關閉 InPrivate 瀏覽]  。

    > [!div class="mx-imgBorder"]
    > ![在 Internet Explorer 中，使用 ADMX 範本關閉 InPrivate 瀏覽](./media/tutorial-walkthrough-administrative-templates/group-policy-turn-off-inprivate-browsing.png)

> [!TIP]
> 您也可以使用 GPEdit (**編輯群組原則**應用程式) 查看內建的 Windows 原則。

#### <a name="compare-an-edge-policy"></a>比較 Edge 原則

1. 在裝置管理系統管理中心，移至您的**系統管理範本 - Windows 10 學生版裝置**範本。
2. 從下拉式清單中選取 [Edge 77 版和更新版本]  。
3. 搜尋 [啟動]  。 請注意您可以使用的設定。
4. 在群組原則管理編輯器中，尋找下列設定：

    - 裝置：展開 [電腦設定]   >  [原則]   >  [系統管理範本]   >  [Microsoft Edge]   >  [安裝程式、首頁及新索引標籤頁]  。
    - 使用者:展開 [使用者設定]   >  [原則]   >  [系統管理範本]   >  [Microsoft Edge]   >  [安裝程式、首頁及新索引標籤頁]  。

### <a name="what-did-i-just-do"></a>我剛剛做了些什麼？

您在 Intune 中建立了系統管理範本。 在此範本中，我們檢視了一些 ADMX 設定，以及查看了群組原則管理中相同的 ADMX 設定。

## <a name="add-settings-to-the-students-admin-template"></a>新增設定至學生管理範本

在此範本中，我們會設定一些 Internet Explorer 設定，以鎖定多位學生共用的裝置。

1. 在您的 **系統管理範本 - Windows 10 學生版裝置**中，搜尋 [關閉 InPrivate 瀏覽]  ，然後選取裝置原則：

    > [!div class="mx-imgBorder"]
    > ![在 Microsoft Intune 中關閉系統管理範本中的 InPrivate 瀏覽裝置原則](./media/tutorial-walkthrough-administrative-templates/turn-off-inprivate-browsing-administrative-template.png)

2. 在此視窗中，請注意您可以設定的描述和值。 這些選項類似於您在群組原則中所見。
3. 選取 [啟用]   >  [確定]  ，以儲存您的變更。
4. 另請設定下列 Internet Explorer 設定。 請務必選取 [確定]  ，以儲存您的變更。

    - **允許拖放或複製及貼上檔案**
      - **類型**：裝置
      - **路徑**：\Windows 元件\Internet Explorer\網際網路控制台\安全性網頁\網際網路區域
      - **值**：停用

    - **防止忽略憑證錯誤**
      - **類型**：裝置
      - **路徑**：\Windows 元件\Internet Explorer\網際網路控制台
      - **值**：已啟用

    - **停用變更首頁設定**
      - **類型**：User
      - **路徑**：\Windows 元件\Internet Explorer
      - **值**：已啟用
      - **首頁**：輸入 URL，例如 `contoso.com`。

5. 清除您的搜尋篩選。 請注意，您的設定會列在頂端：

    > [!div class="mx-imgBorder"]
    > ![設定會列在 Microsoft Intune 的頂端](./media/tutorial-walkthrough-administrative-templates/configured-settings-administrative-template.png)

### <a name="assign-your-template"></a>指派您的範本

1. 在您的範本中，選取 [指派]  。 您可能必須關閉您的範本，然後從**組態設定檔裝置**清單中選取：

    > [!div class="mx-imgBorder"]
    > ![從 Microsoft Intune 的組態設定檔裝置清單中，選取您的系統管理範本設定檔](./media/tutorial-walkthrough-administrative-templates/filter-administrative-template-device-configuration-profiles-list.png)

2. 選擇 [選取您要包括的群組]  。 現有使用者與群組清單會隨即顯示。
3. 選取您稍早建立的**所有 Windows 10 學生版裝置** > [選取]  。

    若您在生產環境中使用此教學課程，請考慮新增空白群組。 此課程的目的在練習指派您的範本。

4. [儲存]  變更。

設定檔一經儲存，便會在裝置簽入 Intune 時套用。 若裝置已連線至網際網路，將會立即執行。 如需原則重新整理次數的詳細資訊，請參閱[為裝置指派原則、設定檔或應用程式之後，需要多久時間才能套用這些原則、設定檔或應用程式](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)

指派嚴格或限制的原則及設定檔時，請勿讓自己變得窒礙難行。建立群組時，請考慮從原則和設定檔排除該群組。 方法是能夠進行疑難排解。 監視此群組，以確認其使用方式一如預期。

### <a name="what-did-i-just-do"></a>我剛剛做了些什麼？

您在端點管理員系統管理中心，建立了系統管理範本裝置設定檔，並將此設定檔指派給您所建立的群組。

## <a name="create-a-onedrive-template"></a>建立 OneDrive 範本

在本節中，您會在 Intune 中建立 OneDrive 管理範本，以控制一些設定。 因為組織常會使用這些特定設定，所以選擇這些設定。

1. 建立其他設定檔 ([裝置]   >  [組態設定檔]   >  [建立設定檔]  )。

2. 輸入下列內容：

    - **名稱**：輸入**適用於所有 Windows 10 使用者之 OneDrive 原則的系統管理範本**。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取 [Windows 10 及更新版本]  。
    - **設定檔類型**：選取 [系統管理範本]  。

3. 選取 [建立]  。
4. 從下拉式清單中選取 [Office]  。
5. **啟用**下列設定。 請務必選取 [確定]  ，以儲存您的變更。

    - **使用使用者的 Windows 認證，無訊息地將使用者登入 OneDrive 同步用戶端**
    - **隨需使用 OneDrive 檔案**
    - **防止使用者同步個人 OneDrive 帳戶**

您的設定會看起來類似下列設定：

> [!div class="mx-imgBorder"]
> ![在 Microsoft Intune 中建立 OneDrive 系統管理範本](./media/tutorial-walkthrough-administrative-templates/one-drive-administrative-template.png)

如需 OneDrive 用戶端設定的詳細資訊，請參閱[使用群組原則控制 OneDrive 同步用戶端的設定](https://docs.microsoft.com/onedrive/use-group-policy)。

### <a name="assign-your-template"></a>指派您的範本

1. 在您的範本中，選取 [指派]  。
2. 選擇 [選取您要包括的群組]  。 現有使用者與群組清單會隨即顯示。
3. 選取您稍早建立的**所有 Windows 裝置** > [選取]  。

    若您在生產環境中使用此教學課程，請考慮新增空白群組。 此課程的目的在練習指派您的範本。

4. [儲存]  變更。

至此您已建立一些系統管理範本，並已將這些範本指派給您所建立的群組。 接下來將要為使用 Windows PowerShell 建立系統管理範本，以及使用 Microsoft Graph API 建立 Intune。

## <a name="optional-create-a-policy-using-powershell-and-graph-api"></a>選用：使用 PowerShell 和 Graph API 建立原則

本節將使用下列來源。 我們將在本節中安裝這些資源。

- [Intune PowerShell SDK](https://github.com/microsoft/Intune-PowerShell-SDK)
- [適用於 Intune 的 Microsoft Graph API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

1. 以系統管理員身分，在**系統管理電腦**中開啟 **Windows PowerShell**：

    1. 在您的搜尋列中，輸入 **powershell**。
    2. 以滑鼠右鍵按一下 [Windows PowerShell]   >  [以系統管理員身分執行]  。

    > [!div class="mx-imgBorder"]
    > ![以系統管理員身分執行 Windows PowerShell](./media/tutorial-walkthrough-administrative-templates/run-windows-powershell-administrator.png)

2. 取得及設定執行原則。

    1. 輸入：`get-ExecutionPolicy`

        記下設定的內容，可能為**受限制**。 完成本教學課程後，請將其設定回原來的值。

    2. 輸入：`Set-ExecutionPolicy -ExecutionPolicy Unrestricted`

    3. 輸入 `Y` 加以變更。

    PowerShell 的執行原則有助於遏止執行惡意指令碼。 如需詳細資訊，請參閱[關於執行原則](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies)。

3. 輸入：`Install-Module -Name Microsoft.Graph.Intune`

    當發生下列情況時，請輸入 `Y`：

    - 要求安裝 NuGet 提供者
    - 要求從不信任的存放庫安裝模組

    可能需要幾分鐘的時間才能完成。 完成時會顯示類似如下的提示：

    > [!div class="mx-imgBorder"]
    > ![安裝模組之後的 Windows PowerShell 提示](./media/tutorial-walkthrough-administrative-templates/powershell-prompt.png)

4. 在您的網頁瀏覽器中，移至 [https://github.com/Microsoft/Intune-PowerShell-SDK/releases](https://github.com/Microsoft/Intune-PowerShell-SDK/releases)，然後選取 [Intune-PowerShell-1907.00921.0001 SDK_v6]  檔案。

    1. 選取 [另存新檔]  ，然後選取您容易記住的資料夾。 建議選擇 `c:\psscripts`。
    2. 開啟您的資料夾，再以滑鼠右鍵按一下 .zip 檔案 > [解壓縮所有]   >  [解壓縮]  。 您的資料夾結構看起來與下列資料夾類似：

        > [!div class="mx-imgBorder"]
        > ![解壓縮之後的 Intune PowerShell SDK 資料夾結構](./media/tutorial-walkthrough-administrative-templates/psscripts-directory.png)

5. 在 [檢視]  索引標籤上，檢查 **副檔名**：

    > [!div class="mx-imgBorder"]
    > ![在檔案總管中的檢視索引標籤上選取副檔名](./media/tutorial-walkthrough-administrative-templates/file-names-extension.png)

6. 在您的資料夾中，移至 `c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471`。 以滑鼠右鍵按一下每個 .dll > [屬性]   >  [解除封鎖]  。

    > [!div class="mx-imgBorder"]
    > ![解除封鎖 DLL](./media/tutorial-walkthrough-administrative-templates/unblock-dll.png)

7. 在您的 [Windows PowerShell]  應用程式中，輸入：

    ```powershell
    Import-Module c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471\Microsoft.Graph.Intune.psd1
    ```

    若提示從不信任的發行者執行，請輸入 `R`。

8. Intune 系統管理範本使用 Graph 測試版本：

    1. 輸入：`Update-MSGraphEnvironment -SchemaVersion 'beta'`

    2. 輸入：`Connect-MSGraph -AdminConsent`

    3. 當出現提示時，請使用相同的 Microsoft 365 系統管理員帳戶登入。 這些 Cmdlet 會在您的租用戶組織中建立原則。

        **使用者**：輸入您 Microsoft 365 租用戶訂閱的系統管理員帳戶。  
        **密碼**：輸入密碼。

    4. 選取 [接受]  。

9. 建立**測試組態**的組態設定檔。 輸入：

    ```powershell
    $configuration = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations -Content '{"displayName":"Test Configuration","description":"A test configuration created through PS"}' -HttpMethod POST
    ```

    當這些 Cmdlet 成功時，就會建立設定檔。 若要確認，請移至端點管理員系統管理中心 > [組態設定檔]  。 您的**測試組態**的設定檔應會列出。

10. 取得所有的 SettingDefinition。 輸入：

    ```powershell
    $settingDefinitions = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions -HttpMethod GET
    ```

11. 使用顯示名稱設定尋找定義識別碼。 輸入：

    ```powershell
    $desiredSettingDefinition = $settingDefinitions.value | ? {$_.DisplayName -Match "Silently sign in users to the OneDrive sync client with their Windows credentials"}
    ```

12. 進行設定。 輸入：

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues" -Content ("{""enabled"":""true"",""configurationType"":""policy"",""definition@odata.bind"":""https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions('$($desiredSettingDefinition.id)')""}") -HttpMethod POST
    ```

    ```powershell
    Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -Content ("{""enabled"":""false""}") -HttpMethod PATCH
    ```

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -HttpMethod GET
    ```

### <a name="see-your-policy"></a>查看您的原則

1. 在端點管理員系統管理中心中 > [組態設定檔]   >  [重新整理]  。
2. 選取您的 [測試組態]  設定檔 > [設定]  。
3. 在下拉式清單內，選取 [所有產品]  。

您會看到**使用使用者的 Windows 認證，無訊息地將使用者登入 OneDrive 同步用戶端**設定已設定。

## <a name="policy-best-practices"></a>原則最佳做法

在 Intune 中建立原則和設定檔時，需要考慮一些建議和最佳做法。 如需詳細資訊，請參閱[原則與設定檔的最佳做法](device-profile-create.md#recommendations)。

## <a name="clean-up-resources"></a>清除資源

當不再需要時，您可以：

- 刪除您所建立的群組：

  - **所有 Windows 10 學生版裝置**
  - **所有 Windows 裝置**
  - **所有老師**

- 刪除您所建立的系統管理範本：

  - **系統管理範本 - Windows 10 學生版裝置**
  - **套用到所有 Windows 10 使用者之 OneDrive 原則的系統管理範本**
  - **測試設定**

- 將 Windows PowerShell 執行原則設定回原來的值。 下列範例會將執行原則設定為受限制：

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Restricted
  ```

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將更熟悉 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)、使用查詢建立器建立動態群組，以及在 Intune 中建立系統管理範本，以設定 [ADMX 設定](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies)。 您也可以使用內部部署和雲端中的 ADMX 範本與 Intune 進行比較。 此外，您還可使用 PowerShell Cmdlet 建立系統管理範本。

如需 Intune 中系統管理範本的詳細資訊，請參閱：

> [!div class="nextstepaction"]
> [使用 Windows 10 範本設定 Intune 群組原則的設定](administrative-templates-windows.md)
