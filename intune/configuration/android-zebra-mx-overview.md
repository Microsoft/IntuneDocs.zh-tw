---
title: 在 Microsoft Intune 中使用 Android 裝置上的 Zebra 行動性延伸模組 - Azure | Microsoft Docs
description: 使用 Microsoft Intune，透過 Zebra 行動性延伸模組 (MX) 管理及使用執行 Android 的 Zebra 裝置。 請查看所有步驟，包括安裝公司入口網站應用程式、側載應用程式、指派裝置系統管理員角色、建立 StageNow 設定檔等。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: jieyan
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 83048061cc7b3e1aaeb09ff54dec819720f2571f
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206817"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>在 Microsoft Intune 中透過 Zebra 行動性延伸模組使用及管理 Zebra 裝置



Intune 包含一組豐富的功能，包括管理應用程式，以及設定裝置設定。 這些內建功能和設定可用來管理 Zebra Technologies 所製造的 Android 裝置，亦稱為「Zebra 裝置」。

在 Android 裝置上，使用 Zebra 的**行動性延伸模組 (MX)** 設定檔來自訂或新增更多的 Zebra 特定設定。

本文說明如何在 Microsoft Intune 中使用 Zebra 裝置上的 Zebra 行動性延伸模組 (MX)。

本功能適用於：

- Android

您的公司可能會將 Zebra 裝置用於零售、廠房等。 例如，您是零售商，而您環境包含銷售夥伴所使用的數千個 Zebra 行動裝置。 Intune 可協助管理這些裝置，作為行動裝置管理 (MDM) 解決方案的一部分。

使用 Intune，您可以註冊 Zebra 裝置，將您的企業營運應用程式部署到裝置。 [裝置設定] 設定檔可讓您建立 MX 設定檔，以管理您的 Zebra 特定設定。

