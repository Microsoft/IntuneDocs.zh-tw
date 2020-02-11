---
title: 在 Microsoft Intune 中設定商務用 Windows Update - Azure | Microsoft Docs
description: 使用更新通道和功能更新原則來管理 Windows 10 軟體更新。 您可以使用 Microsoft Intune 來檢閱相容性，以及暫停商務用 Windows Update 設定的更新安裝。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e478402f826809bda4f81315d5a1a4ff6e1a8b88
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886793"
---
# <a name="manage-windows-10-software-updates-in-intune"></a>在 Intune 中管理 Windows 10 軟體更新

使用 Intune 從商務用 Windows Update 管理 Windows 10 軟體更新的安裝。

藉由使用「商務用 Windows Update」，您將可以簡化更新管理體驗。 您無須針對多組裝置核准個別的更新。 您可以藉由設定更新首度發行策略，對您的環境進行風險管理。 Intune 可讓您在裝置上[設定更新設定](windows-update-settings.md)，並可讓您將更新安裝延後。 您也可以防止裝置安裝新版 Windows 的功能，以確保裝置的穩定性，同時允許這些裝置繼續安裝品質和安全性的更新。

Intune 只會儲存更新原則指派，而不會儲存更新本身。 裝置會直接存取 Windows Update 以取得更新。

Intune 提供下列原則類型以管理更新：

- **Windows 10 更新通道**：此原則是用來設定 Windows 10 更新安裝時機的設定集合。

- **Windows 10 功能更新 (公開預覽)** ：此原則會將裝置帶入指定的 Windows 版本，並凍結這些裝置上的功能集，直到您選擇將其更新為較新的 Windows 版本。  雖然功能版本保持不變，但裝置可繼續安裝其功能版本可用的品質和安全性更新。

您可以將 Windows 10 更新通道和 Windows 10 功能更新的原則指派給裝置群組。 您可以在相同的 Intune 環境中使用這兩種原則類型，管理 Windows 10 裝置軟體更新以及建立反映商務需求的更新策略。

如需詳細資訊，請參閱[使用商務用 Windows Update 來管理更新](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb)。

## <a name="prerequisites"></a>先決條件

若要在 Intune 中使用適用於 Windows 10 裝置的 Windows 更新，必須符合下列必要條件。

- Windows 10 電腦必須執行下列 Windows 10 版本：
  - **Windows 10 更新通道**：1607 版或更新版本
  - **Windows 10 功能更新**：1703 版或更新版本

- Windows Update 支援下列 Windows 10 版本：
  - Windows 10
  - Windows 10 團隊版 - 適用於 Surface Hub 裝置 (不支援 *Windows 10 功能更新*)
  - Windows Holographic for Business

    Windows Holographic for Business 支援 Windows 更新的設定子集，包括：
    - **自動更新行為**
    - **Microsoft 產品更新**
    - **維護通道**：支援 [半年通道]  和 [半年通道 (已設定目標)]  選項。 如需詳細資訊，請參閱[管理 Windows 全像攝影版](../fundamentals/windows-holographic-for-business.md)。

  > [!NOTE]
  > **不支援的版本**：
  > - Windows 10 Mobile  
  > - Windows 10 企業版 LTSC。 商務用 Windows Update (WUfB) 目前不支援「長期服務通道」  版本。 規劃使用替代的修補方法，例如 WSUS 或 Configuration Manager。

- 在 Windows 裝置上，[意見反應與診斷]   > [診斷與使用方式資料]  必須設定為 [基本]  、[增強]  或 [完整]  。

  您可以手動設定 Windows 10 裝置的「診斷與使用狀況資料」  設定，或是使用適用於 Windows 10 與更新版本的 Intune 裝置限制設定檔。 如果您使用裝置限制設定檔，請至少將 [共用使用方式資料]  的[裝置限制設定](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry)設定為 [基本]  。 當您設定適用於 Windows 10 或更新版本的裝置限制原則時，可以在 [報告和遙測]  類別底下找到此設定。

  如需有關裝置設定檔的詳細資訊，請參閱[設定裝置限制設定](../configuration/device-restrictions-configure.md)。

## <a name="windows-10-update-rings"></a>Windows 10 更新通道

建立更新通道，其指定 Windows 即服務如何及何時使用功能與品質更新來更新您的 Windows 10 裝置。 使用 Windows 10 時，新的「功能更新」和「品質更新」會包含所有先前更新內容。 只要您已安裝最新更新，即可確保您的 Windows 10 裝置處於最新狀態。 不同於舊版 Windows，您現在必須安裝整個更新而不是部分更新。

