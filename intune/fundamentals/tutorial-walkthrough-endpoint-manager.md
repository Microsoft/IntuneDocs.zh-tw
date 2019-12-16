---
title: 教學課程 - 逐步解說 Microsoft 端點管理員中的 Intune
titleSuffix: Microsoft Intune
description: 在本教學課程中，您將導覽 Microsoft 端點管理員系統管理中心內的 Microsoft Intune，以深入了解如何完成工作。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune from the Microsoft Endpoint Manager admin center.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 267f09c3dc16aab10fbe64f0e8662ee6f7c7ffa0
ms.sourcegitcommit: ec69e7ccc6e6183862a48c1b03ca6a3bf573f354
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907988"
---
# <a name="tutorial-walkthrough-intune-in-microsoft-endpoint-manager"></a>教學課程：逐步解說 Microsoft 端點管理員中的 Intune

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) 包含超過 100 項服務，可協助您解決各種雲端運算案例和可能情況。 Microsoft Intune 是 Azure 提供的數項服務之一。 Intune 可協助您確保公司的裝置、應用程式和資料符合公司的安全性需求。 您可以掌控並設定必須檢查哪些需求，以及當這些需求不符合時會發生什麼事。 您可以在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)找到 Microsoft Intune 服務，以及其他裝置管理相關設定。 了解 Intune 所提供的功能將有助您完成各種行動裝置管理 (MDM) 和行動應用程式管理 (MAM) 工作。

> [!NOTE]
> Microsoft 端點管理員是單一的整合式端點管理平台，可管理您的所有端點。 此 Microsoft 端點管理員系統管理中心整合 ConfigMgr 和 Microsoft Intune。

在本教學課程中，您將：
> [!div class="checklist"]
> * 導覽 Microsoft 端點管理員系統管理中心
> * 自訂 Microsoft 端點管理員系統管理中心的檢視

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必要條件
設定 Microsoft Intune 之前，請先檢閱下列需求：

