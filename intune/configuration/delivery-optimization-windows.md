---
title: Microsoft Intune 中 Windows 10 的傳遞最佳化設定 - Azure | Microsoft Docs
description: 設定您利用 Intune 管理的 Windows 10 裝置如何使用傳遞最佳化。 在 Intune 中，建立裝置組態設定檔，以從網際網路安裝更新。 另請參閱如何使用傳遞最佳化設定檔來取代現有更新通道。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 7d94a2c7e47b3cfcc9f4592faf0a4c2a09a24ac4
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72495236"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Microsoft Intune 中的傳遞最佳化設定

使用 Intune，您可以使用 Windows 10 裝置的傳遞最佳化設定，以減少這些裝置下載應用程式和更新時的頻寬耗用量。 傳遞最佳化會設定為裝置組態設定檔的一部分。  

本文描述如何設定傳遞最佳化設定，作為裝置組態設定檔的一部分。 在您建立設定檔之後，接著會將該設定檔指派或部署到您的 Windows 10 裝置。 

如需 Intune 支援的傳遞最佳化設定清單，請參閱 [Intune 的傳遞最佳化設定](../delivery-optimization-settings.md)。  

若要了解 Windows 10 上的傳遞最佳化，請參閱 Windows 文件中的[傳遞最佳化更新](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)。  


> [!NOTE]
> **軟體更新 - Windows 10 更新通道**已由**傳遞最佳化**設定取代。 您現有的更新通道可以變更為使用 [傳遞最佳化]  設定。 [將現有的更新通道移轉至傳遞最佳化](#move-existing-update-rings-to-delivery-optimization) (在本文中) 
## <a name="create-the-profile"></a>建立設定檔

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。

2. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。

3. 輸入下列內容：

    - **名稱**：為新的設定檔輸入描述性名稱。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取平台：  

        - **Windows 10 及更新版本**

    - **設定檔類型**：選取 [傳遞最佳化]  。
    - **設定**：設定定義更新和應用程式下載方式的設定。 如需可用設定的資訊，請參閱 [Intune 的傳遞最佳化設定](../delivery-optimization-settings.md)。

4. 完成後，請選取 [確定]   > [建立]  以儲存變更。

設定檔隨即建立並顯示在清單中。 接下來，[指派設定檔](device-profile-assign.md)，然後[監視其狀態](device-profile-monitor.md)。

## <a name="move-existing-update-rings-to-delivery-optimization"></a>將現有的更新通道移轉至傳遞最佳化

**傳遞最佳化**設定取代了**軟體更新 - Windows 10 更新通道**。 您輕鬆就能將現有的更新通道變更為使用**傳遞最佳化**設定。 若要在建立傳遞最佳化設定檔時維持相同的設定，請使用相同的「傳遞最佳化下載模式」  ，然後設定與您所使用項目相同的設定。 不過，您可以選擇重新設定傳遞最佳化設定，以利用傳遞最佳化設定檔可管理的完整其他設定。

1. 建立傳遞最佳化組態設定檔：

    1. 在 Intune 中，選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
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
1. 將此新的設定檔指派至與現有軟體更新通道相同的裝置和使用者。 [指派設定檔](device-profile-assign.md)列出步驟。

3. 將現有軟體通道取消設定：
    1. 在 Intune 中，移至 [軟體更新]  > Windows 10 更新通道。
    2. 在清單中，選取您的更新通道。
    3. 在設定中，將 [傳遞最佳化下載模式]  設定成 [未設定]  。
    4. 按一下 [確定]   > [儲存]  來儲存您的變更。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。  
檢視 Intune 的[傳遞最佳化設定](../delivery-optimization-settings.md)。
