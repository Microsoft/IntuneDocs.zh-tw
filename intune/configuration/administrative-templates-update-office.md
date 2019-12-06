---
title: 在 Microsoft Intune 中使用系統管理範本更新 Office 365 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 中的系統管理範本，將 Office 365 應用程式更新為最新版本，並選擇 Office 檢查更新的頻率。 查看將 Intune 原則套用到 Office 更新時所更新的裝置登錄機碼。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cf872387d6e6f4f91af9f074f54695b081b79119
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74549105"
---
# <a name="use-update-channel-and-target-version-settings-to-update-office-365-with-microsoft-intune-administrative-templates"></a>使用更新通道和目標版本設定，以 Microsoft Intune 來更新 Office 365 系統管理範本

在 Intune 中，您可以[使用 Windows 10 範本設定群組原則設定](administrative-templates-windows.md)。 本文說明如何使用 Intune 中的系統管理範本來更新 Office 365。 它也會提供確認原則套用成功的指引。 此資訊在進行疑難排解時也有幫助。

在此情節中，您會在 Intune 中建立系統管理範本，以便在您的裝置上更新 Office 365。

如需系統管理範本的詳細資訊，請參閱[設定群組原則設定的 Windows 10 範本](administrative-templates-windows.md)。

適用於：

- Windows 10 及更新版本
- Office 365

## <a name="prerequisites"></a>必要條件

