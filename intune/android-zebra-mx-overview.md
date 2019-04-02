---
title: 使用 Microsoft Intune-Azure 中的 Android 裝置上的色彩行動延伸模組 |Microsoft Docs
description: 您可以使用 Microsoft Intune 來管理及使用色彩與色彩行動擴充程式 (MX) 執行 Android 的裝置。 請參閱所有的步驟，包括安裝公司入口網站應用程式側載應用程式、 將裝置系統管理員角色指派、 建立 StageNow 設定檔，以及更多內容。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa2734247569245794bce7fe1de68c8b20c6091f
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490599"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>使用及管理在 Microsoft Intune 中的色彩行動延伸模組使用的色彩裝置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 包含一組豐富的功能，包括管理應用程式，以及設定裝置設定。 這些內建的功能和設定，可管理 Android 裝置製造色彩技術，也稱為 「 色彩裝置 」。

如果您想要自訂或新增更多色彩特定設定，您也可以使用色彩**行動擴充程式 (MX)** 在這些裝置上。 

本功能適用於：

- Android

您的公司可能會使用色彩裝置 for retail 工廠中，等。 比方說，你是零售商，而您的環境包含數千個色彩銷售夥伴所用的行動裝置。 Intune 可協助您的行動裝置管理 (MDM) 解決方案的一部分來管理這些裝置。

使用 Intune，您可以註冊色彩將您的特定業務應用程式部署到裝置的裝置。 [裝置設定] 設定檔可讓您建立 MX 設定檔，以管理您的特定色彩的設定。

本文說明如何使用 Microsoft Intune 中的色彩裝置上的色彩行動擴充程式 (MX)。

## <a name="before-you-begin"></a>開始之前