> [!NOTE]
> 根據預設，Zebra MX Api 不會在裝置上鎖定。 在裝置於 Intune 中註冊之前，裝置可能會以惡意方式洩漏。 當裝置處於「清除」狀態時，建議您使用「存取管理員」（AccessMgr）鎖定 MX Api。 例如，您可以選擇只允許您信任的公司入口網站應用程式和應用程式呼叫 MX Api。
>
> 如需詳細資訊，請參閱在 Zebra 的網站上[鎖定您的裝置](https://developer.zebra.com/community/home/blog/2017/04/11/locking-down-your-device)。

## <a name="before-you-begin"></a>開始之前

- 請確定您具有來自 Zebra Technologies 的最新版本 StageNow 桌面應用程式。
- 請務必檢閱 [Zebra's full MX feature matrix](http://techdocs.zebra.com/mx/compatibility) (Zebra 的完整 MX 功能矩陣) (開啟 Zebra 的網站)，以確認您所建立設定檔與裝置的 MX 版本、OS 版本及模型相容。
- 某些裝置 (例如 TC20/25 裝置) 不支援 StageNow 中所有可用的 MX 功能。 請務必檢閱 [Zebra's feature matrixZebra](http://techdocs.zebra.com/mx/tc2x/) (Zebra 的功能矩陣) (開啟 Zebra 的網站)，以取得更新的支援資訊。

## <a name="step-1-install-the-latest-company-portal-app"></a>步驟 1：安裝最新的公司入口網站應用程式

在裝置上，開啟 [Google Play] 存放區。 從 Microsoft 下載並安裝 Intune 公司入口網站應用程式。 從 Google Play 安裝時，公司入口網站應用程式會自動取得更新和修正程式。

如果無法使用 Google Play，請下載[適用於 Android 的 Microsoft Intune 公司入口網站](https://www.microsoft.com/download/details.aspx?id=49140) (開啟另一個 Microsoft 網站) 並[加以側載](#sideload-the-company-portal-app) (在本文中)。 以這種方式安裝時，應用程式不會自動接收更新或或修正程式。 請務必定期更新，並手動修補應用程式。

### <a name="sideload-the-company-portal-app"></a>側載公司入口網站應用程式

「側載」是指您不使用 Google Play 來安裝應用程式。 若要側載公司入口網站應用程式，請使用 StageNow。 

下列步驟提供概觀。 如需特定的詳細資料，請參閱 Zebra 的文件。 [Enroll in an MDM using StageNow](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (使用 StageNow 在 MDM 中註冊) (開啟 Zebra 的網站) 可能是不錯的資源。

1. 在 StageNow 中，針對 [Enroll in an MDM] \(在 MDM 中註冊\)  建立設定檔。
2. 在 [Deployment] \(部署\)  中，選擇下載 MDM 代理程式檔案。
3. 將 [Support App] \(支援應用程式\)  和 [Download Configuration] \(下載設定\)  步驟設定為 [No] \(否\)  。
4. 在 [Download MDM] \(下載 MDM\)  中，選取 [Transfer/Copy File] \(傳輸/複製檔案\)  。 新增公司入口網站 Android 套件 (APK) 的來源和目的地。
5. 在 [Launch MDM] \(啟動 MDM\)  中，依原樣保留預設值。 新增下列詳細資料：

    - **套件名稱**：`com.microsoft.windowsintune.companyportal`
    - **類別名稱**：`com.microsoft.windowsintune.companyportal.views.SplashActivity`

繼續發佈設定檔，並使用裝置上的 StageNow 應用程式加以自訂。 隨即會在裝置上安裝並開啟公司入口網站。

> [!TIP]
> 如需 StageNow 及其功用的詳細資訊，請參閱 [StageNow Android device staging](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (StageNow Android 裝置預備) (開啟 Zebra 的網站)。

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>步驟 2：確認公司入口網站應用程式具有裝置系統管理員角色

公司入口網站應用程式需要有裝置系統管理員，才能管理 Android 裝置。 為了啟用裝置系統管理員角色，部分 Zebra 裝置會在裝置上包含使用者介面 (UI)。 如果裝置包含 UI，公司入口網站應用程式會提示終端使用者於[註冊](#step-3-enroll-the-device-in-to-intune) (在本文中) 期間授與裝置系統管理員。

如果無法使用 UI，請使用 StageNow 中的 [DevAdmin Manager] \(DevAdmin 管理員\)  來建立設定檔，以手動方式將裝置系統管理員授與給公司入口網站應用程式。

下列步驟提供概觀。 如需特定的詳細資料，請參閱 Zebra 的文件。 
[Set battery swap mode as device administrator](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (以裝置系統管理員身分設定電池更換模式) (開啟 Zebra 的網站) 可能是不錯的資源。

1. 在 StageNow 中，建立設定檔並選取 [Xpert Mode] \(Xpert 模式\)  。
2. 將 [DevAdmin Manager] \(DevAdmin 管理員\)  新增至設定檔。
3. 將 [Device Administration Action] \(裝置系統管理員動作\)  設定為 [Turn On as Device Administrator] \(以裝置系統管理員身分開啟\)  。
4. 將 [Device Admin Package Name] \(裝置系統管理員套件名稱\)  設定為 `com.microsoft.windowsintune.companyportal`。
5. 將 [Device Admin Class Name] \(裝置系統管理員類別名稱\)  設定為 `com.microsoft.omadm.client.PolicyManagerReceiver`。

繼續發佈設定檔，並使用裝置上的 StageNow 應用程式加以自訂。 公司入口網站應用程式隨即獲授與裝置系統管理員角色。

## <a name="step-3-enroll-the-device-in-to-intune"></a>步驟 3：將裝置註冊到 Intune 中

完成前兩個步驟之後，公司入口網站應用程式即安裝在裝置上。 裝置已準備好要註冊到 Intune 中。

[註冊 Android 裝置](../enrollment/android-enroll.md)列出這些步驟。 如果您有多部 Zebra 裝置，建議您使用[裝置註冊管理員 (DEM) 帳戶](../enrollment/device-enrollment-manager-enroll.md)。 使用 DEM 帳戶會一併移除從公司入口網站應用程式中取消註冊的選項，讓使用者無法輕鬆地取消註冊裝置。

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>步驟 4：在 StageNow 中建立裝置管理設定檔

您可以使用 StageNow 來建立設定檔，以設定您想要在裝置上管理的設定。 如需特定的詳細資料，請參閱 Zebra 的文件。 [Profiles](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (設定檔) (開啟 Zebra 的網站) 可能是不錯的資源。

當您在 StageNow 中建立設定檔時，請在最後一個步驟中選取 [Export to MDM] \(匯出至 MDM\)  。 此步驟會產生 XML 檔案。 儲存此檔案。 您在之後的步驟中需要該檔案。

- 建議您先測試設定檔，再將它部署至您組織中的裝置。 若要測試，請在電腦上透過 StageNow 建立設定檔的最後一個步驟中，使用 [Test] \(測試\)  選項。 然後，在裝置上透過 StageNow 應用程式取用 StageNow 產生的檔案。

  裝置上的 StageNow 應用程式會顯示當您測試設定檔時產生的記錄。 [在 Intune 中於執行 Android 的 Zebra 裝置上使用 StageNow 記錄](android-zebra-mx-logs-troubleshoot.md)含有使用 StageNow 記錄來了解錯誤的資訊。

- 如果您參考應用程式、更新套件，或更新 StageNow 設定檔中的其他檔案，您希望裝置取得這些更新。 若要取得更新，在套用設定檔時，裝置必須連線到 StageNow 部署伺服器。 

  或者，您可以在 Intune 中使用內建功能以取得這些變更，包括：

  - 可[新增](../apps/apps-add.md)、[部署](../apps/apps-deploy.md)、更新及[監視](../apps/apps-monitor.md)應用程式的應用程式管理功能。
  - 在執行 Android Enterprise 的裝置上管理[系統和應用程式更新](device-restrictions-android-for-work.md#device-owner-only)

測試檔案之後，下一步是使用 Intune 將設定檔部署到裝置。

- 您可以將一個或多個 MX 設定檔部署到裝置。
- 您也可以匯出多個 StageNow 設定檔，並將設定合併至單一 XML 檔案。 然後，將 XML 檔案上傳至 Intune，以部署至您的裝置。

  > [!WARNING]
  > 如果將多個 MX 設定檔的目標設定為相同的群組，並設定相同的屬性，裝置上將會有衝突。
  >
  > 如果在單一 MX 設定檔中多次設定相同的屬性，最後一次設定會獲勝。

## <a name="step-5-create-a-profile-in-intune"></a>步驟 5：在 Intune 中建立設定檔

在 Intune 中，建立裝置組態設定檔：

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
3. 輸入下列內容：

    - **名稱**：為新的設定檔輸入描述性名稱。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取 [Android]  。
    - **設定檔類型**：選取 [MX 設定檔 (僅限 Zebra)]  。

4. 在 [.xml 格式的 MX 設定檔]  中，新增[您從 StageNow 匯出](#step-4-create-a-device-management-profile-in-stagenow) (在本文中) 的 XML 設定檔。
5. 選取 [確定]   > [建立]  儲存您的變更。 原則隨即建立，並顯示在清單中。

    > [!TIP]
    > 基於安全性理由，您在儲存之後不會看到設定檔的 XML 文字。 文字已經加密，您只會看到星號 (`****`)。 供您參考，建議您先儲存 MX 設定檔的複本，再將其新增至 Intune。

設定檔已建立，但還不會執行任何動作。 接下來，[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

下次裝置檢查設定更新時，MX 設定檔會部署到裝置中。 裝置註冊時，裝置會與 Intune 進行同步處理，然後大約每隔 8 小時執行一次。 您也可以[在 Intune 中強制同步處理](../remote-actions/device-sync.md)。 或者，在裝置上開啟 [公司入口網站應用程式]   > [設定]   > [同步處理]  。 

## <a name="update-a-zebra-mx-configuration-after-its-assigned"></a>在指派之後更新 Zebra MX 設定

若要更新 Zebra 裝置的 MX 特定設定，您可以： 

- 建立已更新的 StageNow XML 檔，編輯現有的 Intune MX 設定檔，並上傳新的 StageNow XML 檔案。 這個新檔案會覆寫設定檔中的上一個原則，並取代先前的設定。
- 建立新的 StageNow XML 檔案，以進行不同的設定、建立新的 Intune MX 設定檔、上傳新的 StageNow XML 檔，並將它指派給相同的群組。 已部署多個設定檔。 如果新的設定檔設定現有設定檔中已存在的設定，則會發生衝突。

## <a name="next-steps"></a>後續步驟

- [指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
- [使用 StageNow 記錄針對 Zebra 裝置進行疑難排解](android-zebra-mx-logs-troubleshoot.md)。
