---
title: 設定註冊狀態頁面
titleSuffix: Microsoft Intune
description: 針對註冊 Windows 10 裝置的使用者設定問候語頁面。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: f01009a0cb35f4270bdb1e768ee781172c8bfa2f
ms.sourcegitcommit: 17f58d35a6bdff3e179662f3731fc74d39144470
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2019
ms.locfileid: "55105182"
---
# <a name="set-up-an-enrollment-status-page"></a>設定註冊狀態頁面
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
在使用 Intune 進行裝置設定期間，[註冊狀態] 頁面會顯示裝置上的安裝資訊。 某些應用程式、設定檔及憑證在使用者完成裝置的全新註冊登入時可能無法安裝。 註冊狀態頁面可協助使用者了解其裝置在裝置設定期間的狀態。 您可以建立多個註冊狀態頁面設定檔，並將其套用至不同的群組。 設定檔可設定為：
- 顯示安裝進度。
- 封鎖使用直到安裝完成。
- 指定裝置設定失敗時使用者可採取的動作。

您也可以設定每個設定檔的優先順序，來解決將設定檔指派給相同使用者或裝置時所發生的衝突。

 
## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>為所有使用者開啟預設註冊狀態頁面

若要開啟註冊狀態頁面，請遵循下列步驟。
 
1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [註冊狀態頁面 (預覽)]。
2. 在 [註冊狀態頁面] 刀鋒視窗中，選擇 [預設] > [設定]。
3. 針對 [顯示應用程式和設定檔安裝進度]，選擇 [是]。
4. 選擇您想要開啟的其他設定，然後選擇 [儲存]。

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>建立註冊狀態頁面設定檔並指派給群組

1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [註冊狀態頁面 (預覽)] > [建立設定檔]。
2. 提供 [名稱] 和 [描述]。
3. 選擇 **[建立]**。
4. 在 [註冊狀態頁面] 清單選擇新的設定檔。
5. 選擇 指派 > 選取群組 > 選擇您想要採用這個設定檔的群組 > 選取 >  儲存。
6. 選擇 [設定] > 選擇您想要套用至這個設定檔的設定 > [儲存]。

## <a name="set-the-enrollment-status-page-priority"></a>設定註冊狀態頁面優先順序

一個裝置或使用者可能位於多個群組，並具有多個註冊狀態頁面設定檔。 為了解決此衝突，您可以設定每個設定檔的優先順序。 如果某人具有多個註冊狀態頁面設定檔，則只會套用優先順序最高的設定檔。

1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [註冊狀態頁面 (預覽)]。
2. 將滑鼠移到清單中的設定檔上方。
3. 使用三個垂直點，將設定檔拖曳到所要的清單位置。

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>封鎖對裝置的存取，直到已安裝特定應用程式

您可以指定需要先安裝哪些應用程式，使用者才能存取桌面。

1. 在 Intune 中，選擇 [裝置註冊] > [Windows 註冊] > [註冊狀態頁面 (預覽)]。
2. 選擇定檔 > [設定]。
3. 對於 [顯示應用程式與設定檔的安裝進度]，選擇 [是]。
4. 對於 [所有應用程式與設定檔未完成安裝之前，禁止使用裝置]，選擇 [是]。
5. 對於 [若這些必要的應用程式已指派給使用者/裝置，請在安裝這些應用程式之前，封鎖裝置使用它們]，選擇 [已選取]。
 6. 選擇 [選取應用程式] > 選擇應用程式 > [選取] > [儲存]。

## <a name="enrollment-status-page-tracking-information"></a>註冊狀態頁面追蹤資訊

狀態頁面會追蹤裝置準備、裝置設定和帳戶設定等資訊。

### <a name="device-preparation"></a>裝置準備

針對裝置準備，註冊狀態頁面會追蹤信賴平台模組 (TPM) 金鑰認證 (若適用)、加入 Azure Active Directory 的進度，以及註冊 Intune 的進度。

### <a name="device-setup"></a>裝置設定

針對裝置設定，註冊狀態頁面會追蹤下列項目，如果它們指派給所有裝置的話：
- 安全性原則
    - 適用於所有註冊的一個設定服務提供者 (CSP) 。
    - 這裡不會追蹤 Intune 所設定的實際 CSP。
- 應用程式
    - 每個機器的特定業務 (LOB) MSI 應用程式。
    - 具有安裝內容 = 裝置的 LOB 存放區應用程式。
    - 具有安裝內容 = 裝置的離線存放區 LOB 存放區應用程式。
- 連線設定檔
    - 指派給**所有裝置**，或是註冊裝置為其成員之裝置群組的 VPN 或 Wi-Fi 設定檔，但僅適用於 Autopilot 裝置
- 指派給**所有裝置**，或是註冊裝置為其成員之裝置群組的憑證設定檔，但僅適用於 Autopilot 裝置

### <a name="account-setup"></a>帳戶設定
對於帳戶設定，註冊狀態頁面會追蹤下列項目：
- 安全性原則
    - 適用於所有註冊的一個 CSP 。
    - 這裡不會追蹤 Intune 所設定的實際 CSP。
- 應用程式
    - 指派給所有裝置、所有使用者，或是註冊裝置的使用者為其成員之使用者群組的每個使用者 LOB MSI 應用程式。
    - 指派給所有使用者，或是註冊裝置的使用者為其成員之使用者群組的每個機器 LOB MSI 應用程式。
    - 指派給下列任何一項的 LoB 市集應用程式、線上市集應用程式和離線市集應用程式：
        - 所有裝置
        - 所有使用者
        - 使用者群組，其中註冊裝置的使用者為其成員，且安裝內容設定至「使用者」。
- 連線設定檔
    - 指派給所有使用者，或是註冊裝置的使用者為其成員之使用者群組的 VPN 或 Wi-Fi 設定檔。
- 憑證
    - 指派給所有使用者，或是註冊裝置的使用者為其成員之使用者群組的憑證設定檔。

## <a name="next-steps"></a>後續步驟
設定 Windows 註冊頁面之後，了解如何管理 Windows 裝置。 如需詳細資訊，請參閱[什麼是 Microsoft Intune 裝置管理？](https://docs.microsoft.com/intune/device-management)
