---
title: Microsoft Intune 中適用於 Windows Holographic for Business 的裝置限制 - Azure | Microsoft Docs
description: 了解及設定 Microsoft Intune 中適用於 Windows Holographic for Business 的裝置限制設定，包括取消註冊、地理位置、密碼、從 App Store 安裝應用程式、Microsoft Edge 中的 Cookie 和快顯、Windows Defender、搜尋、雲端與儲存體、藍牙連線能力、系統時間，以及 Azure 中的使用情況資料。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f79985c9854af462fa9a456304a3184128283b9c
ms.sourcegitcommit: d8edd1c3d24123762dd6d14776836df4ff2a31dd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2018
ms.locfileid: "51576795"
---
# <a name="device-restriction-settings-for-windows-holographic-for-business-in-intune"></a>Intune 中適用於 Windows Holographic for Business 的裝置限制

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

執行 Windows Holographic for Business 的裝置，例如 Microsoft Hololens，支援下列裝置限制設定。

## <a name="general"></a>一般

- **手動取消註冊** - 讓使用者可從裝置手動刪除工作場所帳戶。
- **Cortana** - 啟用或停用 Cortana 語音助理。
- **地理位置** - 指定裝置是否可以使用定位服務資訊。

## <a name="password"></a>密碼
-   **密碼** - 需要使用者輸入密碼才可存取該裝置。
    -   **裝置從閒置狀態回復時需要密碼** - 指定使用者必須輸入密碼才能解除鎖定裝置。

## <a name="app-store"></a>App Store

-   **自動更新來自市集的應用程式** - 允許自動更新從 Microsoft 網上商店安裝的應用程式。
-   **安裝信任的應用程式** - 允許側載使用受信任憑證簽署的應用程式。
-   **開發人員解除鎖定** - 允許 Windows 開發人員設定，例如允許使用者修改側載應用程式。

## <a name="microsoft-edge-browser"></a>Microsoft Edge 瀏覽器

-   **Cookie** - 讓瀏覽器儲存網際網路 Cookie 到裝置上。
-   **快顯視窗** - 封鎖瀏覽器中的快顯視窗 (僅適用於 Windows 10 Desktop)。
-   **搜尋建議** - 讓您的搜尋引擎在您輸入搜尋片語時建議網站。
-   **密碼管理員** - 啟用或停用 Microsoft Edge [密碼管理員] 功能。
- **傳送不追蹤標頭** - 設定 Microsoft Edge 瀏覽器以傳送不追蹤標頭給使用者瀏覽的網站。

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen 篩選工具

- **適用於 Microsoft Edge 的 SmartScreen 篩選工具** - 啟用 Microsoft Edge SmartScreen 以存取網站和檔案下載。

## <a name="search"></a>搜尋
- **搜尋位置** - 指定搜尋是否可使用位置資訊。 資訊

## <a name="cloud-and-storage"></a>雲端與儲存體
-   **Microsoft 帳戶** - 讓使用者建立 Microsoft 帳戶與裝置之間的關聯。

## <a name="cellular-and-connectivity"></a>行動數據與連線

-   **藍牙**- 控制使用者是否可在裝置上啟用及設定藍牙。
-   **藍牙探索** - 讓其他藍牙啟用的裝置探索此裝置。
-   **藍牙廣告** - 讓藍牙可透過藍牙裝置接收廣告。

## <a name="control-panel-and-settings"></a>控制台和設定

- **修改系統時間** - 防止使用者變更裝置日期和時間。

## <a name="kiosk---obsolete"></a>Kiosk - 已淘汰

這些設定為唯讀且無法變更。 若要設定 kiosk 模式，請參閱 [Kiosk 設定](kiosk-settings.md#windows-holographic-for-business)。

Kiosk 裝置通常會執行特定的應用程式。 使用者無法存取裝置上 kiosk 應用程式外的任何功能。

- **Kiosk 模式** - 識別原則所支援的 kiosk 模式類型。 這些選項包括：

  - **未設定** (預設) - 不啟用 kiosk 模式的原則。 
  - **單一應用程式 kiosk** - 此設定檔可讓裝置只在單一應用程式上執行。 當使用者登入時，會啟動特定的應用程式。 此模式也會限制使用者開啟新的應用程式或變更執行中的應用程式。
  - **多應用程式 kiosk** - 此設定檔可讓裝置在多個應用程式上執行。 只有您新增的應用程式才可供使用者使用。 多應用程式 kiosk (或固定用途裝置) 的好處是讓個人只存取所需的應用程式，來為個人提供一個簡單明瞭的體驗。 此外，還可從其檢視中移除不需要的應用程式。 
  
    當您為多應用程式 kiosk 體驗新增應用程式時，也會新增 [開始] 功能表配置檔案。 [[開始] 功能表配置檔案](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-file-for-intune)包含可用於 Intune 中的範例 XML。 

#### <a name="single-app-kiosks"></a>單一應用程式 Kiosk
輸入下列設定：

- **使用者帳戶** - 輸入與 kiosk 應用程式關聯的本機 (對裝置而言) 使用者帳戶或 Azure AD 帳戶登入。 針對已加入 Azure AD 網域的帳戶，請使用 `domain\username@tenant.org` 格式來輸入帳戶。 

    針對在面對大眾的環境中且已啟用自動登入功能的 kiosk，應該使用權限最低 (例如本機標準使用者帳戶) 的使用者類型。 若要設定 Azure Active Directory (AD) 帳戶以使用 kiosk 模式，請使用 `AzureAD\user@contoso.com` 格式。

- **應用程式的應用程式使用者模型識別碼 (AUMID)** - 輸入 kiosk 應用程式的 AUMID。 若要深入了解，請參閱 [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)(尋找已安裝應用程式的應用程式使用者模型識別碼)。

## <a name="reporting-and-telemetry"></a>報告和遙測

- **共用使用方式資料** - 選取診斷資料傳送層級。
