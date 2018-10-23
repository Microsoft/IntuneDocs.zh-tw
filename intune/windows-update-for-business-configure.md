---
title: 在 Microsoft Intune 中設定商務用 Windows Update - Azure | Microsoft Docs
description: 在 Windows 10 裝置上使用 Microsoft Intune 來更新設定檔中的 [軟體更新] 設定，以在 [商務用 Windows Update] 設定中建立更新通道、檢閱合規性及暫停更新。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 6/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
ms.openlocfilehash: d709681519f2e68d38958d6ec2082b762e22cf60
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2018
ms.locfileid: "49425150"
---
# <a name="manage-software-updates-in-intune"></a>管理 Intune 中的軟體更新

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

「Windows 即服務」是更新 Windows 10 裝置的方式。 使用 Windows 10 時，新的「功能更新」和「品質更新」會包含所有先前更新的內容。 只要您已安裝最新更新，即可確保您的 Windows 10 裝置處於最新狀態。 不同於舊版 Windows，您現在必須安裝整個更新而不是部分更新。

藉由使用「商務用 Windows Update」，您將可以簡化更新管理體驗。 您無須針對多組裝置核准個別的更新。 您可以藉由設定更新首度發行策略，對您的環境進行風險管理。 而 Windows Update 則會確保在適當的時間安裝更新。 Microsoft Intune 可讓您在裝置上設定更新設定，並可讓您將更新安裝延後。 Intune 不會儲存更新，只會儲存更新原則指派。 裝置會直接存取 Windows Update 以取得更新。 使用 Intune 來設定及管理 **Windows 10 更新通道**。 更新通道是一組設定，用來設定安裝 Windows 10 更新的時機和方式。 例如，您可以進行下列設定：

