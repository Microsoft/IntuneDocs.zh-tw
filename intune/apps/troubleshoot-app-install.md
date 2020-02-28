---
title: 針對應用程式安裝問題進行疑難排解
titleSuffix: Microsoft Intune
description: 使用 [Microsoft Intune 疑難排解] 窗格，以協助您針對應用程式安裝問題進行疑難排解。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 13aea23f58c69d5c7e38f77ae7dfa19bd12edd35
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511646"
---
# <a name="troubleshoot-app-installation-issues"></a>針對應用程式安裝問題進行疑難排解

在受 Microsoft Intune MDM 管理的裝置上，應用程式安裝有時可能會失敗。 當這些應用程式安裝失敗時，使用者可能無法輕易地了解失敗的原因，或是對問題進行疑難排解。 Microsoft Intune 提供應用程式安裝失敗詳細資料，可讓技術支援人員和 Intune 系統管理員檢視應用程式資訊，以處理使用者的協助要求。 Intune 中的 [疑難排解] 窗格會提供失敗的詳細資訊，包括使用者裝置上的受控應用程式相關詳細資料。 有關應用程式完整生命週期的詳細資訊，會在 [受控應用程式]  窗格中的每個個別裝置下提供。 您可以檢視安裝問題，例如當應用程式建立、修改、設定目標，以及傳遞至裝置時的問題。 

> [!NOTE]
> 如需特定應用程式安裝錯誤碼的資訊，請參閱 [Intune 應用程式安裝錯誤參考](~/apps/app-install-error-codes.md)。

## <a name="app-troubleshooting-details"></a>應用程式疑難排解詳細資料

Intune 會根據特定使用者裝置上安裝的應用程式，提供應用程式疑難排解的詳細資料。

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 選取 [疑難排解 + 支援]  。
4. 按一下 [選取使用者]  來選取使用者以進行疑難排解。 [選取使用者]  窗格隨即顯示。
5. 鍵入名稱或電子郵件地址來選取使用者。 按一下窗格底部的 [選取]  。 在 [疑難排解]  窗格中，會顯示使用者的疑難排解資訊。 
6. 從 [裝置]  清單中選取要進行疑難排解的裝置。
    ![[Intune 疑難排解] 窗格。](./media/troubleshoot-app-install/troubleshoot-app-install-01.png)
7. 從 [選取的裝置] 窗格中選取 [受控應用程式]  。 受控應用程式清單隨即出現。
    ![由 Intune 所管理特定裝置的詳細資料。](./media/troubleshoot-app-install/troubleshoot-app-install-02.png)
