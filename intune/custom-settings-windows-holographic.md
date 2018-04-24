---
title: 在 Microsoft Intune 中自訂 Windows Holographic for Business 裝置的設定 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中建立自訂設定檔以將 OMA-URI 設定用於執行 Windows Holographic for Business 的裝置。 您可以設定 AllowFastReconnect、AllowVPN、AllowUpdateService、UpdateServiceURL、RequireUpdatesApproval、ApprovedUpdates 及 ApplicationLaunchRestrictions 原則設定服務提供者 (CSP) 設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.article: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b349a61d61288f700294e04d029d825afba13445
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="custom-device-settings-for-devices-running-windows-holographic-for-business-in-intune"></a>在 Intune 中為執行 Windows Holographic for Business 的裝置自訂裝置設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

 使用適用於 Windows Holographic for Business 的 Microsoft Intune **自訂**設定檔，部署 OMA-URI (開放行動聯盟的統一資源識別碼) 設定，此設定可用來控制裝置上的功能。 Windows Holographic for Business 提供許多設定服務提供者 (CSP) 設定。 如需 CSP 概觀，請參閱[適用於 IT 專業人員的設定服務提供者 (CSP) 簡介](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)。 如需 Windows Holographic 支援的特定 CSP，請參閱 [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (Windows Holographic 支援的 CSP)。

如果您正在尋找特定的設定，請記住 [Windows Holographic for Business 裝置限制設定檔](device-restrictions-windows-holographic.md)包含許多內建設定，而且您不需要指定自訂值。

## <a name="create-the-custom-oma-uri-profile"></a>建立自訂 OMA-URI 設定檔
1. 使用[在 Microsoft Intune 中設定自訂裝置設定](custom-settings-configure.md)中的指示來開始著手。
2. 在 [建立設定檔] 中選擇 [設定]，可新增一或多個 OMA URI 設定。
3. 在 [自訂 OMA URI 設定] 中，按一下 [新增] 可新增新的值。 您也可以按一下 [匯出]，建立所有值的清單 (以逗號分隔值 (.csv) 的方式設定的檔案)。
4. 針對要新增的各個 OMA-URI 設定，輸入下列資訊：
    - **設定名稱** - 輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。
    - **設定描述** - 選擇性地輸入設定的描述。
    - **資料類型** - 從以下項目選擇︰
        - **字串**
        - **字串 (XML)**
        - **日期和時間**
        - **整數**
        - **浮點數**
        - **布林值**
    - **OMA-URI (區分大小寫)** - 指定您想要為其提供設定的 OMA-URI。
    - **值** - 指定要與您輸入的 OMA-URI 產生關聯的值。
1. 當您完成時，請返回 [建立設定檔]，然後按一下 [建立]。
設定檔隨即建立，並出現在設定檔清單上。

## <a name="recommended-custom-settings"></a>建議的自訂設定

下列設定適用於執行 Windows Holographic for Business 的裝置：

### <a name="allowfastreconnecthttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-authenticationauthentication-allowfastreconnect"></a>[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)

---
|OMA-URI|資料類型  |
|---------|---------|
|./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|整數<br>0 - 不允許<br>1 - 允許 (預設值)|

### <a name="allowvpnhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-settingssettings-allowvpn"></a>[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)

---
|OMA-URI|資料類型  |
|---------|---------|
|./Vendor/MSFT/Policy/Config/Settings/AllowVPN|整數<br>0 - 不允許<br>1 - 允許 (預設值)|

### <a name="allowupdateservicehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-allowupdateservice"></a>[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)

---
|OMA-URI|資料類型  |
|---------|---------|
|./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|整數<br>0 – 不允許更新服務 <br>1 – 允許更新服務允許 (預設值)。|

### <a name="updateserviceurlhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-updateserviceurl"></a>[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

---
|OMA-URI|資料類型  |
|---------|---------|
|./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|字串<br>URL - 裝置會在指定的 URL 檢查來自 WSUS 伺服器的更新。<br>未設定 - 裝置會檢查來自 Microsoft Update 的更新。|

### <a name="requireupdatesapprovalhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-requireupdateapproval"></a>[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)

---
|OMA-URI|資料類型  |
|---------|---------|
|./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|整數<br>0 - 未設定。 裝置會安裝所有適用的更新。<br>1 - 裝置只會安裝適用並且在核准更新清單上的更新。 如果 IT 想要控制在裝置上部署更新，例如需要先測試才能部署時，將此原則設定為 1。|

### <a name="approvedupdateshttpsdocsmicrosoftcomwindowsclient-managementmdmupdate-csp"></a>[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)

---
|OMA-URI|資料類型  |
|---------|---------|
|./Vendor/MSFT/Update/ApprovedUpdates<br><br>**重要**<br>您必須閱讀並代表您的使用者接受更新 EULA。 若不這樣做將違反法律或契約義務。|更新核准以及代表終端使用者接受 UELA 的節點。|

### <a name="applicationlaunchrestrictionshttpsdocsmicrosoftcomwindowsclient-managementmdmapplocker-csp"></a>[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)

---
|OMA-URI|資料類型  |
|---------|---------|
|./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br><br>**重要**<br>AppLocker CSP 文章使用逸出的 XML 範例。 若要使用 Intune 自訂設定檔進行設定，您必須使用純文字 XML。|字串<br>如需詳細資訊，請參閱 [AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)。|

## <a name="find-the-policies-you-can-configure"></a>尋找可設定的原則

您可以在 [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (Windows Holographic 支援的 CSP) 中找到 Windows Holographic 支援的所有設定服務提供者 (CSP) 的完整清單。 並非所有設定都與所有的 Windows Holographic 版本相容。 Windows 文章中的表格會顯示每個 CSP 所支援的版本。

此外，Intune 不支援文章中列出的所有設定。 若要了解 Intune 是否支援您想要的設定，請開啟該設定的文章。 每個設定頁面都會顯示它所支援的作業。 若要使用 Intune，該設定必須支援「新增」或「取代」作業。