- **Windows 10 維護通道**：選擇您希望裝置群組從中收到更新的維護通道。 下列是可用的通道： 
  - 半年通道
  - 半年通道 (已設定目標)
  - Windows 測試人員 - 快
  - Windows 測試人員 - 慢
  - 發行 Windows 測試人員 
      
  如需有關可用維護通道的詳細資料，請參閱 [Windows 即服務概觀](https://docs.microsoft.com/windows/deployment/update/waas-overview#servicing-channels)。
- **延遲設定**︰設定更新延遲設定，以延遲裝置群組的更新安裝。 請使用這些設定來分階段進行更新首度發行，以便全程檢閱進度。
- **暫停**︰如果您在更新首度發行期間發現問題，延後更新的安裝。
- **維護期間**︰設定可以安裝更新的時數。
- **更新類型**︰選擇要安裝的更新類型。 例如，高品質更新、功能更新或驅動程式。
- **安裝行為**︰設定安裝更新的方式。 例如，裝置會在安裝後自動重新啟動嗎？
- **對等下載**︰您可以選擇設定對等下載。 如有設定，當裝置完成下載更新時，其他裝置可以從該裝置下載更新。 此設定可加速下載程序。

建立更新響鈴之後，將它們指派給裝置群組。 藉由使用更新響鈴，您可以建立可反映您業務需求的更新策略。 如需詳細資訊，請參閱[使用商務用 Windows Update 來管理更新](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb)。

## <a name="before-you-start"></a>開始之前

- 若要更新 Windows 10 電腦，這些電腦必須至少執行 Windows 10 專業版並已安裝 Windows 年度更新。

- Windows Update 支援下列 Windows 10 版本：
  - Windows 10
  - Windows 10 Team (適用於 Surface Hub 裝置)
  - [Windows Holographic for Business](#windows-holographic-for-business-support)

  不支援執行「Windows 10 行動裝置版」的裝置。

- 在 Windows 裝置上，[意見與診斷]  >  [診斷與使用方式資料] 必須至少設定為 [基本]。

    ![診斷與使用方式資料的 Windows 設定](./media/telemetry-basic.png)

    您可以手動設定此設定，或使用 Intune 裝置限制設定檔 (用於 Windows 10 和更新版本)。 若要這樣做，請至少將 [一般]  >  [提交診斷資料] 的設定設為 [基本]。 如需有關裝置設定檔的詳細資訊，請參閱[設定裝置限制設定](device-restrictions-configure.md)。

- 在 Intune 管理主控台中，有四種設定可控制軟體更新行為。 這些設定是 Windows 10 桌上電腦和行動裝置上，一般組態原則的一部分：
  - **允許自動更新**
  - **允許發行前版本功能**
  - **已排程的安裝日**
  - **已排程的安裝時間**

  Azure 傳統入口網站在裝置組態設定檔中也有一些其他 Windows 10 更新設定。 當您移轉至 Azure 入口網站時，如果已設定這當中的任何設定，強烈建議您執行下列操作︰

1. 在 Azure 入口網站上，以您需要的設定建立 Windows 10 更新響鈴。 Azure 入口網站已不再支援 [允許搶鮮版功能] 設定，因其不再適用於最新的 Windows 10 組建。 當您建立更新響鈴時，可以設定另外三個設定，以及其他 Windows 10 更新設定。

   > [!NOTE]
   > 移轉之後，在傳統入口網站中建立的 Windows 10 更新設定不會顯示在 Azure 入口網站中。 不過，系統會套用這些設定。 如果您移轉這當中的任何設定，並從 Azure 入口網站中編輯所移轉的原則，系統就會將這些設定從原則中移除。

2. 刪除傳統入口網站中的更新設定。 移轉至 Azure 入口網站並將相同設定新增至更新通道之後，您必須在傳統入口網站中刪除這些設定，以避免任何可能發生的原則衝突。 例如，當相同的設定具有不同的設定值時，就會發生衝突。 您很難得知此狀況，因為在傳統入口網站中設定的設定不會顯示在 Azure 入口網站中。

## <a name="create-and-assign-update-rings"></a>建立及指派更新通道

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [軟體更新] > [Windows 10 更新通道] > 建立。
4. 輸入名稱、描述 (選擇性)，然後選擇 [設定]。
5. 在 [設定] 中，輸入下列資訊：

   - **維護通道**：設定裝置從中接收 Windows 更新的通道。
   - **Microsoft 產品更新**︰選擇是否要從 Microsoft Update 掃描應用程式更新。
   - **Windows 驅動程式**︰選擇是否要在更新期間排除 Windows Update 驅動程式。
   - **自動更新行為**：選擇如何安裝自動更新、何時重新啟動或重新開機。 如需詳細資訊，請參閱 [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#update-allowautoupdate)。
     - **自動行為頻率**如果您針對更新行為選取 [在排定的時間自動安裝並重新啟動]，就會顯示此設定。 請使用此設定來排定何時安裝更新，包括週、日及時間。

   - **重新啟動檢查**：預設為啟用。 當您重新啟動裝置時，會進行一些檢查，包括檢查作用中的使用者、電池電量、執行中的遊戲等。 若要在重新啟動裝置時略過這些檢查，請選取 [略過]。

   - **品質更新延遲期間 (天)**：輸入品質更新延遲的天數。 最多可以延遲接收這些「品質更新」至其發行後 30 天。

     「品質更新」通常會修正和改進現有的 Windows 功能，而且會在每個月的第一個星期二發行。 不過，Microsoft 也可能隨時發行這些更新。 您可以定義在 Windows Update 提供「品質更新」之後，是否要延遲接收「品質更新」，以及要延遲多久。

   - **功能更新延遲期間 (天)**：輸入功能更新延遲的天數。 最多可以延遲接收「功能更新」至其發行後 180 天。

     「功能更新」通常是 Windows 的新功能。 在您設定 [維護通道] 設定之後，便可以定義在 Windows Update 提供「功能更新」之後，是否要延遲接收「功能更新」，以及要延遲多久。

     例如：**若 [維護通道] 已設定為 [半年通道 (已設定目標)] 且延遲期間為 30 天**：假設 Windows Update 在 1 月以 [半年通道 (已設定目標)] 的形式首次公開提供「功能更新 X」。 裝置要等到 2 月 (30 天後) 才會接收更新。

     **若 [維護通道] 已設定為 [半年通道] 且延遲期間為 30 天**：假設 Windows Update 在 1 月以 [半年通道 (已設定目標)] 的形式首次公開提供「功能更新 X」。 四個月後 (4 月)，「功能更新 X」才會發行到半年通道。 裝置會在此「半年通道」發行的 30 天後收到「功能更新」，而在 5 月進行更新。

   - **傳遞最佳化下載模式**選擇裝置下載 Windows 更新的方法。 如需詳細資訊，請參閱 [DeliveryOptimization/DODownloadMode](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode)。

6. 完成時，選取 [確定]。 在 [建立更新通道] 中，選取 [建立]。

新的更新響鈴會隨即顯示在更新響鈴清單中。

1. 若要指派更新響鈴，在更新響鈴清單中，選取響鈴，在 [<響鈴名稱>] 索引標籤中選擇 [指派]。
2. 在下一個索引標籤中，選擇 [Select groups to include] (選取要包含的群組)，然後選擇要指派此響鈴的群組。
3. 完成之後，選擇 [選取] 來完成這項指派。

## <a name="update-compliance-reporting"></a>更新合規性報告
您可以在 Intune 中檢視更新合規性，或使用稱為「更新合規性」的免費解決方案。

### <a name="review-update-compliance-in-intune"></a>在 Intune 中檢視更新合規性 
<!-- 1352223 -->檢閱原則報告，以檢視您已設定之 Windows 10 更新通道的部署狀態。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [軟體更新] > [概觀]。 您可以看到所指派任何更新通道的狀態一般資訊。
4. 請開啟下列其中一個報表：

   **針對所有部署通道**：  
   1. 在 [軟體更新] 上 > [Windows 10 更新通道]
   2. 在 [監視] 區段，選擇 [依更新通道別部署狀態]。

   **針對特定部署通道**：  
   1. 在 [軟體更新] > [Windows 10 更新通道] 中，選擇要檢閱的部署通道。
   2. 在 [監視] 區段中，從下列報表選擇，以檢視更新通道的更多詳細資訊：
      - **裝置狀態**
      - **使用者狀態**

### <a name="review-update-compliance-using-oms"></a>使用 OMS 檢視更新合規性
您可以使用稱為「更新合規性」的免費解決方案來監視 Windows 10 更新的首度發行。 如需詳細資訊，請參閱[使用Update Compliance 來監視 Windows Updates](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor)。 當您使用此解決方案時，可以將商業識別碼部署至任何您用 Intune 管理、且要報告更新合規性的 Windows 10 裝置。

在 Intune 主控台中，您可以使用自訂原則的 OMA-URI 設定來設定商業識別碼。 如需詳細資訊，請參閱 [Microsoft Intune 中 Windows 10 裝置的 Intune 原則設定](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)。   

用於設定商業識別碼的 OMA-URI (區分大小寫) 路徑是：./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID

例如，您可以在 [新增或編輯 OMA-URI 設定] 中使用下列值：

- **設定名稱**：Windows Analytics 商業識別碼
- **設定描述**︰設定 Windows Analytics 解決方案的商業識別碼
- **OMA-URI** (區分大小寫)：./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **資料類型**：字串
- **值**：<使用 OMS 工作區中的 [Windows 遙測] 索引標籤上顯示的 GUID>

![OMA-URI 設定 - 編輯資料列](./media/commID-edit.png)

> [!NOTE]
> 如需有關 MS DM 伺服器的詳細資訊，請參閱 [DMClient 設定服務提供者 (CSP)](https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp)。

## <a name="pause-updates"></a>暫停更新
您可以讓裝置暫停接收功能更新或品質更新一段期間，自您暫停更新起最多 35 天。 經過天數上限之後，暫停功能會自動過期，裝置將掃描 Windows Updates 尋找可用的更新。 在這次掃描後，您可以再一次暫停更新。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [軟體更新] > [Windows 10 更新通道]。
4. 在更新通道清單中，選擇您想要暫停的通道，然後選擇 [...] > [暫停品質] > 或 [暫停功能] (視您想要暫停的更新類型而定)。

> [!IMPORTANT]
> 在您發出暫停命令後，裝置會在下次簽入服務時收到此命令。 也有可能在確認更新之前，就已經執行排定的更新。
> 此外，當您發出暫停命令時如果目標裝置已關閉，當您開啟裝置時，它可能會下載並安裝排定的更新，然後再去向 Intune 確認。

### <a name="uninstall-the-latest-from-windows-10-software-updates"></a>解除安裝 Windows 10 軟體更新的最新版本 
如果您發現 Windows 10 電腦上發生重大問題，可以選擇解除安裝 (復原) 最新的功能更新或最新的品質更新。 解除安裝功能或品質更新只適用於裝置所在的維護通道。 解除安裝將會觸發原則，以在 Windows 10 電腦上還原先前的更新。 特別是對於功能更新，您可以將能夠套用解除安裝最新版本的時間限制為 2-60 天。 若要設定軟體更新解除安裝選項：

1. 在 Intue 中，選取 [軟體更新]。
2. 選取 [Windows 10 更新通道] > 選取現有的更新通道 > [解除安裝]。

> [!NOTE]
> 在 Windows 10 電腦上成功復原品質更新之後，終端使用者會繼續在 [Windows 設定] > [更新] > [更新記錄] 中看到列出的更新。

## <a name="windows-holographic-for-business-support"></a>Windows Holographic for Business 支援

Windows Holographic for Business 支援下列設定：

- **自動更新行為**
- **Microsoft 產品更新**
- **服務通道**：支援 [半年通道] 和 [半年通道 (已設定目標)] 選項
