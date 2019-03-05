---
title: 設定 Microsoft Intune 中的條款及條件
titlesuffix: ''
description: 設定使用者會在 Intune 公司入口網站中看到的條款及條件。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1b0571ad6196277ee2bc257d72cc4db24fcc3424
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57237940"
---
# <a name="terms-and-conditions-for-user-access"></a>使用者存取的條款及條件

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

身為 Intune 系統管理員，您可以要求使用者必須先接受公司的條款及條件，然後才能使用公司入口網站來執行下列作業：
- 註冊裝置
- 存取公司應用程式和電子郵件等資源。    
條款及條件的設定是選擇性的。

您可以建立多組條款，並將它們指派給不同的群組，以達成支援不同語言等目的。

建立公司條款及條件的方式有兩種：
- 使用 Intune (如本文中所述)。
- 使用 [Azure Active Directory 使用規定功能](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou)。若要了解哪種方法最適合您，請參閱 [Choosing the right Terms solution for your organization](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409) (選擇適合您組織的條款解決方案) 部落格文章。 

## <a name="create-terms-and-conditions"></a>建立條款及條件
完成下列步驟以建立條款及條件。 顯示名稱和描述是供系統管理使用，而條款屬性則會在公司入口網站中向使用者顯示。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格上，選擇 [裝置註冊] > [條款及條件]。
2. 選擇 **[建立]**。
![正在顯示條款及條件 [建立] 按鈕的 Azure 入口網站螢幕擷取畫面](media/terms-create-terms.png)
3. 在展開的窗格上，指定下列資訊：

   - **顯示名稱**：Azure 入口網站中條款的名稱。 使用者不會看見此名稱。

   - **描述**：可協助您在 Azure 入口網站中識別這組條款的選擇性詳細資料。

4. 選擇 [定義使用條款] 旁的箭頭，以開啟 [條款及條件] 窗格，然後輸入下列資訊：

   ![終端使用者接受條款及條件畫面的螢幕擷取畫面，其中包含條款的摘要](./media/terms-summary-create.png)

   - **標題**：使用者在公司入口網站 [摘要] 上方所看見的條款名稱。
   - **條款摘要**：使用者在接受條款時，說明其意義的文字。 例如，「一旦註冊您的裝置，即表示您同意 Contoso 所訂的使用條款。 在繼續進行之前，請先仔細閱讀條款」。
   - **條款及條件**：使用者看到的條款及條件，他們必須接受或拒絕。

5. 選擇 [確定] > [建立]。

## <a name="see-how-terms-are-displayed-to-your-users"></a>了解條款對使用者的顯示方式
下列範例在管理主控台和公司入口網站中顯示 [標題] 和[條款摘要]。

![管理主控台和公司入口網站中 [標題] 和 [條款摘要] 的螢幕擷取畫面。](./media/terms-summary-terms.png)

下列範例顯示管理主控台和公司入口網站中的條款及條件。

![管理主控台和公司入口網站中條款及條件的螢幕擷取畫面。](./media/terms-properties-terms.png)

## <a name="assign-terms-and-conditions"></a>指派條款及條件

您可以將條款及條件指派給使用者群組，群組中的使用者必須先接受它們才能使用公司入口網站。

1. 在 Azure 入口網站中，選擇 [裝置註冊]，然後選擇 [條款及條件]。
2. 在條款及條件清單中，選擇您要指派的條款 > [管理] > [指派]。
![顯示指派條款及條件 [選取群組] 按鈕和 [選取] 按鈕的 Azure 入口網站 [指派群組] 窗格螢幕擷取畫面](media/terms-assign-groups.png)
3. 選擇 [選取要納入的群組] > 選擇您要指派條款的群組 > [選取]。 無法為動態群組指派條款及條件。
4. 在 [指派的群組] 窗格中，選擇 [儲存]。  條款及條件現在已指派給所選群組中的使用者。 使用者將會在下次存取公司入口網站時，收到接受條款的提示。 條款及條件只需要接受一次。 具有多部裝置的使用者不需要在每部裝置上接受。


## <a name="monitor-terms-and-conditions"></a>監視條款和條件

1. 在 Azure 入口網站中，選擇 [All services] (所有服務) > [Monitoring + Management] (監視 + 管理) > [Intune]。 
1. 在 [Intune] 窗格上，選擇 [裝置註冊] > [條款及條件]。
2. 在條款及條件清單中，選擇您要檢視接受度的條款 > [接受度報告]。

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>使用多個版本的條款和條件
您可以編輯條款及條件，並管理它們的版本。 每次當您大幅變更條款及條件時，您都應該：
- 增加版本號碼
- 要求使用者接受新的條款及條件。如果您要修正錯字或變更格式，請保留目前的版本號碼。

1. 在 Azure 入口網站中，選擇 [All services] (所有服務) > [Monitoring + Management] (監視 + 管理) > [Intune]。

2. 在 [Intune] 窗格上，選擇 [裝置註冊] > [條款及條件] > 選擇您要修改的條款及條件 > [屬性]。

4. 在 [屬性] 窗格上，選擇 [條款及條件]，然後視需要修改 [標題]、[條款摘要] 和 [條款及條件]。 如果您的變更需要使用者重新接受新的條款，請選擇 [需要使用者重新接受並將版本號碼增加至]

4.  選擇 [確定] > [儲存]。

使用者只需要接受更新後的條款及條件一次。 具有多部裝置的使用者不需要在每部裝置上接受條款及條件。
