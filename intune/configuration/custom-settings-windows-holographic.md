---
title: 自訂設定 - Windows Holographic for Business 裝置 - Microsoft Intune
description: 在 Microsoft Intune 中新增或建立自訂設定檔，以將 OMA-URI 設定用於執行 Windows Holographic for Business 的裝置，包括 Microsoft Hololens。 您可以設定 AllowFastReconnect、AllowVPN、AllowUpdateService、UpdateServiceURL、RequireUpdatesApproval、ApprovedUpdates 及 ApplicationLaunchRestrictions 原則設定服務提供者 (CSP) 設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.article: article
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.topic: reference
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 54c38bac5ddf9eee1dd5f1dc6d544de3fa2395ab
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506912"
---
# <a name="use-custom-settings-for-windows-holographic-for-business-devices-in-intune"></a>在 Intune 中使用 Windows Holographic for Business 裝置的自訂設定

透過 Microsoft Intune，您可以使用「自訂設定檔」新增或建立 Windows Holographic for Business 裝置的自訂設定。 自訂設定檔是 Intune 中的功能。 其設計目的是為了新增未內建在 Intune 的裝置設定和功能。

Windows Holographic for Business 自訂設定檔會使用開放行動聯盟的統一資源識別項 (OMA-URI) 設定來進行各種功能設定。 行動裝置製造商通常會使用這些設定來控制裝置上的功能。

