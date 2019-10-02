---
title: 在 Microsoft Intune 中啟用 eSIM 數據連線 - Azure | Microsoft Docs
description: 透過不同的行動數據方案新增或使用 eSIM 取得網際網路和資料存取。 在 Intune 中，新增或匯入啟用代碼，然後使用組態設定檔指派這些啟用代碼。 您也可以監視 eSIM 設定檔，並檢查啟用 eSIM 的裝置狀態。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/31/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c8b3078769428e5ba2679b141476293cb6df6813
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723940"
---
# <a name="configure-esim-cellular-profiles-in-intune---public-preview"></a>在 Intune 中設定 eSIM 行動數據設定檔 - 公開預覽

eSIM 是內嵌的 SIM 卡晶片，可讓您透過支援 eSIM 之裝置 (例如 [Surface LTE Pro](https://www.microsoft.com/surface/business/surface-pro)) 上的行動數據連線來連線到網際網路。 使用 eSIM，您不需要從您的電信業者取得 SIM 卡。 身為全球旅行者，您也可以切換電信業者與數據方案，一律保持連線。

例如，您有工作用行動數據方案，以及另一個不同電信業者的個人用行動數據方案。 出差旅遊時，您可以尋找當地提供行動數據方案的電信業者來取得網際網路存取。

在 Intune 中，您可以匯入由電信業者提供、僅使用一次的啟用代碼。 若要在 eSIM 模組上設定行動數據方案，請將這些啟用代碼部署到支援 eSIM 的裝置。 當 Intune 安裝啟用代碼時，eSIM 硬體模組會使用啟用代碼中的資料來連絡電信業者。 完成之後，eSIM 設定檔會下載到裝置上，並設定以啟用行動數據。

若要使用 Intune 將 eSIM 部署到您的裝置，需要下列項目：

- **支援 eSIM 的裝置**，例如 Surface LTE：請參閱[您的裝置是否支援 eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)。 或者，參閱[一些已知支援 eSIM 的裝置](#esim-capable-devices)清單 (在本文中)。
- 已註冊的 **Windows 10 Fall Creators Update 電腦** (1709 或更新版本) 及受 Intune 管理的 MDM
- 由您的電信業者提供的**啟用代碼**。 這些僅使用一次的啟用代碼會新增至 Intune，並部署到支援 eSIM 的裝置。 連絡您的電信業者以取得 eSIM 啟用代碼。

## <a name="deploy-esim-to-devices---overview"></a>將 eSIM 部署到裝置 - 概觀

若要將 eSIM 部署到裝置，系統管理員會完成下列工作：

1. 匯入由您的電信業者提供的啟用代碼
2. 建立 Azure Active Directory (Azure AD) 裝置群組，其中包含支援 eSIM 的裝置
3. 將 Azure AD 群組指派給您匯入的訂用帳戶集區
4. 監視部署

本文將引導您完成這些步驟。

## <a name="esim-capable-devices"></a>支援 eSIM 的裝置

下列裝置已宣告為支援 eSIM，或目前在市面上。 另請確認[您的裝置是否支援 eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)。

- Acer Swift 7
- Asus NovoGo TP370QL
- Asus TP401
- Asus Transformer Mini T103
- HP Elitebook G5
- HP Envy x2
- HP Probook G5
- Lenovo Miix 630
- Lenovo T480
- Samsung Galaxy Book
- Surface Pro LTE
- HP Spectre Folio 13
- Lenovo Yoga C630

## <a name="step-1-add-cellular-activation-codes"></a>步驟 1：新增行動數據啟用代碼

行動數據啟用代碼是由您的電信業者提供的逗號分隔檔案 (csv)。 當您具有此檔案時，使用下列步驟將它新增至 Intune：

1. 登入 [Azure 入口網站](https://portal.azure.com/)。
2. 選取 [All services] (所有服務)  ，篩選 [Intune]  ，然後選取 [Microsoft Intune]  。
3. 選取 [裝置設定]   > [eSIM cellular profiles] \(eSIM 行動數據設定檔\)   > [新增]  。
4. 選取具有您啟用代碼的 CSV 檔案。
5. 按一下 [確定]  以儲存您的變更。

### <a name="csv-file-requirements"></a>CSV 檔案需求

使用具有啟用代碼的 csv 檔案時，請確定您或您的電信業者遵循下列需求：

- 檔案必須是 csv 格式 (filename.csv)。
- 檔案結構必須遵守嚴謹的格式。 否則，匯入會失敗。 Intune 會在匯入時檢查檔案；如果發現錯誤，就會失敗。
- 啟用代碼會使用一次。 不建議匯入您先前匯入的啟用代碼，這可能會在您部署到相同或不同裝置時造成問題。
- 每個檔案應該專屬於單一電信業者，而且所有啟用代碼都會專屬於相同的計費方案。 Intune 會隨機將啟用代碼散發給目標裝置。 不保證哪部裝置會取得特定啟用代碼。
- 一個 csv 檔案最多可匯入 1000 個啟用代碼。

### <a name="csv-file-example"></a>CSV 檔案範例

1. csv 的第一個資料列和第一個資料格是電信業者 eSIM 啟用服務的 URL，稱為 SM-DP+ (訂閱管理員資料準備伺服器)。 此 URL 應該是不含任何逗號的完整網域名稱 (FQDN)。
2. 第二個及後面所有資料列都是僅使用一次的唯一啟用代碼，其中包含兩個值：

    1. 第一個資料行是唯一的 ICCID (SIM 卡晶片的識別碼)
    2. 第二個資料行是只以逗號分隔 (結尾沒有逗號) 的比對識別碼。 請參閱以下範例：

        ![電信業者啟用代碼範例 csv 檔案](./media/esim-device-configuration/url-activation-code-examples.png)

3. csv 檔案名稱會變成 Azure 入口網站中的行動數據訂用帳戶集區名稱。 在上圖中，檔案名稱為 `UnlimitedDataSkynet.csv`。 因此，Intune 會將訂用帳戶集區命名為 `UnlimitedDataSkynet.csv`：

    ![行動數據訂用帳戶集區會命名為啟用代碼範例 csv 檔案名稱](./media/esim-device-configuration/subscription-pool-name-csv-file.png)

## <a name="step-2-create-an-azure-ad-device-group"></a>步驟 2：建立 Azure AD 裝置群組

建立裝置群組，其中包含支援 eSIM 的裝置。 [新增群組](../fundamentals/groups-add.md)列出這些步驟。

> [!NOTE]
> - 只會以裝置為目標，不會以使用者為目標。
> - 建議建立靜態 Azure AD 裝置群組，其中包含您的 eSIM 裝置。 使用群組確認您只以 eSIM 裝置為目標。

## <a name="step-3-assign-esim-activation-codes-to-devices"></a>步驟 3：將 eSIM 啟用代碼指派給裝置

將設定檔指派給 Azure AD 群組，其中包含您的 eSIM 裝置。

1. 在 [Azure 入口網站](https://portal.azure.com/)中，選取 [所有服務]  ，篩選 [Intune]  ，然後選取 [Microsoft Intune]  。
2. 選取 [裝置設定]   > [eSIM cellular] \(eSIM 行動數據\)   > [設定檔]  。
3. 在設定檔清單中，選取您要指派的 eSIM 行動數據訂用帳戶集區，然後選取 [指派]  。
4. 選擇以 [包含]  群組或 [排除]  群組，然後選取群組。

    ![包含裝置群組以指派設定檔](./media/esim-device-configuration/include-exclude-groups.png)

5. 當您選取群組時，會選擇 Azure AD 群組。 若要選取多個群組，請使用 **Ctrl** 鍵，然後選取群組。
6. 完成後，請 [儲存]  變更。

eSIM 啟用代碼會使用一次。 Intune 在裝置上安裝啟用代碼之後，eSIM 模組會連絡電信業者以下載行動數據設定檔。 此連絡人會完成向電信業者網路註冊裝置。

## <a name="step-4-monitor-deployment"></a>步驟 4：監視部署

### <a name="review-the-deployment-status"></a>檢閱部署狀態

指派設定檔之後，您可以監視訂用帳戶集區的部署狀態。

1. 登入 [Azure 入口網站](https://portal.azure.com/)。
2. 選取 [All services] (所有服務)  ，篩選 [Intune]  ，然後選取 [Microsoft Intune]  。
3. 選取 [裝置設定]   > [eSIM cellular profiles] \(eSIM 行動數據設定檔\)  。 您所有現有的 eSIM 行動數據訂用帳戶集區隨即列出。
4. 選取訂用帳戶，然後檢閱 [部署狀態]  。

### <a name="check-the-profile-status"></a>檢查設定檔狀態
當您建立裝置設定檔之後，Intune 會提供圖形化圖表。 這些圖表顯示設定檔的狀態，例如它已經成功地指派給裝置，或者該設定檔顯示有衝突。

1. 選取 [裝置設定]   > [eSIM cellular profiles] \(eSIM 行動數據設定檔\)  > 選取現有的訂用帳戶。
2. 在 [概觀]  索引標籤中，頂端的圖形化圖表會顯示指派給特定 eSIM 行動數據訂用帳戶集區部署的裝置數目。

    它也會顯示指派相同設定檔之其他平台的裝置數目。

    Intune 會顯示以裝置為目標之啟用代碼的傳遞和安裝狀態。

    - **裝置未同步**：建立 eSIM 部署原則之後，目標裝置尚未連絡 Intune
    - **啟用暫止**：Intune 正在裝置上安裝啟用代碼時的暫時性狀態
    - **使用中**：啟用代碼安裝成功
    - **啟用失敗**：啟用代碼安裝失敗 - 請參閱疑難排解指南。

#### <a name="view-the-detailed-device-status"></a>檢視詳細的裝置狀態

您可以監視並檢視可在 [裝置狀態] 中檢視的詳細裝置清單。**

1. 選取 [裝置設定]   > [eSIM cellular profiles] \(eSIM 行動數據設定檔\)  > 選取現有的訂用帳戶。
2. 選取 [裝置狀態]  。 Intune 會顯示有關裝置的其他詳細資料：

    - **裝置名稱**：目標裝置的名稱
    - **使用者**：已註冊裝置的使用者
    - **ICCID**：裝置上安裝之啟用代碼內由電信業者提供的唯一代碼
    - **啟用狀態**：裝置上啟用代碼的 Intune 傳遞和安裝狀態
    - **行動數據狀態**：由電信業者提供的狀態。 若要進行疑難排解，請連絡電信業者。
    - **上次簽入時間**：裝置上次與 Intune 通訊的日期

### <a name="monitor-esim-profile-details-on-the-actual-device"></a>監視實際裝置上的 eSIM 設定檔詳細資料

1. 在您的裝置上，開啟 [設定]  > 移至 [網路和網際網路]  。
2. 選取 [行動數據]   > [管理 eSIM 設定檔] 
3. eSIM 設定檔隨即列出：

    ![檢視您裝置設定中的 eSIM 設定檔](./media/esim-device-configuration/device-settings-cellular-profiles.png)

## <a name="remove-the-esim-profile-from-device"></a>從裝置中移除 eSIM 設定檔

當您從 Azure AD 群組中移除裝置時，也會移除 eSIM 設定檔。 請務必：

1. 確認您使用 eSIM 裝置 Azure AD 群組。
2. 移至 Azure AD 群組，並從群組中移除裝置。
3. 當已移除的裝置連絡 Intune 時，會評估已更新的原則，並移除 eSIM 設定檔。

當使用者[淘汰](../remote-actions/devices-wipe.md#retire)或取消註冊裝置時，或是當[重設裝置遠端動作](../remote-actions/devices-wipe.md#wipe)在裝置上執行時，也會移除 eSIM 設定檔。

> [!NOTE]
> 移除設定檔可能會停止計費。 連絡您的電信業者以檢查您裝置的計費狀態。

## <a name="best-practices--troubleshooting"></a>最佳做法與疑難排解

- 確定您的 csv 檔案格式正確。 確認檔案未包含重複的代碼、多個電信業者或不同的行動數據方案。 請記住，每個檔案必須專屬於電信業者和行動數據方案。
- 建立靜態裝置 Azure AD 群組，其中只包含目標 eSIM 裝置。
- 如果部署狀態有問題，請檢查下列項目：
  - **檔案格式不正確**：請參閱**步驟 1：新增行動數據啟用代碼** (在本文中) 以了解如何正確格式化您的檔案。
  - **行動數據啟用失敗，請連絡電信業者**：啟用代碼可能未在其網路內啟用。 或者，設定檔下載和行動數據啟用失敗。

## <a name="next-steps"></a>後續步驟
[設定裝置設定檔](../device-profiles.md)
