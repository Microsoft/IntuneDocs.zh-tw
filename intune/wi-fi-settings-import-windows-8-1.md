---
title: "針對 Windows 8.1 及更新版本匯入 Wi-Fi 設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰如何設定將 Windows 的 Wi-Fi 設定匯入 Intune Wi-Fi 設定檔。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2c4e9b19-b268-4f6d-9663-7cdbe4e4a8dd
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 80181ce809265dc4289e56ef65aff66214d2e765
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>如何在 Microsoft Intune 中匯入 Windows 8.1 及更新版本之裝置的 Wi-Fi 設定

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

針對執行 Windows 8.1 或 Windows 10 Desktop 或行動裝置版的裝置，您可以匯入先前匯出至檔案的 Wi-Fi 組態設定檔。

## <a name="export-wi-fi-settings-from-a-windows-device"></a>從 Windows 裝置匯出 Wi-Fi 設定

在 Windows 中，您可以使用 **netsh wlan** 公用程式，將現有的 Wi-Fi 設定檔匯出到 Intune 能夠讀取的 XML 檔案。 在已安裝必要 Wi-Fi 設定檔的 Windows 電腦上，請遵循下列程序。
1. 為匯出 W-Fi 設定檔建立本機資料夾，例如 **c:\WiFi**。
1. 以系統管理員身分開啟命令提示字元。
1. 執行命令 **netsh wlan show profiles**，然後記下您要匯出之設定檔的名稱。 在此範例中，設定檔名稱是 **WiFiName**。
1. 執行命令 **netsh wlan export profile name="ProfileName" folder=c:\Wifi**。這會在您的目標資料夾中建立名為 **w-Fi-WiFiName.xml** 的 Wi-Fi 設定檔。

## <a name="import-the-wi-fi-settings-into-intune"></a>將 Wi-Fi 設定匯入 Intune

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置設定]。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
3. 在 [設定檔] 刀鋒視窗中，按一下 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗中，為裝置限制設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中選擇 [Windows 8.1 及更新版本]。
6. 從 [設定檔類型] 下拉式清單中選擇 [Wi-Fi 匯入]。
7. 在 [Wi-Fi Basic] 刀鋒視窗中設定下列各項︰
    - **連線名稱** - 輸入 Wi-Fi 連線的名稱。 當使用者瀏覽可用的 Wi-Fi 網路時，會對使用者顯示此名稱。
    - **設定檔 XML** - 按一下 [瀏覽] 按鈕可選取內含您要匯入 Intune 之 Wi-Fi 設定檔設定的 XML 檔案。
    - **檔案內容** - 顯示所選組態設定檔的 XML 程式碼。
8. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。

