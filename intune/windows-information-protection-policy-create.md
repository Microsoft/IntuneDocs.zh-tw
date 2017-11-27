---
title: "使用 Intune 建立及部署 Windows 資訊保護 (WIP) 應用程式保護原則"
titlesuffix: Azure portal
description: "使用 Intune 建立及部署 WIP 應用程式保護原則"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ab0456b58704f17d3dc5885ab5ae6b902c9ef152
ms.sourcegitcommit: dc2595bec05206a826cd10cb834bf6043145c917
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2017
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>使用 Intune 建立及部署 Windows 資訊保護 (WIP) 應用程式保護原則

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

從 Intune 1704 版開始，您可以搭配 Windows 10 使用應用程式保護原則，不用註冊即可保護應用程式。

## <a name="before-you-begin"></a>開始之前

我們先聊聊新增 WIP 原則時的一些概念。

### <a name="list-of-allowed-and-exempt-apps"></a>允許和豁免應用程式的清單

-   **允許的應用程式︰**這些應用程式是必須遵守此原則的應用程式。

-   **豁免應用程式︰**這些應用程式不會套用此原則，且可以不受限制地存取公司資料。

### <a name="types-of-apps"></a>應用程式類型

-   **建議的應用程式︰**此為預先填入的應用程式清單 (大部分是 Microsoft Office 應用程式)，可讓您輕鬆匯入原則。 <!---I really don't know what you mean by "easily import into policy"--->

-   **市集應用程式︰**您可以將 Windows 市集中的任何應用程式新增至原則。

-   **Windows 傳統型應用程式︰**您可以將任何傳統的 Windows 傳統型應用程式新增至原則 (例如 .exe、.dll)。

## <a name="pre-requisites"></a>必要條件