Windows 10 更新通道支援[範圍標籤](../fundamentals/scope-tags.md)。 您可以使用範圍標籤搭配更新通道，協助您篩選及管理您所使用的組態集合。

### <a name="create-and-assign-update-rings"></a>建立及指派更新通道

1. 登入 [Microsoft 端點管理員系統管理中心]( https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [裝置]   > [Windows]   > [Windows 10 更新通道]   > [建立]  。

3. 在 [基本]  下，指定名稱、描述 (選擇性)，然後選取 [下一步]  。
  ![建立更新通道]( ./media/windows-update-for-business-configure/basics-tab.png)
  
4. 在 [更新通道設定]  中，設定符合業務需求的設定。 如需可用設定的資訊，請參閱＜Windows 更新設定＞。 設定 [更新]  和 [使用者體驗] 設定之後，請選取 [下一步]  。

5. 若要將標籤套用到更新通道，請在 [範圍標籤]  下，選取 [+ 選取範圍標籤]  以開啟 [選取標籤]  窗格。 選擇一或多個標籤，然後按一下 [選取]  將其新增到更新通道並返回 [範圍標籤]  頁面。

   當就緒時，請選取 [下一步]  以繼續到 [指派]  。

6. 在 [指派]  下，選擇 [+ 選取要納入的群組]  ，然後將更新通道指派給一或多個群組。 使用 [+ 選取要排除的群組]  以微調指派。 選取 [下一步]  以繼續進行操作。

7. 在 [檢閱 + 建立]  下檢閱設定，並在準備儲存 Windows 10 更新通道時選取 [建立]  。 新的更新通道會隨即顯示在更新通道清單中。

### <a name="manage-your-windows-10-update-rings"></a>管理 Windows 10 更新通道

在入口網站中，巡覽至 [裝置]   > [Windows]   > [Windows 10 更新通道]  ，然後選取要管理的原則。  原則即會開啟其 [概觀]  頁面。

在此頁面中，您可以檢視通道指派狀態，並可從 [概觀] 窗格的頂端選取下列動作來管理更新通道：

- [刪除](#delete)
- [暫停](#pause)
- [繼續](#resume)
- [延長](#extend)
- [解除安裝](#uninstall)

![可執行的動作](./media/windows-update-for-business-configure/overview-actions.png)

#### <a name="delete"></a>刪除

選取 [刪除]  可停止強制執行所選 Windows 10 更新通道的設定。 刪除通道會從 Intune 移除其設定，讓 Intune 不再適用，並強制執行這些設定。

從 Intune 刪除通道不會修改已獲指派更新通道之裝置上的設定。  相反地，裝置會保留其目前的設定。 裝置不會維持它們先前曾保存之設定的歷史記錄。 裝置也可以從維持作用中的額外更新通道接收設定。

##### <a name="to-delete-a-ring"></a>若要刪除通道

1. 檢視更新通道的 [概觀] 頁面時，選取 [刪除]  。
2. 選取 [確定]  。

#### <a name="pause"></a>暫停

選取 [暫停]  可以從您暫停通道起，防止獲指派的裝置接收功能更新或品質更新最多 35 天。 經過天數上限之後，暫停功能會自動過期，裝置將掃描 Windows Updates 尋找可用的更新。 進行此掃描之後，您可以再次暫停更新。
如果您繼續使用已暫停的更新通道，然後再次暫停該通道，則暫停期間會重設為 35 天。

##### <a name="to-pause-a-ring"></a>若要暫停通道

1. 檢視更新通道的 [概觀] 頁面時，選取 [暫停]  。
2. 選取 [功能]  或 [品質]  可暫停該類型的更新，然後選取 [確定]  。
3. 暫停一個更新類型之後，您可以再次選取 [暫停] 以暫停其他更新類型。

暫停某個更新類型時，該通道的 [概觀] 窗格會顯示在多少天之後，該更新類型才會繼續。

> [!IMPORTANT]
> 當您發出暫停命令時，裝置會在下次簽入服務時收到此命令。 也有可能在確認更新之前，就已經執行排定的更新。 此外，當您發出暫停命令時如果目標裝置已關閉，當您開啟裝置時，它可能會下載並安裝排定的更新，然後再去向 Intune 確認。

#### <a name="resume"></a>繼續

當更新通道遭到暫停時，您可以選取 [繼續]  ，將該通道的功能與品質更新還原為作用中的作業。 繼續某個更新通道之後，您可以再次暫停該通道。

##### <a name="to-resume-a-ring"></a>若要繼續通道

1. 檢視已暫停之更新通道的 [概觀] 頁面時，選取 [繼續]  。
2. 從可用的選項中選取，以繼續執行 [功能]  或 [品質]  更新，然後選取 [確定]  。
3. 繼續一個更新類型之後，您可以再次選取 [繼續] 以繼續其他更新類型。

#### <a name="extend"></a>擴充  

當更新通道遭到暫停時，您可以選取 [延長]  ，將該更新通道之功能與品質更新的暫停期間重設為 35 天。

##### <a name="to-extend-the-pause-period-for-a-ring"></a>若要延長通道的暫停期間

1. 檢視已暫停之更新通道的 [概觀] 頁面時，選取 [延長]  。
2. 從可用的選項中選取，以繼續執行 [功能]  或 [品質]  更新，然後選取 [確定]  。
3. 延長一個更新類型的暫停期間之後，您可以再次選取 [延長] 來延長其他更新類型。

#### <a name="uninstall"></a>解除安裝  

Intune 系統管理員可以使用 [解除安裝]  ，針對作用中或已暫停的更新通道，解除安裝 (回復) 最新的*功能*更新或最新的*品質*更新。 解除安裝一個類型之後，您可以再解除安裝其他類型。 Intune 不支援或管理使用者解除安裝更新的能力。  

> [!IMPORTANT]
> 當您使用 [解除安裝]  選項時，Intune 會立即將解除安裝要求傳遞到裝置。
>
> - Windows 裝置會在收到 Intune 原則中的變更時開始移除更新。 更新移除不限於維護排程，即使它們已設定為更新通道的一部分時也可以執行。
> - 若更新移除要求必須重新啟動裝置，裝置會重新啟動，而不提供裝置使用者延遲選項。

若要成功解除安裝：

- 裝置必須執行 Windows 10 的 2018 年 4 月更新 (1803 版) 或更新版本。

裝置必須已經安裝最新的更新。 更新是累積的，因此安裝最新更新的裝置將有最新的功能與品質更新。 例如，當您使用此選項時，如果您在 Windows 10 電腦上發現重大問題，可以回復到上一個更新。

使用 [解除安裝] 時，請考量下列各項：

- 解除安裝功能或品質更新只適用於裝置所在的維護通道。

- 為功能或品質更新使用解除安裝將會觸發一個原則，以還原 Windows 10 電腦上的上一個更新。

- 在 Windows 10 裝置上成功回復品質更新之後，裝置使用者會繼續在 [Windows 設定]   > [更新]   > [更新記錄]  中看到列出的更新。

- 特別針對功能更新，您可以解除安裝更新的時間限制為 2-60 天。 這段期間是由更新通道的 [設定功能更新解除安裝期間 (2 - 60 天)]  更新設定所設定。 若更新安裝的時間超過所設定的解除安裝期間，即無法復原已安裝在裝置上的功能更新。

  例如，假設更新通道具有 20 天的功能更新解除安裝期間。 在 25 天之後，您決定要復原上次的功能更新，並使用 [解除安裝] 選項。  已安裝功能更新超過 20 天的裝置無法解除安裝，因為它們已在維護當中移除了必要的位元。 不過，僅安裝功能更新 19 天的裝置，只要在尚未超過 20 天的解除安裝期間成功簽入以接收解除安裝命令，就可以解除安裝更新。

如需有關 Windows Update 原則的詳細資訊，請參閱 Windows 用戶端管理文件中的[更新 CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp)。

##### <a name="to-uninstall-the-latest-windows-10-update"></a>若要解除安裝最新的 Windows 10 更新

1. 檢視已暫停之更新通道的 [概觀] 頁面時，選取 [解除安裝]  。
2. 從可用的選項中選取，以解除安裝 [功能]  或 [品質]  更新，然後選取 [確定]  。
3. 觸發一個更新類型的解除安裝之後，您可以再次選取 [解除安裝] 以解除安裝剩餘的更新類型。

## <a name="windows-10-feature-updates"></a>Windows 10 功能更新

*這項功能處於公開預覽狀態。*

您可以使用「Windows 10 功能更新」  選取希望裝置保持的 Windows 功能版本，例如 Windows 10 1803 版或1809 版。 您可將功能層級設定為 1803 版或更新版本。

當裝置收到 Windows 10 功能更新原則時：

- 裝置會更新至原則指定的 Windows 版本。 已執行較新 Windows 版本的裝置則仍保持為其目前版本。 透過凍結版本，裝置功能集會在原則期間維持穩定。

- 已安裝的 Windows 版本雖保持設定，但裝置仍可在該版本支援期間收到並安裝其 Windows 版本的品質和安全性更新，這有助於讓裝置保持在最新且安全的狀態。

- 不同於使用 35 天後過期的更新通道「暫停」  ，Windows 10 功能更新原則仍然有效。 在修改或移除 Windows 10 功能更新原則之前，裝置都不會安裝新的 Windows 版本。 如果您編輯原則來指定較新的版本，則裝置就可以從該 Windows 版本安裝功能。

### <a name="prerequisites-for-windows-10-feature-updates"></a>Windows 10 功能更新的先決條件

若要在 Intune 中使用 Windows 10 功能更新，必須符合下列先決條件。

- 裝置必須已在 Intune MDM 中註冊，而且必須已加入 Azure AD 或已註冊 Azure AD。
- 若要搭配 Intune 使用「功能更新」原則，裝置必須開啟遙測，並具有[「基本」  ](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry)的最低設定。 遙測是作為[裝置限制原則](../configuration/device-restrictions-configure.md)的一部分，在 [報告和遙測]  底下設定。
  
  接收「功能更新」原則，且將遙測設定為 [未設定]  (代表它已關閉) 的裝置，可能會安裝比在「功能更新」原則中所定義的 Windows 版本還要新的版本。 隨著此功能即將正式推出，我們也正在檢閱要求遙測的必要條件。

### <a name="limitations-for-windows-10-feature-updates"></a>Windows 10 功能更新的限制

- 當您將「Windows 10 功能更新」  原則部署到同時也接收「Windows 10 更新通道」  原則的裝置時，請檢閱更新通道的下列設定：
  - [功能更新延遲期間 (天)]  必須設為 **0**。
  - 更新通道的功能更新必須為「正在執行」  。 不得為暫停。

- Windows 10 功能更新原則無法在 Autopilot 全新體驗 (OOBE) 期間套用，而且只會在裝置完成佈建 (通常為一天) 之後、於第一次 Windows Update 掃描時套用。

### <a name="create-and-assign-windows-10-feature-updates"></a>建立並指派 Windows 10 功能更新

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [裝置]   > [Windows]   > [Windows 10 功能更新]   > [建立]  。

3. 在 [基本]  下，指定名稱、描述 (選擇性)，然後針對 [要部署的功能更新]  選取想要的 Windows 版本功能集，然後選取 [下一步]  。

4. 在 [指派]  下，選擇 [+ 選取要包含的群組]  ，然後將功能更新部署指派給一或多個群組。 選取 [下一步]  以繼續進行操作。

5. 在 [檢閱 + 建立]  下檢閱設定，並在準備儲存 Windows 10 功能更新原則時選取 [建立]  。  

### <a name="manage-windows-10-feature-updates"></a>管理 Windows 10 功能更新

在系統管理中心中，移至 [裝置]   > [Windows]   > [Windows 10 功能更新]  ，然後選取要管理的原則。 原則即會開啟其 [概觀]  窗格。

您可以在此窗格中：

- 選取 [刪除]  以從 Intune 刪除原則，並從裝置中移除此原則。
- 選取 [屬性]  以修改部署。  在 [屬性]  窗格中，選取 [編輯]  以開啟 [Deployment settings or Assignments] \(部署設定或指派\)  ，即可在此修改部署。
- 選取 [End user update status] \(終端使用者更新狀態\)  以檢視原則的相關資訊。

## <a name="validation-and-reporting-for-windows-10-updates"></a>Windows 10 更新的驗證和報告

針對 Windows 10 更新通道與 Windows 10 功能更新，請使用[更新的 Intune 合規性報告](../windows-update-compliance-reports.md)來監視裝置的更新狀態。 此解決方案搭配您的 Azure 訂用帳戶使用[更新合規性](https://docs.microsoft.com/windows/deployment/update/update-compliance-monitor) \(部分機器翻譯\)。

## <a name="next-steps"></a>後續步驟

[Intune 支援的 Windows 更新設定](../windows-update-settings.md)

[針對 Windows 10 更新通道進行疑難排解](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046) \(英文\)