8. 從 [安裝狀態]  指示失敗的清單中選取應用程式。
    ![顯示安裝失敗詳細資料的已選取應用程式。](./media/troubleshoot-app-install/troubleshoot-app-install-03.png)

    > [!Note]  
    > 可以將相同的應用程式指派給多個群組，但對於該應用程式有不同的預期動作 (用途)。 例如，如果在應用程式指派期間針對某個使用者排除了該應用程式，則應用程式已解決的用途會顯示 [已排除]  。 如需詳細資訊，請參閱[如何解決應用程式用途之間的衝突](apps-deploy.md#how-conflicts-between-app-intents-are-resolved)。<br><br>
    > 如果必要的應用程式安裝失敗，您或您的技術服務人員將能夠同步裝置並重試應用程式安裝。

應用程式安裝錯誤詳細資料會指出此問題。 您可以使用這些詳細資料，以決定解決問題所要採取的最佳動作。 如需有關針對應用程式安裝問題進行疑難排解的詳細資訊，請參閱 [Android 應用程式安裝錯誤](app-install-error-codes.md#android-app-installation-errors)和 [iOS 應用程式安裝錯誤](app-install-error-codes.md#ios-and-ipados-app-installation-errors)。

> [!Note]  
> 您也可以將瀏覽器指向 [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting)來存取 [疑難排解]  窗格。

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>以使用者群組為目標的應用程式安裝無法連線到裝置
如果您在安裝應用程式時發生問題，應該考量下列動作：
- 如果應用程式未顯示在公司入口網站中，請確定已使用**可用**的意圖部署應用程式，且使用者使用應用程式支援的裝置類型來存取公司入口網站。
- 針對 Windows BYOD 裝置，使用者必須將公司帳戶新增至裝置。
- 檢查使用者是否超過 AAD 裝置限制：
  1. 瀏覽至 [Azure Active Directory 裝置設定](https://portal.azure.com/#pane/Microsoft_AAD_IAM/DevicesMenupane/DeviceSettings/menuId)。
  2. 請記下針對 [每位使用者的裝置數目上限]  設定的值。
  3. 瀏覽至 [Azure Active Directory 使用者](https://portal.azure.com/#pane/Microsoft_AAD_IAM/UsersManagementMenupane/AllUsers)。
  4. 選取受影響的使用者，然後按一下 [裝置]  。
  5. 如果使用者超過設定的限制，則會刪除不再需要的任何過時記錄。
- 針對 iOS/iPadOS DEP 裝置，請確定使用者已在 [Intune 裝置概觀] 窗格中列為 [由使用者註冊]  。 如果顯示的是 NA，則為 Intune 公司入口網站部署設定原則。 如需詳細資訊，請參閱[設定公司入口網站應用程式](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-and-ipados-dep-devices)。

## <a name="win32-app-installation-troubleshooting"></a>針對 Win32 應用程式安裝進行疑難排解

選取使用 Intune 管理延伸模組部署的 Win32 應用程式。 您可以在 Win32 應用程式安裝失敗時選取 [收集記錄]  選項。 

> [!IMPORTANT]
> [收集記錄]  選項在成功於裝置上安裝 Win32 應用程式時將不會啟用。<p>您必須先在 Windows 用戶端上安裝 Intune 管理延伸模組，才能收集 Win32 應用程式記錄資訊。 將 PowerShell 指令碼或 Win32 應用程式部署至使用者或裝置安全性群組時，將安裝 Intune 管理延伸模組。 如需詳細資訊，請參閱 [Intune 管理延伸模組 - 必要條件](intune-management-extension.md#prerequisites)。

### <a name="collect-log-file"></a>收集記錄檔

若要收集您的 Win32 應用程式安裝記錄，請先遵循[應用程式疑難排解詳細資料](troubleshoot-app-install.md#app-troubleshooting-details)一節中提供的步驟。 接著，請繼續進行下列步驟：

1. 按一下 [安裝詳細資料]  窗格上的 [收集記錄]  選項。

    <image alt="Win32 app installation details - Collect log option" src="./media/troubleshoot-app-install/troubleshoot-app-install-04.png" width="500" />

2. 提供檔案路徑，其中包括記錄檔的名稱，來啟動收集記錄檔的程序，並按一下 [確定]  。

    > [!NOTE]
    > 收集記錄會在兩個小時內完成。 支援的檔案類型： *.log、.txt、.dmp、.cab、.zip、.xml、.evtx 及 .evtl*。 最多允許 25 個檔案路徑。

3. 收集完記錄檔後，您可以選取 [記錄]  連結來下載記錄檔。

    <image alt="Win32 app log details - Download logs" src="./media/troubleshoot-app-install/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > 隨即會顯示通知，指出應用程式記錄收集已成功。

#### <a name="win32-log-collection-requirements"></a>Win32 記錄收集需求

收集記錄檔必須遵循特定的需求：

- 您必須指定完整的記錄檔路徑。 
- 您可以為記錄收集指定環境變數，如下所示：<br>
  *%PROGRAMFILES%、%PROGRAMDATA%、%PUBLIC%、%WINDIR%、%TEMP%、%TMP%*
- 只允許明確的副檔名，例如：<br>
  *.log、.txt、dmp、.cab、.zip、.xml*
- 能夠上傳的記錄檔上限為 60 MB 或 25 個檔案，視先到達的限制而定。 
- Win32 應用程式記錄收集會為符合必要、可用及解除安裝應用程式指派意圖的應用程式啟用。
- 儲存的記錄會經過加密，以保護記錄檔中包含的任何個人識別資訊。
- 當開啟 Win32 應用程式失敗的支援票證時，請使用以上提供的步驟附加相關失敗記錄。

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>針對來自 Microsoft 網上商店的應用程式進行疑難排解

[Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (針對封裝、部署及查詢 Microsoft 網上商店應用程式進行疑難排解) 主題中的資訊可協助您使用 Intune 或任何其他方法，為從 Microsoft 網上商店安裝應用程式時可能發生的常見問題進行疑難排解。

## <a name="app-troubleshooting-resources"></a>應用程式疑難排解資源
- [將 Visio 和 Project 部署為 Office Pro Plus 部署的一部分](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [採取動作以確保透過 Intune 安裝在 Windows 10 1903 上部署 MSfB 應用程式](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [針對 Microsoft Intune 中的 MSI 應用程式部署進行疑難排解](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [將軟體發佈到 Intune 傳統 Windows 電腦代理程式的最佳做法](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>後續步驟

- 如需其他 Intune 疑難排解資訊，請參閱[使用疑難排解入口網站來協助公司的使用者](../fundamentals/help-desk-operators.md)。 
- 深入了解 Microsoft Intune 的任何已知問題。 如需詳細資訊，請參閱 [Intune Customer Success](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess) (Intune 客戶成功)。
- 需要額外說明嗎？ 請參閱[如何取得 Microsoft Intune 支援](../fundamentals/get-support.md)。
