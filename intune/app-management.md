---
title: "什麼是 Microsoft Intune 應用程式管理"
titlesuffix: 
description: "了解 Microsoft Intune 管理應用程式的基本概念。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/09/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 737c2900b2cdd57cb4dfc8373d06111a52e772b2
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="what-is-microsoft-intune-app-management"></a>什麼是 Microsoft Intune 應用程式管理？


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Microsoft Intune 可讓身為 IT 系統管理員的您，管理貴公司員工使用的行動應用程式。 這項功能與管理裝置和保護資料一起存在。 在這項功能之中，您的其中一項優先事項是確定您的終端使用者可以存取完成其工作所需的應用程式。 這可能是一項挑戰，因為︰
- 裝置平台及應用程式類型有千百種。
- 您可能需要同時管理公司裝置和使用者本身裝置上的應用程式。
- 您必須確保網路和資料的安全。

此外，您也可能需要指派及管理未向 Intune 註冊之裝置上的應用程式。

Intune 提供各種功能，可協助您在所要的裝置上取得所需的應用程式。 下表提供應用程式管理功能的摘要。 表格之下是在 Azure 入口網站中了解 Microsoft Intune 的起點。

## <a name="app-management-capabilities-by-platform"></a>各種平台的應用程式管理功能

||||||
|-|-|-|-|-|
|&nbsp; |Android|iOS|Windows Phone 8.1|Windows 10|
|新增應用程式並指派給裝置與使用者|是|是|是|是|
|指派應用程式給未向 Intune 註冊的裝置|是|是|否|否|
|使用應用程式設定原則控制應用程式的啟動行為|否|是|否|否|
|使用行動裝置應用程式佈建原則更新過期的應用程式|否|是|否|否|
|使用應用程式保護原則保護應用程式中的公司資料|是|是|否|否<sup>1</sup>|
|只移除已安裝之應用程式中的公司資料 (應用程式選擇性抹除)|是|是|是|是|
|監視應用程式指派|是|是|是|是|
|指派及追蹤從應用程式市集中大量採購的應用程式|否|否|否|是|
|強制安裝在裝置上的應用程式 (必要)<sup>2</sup>|是|是|是|是|
|可從公司入口網站安裝在裝置上的選擇 (可用安裝)|是|是|是|是|
|安裝網路應用程式的捷徑 (網路連結)|是|是|是|是|
|內部 (企業營運) 應用程式|是|是|否|是|
|市集應用程式|是|是|是|是|
|更新應用程式|是|是|是|是|

<sup>1</sup>您可以考慮使用 [Windows 資訊保護](windows-information-protection-configure.md)來保護 Windows 10 裝置上的應用程式。

<sup>2</sup>僅適用於 Intune 管理的裝置。

## <a name="how-to-get-started"></a>如何開始

在**行動應用程式**工作負載中，您能存取的應用程式相關項目如下：

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [監視 + 管理] 區段。
3. 在 [Intune] 刀鋒視窗上，選擇 [行動應用程式]。

    ![行動應用程式工作負載](./media/apps-workload.png)

下列資訊對應 [行動應用程式] 刀鋒視窗中可用的選項。

### <a name="manage"></a>管理
- **應用程式** - 選取此選項可新增、檢視、指派和監視您工作人員使用的應用程式。 如需詳細資訊，請參閱下列文件：
    - [新增應用程式](apps-add.md)
    - [指派應用程式](apps-deploy.md)
    - [監視應用程式](apps-monitor.md)
- **應用程式設定原則** - 應用程式設定原則可讓您提供使用者執行應用程式時可能需要的設定。 如需詳細資訊，請參閱下列文件：
    - [Intune 的應用程式設定原則](app-configuration-policies-overview.md)
        - [iOS 應用程式設定原則](app-configuration-policies-use-ios.md)
        - [Android 應用程式設定原則](app-configuration-policies-use-android.md)
