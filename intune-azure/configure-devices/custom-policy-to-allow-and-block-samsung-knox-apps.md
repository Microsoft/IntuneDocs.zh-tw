---
title: "Samsung KNOX 的 Intune 原則允許/封鎖應用程式"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版：建立自訂定檔可允許及封鎖 Samsung KNOX Standard 裝置的應用程式。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: ca4f1adc5704ecd66d2af7823f95ca63ec20469e
ms.openlocfilehash: a47ea4c8d3027cb34fd8ecd8324fac52c9846a77
ms.lasthandoff: 03/17/2017



---
# <a name="use-custom-policies-to-allow-and-block-apps-for-samsung-knox-standard-devices-in-microsoft-intune"></a>使用自訂原則來允許和封鎖 Microsoft Intune 中 Samsung KNOX Standard 裝置的應用程式
[!INCLUDE[azure_preview](../includes/azure_preview.md)] 使用此主題中的程序，可建立 Microsoft Intune 的自訂原則，該原則會建立下列其中一個項目︰

- 無法在裝置上執行的應用程式清單。 這份清單中的應用程式會被封鎖而無法執行，即使它們在套用原則時已安裝也一樣。
- 裝置使用者可從 Google Play 市集安裝的應用程式清單。 只可以安裝您列出的應用程式。 無法從市集安裝其他應用程式。

只有執行 Samsung KNOX Standard 的裝置可使用這些設定。

## <a name="create-an-allowed-or-blocked-app-list"></a>建立已允許或已封鎖的應用程式清單

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置設定]。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
2. 在設定檔刀鋒視窗清單中，選擇 [建立設定檔]。
3. 在 [建立設定檔] 刀鋒視窗中，為此裝置設定檔輸入 [名稱] 以及選用 [描述]。
2. 將 [平台類型] 選為 **Android**，且將設定檔類型選為 [自訂]。
3. 按一下 [設定]。
3. 在 [自訂 OMA URI 設定] 刀鋒視窗中，選擇 [新增]。
4. 在 [新增或編輯 OMA-URI 設定] 對話方塊中，指定下列資訊：

### <a name="for-a-list-of-apps-that-are-blocked-from-running-on-the-device"></a>無法在裝置上執行的應用程式清單：

- **名稱** - 輸入 **PreventStartPackages**。
- **描述** - 輸入選用描述，例如「封鎖而無法執行的應用程式清單」。
-     **資料類型** - 從下拉式清單中選擇 [字串]。
-     **OMA URI** - 輸入 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
-     **值** - 輸入您允許的應用程式套件名稱之清單。 您可以使用 **; : ,** 或 **|** 作為分隔符號。 (範例︰package1;package2;)

### <a name="for-a-list-of-apps-that-users-are-allowed-to-install-from-the-google-play-store-while-excluding-all-other-apps"></a>針對使用者在排除所有其他應用程式時，可從 Google Play 商店安裝的應用程式清單：
- **名稱** - 輸入 **AllowInstallPackages**。
- **描述** - 輸入選用描述，例如「使用者可從 Google Play 安裝的應用程式清單」。
- **資料類型** - 從下拉式清單中選擇 [字串]。
- **OMA URI** - 輸入 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
- **值** - 輸入您允許的應用程式套件名稱之清單。 您可以使用 **; : ,** 或 **|** 作為分隔符號。 (範例︰package1;package2;)

4. 按一下 [確定]，然後在 [建立設定檔] 刀鋒視窗中，選擇 [建立]。

>[!TIP]
> 您可以藉由瀏覽至 Google Play 商店上的應用程式，找到應用程式的套件識別碼。 套件識別碼被包含在應用程式頁面的 URL 中。 例如，Microsoft Word 應用程式的套件識別碼為 **com.microsoft.office.word**。

下一次，登入每個目標裝置後，就會套用應用程式設定。


<!---## Assign the custom profile--->

