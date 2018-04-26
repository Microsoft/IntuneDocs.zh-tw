---
title: 允許/封鎖 Samsung Knox 之應用程式的 Microsoft Intune 原則
titlesuffix: ''
description: 建立自訂設定檔以允許及封鎖 Samsung Knox Standard 裝置的應用程式。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 28aab246778610691ee78c447fd08f2a923ec6c0
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>在 Microsoft Intune 中使用自訂原則來允許和封鎖 Samsung Knox Standard 裝置的應用程式 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用本文中的程序，可建立 Microsoft Intune 的自訂原則，該原則會建立下列其中一個項目︰

- 無法在裝置上執行的應用程式清單。 這份清單中的應用程式會被封鎖而無法執行，即使它們在套用原則時已安裝也一樣。
- 裝置使用者可從 Google Play 市集安裝的應用程式清單。 只可以安裝您列出的應用程式。 無法從市集安裝其他應用程式。

只有執行 Samsung Knox Standard 的裝置可使用這些設定。

## <a name="create-an-allowed-or-blocked-app-list"></a>建立已允許或已封鎖的應用程式清單

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [裝置設定]。
2. 在 [裝置設定] 窗格中，選擇 [管理] >  [設定檔]。
2. 在設定檔清單窗格中，選擇 [建立設定檔]。
3. 在 [建立設定檔] 窗格中，輸入此裝置設定檔的 [名稱] 以及選用的 [描述]。
2. 將 [平台] 選為 [Android]，且將 [設定檔類型] 選為 [自訂]。
3. 按一下 [設定]。
3. 在 [Custom OMA-URI Settings] (自訂 OMA-URI 設定) 窗格中，選擇 [新增]。
4. 在 [Add or Edit OMA-URI Setting] (新增或編輯 OMA-URI 設定) 對話方塊中，指定下列設定：

   無法在裝置上執行的應用程式清單：

   - **名稱** - 輸入 **PreventStartPackages**。
   - **描述** - 輸入選用描述，例如「封鎖而無法執行的應用程式清單」。
   -    **資料類型** - 從下拉式清單中選擇 [字串]。
   -    **OMA URI** - 輸入 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
   -    **值** - 輸入您允許的應用程式套件名稱之清單。 您可以使用 **; : ,** 或 **|** 作為分隔符號。 (範例︰package1;package2;)

   針對使用者在排除所有其他應用程式時，可從 Google Play 商店安裝的應用程式清單：
   - **名稱** - 輸入 **AllowInstallPackages**。
   - **描述** - 輸入選用描述，例如「使用者可從 Google Play 安裝的應用程式清單」。
   - **資料類型** - 從下拉式清單中選擇 [字串]。
   - **OMA URI** - 輸入 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
   - **值** - 輸入您允許的應用程式套件名稱之清單。 您可以使用 **; : ,** 或 **|** 作為分隔符號。 (範例︰package1;package2;)

4. 按一下 [確定]，然後在 [建立設定檔] 窗格中，選擇 [建立]。

>[!TIP]
> 您可以藉由瀏覽至 Google Play 商店上的應用程式，找到應用程式的套件識別碼。 套件識別碼被包含在應用程式頁面的 URL 中。 例如，Microsoft Word 應用程式的套件識別碼為 **com.microsoft.office.word**。

下一次，登入每個目標裝置後，就會套用應用程式設定。


<!---## Assign the custom profile--->
