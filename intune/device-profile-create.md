---
title: 在 Microsoft Intune - Azure 中建立裝置設定檔 | Microsoft Docs
description: 在 Microsoft Intune 中新增或設定裝置組態設定檔。 選取平台類型、進行設定，以及加入範圍標籤。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08c6ece37a4ff6eceaa4df735f365453a4bc7d88
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570399"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>在 Microsoft Intune 中建立裝置設定檔

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

裝置設定檔可讓您新增設定項目並加以設定，然後再將這些設定推送至您組織中的裝置。 [使用裝置設定檔在裝置上套用功能和設定](device-profiles.md)則能提供更詳細的資料，包括您可以執行哪些作業。

這篇文章：

- 會列出建立設定檔的步驟。
- 會說明如何新增範圍標籤以「篩選」設定檔。
- 會在裝置接收設定檔和任何設定檔更新時，列出簽入重新整理週期時間。

## <a name="create-the-profile"></a>建立設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務] > 篩選 [Intune] > 選取 [Intune]。

2. 選取 [裝置設定]。 下列選項可供您選擇：

    - **概觀**：列出您的設定檔狀態，並在您指派給使用者和裝置的設定檔中提供其他詳細資料。
    - **管理**：建立裝置設定檔，上傳自訂 [PowerShell 指令碼](intune-management-extension.md)以在設定檔中執行，並使用 [eSIM](esim-device-configuration.md) 將行動數據方案新增至裝置。
    - **監視**：檢查設定檔的狀態為成功或失敗，另檢視您設定檔中的記錄。
    - **安裝**：新增 SCEP 或 PFX 憑證授權單位，或是在設定檔中啟用[電信費用管理](telecom-expenses-monitor.md)。

3. 選取 [設定檔] > [建立設定檔]。 輸入下列內容：

   - **名稱**：為設定檔輸入描述性名稱。 命名您的設定檔，以方便之後能輕鬆識別。 例如，良好的設定檔名稱為**整個公司的 WP 電子郵件設定檔**。
   - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
   - **平台**：選擇您的裝置平台。 選項包括：  

       - **Android**
       - **Android 企業**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 及更新版本**
       - **Windows 10 及更新版本**

   - **設定檔類型**：選取您要建立的設定類型。 顯示的清單取決於您選擇的**平台**。
   - **設定**：下列文章會描述每個設定檔類型的設定︰

       - [系統管理範本](administrative-templates-windows.md)
       - [自訂](custom-settings-configure.md)
       - [傳遞最佳化](delivery-optimization-windows.md)
       - [裝置功能](device-features-configure.md)
       - [裝置限制](device-restrictions-configure.md)
       - [版本升級和模式切換](edition-upgrade-configure-windows-10.md)
       - [教育](education-settings-configure.md)
       - [電子郵件](email-settings-configure.md)
       - [端點保護](endpoint-protection-configure.md)
       - [Identity Protection](identity-protection-configure.md)  
       - [Kiosk](kiosk-settings.md)
       - [PKCS 憑證](certficates-pfx-configure.md)
       - [SCEP 憑證](certificates-scep-configure.md)
       - [信任的憑證](certificates-configure.md)
       - [更新原則](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](advanced-threat-protection.md)
       - [Windows 資訊保護](windows-information-protection-configure.md)

     例如，如果選取 **iOS** 平台，您的設定檔類型選項看起來會類似以下設定檔：

     ![在 Intune 中建立 iOS 設定檔](./media/create-device-profile.png)

4. 完成後，請選取 [確定] > [建立] 以儲存變更。 就會建立設定檔，並顯示在清單中。

## <a name="scope-tags"></a>範圍標籤

新增設定之後，您也可以新增範圍標籤至設定檔。 範圍標籤可將原則指派及篩選至特定群組，例如人力資源或所有 US-NC 員工。

如需範圍標籤和可執行哪些作業的相關詳細資訊，請參閱[針對分散式 IT 使用 RBAC 和範圍標籤](scope-tags.md)。

### <a name="add-a-scope-tag"></a>新增範圍標籤

1. 選取 [範圍 (標籤)]。
2. 選取 [新增] 以建立新的範圍標籤。 或是，從清單中選取現有的範圍標籤。
3. 按一下 [確定] 以儲存您的變更。

## <a name="refresh-cycle-times"></a>重新整理週期時間

Intune 會使用以下重新整理循環檢查組態設定檔是否有更新：

| 平台 | 重新整理循環|
| --- | --- |
| iOS | 每 6 小時 |
| macOS | 每 6 小時 |
| Android | 每 8 小時 |
| 註冊為裝置的 Windows 10 電腦 | 每 8 小時 |
| Windows Phone | 每 8 小時 |
| Windows 8.1 | 每 8 小時 |

如果裝置是最近註冊的，簽入的執行頻率會比較高：

| 平台 | 頻率 |
| --- | --- |
| iOS | 前 6 小時每 15 分鐘，之後每 6 小時 |  
| macOS | 前 6 小時每 15 分鐘，之後每 6 小時 | 
| Android | 前 15 分鐘每 3 分鐘，之後 2 小時每 15 分鐘，再來每 8 小時 | 
| 註冊為裝置的 Windows 10 電腦 | 前 30 分鐘每 3 分鐘，之後每 8 小時 | 
| Windows Phone | 前 15 分鐘每 5 分鐘，之後 2 小時每 15 分鐘，再來每 8 小時 | 
| Windows 8.1 | 前 15 分鐘每 5 分鐘，之後 2 小時每 15 分鐘，再來每 8 小時 | 

使用者可以在任何時間開啟公司入口網站應用程式並同步處理裝置，以立即檢查是否有設定檔更新。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
