---
title: 在 Microsoft Intune 中為 Windows 裝置匯入 Wi-Fi 設定 - Azure | Microsoft Docs
description: 使用 netsh wlan，從 Windows 裝置將 Wi-Fi 設定匯出成 XML 檔案。 接著再將此檔案匯入 Intune，為執行 Windows 8.1、Windows 10 及 Windows Holographic for Business 的裝置匯入 Wi-Fi 設定檔。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f79ccdc71ddbfa3f25daef629515fb612de01852
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207004"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>在 Intune 中，為 Windows 裝置匯入 Wi-Fi 設定

對於執行 Windows 的裝置，您可以匯入先前匯出到檔案的 Wi-Fi 設定檔。 **對於 Windows 10 及更新版本的裝置，您也可以直接在 Intune 中[建立 Wi-Fi 設定檔](wi-fi-settings-windows.md)** 。

適用於：  
- Windows 8.1 及更新版本
- Windows 10 及更新版本
- Windows 10 Desktop 或行動裝置版
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>從 Windows 裝置匯出 Wi-Fi 設定

在 Windows 中，您可以使用 `netsh wlan`，將現有的 Wi-Fi 設定檔匯出成 Intune 能夠讀取的 XML 檔案。 必須以純文字格式匯出金鑰，才能順利使用設定檔。

在已安裝必要 WiFi 設定檔的 Windows 電腦上，請使用下列步驟：

1. 為匯出的 Wi-Fi 設定檔建立本機資料夾，例如 **c:\WiFi**。
2. 以系統管理員身分開啟命令提示字元。
3. 執行 `netsh wlan show profiles` 命令。 記下您想要匯出的設定檔名稱。 在此範例中，設定檔名稱是 **WiFiName**。
4. 執行 `netsh wlan export profile name="ProfileName" folder=c:\Wifi` 命令。 此命令會在目標資料夾中建立名為 **Wi-Fi-WiFiName.xml** 的 Wi-Fi 設定檔。

## <a name="import-the-wi-fi-settings-into-intune"></a>將 Wi-Fi 設定匯入 Intune

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
3. 輸入下列設定：

    - **名稱**：為設定檔輸入描述性名稱。 名稱**必須**與 Wi-Fi 設定檔 XML 中的名稱屬性相同。 否則，就會發生失敗。
    - **描述**：輸入描述來概述設定和其他重要的詳細資料。
    - **平台**：選取 [Windows 8.1 及更新版本]  。
    - **設定檔類型**：選取 [Wi-Fi 匯入]  。

    > [!IMPORTANT]
    > - 如果您要匯出包含預先共用金鑰的 Wi-Fi 設定檔，就**必須**將 `key=clear` 新增至命令中。 例如，輸入：`netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - 搭配 Windows 10 使用預先共用金鑰會導致在 Intune 中顯示補救錯誤。 發生這種情況時，系統會將 Wi-Fi 設定檔適當地指派給裝置，而該設定檔將如預期般運作。
    > - 如果您要匯出包含預先共用金鑰的 Wi-Fi 設定檔，請確定該檔案受到保護。 該金鑰會採用存文字格式，因此您需負責保護該金鑰。

4. 輸入下列設定：

    - **連線名稱**：輸入 Wi-Fi 連線的名稱。 當使用者流覽可用的 Wi-fi 網路時，會向他們顯示此名稱。
    - **設定檔 XML**：選取瀏覽按鈕，然後選取包含您想匯入之 Wi-Fi 設定檔設定的 XML 檔案。
    - **檔案內容**：顯示您所選取組態設定檔的 XML 程式碼。

5. 按一下 [確定]  以儲存您的變更。
6. 完成時，選取 [確定]   > [建立]  以建立 Intune 設定檔。 完成時，您的設定檔會顯示在 [裝置 - 設定檔]  清單中。

## <a name="next-steps"></a>後續步驟

設定檔已建立，但它不會執行任何動作。 接下來，[指派設定檔](../device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

請參閱 [Wi-Fi 設定概觀](wi-fi-settings-configure.md)，包括其他可用平台。
