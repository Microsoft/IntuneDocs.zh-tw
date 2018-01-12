---
title: "如何設定 Intune 電子郵件設定"
titleSuffix: Azure portal
description: "了解如何設定 Intune，以建立您管理的裝置上與公司電子郵件的連線。"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 484bd9b0-fbf1-4f4f-940c-6b12fa07e228
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f697b575a5cdc1fa4009d08a14452508eacb8de1
ms.sourcegitcommit: 5004b9564915712b41860df20324f39fac3dc27d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-configure-email-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中設定電子郵件設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

電子郵件設定檔可用來為您管理的裝置設定連線所需的設定，並與公司電子郵件同步。 如此有助於確保所有裝置之間皆有標準的設定，且有助於減少不知道正確的電子郵件設定的使用者，致電支援電話。

內建的郵件用戶端支援大部分的平台。 目前不支援大部分的協力廠商電子郵件應用程式。

您可以使用電子郵件設定檔，在下列裝置類型上設定原生電子郵件用戶端：

- Android Samsung Knox Standard 4.0 及更新版本
- Android for Work
- iOS 8.0 和更新版本
- Windows Phone 8.1 和更新版本
- Windows 10 桌面版與 Windows 10 行動裝置版

使用本主題中的資訊，可深入了解設定電子郵件設定檔的相關基本概念，然後可深入閱讀每個平台的主題，以了解裝置專屬內容。

## <a name="create-a-device-profile-containing-email-settings"></a>建立內含電子郵件設定的裝置設定檔

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置設定]。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
3. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗中，為電子郵件設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取要套用電子郵件設定的裝置平台。 您目前可為電子郵件裝置設定選擇下列平台之一︰
    - **Android** (僅限 Samsung Android Knox Standard)
    - **Android for Work**
    - **iOS**
    - **Windows Phone 8.1**
    - **Windows 10 及更新版本**
6. 從 [設定檔類型] 下拉式清單中，選擇 [電子郵件]。
7. 您可設定的設定值取決於您選擇的平台而有所不同。 前往下列主題之一，即可取得每個平台的詳細設定︰
    - [Android for Work 和 Samsung Knox Standard 設定](email-settings-android.md)
    - [iOS 設定](email-settings-ios.md)
    - [Windows Phone 8.1 設定](email-settings-windows-phone-8-1.md)
    - [Windows 10 設定](email-settings-windows-10.md)
8. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。
若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。

## <a name="further-information"></a>進一步資訊

### <a name="remove-an-email-profile"></a>移除電子郵件設定檔

若想要從裝置移除電子郵件設定檔，請編輯指派，然後再移除裝置所屬的任一群組。 請注意，若該電子郵件設定檔是裝置上唯一的電子郵件設定檔，即無法以此方式移除。

### <a name="securing-email-access"></a>保護電子郵件存取

您可以使用下列兩種方法之一來保護電子郵件設定檔︰

1. **憑證** - 當您建立電子郵件設定檔時，請選擇先前在 Intune 中建立的憑證設定檔。 這稱為識別憑證，用來針對允許使用者裝置連線的受信任憑證設定檔 (或根憑證) 進行驗證。 受信任的憑證會指派到可驗證電子郵件連線的電腦 (一般是原生郵件伺服器)。
如需如何在 Intune 中建立及使用憑證設定檔的詳細資訊，請參閱 [How to configure certificates with](certificates-configure.md) (如何利用 Intune 設定憑證)。
2. **使用者名稱與密碼** - 使用者藉由提供使用者名稱和密碼，向原生郵件伺服器進行驗證。
密碼不會包含在電子郵件設定檔中，因此使用者需要在連線至電子郵件時提供。


### <a name="how-intune-handles-existing-email-accounts"></a>Intune 如何處理現有電子郵件帳戶

如果使用者已設定了電子郵件帳戶，則 Intune 電子郵件設定檔指派的結果會取決於裝置平台︰

- **iOS：**依據主機名稱和電子郵件地址，偵測到重複的現有電子郵件設定檔。 重複的電子郵件設定檔將會封鎖 Intune 設定檔的指派。 在此情況下，公司入口網站會通知使用者他們並不符合規範，且會提示使用者要手動移除設定的設定檔。 為避免此問題，請指示使用者先進行註冊，再安裝電子郵件設定檔，允許 Intune 設定該設定檔。
- **Windows：**依據主機名稱和電子郵件地址，偵測到重複的現有電子郵件設定檔。 Intune 會覆寫使用者建立的現有電子郵件設定檔。
- **Android Samsung Knox Standard** 依據電子郵件地址，偵測到重複的現有電子郵件設定檔，而且會使用 Intune 設定檔覆寫它。
因為 Android 不會使用主機名稱來識別設定檔，所以建議您不要建立多個電子郵件設定檔在不同主機上的使用相同的電子郵件地址，以避免彼此覆寫。
- **Android for Work** Intune 提供兩個 Android for Work 電子郵件設定檔，分別用於 Gmail 和 Nine Work 電子郵件應用程式。 這些應用程式都是在 Google Play 商店取得，並且安裝在裝置工作設定檔中，因此不會產生重複的設定檔。 兩個應用程式都支援連線到 Exchange。 若要啟用電子郵件連線功能，請將其中一個電子郵件應用程式部署到使用者的裝置後，再建立及部署適當的電子郵件設定檔。 Nine Work 之類的電子郵件應用程式可能不是免費的。 請檢閱應用程式的授權詳細資料，如有任何問題，請連絡應用程式公司。

### <a name="update-an-email-profile"></a>更新電子郵件設定檔

如果您變更之前指派的電子郵件設定檔，使用者可能會看到要求核准其電子郵件設定重新設定的訊息。