- [支援的作業系統與瀏覽器](../supported-devices-browsers.md) 
- [網路設定需求與頻寬](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>註冊 Microsoft Intune 免費試用

免費試用 Intune 30 天。 如果您已經有工作或學校帳戶，請**登入**該帳戶，並將 Intune 新增至您的訂閱。 否則，您可以[註冊免費的試用帳戶](free-trial-sign-up.md)供您的組織使用 Intune。

> [!IMPORTANT]
> 註冊新帳戶後，無法合併現有的工作或學校帳戶。

## <a name="tour-microsoft-intune-in-the-microsoft-endpoint-manager-admin-center"></a>導覽 Microsoft 端點管理員系統管理中心內的 Microsoft Intune

請遵循下列步驟，以深入了解 Microsoft 端點管理員系統管理中心內的 Intune。 完成導覽之後，您將深入了解 Intune 主要區域的一部分。

1. 開啟瀏覽器，並登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 若您剛開始使用 Intune，請使用免費的試用訂用帳戶。

    ![Microsoft 端點管理員系統管理中心 - 首頁的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-01.png)

    當您在 Azure 中開啟 Microsoft 端點管理員或任何其他服務時，該服務就會顯示在窗格中。 您可能在 Intune 中最先使用的一些工作負載包括 [裝置]  、[應用程式]  、[使用者]  和 [群組]  。 工作負載不過是服務的一個子區域。 當您選取工作負載時，它會以完整頁面開啟該窗格。 其他窗格會在開啟時從窗格右側滑出，並關閉以顯示上一個窗格。 

    根據預設，當您開啟 Microsoft 端點管理員時會看到 [首頁]  窗格。 此窗格提供租用戶狀態與合規性狀態的整體視覺快照，以及其他實用的相關連結。

2. 從瀏覽窗格，選取 [儀表板]  以顯示 Intune 租用戶中裝置和用戶端應用程式的整體詳細資料。 如果您要開始使用新的 Intune 租用戶，則目前不會有任何已註冊的裝置。 

    ![Microsoft 端點管理員系統管理中心 - 儀表板的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-02.png)
    
    Intune 可讓您管理員工的裝置與應用程式，包括員工存取公司資料的方式。 若要使用這項行動裝置管理 (MDM) 服務，裝置必須先在 Intune 中註冊。 裝置會在註冊時收到 MDM 憑證。 這項憑證會用來與 Intune 服務通訊。 

    有數種方法可以在 Intune 中註冊員工裝置。 每種方法皆會因裝置擁有權 (個人或公司)、裝置類型 (iOS、Windows、Android) 及管理需求 (重設、親和性、鎖定) 而有所不同。 不過，您必須先設定 Intune 基礎結構，才能啟用裝置註冊。 裝置註冊特別要求您[設定 MDM 授權單位](mdm-authority-set.md)。 如需準備您 Intune 環境 (租用戶) 的詳細資訊，請參閱[設定 Intune](setup-steps.md)。 準備好 Intune 租用戶之後，您可以註冊裝置。 如需裝置註冊的詳細資訊，請參閱[什麼是裝置註冊？](../enrollment/device-enrollment.md)

3. 從瀏覽窗格，選取 [裝置]  以顯示 Intune 租用戶已註冊裝置的詳細資料。 

    > [!TIP]
    > 如果您先前曾經在 Azure 入口網站中使用 Intune，則可以透過登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並選取 [裝置]  ，以在 Azure 入口網站中找到上述詳細資料。

    [裝置 - 概觀]  窗格包含數個索引標籤，可讓您檢視下列狀態和警示的摘要：
    - **註冊狀態** - 依平台和註冊失敗檢閱 Intune 已註冊裝置的詳細資料。
    - **註冊警示** - 依平台尋找未指派裝置的更多詳細資料。 
    - **合規性狀態** - 根據裝置、原則、設定、威脅和保護來檢閱合規性狀態。 此外，此窗格也會提供沒有合規性政策的裝置清單。
    - **設定狀態** - 檢閱裝置設定檔的設定狀態，以及設定檔部署。 
    - **軟體更新狀態** - 查看所有裝置和所有使用者的視覺部署狀態。

    ![Microsoft 端點管理員系統管理中心 - 裝置的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-03.png)

4. 從 [裝置 - 概觀]  窗格，選取 [合規性政策]  以顯示 Intune 所管理裝置合規性的詳細資料。 您將會看到類似下圖的詳細資料。

    ![Microsoft 端點管理員系統管理中心 - 合規性政策的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-04.png)
    
    > [!TIP]
    > 如果您先前曾經在 Azure 入口網站中使用 Intune，則可以透過登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並選取 [裝置合規性]  ，在 Azure 入口網站中找到上述詳細資料。

    合規性需求基本上就是一些規則，例如要求裝置 PIN 或要求裝置加密。 裝置合規性政策會定義裝置必須遵循才能視為符合規範的規則和設定。 若要使用裝置合規性，您必須具備：
    - Intune 和 Azure Active Directory (Azure AD) Premium 訂用帳戶
    - 執行支援平台的裝置
    - 裝置必須在 Intune 中註冊
    - 一位使用者註冊或沒有主要使用者註冊的裝置。
    
    如需詳細資訊，請參閱 [Intune 中的裝置合規性政策入門](../protect/device-compliance-get-started.md)。

5. 從 [裝置 - 概觀]  ，選取 [條件式存取]  以顯示存取原則的詳細資料。

    ![Microsoft 端點管理員系統管理中心 - 條件式存取的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-05.png)

    > [!TIP]
    > 如果您先前曾經在 Azure 入口網站中使用 Intune，則可以透過登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並選取 [條件式存取]  ，在 Azure 入口網站中找到上述詳細資料。

    條件式存取是指您可以控制允許連線到您電子郵件和公司資源的裝置與應用程式的方式。 若要了解以裝置或應用程式為基礎的條件式存取，並尋找搭配 Intune 使用條件式存取的常見案例，請參閱[什麼是條件式存取？](../protect/conditional-access.md)

6. 從瀏覽窗格，選取 [裝置]   > [組態設定檔]  以顯示 Intune 中裝置設定檔的詳細資料。

    ![Microsoft 端點管理員系統管理中心 - 組態設定檔的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-06.png)
    
    > [!TIP]
    > 如果您先前曾經在 Azure 入口網站中使用 Intune，則可以透過登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並選取 [裝置設定]  ，在 Azure 入口網站中找到上述詳細資料。

    Intune 包含您可以在組織內不同裝置上啟用或停用的設定及功能。 這些設定和功能會新增至「組態設定檔」。 您可以為不同的裝置和平台 (包括 iOS、Android、macOS 和 Windows) 建立設定檔。 然後，您可以使用 Intune 將設定檔套用至您組織中的裝置。   

    如需裝置設定的詳細資訊，請參閱[在 Microsoft Intune 中使用裝置設定檔將功能設定套用至您的裝置](../configuration/device-profiles.md)。

7. 從瀏覽窗格，選取 [裝置]   > [所有裝置]  以顯示 Intune 租用戶已註冊裝置的詳細資料。 如果您要開始使用新的 Intune 登錄，則目前不會有任何已註冊的裝置。

    ![Microsoft 端點管理員系統管理中心 - 所有裝置的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-07.png)

    此裝置清單會顯示合規性、OS 版本和上次簽入日期的重要詳細資料。

    > [!TIP]
    > 如果您先前曾經在 Azure 入口網站中使用 Intune，則可以透過登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並選取 [裝置]   > [所有裝置]  ，在 Azure 入口網站中找到上述詳細資料。
 
8. 從瀏覽窗格，選取 [應用程式]  以顯示應用程式狀態的概觀。 此窗格會根據下列索引標籤提供應用程式安裝狀態：

    > [!TIP]
    > 如果您先前曾經在 Azure 入口網站中使用 Intune，則可以透過登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並選取 [用戶端應用程式]  ，在 Azure 入口網站中找到上述詳細資料。

    [應用程式 - 概觀]  窗格包含兩個索引標籤，可讓您檢視下列狀態的摘要：
    - **安裝狀態** - 檢視前幾個安裝失敗的裝置，以及安裝失敗的應用程式。  
    - **應用程式防護原則狀態** - 尋找已指派應用程式防護原則的使用者及已標幟的使用者詳細資料。

    ![Microsoft 端點管理員系統管理中心 - 應用程式的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-08.png)

    身為 IT 系統管理員，您可以使用 Microsoft Intune 來管理公司員工使用的用戶端應用程式。 而這項功能還可以用於管理裝置與保護資料。 系統管理員最優先的事項之一，是確保終端使用者能夠存取工作所需的應用程式。 此外，您也可能需要指派及管理未向 Intune 註冊之裝置上的應用程式。 Intune 提供各種功能，可協助您在所要的裝置上取得所需的應用程式。 

    > [!NOTE]
    > [應用程式 - 概觀]  窗格也會提供租用戶狀態和帳戶詳細資料。

    如需新增和指派應用程式的詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](../apps/apps-add.md) 和[使用 Microsoft Intune 將應用程式指派給群組](../apps/apps-deploy.md)。

