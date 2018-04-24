---
title: 使用 Microsoft Intune - Azure 升級 Windows 10 裝置 | Microsoft Docs
description: 在 Microsoft Intune 中建立裝置設定檔，將 Windows 10 裝置升級至較新版本。 另請參閱 Windows 10 專業版、N 版本、教育版、雲端版、企業版、核心版、全像攝影版和行動裝置版的支援升級路徑。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 994ab8e7d955d18b293e4d9e9661e0c44baaaa1f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="configure-windows-10-edition-upgrade-profile-in-intune"></a>在 Intune 中設定 Windows 10 版本升級設定檔
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

在 Intune 中設定升級設定檔以將執行 Windows 10 版本的裝置自動升級為不同的版本。 另請參閱支援的升級路徑。

## <a name="before-you-begin"></a>開始之前
將裝置升級至最新版本之前，您需要下列其中一項：

- 可以在您以原則設為目標的所有裝置上 (適用於 Windows 10 Desktop 版本)，安裝更新 Windows 版本的有效產品金鑰。 您可以使用多次啟用金鑰 (MAK) 或金鑰管理伺服器 (KMS) 金鑰，或 Microsoft 授權檔案，其中包含在您以原則為目標的所有裝置上 (適用於 Windows 10 行動裝置版與 Windows 10 全像攝影版)，安裝更新 Windows 版本的授權資訊。
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

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>建立內含裝置限制設定的裝置設定檔
1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 依序選取 [裝置設定]、[設定檔]，然後選取 [建立設定檔]。
4. 輸入版本升級設定檔的 [名稱] 和 [描述]。
5. 從 [平台] 下拉式清單中，選擇 [Windows 10 及更新版本]。
6. 從 [設定檔類型] 下拉式清單中，選擇 [版本升級]。
7. 在 [版本升級] 內容中，輸入下列設定：
   - **要升級的目標版本** - 從下拉式清單中，選取要升級的目標裝置之 Windows 10 桌面版、Windows 10 全像攝影版或 Windows 10 行動裝置版的版本。
   - **產品金鑰** - 輸入您從 Microsoft 收到的產品金鑰，可用來升級所有 Windows 10 Desktop 目標裝置。 
    建立包含產品金鑰的原則之後，即無法更新金鑰，且會基於安全性考量而隱藏。 若要變更產品金鑰，請再次輸入完整金鑰。
   - **授權檔** - 選擇 [瀏覽] 以選取您從 Microsoft 收到的授權檔。 這個授權檔包含您要將目標裝置升級的 Windows 全像攝影版或 Windows 10 行動裝置版的授權資訊。
8. 完成時，請選取 [建立] 以儲存變更。

設定檔隨即建立，並列在設定檔中。

## <a name="next-steps"></a>接下來的步驟

若要將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。

>[!NOTE]
>如果您稍後移除原則指派，裝置上的 Windows 版本不會還原，而且會繼續正常運作。