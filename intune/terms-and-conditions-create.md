---
title: "設定 Microsoft Intune 中的條款及條件"
titleSuffix: Intune Azure preview
description: "設定使用者會在 Intune 公司入口網站中看到的條款及條件。 "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: d53e91e24988d1bc71ff8df425f0d82e0fc43b58
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---

# <a name="ensure-users-accept-company-terms-for-access"></a>確定使用者接受公司條款以進行存取

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

身為 Intune 管理員，您可以要求使用者必須先接受貴公司的條款及條件，然後才能使用公司入口網站來註冊他們的裝置並存取公司資源 (例如應用程式和電子郵件)。 條款及條件的設定是選擇性的。

您可以建立多組條款，並將它們指派給不同的群組，以達成支援不同語言等目的。

## <a name="create-terms-and-conditions"></a>建立條款及條件
完成下列步驟以建立條款及條件。 顯示名稱和描述是供系統管理使用，而條款屬性則會在公司入口網站中向使用者顯示。

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 [Intune] 刀鋒視窗上，選擇 [裝置註冊]，然後選擇 [條款及條件]。

3. 選取 [建立]。
![正在顯示條款及條件之 [建立] 按鈕的 Intune 入口網站螢幕擷取畫面](media/terms-create-terms.png)

4. 在展開的刀鋒視窗上，指定下列資訊：

   - **顯示名稱**：Intune 入口網站中條款的名稱。 使用者不會看見此名稱。

   - **描述**︰可協助您在 Intune 入口網站中識別這組條款的選擇性詳細資料。

5. 選取 [Define terms of use ]\(定義使用規定) 旁的箭頭，以開啟 [條款及條件] 刀鋒視窗，然後輸入下列資訊︰

   ![包含條款摘要之終端使用者接受條款和條件畫面的螢幕擷取畫面](./media/terms-summary-create.png)

   - **標題**：使用者在公司入口網站中看到的標題。

   - **條款摘要**︰當使用者接受條款時說明其意義的文字。 例如「一旦註冊您的裝置，即表示您同意 Contoso 所訂的使用條款。 在繼續進行之前，請先仔細閱讀條款」。

   - **條款及條件**︰使用者會看到且必須接受或拒絕的條款及條件。

6. 選取 [確定]，然後選取 [建立]。

## <a name="assign-terms-and-conditions"></a>指派條款及條件

您可以將條款及條件指派給使用者群組，群組中的使用者必須先接受它們才能使用公司入口網站。

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 [Intune] 刀鋒視窗上，選擇 [裝置註冊]，然後選擇 [條款及條件]。

3. 在條款及條件清單中，選取您要指派的條款，然後選取 [指派的群組]。
![正在顯示 [選取群組] 按鈕和指派條款及條件之 [選取] 按鈕的 Intune 入口網站 [指派群組] 刀鋒視窗螢幕擷取畫面](media/terms-assign-groups.png)

4. 按一下 [選取群組] 按鈕，然後在 [選取群組] 刀鋒視窗中，選取您要指派條款的群組，然後按一下 [選取]。

5. 在 [指派的群組] 刀鋒視窗中，按一下 [儲存]。  條款及條件現在已指派給所選群組中的使用者。 使用者將會在下次存取公司入口網站時，收到接受條款的提示。

   ![包含條款摘要之終端使用者接受條款和條件畫面的螢幕擷取畫面](./media/terms-summary-accept.png)

## <a name="monitor-a-terms-and-conditions"></a>監視條款及條件

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。 在 [Intune] 刀鋒視窗上，選擇 [裝置註冊]，然後選擇 [條款及條件]。
2. 在條款及條件清單中，選取您要檢視接受狀態的條款，然後選取 [接受狀態]。

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>使用多個版本的條款和條件
您可以編輯條款及條件，並管理它們的版本。 建議您在大幅變更條款及條件時增加版本號碼，並要求使用者重新接受。 假如您只是修正錯字或變更格式，請保留目前的版本號碼。

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 [Intune] 刀鋒視窗上，選擇 [裝置註冊]，選擇 [條款及條件]，選取您要修改的條款及條件，然後選取 [屬性]。

4. 在 [屬性] 刀鋒視窗上，選取 [條款及條件]，然後視需要修改 [標題]、[條款摘要] 和 [條款及條件]。 如果您做出的變更需要使用者重新接受新的條款，請按一下 [需要使用者重新接受並將版本號碼增加至]

4.  選取 [確定]，然後選取 [儲存]。

