---
title: 在 Microsoft Intune - Azure 中建立裝置設定檔 | Microsoft Docs
description: 在 Microsoft Intune 中新增或設定裝置設定檔 (包括選取平台類型) 並在 Azure 入口網站中設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3d46960e6ea7e2ae9bed6c0016ddc309bd15f572
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>在 Microsoft Intune 中建立裝置設定檔

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>建立設定檔
1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，並搜尋 **Microsoft Intune**。

2. 在 **Microsoft Intune** 中，選取 [裝置設定]，然後選取 [設定檔]。 然後選取 [建立設定檔]。

3. 輸入下列內容：

   - **名稱**：為新的設定檔輸入描述性名稱。
   - **描述**：輸入設定檔的描述。 (這是選用項目，但建議使用。)
   - **平台**：選取平台類型：  

       - **Android**
       - **Android for Work**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 及更新版本**
       - **Windows 10 及更新版本**

   - **設定檔類型**：選取您想要建立的類型。 清單取決於您選擇的平台。
   - **設定**：下列主題描述每個設定檔類型的設定︰

       -  [裝置功能設定](device-features-configure.md)
       -  [裝置限制設定](device-restrictions-configure.md)
       -  [電子郵件設定](email-settings-configure.md)
       -  [VPN 設定](vpn-settings-configure.md)
       -  [Wi-Fi 設定](wi-fi-settings-configure.md)
       -  [Windows 10 版本升級設定](edition-upgrade-configure-windows-10.md)
       -  [憑證設定](certificates-configure.md)
       -  [Windows 資訊保護設定](windows-information-protection-configure.md)
       -  [教育設定](education-settings-configure.md)
       -  [自訂設定](custom-settings-configure.md)

     ![建立設定檔的螢幕擷取畫面](./media/create-device-profile.png)

4. 完成時選取 [建立]。

會建立設定檔，而且會出現在清單中。


## <a name="next-steps"></a>接下來的步驟
若要指派裝置設定檔，請參閱 [How to assign device profiles with Microsoft Intune](device-profile-assign.md) (如何以 Microsoft Intune 指派裝置設定檔)。
