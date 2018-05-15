---
title: 設定行動裝置管理授權單位
titlesuffix: Microsoft Intune
description: 在 Intune 中設定行動裝置管理授權單位。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f903e9dfe5fb30f45806aac5694171814492f2e
ms.sourcegitcommit: 0f1a5d6e577915d2d748d681840ca04a0a2604dd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="set-the-mobile-device-management-authority"></a>設定行動裝置管理授權單位

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

行動裝置管理 (MDM) 授權單位設定會決定您管理裝置的方式。 身為 IT 系統管理員，您必須在使用者可以註冊裝置以進行管理之前，設定 MDM 授權單位。

可能的設定如下︰

- **Intune 獨立版** - 雲端版管理解決方案，可透過 Azure 入口網站設定。 包含 Intune 提供的完整功能集。 [在 Intune 主控台中設定 MDM 授權單位](#set-mdm-authority-to-intune)。

- **Intune 混合版** - Intune 雲端解決方案與 System Center Configuration Manager 的整合版。 您可以使用 Configuration Manager 主控台設定 Intune。 [在 Configuration Manager 中設定 MDM 授權單位](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription)。

- **Office 365 的行動裝置管理** - Office 365 與 Intune 雲端解決方案的整合版。 您可以從 Office 365 系統管理中心設定 Intune。 包含 Intune 獨立版提供的功能子集。 在 Office 365 系統管理中心中設定 MDM 授權單位。

> [!IMPORTANT]
> 在 Configuration Manager 1610 版或更新版本及 Microsoft Intune 1705 版中，您可以在不需要連絡 Microsoft 支援服務的情況下變更 MDM 授權單位，且不需要取消註冊並重新註冊您現有的受管理裝置。 如需詳細資訊，請參閱[選擇錯誤的 MDM 授權單位設定時該怎麼辦](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting)。

## <a name="set-mdm-authority-to-intune"></a>將 MDM 授權單位設為 Intune

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 選取橙色橫幅，以開啟 [行動裝置管理授權單位] 設定。
4. 在 [行動裝置管理授權單位] 下，從下列選項中選擇您的 MDM 授權單位：
   - **Intune MDM 授權單位**
   - **Configuration Manager MDM 授權單位**
   - **無**

   ![Intune 設定行動裝置管理授權單位畫面的螢幕擷取畫面](media/set-mdm-auth.png)

   接著會顯示一則訊息指出您已成功將 Intune 設定為 MDM 授權單位。

## <a name="enable-device-enrollment"></a>啟用裝置註冊

將 Intune 設定為 MDM 授權單位時，使用者可以藉由下列方式註冊個人擁有的裝置並取得資源 (例如電子郵件) 存取權：安裝公司入口網站 (iOS、macOS 及 Android)、新增工作認證 (Windows) 或存取公司入口網站 (iOS、Android、macOS)。

不同的平台具有下列需求，才能啟用或簡化註冊：
- **iOS** - (必要) [取得 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)，然後[啟用公司擁有之 iOS 裝置的註冊](ios-enroll.md) (選擇性)。
- **Android** - (選擇性) [啟用 Android 工作設定檔](android-enroll.md)
- **Windows** - (選擇性) 啟用[自動註冊](windows-enroll.md)或[大量註冊](windows-bulk-enroll.md)
- **macOS** - (必要) [取得 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)。

### <a name="workflow-of-intune-administration-ui"></a>Intune 系統管理使用者介面的工作流程
啟用 Android 或 Apple 裝置管理時，Intune 會傳送裝置與使用者資訊，以便與第三方服務整合來管理其各自的裝置。

下列案例會另外詢問是否同意共用資料：
- 啟用 Android for Work 時。
- 啟用並上傳 Apple MDM Push Certificate 時。
- 啟用任何 Apple 服務時，例如裝置註冊計劃、School Manager 或大量採購方案。

在每個案例中，同意會與執行行動裝置管理服務嚴格相關，例如確認 IT 系統管理員已授權 Google 或 Apple 裝置註冊。 當下列位置推出新的工作流程時，會提供文件說明哪些資訊為共用：
- [Intune 傳送至 Google 的資料](https://aka.ms/Data-intune-sends-to-google)
- [Intune 傳送至 Apple 的資料](https://aka.ms/data-intune-sends-to-apple)

如需 Microsoft 的 GDPR 合規性詳細資訊，請參閱[信任中心 - 評估您的 GDPR 合規性](https://aka.ms/trust_center_info)。

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 憑證到期後的行動裝置清除

當行動裝置與 Intune 服務通訊時，會自動更新 MDM 憑證。 若行動裝置被抹除，或有一段時間無法與 Intune 服務通訊，便無法更新 MDM 憑證。 當 MDM 憑證過期 180 天後，該裝置便會從 Azure 入口網站上移除。
