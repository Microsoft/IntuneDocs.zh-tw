---
title: 在 Microsoft Intune 中設定 iOS 裝置的個別應用程式 VPN - Azure | Microsoft Docs
description: 在 iOS 裝置上，使用 Microsoft Intune 查看必要條件、建立虛擬私人網路 (VPN) 使用者群組、新增 SCEP 憑證設定檔、設定個別應用程式 VPN 設定檔，然後將一些應用程式指派給 VPN 設定檔。 同時列出確認裝置上 VPN 連線的步驟。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 87c3313fd7b5fc0705460e539164ac70779bebeb
ms.sourcegitcommit: 77540295381a59918eb638ce9c1870209cf8af02
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46505762"
---
# <a name="set-up-per-app-virtual-private-network-vpn-in-intune-for-ios-devices"></a>在 Intune 中設定 iOS 裝置的個別應用程式虛擬私人網路 (VPN)

您可以指定哪些受控應用程式可以在受 Intune 管理的 iOS 裝置上使用您的虛擬私人網路 (VPN)。 您在 Intune 中建立個別應用程式 VPN 後，使用者存取公司文件時，就會自動透過您的 VPN 連線。

下列提供者目前推出個別應用程式 VPN：

 - Check Point Remote Access VPN
 - Cisco AnyConnect
 - Citrix
 - F5
 - Pulse 連線安全
 - SonicWall
 - Palo Alto Networks GlobalProtect
 - Zscaler

## <a name="prerequisites-for-per-app-vpn"></a>個別應用程式 VPN 的必要條件

> [!IMPORTANT]
> 您的 VPN 廠商對於個別應用程式 VPN 可能會有其他特定需求，例如特定硬體或授權。 請務必查閱其文件，並在 Intune 中設定個別應用程式 VPN 之前符合這些必要條件。

為證明身分識別，VPN 伺服器會出示必須接受的憑證，而且裝置不會提示。 為確保自動核准憑證，請建立內含憑證授權單位 (CA) 核發之 VPN 伺服器根憑證的受信任憑證設定檔。 

匯出憑證並新增 CA。

1. 開啟 VPN 伺服器上的管理主控台。
2. 驗證您的 VPN 伺服器使用憑證式驗證。 
3. 匯出受信任的根憑證檔案。 其副檔名為 .cer，並在建立受信任的憑證設定檔時予以新增。
4. 將簽發驗證憑證的 CA 名稱新增至 VPN 伺服器。
    如果裝置顯示的 CA 符合 VPN 伺服器上受信任 CA 清單的其中一個 CA，VPN 伺服器就可成功驗證裝置。

## <a name="create-a-group-for-your-vpn-users"></a>為您的 VPN 使用者建立一個群組

建立或選擇 Azure Active Directory (Azure AD) 中的現有群組，以納入可存取個別應用程式 VPN 的成員。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選擇 [群組] 並按一下 [新增群組]。
3. 為群組選取 [群組類型]。 
3. 鍵入群組的 [群組名稱]。 
4. 鍵入群組的 [群組描述]。 
5. 為 [成員資格類型] 選取 [已指派]。
7. 在 [成員] 窗格中，根據名稱或電子郵件地址搜尋 VPN 使用者。
8. 選取各個使用者，然後按一下 [選取]。
9. 按一下 [建立]

## <a name="create-a-trusted-certificate-profile"></a>建立受信任的憑證設定檔

將 CA 發行的 VPN 伺服器根憑證匯入在 Intune 中建立的設定檔。 受信任的憑證設定檔會指示 iOS 裝置自動信任 VPN 伺服器顯示的 CA。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選擇 [裝置設定]，然後按一下 [設定檔]。
3. 按一下 [建立設定檔]。 在 [建立設定檔] 中：
    1. 鍵入**名稱**。
    2. 鍵入**描述**。
    3. 為 [平台] 選取 [iOS]。
    4. 為 [設定檔類型] 選取 [信任的憑證]。
