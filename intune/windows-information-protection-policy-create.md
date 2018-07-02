---
title: 建立及部署 Windows 資訊保護 (WIP) 應用程式保護原則
titlesuffix: Microsoft Intune
description: 使用 Microsoft Intune 建立及部署 Windows 資訊保護 (WIP) 應用程式保護原則
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 61df998dae611eb7350fa144260780b5589afc61
ms.sourcegitcommit: 07528df71460589522a2e1b3e5f9ed63eb773eea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34762241"
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>使用 Intune 建立及部署 Windows 資訊保護 (WIP) 應用程式保護原則

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

您可以搭配 Windows 10 應用程式使用應用程式保護原則，不用註冊裝置即可保護應用程式。

## <a name="before-you-begin"></a>開始之前

您必須了解新增 WIP 原則時的一些概念：

### <a name="list-of-allowed-and-exempt-apps"></a>允許和豁免應用程式的清單

-   **受保護的應用程式︰** 這些應用程式是必須遵守此原則的應用程式。

-   **豁免應用程式︰** 這些應用程式不會套用此原則，且可以不受限制地存取公司資料。

### <a name="types-of-apps"></a>應用程式類型

-   **建議的應用程式︰** 此為預先填入的應用程式清單 (大部分是 Microsoft Office 應用程式)，可讓您輕鬆匯入原則。
-   **市集應用程式︰** 您可以將 Windows 市集中的任何應用程式新增至原則。
-   **Windows 傳統型應用程式︰** 您可以將任何傳統的 Windows 傳統型應用程式新增至原則 (例如 .exe、.dll)。

## <a name="prerequisites"></a>必要條件

您必須先設定 MAM 提供者，才能建立 WIP 應用程式保護原則。 深入了解[如何設定搭配 Intune 的 MAM 提供者 (英文)](app-protection-policies-configure-windows-10.md)。

此外，您也需要下列授權和更新：