- **應用程式防護原則** - 應用程式防護原則可讓您建立設定與應用程式之間的關聯以利保護它所使用的公司資料。 例如，您可以限制某應用程式與其他應用程式的通訊能力，或是要求使用者輸入 PIN 碼才能存取公司應用程式。 如需詳細資訊，請參閱下列文章：
    - [應用程式保護原則](app-protection-policies.md)
- **應用程式選擇性抹除** - 只移除所選裝置上的公司資料。 如需詳細資訊，請參閱下列文章：
    - [應用程式選擇性抹除](apps-selective-wipe.md)
- **iOS 應用程式佈建設定檔** - iOS 應用程式包含佈建設定檔和由憑證所簽署的程式碼。 憑證過期之後，就無法再執行應用程式。 Intune 提供工具，讓您可主動將新的佈建設定檔原則指派至具有即將到期之應用程式的裝置。 如需詳細資訊，請參閱下列文章：
    - [iOS 應用程式佈建設定檔](app-provisioning-profile-ios.md)

如需詳細資訊，請參閱[管理應用程式](app-management.md)。

### <a name="monitor"></a>監視
- **應用程式授權** - 檢視、指派及監視從應用程式市集大量採購的應用程式。 如需詳細資訊，請參閱下列文件：
    - [iOS 大量採購方案 (VPP) 應用程式](vpp-apps-ios.md)
    - [商務用 Microsoft 網上商店大量採購應用程式](windows-store-for-business.md)
- **探索到的應用程式** - 顯示 Intune 指派並安裝在裝置上的所有應用程式。
- **應用程式安裝狀態** - 顯示您所建立之應用程式指派的狀態。
- **應用程式保護狀態** - 顯示您選取之使用者的應用程式保護原則狀態。
- **稽核記錄檔** - 顯示所有 IT 系統管理員所進行的 Intune 應用程式相關活動。

如需詳細資訊，請參閱[監視應用程式](apps-monitor.md)。

### <a name="setup"></a>Setup
- **iOS VPP 權杖** - 套用並檢視您的 iOS 大量採購方案 (VPP) 授權。
    - [iOS 大量採購應用程式](vpp-apps-ios.md)
- **Windows 企業憑證** - 套用或檢視程式碼簽署憑證的狀態，此憑證可用來將企業營運應用程式發佈到您的受控 Windows 裝置。
- **Windows Symantec 憑證** - 套用或檢視 Symantec 程式碼簽署憑證的狀態，將 XAP 和 WP8.x appx 檔案發佈至 Windows 10 行動裝置時需要此憑證。
- **商務用 Microsoft 網上商店** - 設定對商務用 Microsoft 網上商店的整合。 執行此動作之後，可以將採購的應用程式同步到 Intune 並加以指派，以及追蹤授權使用狀況。 如需詳細資訊，請參閱下列文章：
    - [商務用 Microsoft 網上商店大量採購應用程式](windows-store-for-business.md)
- **Windows 側載金鑰** - 您可以新增 Windows 側載金鑰，以便用來將應用程式直接安裝到裝置，而非發行應用程式並從 Windows 市集下載。 如需詳細資訊，請參閱下列文章：
    - [側載 Windows 應用程式](app-sideload-windows.md)
- **公司入口網站品牌** - 自訂公司入口網站以顯示您公司的品牌。 如需詳細資訊，請參閱下列文章：
    - [公司入口網站設定](company-portal-app.md)
- **應用程式類別** - 新增、釘選及刪除應用程式類別名稱。
- **Android for Work** - 核准並同步處理您已經為企業核准的應用程式。 如需詳細資訊，請參閱下列文章：
    - [Android for Work 應用程式](apps-add-android-for-work.md)

### <a name="help-and-support"></a>說明及支援
- **說明及支援** - 進行疑難排解、要求支援，或者檢視 Intune 狀態。 如需詳細資訊，請參閱下列文章：
    - [針對問題進行疑難排解](help-desk-operators.md)

## <a name="next-steps"></a>接下來的步驟

- [如何將應用程式新增至 Microsoft Intune](apps-add.md)
