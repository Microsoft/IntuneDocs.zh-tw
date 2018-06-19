---
title: 執行 Windows 10 的裝置的 Microsoft Intune 自訂設定
titlesuffix: ''
description: 了解您可以在 Windows 10 自訂設定檔中設定的自訂設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 36705c49a55c88c41470feaad14520e900dcb3dd
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31837008"
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-10"></a>執行 Windows 10 的裝置的 Microsoft Intune 自訂裝置設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

 使用適用於 Windows 10 和 Windows 10 行動裝置版的 Microsoft Intune **自訂**設定檔，部署 OMA-URI (開放行動聯盟的統一資源識別項) 設定，此設定可用來控制裝置上的功能。 Windows 10 讓許多設定服務提供者 (CSP) 設定可供使用，例如[原則設定服務提供者 (原則 CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)。
如果您正在尋找特定的設定，請記住 [Windows 10 裝置限制設定檔](device-restrictions-windows-10.md)包含許多內建於 Intune 的設定，而且您不需要指定自訂值。

## <a name="configure-custom-settings"></a>設定自訂設定

1. 請使用[如何在 Microsoft Intune 中設定自訂裝置設定](custom-settings-configure.md)中的指示，即可開始使用。
1. 在 [Custom OMA-URI Settings] (自訂 OMA URI 設定) 窗格上，按一下 [新增] 以新增值。 您也可以按一下 [匯出]，建立所有值的清單 (以逗號分隔值 (.csv) 的方式設定的檔案)。
1. 為您想要新增的各個 OMA-URI 設定輸入下列資訊。 使用本文中的清單，了解您可使用的相關設定︰
    - **名稱** - 輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。
    - **描述**：選擇性地輸入設定的描述。
    - **OMA-URI (區分大小寫)** - 指定您想要為其提供設定的 OMA-URI。
    - **資料類型** - 從以下項目選擇︰
        - **字串**
        - **字串 (XML)**
        - **日期和時間**
        - **整數**
        - **浮點數**
        - **布林值**
        - **Base64**
    - **值** - 指定要與您輸入的 OMA-URI 產生關聯的值或檔案。
1. 當您完成時，請選取 [確定] 返回 [建立設定檔] 窗格，然後選取 [建立]。
設定檔隨即建立，並出現在 [設定檔清單] 窗格上。

## <a name="example"></a>範例
在下列螢幕擷取畫面中，已啟用 **Connectivity/AllowVPNOverCellular** 設定。 這可讓 Windows 10 裝置在行動電話通訊網路上時，開啟 VPN 連線。

> ![包含 VPN 設定的自訂原則範例](./media/custom-policy-example.png)


## <a name="how-to-find-the-policies-you-can-configure"></a>如何尋找可設定的原則

在 Windows 文件庫的[設定服務提供者參考 (英文)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) 中，可以找到 Windows 10 所支援所有設定服務提供者 (CSP) 的完整清單。

並非所有設定都與所有的 Windows 10 版本相容。 Windows 文章中的表格會顯示每個 CSP 所支援的版本。

此外，Intune 不支援文章中列出的所有設定。 若要了解 Intune 是否支援您想要的設定，請開啟該設定的文章。 每個設定頁面都會顯示它所支援的作業。 若要使用 Intune，該設定必須支援「新增」或「取代」作業。