4. 按一下資料夾圖示，並瀏覽至從您 VPN 管理主控台匯出的 VPN 憑證 (.cer 檔案)。 按一下 [確定]。
5. 按一下 [建立]。

    ![建立受信任的憑證設定檔](./media/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-certificate-profile"></a>建立 SCEP 憑證設定檔

受信任的根憑證設定檔可讓 iOS 自動信任 VPN 伺服器。 SCEP 憑證提供從 iOS VPN 用戶端連線到 VPN 伺服器的認證。 憑證可讓裝置以無訊息的方式進行驗證，不會提示 iOS 裝置使用者使用者名稱和密碼。 

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選擇 [裝置設定]，然後按一下 [設定檔]。
3. 按一下 [建立設定檔]。 在 [建立設定檔] 中：
    1. 鍵入**名稱**。
    2. 鍵入**描述**。
    3. 為 [平台] 選取 [iOS]。
    4. 為 [設定檔類型] 選取 [SCEP 憑證]。
4. 選取 [年份] 並為 [憑證有效期間] 鍵入 `2`。
5. 為 [主體名稱格式] 選取 [一般名稱]。
6. 為 [主體別名] 選取 [使用者主體名稱 (UPN)]。
7. 為 [金鑰使用方法] 選取 [數位簽章] 和 [金鑰編密]。
8. 為 [金鑰大小 (位元組)] 選取 [2048]。
9. 按一下 [根憑證]，然後選取一個 SCEP 憑證。 按一下 [確定]。
10. 在 [擴充金鑰使用方法] 的 [名稱] 中，鍵入 `Client Authentication`。
11. 在 [物件識別碼] 中，鍵入 `1.3.6.1.5.5.7.3.2`。
12. 按一下 [加入] 。
13. 鍵入伺服器 URL 並按一下 [新增]。
14. 按一下 [確定]。
15. 按一下 [建立]。

    ![建立 SCEP 憑證設定檔](./media/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>建立個別應用程式 VPN 設定檔

VPN 設定檔包含附有用戶端認證、VPN 連線資訊與個別應用程式 VPN 旗標的 SCEP 憑證，讓 iOS 應用程式得以使用個別應用程式 VPN 功能。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選擇 [裝置設定]，然後按一下 [設定檔]。
3. 按一下 [建立設定檔]。 在 [建立設定檔] 中：
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
    7. 選取 [Disable Split tunneling] (停用分割通道)。
5. 按一下 [自動 VPN]。 在 [自動 VPN] 中：
    1. 為 [自動 VPN 類型] 選取 [個別應用程式 VPN]。
    2. 鍵入 VPN 的 URL 並按一下 [新增]。
    3. 按一下 [確定]。
6. 按一下 [確定]。
7. 按一下 [建立]。

    ![建立個別應用程式 VPN 設定檔](./media/vpn-per-app-create-vpn-profile.png)


## <a name="associate-an-app-with-the-vpn-profile"></a>建立應用程式與 VPN 設定檔的關聯

在新增 VPN 設定檔之後，請對設定檔建立應用程式與 Azure AD 群組的關聯。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選擇 [用戶端應用程式]。
4. 按一下 [應用程式]。
5. 從應用程式清單中選取應用程式。
6. 按一下 [指派]。
7. 按一下 [新增群組]。
8. 在 [新增群組] 窗格的 [指派類型]，選取 [必要]。
9. 選取您之前定義的群組，並選取 [Make this app required] (讓此應用程式成為必要)。
10. 為 [VPN] 選取您的 VPN 定義。
 
    > [!NOTE]  
    > 有時，VPN 定義最多會花費一分鐘的時間來擷取值。 請先稍候 3 到 5 分鐘再按一下 [儲存]。

11. 按一下 [確定] ，然後按一下 [儲存]。

    ![建立應用程式與 VPN 的關聯](./media/vpn-per-app-app-to-vpn.png)

在下次裝置簽入期間，當下列條件存在時，將會移除應用程式與設定檔之間的關聯：
- 應用程式以必要安裝意圖為目標。
- 設定檔與應用程式都以相同的群組為目標。
- 您將個別應用程式 VPN 設定從應用程式指派移除。

當下列條件成立時，應用程式與設定檔之間的關聯會保存到終端使用者要求從公司入口網站重新安裝為止：
- 應用程式以可用安裝意圖為目標。
- 設定檔與應用程式都以相同的群組為目標。
- 使用者要求從公司入口網站安裝應用程式，這導致裝置上同時安裝應用程式與設定檔。
- 您將個別應用程式 VPN 設定從應用程式指派移除或變更。

## <a name="verify-the-connection-on-the-ios-device"></a>驗證 iOS 裝置上的連線

完成個別應用程式 VPN 設定，並建立其與您應用程式的關聯後，請從裝置驗證連線是否可運作。

### <a name="before-you-attempt-to-connect"></a>嘗試連線前

 - 請先確定您正在執行 iOS 9 或更新版本。
 - 請確定您將上述提到的「所有」原則部署都到相同的使用者群組。 若未如實執行，個別應用程式 VPN 體驗一定會中斷。  
 - 請確定您已安裝支援的協力廠商 VPN 應用程式。 支援下列 VPN 應用程式：
    - Check Point Capsule Connect
    - Cisco AnyConnect
    - Citrix VPN
    - F5 Access
    - Pulse Secure
    - SonicWall Mobile Connect
    - Zscaler App

    > [!NOTE]
    > 如果您使用 Pulse Secure VPN 應用程式，您可以選擇使用應用程式層或封包層通道。 若是應用程式層通道，請將 [ProviderType] 值設定為 [應用程式 Proxy]，若是封包層通道，則設定為 [封包通道]。

### <a name="connect-using-the-per-app-vpn"></a>使用個別應用程式 VPN 來連線

在不選取 VPN 或鍵入認證的情況下連線，來驗證零觸控體驗。 零觸控體驗意味著：

 - 裝置不會要求您信任 VPN 伺服器。 也就是說，您看會到 [動態信任] 對話方塊。
 - 您無須鍵入認證。
 - 點選 [連線] 按鈕之後，就會連線到 VPN。

驗證 iOS 裝置上的連線。

1. 點選 [VPN 應用程式]。
2. 點選 [連線]。  
VPN 成功連線，而且沒有其他任何提示。

<!-- ## Troubleshooting the per-app VPN

The user experiences the feature by silently connecting to the VPN. This experience, however, can provide little information for troubleshooting. You can review the event logs crated by the iOS device.

`Note -- use the Apple Configurator as the supported tool. Only runs on a mac.'

To review event logs:

1. Connect your iOS device to a PC
2. Open the **iPhone Configuration Utility** (IPCU). If you do not have a copy, you can install it from [CompatCenter](http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=iPhone%20Configuration%20Utility&vendor=Apple&Locale=1033%2C2057%2C3081%2C4105%2C16393&ModelOrVersion=3&BreadCrumbPath=iphone%20configuration%20utility&LastSearchTerm=iphone%2Bconfiguration%2Butility&Type=Software&tempOsid=Windows%208.1)
3. Review the logs. -->

## <a name="next-steps"></a>接下來的步驟

- 若要檢閱 iOS 設定，請參閱 [Microsoft Intune 中 iOS 裝置的 VPN 設定](vpn-settings-ios.md)。
-  若要深入了解 VPN 設定和 Intune，請參閱[如何在 Microsoft Intune 中進行 VPN 設定](vpn-settings-configure.md)。