Windows Holographic for Business 提供許多設定服務提供者 (CSP) 設定。 如需 CSP 概觀，請參閱[適用於 IT 專業人員的設定服務提供者 (CSP) 簡介](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)。 如需 Windows Holographic 支援的特定 CSP，請參閱 [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (Windows Holographic 支援的 CSP)。

如果您正在尋找特定的設定，請記住 [Windows Holographic for Business 裝置限制設定檔](device-restrictions-windows-holographic.md)包含許多內建設定。 因此，您可能不需要輸入自訂值。

本文示範如何建立 Windows Holographic for Business 裝置的自訂設定檔。 其中也包含建議的 OMA-URI 設定清單。

## <a name="create-the-profile"></a>建立設定檔

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
3. 輸入下列設定：

    - **名稱**：輸入設定檔的名稱，例如 `hololens custom profile`。
    - **描述**：輸入設定檔的描述。
    - **平台**：選擇 [Windows 10 及更新版本]  。
    - **設定檔類型**：選擇 [自訂]  。

4. 在 [自訂 OMA-URI 設定]  中，選取 [新增]  。 輸入下列設定：

    - **名稱**：輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。
    - **描述**：輸入描述來概述設定和其他重要的詳細資料。
    - **OMA-URI** (區分大小寫)：輸入您要用作設定的 OMA-URI。
    - **資料類型**：選擇您要用於這個 OMA-URI 設定的資料類型。 選項包括：

        - 字串
        - 字串 (XML 檔案)
        - 日期和時間
        - 整數
        - 浮點數
        - 布林值
        - Base64 (檔案)

    - **值**：輸入要與您輸入之 OMA-URI 相關聯的資料值。 該值取決於您選取的資料類型。 例如，如果您選擇 [日期和時間]  ，請從日期選擇器選取值。

    新增一些設定之後，您可以選取 [匯出]  。 [匯出]  會以逗號分隔值 (.csv) 檔案格式，為您新增的所有值建立一份清單。

5. 按一下 [確定]  以儲存您的變更。 視需要繼續新增更多設定。
6. 完成時，選擇 [確定]   > [建立]  以建立 Intune 設定檔。 完成時，您的設定檔會顯示在 [裝置設定 - 設定檔]  清單中。

## <a name="recommended-custom-settings"></a>建議的自訂設定

下列設定適用於執行 Windows Holographic for Business 的裝置：

### <a name="allowfastreconnecthttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-authenticationauthentication-allowfastreconnect"></a>[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)

> [!div class="mx-tableFixed"]
> |OMA-URI|資料類型|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|整數<br/>0 - 不允許<br/>1 - 允許 (預設值)|

### <a name="allowupdateservicehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-allowupdateservice"></a>[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)

> [!div class="mx-tableFixed"]
> |OMA-URI|資料類型|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|整數<br/>0 – 不允許更新服務 <br/>1 – 允許更新服務允許 (預設值)。|

### <a name="allowvpnhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-settingssettings-allowvpn"></a>[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)

> [!div class="mx-tableFixed"]
> |OMA-URI|資料類型|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|整數<br/>0 - 不允許<br/>1 - 允許 (預設值)|

### <a name="requireupdatesapprovalhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-requireupdateapproval"></a>[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)

> [!div class="mx-tableFixed"]
> |OMA-URI|資料類型|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|整數<br/>0 - 未設定。 裝置會安裝所有適用的更新。<br/>1 - 裝置只會安裝適用並且在核准更新清單上的更新。 如果 IT 想要控制在裝置上部署更新，例如需要先測試才能部署時，將此原則設定為 1。|

### <a name="scheduledinstalltimehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-scheduledinstalltime"></a>[ScheduledInstallTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduledinstalltime)

> [!div class="mx-tableFixed"]
> |OMA-URI|資料類型|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|整數 0-23，其中 0 = 上午 12 點，23 = 下午 11 點<br/>預設值為 3。|

### <a name="updateserviceurlhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-updateserviceurl"></a>[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

> [!div class="mx-tableFixed"]
> |OMA-URI|資料類型|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|字串<br/>URL - 裝置會在指定的 URL 檢查來自 WSUS 伺服器的更新。<br/>未設定 - 裝置會檢查來自 Microsoft Update 的更新。|

### <a name="approvedupdateshttpsdocsmicrosoftcomwindowsclient-managementmdmupdate-csp"></a>[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|資料類型|
> |---|---|
> |./Vendor/MSFT/Update/ApprovedUpdates/*GUID*<br/><br/>**重要**<br/>您必須閱讀並代表您的使用者接受更新 EULA。 若不這樣做將違反法律或契約義務。|更新核准以及代表終端使用者接受 UELA 的節點。<br/><br/>如需詳細資訊，請參閱[更新 CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp)。|

### <a name="applicationlaunchrestrictionshttpsdocsmicrosoftcomwindowsclient-managementmdmapplocker-csp"></a>[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|資料類型|
> |----|---|
> |./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br/><br/>**重要**<br/>AppLocker CSP 文章使用逸出的 XML 範例。 若要使用 Intune 自訂設定檔進行設定，您必須使用純文字 XML。|字串<br/>如需詳細資訊，請參閱 [AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)。|

### <a name="deletionpolicyhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[DeletionPolicy](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|資料類型|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/DeletionPolicy|整數<br/>0 - 當裝置恢復成沒有目前使用中使用者的狀態時立即刪除<br/>1 - 達到儲存體容量閾值時刪除 (預設)<br/>2 - 同時達到儲存體容量閾值和設定檔非使用狀態閾值時刪除|

### <a name="enableprofilemanagerhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[EnableProfileManager](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|資料類型|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/EnableProfileManager|布林值<br/>True - 啟用<br/>False - 停用 (預設)|

### <a name="profileinactivitythresholdhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[ProfileInactivityThreshold](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|資料類型|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/ProfileInactivityThreshold|整數<br/>預設值為 30。|


### <a name="storagecapacitystartdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStartDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|資料類型|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStartDeletion|整數<br/>預設值為 25。|

### <a name="storagecapacitystopdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStopDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|資料類型|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStopDeletion|整數<br/>預設值為 50。|

## <a name="find-the-policies-you-can-configure"></a>尋找可設定的原則

您可以在 [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (Windows Holographic 支援的 CSP) 中找到 Windows Holographic 支援的所有設定服務提供者 (CSP) 的完整清單。 並非所有設定都與所有的 Windows Holographic 版本相容。 [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (Windows Holographic 支援的 CSP) 中的表格列出每個 CSP 支援的版本。

此外，Intune 不支援所有在 [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (Windows Holographic 支援的 CSP) 中列出的設定。 若要了解 Intune 是否支援您想要的設定，請開啟該設定的文章。 每個設定頁面都會顯示它所支援的作業。 若要使用 Intune，該設定必須支援「新增」  或「取代」  作業。

## <a name="next-steps"></a>後續步驟

設定檔已建立，但還不會執行任何動作。 接下來，請[指派此設定檔](device-profile-assign.md)。

了解如何在 [Windows 10 裝置](../custom-settings-windows-10.md)上建立自訂設定檔。