-   [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) 授權
-   [Windows Creators Update](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> WIP 不支援多重身分識別，一次只能存在一個受管理的身分識別。

## <a name="to-add-a-wip-app-protection-policy"></a>新增 WIP 應用程式保護原則

當您在組織中設定 Intune 之後，就可以建立 WIP 特定原則。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [所有服務] > [Intune]。
3. 在 [Microsoft Intune] 刀鋒視窗中選取 [行動應用程式]。
4. 在 [行動應用程式] 刀鋒視窗中選取 [應用程式防護原則]。
5. 選取 [新增原則]，即可顯示 [新增原則] 刀鋒視窗。
6. 新增下列值：
    - **名稱：** 輸入新原則的名稱 (必要)。
    - **描述：**(選擇性) 鍵入描述。
    - **平台：** 選擇 [Windows 10] 做為應用程式保護原則的支援平台。
    - **註冊狀態：** 選擇 [沒有註冊] 做為原則的註冊狀態。
7.  選擇 **[建立]**。 原則會建立並顯示在 [應用程式防護原則] 刀鋒視窗的表格中。

## <a name="to-add-recommended-apps-to-your-protected-apps-list"></a>將建議的應用程式新增到受保護的應用程式清單

1. 在 [Microsoft Intune] 刀鋒視窗中選取 [行動應用程式]。
2. 在 [行動應用程式] 刀鋒視窗中選取 [應用程式防護原則]。
3. 在 [應用程式防護原則] 刀鋒視窗中，選擇您想要修改的原則。 [Intune 應用程式防護] 刀鋒視窗隨即出現。
4. 從 [Intune 應用程式防護] 刀鋒視窗中選擇 [受保護的應用程式]。 [受保護的應用程式] 刀鋒視窗隨即開啟，顯示此應用程式保護原則清單中已包含的所有應用程式。
5. 選取 [新增應用程式]。 [新增應用程式] 資訊會向您顯示應用程式的篩選清單。 刀鋒視窗頂端的清單允許您變更清單篩選條件。
6. 選取您希望允許存取公司資料的每個應用程式。
7. 按一下 [確定]。 [受保護的應用程式] 刀鋒視窗隨即更新，顯示所有選取的應用程式。
8. 按一下 **[儲存]**。

## <a name="add-a-store-app-to-your-protected-apps-list"></a>將市集應用程式新增到受保護的應用程式清單

**新增市集應用程式**
1. 在 [Microsoft Intune] 刀鋒視窗中選取 [行動應用程式]。
2. 在 [行動應用程式] 刀鋒視窗中選取 [應用程式防護原則]。
3. 在 [應用程式防護原則] 刀鋒視窗中，選擇您想要修改的原則。 [Intune 應用程式防護] 刀鋒視窗隨即出現。
4. 從 [Intune 應用程式防護] 刀鋒視窗中選擇 [受保護的應用程式]。 [受保護的應用程式] 刀鋒視窗隨即開啟，顯示此應用程式保護原則清單中已包含的所有應用程式。
5. 選取 [新增應用程式]。 [新增應用程式] 資訊會向您顯示應用程式的篩選清單。 刀鋒視窗頂端的清單允許您變更清單篩選條件。
6. 從清單中，選取 [市集應用程式]。
7. 輸入 [名稱]、[Pubisher] (發行者)、[產品名稱] 和 [動作] 的值。 請務必將 [動作] 的值設定為 [允許]，以便應用程式可以存取您的公司資料。
9. 按一下 [確定]。 [受保護的應用程式] 刀鋒視窗隨即更新，顯示所有選取的應用程式。
10. 按一下 **[儲存]**。

## <a name="add-a-desktop-app-to-your-protected-apps-list"></a>將桌面應用程式新增到受保護的應用程式清單

**新增傳統型應用程式**
1. 在 [Microsoft Intune] 刀鋒視窗中選取 [行動應用程式]。
2. 在 [行動應用程式] 刀鋒視窗中選取 [應用程式防護原則]。
3. 在 [應用程式防護原則] 刀鋒視窗中，選擇您想要修改的原則。 [Intune 應用程式防護] 刀鋒視窗隨即出現。
4. 從 [Intune 應用程式防護] 刀鋒視窗中選擇 [受保護的應用程式]。 [受保護的應用程式] 刀鋒視窗隨即開啟，顯示此應用程式保護原則清單中已包含的所有應用程式。
5. 選取 [新增應用程式]。 [新增應用程式] 資訊會向您顯示應用程式的篩選清單。 刀鋒視窗頂端的清單允許您變更清單篩選條件。
6. 從清單中，選取 [桌面應用程式]。
7. 輸入 [名稱]、[Pubisher] (發行者)、[產品名稱]、[檔案]、[最小版本]、[最大版本] 和 [動作] 的值。 請務必將 [動作] 的值設定為 [允許]，以便應用程式可以存取您的公司資料。
9. 按一下 [確定]。 [受保護的應用程式] 刀鋒視窗隨即更新，顯示所有選取的應用程式。
10. 按一下 **[儲存]**。

## <a name="wip-learning"></a>WIP 學習
在您新增要使用 WIP 來保護的應用程式之後，需要使用「WIP 學習」來套用保護模式。

### <a name="before-you-begin"></a>開始之前

WIP 學習是一種報表，可讓您監視啟用 WIP 的應用程式與 WIP 未知的應用程式。 未知的應用程式是不屬於組織 IT 部門所部署的應用程式。 在應用程式強制 WIP 使用「封鎖」模式之前，您可以從報告匯出這些應用程式，然後將它們新增到 WIP 原則，以避免造成生產力中斷。

<!-- 1631908 -->
除了檢視啟用 WIP 之應用程式的資訊外，您也可檢視與網站共用工作資料之裝置的摘要。 您可以藉由這項資訊，決定哪些網站應該加入群組和使用者 WIP 原則。 摘要會顯示啟用 WIP 之應用程式所存取的網站 URL。

在進行啟用 WIP 的應用程式和 WIP 未知的應用程式相關工作時，建議您先從 [無訊息] 或 [允許覆寫] 開始，同時透過少數幾名使用者確認受保護的應用程式清單上具有正確的應用程式。 完成之後，您就可以變更為最終強制原則**封鎖**。

### <a name="what-are-the-protection-modes"></a>什麼是保護模式？

#### <a name="block"></a>封鎖
WIP 會尋找不適當的資料共用做法，並阻止使用者完成動作。 這可能包括與未受公司保護的應用程式共用資料，以及與組織以外的人員或裝置共用公司資料。

#### <a name="allow-overrides"></a>允許覆寫
WIP 會尋找不適當的資料共用，並在使用者執行某些可能不安全的動作時警告使用者。 不過，此模式可讓使用者覆寫原則並共用資料，但是會將動作記錄到稽核記錄中。

#### <a name="silent"></a>無訊息
WIP 會以無訊息方式執行，記錄不適當的資料共用，而不會封鎖在「允許覆寫」模式中可能會提示員工互動的任何動作。 此模式仍然會停止不允許的動作，例如，應用程式以不適當的方式嘗試存取網路資源或受 WIP 保護的資料。

#### <a name="off-not-recommended"></a>關閉 (不建議使用)
此模式會關閉 WIP，因此不會協助保護或稽核資料。

關閉 WIP 之後，系統會嘗試將本機連接之磁碟機上任何 WIP 標記的檔案解密。 請注意，如果您再次開啟 WIP 保護，則不會自動重新套用先前的解密和原則資訊。

### <a name="add-a-protection-mode"></a>新增保護模式

1.  從 [應用程式原則] 刀鋒視窗，選擇您的原則名稱，然後選擇 [Required settings] (必要設定)。

    ![學習模式的螢幕擷取畫面](./media/learning-mode-sc1.png)

1.  選取設定，然後選擇 [儲存]。

### <a name="use-wip-learning"></a>使用 WIP 學習

1. 開啟 [Azure 入口網站](https://portal.azure.com)。 選擇 [所有服務]。 在文字方塊篩選中，鍵入 **Intune**。

3. 選擇 [Intune] > [行動應用程式]。

4. 選擇 [應用程式保護狀態] > [報告] > [Windows 資訊保護學習]。  

    您可以根據 WIP 學習記錄報告中顯示的應用程式，將這些應用程式新增至應用程式保護原則。

## <a name="allow-windows-search-indexer-to-search-encrypted-items"></a>允許 Windows 搜尋索引子搜尋加密項目
允許或不允許編製項目的索引。 這個參數是針對 Windows 搜尋索引子，它控制是否編製加密項目的索引，例如 Windows 資訊保護 (WIP) 保護的檔案。

這個應用程式保護原則選項是在 Windows 資訊保護原則的 [進階設定] 中。 應用程式保護原則必須設為 *Windows 10* 平台，且應用程式原則 [註冊狀態] 必須設為 [註冊]。

啟用此原則時，會編製 WIP 保護項目的索引，而其相關中繼資料會儲存在未加密的位置。 中繼資料包含像是檔案路徑和修改日期等事項。

停用此原則時，不會編製 WIP 保護項目的索引，且不會出現在 Cortana 或檔案總管的結果中。 如果裝置上有許多 WIP 保護的媒體檔案，也可能影響相片和 Groove 應用程式的效能。

## <a name="add-encrypted-file-extensions"></a>新增加密副檔名

除了設定 [Allow Windows Search Indexer to search encrypted items] (允許 Windows 搜尋索引子搜尋加密項目 選項，您也可以指定副檔名清單。 從網路位置清單中所定義之公司界限內的伺服器訊息區塊 (SMB) 共用複製時，會加密具有這些副檔名的檔案。 未指定此原則時，會套用現有的自動加密行為。 已設定此原則時，將只會加密具有清單中之副檔名的檔案。

## <a name="deploy-your-wip-app-protection-policy"></a>部署 WIP 應用程式保護原則

> [!IMPORTANT]
> 此資訊適用於未不註冊裝置的 WIP。

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

建立 WIP 應用程式保護原則之後，您需要使用 MAM 將它部署到組織。

1.  在 [應用程式原則] 刀鋒視窗上，選擇您新建立的應用程式保護原則，然後選擇 [使用者群組] > [Add user group] (新增使用者群組)。

    [新增使用者群組] 刀鋒視窗中隨即會開啟使用者群組清單，此清單由 Azure Active Directory 中的所有安全性群組所組成。

2.  選擇您要套用原則的群組，然後選擇 [選取] 來部署原則。

## <a name="next-steps"></a>接下來的步驟

深入了解 Windows 資訊保護，請參閱[使用 Windows 資訊保護 (WIP) 保護您的企業資料](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)。
