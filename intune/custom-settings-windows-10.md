---
title: "Windows 10 裝置的 Intune 自訂設定"
titlesuffix: Azure portal
description: "了解可用於 Windows 10 自訂設定檔中的設定。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7bcea136-7260-4042-b21b-c7dab86b380d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7101c489c0418b98be3224888a8473a77192ce0f
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="custom-device-settings-for-windows-10-devices-in-microsoft-intune"></a>Microsoft Intune 中 Windows 10 裝置的自訂裝置設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 使用適用於 Windows 10 和 Windows 10 行動裝置版的 Microsoft Intune **自訂**設定檔，部署 OMA-URI (開放行動聯盟的統一資源識別項) 設定，此設定可用來控制裝置上的功能。 Windows 10 讓許多 CSP 設定可供使用，例如[原則設定服務提供者 (原則 CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)。
如果您正在尋找特定的設定，請記住 [Windows 10 裝置限制設定檔](device-restrictions-windows-10.md)包含許多內建於 Intune 的設定，而且您不需要指定自訂值。

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
5. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。
隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。

## <a name="example"></a>範例
在下方的螢幕擷取畫面中，已啟用 **Connectivity/AllowVPNOverCellular** 設定。 這可讓 Windows 10 裝置在行動電話通訊網路上時，開啟 VPN 連線。

> ![包含 VPN 設定的自訂原則範例](./media/custom-policy-example.png)


## <a name="how-to-find-the-policies-you-can-configure"></a>如何尋找可設定的原則

在 Windows 文件庫的[設定服務提供者參考 (英文)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) 中，可以找到 Windows 10 所支援所有設定服務提供者 (CSP) 的完整清單。

並非所有設定都與所有的 Windows 10 版本相容。 Windows 主題中的表格會顯示每個 CSP 所支援的版本。

此外，Intune 不支援主題中列出的所有設定。 若要了解 Intune 是否支援您想要的設定，請開啟該設定的主題。 每個設定頁面都會顯示它所支援的作業。 若要使用 Intune，該設定必須支援「新增」或「取代」作業。


