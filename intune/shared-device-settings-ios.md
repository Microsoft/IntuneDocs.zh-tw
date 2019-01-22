---
title: 使用 Microsoft Intune 自訂 iOS 裝置上的鎖定畫面 - Azure | Microsoft Docs
titlesuffix: ''
description: 了解您可以透過適用於 iOS 的共用裝置組態設定，用來在 iOS 裝置鎖定畫面上顯示資訊的 Microsoft Intune 設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9f4d75d795421c761398f349c324b498fd21ca01
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203071"
---
# <a name="add-custom-messages-to-lock-screen-and-login-window-on-ios-devices-using-microsoft-intune"></a>使用 Microsoft Intune 將自訂訊息新增至 iOS 裝置上的鎖定畫面和登入視窗

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文說明可用來在 iOS 裝置鎖定畫面和登入視窗上顯示資訊的 Microsoft Intune 設定。 

您可以使用這些設定，在登入視窗和鎖定畫面上顯示自訂訊息或文字。 例如，您可以輸入「若遺失，請送回...」訊息和資產標籤資訊。

這些設定支援執行 iOS 9.3 及更新版本的受監督裝置。

## <a name="create-the-profile"></a>建立設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務] > 篩選 [Intune] > 選取 [Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入設定檔的**名稱**和**描述**。
4. 在 [平台] 中，選取 [iOS]。 在 [設定檔類型] 中，選取 [裝置功能]。
5. 在 [設定] 中，選取 [鎖定畫面訊息 (僅限受監督)]。 進行以下設定：

    - **資產標籤資訊**：輸入裝置資產標籤的相關資訊。 例如，輸入 `123xyz`。

        您輸入的文字會顯示在裝置登入視窗與鎖定畫面上。

    - **鎖定畫面註腳**：輸入當裝置遺失或遭竊時，可能有助於取回裝置的備註。 您可以在此欄位中輸入任何所需的文字。 例如，輸入類似 `If found, call Contoso at ...` 的內容。

    裝置權杖也可用來在這些欄位中新增裝置特定資訊。 例如，若要顯示序號，請輸入 `Serial Number: {{serialnumber}}`。 在鎖定畫面上，此文字顯示類似於 `Serial Number 123456789ABC`。 輸入變數時，請務必使用大括弧 `{{ }}`。 [應用程式設定權杖](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)包含可以使用的變數清單。 您也可以使用 `deviceName` 或任何其他的裝置特定值。

6. 完成後，請選取 [確定] > [確定] > [建立]。 您的設定檔會顯示在清單中。

## <a name="next-steps"></a>後續步驟

設定檔已建立，但還不會執行任何動作。 接下來，[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
