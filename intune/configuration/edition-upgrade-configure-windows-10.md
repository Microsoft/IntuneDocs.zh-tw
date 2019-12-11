---
title: 在 Windows 10 裝置上升級或使用 S 模式 - Microsoft Intune - Azure | Microsoft Docs
description: 使用 Microsoft Intune，以將 Windows 10 裝置升級至不同版本或切換 S 模式。 系統管理員可以使用裝置組態設定檔，將 Windows 10 專業版升級至 Windows 10 企業版，以及切換移出 S 模式。 查看針對 Windows 10 專業版、N 版、教育版、Cloud、企業版、Core、全像攝影版和行動裝置版所支援的升級路徑。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3595e75a73868378c9c366de6c751c21a9151ae3
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059525"
---
# <a name="upgrade-windows-10-editions-or-switch-out-of-s-mode-on-devices-using-microsoft-intune"></a>使用 Microsoft Intune 在裝置上升級 Windows 10 版本或切換移出 S 模式

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

作為行動裝置管理 (MDM) 解決方案的一部分，您可能會想要升級您的 Windows 10 裝置。 例如，您會想要將「Windows 10 專業版」裝置升級至「Windows 10 企業版」。 或者，您想要讓裝置切換移出 S 模式。

[Windows 10 S 模式](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) (開啟另一個 Microsoft 網站) 是針對安全性與效能所設計的。 您可以使用 Intune 來切換移出 S 模式。 切換移出 S 模式是單向作業。 一旦您切換移出 S 模式，就無法回到 Windows 10 S 模式。

查看一些關於網域的[常見問題](https://support.microsoft.com/help/4020089/windows-10-in-s-mode-faq)。

本功能適用於：

- Windows 10 及更新版本
- Windows 10 1809 或更新版本 (適用於 S 模式)
- Windows Holographic for Business

這些功能可於 Intune 中取得，並可由系統管理員設定。 Intune 會使用「組態設定檔」來依據貴組織的需求建立和自訂這些設定。 在您於設定檔中新增這些功能之後，便可將該設定檔推送或部署至貴組織中的 Windows 10 裝置。 當您部署設定檔時，Intune 會自動升級裝置或切換移出 S 模式。

本文列出支援的升級路徑，並示範如何建立裝置組態設定檔。 您也可以查看適用於 [Windows 10](edition-upgrade-windows-settings.md) 的所有可用升級和 S 模式設定。

> [!NOTE]
> 如果您稍後移除原則指派，裝置上的 Windows 版本並不會還原。 裝置會繼續正常執行。

## <a name="prerequisites"></a>必要條件

在您升級裝置之前，請確定您已具備下列必要條件：

- 可以在您以原則設為目標的所有裝置上 (適用於 Windows 10 Desktop 版本)，安裝更新 Windows 版本的有效產品金鑰。 您可以使用多次啟用金鑰 (MAK) 或金鑰管理伺服器 (KMS) 金鑰。
- 針對「Windows 10 行動裝置版」和「Windows 10 全像攝影版」，您可以使用 Microsoft 授權檔案。 此授權檔案包含可在作為原則目標的所有裝置上安裝更新版本的授權資訊。
- 會在 Microsoft Intune 中註冊您指派原則的 Windows 10 裝置。 您無法將版本升級原則和執行 Intune 電腦用戶端軟體的電腦搭配使用。

## <a name="supported-upgrade-paths"></a>支援的升級路徑

下表列出 Windows 10 版本升級設定檔所支援的升級路徑。

| 從 | 升級至 |
|---|---|
| Windows 10 Pro | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 專業教育版 |
| Windows 10 專業版 N 版本 | Windows 10 教育版 N 版本 <br/>Windows 10 企業版 N 版本 <br/>Windows 10 專業教育版 N 版本 | 
| Windows 10 專業教育版 | Windows 10 Education | 
| Windows 10 專業教育版 N 版本 | Windows 10 教育版 N 版本 |
| Windows 10 Cloud | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro <br/>Windows 10 專業教育版 | 
| Windows 10 Cloud N 版本 | Windows 10 教育版 N 版本 <br/>Windows 10 企業版 N 版本 <br/>Windows 10 專業版 N 版本 <br/>Windows 10 專業教育版 N 版本 | 
| Windows 10 Enterprise | Windows 10 Education | 
| Windows 10 企業版 N 版本 | Windows 10 教育版 N 版本 | 
| Windows 10 Core | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 專業教育版 | 
| Windows 10 Core N 版本 | Windows 10 教育版 N 版本 <br/>Windows 10 企業版 N 版本 <br/>Windows 10 專業教育版 N 版本 | 
| Windows 10 Holographic | Windows 10 Holographic for Business |
| Windows 10 Mobile | Windows 10 Mobile Enterprise |

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)  (X) = not supported    
![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro Education|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro Education N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Cloud|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Cloud N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Enterprise|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Enterprise N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Core|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Core N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Mobile|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Holographic|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png) -->

## <a name="create-the-profile"></a>建立設定檔

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
3. 輸入下列內容：

    - **名稱**：為新的設定檔輸入描述性名稱。 例如，輸入類似 `Windows 10 edition upgrade profile` 或 `Windows 10 switch off S mode` 的內容。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取 [Windows 10 及更新版本]  。
    - **設定檔類型**：選取 [版本升級]  。
    - **設定**：輸入您要設定的設定。 如需所有設定的清單及其用途，請參閱：

        - [Windows 10 升級和 S 模式](edition-upgrade-windows-settings.md)
        - [Windows Holographic for Business](holographic-upgrade.md)

4. 選取 [確定]   > [建立]  儲存您的變更。

設定檔隨即建立，並顯示在清單中。 請確認會[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

## <a name="next-steps"></a>後續步驟

建立設定檔之後即可加以指派。 接下來，[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

檢視適用於 [Windows 10](edition-upgrade-windows-settings.md) 和 [Windows Holographic for Business](holographic-upgrade.md) 裝置的升級和 S 模式設定。
