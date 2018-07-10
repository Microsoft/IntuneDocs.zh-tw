---
title: Microsoft Intune 中適用於 Windows 10 裝置的自訂設定 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 中的自訂設定檔，在執行 Windows 10 的裝置上設定 OMA-URI 自訂設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bdbb6643a4ee8aace0db22cd7f9189f7ac6445f0
ms.sourcegitcommit: ada99fefe9a612ed753420116f8c801ac4bf0934
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36232821"
---
# <a name="custom-oma-uri-settings-for-windows-10-devices---intune"></a>適用於 Windows 10 裝置的自訂 OMA-URI 設定 - Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用適用於 Windows 10 和 Windows 10 行動裝置版的 Microsoft Intune **自訂**設定檔，部署 OMA-URI (開放行動聯盟的統一資源識別項) 設定。 這些設定可用來控制裝置上的功能。 Windows 10 讓許多設定服務提供者 (CSP) 設定可供使用，例如[原則設定服務提供者 (原則 CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)。

如果您正在尋找特定設定，請記住 [Windows 10 裝置限制設定檔](device-restrictions-windows-10.md)包含許多內建於 Intune 的設定，而且不需要自訂值。

## <a name="configure-custom-settings"></a>設定自訂設定

1. 使用**自訂**設定檔類型來建立新的組態設定檔。 [如何設定自訂裝置設定](custom-settings-configure.md)列出步驟。
2. 在 [自訂 OMA-URI 設定]中，選取 [新增] 建立新的設定。 您也可以按一下 [匯出]，建立所有值的清單 (以逗號分隔值 (.csv) 的方式設定的檔案)。
3. 針對要新增的各個 OMA-URI 設定，輸入下列資訊：

- **名稱**：輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。
- **描述**：選擇性輸入設定的描述。
- **OMA-URI (區分大小寫)**：輸入您想要為其提供設定的 OMA-URI。
- **資料類型**：從以下項目選擇︰
  - **字串**
  - **字串 (XML)**
  - **日期和時間**
  - **整數**
  - **浮點數**
  - **布林值**
  - **Base64**
- **值**：輸入要與您所輸入 OMA-URI 建立關聯的值或檔案。

4. 完成後，請選取 [確定]。 在 [建立設定檔] 中，選取 [建立]。 設定檔隨即建立，並顯示在設定檔清單中。

## <a name="example"></a>範例
在下列範例中，已啟用 **Connectivity/AllowVPNOverCellular** 設定。 此設定可讓 Windows 10 裝置在行動電話通訊網路上時，開啟 VPN 連線。

![包含 VPN 設定的自訂原則範例](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>尋找可設定的原則

在 [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (設定服務提供者參考) 中，可以找到 Windows 10 所支援所有設定服務提供者 (CSP) 的完整清單。

並非所有設定都與所有的 Windows 10 版本相容。 [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (設定服務提供者參考) 告訴您每個 CSP 所支援的版本。

此外，Intune 不支援列出的所有設定。 若要了解 Intune 是否支援您想要的設定，請開啟該設定的文章。 每個設定頁面都會顯示它所支援的作業。 若要使用 Intune，該設定必須支援「新增」或「取代」作業。
