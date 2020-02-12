---
title: Microsoft Intune 中 Windows 10 的傳遞最佳化設定 - Azure | Microsoft Docs
description: 設定您利用 Intune 管理的 Windows 10 裝置如何使用傳遞最佳化。 在 Intune 中，建立裝置組態設定檔，以從網際網路安裝更新。 另請參閱如何使用傳遞最佳化設定檔來取代現有更新通道。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/10/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 9fb4aab6b02c6ad6a5d2f18ca9d15beafc12d58a
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124804"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Microsoft Intune 中的傳遞最佳化設定

使用 Intune，您可以為 Windows 10 裝置使用傳遞最佳化設定，以減少那些裝置下載應用程式與更新時的頻寬耗用量。 設定傳遞最佳化作為裝置組態設定檔的一部分。  

本文描述如何設定傳遞最佳化設定，作為裝置組態設定檔的一部分。 在您建立設定檔之後，接著會將該設定檔指派或部署到您的 Windows 10 裝置。 

若要檢視 Intune 支援的傳遞最佳化設定清單，請參閱 [Intune 的傳遞最佳化設定](../delivery-optimization-settings.md)。  

若要了解 Windows 10 上的傳遞最佳化，請參閱 Windows 文件中的[傳遞最佳化更新](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)。  

## <a name="create-the-profile"></a>建立設定檔

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。

3. 輸入下列內容：

    - **名稱**：為新的設定檔輸入描述性名稱。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取 [Windows 10 及更新版本]  。
    - **設定檔類型**：選取 [傳遞最佳化]  。

4. 選擇 [設定]   > [設定]  ，並定義更新和應用程式的下載方式。 如需可用設定的資訊，請參閱 [Intune 的傳遞最佳化設定](../delivery-optimization-settings.md)。

5. 完成後，請選取 [確定]   > [建立]  以儲存變更。

設定檔隨即建立並顯示在清單中。 接下來，[指派設定檔](device-profile-assign.md)，然後[監視其狀態](device-profile-monitor.md)。

<!-- ## Move existing update rings to delivery optimization

**Delivery optimization** settings replace **Software updates – Windows 10 Update Rings**. Your existing update rings can be easily changed to use the **Delivery optimization** settings. To maintain the same settings when you create a delivery optimization profile, use the same *Delivery optimization download mode* and then set the same settings as you already use. However, you can choose to reconfigure delivery optimization settings to take advantage of the full range of addition settings that the Delivery Optimization profile can manage. 
-->

## <a name="remove-delivery-optimization-from-windows-10-update-rings"></a>從 Windows 10 更新通道移除傳遞最佳化

傳遞最佳化先前設定為軟體更新通道的一部分。 從 2019 年 2 月開始，傳遞最佳化設定已設定為傳遞最佳化裝置組態設定檔的一部分，其中包括的其他設定會影響裝置的軟體更新傳遞。 如果您還沒有這麼做，請透過將傳遞最佳化設定設定為 [未設定]  以將其從您的更新通道移除，然後使用傳遞最佳化設定檔來管理較大範圍的可用選項。

1. 建立傳遞最佳化裝置組態設定檔：

    1. 在 Microsoft Endpoint Manager 系統管理中心內，選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
    2. 輸入下列內容：

        - **名稱**：為新的設定檔輸入描述性名稱。
        - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
        - **平台**：選取 [Windows 10 及更新版本]  。
        - **設定檔類型**：選取 [傳遞最佳化]  。
        - **設定**：針對 [傳遞最佳化下載模式]  ，除非您想要變更套用到裝置的設定，否則請選擇現有軟體更新通道所使用的相同模式。 選項包括：
            - **未設定**
            - **只有 HTTP，沒有任何對等**
            - **HTTP 混合 (具有相同 NAT 後方之對等互連)**
            - **HTTP 混合 (具有跨私人群組的對等互連)**
            - **混合網際網路對等的 HTTP**
            - **無對等的簡式下載模式**
            - **略過模式**
    3. 設定您可能要管理的任何其他設定。

2. 將此新的設定檔指派至與現有軟體更新通道相同的裝置和使用者。 [指派設定檔](device-profile-assign.md)列出步驟。

3. 將現有軟體通道取消設定：
    1. 在 Microsoft Endpoint Manager 系統管理中心內，移至 [軟體更新]  > [Windows 10 更新通道]。
    2. 在清單中，選取您的更新通道。
    3. 在設定中，將 [傳遞最佳化下載模式]  設定成 [未設定]  。
    4. 按一下 [確定]   > [儲存]  來儲存您的變更。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。  
檢視 Intune 的[傳遞最佳化設定](../delivery-optimization-settings.md)。
