---
title: 允許/封鎖 Samsung Knox 之應用程式的 Microsoft Intune 原則
titleSuffix: ''
description: 建立自訂設定檔以允許及封鎖 Samsung Knox Standard 裝置的應用程式。
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
ms.openlocfilehash: 4b83a0339d87375502159467af323fceae5eb6e2
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207072"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>在 Microsoft Intune 中使用自訂原則來允許和封鎖 Samsung Knox Standard 裝置的應用程式 

使用本文中的程序，可建立 Microsoft Intune 的自訂原則，該原則會建立下列其中一個項目︰

- 無法在裝置上執行的應用程式清單。 這份清單中的應用程式會被封鎖而無法執行，即使它們在套用原則時已安裝也一樣。
- 允許裝置使用者從 Google Play 商店安裝的應用程式清單。 只可以安裝您列出的應用程式。 無法從市集安裝其他應用程式。

只有執行 Samsung Knox Standard 的裝置可使用這些設定。

## <a name="create-an-allowed-or-blocked-app-list"></a>建立已允許或已封鎖的應用程式清單

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
3. 輸入下列設定：

    - **名稱**：為設定檔輸入描述性名稱。 命名您的設定檔，以方便之後能輕鬆識別。 例如，良好的設定檔名稱是**Windows phone 自訂設定檔**。
    - **描述**：輸入描述來概述設定和其他重要的詳細資料。
    - **平台**：選取 [Android]  。
    - **配置檔案類型**：選取 [**自訂**]。

4. 在 [自訂 OMA-URI 設定]  中，選取 [新增]  。 輸入下列設定：

    無法在裝置上執行的應用程式清單：

    - **名稱**：輸入 **PreventStartPackages**。
    - **描述**：輸入描述來概述設定及其他可協助您找到設定檔的相關資訊。 例如，輸入**已封鎖而無法執行的應用程式清單**。
    - **OMA-URI** (區分大小寫)：輸入 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**。
    - **資料類型**：選取 [**字串**]。
    - **值**：輸入您想要允許的應用程式套件名稱清單。 您可以使用 `;`、`:` 或 `|` 作為分隔符號。 例如，輸入 `package1;package2;`。

   針對使用者在排除所有其他應用程式時，可從 Google Play 商店安裝的應用程式清單：

    - **名稱**：輸入 **AllowInstallPackages**。
    - **描述**：輸入描述來概述設定及其他可協助您找到設定檔的相關資訊。 例如，輸入**使用者可以從 Google Play 安裝的應用程式清單**。
    - **OMA-URI** (區分大小寫)：輸入 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**。
    - **資料類型**：選取 [**字串**]。
    - **值**：輸入您想要允許的應用程式套件名稱清單。 您可以使用 `;`、`:` 或 `|` 作為分隔符號。 例如，輸入 `package1;package2;`。

5. 按一下 [確定]  以儲存您的變更。
6. 完成時，選取 [確定]   > [建立]  以建立 Intune 設定檔。 完成時，您的設定檔會顯示在 [裝置 - 設定檔]  清單中。

>[!TIP]
> 您可以藉由瀏覽至 Google Play 商店上的應用程式，找到應用程式的套件識別碼。 套件識別碼被包含在應用程式頁面的 URL 中。 例如，Microsoft Word 應用程式的套件識別碼為 **com.microsoft.office.word**。

下一次當每個目標裝置簽入時，就會套用應用程式設定。

## <a name="next-steps"></a>後續步驟

設定檔已建立，但還不會執行任何動作。 接下來，[指派設定檔](../device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
