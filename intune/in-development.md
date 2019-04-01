---
title: 在開發-Microsoft Intune
titlesuffix: ''
description: 在開發過程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c377a8558b1f318b4ddad735b6368a291e34516
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57756814"
---
# <a name="in-development-for-microsoft-intune---march-2019"></a>在開發 Microsoft Intune-2019 年 3 月

若要可協助您的整備程度和計劃、 此頁面清單 Intune UI 更新及功能正在開發，但尚未發行。 此外：

- 如果我們預期，您必須採取動作，在變更之前，我們將發佈免費的 Office 訊息中心 post。
- 當為預覽功能啟動實際執行環境，或已正式推出，功能描述會移動關閉此頁面，並拖曳至[什麼是新的頁面](whats-new.md)。
- 此頁面並[什麼是新的頁面](whats-new.md)會定期更新。 請回來查看其他更新。
- 請參閱[M365 藍圖](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)策略性的交付項目與時間軸。

> [!Note]
> 這些項目會反映 Microsoft 的未來版本中推出的 Intune 功能的目前預期動作。 日期和個別的功能可能會變更。 並非所有的項目，在開發過程中會對此頁面中的功能描述。

**RSS 摘要**：將下列 URL 複製並貼上至您的摘要讀取器中，以在本頁更新時收到通知：`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`


<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 入口網站中的 Intune


<!-- 1903 start-->

### <a name="encryption-report-----2351538---"></a>加密的報表  <!-- 2351538 -->
您可以使用新的加密報表以檢視有關您裝置的加密狀態的詳細資料。 可用的詳細資料會包含裝置的 TPM 版本、 加密整備和狀態、 錯誤報告，以及更多。  

### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-----2351547----"></a>從 Intune 入口網站存取 BitLocker 修復金鑰  <!-- 2351547  -->
我們將新增新的進入點中的裝置，您可以在其中檢視詳細資料從 Azure Active Directory (AAD) 有關 BitLocker 金鑰識別碼和 BitLocker 修復金鑰。

### <a name="scope-tags-for-app-configuration-policies---2371891---"></a>應用程式設定原則的範圍標籤 <!--2371891 -->
您可以將範圍標籤新增至應用程式設定原則，以便只與角色也被指派該範圍標籤的人員才可以存取應用程式設定原則。 應用程式設定原則只能以目標或指派相同的範圍標籤的應用程式相關聯。

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>將 Autopilot 設定檔指派給所有裝置虛擬群組 <!--2715522 -->
您將可以將 Autopilot 設定檔指派給所有裝置虛擬群組。 若要進行此動作，請選擇 [裝置註冊] > [Windows 註冊] > [部署設定檔]> 選擇設定檔 > [指派] > 在 [指派對象] 下方，選擇 [所有裝置]。 如需 Autopilot 設定檔的詳細資訊，請參閱[使用 Windows AutoPilot 註冊 Windows 裝置](enrollment-autopilot.md)。

### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523----"></a>安裝 Windows 大量註冊之後，請使用公司入口網站應用程式可用的應用程式 <!-- 2751523  -->
註冊到 Intune 所使用的 Windows 裝置[Windows 大量註冊](windows-bulk-enroll.md)（佈建套件） 都能夠使用公司入口網站應用程式安裝可用的應用程式。 如需有關公司入口網站應用程式的詳細資訊，請參閱[手動新增 Windows 10 公司入口網站](store-apps-company-portal-app.md)並[如何設定 Microsoft Intune 公司入口網站應用程式](company-portal-app.md)。

### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430---"></a>IOS 應用程式佈建設定檔的範圍標籤 <!--2934430 -->
您可以將範圍標記新增至 iOS 應用程式佈建設定檔，讓 iOS 應用程式佈建設定檔的人士也指派該範圍標籤角色存取。 

### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477----"></a>Office 部署工具 (ODT) XML for Office 專業增強版部署 <!-- 3192477  -->
您可以在 Intune 管理主控台中建立 Office Pro Plus 的執行個體時提供 Office 部署工具 (ODT) XML。 如果現有的 Intune UI 選項不符合您的需求，這可讓更大的自訂功能。 

