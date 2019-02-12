---
title: 在 Microsoft Intune 中建立裝置的 Wi-Fi 設定檔 - Azure | Microsoft Docs
description: 請查看在 Microsoft Intune 中建立 Wi-Fi 裝置組態設定檔的步驟。 建立 Android、 Android 企業、Android kiosk、iOS、macOS、Windows 10 及更新版本，以及 Windows Holographic for Business 適用的設定檔。 您可以使用這些設定檔建立 WiFi 連線以使用憑證、選擇 EAP 類型、選取驗證方法、啟用 Proxy，以及執行更多作業。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c780f68d3c332cec899250ea4a0ee85745247b37
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842434"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>在 Microsoft Intune 中新增 Wi-Fi 設定並在您的裝置上使用

Wi-Fi 是許多行動裝置用來存取網路的無線網路。 Microsoft Intune 包含內建的 Wi-Fi 設定，可被部署到貴組織中的使用者和裝置。 這組設定稱為「設定檔」，其可被指派給不同的使用者和群組。 指派之後，您的使用者即可在無須自行設定的情況下存取貴組織的 Wi-Fi 網路。

例如，您安裝了名為 Contoso Wi-Fi 的新 Wi-Fi 網路。 然後您要將所有 iOS 裝置都設定為連線到此網路。 程序如下︰

1. 建立包含可連線到 Contoso Wi-Fi 無線網路之設定的 Wi-Fi 設定檔。
2. 將設定檔指派給包含所有 iOS 裝置使用者的群組。
3. 使用者即可在其裝置上的無線網路清單中找到此新的 Contoso Wi-Fi 網路。 然後他們可以使用您選擇的驗證方法連線到網路。

本文列出建立 Wi-Fi 設定檔的步驟。 它也包含說明每個平台之不同設定的連結。

## <a name="supported-device-platforms"></a>支援的裝置平台

Wi-Fi 設定檔支援下列裝置平台：

- Android 4 及更新版本
- Android 企業與 kiosk
- iOS 8.0 和更新版本
- macOS (Mac OS X 10.11 及更新版本)
- Windows 10 和更新版本、Windows 10 行動裝置版，和 Windows Holographic for Business

> [!NOTE]
> 對於執行 Windows 8.1 的裝置，可以匯入先前從其他裝置所匯出的 Wi-Fi 設定。

## <a name="create-a-device-profile"></a>建立裝置設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務] > 篩選 [Intune]，然後選取 [Microsoft Intune]。 
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入 Wi-Fi 設定檔的 [名稱] 和 [描述]。
4. 在 [平台] 下拉式清單中，選取要套用 Wi-Fi 設定的裝置平台。 選項包括：

    - **Android**
    - **Android 企業**
    - **iOS**
    - **macOS**
    - **Windows 8.1 及更新版本**
    - **Windows 10 及更新版本**

5. 在 [設定檔類型] 中，選擇 [Wi-Fi]。

    - 針對執行為 kiosk 的 **Android 企業**裝置，您可以選擇 [僅限裝置擁有者] > [Wi-Fi]。
    - 針對 **Windows 8.1 和更新版本**，您可以選擇 [Wi-Fi 匯入]。 此選項可讓您以先前從不同裝置所匯出的 XML 檔案方式匯入 Wi-Fi 設定。

6. 每個平台的部分 Wi-Fi 設定會不一樣。 若要查看特定平台的設定，請選擇：

    - [Android](wi-fi-settings-android.md)
    - [Android 企業與 kiosk](wi-fi-settings-android-enterprise.md)
    - [iOS](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 及更新版本](wi-fi-settings-windows.md)
    - [Windows 8.1 和更新版本](wi-fi-settings-import-windows-8-1.md)，包括 Windows Holographic for Business

    大部分平台都有 [基本] 和 [企業] 設定。 **基本** 包含像網路名稱和 SSID 這樣的功能。 **企業**可讓您提供更進階的資訊，像是可延伸的驗證通訊協定 (EAP)。

7. 完成新增您的 Wi-Fi 設定時，請選取 [建立設定檔] > [建立] 以新增組態設定檔。 此時會建立設定檔，並顯示在設定檔清單 ([裝置設定] > [設定檔]) 中。

## <a name="next-steps"></a>後續步驟

設定檔已建立，但它不會執行任何動作。 接者，請[指派此設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
