---
title: 設定註冊狀態頁面
titleSuffix: Microsoft Intune
description: 歡迎註冊 Windows 10 裝置的使用者。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/17/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c6604c35cebdad4341f27a51db1a4c735f9a9818
ms.sourcegitcommit: 6bd5867c41fb5288fde114dbfcc127dd206f7148
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="set-up-an-enrollment-status-page"></a>設定註冊狀態頁面
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
在裝置安裝期間，註冊狀態頁面會顯示使用者裝置上的安裝狀態資訊。 某些應用程式、設定檔及憑證在使用者註冊時可能無法完全安裝。 狀態頁面可協助使用者了解他們的裝置在註冊期間和之後的狀態。 您可以為所有使用者開啟狀態頁面，以及防止使用者使用裝置，直到所有指派的應用程式和設定檔都已安裝為止。
 
若要為所有使用者開啟註冊狀態頁面，請遵循下列步驟。
 
1.  在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [註冊狀態頁面 (預覽)]。
2.  在 [註冊狀態頁面] 刀鋒視窗中，選擇 [預設] > [設定]。
3.  針對 [顯示應用程式和設定檔安裝進度]，選擇 [是]。
4.  選擇您想要開啟的其他設定，然後選擇 [儲存]。
 
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
- 尚未追蹤連線設定檔 (VPN 和 Wi-Fi)，因此這些一律會是 "0/0"。
- 尚未追蹤憑證，因此這些一律會是 "0/0"。

### <a name="account-setup"></a>帳戶設定
對於帳戶設定，註冊狀態頁面會追蹤下列項目：
- 安全性原則
    - 適用於所有註冊的一個 CSP 。
    - 這裡不會追蹤 Intune 所設定的實際 CSP。
- 應用程式
    - 指派給所有裝置、所有使用者，或是註冊裝置的使用者為其成員之使用者群組的每個使用者 LOB MSI 應用程式。
    - 指派給所有使用者，或是註冊裝置的使用者為其成員之使用者群組的每個機器 LOB MSI 應用程式。
    - 指派給所有裝置、所有使用者，或是註冊裝置的使用者為其成員且安裝內容等於使用者之使用者群組的 LOB 存放區應用程式。
    - 指派給所有裝置、所有使用者，或是註冊裝置的使用者為其成員且安裝內容等於使用者之使用者群組的連線存放區應用程式。
    - 指派給所有裝置、所有使用者，或是註冊裝置的使用者為其成員且安裝內容等於使用者之使用者群組的離線存放區應用程式。
- 連線設定檔
    - 指派給所有使用者，或是註冊裝置的使用者為其成員之使用者群組的 VPN 或 Wi-Fi 設定檔。
- 憑證
    - 指派給所有使用者，或是註冊裝置的使用者為其成員之使用者群組的憑證設定檔。

## <a name="next-steps"></a>接下來的步驟
設定 Windows 註冊頁面之後，了解如何管理 Windows 裝置。 如需詳細資訊，請參閱[什麼是 Microsoft Intune 裝置管理？](https://docs.microsoft.com/intune/device-management)