###  <a name="block-users-from-scanning-for-windows-updates-------3316758------"></a>禁止使用者掃描 Windows 更新    <!-- 3316758    -->
我們將新增新 Windows 更新通道設定，您可以使用，將會封鎖從掃描 Windows 更新的使用者。 此設定無法從入口網站中使用，但可以使用 Intune 圖形 API 來設定。

### <a name="windows-update-notifications-----3316782---"></a>Windows 更新通知  <!-- 3316782 -->
我們將新增支援 Windows Update ring 設定，因此您可以設定您的使用者看到的 Windows 更新通知。 此設定無法從入口網站中使用，但可以使用 Intune 圖形 API 來設定。

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>變更為適用於 iOS 的公司入口網站註冊 12 的裝置使用者 <!--3448635 -->  
適用於 iOS 的公司入口網站將會更新，應用程式的註冊畫面和步驟，以配合在 Apple iOS 12.2 中發行的 MDM 註冊變更。 更新的工作流程現在會提示使用者：

- 允許 Safari 以開啟公司入口網站 （透過 Safari)，並下載管理設定檔，然後再回到 公司入口網站應用程式。 
- 開啟 設定 應用程式在其裝置上安裝管理設定檔。
- 返回公司入口網站應用程式，以完成註冊。  

如需有關如何準備這些變更的詳細資訊，請參閱 < [Microsoft 技術社群文章](https://techcommunity.microsoft.com/)。 在此同時，若要支援新的 iOS 註冊在公司入口網站中，我們已更新中的步驟[在 Intune 中的註冊 iOS 裝置](https://docs.microsoft.com/en-us/intune/ios-enroll)。 Apple 發行 iOS 版 12.2 之後，這些文件變更會即時。 

### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202-------"></a>在 [租用戶狀態] 頁面上的其他連接器的支援 <!-- 3617202     -->
[租用戶狀態] 頁面會顯示狀態資訊的其他連接器，包括*Windows Defender 進階威脅防護*(ATP) 和其他 Mobile Threat Defense 連接器。

### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917---"></a>授與 Intune 唯讀存取某些 Azure Active Directory 角色 <!-- 3637917 -->
我們將會被授與 Intune 讀取下列的 Azure AD 角色的存取權。 授與 Azure AD 角色的權限取代使用 Intune 角色型存取控制 (RBAC) 授與權限。

讀取 Intune 稽核資料的權限：

- 合規性管理員
- 合規性資料管理員

閱讀 Intune 的所有資料的存取權：

- 安全性系統管理員
- 安全性運算子
- 安全性讀取者
- 全域讀取器

### <a name="easier-access-to-diagnostic-settings------3804627-----"></a>更容易存取的診斷設定   <!-- 3804627   -->
我們將新增的新選項**稽核記錄檔**刀鋒視窗中的每個在 Intune 主控台中，您可以直接開啟使用中的每個稽核記錄檔工作負載*診斷設定*頁面。

### <a name="create-and-use-device-configuration-profiles-on-android-zebra-devices-in-intune----3895244----"></a>建立和使用在 Intune 中 Android 色彩裝置的裝置組態設定檔 <!-- 3895244  -->
Intune 將支援設定色彩的 Android 裝置。 具體來說，您將能夠： 

- 建立裝置組態設定檔，並將設定套用至使用 StageNow 所產生的行動延伸模組 (MX) 設定檔的 Android 色彩裝置 (**裝置組態** > **設定檔** > **建立設定檔** > **Android**平台)。

適用於：  
- Android

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>線上授權商務用 Microsoft Store 應用程式的部署 <!-- 1672660  -->
您將能夠在裝置內容中指派必要的線上授權商務用 Microsoft Store 應用程式。 以此方式部署商務用 Microsoft Store 應用程式，即可在裝置上為所有使用者安裝應用程式。 這僅適用於 Windows 10 RS4+ 電腦裝置。 您可以從 MSFB 線上授權應用程式的用戶端應用程式指派頁面，存取在裝置內容中安裝的選項。

## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。
