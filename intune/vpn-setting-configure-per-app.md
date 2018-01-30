---
title: "在 Microsoft Intune 中設定 iOS 裝置的個別應用程式 VPN"
titleSuffix: Intune on Azure
description: "指定哪些受管理應用程式可以在受 Intune 管理的 iOS 裝置使用您的 VPN。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/5/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6f7e53f9a440d945d834c17b9db85ed5f6e42229
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="set-up-per-app-vpn-in-microsoft-intune-for-ios-devices"></a>在 Microsoft Intune 中設定 iOS 裝置的個別應用程式 VPN

您可以指定哪些受管理應用程式可以在受 Intune 管理的 iOS 裝置上使用您的虛擬私人網路 (VPN)。 您在 Intune 中指定個別應用程式 VPN 後，當終端使用者存取公司文件時，就會自動透過您的 VPN 連線。

## <a name="prerequisites-for-the-per-app-vpn"></a>個別應用程式 VPN 的必要條件

為證明身分識別，VPN 伺服器會出示必須接受的憑證，而且裝置不會提示。 為確保自動核准憑證，請建立內含憑證授權單位 (CA) 核發之 VPN 伺服器根憑證的受信任憑證設定檔。 

匯出憑證並新增 CA。

1. 開啟 VPN 伺服器上的管理主控台。
2. 驗證您的 VPN 伺服器使用憑證式驗證。 
3. 匯出受信任的根憑證檔案。 其副檔名為 .cer，並在建立受信任的憑證設定檔時予以新增。
4. 將簽發驗證憑證的 CA 名稱新增至 VPN 伺服器。
    如果裝置顯示的 CA 符合 VPN 伺服器上受信任 CA 清單的其中一個 CA，VPN 伺服器就可成功驗證裝置。

## <a name="create-a--group-for-your-vpn-users"></a>建立 VPN 使用者的群組

建立或選擇 Azure Active Directory (Azure AD) 中的現有群組，以納入可存取個別應用程式 VPN 的成員。

1. 開啟 Azure 入口網站。 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
2. 選擇 [群組] 並按一下 [新增群組]。
3. 鍵入群組的**名稱**。 
4. 鍵入群組的**名稱**。 
5. 為 [成員資格類型] 選取 [已指派]。
6. 為 [啟用 Office 功能] 選取 [否]。
7. 在 [成員] 刀鋒視窗中，根據名稱或電子郵件地址搜尋 VPN 使用者。
8. 選取各個使用者，然後按一下 [選取]。
9. 按一下 [建立]

## <a name="create-a-trusted-certificate-profile"></a>建立受信任的憑證設定檔

將 CA 發行的 VPN 伺服器根憑證匯入在 Intune 中建立的設定檔。 受信任的憑證設定檔會指示 iOS 裝置自動信任 VPN 伺服器顯示的 CA。

1. 開啟 Azure 入口網站。 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
2. 選擇 [裝置設定]，然後按一下 [設定檔]。
3. 按一下 [+ 建立設定檔]。 在 [建立設定檔] 中：
    1. 鍵入**名稱**。
    2. 鍵入**描述**。
    3. 為 [平台] 選取 [iOS]。
    4. 為 [設定檔類型] 選取 [信任的憑證]。
