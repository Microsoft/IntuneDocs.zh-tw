---
title: 透過 Microsoft Intune 在 Windows 10 裝置上升級或使用 S 模式 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中建立裝置設定檔，將 Windows 10 裝置升級至不同的版本。 例如，您可以將 Windows 10 專業版升級至 Windows 10 企業版。 您也可以使用組態設定檔，在裝置上啟用或切換移出 S 模式。 另請參閱 Windows 10 專業版、N 版本、教育版、雲端版、企業版、核心版、全像攝影版和行動裝置版的支援升級路徑。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: eb44647e50e406b9ef5052c576660c9b7eebf6dd
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189753"
---
# <a name="use-a-configuration-profile-to-upgrade-windows-10-or-switch-from-s-mode-in-intune"></a>在 Intune 中使用組態設定檔升級 Windows 10 或切換移出 S 模式
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

在 Intune 中設定升級設定檔以將執行 Windows 10 版本的裝置自動升級為不同的版本。 另請參閱支援的升級路徑。

## <a name="before-you-begin"></a>開始之前
將裝置升級至最新版本之前，您需要下列必要元件：

- 可以在您以原則設為目標的所有裝置上 (適用於 Windows 10 Desktop 版本)，安裝更新 Windows 版本的有效產品金鑰。 您可以使用多次啟用金鑰 (MAK) 或金鑰管理伺服器 (KMS) 金鑰。 針對 Windows 10 行動裝置版與 Windows 10 全像攝影版，您可以使用 Microsoft 授權檔案，其中包含在您設為以原則目標之所有裝置上安裝更新版 Windows 的授權資訊。
- 會在 Microsoft Intune 中註冊您指派原則的 Windows 10 裝置。 您無法將版本升級原則和執行 Intune 電腦用戶端軟體的電腦搭配使用。

## <a name="supported-upgrade-paths"></a>支援的升級途徑
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


<!-- Testing a new table on 3/5/18 

The following lists provide the supported upgrade paths for the Windows 10 edition upgrade profile. The Windows 10 edition to upgrade to is in bold followed by the list of supported editions that you can upgrade from:

**Windows 10 Education**
- Windows 10 Pro
- Windows 10 Pro Education
- Windows 10 Cloud
- Windows 10 Enterprise
- Windows 10 Core
    
**Windows 10 Education N edition**    
- Windows 10 Pro N edition
- Windows 10 Pro Education N edition
- Windows 10 Cloud N edition
- Windows 10 Enterprise N edition
- Windows 10 Core N edition
    
**Windows 10 Enterprise**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Enterprise N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition
    
**Windows 10 Pro**
- Windows 10 Cloud
    
**Windows 10 Pro N edition**
- Windows 10 Cloud N edition
    
**Windows 10 Pro Education**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Pro Education N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition

**Windows 10 Holographic for Business**
- Windows 10 Holographic

**Windows 10 Mobile Enterprise**
- Windows 10 Mobile -->

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/check_grn.png)  (X) = not supported    
![unsupported](./media/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)   |![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Mobile|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|
|Holographic|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png) -->

## <a name="upgrade-the-edition"></a>升級版本

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入設定檔的**名稱**和**描述**。 例如，輸入類似 `Windows 10 edition upgrade` 的內容
4. 針對 [平台]，選取 [Windows 10 及更新版本]。
5. 針對 [設定檔類型]，選取 [版本升級]。
6. 在 [版本升級] 內容中，輸入下列設定：

   - **要升級到的版本**：選取您要升級到的 Windows 10 版本。 由此原則設為目標的裝置會升級至您選擇的版本。
   - **產品金鑰**：輸入您從 Microsoft 收到的產品金鑰。 建立包含產品金鑰的原則之後，即無法更新金鑰，且會基於安全性考量而隱藏。 若要變更產品金鑰，請再次輸入完整金鑰。
   - **授權檔案**：針對**商務用 Windows 10 全像攝影版**或 **Windows 10 行動裝置版**，選擇 [瀏覽] 來選取您從 Microsoft 收到的授權檔案。 這個授權檔案包含您要將目標裝置升級到的版本授權資訊。

7. 按一下 [確定] 以儲存您的變更。 選取 [建立] 以建立設定檔。

## <a name="switch-out-of-s-mode"></a>切換移出 S 模式

[Windows 10 S 模式](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode)是專為安全性和效能所設計。 如果您的裝置只會執行來自 Microsoft Store 的應用程式，則您可以使用 S 模式來協助確保裝置安全。 如果您的裝置需要 Microsoft Store 中沒有的應用程式，則您會切換移出 S 模式。 切換移出 S 模式是單向作業。 一旦您切換移出 S 模式，就無法回到 Windows 10 S 模式。

下列步驟示範如何建立設定檔，以控制 Windows 10 (1809 或更新版本) 裝置上的 S 模式。

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入設定檔的**名稱**和**描述**。 例如，輸入類似 `Windows 10 switch off S mode` 的內容
4. 針對 [平台]，選取 [Windows 10 及更新版本]。
5. 針對 [設定檔類型]，選取 [版本升級]。
6. 選取 [Mode switch (Windows Insider only)] \(模式切換 (僅限 Windows 測試人員)\)，然後設定 [Switch out of S mode] \(切換移出 S 模式\) 屬性。 選項包括：

    - **No configuration** \(沒有設定\)：S 模式裝置會保持在 S 模式。 終端使用者可以將裝置切換移出 S 模式。
    - **Keep in S mode** \(保持在 S 模式\)：防止終端使用者將裝置切換移出 S 模式。
    - **Switch** \(切換\)：將裝置切換移出 S 模式。

7. 按一下 [確定] 以儲存您的變更。 選取 [建立] 以建立設定檔。

設定檔隨即建立，並列在設定檔中。

## <a name="next-steps"></a>接下來的步驟

[指派這個設定檔](device-profile-assign.md)給您的群組。

>[!NOTE]
>如果您稍後移除原則指派，裝置上的 Windows 版本不會還原，而且會繼續正常運作。
