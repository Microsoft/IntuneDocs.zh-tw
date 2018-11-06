---
title: 在 Microsoft Intune 中新增 Windows 10 裝置的自訂設定 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中新增或建立自訂設定檔，將 OMA-URI 設定用於執行 Windows 10 的裝置。 使用自訂設定檔新增自訂設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 78ed923c7502744ccd7f23e341049ce8ee8a8d86
ms.sourcegitcommit: c969b596ec0fec227484c50f210ba4e159e2e533
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2018
ms.locfileid: "49983205"
---
# <a name="use-custom-settings-for-windows-10-devices-in-intune"></a>在 Intune 中使用 Windows 10 裝置的自訂設定

透過 Microsoft Intune，您可以使用「自訂設定檔」新增或建立 Windows 10 裝置的自訂設定。 自訂設定檔是 Intune 中的功能。 其設計目的是為了新增未內建在 Intune 的裝置設定和功能。

Windows 10 自訂設定檔會使用開放行動聯盟的統一資源識別項 (OMA-URI) 設定來進行各種功能設定。 行動裝置製造商通常會使用這些設定來控制裝置上的功能。 

Windows 10 讓許多設定服務提供者 (CSP) 設定可供使用，例如[原則設定服務提供者 (原則 CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)。

如果您正在尋找特定的設定，請記住 [Windows 10 裝置限制設定檔](device-restrictions-windows-10.md)包含許多內建設定。 因此，您可能不需要輸入自訂值。

本文示範：

- 如何建立 Windows 10 裝置的自訂設定檔
- 包含建議的 OMA-URI 設定清單
- 提供開啟 VPN 連線的自訂設定檔範例

## <a name="create-the-profile"></a>建立設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入下列設定：

    - **名稱**：輸入設定檔的名稱，例如 `windows 10 custom profile`。
    - **描述**：輸入設定檔的描述。
    - **平台**：選擇 [Windows 10 及更新版本]。
    - **設定檔類型**：選擇 [自訂]。

4. 在 [自訂 OMA-URI 設定] 中，選取 [新增]。 輸入下列設定：

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

    - **值**：輸入要與您輸入之 OMA-URI 相關聯的資料值。 該值取決於您選取的資料類型。 例如，如果您選擇 [日期和時間]，請從日期選擇器選取值。

    新增一些設定之後，您可以選取 [匯出]。 [匯出] 會以逗號分隔值 (.csv) 檔案格式，為您新增的所有值建立一份清單。

5. 按一下 [確定] 以儲存您的變更。 視需要繼續新增更多設定。
6. 完成時，選擇 [確定] > [建立] 以建立 Intune 設定檔。 完成時，您的設定檔會顯示在 [裝置設定 - 設定檔] 清單中。

## <a name="example"></a>範例

在下列範例中，已啟用 **Connectivity/AllowVPNOverCellular** 設定。 此設定可讓 Windows 10 裝置在行動電話通訊網路上時，開啟 VPN 連線。

![包含 VPN 設定的自訂原則範例](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>尋找可設定的原則

在 [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (設定服務提供者參考) 中，可以找到 Windows 10 所支援所有設定服務提供者 (CSP) 的完整清單。

並非所有設定都與所有的 Windows 10 版本相容。 [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (設定服務提供者參考) 告訴您每個 CSP 所支援的版本。

此外，Intune 不支援所有在 [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (設定服務提供者參考) 中列出的設定。 若要了解 Intune 是否支援您想要的設定，請開啟該設定的文章。 每個設定頁面都會顯示它所支援的作業。 若要使用 Intune，該設定必須支援「新增」或「取代」作業。

## <a name="next-steps"></a>接下來的步驟

設定檔已建立，但還不會執行任何動作。 接下來，請[指派此設定檔](device-profile-assign.md)。