4. 按一下資料夾圖示，並瀏覽至從您 VPN 管理主控台匯出的 VPN 憑證 (.cer 檔案)。 按一下 [確定]
5. 按一下 [建立]。

    ![建立受信任的憑證設定檔](media\vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-certificate-profile"></a>建立 SCEP 憑證設定檔

受信任的根憑證設定檔可讓 iOS 自動信任 VPN 伺服器。 SCEP 憑證提供從 iOS VPN 用戶端連線到 VPN 伺服器的認證。 憑證可讓裝置以無訊息的方式進行驗證，不會提示 iOS 裝置使用者使用者名稱和密碼。 

1. 開啟 Azure 入口網站。 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。 
2. 選擇 [裝置設定]，然後按一下 [設定檔]。
3. 按一下 [+ 建立設定檔]。 在 [建立設定檔] 中：
    1. 鍵入**名稱**。
    2. 鍵入**描述**。
    3. 為 [平台] 選取 [iOS]。
    4. 為 [設定檔類型] 選取 [SCEP 憑證]。
4. 選取 [年份] 並為 [憑證有效期間] 鍵入 `2`。
5. 為 [主體名稱格式] 選取 [一般名稱]。
6. 為 [主體別名] 選取 [使用者主體名稱 (UPN)]。
7. 為 [金鑰使用方法] 選取 [數位簽章] 和 [金鑰編密]。
8. 為 [金鑰大小 (位元組)] 選取 [2048]。
9. 按一下 [根憑證]，然後選取一個 SCEP 憑證。 按一下 [ **確定**]。
10. 在 [擴充金鑰使用方法] 的 [名稱] 中，鍵入 `Client Authentication`。
11. 在 [物件識別碼] 中，鍵入 `1.3.6.1.5.5.7.3.2`。
12. 按一下 [加入] 。
13. 鍵入伺服器 URL 並按一下 [新增]。
14. 按一下 [ **確定**]。
15. 按一下 [建立]。

    ![建立 SCEP 憑證設定檔](media\vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>建立個別應用程式 VPN 設定檔

VPN 設定檔包含附有用戶端認證、VPN 的連線資訊及個別應用程式 VPN 旗標的 SCEP 憑證，讓 iOS 應用程式得以使用個別應用程式 VPN 功能。

1. 開啟 Azure 入口網站。 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
2. 選擇 [裝置設定]，然後按一下 [設定檔]。
3. 按一下 [+ 建立設定檔]。 在 [建立設定檔] 中：
    1. 鍵入**名稱**。
    2. 鍵入**描述**。
    3. 為 [平台] 選取 [iOS]。
    4. 為 [設定檔類型] 選取 [VPN]。
4. 選取 [基底 VPN]。 在 [基底 VPN]中：
    1. 鍵入**連線名稱**。
    2. 鍵入 **IP 位址或 FQDN**。
    3. 為 [驗證方法] 選取 [憑證]。
    4. 在 [驗證憑證] 下選取 SCEP 憑證並按一下 [確定]。
    5. 選取您 VPN 的 [連線類型]。
    6. 如有必要，請設定您 VPN 的屬性。
    7. 選取 [停用分割] 通道。
5. 按一下 [自動 VPN]。 在 [自動 VPN] 中：
    1. 為 [自動 VPN 類型] 選取 [個別應用程式 VPN]。
    2. 鍵入 VPN 的 URL 並按一下 [新增]。
    3. 按一下 [ **確定**]。
6. 按一下 [ **確定**]。
7. 按一下 [建立]。

    ![建立個別應用程式 VPN 設定檔](media\vpn-per-app-create-vpn-profile.png)


## <a name="associate-an-app-with-the-vpn-profile"></a>建立應用程式與 VPN 設定檔的關聯

在新增 VPN 設定檔之後，請對設定檔建立應用程式與 Azure AD 群組的關聯。

1. 開啟 Azure 入口網站。 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
2. 選擇 [Mobile Apps]。
3. 按一下 [應用程式]。
4. 從應用程式清單中選取應用程式。
5. 按一下 [指派]。
6. 按一下 [選取群組]，選取您先前定義的群組。 按一下 [選取]。
7. 在 [指派] 刀鋒視窗中，為 [類型] 選取 [必要]。
8. 為 [VPN] 選取您的 VPN 定義。
 
    > [!NOTE]  
    > 有時，VPN 定義最多會花費一分鐘的時間來擷取值。 請先稍候 3 到 5 分鐘再按一下 [儲存]。

9. 按一下 **[儲存]**。

    ![建立應用程式與 VPN 的關聯](media\vpn-per-app-app-to-vpn.png)

## <a name="verify-the-connection-on-the-ios-device"></a>驗證 iOS 裝置上的連線

完成個別應用程式 VPN 設定，並建立其與您應用程式的關聯後，請驗證能夠與裝置連線。

### <a name="before-you-attempt-to-connect"></a>嘗試連線前

 - 請先確定您執行 iOS 7 或更新版本。
 - 請確定您將上述提到的「所有」原則部署都到相同的使用者群組。 若未如實執行，個別應用程式 VPN 體驗一定會中斷。  
 - 請確定您已安裝支援的協力廠商 VPN 應用程式。 支援下列 VPN 應用程式：
    - Pulse Secure
    - Checkpoint
    - F5
    - SonicWall

### <a name="connect-using-the-per-app-vpn"></a>使用個別應用程式 VPN 來連線

在不選取 VPN 或鍵入認證的情況下連線，來驗證零觸控體驗。 零觸控體驗意味著：

 - 裝置不會要求您信任 VPN 伺服器。 也就是說，您看會到 [動態信任] 對話方塊。
 - 您無須鍵入認證。
 - 點選 [連線] 按鈕之後，就會連線到 VPN。

驗證 iOS 裝置上的連線。

1. 點選 [VPN 應用程式]。
2. 點選 [連線]。  
VPN 成功連線，而且沒有其他任何提示。

<!-- ## Troubleshooting the Per-App VPN

The user experiences the feature by silently connecting to the VPN. This experience, however, can provide little information for troubleshooting. You can review the event logs crated by the iOS device.

`Note -- use the Apple Configurator as the supported tool. Only runs on a mac.'

To review event logs:

1. Connect your iOS device to a PC
2. Open the **iPhone Configuration Utility** (IPCU). If you do not have a copy, you can install it from [CompatCenter](http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=iPhone%20Configuration%20Utility&vendor=Apple&Locale=1033%2C2057%2C3081%2C4105%2C16393&ModelOrVersion=3&BreadCrumbPath=iphone%20configuration%20utility&LastSearchTerm=iphone%2Bconfiguration%2Butility&Type=Software&tempOsid=Windows%208.1)
3. Review the logs. -->

## <a name="next-steps"></a>接下來的步驟

- 若要檢閱 iOS 設定，請參閱 [Microsoft Intune 中 iOS 裝置的 VPN 設定](vpn-settings-ios.md)。
-  若要深入了解 VPN 設定和 Intune，請參閱[如何在 Microsoft Intune 中進行 VPN 設定](vpn-settings-configure.md)。