請務必針對您的 Office 應用程式[啟用 Office 365 專業增強版自動更新](https://docs.microsoft.com/deployoffice/configure-update-settings-for-office-365-proplus) \(部分機器翻譯\)。 您可以使用群組原則或 Intune Office 2016 ADMX 範本來執行此動作：

![在 Intune 系統管理範本中，設定 Office 的 [啟用自動更新] 設定](./media/administrative-templates-update-office/admx-enable-automatic-updates.png)

## <a name="set-the-update-channel-in-the-intune-administrative-template"></a>在 Intune 系統管理範本中設定更新通道

1. 在 [Intune 系統管理範本](administrative-templates-windows.md#create-a-template)中，移至 [更新通道]  設定，然後輸入您想要的通道。 例如，選擇 `Semi-Annual Channel`：

    ![在 Intune 系統管理範本中，設定 Office 的 [更新通道] 設定](./media/administrative-templates-update-office/admx-enable-update-channel-setting.png)

    > [!NOTE]
    > 建議您更頻繁地更新。 半年僅作為範例使用。

2. 請務必[指派原則](device-profile-assign.md)給您的 Windows 10 裝置。 若要更快測試原則，您也可以同步處理原則：

    - [在 Intune 中同步處理原則](../remote-actions/device-sync.md)
    - [以手動方式同步處理裝置上的原則](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows#sync-from-settings-app)

## <a name="check-the-intune-registry-keys"></a>檢查 Intune 登錄機碼

指派原則並同步處理裝置後，您可以確認該策略已套用：

1. 在裝置上，開啟 [登錄編輯程式]  應用程式。
2. 移至 Intune 原則路徑：`Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`。

    > [!TIP]
    > 登錄機碼中的 `<Provider ID>` 會變更。 若要尋找裝置的提供者識別碼，請開啟 [登錄編輯程式]  應用程式，然後移至 `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\AdmxInstalled`。 提供者識別碼隨即顯示。

    套用原則時，您會看到下列登錄機碼：

    - `L_UpdateBranch`
    - `L_UpdateTargetVersion`

    查看下列範例時，您會看到 `L_UpdateBranch` 具有類似 `<enabled /><data id="L_UpdateBranchID" value="Deferred" />` 的值。 此值表示它會設定為 [半年通道]：

    ![系統管理範本 L_Updatebranch 登錄機碼範例](./media/administrative-templates-update-office/admx-update-branch-registry-key.png)

    > [!TIP]
    > [使用 Configuration Manager 管理 Office 365 專業增強版](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager) \(部份機器翻譯\) 會列出值及其意義。 登錄值是以選取的散發通道為基礎：
    >
    >- 每月通道                - value="Current"
    >- 每月通道 (已設定目標)     - value="Current"
    >- 半年通道            - value="Current"
    >- 半年通道 (已設定目標) - value="FirstReleaseDeferred"
    >- 測試人員 - 快                   - value="InsiderFast"

此時，Intune 原則已成功套用至裝置。

## <a name="check-the-office-registry-keys"></a>檢查 Office 登錄機碼

1. 在裝置上，開啟 [登錄編輯程式]  應用程式。
2. 移至 Office 原則路徑：`Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`。

    您會看到下列登錄機碼：

    - `UpdateChannel`：根據已設定的設定而變更的動態索引鍵。
    - `CDNBaseUrl`：在裝置上安裝 Office 365 時設定。

3. 查看 `UpdateChannel` 值。 此值會告訴您 Office 的更新頻率。 [使用 Configuration Manager 管理 Office 365 專業增強版](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager) \(部份機器翻譯\) 會列出值，以及它們所設定的內容。

    查看下列範例時，您會看到 `UpdateChannel` 設定為 `http://officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60`，即 [每月]  ：

    ![系統管理範本 Office UpdateChannel 登錄機碼範例](./media/administrative-templates-update-office/admx-update-channel-office-registry-key.png)

    這個範例表示尚未套用原則，因為它仍然設定為 [每月]  ，而不是 [半年]  。

當 [工作排程器]   > [Office 自動更新 2.0]  執行時，或當使用者登入裝置時，就會更新此登錄機碼。 若要確認，請開啟 [Office 自動更新 2.0]  工作 > [觸發程式]  。 視您的觸發程式而定，在更新 `UpdateChannel` 登錄機碼之前，可能至少需要一天的時間。

## <a name="force-office-automatic-updates-to-run"></a>強制執行 Office 自動更新

若要測試您的原則，您可以在裝置上強制執行原則設定。 下列步驟會更新登錄。 一如往常，更新登錄時請務必小心。

1. 清除登錄機碼：

    1. 移至 `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Updates`。
    2. 按兩下 [`UpdateDetectionLastRunTime`] 索引鍵、刪除值資料 > [確定]  。

2. 執行 Office 自動更新工作：

    1. 在裝置上開啟 [工作排程器]  應用程式。
    2. 展開 [工作排程器程式庫]   > [Microsoft]   > [Office]  。
    3. 選取 [Office 自動更新 2.0]   > [執行]  ：

        ![開啟 [工作排程]，然後執行 [Office 自動更新]](./media/administrative-templates-update-office/admx-task-scheduler-office-automatic-updates.png)

        等待工作完成，這可能需要幾分鐘的時間。

3. 在 [登錄編輯程式]  中，移至 `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`。 檢查 `UpdateChannel` 值。

    您應該使用原則中設定的值對其進行更新。 在我們的範例中，此值應該設定為 `http://officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114`。

此時，裝置上已成功變更 Office 更新通道。 您可以針對接收此更新以檢查狀態的使用者，開啟 Office 365 應用程式。

## <a name="force-the-office-synchronization-to-update-account-information"></a>強制 Office 同步處理更新帳戶資訊  

如果您想要執行更多操作，則可以強制 Office 取得最新版本的更新。 下列步驟僅應作為確認，或如果您需要裝置從該通道快速取得最新版本更新。 否則，請讓 Office 執行其作業，並自動更新。

### <a name="step-1-force-the-office-version-to-update"></a>步驟 1：強制 Office 版本更新

1. 確認 Office 版本支援您所選擇的更新通道。 [Office 365 專業增強版的更新歷程記錄](https://docs.microsoft.com/officeupdates/update-history-office365-proplus-by-date)會列出支援不同更新通道的組建編號。

2. 在您的 [Intune 系統管理範本](administrative-templates-windows.md#create-a-template)中，移至 [目標版本]  設定，然後輸入您想要的版本。

    您的 [目標版本]  設定看起來類似下列設定：

    ![在 Intune 系統管理範本中，設定 Office 的 [目標版本] 設定](./media/administrative-templates-update-office/admx-enable-target-version-setting.png)

> [!IMPORTANT]
>
> - 請務必指派原則。
> - 如果您變更現有的原則，您的變更會影響所有指派的使用者。
> - 如果您要測試此功能，建議您建立測試原則，並將原則指派給使用者的測試群組。

### <a name="step-2-check-the-office-version"></a>步驟 2：檢查 Office 版本

將原則部署給所有使用者之前，請考慮使用這些步驟來測試原則。

1. 在 [登錄編輯程式]  應用程式中，移至 `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`

2. 查看 `L_UpdateTargetVersion` 值。 套用原則之後，此值會設定為您所輸入的版本，例如 `<enabled /><data id="L_UpdateTargetVersionID" value="16.0.10730.20344" />`。

    此時，Intune 原則已成功套用至裝置。

3. 接下來，您可以強制 Office 進行更新。 開啟 Office 應用程式，例如 Excel。 選擇立即更新 (可能在 [帳戶]  功能表中)。

    更新需要幾分鐘的時間。 您可以確認 Office 正在嘗試取得您輸入的版本：

      1. 在裝置上，移至 `C:\Program Files (x86)\Microsoft Office\Updates\Detection\Version`。
      2. 開啟 `VersionDescriptor.xml` 檔案，然後移至 `<Version>` 區段。 可用的版本應該與您在 Intune 原則中輸入的版本相同，例如：

          ![檢查版本描述項 Office XML 檔案中的版本區段](./media/administrative-templates-update-office/office-version-descriptor-xml-example.png)

4. 安裝更新之後，Office 應用程式應該會顯示新版本 (例如，在 [帳戶]  功能表上)

## <a name="next-steps"></a>後續步驟

[Office 365 用戶端的更新通道值](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager)

[Office 365 專業增強版的 Office 雲端原則服務概觀](https://docs.microsoft.com/deployoffice/overview-office-cloud-policy-service)

[在 Microsoft Intune 中使用 Windows 10 範本設定群組原則設定 (ADMX 範本)](administrative-templates-windows.md)
