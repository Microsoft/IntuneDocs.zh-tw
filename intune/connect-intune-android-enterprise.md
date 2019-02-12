---
title: 將 Intune 帳戶連線至 Android 企業帳戶
titlesuffix: Microsoft Intune
description: 了解如何將 Intune 帳戶連線至 Android 企業帳戶。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 421d9c56f959fe30d35c0c55ce34017a7a0ba5a6
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838253"
---
# <a name="connect-your-intune-account-to-your-android-enterprise-account"></a>將 Intune 帳戶連線至 Android 企業帳戶

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

為了支援 [Android 工作設定檔裝置](android-work-profile-enroll.md)、[Android 完全受控裝置](android-fully-managed-enroll.md)和 [Android 專用裝置](android-kiosk-enroll.md)，您必須將 Intune 租用戶帳戶連線至 Android 企業帳戶。  

> [!NOTE]
> 因為 Google 和 Microsoft 網域之間的互動，這個步驟可能需要調整瀏覽器設定。  請確定 "portal.azure.com" 和 "play.google.com" 位於您瀏覽器中相同的安全性區域。

1. 如果尚未這麼做，請將[行動裝置管理授權單位](mdm-authority-set.md)設定為 **Microsoft Intune**，以針對行動裝置管理做準備。
2. 登入 [Azure 入口網站中的 Intune](https://aka.ms/intuneportal)，選擇 [裝置註冊] > [Android 註冊] > [受控 Google Play]。  如果您使用自訂的 Intune 管理員角色，則存取這個會需要組織讀取和更新的權限。
   
   ![Android 企業註冊畫面](./media/android-work-bind.png)

3. 選擇 [我同意] 將權限授與 Microsoft，以[將使用者和裝置資訊傳送給 Google](data-intune-sends-to-google.md)。 
   
4. 選擇 [啟動 Google 以立即連線] 以開啟受控 Google Play 網站。 在瀏覽器的新索引標籤中開啟網站。
  
5. 在 Google 的登入頁面上，輸入要與此租用戶之所有 Android 企業管理工作建立關聯的 Google 帳戶。 這是貴公司 IT 管理員共用的 Google 帳戶，可以在 Google Play 主控台中管理及發佈應用程式。 您可以使用現有的 Google 帳戶或建立新帳戶。 您選擇的帳戶絕不能與 G 套件網域建立關聯性。
    
    > [!Note]
    > 若您使用 Microsoft Edge 瀏覽器，請按一下右上角的 [登入] 來登入您的 Google 帳戶。

6. 提供您的公司名稱作為**組織名稱**。 針對**企業行動管理 (EMM) 提供者**，應該顯示 **Microsoft Intune**。

7. 同意 Android 合約，然後選擇 [確認]。 您的要求將會被處理。

## <a name="disconnect-your-android-enterprise-administrative-account"></a>中斷與 Android 企業系統管理帳戶的連線

您可以關閉 Android 企業註冊和管理。 若要這樣做，您必須先淘汰任何已註冊的 Android 工作設定檔裝置。 然後，在 Intune 管理主控台中選擇 [中斷連線]，移除所有已註冊之 Android 工作設定檔裝置和 Kiosk 裝置的註冊。 這也會移除 Android 企業帳戶與 Intune 之間的關聯性。

1. 以 Intune 系統管理員的身分，在 [Azure 入口網站](https://portal.azure.com)中選擇 [所有服務] > [監視 + 管理] > [Intune]。
2. 選擇 [裝置註冊] > [Android 註冊] > [受控 Google Play] > [中斷連線]。
3. 選擇 [是] 以中斷連線，然後從 Intune 取消註冊所有的 Android 企業裝置。

## <a name="next-steps"></a>後續步驟

連線至 Android 企業帳戶之後，您可以[設定 Android 工作設定檔裝置](android-work-profile-enroll.md)及[設定 Android kiosk 裝置](android-kiosk-enroll.md)。
