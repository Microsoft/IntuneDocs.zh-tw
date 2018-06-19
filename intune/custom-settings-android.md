---
title: 在 Microsoft Intune 中新增 Android 裝置的自訂設定 | Microsoft Docs
description: 在 Microsoft Intune 中為 Android 裝置新增或建立自訂設定檔，以使用預先共用金鑰、建立 WiFi 設定檔、建立個別應用程式 VPN 設定檔，或允許、禁止 Samsung Knox Standard 裝置應用程式
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0195e138b59fae019fa2bc02aadf211257a65cac
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31022045"
---
# <a name="custom-settings-for-android-devices---intune"></a>Android 裝置的自訂設定 - Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

自訂設定檔會使用開放行動聯盟的統一資源識別項 (OMA URI) 設定來進行 Android 裝置上的各種功能設定。 行動裝置製造商通常會使用這些設定來控制裝置上的功能。

使用自訂設定檔，您便可以設定及指派下列 Android 設定。 Intune 原則並未內建這些設定：

- [使用預先共用的金鑰建立 Wi-Fi 設定檔](/intune/wi-fi-profile-shared-key)
- [建立個別應用程式 VPN 設定檔](/intune/android-pulse-secure-per-app-vpn)
- [允許或禁止應用程式在 Samsung Know Standard 裝置上執行](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> 這種設定檔類型只能進行列出的設定。 Android 裝置不會公開您可設定的完整 OMA-URI 設定清單。 如果您希望能夠使用更多設定，請在 [Intune Uservoice 網站](https://microsoftintune.uservoice.com/forums/291681-ideas) (Intune Uservoice 網站) 票選更多設定。

## <a name="custom-profile-settings-for-android-devices"></a>Android 裝置的自訂設定檔設定

1. 登入 [Azure 入口網站](https://portal.azure.com)。 
2. 選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 使用 Android 平台建立自訂設定檔。 [在 Microsoft Intune 中設定自訂裝置設定](custom-settings-configure.md)列出了步驟。
4. 在 [自訂 OMA-URI 設定]中，選取 [新增]，然後選取 [新增資料列]。
5. 輸入下列內容：

   - **名稱** - 為 OMA-URI 設定輸入唯一名稱，使其易於找到。
   - **描述** - 輸入描述來概述設定和其他重要的詳細資料。
   - **資料類型** - 輸入您要用於這個 OMA-URI 設定的資料類型。 選擇 [字串]、[字串 (XML)]、[日期和時間]、[整數]、[浮點數] 或 [布林值]。
   - **OMA-URI** - 輸入您想要的 OMA-URI。
   - **值** - 輸入要與您所輸入之 OMA-URI 相關聯的值。

6. 按一下 [確定] 以儲存您的變更。 視需要繼續新增更多設定。

## <a name="next-steps"></a>接下來的步驟

當您完成設定時，設定檔會隨即建立，並出現在清單上。 若要將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。
