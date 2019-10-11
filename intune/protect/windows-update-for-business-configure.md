---
title: 在 Microsoft Intune 中設定商務用 Windows Update - Azure | Microsoft Docs
description: 在 Windows 10 裝置上使用 Microsoft Intune 來更新設定檔中的 [軟體更新] 設定，以在 [商務用 Windows Update] 設定中建立更新通道、檢閱合規性及暫停更新。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5a9ecc1cabb00122d2812580b663fcd0c1dfabc3
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728087"
---
# <a name="manage-software-updates-in-intune"></a>管理 Intune 中的軟體更新

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

使用 Intune 定義可指定 Windows 即服務如何及何時更新您 Windows 10 裝置的更新通道。 更新通道是您指派給裝置群組的原則。 藉由使用更新響鈴，您可以建立可反映您業務需求的更新策略。 如需詳細資訊，請參閱[使用商務用 Windows Update 來管理更新](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb)。

使用 Windows 10 時，新的「功能更新」和「品質更新」會包含所有先前更新內容。 只要您已安裝最新更新，即可確保您的 Windows 10 裝置處於最新狀態。 不同於舊版 Windows，您現在必須安裝整個更新而不是部分更新。


藉由使用「商務用 Windows Update」，您將可以簡化更新管理體驗。 您無須針對多組裝置核准個別的更新。 您可以藉由設定更新首度發行策略，對您的環境進行風險管理。 Intune 可讓您在裝置上[設定更新設定](../windows-update-settings.md)，並可讓您將更新安裝延後。 Intune 不會儲存更新，只會儲存更新原則指派。 裝置會直接存取 Windows Update 以取得更新。 在安裝 Windows 10 更新時設定的這組設定稱為 *Windows 10 更新通道*。

Windows 10 更新通道支援[範圍標籤](../fundamentals/scope-tags.md)。 您可以使用範圍標籤搭配更新通道，協助您篩選及管理您所使用的組態集合。

## <a name="prerequisites"></a>必要條件  

若要在 Intune 中使用適用於 Windows 10 裝置的 Windows 更新，必須符合下列必要條件。  

- Windows 10 電腦必須至少執行 Windows 10 專業版並已安裝 Windows 年度更新或更新版本 (1607 版或更新版本)
- Windows Update 支援下列 Windows 10 版本：
  - Windows 10
  - Windows 10 Team (適用於 Surface Hub 裝置)
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