9. 從 [應用程式 - 概觀]  窗格，選取 [所有應用程式]  以查看新增至 Intune 的應用程式清單。

    > [!TIP]
    > 如果您先前曾經在 Azure 入口網站中使用 Intune，則可以透過登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並選取 [用戶端應用程式]   > [應用程式]  ，在 Azure 入口網站中找到上述詳細資料。

    您可以根據平台，將各種不同的應用程式類型新增至 Intune。 新增應用程式之後，您就可以將其指派給使用者群組。 

    ![Microsoft 端點管理員系統管理中心 - 所有應用程式的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-09.png)

    如需詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](~/apps/apps-add.md)。 

10. 從瀏覽窗格，選取 [使用者]  以顯示 Intune 中所包含使用者的詳細資料。 這些使用者是您公司的員工。

    ![Microsoft 端點管理員系統管理中心 - 使用者的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-10.png)

    > [!TIP]
    > 如果您先前曾經在 Azure 入口網站中使用 Intune，則可以透過登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並選取 [使用者]  ，在 Azure 入口網站中找到上述詳細資料。

    您可以將使用者直接新增至 Intune，或同步內部部署 Active Directory 中的使用者。 新增之後，使用者便可以註冊裝置，並存取公司資源。 您也可以提供使用者其他權限來存取 Intune。 如需詳細資訊，請參閱[新增使用者並授與 Intune 系統管理權限](users-add.md)。

11. 從瀏覽窗格，選取 [群組]  以顯示 Intune 中所包含 Azure Active Directory (Azure AD) 群組的詳細資料。 身為 Intune 系統管理員，您可以使用群組來管理裝置與使用者。

    ![Microsoft 端點管理員系統管理中心 - 群組的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-11.png)

    > [!TIP]
    > 如果您先前曾經在 Azure 入口網站中使用 Intune，則可以透過登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並選取 [群組]  ，在 Azure 入口網站中找到上述詳細資料。

    您可以根據組織需求來設定群組。 依地理位置、部門或硬體特性建立群組，來組織使用者或裝置。 使用群組管理大規模的工作。 例如，您可以為許多使用者設定原則，或將應用程式部署到一組裝置。 如需群組的詳細資訊，請參閱[新增群組來組織使用者和裝置](../groups-add.md)。

12. 從瀏覽窗格，選取 [租用戶系統管理]  以顯示 Intune 租用戶的詳細資料。

    > [!TIP]
    > 如果您先前曾經在 Azure 入口網站中使用 Intune，則可以透過登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並選取 [租用戶狀態]  ，在 Azure 入口網站中找到上述詳細資料。

    [租用戶系統管理 - 租用戶狀態]  窗格提供 [租用戶詳細資料]  、[連接器狀態]  和 [服務健全狀況儀表板]  索引標籤。 如果租用戶或 Intune 本身發生任何問題，您會從此窗格找到可用的詳細資料。 

    ![Microsoft 端點管理員系統管理中心 - 租用戶狀態的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-12.png)

    如需詳細資訊，請參閱 [Intune 租用戶狀態](../tenant-status.md)。

