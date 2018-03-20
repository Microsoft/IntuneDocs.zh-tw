---
title: "在 Intune 中設定商務用 Windows Update 的設定"
titleSuffix: Azure portal
description: "了解如何在 Intune 中設定商務用 Windows Update 的設定，以控制 Windows 10 裝置的更新。"
keywords: 
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: coryfe
ms.suite: ems
ms.openlocfilehash: d6ccda2aba0b1383de6c38b7a2fdcfdc742d0e15
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="manage-software-updates"></a>管理軟體更新

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

「Windows 即服務」是更新 Windows 10 裝置的方式。 使用 Windows 10，新的「功能更新」和「品質更新」會包含所有先前更新的內容。 這表示只要您安裝了最新的更新，就能確定您的 Windows 10 裝置已更新至最新版。 不同於舊版 Windows，您現在必須安裝整個更新而不是部分更新。

使用商務用 Windows Update，可以簡化更新管理體驗，因此您不需要核准裝置群組的個別更新。 只要設定更新首度發行策略，您還是可以管理環境中的風險，Windows Update 會確保在適當的時間安裝更新。 Microsoft Intune 可讓您在裝置上設定更新設定，並可讓您延後更新的安裝。 Intune 不會儲存更新，只會儲存更新原則指派。 裝置會直接存取 Windows Update 以取得更新。 使用 Intune 來設定及管理 **Windows 10 更新通道**。 更新響鈴是一組包含何時及如何安裝 Windows 10 更新的設定。 例如，您可以進行下列設定：

- **Windows 10 維護通道**：選擇您希望裝置的群組要從半年通道 (已設定目標) 或半年通道收到更新。  
- **延遲設定**︰設定更新延遲設定，以延遲裝置群組的更新安裝。 使用這些設定讓您能推展階段性的更新，以便全程檢查過程進度。
- **暫停**︰如果您在更新首度發行期間發現問題，延後更新的安裝。
- **維護期間**︰設定可以安裝更新的時數。
- **更新類型**︰選擇要安裝的更新類型。 例如，高品質更新、功能更新或驅動程式。
- **安裝行為**︰這會設定更新的安裝方式。 例如，裝置會在安裝後自動重新啟動嗎？
- **同儕下載**︰您可以指定是否要設定同儕下載。 如有設定，當裝置完成下載更新時，其他裝置可以從該裝置下載更新。 這會加速下載程序。

建立更新響鈴之後，將它們指派給裝置群組。 藉由使用更新響鈴，您可以建立可反映您業務需求的更新策略。 如需詳細資訊，請參閱[使用商務用 Windows Update 來管理更新](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb)。

## <a name="before-you-start"></a>開始之前

- 若要更新 Windows 10 電腦，這些電腦必須至少執行 Windows 10 專業版並已安裝 Windows 年度更新。

