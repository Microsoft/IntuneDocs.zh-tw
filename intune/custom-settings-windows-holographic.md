---
title: "適用於 Windows Holographic for Business 裝置的 Intune 自訂設定"
titlesuffix: Azure portal
description: "了解可用於 Windows Holographic for Business 自訂設定檔中的設定。」"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 1/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ae46aef10ca294637a4d433ce273d3c53e695d64
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="custom-device-settings-for-windows-holographic-for-business-devices-in-microsoft-intune"></a>在 Microsoft Intune 中為 Windows Holographic for Business 裝置自訂裝置設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 使用適用於 Windows Holographic for Business 的 Microsoft Intune **自訂**設定檔，部署 OMA-URI (開放行動聯盟的統一資源識別碼) 設定，此設定可用來控制裝置上的功能。 Windows Holographic for Business 提供許多設定服務提供者 (CSP) 設定。 如需 CSP 概觀，請參閱[適用於 IT 專業人員的設定服務提供者 (CSP) 簡介](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)。 如需 Windows Holographic 支援的特定 CSP，請參閱 [CSPs supported in Windows Holographic](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens) (Windows Holographic 支援的 CSP)。

如果您正在尋找特定的設定，請記住 [Windows Holographic for Business 裝置限制設定檔](device-restrictions-windows-holographic.md)包含許多內建設定，而且您不需要指定自訂值。

1. 請使用[如何在 Microsoft Intune 中設定自訂裝置設定](custom-settings-configure.md)中的指示，即可開始使用。
2. 在 [建立設定檔] 刀鋒視窗中選擇 [設定]，可新增一或多個 OMA URI 設定。
3. 在 [自訂 OMA URI 設定] 刀鋒視窗中，按一下 [新增] 可新增新的值。 您也可以按一下 [匯出]，建立所有值的清單 (以逗號分隔值 (.csv) 的方式設定的檔案)。
4. 為您想要新增的各個 OMA-URI 設定輸入下列資訊。 使用本主題中的清單，了解您可使用的相關設定︰
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
5. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後按一下 [建立]。
設定檔隨即建立，並出現在 [設定檔清單] 刀鋒視窗上。

## <a name="supported-custom-settings"></a>支援的自訂設定

Windows Holographic for Business 支援下列自訂設定：


|設定名稱|OMA-URI|資料類型  |
|---------|---------|---------|
|AllowFastReconnect     |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|整數 (0 - 不允許，1 - 允許)|
|AllowVPN     |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|整數 (0 - 不允許，1 - 允許)|



## <a name="how-to-find-the-policies-you-can-configure"></a>如何尋找可設定的原則

您可以在 [CSPs supported in Windows Holographic](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens) (Windows Holographic 支援的 CSP) 中找到 Windows Holographic 支援的所有設定服務提供者 (CSP) 的完整清單。 並非所有設定都與所有的 Windows Holographic 版本相容。 Windows 主題中的表格會顯示每個 CSP 所支援的版本。

此外，Intune 不支援主題中列出的所有設定。 若要了解 Intune 是否支援您想要的設定，請開啟該設定的主題。 每個設定頁面都會顯示它所支援的作業。 若要使用 Intune，該設定必須支援「新增」或「取代」作業。


