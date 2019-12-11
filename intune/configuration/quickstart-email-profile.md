---
title: 快速入門 - 建立 iOS 的電子郵件裝置設定檔
titleSuffix: Microsoft Intune
description: 了解如何使用 Microsoft Intune 建立電子郵件裝置設定檔，讓 iOS 裝置可以安全地連線至公司電子郵件。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b2f1372a6d7ced09a9ebdfc11cbad69501827bc
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059317"
---
# <a name="quickstart-create-an-email-device-profile-for-ios"></a>快速入門：建立 iOS 的電子郵件裝置設定檔

在本快速入門中，您會看到如何建立 iOS 裝置的電子郵件裝置設定檔。 此設定檔指定 iOS 裝置上內建電子郵件應用程式所需的設定來連線至公司電子郵件。 電子郵件裝置設定檔可協助將各個裝置的設定標準化，並讓終端使用者不需要任何設定，就能從其個人裝置存取公司電子郵件。 若要進一步保護您的電子郵件，您可以使用電子郵件設定檔來判斷裝置是否符合規範，然後將條件式存取設定為僅允許符合規範的裝置存取電子郵件。 如需電子郵件設定檔的詳細資訊，請參閱[如何在 Microsoft Intune 中設定電子郵件設定](email-settings-configure.md)

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](../fundamentals/free-trial-sign-up.md)。

## <a name="sign-in-to-intune"></a>登入 Intune

請以全域管理員或 Intune 服務管理員身分登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 如果您已建立 Intune 試用版訂閱，則用來建立訂閱的帳戶是全域管理員。

## <a name="create-an-ios-email-profile"></a>建立 iOS 電子郵件設定檔

1. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。

   ![建立 iOS 的電子郵件設定檔](./media/quickstart-email-profile/ios-create-profile.png)

2. 在 [名稱]  下方，輸入新設定檔的描述性名稱。 在此範例中，輸入 **iOS require work email**。
3. 輸入下列設定檔資訊：
    - 針對 [描述]  ，輸入 **Require iOS devices to use work email**。
    - 針對 [平台]  ，選取 [iOS]  。
    - 針對 [設定檔類型]  ，選取 [電子郵件]  。

        ![建立用於 iOS 的電子郵件設定檔](./media/quickstart-email-profile/ios-email-profile-name.png)

4. 選取 [設定]  ，然後輸入下列設定 (保留其他設定的預設值)：
   - **電子郵件伺服器**：在本快速入門中，輸入 **outlook.office365.com**。 此設定指定 iOS 郵件應用程式將用來連線至電子郵件之電子郵件伺服器的 Exchange 位置 (URL)。
   - **帳戶名稱**：輸入**公司電子郵件**。
   - **AAD 中的使用者名稱屬性**：此名稱是 Intune 從 Azure Active Directory (Azure AD) 中取得的屬性。 Intune 會使用此名稱動態產生此設定檔的使用者名稱。 在本快速入門中，假設我們想要使用**使用者主體名稱**作為設定檔的使用者名稱 (例如 user1@contoso.com)。
   - **AAD 中的電子郵件地址屬性**：此設定是 Azure AD 中將用來登入 Exchange 的電子郵件地址。 在本快速入門中，選取 [使用者主體名稱]  。
   - **驗證方法**：在本快速入門中，選取 [使用者名稱和密碼]  。 (如果您已經設定 Intune 的憑證，則也可以選擇 [憑證]  )。

        ![建立用於 iOS 的電子郵件設定檔](./media/quickstart-email-profile/ios-email-profile.png)

5. 選取 [確定]   > [建立]  。 新的設定檔會出現在已顯示儀表板的設定檔清單中，因此您可以監視如何將設定檔指派給 iOS 裝置和 iOS 使用者。
6. 選取 [指派]  。
7. 選取 [包含]  索引標籤，然後選取 [所有使用者和所有裝置]  。 
8. 選取 [儲存]  。

## <a name="clean-up-resources"></a>清除資源

如果您不想要使用為其他教學課程或測試建立的設定檔，則可以立即將其刪除。

1. 在 Intune 中，選取 [裝置設定]  ，然後選取 [設定檔]  。
2. 選取您所建立的測試設定檔：**iOS require work email**。
3. 選取設定檔旁邊的省略符號 ( **...** )，然後選取 [刪除]  。

## <a name="next-steps"></a>後續步驟

在本快速入門中，您已建立 iOS 裝置的電子郵件設定檔。 現在，您可以使用此設定檔來判斷 iOS 裝置是否符合規範，方法是建立將任何不符合該設定檔的 iOS 裝置標記為不符合規範的合規性政策。 如需進一步保護，您可以建立條件式存取原則，以封鎖不符合規範的 iOS 裝置存取電子郵件。 如需裝置合規性原則的詳細資訊，請參閱[開始使用 Intune 中的裝置合規性原則](../protect/device-compliance-get-started.md)。

> [!div class="nextstepaction"]
> [教學課程：保護受控裝置上的 Exchange Online 電子郵件](../tutorial-protect-email-on-enrolled-devices.md)
