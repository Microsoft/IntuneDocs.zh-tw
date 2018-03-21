---
title: "針對 Windows 8.1 及更新版本匯入 Wi-Fi 設定"
titleSuffix: Microsoft Intune
description: "如何將 Windows 的 Wi-Fi 設定匯入 Intune Wi-Fi 設定檔。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 890a10ecf4212656c189adaf46bb2839898758c1
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>在 Microsoft Intune 中匯入 Windows 8.1 及更新版本之裝置的 Wi-Fi 設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

針對執行 Windows 8.1、Windows 10 Desktop 或行動裝置版、或 Windows Holographic for Business 的裝置，您可以匯入先前已匯出至檔案的 Wi-Fi 組態設定檔。

## <a name="export-wi-fi-settings-from-a-windows-device"></a>從 Windows 裝置匯出 Wi-Fi 設定

在 Windows 中，您可以使用 **netsh wlan** 公用程式，將現有的 Wi-Fi 設定檔匯出到 Intune 能夠讀取的 XML 檔案。 在已安裝必要 Wi-Fi 設定檔的 Windows 電腦上，請遵循下列程序。
1. 為匯出 W-Fi 設定檔建立本機資料夾，例如 **c:\WiFi**。
1. 以系統管理員身分開啟命令提示字元。
1. 執行命令 **netsh wlan show profiles**，然後記下您要匯出之設定檔的名稱。 在此範例中，設定檔名稱是 **WiFiName**。
1. 執行命令 **netsh wlan export profile name="ProfileName" folder=c:\Wifi**。這會在您的目標資料夾中建立名為 **Wi-Fi-WiFiName.xml** 的 Wi-Fi 設定檔。

## <a name="import-the-wi-fi-settings-into-intune"></a>將 Wi-Fi 設定匯入 Intune

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [監視 + 管理] 區段。
3. 在 [Intune] 窗格中，選擇 [裝置設定]。
4. 在 [裝置設定] 窗格的 [管理] 區段下，選擇 [設定檔]。
5. 在 [設定檔] 窗格中，按一下 [建立設定檔]。
6. 在 [建立設定檔] 窗格上，輸入裝置限制設定檔的 [名稱] 和 [描述]。


   > [!WARNING]
   > 名稱**必須**和 Wi-Fi 設定檔 XML 的名稱屬性相同，否則會失敗。

7. 從 [平台] 下拉式清單中選擇 [Windows 8.1 及更新版本]。
8. 從 [設定檔類型] 下拉式清單中選擇 [Wi-Fi 匯入]。
9. 在 [Wi-Fi] 窗格中進行下列設定︰
    - **連線名稱** - 輸入 Wi-Fi 連線的名稱。 當使用者瀏覽可用的 Wi-Fi 網路時，會看到此名稱。
    - **設定檔 XML** - 按一下 [瀏覽] 按鈕可選取內含您要匯入 Intune 之 Wi-Fi 設定檔設定的 XML 檔案。
    - **檔案內容** - 顯示所選組態設定檔的 XML 程式碼。
10. 當您完成時，請選擇 [確定] 返回 [建立設定檔] 窗格，然後選取 [建立]。

設定檔隨即建立，並出現在 [設定檔清單] 窗格上。
