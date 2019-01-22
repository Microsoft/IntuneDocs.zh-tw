---
title: 在 Microsoft Intune - Azure 中建立裝置設定檔 | Microsoft Docs
description: 在 Microsoft Intune 中新增或設定裝置設定檔 (包括選取平台類型) 並在 Azure 入口網站中設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cb6e3f0a9f62348d55b5dc2284c1007ea7faf088
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203207"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>在 Microsoft Intune 中建立裝置設定檔

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>建立設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務] > 篩選 [Intune] > 選取 [Intune]。

2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。

3. 輸入下列內容：

   - **名稱**：為新的設定檔輸入描述性名稱。
   - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
   - **平台**：選取平台類型：  

       - **Android**
       - **Android 企業**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 及更新版本**
       - **Windows 10 及更新版本**

   - **設定檔類型**：選取您想要建立的類型。 清單取決於您選擇的平台。
   - **設定**：下列文章會描述每個設定檔類型的設定︰

       -  [裝置功能](device-features-configure.md)
       -  [裝置限制](device-restrictions-configure.md)
       -  [端點保護](endpoint-protection-configure.md)
       -  [Identity Protection](identity-protection-configure.md)  
       -  [Kiosk](kiosk-settings.md)
       -  [電子郵件](email-settings-configure.md)
       -  [VPN](vpn-settings-configure.md)
       -  [Wi-Fi](wi-fi-settings-configure.md)
       -  [Windows 10](education-settings-configure.md) 和 [iOS](wi-fi-settings-ios.md) 的教育
       -  [Windows 10 版本升級](edition-upgrade-configure-windows-10.md)
       -  [iOS 更新原則](software-updates-ios.md)
       -  [憑證](certificates-configure.md)
       -  [Windows 資訊保護](windows-information-protection-configure.md)
       -  [自訂](custom-settings-configure.md)

     ![建立設定檔的螢幕擷取畫面](./media/create-device-profile.png)

4. 完成時選取 [建立]。

會建立設定檔，而且會出現在清單中。

## <a name="next-steps"></a>後續步驟
[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