- Windows Update 支援下列 Windows 10 版本：
    - Windows 10
    - Windows 10 Team (適用於 Surface Hub 裝置)
    - [Windows Holographic for Business](#windows-holographic-for-business-support)

 不支援執行 Windows 10 行動裝置版的裝置。

- 在 Windows 裝置上，[意見與診斷]  >  [診斷與使用方式資料] 必須至少設定為 [基本]。

    ![診斷與使用方式資料的 Windows 設定](./media/telemetry-basic.png)

    您可以手動設定此設定，或使用 Intune 裝置限制設定檔 (用於 Windows 10 和更新版本)。 若要這樣做，請至少將 [一般]  >  [提交診斷資料] 的設定設為 [基本]。 如需有關裝置設定檔的詳細資訊，請參閱[如何設定裝置限制設定](device-restrictions-configure.md)。

- 在 Intune 管理主控台中，有四種設定可控制軟體更新行為。 這些設定是 Windows 10 桌上電腦和行動裝置上，一般組態原則的一部分：
    - **允許自動更新**
    - **允許發行前版本功能**
    - **已排程的安裝日**
    - **已排程的安裝時間**

  傳統入口網站在裝置組態設定檔中也有一些其他的 Windows 10 更新設定。 當您移轉至 Azure 入口網站時，如果在 Intune 管理主控台中設定了這些設定，強烈建議您執行下列操作︰

1. 在 Azure 入口網站上，以您需要的設定建立 Windows 10 更新響鈴。 Azure 入口網站已不再支援 [允許搶鮮版功能] 設定，因其不再適用於最新的 Windows 10 組建。 當您建立更新響鈴時，可以設定另外三個設定，以及其他 Windows 10 更新設定。

  > [!NOTE]
  > 移轉之後，在傳統入口網站中建立的 Windows 10 更新設定不會顯示在 Azure 入口網站中。 不過，這些設定仍會繼續套用。 如果您有移轉這些設定，並在 Azure 入口網站中編輯移轉的原則，這些設定將會從原則中移除。

2. 刪除傳統入口網站中的更新設定。 移轉至 Azure 入口網站，並新增相同設定到更新響鈴之後，您必須在傳統入口網站中刪除這些設定，以避免任何可能發生的原則衝突。 例如，相同的設定若使用不同的值將會造成衝突且無從得知，因為在傳統入口網站中設定的設定不會顯示在 Azure 入口網站。

## <a name="how-to-create-and-assign-update-rings"></a>如何建立及指派更新響鈴

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [軟體更新]。
4. 在 [軟體更新] 窗格中，選擇 [管理]  >  [Windows 10 更新響鈴]。
5. 在顯示更新響鈴清單的窗格中，選擇 [建立]。
6. 在 [建立更新響鈴] 窗格中，提供更新響鈴的名稱和描述 (選擇性)，然後選擇 [設定 - 設定]。
7. 在 [設定] 窗格中，設定下列資訊：
    - **維護通道**：設定裝置接收 Windows 更新的通道 (半年通道 (已設定目標) 或半年通道)。
    - **Microsoft 產品更新**︰選擇是否要從 Microsoft Update 掃描應用程式更新。
    - **Windows 驅動程式**︰選擇是否要在更新期間排除 Windows Update 驅動程式。
    - **自動更新行為**︰選擇要如何管理自動更新行為，以進行掃描、下載及安裝更新。 如需詳細資訊，請參閱 [Update/AllowAutoUpdate](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#update-allowautoupdate)。
    - **品質更新延遲期間 (天)** - 指定品質更新延遲的天數。 最多可以延遲接收「品質更新」至其發行後 30 天。  

    品質更新通常會修正和改進現有的 Windows 功能，而且通常在每個月的第一個星期二發行，不過 Microsoft 也可能在任何時間發行。 您可以定義在品質更新發行後，「是否」要延遲以及延遲「多久」接收品質更新。

    - **功能更新延遲期間 (天)** - 指定功能更新延遲的天數。 您可以延遲接收「功能更新」至其發行後 180 天。

    功能更新一般是 Windows 的新功能。 進行 [維護通道] 設定之後 (半年通道 (已設定目標) 或半年通道)，您接著可以定義在 Microsoft 於 Windows Update 發行「功能更新」後，是否要延遲接收「功能更新」，以及要延遲多久。

    例如：**若維護通道已設為 [半年通道 (已設定目標)] 且延遲期間為 30 天**：可以假設「功能更新 X」會在 1 月以半年通道 (已設定目標) 首度公開發行。 裝置要到 2 月 (30 天後) 才會接收更新。

    **若維護通道已設為 [半年通道] 且延遲期間為 30 天**：可以假設「功能更新 X」會在 1 月以半年通道 (已設定目標) 首度公開發行。 四個月後 (4 月)，「功能更新 X」才會發行到半年通道。 裝置將會在此半年通道發行的 30 天後收到「功能更新 X」，並將在 5 月更新。

    - **傳遞最佳化下載方法** - 選擇裝置將下載 Windows 更新的方法。 如需詳細資訊，請參閱 [DeliveryOptimization/DODownloadMode](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode)。
1. 完成設定後，按一下 [確定]，然後在 [建立更新響鈴] 窗格中按一下 [建立]。

新的更新響鈴會隨即顯示在更新響鈴清單中。

1. 若要指派更新響鈴，在更新響鈴清單中，選取響鈴，在 [<響鈴名稱>] 索引標籤中選擇 [指派]。
2. 在下一個索引標籤中，選擇 [Select groups to include] (選取要包含的群組)，然後選擇要指派此響鈴的群組。
3. 完成之後，選擇 [選取] 來完成這項指派。

## <a name="update-compliance-reporting"></a>更新合規性報告
您可以在 Intune 中檢視更新合規性，或使用 Operations Management Suite (OMS) 中稱為 Update Compliance 的免費解決方案。

### <a name="review-update-compliance-in-intune"></a>在 Intune 中檢視更新合規性 
<!-- 1352223 -->
檢視原則報告，以檢視您已設定之 Windows 10 更新通道的部署狀態。 
1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [軟體更新]。
4. 在 [軟體更新] 窗格中，選擇 [概觀]。 您可以從這裡看到您指派之任何更新通道的狀態一般資訊。
5. 請開啟下列其中一個報表： 
     
   **針對所有的部署通道：**
   1. 在 [軟體更新] > [Windows 10 更新通道] 窗格中。 
   2. 在 [監視] 區段，選擇 [依更新通道別部署狀態]。
                   
   **針對特定的部署通道：** 
   1. 在 軟體更新 > Windows 10 更新通道 窗格中，選擇要檢視的部署通道。
   2. 在 [監視] 區段中，從下列報表選擇，以檢視更新通道的更多詳細資訊：
      - **裝置狀態**
      - **使用者狀態**

### <a name="review-update-compliance-using-oms"></a>使用 OMS 檢視更新合規性
您可以使用 Operations Management Suite (OMS) 中的免費解決方案 Update Compliance 來監視 Windows 10 更新的首度發行。 如需詳細資訊，請參閱[使用Update Compliance 來監視 Windows Updates](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor)。 當您使用此解決方案時，可以將商業識別碼部署至任何您用 Intune 管理、且要報告更新合規性的 Windows 10 裝置。

在 Intune 主控台中，您可以使用自訂原則的 OMA-URI 設定來設定商業識別碼。 如需詳細資訊，請參閱 [Microsoft Intune 中 Windows 10 裝置的 Intune 原則設定](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)。   

用於設定商業識別碼的 OMA-URI (區分大小寫) 路徑是：./Vendor/MSFT/DMClient/Provider/ProviderID/CommercialID

例如，您可以在 [新增或編輯 OMA-URI 設定] 中使用下列值：

- **設定名稱**：Windows Analytics 商業識別碼
- **設定描述**︰設定 Windows Analytics 解決方案的商業識別碼
- **OMA-URI** (區分大小寫)：./Vendor/MSFT/DMClient/Provider/ProviderID/CommercialID
- **資料類型**：字串
- **值**：<使用 OMS 工作區中的 [Windows 遙測] 索引標籤上顯示的 GUID>

![診斷與使用方式資料的 Windows 設定](./media/commID.png)

## <a name="how-to-pause-updates"></a>如何暫停更新
您可以讓裝置暫停接收功能更新或品質更新一段期間，自您暫停更新起最多 35 天。 經過天數上限之後，暫停功能會自動過期，裝置將掃描 Windows Updates 尋找可用的更新。 在這次掃描後，您可以再一次暫停更新。
1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [軟體更新]。
4. 在 [軟體更新] 窗格中，選擇 [管理]  > [Windows 10 更新響鈴]。
5. 在顯示更新響鈴清單的窗格中，選擇您要暫停的響鈴，然後選擇 ...  > 暫停品質 > 或 暫停功能，取決於您要暫停的更新類型。

> [!IMPORTANT]
> 在您發出暫停命令後，裝置會在下次向服務確認時收到此命令。 也有可能在確認更新之前，就已經執行排定的更新。
> 此外，當您發出暫停命令時如果目標裝置已關閉，當您開啟裝置時，它可能會下載並安裝排定的更新，然後再去向 Intune 確認。

## <a name="windows-holographic-for-business-support"></a>Windows Holographic for Business 支援

Windows Holographic for Business 支援下列設定：

- **自動更新行為**
- **Microsoft 產品更新**
- **維護通道**