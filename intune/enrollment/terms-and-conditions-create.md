---
title: 設定 Microsoft Intune 中的條款及條件
titleSuffix: ''
description: 設定使用者會在 Intune 公司入口網站中看到的條款及條件。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3fb5818609763753878fec7a84fd8c19eb154f88
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955434"
---
# <a name="terms-and-conditions-for-user-access"></a>使用者存取的條款及條件

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

身為 Intune 系統管理員，您可以要求使用者必須先接受公司的條款及條件，然後才能使用公司入口網站來執行下列作業：
- 註冊裝置
- 存取公司應用程式和電子郵件等資源。

條款及條件的設定是選擇性的。

您可以建立多組條款，並將它們指派給不同的群組，以達成支援不同語言等目的。

建立公司條款及條件的方式有兩種：
- 使用 Intune (如本文中所述)。
- 使用 [Azure Active Directory 使用規定功能](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou) \(部分機器翻譯\)

若要了解哪種方法最適合您，請參閱[選擇適合貴組織的條款解決方案](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409) \(英文\) 部落格文章。 

## <a name="create-terms-and-conditions"></a>建立條款及條件
完成下列步驟以建立條款及條件。 顯示名稱和描述是供系統管理使用，而條款屬性則會在公司入口網站中向使用者顯示。

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，選擇 [租用戶系統管理]   > [條款及條件]  。
2. 選擇 **[建立]** 。
3. 在 [基本]  頁面上，指定下列資訊：

   - **名稱**：Azure 入口網站中條款的名稱。 使用者不會看見此名稱。
   - **描述**：可協助您在 Azure 入口網站中識別這組條款的選擇性詳細資料。

    ![顯示 Azure 入口網站中適用於條款及條件的 [基本] 頁面螢幕擷取畫面](./media/terms-and-conditions-create/terms-basics-page.png)

4. 選擇 [下一步]  以移至 [條款]  頁面，並提供下列資訊：

   - **標題**：使用者在公司入口網站 [摘要]  上方所看見的條款名稱。
   - **條款及條件**：使用者看到的條款及條件，他們必須接受或拒絕。
   - **條款摘要**：使用者在接受條款時，說明其意義的文字。 例如，「一旦註冊您的裝置，即表示您同意 Contoso 所訂的使用條款。 在繼續進行之前，請先仔細閱讀條款」。

5. 選擇 [下一步]  以移至 [範圍標籤]  頁面。

6. 選擇 [選取範圍標籤]  、選取您要指派給這些條款及條件的範圍標籤，然後選擇 [選取]  。 

7. 選擇 [下一步]  以移至 [指派]  頁面，然後為 [指派給]  選擇下列其中一個選項：
    - **所有使用者**：選擇此選項，以將這些條款及條件指派給所有使用者。
    - **選取群組**：選擇此選項，在您藉由選擇 [選取要納入的群組]  來識別的群組中，將這些條款及條件指派給該群組中的每個人。

8. 選擇 [下一步]   > [建立]  。

## <a name="see-how-terms-are-displayed-to-your-users"></a>了解條款對使用者的顯示方式
下列範例在管理主控台和公司入口網站中顯示 [標題]  和[條款摘要]  。

![管理主控台和公司入口網站中 [標題] 和 [條款摘要] 的螢幕擷取畫面。](./media/terms-and-conditions-create/terms-summary-terms.png)

下列範例顯示管理主控台和公司入口網站中的條款及條件。

![管理主控台和公司入口網站中條款及條件的螢幕擷取畫面。](./media/terms-and-conditions-create/terms-properties-terms.png)


## <a name="monitor-terms-and-conditions"></a>監視條款和條件

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，選擇 [租用戶系統管理]   > [條款及條件]  。
2. 在條款及條件清單中，選擇您要檢視接受度的條款 > [接受度報告]  。

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>使用多個版本的條款和條件
您可以編輯條款及條件，並管理它們的版本。 每次當您大幅變更條款及條件時，您都應該：
- 增加版本號碼
- 要求使用者接受新的條款及條件

假如您只是修正錯字或變更格式，請保留目前的版本號碼。

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，選擇 [租用戶系統管理]   > [條款及條件]  > 選擇要修改的條款及條件 > [屬性]  。

2. 在 [屬性]  窗格上，選擇 [條款及條件]  ，然後視需要修改 [標題]  、[條款摘要]  和 [條款及條件]  。 如果您的變更需要使用者重新接受新的條款，請選擇 [需要使用者重新接受並將版本號碼增加至] 

3. 選擇 [確定]   > [儲存]  。

使用者只需要接受更新後的條款及條件一次。 具有多部裝置的使用者不需要在每部裝置上接受條款及條件。
