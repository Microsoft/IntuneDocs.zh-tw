---
title: 設定註冊狀態頁面
titleSuffix: Microsoft Intune
description: 歡迎註冊 Windows 10 裝置的使用者。
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
ms.custom: intune-azure
ms.openlocfilehash: f5460db2d646d8bd417baa50d8188acbf69a251d
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48827984"
---
# <a name="set-up-an-enrollment-status-page"></a>設定註冊狀態頁面
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
在裝置安裝期間，註冊狀態頁面會顯示裝置上的安裝資訊。 某些應用程式、設定檔及憑證在使用者註冊時可能無法完全安裝。 狀態頁面可協助使用者了解他們的裝置在註冊期間和之後的狀態。 您可以為所有使用者開啟狀態頁面，或建立以特定使用者群組為目標的設定檔。  您可以設定設定檔，以顯示安裝進度、在安裝完成之前封鎖使用、允許重設等等。
 
## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>為所有使用者開啟預設註冊狀態頁面

若要為所有使用者開啟註冊狀態頁面，請遵循下列步驟。
 
1.  在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [註冊狀態頁面 (預覽)]。
2.  在 [註冊狀態頁面] 刀鋒視窗中，選擇 [預設] > [設定]。
3.  針對 [顯示應用程式和設定檔安裝進度]，選擇 [是]。
4.  選擇您想要開啟的其他設定，然後選擇 [儲存]。

## <a name="create-enrollment-status-page-profile-to-target-specific-users"></a>建立以特定使用者為目標的註冊狀態頁面設定檔

1.  在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [註冊狀態頁面 (預覽)] > [建立設定檔]。
2. 提供 [名稱] 和 [描述]。
3. 選擇 **[建立]**。
4. 在 [註冊狀態頁面] 清單選擇新的設定檔。
5. 選擇 指派 > 選取群組 > 選擇您想要採用這個設定檔的群組 > 選取 >  儲存。
6. 選擇 [設定] > 選擇您想要套用至這個設定檔的設定 > [儲存]。


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
- 尚未追蹤連線設定檔 (VPN 和 Wi-Fi)，因此一律會是 "0/0"。
- 尚未追蹤憑證，因此一律會是 "0/0"。

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

## <a name="next-steps"></a>接下來的步驟
設定 Windows 註冊頁面之後，了解如何管理 Windows 裝置。 如需詳細資訊，請參閱[什麼是 Microsoft Intune 裝置管理？](https://docs.microsoft.com/intune/device-management)