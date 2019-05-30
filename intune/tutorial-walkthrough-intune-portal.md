---
title: 教學課程 - 逐步解說 Azure 入口網站中的 Intune
titleSuffix: Microsoft Intune
description: 在本教學課程中，您將導覽 Microsoft Intune，以深入了解如何完成工作。
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 03/28/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e892d8a3-7f74-498c-98d5-e968a8fbb049
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c84cd0ec61ea08956bbebd040167991c6285d073
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66044974"
---
# <a name="tutorial-walkthrough-of-microsoft-intune-in-the-azure-portal"></a>教學課程：逐步解說 Azure 入口網站中的 Microsoft Intune

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) 包含超過 100 項服務，可協助您解決各種雲端運算案例和可能情況。 Microsoft Intune 是 Azure 提供的數項服務之一。 Intune 可協助您確保公司的裝置、應用程式和資料符合公司的安全性需求。 您可以掌控並設定必須檢查哪些需求，以及當這些需求不符合時會發生什麼事。 您可以在 [Azure 入口網站](https://portal.azure.com)中找到 Microsoft Intune 服務。 了解 Intune 所提供的功能將有助您完成各種行動裝置管理 (MDM) 和行動應用程式管理 (MAM) 工作。

在本教學課程中，您將：
> [!div class="checklist"]
> * 導覽 Microsoft Intune
> * 設定 Azure 入口網站

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必要條件
設定 Microsoft Intune 之前，請先檢閱下列需求：

   - [支援的作業系統與瀏覽器](supported-devices-browsers.md) 
   - [網路設定需求與頻寬](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>註冊 Microsoft Intune 免費試用

免費試用 Intune 30 天。 如果您已經有工作或學校帳戶，請**登入**該帳戶，並將 Intune 新增您的訂閱。 否則，您可以[註冊免費的試用帳戶](free-trial-sign-up.md)供您的組織使用 Intune。

> [!IMPORTANT]
> 註冊新帳戶後，無法合併現有的工作或學校帳戶。

## <a name="tour-microsoft-intune"></a>導覽 Microsoft Intune

請遵循下列步驟，以深入了解 Azure 入口網站中的 Intune。 完成導覽之後，您將深入了解 Intune 主要區域的一部分。

1. 開啟瀏覽器並登入 [Intune 入口網站](https://aka.ms/intuneportal)。 若您剛開始使用 Intune，請使用免費的試用訂用帳戶。

    ![Microsoft Intune 入口網站的螢幕擷取畫面](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-01.png)

    當您在 Azure 中開啟 Intune 或任何其他服務時，該服務就會顯示在窗格中。 您可能在 Intune 中最先使用的一些工作負載包括 [裝置]、[用戶端應用程式]、[使用者] 和 [群組]。 工作負載不過是服務的一個子區域。 當您選取工作負載時，它會以完整頁面開啟該窗格。 其他窗格會在開啟時從窗格右側滑出，並關閉以顯示上一個窗格。 窗格也稱為刀鋒視窗。 

    根據預設，當您開啟 Intune 時會看到 [概觀] 窗格。 此窗格提供裝置指派與合規性狀態，以及應用程式安裝狀態的整體視覺快照。

2. 從 [Intune](https://aka.ms/intuneportal)，選取 [裝置註冊] 以顯示您 Intune 租用戶已註冊裝置的詳細資料。 如果您要開始使用新的 Intune 租用戶，則目前不會有任何已註冊的裝置。 

    ![[裝置註冊] 窗格的螢幕擷取畫面](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-02.png)
    
    Intune 可讓您管理員工的裝置與應用程式，包括員工存取公司資料的方式。 若要使用這項行動裝置管理 (MDM) 服務，裝置必須先在 Intune 中註冊。 裝置會在註冊時收到 MDM 憑證。 這項憑證會用來與 Intune 服務通訊。 

    有數種方法可以在 Intune 中註冊員工裝置。 每種方法皆會因裝置擁有權 (個人或公司)、裝置類型 (iOS、Windows、Android) 及管理需求 (重設、親和性、鎖定) 而有所不同。 不過，您必須先設定 Intune 基礎結構，才能啟用裝置註冊。 裝置註冊特別要求您[設定 MDM 授權單位](mdm-authority-set.md)。 如需準備您 Intune 環境 (租用戶) 的詳細資訊，請參閱[設定 Intune](setup-steps.md)。 準備好 Intune 租用戶之後，您可以註冊裝置。 如需裝置註冊的詳細資訊，請參閱[什麼是裝置註冊？](device-enrollment.md)

3. 從 [Intune](https://aka.ms/intuneportal)，選取 [裝置合規性] 以顯示 Intune 所管理裝置合規性的詳細資料。 您將會看到類似下圖的詳細資料。

    ![[裝置合規性] 窗格的螢幕擷取畫面](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-03.png)
    
    合規性需求基本上就是一些規則，例如要求裝置 PIN 或要求裝置加密。 裝置合規性政策會定義裝置必須遵循才能視為符合規範的規則和設定。 若要使用裝置合規性，您必須具備：
    - Intune 和 Azure Active Directory (Azure AD) Premium 訂用帳戶
    - 執行支援平台的裝置
    - 裝置必須在 Intune 中註冊
    - 註冊至一位使用者或沒有主要使用者的裝置。
    
    如需詳細資訊，請參閱 [Intune 中的裝置合規性政策入門](device-compliance-get-started.md)。

4. 從 [Intune](https://aka.ms/intuneportal)，選取 [裝置設定] 以顯示 Intune 中裝置設定檔的詳細資料。 

    ![[裝置設定] 窗格的螢幕擷取畫面](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-04.png)
    
    Intune 包含您可以在組織內不同裝置上啟用或停用的設定及功能。 這些設定和功能會新增至「組態設定檔」。 您可以為不同的裝置和平台 (包括 iOS、Android 和 Windows) 建立設定檔。 然後，您可以使用 Intune 將設定檔套用至您組織中的裝置。   

    如需裝置設定的詳細資訊，請參閱[在 Microsoft Intune 中使用裝置設定檔將功能設定套用至您的裝置](device-profiles.md)。

5. 從 [Intune](https://aka.ms/intuneportal)，選取 [裝置] 以顯示您 Intune 租用戶已註冊裝置的詳細資料。 如果您要開始使用新的 Intune 登錄，則目前不會有任何已註冊的裝置。 

    ![[裝置註冊] 窗格的螢幕擷取畫面](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-05.png)
    
    [裝置] 窗格提供您租用戶已註冊裝置的詳細資料。 您可以按一下 [所有裝置] 以顯示您 Intune 租用戶的裝置清單。 

6. 從 [Intune](https://aka.ms/intuneportal)，選取 [用戶端應用程式] 以顯示應用程式安裝狀態。

    ![[用戶端應用程式] 窗格的螢幕擷取畫面](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-06.png)
    
    身為 IT 系統管理員，您可以使用 Microsoft Intune 來管理公司員工使用的用戶端應用程式。 這項功能與管理裝置和保護資料一起存在。 系統管理員最優先的事項之一，是確保使用者能夠存取工作所需的應用程式。 此外，您也可能需要指派及管理未向 Intune 註冊之裝置上的應用程式。 Intune 提供各種功能，可協助您在所要的裝置上取得所需的應用程式。 如需新增和指派應用程式的詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](apps-add.md) 和[使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)。

7. 從 [Intune](https://aka.ms/intuneportal)，選取 [條件式存取] 以顯示存取原則的詳細資料。

    ![[條件式存取] 窗格的螢幕擷取畫面](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-07.png)

    條件式存取是指您可以控制可連線到您電子郵件和公司資源的裝置與應用程式的方式。 若要深入了解以裝置和應用程式為基礎的條件式存取，並尋找搭配 Intune 使用條件式存取的常見案例，請參閱[什麼是條件式存取？](conditional-access.md)

8. 從 [Intune](https://aka.ms/intuneportal)，選取 [使用者] 以顯示 Intune 中所包含使用者的詳細資料。 這些使用者是您公司的員工。 
 
    ![[使用者] 窗格的螢幕擷取畫面](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-08.png)

    您可以將使用者直接新增至 Intune，或同步內部部署 Active Directory 中的使用者。 新增之後，使用者便可以註冊裝置，並存取公司資源。 您也可以提供使用者其他權限來存取 Intune。 如需詳細資訊，請參閱[新增使用者並授與 Intune 系統管理權限](users-add.md)。

9. 從 [Intune](https://aka.ms/intuneportal)，選取 [群組] 以顯示 Intune 中所包含 Azure Active Directory (Azure AD) 群組的詳細資料。 身為 Intune 系統管理員，您可以使用群組來管理裝置與使用者。 

    ![[群組] 窗格的螢幕擷取畫面](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-09.png)

    您可以設定群組來符合組織需求。 依地理位置、部門或硬體特性建立群組，來組織使用者或裝置。 使用群組管理大規模的工作。 例如，您可以為許多使用者設定原則，或將應用程式部署到一組裝置。 如需群組的詳細資訊，請參閱[新增群組來組織使用者和裝置](groups-add.md)。

10. 從 [Intune](https://aka.ms/intuneportal)，選取 [說明及支援] 以要求協助。 身為 IT 系統管理員，您可以使用 [說明及支援] 選項來搜尋和檢視解決方案，並提出 Intune 的線上支援票證。 

    ![[說明及支援] 窗格的螢幕擷取畫面](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-10.png)

    若要建立支援票證，您的帳戶必須指派為 Azure Active Directory 中的一個管理員角色。 這些管理員角色包括 [Intune 系統管理員]、[全域管理員] 和 [服務管理員]。 如需詳細資訊，請參閱[如何取得 Microsoft Intune 支援](get-support.md)。

11. 從 [Intune](https://aka.ms/intuneportal)，選取 [租用戶狀態] 以顯示您 Intune 租用戶的詳細資料。

    ![[租用戶狀態] 窗格的螢幕擷取畫面](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-11.png)

    租用戶狀態詳細資料包括連接器狀態、Intune 服務健全狀況和 Intune 新聞。 如果您的租用戶或 Intune 本身發生任何問題，您會在 [租用戶狀態] 窗格中找到詳細資料。 如需詳細資訊，請參閱 [Intune 租用戶狀態](tenant-status.md)。

12. 從 [Intune](https://aka.ms/intuneportal)，選取 [疑難排解] 以抵達疑難排解提示、要求支援或檢查 Intune 狀態的捷徑。 這是您所選取 Intune 使用者的特定資訊。

    ![[疑難排解] 窗格的螢幕擷取畫面](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-12.png)

如需在 Intune 內進行疑難排解的詳細資訊，請參閱[使用疑難排解入口網站協助您公司的使用者](help-desk-operators.md)。

## <a name="configure-the-azure-portal"></a>設定 Azure 入口網站

Azure 可讓您自訂和設定入口網站的檢視。

### <a name="change-the-sidebar"></a>變更資訊看板

Azure 入口網站左側的**資訊看板**會顯示所有可用 Azure 服務清單。 您可以從預設檢視變更此完整清單，以保留您最重要服務的持續性檢視。 下列資訊使用 Intune 作為要新增至清單頂端的服務範例。

![在 [More services] (更多服務) 清單中搜尋 Microsoft Intune 的使用者。](./media/azure-add-intune1.png)

1. 從頁面左側的資訊看板，選取 [所有服務]。
2. 在篩選方塊中，搜尋 **Intune**。
3. 選取**星狀**，以將 Intune 新增至我的最愛服務清單底部。
4. 將滑鼠游標放在 Intune 服務上方。 使用服務名稱右側的三個垂直點，以選取並拖曳 Intune。

### <a name="change-the-dashboard"></a>變更儀表板

您的預設登陸頁面是「儀表板」。 您可以在這個頁面自訂您的磚，以顯示與您最相關的資訊。

![泛型新儀表板的影像。 它會在左側顯示具有所有服務的資訊看板，然後在中央顯示主要儀表板。 儀表板修改按鈕會沿著上方，並且具有多個磚可以存取所有資源、快速入門教學課程、服務健全狀況和 Azure Marketplace。](./media/azure-default-dashboard.png)

若要修改目前儀表板，請選取 [編輯儀表板] 按鈕。 如果您不想要變更預設儀表板，也可以建立「新儀表板」。 建立新的儀表板，即可透過「磚庫」提供空白的私用儀表板，以讓您新增或重新排列磚。 您可以透過 [搜尋] 以及 [資源群組] 或 [標記]，依 [一般] 類別 [類型] 找到磚。

您也可以透過任何**省略**按鈕以及選取 [釘選到儀表板]，直接將磚新增至儀表板。

![[使用者和群組] > Intune 中的 [所有群組] 位置的特寫，其可在群組最右側顯示 [釘選到儀表板] 選項。](./media/azure-pin-to-dashboard.png)

將更多內容 (例如群組和使用者) 新增至 Intune 之後，此功能會更具相關性。

## <a name="next-steps"></a>後續步驟

若要在 Microsoft Intune 上快速開始執行，請先設定免費的 Intune 帳戶，再逐步完成 Intune 快速入門。

> [!div class="nextstepaction"]
> [快速入門：免費試用 Microsoft Intune](free-trial-sign-up.md)