- 如果您使用 Azure 傳統入口網站，請[將您的設定移轉到 Azure 入口網站](#migrate-update-settings-to-the-azure-portal)。  


## <a name="create-and-assign-update-rings"></a>建立及指派更新通道

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 選取 [軟體更新]   > [Windows 10 更新通道]   > 建立  。
4. 輸入名稱、描述 (選擇性)，然後選擇 [設定]  。
5. 在 [設定]  中，設定符合您業務需求的設定。 如需可用設定的相關資訊，請參閱 [Windows 更新設定](../windows-update-settings.md)。  
6. 完成時，選取 [確定]  。 在 [建立更新通道]  中，選取 [建立]  。 新的更新響鈴會隨即顯示在更新響鈴清單中。
7. 若要指派通道，請在更新通道清單中選取通道，然後在 [\<通道名稱>] 索引標籤上，選擇 [指派]  。
8. 使用 [包含]  和 [排除]  索引標籤定義要獲指派 [通道] 的群組，然後選取 [儲存]  以完成指派。

## <a name="manage-your-windows-10-update-rings"></a>管理 Windows 10 更新通道
在入口網站中，您可以選取 Windows 10 更新通道以開啟其 [概觀]  窗格。 您可以從此窗格檢視通道指派狀態，並採取其他動作來管理通道。 
### <a name="to-view-an-updates-rings-overview-pane"></a>若要檢視更新通道的 [概觀] 窗格： 
1. 登入 Azure 入口網站。
2. 瀏覽至 [Intune]   > [軟體更新]   > [Windows 10 更新通道]  。
3. 選取您要檢視或管理的更新通道。  

除了檢視指派狀態之外，您還可以從 [概觀] 窗格的頂端選取下列動作來管理更新通道：  
- [刪除](#delete)  
- [暫停](#pause)  
- [繼續](#resume)  
- [延長](#extend)  
- [解除安裝](#uninstall)  

![可執行的動作](./media/windows-update-for-business-configure/overview-actions.png)

### <a name="delete"></a>刪除  
選取 [刪除]  可停止強制執行所選 Windows 10 更新通道的設定。 刪除通道會從 Intune 移除其設定，讓 Intune 不再適用，並強制執行這些設定。  

從 Intune 刪除通道不會修改已獲指派更新通道之裝置上的設定。  相反地，裝置會保留其目前的設定。 這是因為裝置不會維護先前設定的歷史記錄，而且裝置可能會從仍然作用中的其他更新通道接收設定。  

#### <a name="to-delete-a-ring"></a>若要刪除通道  
1. 檢視更新通道的 [概觀] 頁面時，選取 [刪除]  。  
2. 選取 [確定]  。  

### <a name="pause"></a>暫停  
選取 [暫停]  可以從您暫停通道起，防止獲指派的裝置接收功能更新或品質更新最多 35 天。 經過天數上限之後，暫停功能會自動過期，裝置將掃描 Windows Updates 尋找可用的更新。 在這次掃描後，您可以再一次暫停更新。 如果您繼續使用已暫停的更新通道，然後再次暫停該通道，則暫停期間會重設為 35 天。  

#### <a name="to-pause-a-ring"></a>若要暫停通道  
1. 檢視更新通道的 [概觀] 頁面時，選取 [暫停]  。  
2. 選取 [功能]  或 [品質]  可暫停該類型的更新，然後選取 [確定]  。  
3. 暫停一個更新類型之後，您可以再次選取 [暫停] 以暫停其他更新類型。  

暫停某個更新類型時，該通道的 [概觀] 窗格會顯示在多少天之後，該更新類型才會繼續。

> [!IMPORTANT]  
> 當您發出暫停命令時，裝置會在下次簽入服務時收到此命令。 也有可能在確認更新之前，就已經執行排定的更新。 此外，當您發出暫停命令時如果目標裝置已關閉，當您開啟裝置時，它可能會下載並安裝排定的更新，然後再去向 Intune 確認。

### <a name="resume"></a>繼續  
當更新通道遭到暫停時，您可以選取 [繼續]  ，將該通道的功能與品質更新還原為作用中的作業。 繼續某個更新通道之後，您可以再次暫停該通道。  

#### <a name="to-resume-a-ring"></a>若要繼續通道  
1. 檢視已暫停之更新通道的 [概觀] 頁面時，選取 [繼續]  。  
2. 從可用的選項中選取，以繼續執行 [功能]  或 [品質]  更新，然後選取 [確定]  。  
3. 繼續一個更新類型之後，您可以再次選取 [繼續] 以繼續其他更新類型。  

### <a name="extend"></a>擴充  
當更新通道遭到暫停時，您可以選取 [延長]  ，將該更新通道之功能與品質更新的暫停期間重設為 35 天。  

#### <a name="to-extend-the-pause-period-for-a-ring"></a>若要延長通道的暫停期間  
1. 檢視已暫停之更新通道的 [概觀] 頁面時，選取 [延長]  。 
2. 從可用的選項中選取，以繼續執行 [功能]  或 [品質]  更新，然後選取 [確定]  。  
3. 延長一個更新類型的暫停期間之後，您可以再次選取 [延長] 來延長其他更新類型。  

### <a name="uninstall"></a>解除安裝  
Intune 系統管理員可以使用 [解除安裝]  ，針對作用中或已暫停的更新通道，解除安裝 (回復) 最新的*功能*更新或最新的*品質*更新。 解除安裝一個類型之後，您可以再解除安裝其他類型。 Intune 不支援或管理使用者解除安裝更新的能力。  

若要成功解除安裝：  
- 裝置必須執行 Windows 10 的 2018 年 4 月更新 (1803 版) 或更新版本。  

裝置必須已經安裝最新的更新。 更新是累積的，因此安裝最新更新的裝置將有最新的功能與品質更新。 例如，當您使用此選項時，如果您在 Windows 10 電腦上發現重大問題，可以回復到上一個更新。  

使用 [解除安裝] 時，請考量下列各項：  
- 解除安裝功能或品質更新只適用於裝置所在的維護通道。  

- 為功能或品質更新使用解除安裝將會觸發一個原則，以還原 Windows 10 電腦上的上一個更新。  

- 在 Windows 10 裝置上成功回復品質更新之後，使用者會繼續在 [Windows 設定]   > [更新]   > [更新記錄]  中看到列出的更新。  

- 若是功能更新，具體來說，您可以解除安裝功能更新的時間僅限於 2-60 天，這是更新通道的更新設定 [設定功能更新解除安裝期間 (2 到 60 天)]  所設定的。 若功能更新安裝的時間已超過所設定的解除安裝期間，您就無法復原已安裝在裝置上的功能更新。  

  例如，假設更新通道具有 20 天的功能更新解除安裝期間。 在 25 天之後，您決定要復原上次的功能更新，並使用 [解除安裝] 選項。  已安裝功能更新超過 20 天的裝置無法解除安裝，因為它們已在維護時移除了必要的位元。 不過，僅安裝功能更新 19 天的裝置，只要它們在尚未超過 20 天的解除安裝期間成功簽入以接收解除安裝命令，就可以將更新解除安裝。  

如需有關 Windows Update 原則的詳細資訊，請參閱 Windows 用戶端管理文件中的[更新 CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp)。  

#### <a name="to-uninstall-the-latest-windows-10-update"></a>若要解除安裝最新的 Windows 10 更新  
1. 檢視已暫停之更新通道的 [概觀] 頁面時，選取 [解除安裝]  。  
2. 從可用的選項中選取，以解除安裝 [功能]  或 [品質]  更新，然後選取 [確定]  。  
3. 觸發一個更新類型的解除安裝之後，您可以再次選取 [解除安裝] 以解除安裝剩餘的更新類型。  

## <a name="migrate-update-settings-to-the-azure-portal"></a>將更新設定移轉至 Azure 入口網站  
Azure 傳統入口網站在裝置組態設定檔中也有一些其他 Windows 10 更新設定。 如果您在移轉至 Azure 入口網站時設定了這其中任何設定，則強烈建議您執行下列動作：  

1. 在 Azure 入口網站上，以您需要的設定建立 Windows 10 更新響鈴。 Azure 入口網站已不再支援 [允許發行前版本功能]  設定，因其不再適用於最新的 Windows 10 組建。 當您建立更新響鈴時，可以設定另外三個設定，以及其他 Windows 10 更新設定。  

   > [!NOTE]  
   > 移轉之後，在傳統入口網站中建立的 Windows 10 更新設定不會顯示在 Azure 入口網站中。 不過，系統會套用這些設定。 如果您移轉這當中的任何設定，並從 Azure 入口網站中編輯所移轉的原則，系統就會將這些設定從原則中移除。  

2. 刪除傳統入口網站中的更新設定。 移轉至 Azure 入口網站並將相同設定新增至更新通道之後，您必須在傳統入口網站中刪除這些設定，以避免任何可能發生的原則衝突。 例如，當相同的設定具有不同的設定值時，就會發生衝突。 您很難得知此狀況，因為在傳統入口網站中設定的設定不會顯示在 Azure 入口網站中。  

## <a name="next-steps"></a>後續步驟
[Intune 支援的 Windows 更新設定](../windows-update-settings.md)  

[更新的 Intune 合規性報表](../windows-update-compliance-reports.md)

[針對 Windows 10 更新通道進行疑難排解](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046) \(英文\)