- 您必須具備 StageNow 傳統型應用程式從色彩技術的最新版本。
- 請務必檢查[色彩的完整 MX 功能矩陣](http://techdocs.zebra.com/mx/compatibility)（開啟色彩的網站） 以確認您所建立的設定檔與裝置的 MX 版本、 作業系統版本和模型相容。
- 某些裝置，例如 TC20/25 裝置不支援的所有可用的 MX 功能 StageNow 中。 請務必檢查[色彩的功能矩陣](http://techdocs.zebra.com/mx/tc2x/)（開啟色彩的網站） 的更新的支援資訊。

## <a name="step-1-install-the-latest-company-portal-app"></a>步驟 1： 安裝最新的公司入口網站應用程式

在裝置上，移至 Google Play 商店，下載和安裝 Microsoft Intune 公司入口網站應用程式。 從 Google Play 安裝時，公司入口網站應用程式會取得更新，並自動修正。

如果無法使用的 Google Play，下載[適用於 Android 的 Microsoft Intune 公司入口網站](https://www.microsoft.com/download/details.aspx?id=49140)（開啟另一個 Microsoft 網站） 和[側面載入它](#sideload-the-company-portal-app)（在本文中）。 當這種方式安裝，應用程式不接收更新，或自動修正。 您應該定期更新，並手動修補應用程式。

### <a name="sideload-the-company-portal-app"></a>側載公司入口網站應用程式

「 側載 」 時，您不使用 Google Play 安裝應用程式。 若要側載公司入口網站應用程式中，使用 StageNow。 

下列步驟提供概觀。 特定的詳細資訊，請參閱色彩的文件。 [在使用 StageNow MDM 中註冊](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/)（開啟色彩的網站） 可能是不錯的資源。

1. 在 StageNow，建立的設定檔**在 MDM 中的註冊**。
2. 在 **部署**，選擇下載 MDM 代理程式的檔案。
3. 設定**支援應用程式**並**下載組態**步驟**No**。
4. 在 **下載 MDM**，選取**傳輸/複製檔案**。 加入來源和目的地的 Android 公司入口網站的套件 (APK)。
5. 在 **啟動 MDM**，保留預設值為-是。 新增下列詳細資料：

    - **套件名稱**：`com.microsoft.windowsintune.companyportal`
    - **類別名稱**：`com.microsoft.windowsintune.companyportal.views.SplashActivity`

繼續發行設定檔，並使用 StageNow 裝置上應用程式。 安裝並在裝置上開啟公司入口網站應用程式。

> [!TIP]
> 如需有關 StageNow，以及它的功用的詳細資訊，請參閱[StageNow Android 裝置預備](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html)（開啟色彩的網站）。

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>步驟 2： 確認公司入口網站應用程式具備裝置系統管理員角色

公司入口網站應用程式需要管理 Android 裝置的裝置系統管理員。 若要啟用裝置系統管理員角色，部分色彩裝置包括在裝置上的使用者介面 (UI)。 如果裝置包含 UI，公司入口網站應用程式會提示使用者授與裝置系統管理員，在[註冊](#step-3-enroll-the-device-in-to-intune)（在本文中）。

如果無法使用的 UI，使用**DevAdmin Manager** StageNow 建立設定檔，以手動方式將裝置系統管理員授與公司入口網站應用程式中。

下列步驟提供概觀。 特定的詳細資訊，請參閱色彩的文件。 
[設定電池交換模式，裝置系統管理員身分](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool)（開啟色彩的網站） 可能是不錯的資源。

1. 在 StageNow，建立設定檔，然後選取**Xpert 模式**。
2. 新增**DevAdmin Manager**至設定檔。
3. 設定**裝置管理動作**要**開啟 裝置系統管理員身分**。
4. 設定**裝置系統管理員的封裝名稱**至`com.microsoft.windowsintune.companyportal`。
5. 設定**裝置系統管理類別名稱**至`com.microsoft.omadm.client.PolicyManagerReceiver`。

繼續發行設定檔，並使用 StageNow 裝置上應用程式。 公司入口網站應用程式會授與裝置系統管理員角色。

## <a name="step-3-enroll-the-device-in-to-intune"></a>步驟 3： 註冊 Intune 中裝置

完成前兩個步驟之後，公司入口網站應用程式會安裝在裝置上。 裝置已準備好註冊至 Intune。

[註冊 Android 裝置](android-enroll.md)列出的步驟。 如果您有許多色彩裝置時，您可能想要[裝置註冊管理員帳戶](device-enrollment-manager-enroll.md)。

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>步驟 4: StageNow 中建立的裝置管理設定檔

您可以使用 StageNow 建立的設定檔，設定您想要管理的裝置上的設定。 特定的詳細資訊，請參閱色彩的文件。 [設定檔](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/)（開啟色彩的網站） 可能是不錯的資源。

當您建立設定檔中 StageNow，最後一個步驟時，選取**匯出至 MDM**。 這會產生 XML 檔案。 儲存這個檔案。 您需要在稍後的步驟。

> [!TIP]
> 建議您測試設定檔，再將它部署至裝置在您的組織。 若要測試，請使用 StageNow 建立設定檔，在您的電腦上時的最後一個步驟中使用**測試**選項。 然後，使用 StageNow 產生的檔案與 StageNow 應用程式在裝置上。 
> 
> StageNow 應用程式在裝置上的會顯示當您測試設定檔時，產生的記錄檔。 [使用 StageNow 登入在 Intune 中執行 Android 的色彩裝置](android-zebra-mx-logs-troubleshoot.md)已使用 StageNow 記錄檔以了解錯誤的詳細資訊。

> [!NOTE]
> 如果您參考應用程式、 更新套件，或更新 StageNow 設定檔中的其他檔案，您會想要取得這些更新的裝置。 若要取得更新，裝置必須連接到 StageNow 部署伺服器時套用的設定檔。 
> 
> 或者，您可以在 Intune 中使用內建功能，以取得這些變更，包括： 
> - 應用程式管理功能與[新增](apps-add.md)，[部署](apps-deploy.md)，更新，並[監視器](apps-monitor.md)應用程式。
> - 管理[系統和應用程式的更新](device-restrictions-android-for-work.md#device-owner-only)在裝置上執行 Android 的企業版

測試檔案之後下, 一個步驟是將設定檔部署到使用 Intune 的裝置。

> [!NOTE]
> 將一個設定檔部署到每個裝置。 如果您想要部署的裝置上的多個 StageNow 設定檔，然後匯出 StageNow 設定檔，並結合成單一 XML 檔案的設定，才能將它新增至 Intune。 
> 
> 您不想設定相同的屬性相同的 XML 檔案中的兩個設定。 目標是為了防止在裝置上的設定相衝突。

## <a name="step-5-create-a-profile-in-intune"></a>步驟 5： 在 Intune 中建立設定檔

在 Intune 中，建立裝置組態設定檔：

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務] > 篩選 [Intune] > 選取 [Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入下列內容：

    - **名稱**：為新的設定檔輸入描述性名稱。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取 [Android]。
    - **設定檔類型**： 選取  **MX 設定檔 （僅色彩）**。

4. 在  **MX.xml 格式的設定檔**，新增 XML 設定檔[從 StageNow 匯出](#step-4-create-a-device-management-profile-in-stagenow)（在本文中）。
5. 選取 [確定] > [建立] 儲存您的變更。 建立原則，並顯示在清單中。

設定檔已建立，但還不會執行任何動作。 接下來，[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

下次裝置會檢查組態更新 MX 設定檔部署至裝置。 當裝置註冊時，與 Intune 同步處理裝置，然後大約每隔 8 小時。 您也可以[強制在 Intune 中的同步處理](device-sync.md)。 或者，您也可以在裝置上，開啟**公司入口網站應用程式** > **設定** > **同步**。 

> [!TIP]
> - 基於安全性理由，您不會看到設定檔的 XML 文字之後您將它儲存。 文字已經加密，並只會看到星號 (`****`)。 供您參考，建議您先儲存 MX 設定檔的複本，才能將它們新增至 Intune。
> 
> - 若要更新設定檔，它會指派給色彩裝置之後，建立更新的 StageNow XML 檔案、 編輯現有的 Intune 設定檔，並加入新的 StageNow XML 檔案。 這個新檔案會覆寫先前 StageNow 原則設定檔中。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

[使用 StageNow 記錄來疑難排解色彩裝置](android-zebra-mx-logs-troubleshoot.md)。
