---
title: 如何從 Intune 移除 Android 裝置 | Microsoft Docs
description: 從 Intune 公司入口網站移除 Android 裝置
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8f2e9313cf2a4d639096f783b895596fc2535649
ms.sourcegitcommit: 884654da8e72a63bfaea6b5def6c7891b065f251
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163538"
---
# <a name="unenroll-your-android-device-from-management"></a>將您的 Android 裝置取消註冊管理  

移除已註冊的 Android 裝置，使其不再受您組織管理。 本文說明如何從公司入口網站應用程式移除裝置。 移除裝置之後：  

* 裝置將無法存取您組織的受保護資料和資源。
* 裝置不會再出現於公司入口網站中。
* 您無法從公司入口網站安裝應用程式。
* 您在新增裝置時變更的任何裝置設定 (例如停用相機或要求特定密碼長度) 皆會失效。  

> [!NOTE]
> 您無法從 Microsoft Intune 應用程式取消註冊或移除公司擁有的裝置。 裝置是在初始裝置設定期間註冊，而且必須註冊才能存取您組織的資源。  

1. 在公司入口網站中，移至右上角並點選三個垂直點。 動作功能表隨即開啟。

   ![Android 版公司入口網站應用程式的螢幕擷取畫面，右上角是開啟的動作功能表。 新的 [移除公司入口網站] 選項是第三個選項，位於 [我的設定檔] 和 [設定] 底下，在 [條款及條件]、[說明與意見反應] 和 [關於] 之上。](./media/android_remove_cp_menu_action_after_1705.png)

2. 點選 [移除公司入口網站]  。  

3. 隨即顯示一則訊息，其中包含取消註冊裝置之後續情況的資訊。 點選 [確定]  確認您要從公司入口網站移除裝置。

   ![從動作功能表選取新的 [移除公司入口網站] 選項後所提供的確認螢幕擷取畫面。](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="remove-data-collected-by-the-company-portal-app"></a>移除公司入口網站應用程式所收集的資料  

移除 Android 版公司入口網站應用程式在您裝置上安裝的所有資料：

- 點選 [應用程式]   > [應用程式名稱]   > [清除資料]  ，以清除應用程式資料。
- 刪除下列資料夾：\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal。

## <a name="uninstall-the-company-portal-app"></a>解除安裝公司入口網站應用程式

公司入口網站是裝置管理應用程式。 您必須先將裝置取消註冊管理，才能解除安裝。 完成後，請點選並按住公司入口網站應用程式圖示，直到您看到 [解除安裝]  。 點選 [解除安裝]  以從您的裝置移除應用程式。  

或者，點選 [設定]   > [應用程式]   > [公司入口網站]   > [解除安裝]  。  

### <a name="remove-the-company-portal-app-as-a-device-administrator"></a>以裝置系統管理員身分移除公司入口網站應用程式

非到萬不得已時，您可以透過裝置系統管理員身分從裝置解除安裝應用程式。  

如果您的裝置屬公司所擁有，您的組織可能會要求裝置上隨時有公司入口網站。 如果您將它解除安裝，在重新安裝應用程式之前，您可能無法存取受保護的公司資源 (例如電子郵件、應用程式、Wi-Fi 或 VPN)。 如需安裝、更新或移除必要應用程式的詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](/intune/apps/apps-add#apps-that-are-added-automatically-by-intune)。

以下示範如何透過裝置系統管理員身分停用公司入口網站。 您 Android 裝置上每項設定的實際名稱可能會有所不同。  

**選項 1**：  

1. 選取 [設定]   > [安全性]   > [其他安全性設定]   > [裝置系統管理員]  。  
2. 清除 [公司入口網站]  選項。  

**選項 2**：

1. 選取 [設定]   > [Lock screen and security] \(鎖定螢幕和安全性\)   > [Other security settings] \(其他安全性設定\)   > [Device admin apps] \(裝置系統管理員應用程式\)  。
2. 清除 [公司入口網站]  選項。

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。
