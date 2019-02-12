---
title: Microsoft Intune 中 Windows 10 的傳遞最佳化設定 - Azure | Microsoft Docs
description: 使用可在 Windows 10 和更新版裝置上取得的傳遞最佳化雲端服務，設定如何將軟體更新傳遞到您的裝置。 在 Intune 中，建立裝置組態設定檔，以從網際網路安裝更新。 另請參閱如何使用傳遞最佳化設定檔來取代現有更新通道。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f335c8acf9e979366fe75d1a3da2318b7ec46400
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836688"
---
# <a name="windows-10-and-newer-delivery-optimization-settings-in-microsoft-intune"></a>Microsoft Intune 中 Windows 10 (和更新版本) 的傳遞最佳化設定

> [!NOTE]
> **軟體更新 - Windows 10 更新通道**已由**傳遞最佳化**設定取代。 您現有的更新通道可以變更為使用 [傳遞最佳化] 設定。 本文中的[將現有的更新通道移轉至傳遞最佳化](#move-existing-update-rings-to-delivery-optimization)會列出步驟。 


此功能適用於下列平台：

- Windows 10 及更新版本

本文列出並描述您可以針對 Windows 10 裝置設定的所有傳遞最佳化設定。 這些設定會新增至裝置組態設定檔中，然後使用 Microsoft Intune 指派或部署到您的裝置。

[傳遞最佳化更新](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)是深入了解有關 Windows 10 傳遞最佳化的絕佳資源。

## <a name="create-the-profile"></a>建立設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務] > 篩選 [Intune] > 選取 [Intune]。

2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。

3. 輸入下列內容：

    - **名稱**：為新的設定檔輸入描述性名稱。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取平台：  

        - **Windows 10 及更新版本**

    - **設定檔類型**：選取 [傳遞最佳化]。
    - **設定**：選擇您想要的更新下載方式。 選項包括： 

        - **未設定**：終端使用者以自己的方法更新其裝置，可以使用 OS 提供的 [Windows Updates] 或 [傳遞最佳化] 設定。
        - **只有 HTTP，沒有任何對等**：只從網際網路取得更新。 不從您網路上的其他電腦 (稱為對等互連或對等) 取得更新。
        - **HTTP 混合 (具有相同 NAT 後方之對等互連)**：從網際網路和從您網路上的其他電腦取得更新。 
        - **HTTP 混合 (具有跨私人群組的對等互連)**：對等互連會發生於在相同 Active Directory 站台 (如果存在) 中或在相同網域中的裝置上。 選取此選項時，會在您的網路位址轉譯 (NAT) IP 位址之間對等互連。
        - **混合網際網路對等的 HTTP**：從網際網路和從您網路上的其他電腦取得更新。
        - **無對等的簡式下載模式**：從網際網路直接從更新擁有者 (如 Microsoft) 取得更新。 它不會連絡傳遞最佳化雲端服務。
        - **略過模式**：使用背景智慧型傳送服務 (BITS) 來取得更新。 不使用傳遞最佳化。

4. 完成後，請選取 [確定] > [建立] 以儲存變更。

設定檔隨即建立，並顯示在清單中。 接下來，[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

## <a name="move-existing-update-rings-to-delivery-optimization"></a>將現有的更新通道移轉至傳遞最佳化

**軟體更新 - Windows 10 更新通道**已由**傳遞最佳化**設定取代。 您輕鬆就能將現有的更新通道變更為使用**傳遞最佳化**設定。 步驟:

1. 建立傳遞最佳化組態設定檔：

    1. 在 Intune 中，選取 [裝置設定] > [設定檔] > [建立設定檔]。
    2. 輸入下列內容：

        - **名稱**：為新的設定檔輸入描述性名稱。
        - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
        - **平台**：選取 [Windows 10 及更新版本]。
        - **設定檔類型**：選取 [傳遞最佳化]。
        - **設定**：對於 [傳遞最佳化下載模式]，選擇現有軟體更新通道所使用的相同模式。 選項包括：
            - **未設定**
            - **只有 HTTP，沒有任何對等**
            - **HTTP 混合 (具有相同 NAT 後方之對等互連)**
            - **HTTP 混合 (具有跨私人群組的對等互連)**
            - **混合網際網路對等的 HTTP**
            - **無對等的簡式下載模式**
            - **略過模式**

2. 將此新的設定檔指派至與現有軟體更新通道相同的裝置和使用者。 [指派設定檔](device-profile-assign.md)列出步驟。

3. 將現有軟體通道取消設定：
    1. 在 Intune 中，移至 [軟體更新] > Windows 10 更新通道。
    2. 在清單中，選取您的更新通道。
    3. 在設定中，將 [傳遞最佳化下載模式] 設定成 [未設定]。
    4. 按一下 [確定] > [儲存] 來儲存您的變更。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
