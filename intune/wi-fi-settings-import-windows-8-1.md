---
title: 在 Microsoft Intune 中為 Windows 裝置匯入 Wi-Fi 設定 - Azure | Microsoft Docs
description: 使用 netsh wlan，從 Windows 裝置將 Wi-Fi 設定匯出成 XML 檔案。 接著再將此檔案匯入 Intune，為執行 Windows 8.1、Windows 10 及 Windows Holographic for Business 的裝置匯入 Wi-Fi 設定檔。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6ce5cdd9509ed3407491714ccfa853613eb43973
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321130"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>在 Intune 中，為 Windows 裝置匯入 Wi-Fi 設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

對於執行 Windows 的裝置，您可以匯入先前匯出到檔案的 Wi-Fi 設定檔。 **對於 Windows 10 及更新版本的裝置，您可以直接在 Intune 中[建立 Wi-Fi 設定檔](wi-fi-settings-windows.md)**。

適用於：  
- Windows 8.1 及更新版本
- Windows 10 及更新版本
- Windows 10 Desktop 或行動裝置版
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>從 Windows 裝置匯出 Wi-Fi 設定

在 Windows 中，您可以使用 **netsh wlan**，將現有的 Wi-Fi 設定檔匯出成 Intune 能夠讀取的 XML 檔案。 必須以純文字格式匯出金鑰，才能順利使用設定檔。

在已安裝必要 WiFi 設定檔的 Windows 電腦上，請使用下列步驟：

1. 為匯出 W-Fi 設定檔建立本機資料夾，例如 **c:\WiFi**。
2. 以系統管理員身分開啟命令提示字元。
3. 執行 `netsh wlan show profiles` 命令，並記下您想要匯出設定檔的名稱。 在此範例中，設定檔名稱是 **WiFiName**。
4. 執行 `netsh wlan export profile name="ProfileName" folder=c:\Wifi` 命令。 這會在目標資料夾中建立名為 **Wi-Fi-WiFiName.xml** 的 Wi-Fi 設定檔。

## <a name="import-the-wi-fi-settings-into-intune"></a>將 Wi-Fi 設定匯入 Intune

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
4. 輸入裝置限制設定檔的 [名稱] 和 [描述]。

    > [!IMPORTANT]
    > - 名稱**必須**與 Wi-Fi 設定檔 XML 中的名稱屬性相同。 否則，就會發生失敗。
    > - 如果您要匯出包含預先共用金鑰的 Wi-Fi 設定檔，就**必須**將 `key=clear` 新增至命令中。 例如，輸入：`netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - 搭配 Windows 10 使用預先共用金鑰會導致在 Intune 中出現補救錯誤。 發生這種情況時，系統會將 Wi-Fi 設定檔適當地指派給裝置，而該設定檔將如預期般運作。
    > - 如果您要匯出包含預先共用金鑰的 Wi-Fi 設定檔，請確定該檔案受到保護。 該金鑰會採用存文字格式，因此您需負責保護該金鑰。

5. 在 [平台] 中，選取 [Windows 8.1 及更新版本]。
6. 在 [設定檔類型] 中，選取 [Wi-Fi 匯入]。
7. 進行以下設定：
  - **連線名稱**：輸入 Wi-Fi 連線的名稱。 當使用者瀏覽可用的 Wi-Fi 網路時，會看到此名稱。
  - **設定檔 XML**：選取 [瀏覽] 按鈕以選取 XML 檔案，其中包含了您要匯入至 Intune 的 Wi-Fi 設定檔。
  - **檔案內容**：顯示所選組態設定檔的 XML 程式碼。
8. 完成時，選擇 [確定]，然後**建立**設定檔。

設定檔隨即建立，並列在設定檔清單中。
