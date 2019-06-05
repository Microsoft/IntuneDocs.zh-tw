---
title: 在 Microsoft Intune 中設定電子郵件設定 - Azure | Microsoft Docs
titleSuffix: ''
description: 在 Microsoft Intune 中建立電子郵件設定檔，並將此設定檔部署到 Android Enterprise、iOS 和 Windows 裝置。 使用電子郵件設定檔來設定一般電子郵件設定，包括電子郵件伺服器和驗證方法，以連線到您所管理裝置上的公司電子郵件。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6a80ff2ca7c2265da358f57291032f59d47d22dd
ms.sourcegitcommit: 063177c6c365fef3642edd7c455790958469aad9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412351"
---
# <a name="add-email-settings-to-devices-using-intune"></a>使用 Intune 將電子郵件設定新增至裝置

Microsoft Intune 包含不同的電子郵件設定，可部署到您組織中的裝置。 IT 系統管理員會建立具有特定設定的電子郵件設定檔，以連線到郵件伺服器，例如 Office 365 和 Gmail。 終端使用者接著會連線、驗證並同步處理其行動裝置上的組織電子郵件帳戶。 藉由建立及部署電子郵件設定檔，您就能確認多部裝置之間皆有標準的設定。 此外也有助於減少不知道正確電子郵件設定的終端使用者與支援部門連絡的次數。

您可以使用電子郵件設定檔，針對下列裝置設定內建電子郵件設定：

- Android Samsung Knox Standard 4.0 及更新版本
- Android 企業
- iOS 8.0 和更新版本
- Windows Phone 8.1 和更新版本
- Windows 10 桌面版與 Windows 10 行動裝置版

本文示範如何在 Microsoft Intune 中建立電子郵件設定檔。 它也包含不同平台的連結，以取得更具體的設定。

## <a name="create-a-device-profile"></a>建立裝置設定檔

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
3. 輸入電子郵件設定檔的 [名稱]  和 [描述]  。
4. 從下拉式清單中選擇您的 [平台]  。 選項包括：

    - **Android** (僅限 Samsung Android Knox Standard)
    - **Android 企業**
    - **iOS**
    - **Windows Phone 8.1**
    - **Windows 10 及更新版本**

5. 在 [設定檔類型]  下拉式清單中，選擇 [電子郵件]  。
6. 您可以進行的設定可能會因每個平台而有所不同。 如需特定設定，請選擇您的平台：

    - [Android Samsung Knox Standard 設定](email-settings-android.md)
    - [Android 企業設定](email-settings-android-enterprise.md)
    - [iOS 設定](email-settings-ios.md)
    - [Windows Phone 8.1 設定](email-settings-windows-phone-8-1.md)
    - [Windows 10 設定](email-settings-windows-10.md)

輸入您的設定並建立設定檔之後，您的設定檔會顯示在 [設定檔] 清單中。 接下來，請[將此設定檔指派給一些群組](device-profile-assign.md)。

## <a name="remove-an-email-profile"></a>移除電子郵件設定檔

電子郵件設定檔會指派給裝置群組，而不是使用者群組。 您可以透過不同的方式從裝置移除電子郵件設定檔，即使裝置上只有一個電子郵件設定檔也一樣：

- **選項 1**：開啟電子郵件設定檔 ([裝置設定]   > [設定檔]  )，然後選擇 [指派]  。 [包含]  索引標籤顯示獲指派設定檔的群組。 以滑鼠右鍵按一下群組 > [移除]  。 請務必**儲存**您的變更。

- **選項 2**：[抹除或淘汰裝置](devices-wipe.md)。 您可以使用這些動作選擇性或完全移除資料和設定。

## <a name="secure-email-access"></a>安全存取電子郵件

您可以使用下列選項來保護電子郵件設定檔：

- **憑證**：當您建立電子郵件設定檔時，您可以選擇先前在 Intune 中建立的憑證設定檔。 這個憑證稱為識別憑證。 它會針對受信任的憑證設定檔或根憑證進行驗證，以確認使用者的裝置可以連線。 受信任的憑證會指派到可驗證電子郵件連線的電腦。 一般而言，此電腦是原生郵件伺服器。

  如需如何在 Intune 中建立及使用憑證設定檔的詳細資訊，請參閱 [How to configure certificates with](certificates-configure.md) (如何利用 Intune 設定憑證)。

- **使用者名稱和密碼**：終端使用者會藉由輸入使用者名稱和密碼，來向原生郵件伺服器進行驗證。 電子郵件設定檔中沒有密碼。 因此，終端使用者要在連線到電子郵件時輸入密碼。

## <a name="how-intune-handles-existing-email-accounts"></a>Intune 如何處理現有電子郵件帳戶

如果使用者已設定電子郵件帳戶，則會根據平台，以不同方式指派電子郵件設定檔。

- **iOS**：依據主機名稱和電子郵件地址，偵測到重複的現有電子郵件設定檔。 重複的電子郵件設定檔會封鎖 Intune 設定檔的指派。 在此情況下，公司入口網站應用程式會通知使用者其不符合規範，並提示終端使用者手動移除已設定的設定檔。 為協助避免此情況，請指示終端使用者「先」  註冊，然後再安裝電子郵件設定檔，以允許 Intune 設定該設定檔。

- **Windows：** 依據主機名稱和電子郵件地址，偵測到重複的現有電子郵件設定檔。 Intune 會覆寫終端使用者所建立的現有電子郵件設定檔。

- **Android Samsung Knox Standard**：依據電子郵件地址，偵測到重複的現有電子郵件設定檔，且會以 Intune 設定檔覆寫它。 Android 不會使用主機名稱來識別設定檔。 請勿在不同主機上使用相同電子郵件地址來建立多個電子郵件設定檔。 這些設定檔會彼此覆寫。

- **Android 公司設定檔**：Intune 提供兩個 Android 公司電子郵件設定檔：一個用於 Gmail 應用程式，一個用於 Nine Work 應用程式。 這些應用程式都可從 Google Play 商店取得，並在裝置工作設定檔中安裝。 這些應用程式都不會建立重複的設定檔。 兩個應用程式都支援連線到 Exchange。 若要使用電子郵件連線功能，請將其中一個電子郵件應用程式部署到使用者的裝置。 然後建立及部署適當的電子郵件設定檔。 Nine Work 之類的電子郵件應用程式可能不是免費的。 請檢閱應用程式的授權詳細資料，如有任何問題，請連絡應用程式廠商。

## <a name="changes-to-assigned-email-profiles"></a>對指派的電子郵件設定檔進行變更

如果您變更之前指派的電子郵件設定檔，終端使用者可能會看到要求核准其電子郵件設定重新設定的訊息。

## <a name="next-steps"></a>後續步驟

一旦設定檔建立完成，它還不會執行任何動作。 接下來，[將設定檔指派給一些裝置](device-profile-assign.md)。
