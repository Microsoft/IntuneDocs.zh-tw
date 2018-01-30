---
title: "使用 Intune 設定 Windows 10 版本升級"
titlesuffix: Azure portal
description: "了解如何使用 Intune，將您管理的 Windows 10 裝置升級到其他版本。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 12/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8581aea9db4c04efda5fe9f3281be95330bcd2e2
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-configure-windows-10-edition-upgrades-in-microsoft-intune"></a>如何在 Microsoft Intune 中設定 Windows 10 版本升級
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用本文中的資訊來了解如何設定 Windows 10 版本升級設定檔。 此設定檔能讓您將執行 Windows 10 版本的裝置自動升級為不同的版本。 

## <a name="before-you-start"></a>開始之前
在開始將裝置升級至最新版本之前，您需要下列其中一項：

- 可以在您以原則設為目標的所有裝置上 (適用於 Windows 10 Desktop 版本)，安裝新版本 Windows 的有效產品金鑰。 您可以使用多次啟用金鑰 (MAK) 或金鑰管理伺服器 (KMS) 金鑰，或來自 Microsoft 的授權檔案，其中包含在您以原則為目標的所有裝置上 (適用於 Windows 10 行動裝置版與 Windows 10 全像攝影版)，安裝新版 Windows 的授權資訊。
- 必須在 Microsoft Intune 中註冊您指派原則的目標 Windows 10 裝置。 您無法將版本升級原則和執行 Intune 電腦用戶端軟體的電腦搭配使用。

## <a name="supported-upgrade-paths-for-the-windows-10-edition-upgrade-profile"></a>Windows 10 版本升級設定檔所支援的升級路徑
下列清單提供 Windows 10 版本升級設定檔所支援的升級路徑。 要升級至的 Windows 10 版本會以粗體顯示，並於下方列出支援升級至該版本的所有版本：

**Windows 10 教育版**
- Windows 10 Pro
- Windows 10 專業教育版
- Windows 10 Cloud
- Windows 10 Enterprise
- Windows 10 Core
    
**Windows 10 教育版 N 版本**    
- Windows 10 專業版 N 版本
- Windows 10 專業教育版 N 版本
- Windows 10 Cloud N 版本
- Windows 10 企業版 N 版本
- Windows 10 Core N 版本
    
**Windows 10 企業版**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 企業版 N 版本**
- Windows 10 專業版 N 版本
- Windows 10 Cloud N 版本
- Windows 10 Core N 版本
    
**Windows 10 專業版**
- Windows 10 Cloud
    
**Windows 10 專業版 N 版本**
- Windows 10 Cloud N 版本
    
**Windows 10 專業教育版**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 專業教育版 N 版本**
- Windows 10 專業版 N 版本
- Windows 10 Cloud N 版本
- Windows 10 Core N 版本

**Windows 10 Holographic for Business**
- Windows 10 Holographic

**Windows 10 行動裝置企業版**
- Windows 10 Mobile

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
1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置設定]。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
3. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗中，為教育升級設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選擇 [Windows 10 及更新版本]。
6. 從 [設定檔類型] 下拉式清單中，選擇 [版本升級]。
7. 在 [版本升級] 刀鋒視窗中，進行下列設定：
    - **要升級的目標版本** - 從下拉式清單中，選取希望目標裝置升級的 Windows 10 桌面版、Windows 10 全像攝影版或 Windows 10 行動裝置版之版本。
    - **產品金鑰** - 指定您從 Microsoft 取得的產品金鑰，可用來升級所有 Windows 10 Desktop 目標裝置。<br>建立包含產品金鑰的原則之後，稍後便無法再編輯該產品金鑰。 這是因為金鑰基於安全性考量而隱藏。 若要變更產品金鑰，您必須再次輸入完整金鑰。
    - **授權檔案** - 選擇 [瀏覽] 以選取您從 Microsoft 取得的授權檔，其中包含要升級目標裝置的 Windows 全像攝影版或 Windows 10 行動裝置版的授權資訊。
8. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

設定檔隨即建立，並出現在 [設定檔清單] 刀鋒視窗上。

## <a name="next-steps"></a>接下來的步驟

若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。

>[!NOTE]
>如果您稍後移除原則指派，裝置上的 Windows 版本不會還原，而且會繼續正常運作。