13. 從瀏覽窗格，選取 [疑難排解 + 支援]   > [疑難排解]  以查看特定使用者的狀態詳細資料。 

    > [!TIP]
    > 如果您先前曾經在 Azure 入口網站中使用 Intune，則可以透過登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並選取 [疑難排解]  ，在 Azure 入口網站中找到上述詳細資料。

    從 [指派]  下拉式清單，您可以選擇檢視用戶端應用程式、原則、更新通道和註冊限制的目標指派。 此外，此窗格也會提供特定使用者的裝置詳細資料、應用程式防護狀態和註冊失敗。

    ![Microsoft 端點管理員系統管理中心 - 疑難排解的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-13.png)

    如需在 Intune 內進行疑難排解的詳細資訊，請參閱[使用疑難排解入口網站協助您公司的使用者](../help-desk-operators.md)。

14. 從瀏覽窗格，選取 [疑難排解 + 支援]   > [說明及支援]  以要求協助。 

    > [!TIP]
    > 如果您先前曾經在 Azure 入口網站中使用 Intune，則可以透過登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並選取 [說明及支援]  ，在 Azure 入口網站中找到上述詳細資料。

    身為 IT 系統管理員，您可以使用 [說明及支援]  選項來搜尋和檢視解決方案，並提出 Intune 的線上支援票證。 

    ![Microsoft 端點管理員系統管理中心 - 說明及支援的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-14.png)

    若要建立支援票證，您的帳戶必須指派為 Azure Active Directory 中的一個管理員角色。 這些管理員角色包括 [Intune 系統管理員]  、[全域管理員]  和 [服務管理員]  。 

    如需詳細資訊，請參閱[如何取得 Microsoft Intune 支援](../get-support.md)。

15. 從瀏覽窗格，選取 [疑難排解 + 支援]   > [引導式案例]  以顯示可用的 Intune 引導式案例。 

    引導式案例是以單一端對端使用案例為中心的一系列自訂步驟。 常見案例會以組織中系統管理員、使用者或裝置所扮演的角色為基礎。 這些角色通常需要一組仔細協調的設定檔、設定、應用程式和安全性控制項，以提供最佳的使用者體驗和安全性。

    如果您尚不熟悉實作特定 Intune 案例所需的所有步驟和資源，便可以使用引導式案例作為起點。 

    ![Microsoft 端點管理員系統管理中心 - 引導式案例的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-15.png)

    如需引導式案例的詳細資訊，請參閱[引導式案例概觀](~/fundamentals/guided-scenarios-overview.md)。

## <a name="configure-the-microsoft-endpoint-manager-admin-center"></a>設定 Microsoft 端點管理員系統管理中心

Azure 可讓您自訂和設定入口網站的顯示畫面。

### <a name="change-the-dashboard"></a>變更儀表板

**儀表板**可顯示 Intune 租用戶中裝置和用戶端應用程式的整體詳細資料。 儀表板可讓您在 Microsoft 端點管理員系統管理中心內建立集中式管理檢視。 使用儀表板作為工作區，以便在其中快速啟動日常作業工作及監視資源。 例如，您可以根據專案、工作或使用者角色來建置自訂儀表板。 Microsoft 端點管理員系統管理中心提供預設儀表板作為起點。 您可以編輯預設儀表板、建立和自訂其他儀表板，以及發佈和共用儀表板供其他使用者使用。 

   ![Microsoft 端點管理員系統管理中心 - 儀表板的螢幕擷取畫面](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-16.png)

若要修改目前儀表板，請選取 [編輯]  。 如果您不想要變更預設儀表板，也可以建立「新儀表板」  。 建立新的儀表板，即可透過「磚庫」  提供空白的私人儀表板，以讓您新增或重新排列磚。 您可以依類別或資源類型來尋找磚。 您也可以搜尋特定磚。 選取 [我的儀表板]  即可選取任何一個現有的自訂儀表板。

### <a name="change-the-portal-settings"></a>變更入口網站設定

您可以選擇預設檢視、主題、認證逾時期限，以及語言和區域設定來自訂 Microsoft 端點管理員系統管理中心。

   <img alt="Screenshot of the Microsoft Endpoint Manager admin center - Portal settings" src="./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-17.png" width="250">

## <a name="next-steps"></a>後續步驟

若要在 Microsoft Intune 上快速開始執行，請先設定免費的 Intune 帳戶，再逐步完成 Intune 快速入門。

> [!div class="nextstepaction"]
> [快速入門：免費試用 Microsoft Intune](free-trial-sign-up.md)
