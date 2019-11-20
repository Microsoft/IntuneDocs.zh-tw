---
title: 將您的 Intune 帳戶連線到受控 Google Play 帳戶。
titleSuffix: Microsoft Intune
description: 了解如何將您的 Intune 帳戶連線到受控 Google Play 帳戶。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a89b94f098292bf44122d6d2d144c7f35967cd32
ms.sourcegitcommit: 556b7ea2049014c9027f0e44affd3f301fab55fc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73709457"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>將您的 Intune 帳戶連線到受控 Google Play 帳戶

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

為了支援 [Android Enterprise 工作設定檔裝置](android-work-profile-enroll.md)、[Android Enterprise 完全受控裝置](android-fully-managed-enroll.md)和 [專用裝置](android-kiosk-enroll.md)，您必須將 Intune 租用戶帳戶連線到受控 Google Play 帳戶。  

為了讓您能夠更輕鬆地設定並使用 Android Enterprise 管理，在連線至 Google Play 之後，Intune 便會將四個常見的 Android Enterprise 相關應用程式自動新增到 Intune 管理主控台。 四個 Android 企業應用程式如下：

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - 用於 Android 企業完全受控案例。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 協助您登入您的帳戶 (若您使用雙重要素驗證)。
- **[Intune 公司入口網站](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - 用於應用程式保護原則 (APP) 與 Android 企業公司設定檔案例。
- [受控家用案例](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - 用於 Android 企業專用/資訊站案例。

> [!NOTE]
> 因為 Google 和 Microsoft 網域之間的互動，這個步驟可能需要調整瀏覽器設定。  請確定 "portal.azure.com" 和 "play.google.com" 位於您瀏覽器中相同的安全性區域。

1. 如果尚未這麼做，請將[行動裝置管理授權單位](../fundamentals/mdm-authority-set.md)設定為 **Microsoft Intune**，以針對行動裝置管理做準備。
2. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，選擇 [裝置註冊]   > [Android 註冊]   > [受控 Google Play]  。  如果您使用自訂的 Intune 管理員角色，則存取這個會需要組織讀取和更新的權限。
   
   ![Android 企業註冊畫面](./media/connect-intune-android-enterprise/android-work-bind.png)

3. 選擇 [我同意]  將權限授與 Microsoft，以[將使用者和裝置資訊傳送給 Google](../protect/data-intune-sends-to-google.md)。 
   
4. 選擇 [啟動 Google 以立即連線]  以開啟受控 Google Play 網站。 在瀏覽器的新索引標籤中開啟網站。
  
5. 在 Google 的登入頁面上，輸入將與此租用戶所有的 Android Enterprise 管理工作建立關聯的 Google 帳戶。 這是貴公司 IT 管理員共用的 Google 帳戶，可以在 Google Play 主控台中管理及發佈應用程式。 您可以使用現有的 Google 帳戶或建立新帳戶。 您選擇的帳戶絕不能與 G 套件網域建立關聯性。
    
    > [!Note]
    > 若您使用 Microsoft Edge 瀏覽器，請按一下右上角的 [登入]  來登入您的 Google 帳戶。

6. 提供您的公司名稱作為**組織名稱**。 針對**企業行動管理 (EMM) 提供者**，應該顯示 **Microsoft Intune**。

7. 同意 Android 合約，然後選擇 [確認]  。 您的要求將會被處理。

## <a name="disconnect-your-android-enterprise-administrative-account"></a>中斷與 Android Enterprise 系統管理帳戶的連線

您可以關閉 Android Enterprise 註冊和管理。 若要這樣做，您必須先淘汰任何已註冊的 Android Enterprise 裝置，包括工作設定檔裝置、專用裝置及完全受控裝置。 然後，在 Intune 管理主控台中選擇 [中斷連線]  ，從註冊中移除所有已註冊的 Android Enterprise 工作設定檔裝置、專用裝置及完全受控裝置。 這也會移除受控 Google Play 帳戶與 Intune 之間的關聯。

1. 以 Intune 管理員身分登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選擇 [裝置註冊]   > [Android 註冊]   > [受控 Google Play]   > [中斷連線]  。
3. 選擇 [是]  以中斷連線，然後從 Intune 取消註冊所有的 Android 企業裝置。

## <a name="next-steps"></a>後續步驟

連線至受控 Google Play 帳戶之後，您可以[設定 Android Enterprise 工作設定檔裝置](android-work-profile-enroll.md)、[設定 Android Enterprise 專用裝置](android-kiosk-enroll.md)，以及[設定 Android Enterprise 完全受控裝置](android-kiosk-enroll.md)
