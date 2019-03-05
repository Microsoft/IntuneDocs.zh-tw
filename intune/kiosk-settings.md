---
title: Microsoft Intune 中適用於 Windows 和全像攝影版裝置的 Kiosk 設定 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，將您的 Windows 10 (和更新版本) 與 Windows Holographic for Business 裝置設定為單一應用程式和多應用程式 Kiosk、自訂 [開始] 功能表、新增應用程式、顯示工作列，以及設定網頁瀏覽器。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5cab385b55022139b79ca4a749aba0fbe9e5ef3a
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57236784"
---
# <a name="windows-10-and-windows-holographic-for-business-device-settings-to-run-as-a-dedicated-kiosk-using-intune"></a>使用 Intune 以專用 Kiosk 執行的 Windows 10 和 Windows Holographic for Business 裝置設定

在 Windows 10 裝置上，使用 Intune 執行裝置作為 kiosk，有時也稱為專用裝置。 Kiosk 模式中的裝置可以執行一或多個應用程式。 您可以顯示和自訂 [開始] 功能表、新增不同的應用程式 (包括 Win32 應用程式)、將特定首頁新增至網頁瀏覽器，以及執行更多作業。 

此功能適用於執行下列版本的裝置：

- Windows 10 及更新版本
- Windows Holographic for Business

Intune 針對每部裝置支援一個 kiosk 設定檔。 如果您需要在單一裝置上有多個 kiosk 設定檔，則可以使用[自訂 OMA-URI](custom-settings-windows-10.md)。

Intune 會使用「組態設定檔」，依據貴組織的需求來建立和自訂這些設定。 當您於設定檔中新增這些功能之後，請將這些設定部署至貴組織中的群組。

本文示範如何建立裝置組態設定檔。 如需所有設定的清單及其用途，請參閱 [Windows 10 Kiosk 設定](kiosk-settings-windows.md)和 [Windows Holographic for Business Kiosk 設定](kiosk-settings-holographic.md)。

## <a name="create-the-profile"></a>建立設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務] > 篩選 [Intune] > 選取 [Microsoft Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入下列內容：

   - **名稱**：為新的設定檔輸入描述性名稱。
   - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
   - **平台**：選取 [Windows 10 及更新版本]
   - **設定檔類型**：選取 [Kiosk]

4. 在 [設定] 中，選取 **kiosk 模式**。 [Kiosk 模式] 可識別原則支援的 Kiosk 模式類型。 這些選項包括：

    - **未設定** (預設)：不啟用 kiosk 模式的原則。
    - **單一應用程式、全螢幕 kiosk**：裝置以單一使用者帳戶執行，並將其鎖定到單一市集應用程式。 因此當使用者登入時，會啟動特定的應用程式。 此模式也會限制使用者開啟新的應用程式或變更執行中的應用程式。
    - **多應用程式 kiosk**：裝置藉由使用應用程式使用者模型識別碼 (AUMID) 來執行多個市集應用程式、Win32 應用程式或現成的 Windows 應用程式。 只有您新增的應用程式才可在裝置上使用。

        多應用程式 Kiosk (或固定用途裝置) 的優點是讓使用者只存取所需的應用程式，來為他們提供一個簡單明瞭的體驗。 此外，還可從其檢視中移除不需要的應用程式。

    如需所有設定的清單及其用途，請參閱：
      - [Windows 10 Kiosk 設定](kiosk-settings-windows.md)
      - [Windows Holographic for Business Kiosk 設定](kiosk-settings-holographic.md)

5. 當您完成時，請選取 [確定] > [建立] 儲存變更。 

設定檔隨即建立，並顯示在設定檔清單中。 接下來，請[指派](device-profile-assign.md)此設定檔。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

您可以針對執行下列平台的裝置建立 kiosk 設定檔：
- [Android](device-restrictions-android.md#kiosk)
- [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)
- [Windows 10 及更新版本](kiosk-settings-windows.md)
- [Windows Holographic for Business](kiosk-settings-holographic.md)
