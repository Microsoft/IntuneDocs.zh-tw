---
title: "設定行動裝置管理授權單位"
titlesuffix: Azure portal
description: "了解如何在 Intune 中設定行動裝置管理授權單位。 \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e042ccbc085b2cf511d3cd21f2da5e23299264a9
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2017
---
# <a name="set-the-mobile-device-management-authority"></a>設定行動裝置管理授權單位

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

行動裝置管理 (MDM) 授權單位設定會決定您管理裝置的方式。 身為 IT 系統管理員，您必須在使用者可以註冊裝置以進行管理之前，設定 MDM 授權單位。

可能的設定如下︰

- **Intune 獨立版** - 雲端版管理解決方案，可透過 Azure 入口網站設定。 包含 Intune 提供的完整功能集。 [在 Intune 主控台中設定 MDM 授權單位](#set-mdm-authority-to-intune)。

- **Intune 混合版** - Intune 雲端解決方案與 System Center Configuration Manager 的整合版。 您可以使用 Configuration Manager 主控台設定 Intune。 [在 Configuration Manager 中設定 MDM 授權單位](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription)。

- **Office 365 的行動裝置管理** - Office 365 與 Intune 雲端解決方案的整合版。 您可以從 Office 365 系統管理中心設定 Intune。 包含 Intune 獨立版提供的功能子集。 在 Office 365 系統管理中心中設定 MDM 授權單位。

>[!IMPORTANT]    
在 Configuration Manager 1610 版或更新版本及 Microsoft Intune 1705 版中，您可以在不需要連絡 Microsoft 支援服務的情況下變更 MDM 授權單位，且不需要取消註冊並重新註冊您現有的受管理裝置。 如需詳細資訊，請參閱[選擇錯誤的 MDM 授權單位設定時該怎麼辦](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting)。

## <a name="set-mdm-authority-to-intune"></a>將 MDM 授權單位設為 Intune

1. 在 [Azure 入口網站](https://portal.azure.com)中，選擇 [更多服務] > [監視 + 管理] > [Intune]。
2. 選取橙色橫幅，以開啟 [行動裝置管理授權單位] 設定。
3. 在 [行動裝置管理授權單位] 下，從下列選項中選擇您的 MDM 授權單位：
  - **Intune MDM 授權單位**
  - **Configuration Manager MDM 授權單位**
  - **無**

  ![Intune 設定行動裝置管理授權單位畫面的螢幕擷取畫面](media/set-mdm-auth.png)

  接著會顯示一則訊息指出您已成功將 Intune 設定為 MDM 授權單位。

## <a name="enable-device-enrollment"></a>啟用裝置註冊

將 Intune 設定為 MDM 授權單位時，使用者可以註冊個人擁有的裝置，以及使用下列方式來存取電子郵件這類資源，方法是安裝公司入口網站 (iOS 和 Android)、新增工作認證 (Windows)，或存取公司入口網站 (iOS、Android、macOS)。

不同的平台具有下列需求，才能啟用或簡化註冊：
- **iOS** - (必要) [取得 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)，然後[啟用公司擁有之 iOS 裝置的註冊](ios-enroll.md) (選擇性)。
- **Android** - (選擇性) [啟用 Android 工作設定檔](android-enroll.md)
- **Windows** - (選擇性) 啟用[自動註冊](windows-enroll.md)或[大量註冊](windows-bulk-enroll.md)
- **macOS** - 沒有任何需求


## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 憑證到期後的行動裝置清除

當行動裝置與 Intune 服務通訊時，會自動更新 MDM 憑證。 若行動裝置被抹除，或有一段時間無法與 Intune 服務通訊，便無法更新 MDM 憑證。 當 MDM 憑證過期 180 天後，該裝置便會從 Azure 入口網站上移除。
