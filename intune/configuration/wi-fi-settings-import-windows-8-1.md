---
title: 在 Microsoft Intune 中為 Windows 裝置匯入 Wi-Fi 設定 - Azure | Microsoft Docs
description: 使用 netsh wlan，從 Windows 裝置將 Wi-Fi 設定匯出成 XML 檔案。 接著再將此檔案匯入 Intune，為執行 Windows 8.1、Windows 10 及 Windows Holographic for Business 的裝置匯入 Wi-Fi 設定檔。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/18/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40569af35a812074cc62546e3f85929416202b3b
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506421"
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

1. 為匯出 W-Fi 設定檔建立本機資料夾，例如 **c:\WiFi**。
2. 以系統管理員身分開啟命令提示字元。
3. 執行 `netsh wlan show profiles` 命令，並記下您想要匯出設定檔的名稱。 在此範例中，設定檔名稱是 **WiFiName**。
4. 執行 `netsh wlan export profile name="ProfileName" folder=c:\Wifi` 命令。 此命令會在目標資料夾中建立名為 **Wi-Fi-WiFiName.xml** 的 Wi-Fi 設定檔。

## <a name="import-the-wi-fi-settings-into-intune"></a>將 Wi-Fi 設定匯入 Intune

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
3. 輸入裝置限制設定檔的 [名稱]  和 [描述]  。

    > [!IMPORTANT]
    > - 名稱**必須**與 Wi-Fi 設定檔 XML 中的名稱屬性相同。 否則，就會發生失敗。
    > - 如果您要匯出包含預先共用金鑰的 Wi-Fi 設定檔，就**必須**將 `key=clear` 新增至命令中。 例如，輸入：`netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - 搭配 Windows 10 使用預先共用金鑰會導致在 Intune 中出現補救錯誤。 發生這種情況時，系統會將 Wi-Fi 設定檔適當地指派給裝置，而該設定檔將如預期般運作。
    > - 如果您要匯出包含預先共用金鑰的 Wi-Fi 設定檔，請確定該檔案受到保護。 該金鑰會採用存文字格式，因此您需負責保護該金鑰。

4. 在 [平台]  中，選取 [Windows 8.1 及更新版本]  。
5. 在 [設定檔類型]  中，選取 [Wi-Fi 匯入]  。
6. 進行以下設定：
    - **連線名稱**：輸入 Wi-Fi 連線的名稱。 當使用者瀏覽可用的 Wi-Fi 網路時，會看到此名稱。
    - **設定檔 XML**：選取瀏覽按鈕，然後選擇包含您想匯入 之 Wi-Fi 設定檔設定的 XML 檔案。
    - **檔案內容**：顯示所選組態設定檔的 XML 程式碼。
7. 當您完成時，請選取 [確定]   > [建立]  儲存變更。 設定檔隨即建立，並顯示在設定檔清單中。

## <a name="next-steps"></a>後續步驟

設定檔已建立，但它不會執行任何動作。 接下來，請[指派此設定檔](device-profile-assign.md)。

## <a name="more-resources"></a>其他資源

[Wi-Fi 設定概觀](wi-fi-settings-configure.md)，包括其他可用平台。
