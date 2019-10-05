---
title: Windows Phone 8.1 的 Microsoft Intune 裝置限制設定
titleSuffix: ''
description: 了解執行 Windows Phone 8.1 的裝置上可用以控制裝置設定與功能的 Intune 設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: eb5ffa2fe17c3272cb98c670fa42e69f189e7004
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734735"
---
# <a name="microsoft-intune-windows-phone-81-device-restriction-settings"></a>Microsoft Intune Windows Phone 8.1 裝置限制設定

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文將說明所有的 Microsoft Intune 裝置限制設定，讓您可以為執行 Windows Phone 8.1 的裝置進行設定。


## <a name="general"></a>一般

- **相機** - 啟用或封鎖裝置的相機。
- **複製並貼上** - 可以在裝置上使用複製及貼上功能。
- **抽取式存放裝置** - 允許裝置使用如 SD 記憶卡等抽取式存放裝置。
- **地理位置** - 讓裝置可利用位置資訊。
- **Microsoft 帳戶** - 啟用或封鎖使用者將 Microsoft 帳戶連結到裝置。
- **螢幕擷取** - 讓使用者可將螢幕的內容擷取為影像檔案。
- **診斷資料提交** - 讓裝置可將診斷資訊提交到 Microsoft。
- **自訂電子郵件帳戶同步** - 讓裝置可連線到非 Microsoft 的電子郵件帳戶。

## <a name="password"></a>密碼

- **密碼** - 需要使用者輸入密碼才可存取該裝置。
  - **必要的密碼類型** - 指定必要密碼的類型，例如只可為英數字元或數字等等。
  - **密碼長度下限** - 指定密碼所需的字元數下限。
  - **簡單密碼** - 指定是否能使用 ’0000’ 和 ‘1234’ 等簡單密碼。
  - **登入失敗幾次後即抹除裝置** - 指定抹除裝置前可輸入錯誤密碼的次數。
  - **沒有活動最久幾分鐘後鎖定螢幕** - 指定裝置必須處於閒置狀態多久的時間，才會自動鎖住螢幕。
  - **密碼到期 (天數)** - 指定多少天後必須變更裝置密碼。
  - **避免重複使用以前用過的密碼** - 指定可以記住多少個先前使用過的密碼。
- **加密** - 需要加密受支援行動裝置上的資料。

## <a name="app-store"></a>App Store

- **App Store** - 讓使用者可從裝置連接到 App Store。

## <a name="restricted-apps"></a>受限應用程式

您可以在受限制應用程式清單中，設定下列清單之一︰

**封鎖的應用程式**清單 - 列出不允許使用者安裝與執行的應用程式 (並非由 Intune 管理)。
**允許的應用程式**清單 - 列出允許使用者安裝的應用程式。 自動允許 Intune 所管理的應用程式。

若要設定清單，請按一下 [新增]  ，然後在應用程式市集中，指定您所選的名稱 (也可指定選用的應用程式發行者) 以及應用程式的 URL。

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>如何在市集中指定應用程式的 URL

若要在允許和封鎖的應用程式清單中指定應用程式 URL，請使用下列格式：

從 [[Windows Phone 市集]](https://www.microsoft.com/store/apps/windows-phone) 頁面中，搜尋您想要使用的應用程式。

開啟應用程式的頁面，然後將 URL 複製到剪貼簿。 您現在可以在允許或封鎖的應用程式清單中使用這個 URL。

範例：在市集中搜尋 Skype 應用程式。 您使用的 URL 是 `http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51`。



### <a name="additional-options"></a>其他選項

您也可以按一下 [匯入]  填入格式如一下的 csv 檔案清單：<*應用程式 URL*>，<*應用程式名稱*>，<*應用程式發行者*>，或按一下 [匯出]  ，建立 csv 檔案，其中包含格式相同的受限應用程式清單內容。


## <a name="browser"></a>瀏覽器

- **網頁瀏覽器** - 啟用或封鎖裝置的內建網頁瀏覽器。

## <a name="cellular-and-connectivity"></a>行動數據與連線

- **Wi-Fi** - 啟用或停用裝置的 Wi-Fi 功能。
- **Wi-Fi 網際網路共用功能** - 可以使用裝置的 Wi-Fi 網際網路共用功能。
- **自動連線至 Wi-Fi 熱點** - 讓裝置可自動連線到免費 Wi-Fi 熱點，並自動接受任何使用條款。
- **Wi-Fi 熱點報表** - 傳送 Wi-Fi 連線的相關資訊，以協助使用者找出附近的連線。
- **NFC** - 在支援近距離無線通訊之裝置上，啟用或停用使用近距離無線通訊的作業。
- **藍牙** - 啟用或停用裝置的藍牙功能。