您必須先設定 MAM 提供者，才能建立 WIP 應用程式保護原則。 深入了解[如何設定搭配 Intune 的 MAM 提供者 (英文)](https://docs.microsoft.com/app-protection-policies-configure-windows-10.md)。

此外，您也需要下列各項：

-   [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) 授權。
-   [Windows Creators Update](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> WIP 不支援多重身分識別，一次只能存在一個受管理的身分識別。
<!---Should you be linking to a topic that explains what multi-identity is?--->

## <a name="to-add-a-wip-policy"></a>新增 WIP 原則

當您在組織中設定 Intune 之後，就可以透過 [Azure 入口網站](https://docs.microsoft.com/intune-classic/deploy-use/azure-portal-for-microsoft-intune-mam-policies)建立 WIP 特定原則。 <!---Is there an azure topic you can use instead of a classic? if not, should this topic be moved into the azure docset?--->

1.  移至 [Intune 行動應用程式管理儀表板]，選擇 [所有設定] > [應用程式原則]。

2.  在 [應用程式原則] 刀鋒視窗中，選擇 [新增原則]，然後輸入下列值：

    a.  **名稱：**輸入新原則的名稱 (必要)。

    b。  **描述：**輸入選擇性的描述。

    c.  **平台：**選擇 [Windows 10] 做為應用程式保護原則的支援平台。

    d.  **註冊狀態：**選擇 [沒有註冊] 做為原則的註冊狀態。

3.  選擇 **[建立]**。 原則將會建立並顯示在 [應用程式原則] 刀鋒視窗的表格中。

## <a name="to-add-recommended-apps-to-your-allowed-apps-list"></a>將建議的應用程式新增到允許的應用程式清單

1.  從 [應用程式原則] 刀鋒視窗，選擇您的原則名稱，然後從 [新增原則] 刀鋒視窗選擇 [允許的應用程式]。 [允許的應用程式] 刀鋒視窗隨即開啟，顯示此應用程式保護原則清單中已包含的所有應用程式。

2.  從 [允許的應用程式] 刀鋒視窗，選擇 [新增應用程式]。 [新增應用程式] 刀鋒視窗隨即開啟，顯示此清單中包含的所有應用程式。

3.  選取要存取公司資料的每個應用程式，然後選擇 [確定]。 [允許的應用程式] 刀鋒視窗隨即更新，顯示所有選取的應用程式。

## <a name="add-a-store-app-to-your-allowed-apps-list"></a>將市集應用程式新增到允許的應用程式清單

**新增市集應用程式**

1.  從 [應用程式原則] 刀鋒視窗，選擇您的原則名稱，然後從顯示的功能表中選擇 [允許的應用程式]。此功能表會顯示此應用程式保護原則清單中已包含的所有應用程式。

2.  從 [允許的應用程式] 刀鋒視窗，選擇 [新增應用程式]。

3.  在 [新增應用程式] 刀鋒視窗上，從下拉式清單中選擇 [市集應用程式]。 刀鋒視窗會變更為顯示方塊，讓您新增**發行者**和應用程式**名稱**。

4.  輸入應用程式的名稱與其發行者的名稱，然後選擇 [確定]。

    > [!TIP]
    > 以下是範例應用程式，其中**發行者**是 *CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US*，而產品**名稱**是 *Microsoft.MicrosoftAppForWindows*。

5.  在您將資訊輸入欄位之後，選擇 [確定]，便可將應用程式新增到 [允許的應用程式] 清單。

> [!NOTE]
> 若要同時新增多個市集應用程式，可以按一下應用程式列結尾的功能表 **(…)**，然後繼續新增更多應用程式。 完成後，選擇 [確定]。

## <a name="add-a-desktop-app-to-your-allowed-apps-list"></a>將傳統型應用程式新增到允許的應用程式清單

**新增傳統型應用程式**

1.  從 [應用程式原則] 刀鋒視窗，選擇您的原則名稱，然後選擇 [允許的應用程式]。 [允許的應用程式] 刀鋒視窗隨即開啟，顯示此應用程式保護原則清單中已包含的所有應用程式。

2.  從 [允許的應用程式] 刀鋒視窗，選擇 [新增應用程式]。

3.  從 [新增應用程式] 刀鋒視窗的下拉式清單中選擇 [傳統型應用程式]。

4.  在您將資訊輸入欄位之後，選擇 [確定]，即可將應用程式新增到 [允許的應用程式] 清單。

> [!NOTE]
> 若要同時新增多個**傳統型應用程式**，可以按一下應用程式資料列結尾的功能表 **(…)**，然後繼續新增更多應用程式。 完成後，選擇 [確定]。

## <a name="wip-learning"></a>WIP 學習
<!---You've already defined WIP earlier in the topic. You don't need to keep doing so. --->
在您新增要使用 WIP 來保護的應用程式之後，需要使用「WIP 學習」來套用保護模式。

### <a name="before-you-begin"></a>開始之前

WIP 學習是一種報表，可讓您監視 WIP 未知的應用程式。 未知的應用程式是不屬於組織 IT 部門所部署的應用程式。 在應用程式強制 WIP 使用「封鎖」模式之前，您可以從報告匯出這些應用程式，然後將它們新增到 WIP 原則，以避免造成生產力中斷。

您應該利用一小群使用者來驗證允許的應用程式清單中是否有正確的應用程式。驗證時，建議先使用「無訊息」或「允許覆寫」模式。 完成之後，您就可以變更為最終強制原則**封鎖**。

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

1.  選擇 [儲存]。

### <a name="use-wip-learning"></a>使用 WIP 學習

1. 開啟 Azure 入口網站。 選擇 [More services] (更多服務)。 在文字方塊篩選中，鍵入 **Intune**。

3. 選擇 [Intune] > [行動應用程式]。

4. 選擇 [應用程式保護狀態] > [報告] > [Windows 資訊保護學習]。  
 
    您可以根據 WIP 學習記錄報告中顯示的應用程式，將這些應用程式新增至應用程式保護原則。

## <a name="deploy-your-wip-app-protection-policy"></a>部署 WIP 應用程式保護原則

> [!IMPORTANT]
> 這適用於不註冊裝置的 WIP。

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

建立 WIP 應用程式保護原則之後，您需要使用 MAM 將它部署到組織。

1.  在 [應用程式原則] 刀鋒視窗上，選擇您新建立的應用程式保護原則，然後選擇 [使用者群組] > [Add user group] (新增使用者群組)。

    [新增使用者群組] 刀鋒視窗中隨即會開啟使用者群組清單，此清單由 Azure Active Directory 中的所有安全性群組所組成。

1.  選擇您要套用原則的群組，然後選擇 [選取] 來部署原則。
