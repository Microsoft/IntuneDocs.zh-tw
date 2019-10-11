---
title: 在 Microsoft Intune 中新增或設定教育設定 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，於 Windows 10 和更新版本之裝置上的裝置組態設定檔中使用 [進行測驗] 應用程式。 使用 [教育] 設定建立組態設定檔，然後輸入測驗應用程式 URL、選擇使用者登入方式、在測驗期間監視畫面，以及在測驗期間允許或防止文字建議。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3fc42193b461b8a0364e4ef2a2c34fe3e446ada3
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724005"
---
# <a name="use-the-take-a-test-app-on-windows-10-devices-in-microsoft-intune"></a>在 Microsoft Intune 中，於 Windows 10 裝置上使用 [進行測驗] 應用程式

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 中的教育設定檔是專為學生在裝置上進行測驗或考試而設計的。 此功能包括 [進行測驗]  應用程式，以及新增測驗 URL，選擇使用者登入測驗之方式的設定等。 此功能支援下列平台：

- Windows 10 及更新版本

當使用者登入時，[進行測驗] 應用程式會自動開啟您所輸入的測驗。 在測驗過程中，裝置上無法執行任何其他應用程式。 [在 Windows 10 中進行測驗](https://docs.microsoft.com/education/windows/take-tests-in-windows-10) \(部分機器翻譯\) 提供了有關 [進行測驗] 應用程式的更多詳細資料。

本文列出在 Microsoft Intune 中建立裝置組態設定檔的步驟。 它還包括用於閱讀和了解 Windows 10 裝置可用的教育設定的資訊。

## <a name="create-a-device-profile"></a>建立裝置設定檔

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
3. 輸入下列內容：

    - **名稱**：為新的設定檔輸入描述性名稱。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選擇 [Windows 10 及更新版本]  。
    - **設定檔**：選擇**教育設定檔**。

4. 輸入您要設定的設定：

    - [Windows 10 及更新版本](education-settings-windows.md)

5. 選取 [確定]   > [建立]  儲存您的變更。

輸入您的設定並建立設定檔之後，您的設定檔會顯示在 [設定檔] 清單中。 接下來，請[將此設定檔指派給一些群組](device-profile-assign.md)。

## <a name="next-steps"></a>後續步驟

查看 [Windows 10 教育設定](education-settings-windows.md)的清單及其描述。

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
