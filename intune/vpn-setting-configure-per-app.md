---
title: 在 Microsoft Intune 中設定 iOS 裝置的個別應用程式 VPN - Azure | Microsoft Docs
description: 在 iOS 裝置上，使用 Microsoft Intune 查看必要條件、建立虛擬私人網路 (VPN) 使用者群組、新增 SCEP 憑證設定檔、設定個別應用程式 VPN 設定檔，然後將一些應用程式指派給 VPN 設定檔。 同時列出確認裝置上 VPN 連線的步驟。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b3c2b5bc0091544136848bf92fc6cef7524ffa54
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68354501"
---
# <a name="set-up-per-app-virtual-private-network-vpn-for-ios-devices-in-intune"></a>在 Intune 中設定 iOS 裝置的個別應用程式虛擬私人網路 (VPN)

在 Microsoft Intune 中，您可以建立並使用指派給應用程式的虛擬私人網路 (VPN)。 此功能稱為「個別應用程式 VPN」。 您可以選擇哪些受控應用程式可以在受 Intune 管理的裝置上使用您的 VPN。 使用個別應用程式 VPN 時，終端使用者會透過 VPN 自動連線，並取得組織資源 (例如文件) 的存取權。

本功能適用於：

- iOS 9 和更新版本

請參閱您 VPN 提供者的文件，以了解您的 VPN 是否支援個別應用程式 VPN。

本文示範如何建立個別應用程式 VPN 設定檔，並將此設定檔指派給您的應用程式。 請使用這些步驟來為終端使用者建立順暢的個別應用程式 VPN 體驗。 針對大部分支援個別應用程式 VPN 的 VPN，使用者可以開啟應用程式，並自動連線到 VPN。

某些 VPN 允許以使用者名稱和密碼驗證個別應用程式 VPN。 這表示使用者必須輸入使用者名稱和密碼才能連線到 VPN。

## <a name="per-app-vpn-with-zscaler"></a>個別應用程式 VPN 與 Zscaler

Zscaler Private Access (ZPA) 與 Azure Active Directory (Azure AD) 整合以便進行驗證。 使用 ZPA 時，您不需要[信任的憑證](#create-a-trusted-certificate-profile)或是 [SCEP 或 PKCS 憑證](#create-a-scep-or-pkcs-certificate-profile)設定檔 (如本文中所述)。 如果您已設定 Zscaler 的個別應用程式 VPN 設定檔，則開啟其中一個相關聯的應用程式不會自動連線到 ZPA。 相反地，使用者必須先登入 Zscaler 應用程式。 然後，限制相關聯的應用程式才能進行遠端存取。

## <a name="prerequisites-for-per-app-vpn"></a>個別應用程式 VPN 的必要條件

> [!IMPORTANT]
> 您的 VPN 廠商對於個別應用程式 VPN 可能會有其他需求，例如特定硬體或授權。 請務必查閱其文件，並在 Intune 中設定個別應用程式 VPN 之前符合這些必要條件。

為證明身分識別，VPN 伺服器會出示必須接受的憑證，而且裝置不會提示。 為確認自動核准憑證，請建立內含憑證授權單位 (CA) 核發之 VPN 伺服器根憑證的受信任憑證設定檔。 

### <a name="export-the-certificate-and-add-the-ca"></a>匯出憑證並新增 CA

1. 在您的 VPN 伺服器上，開啟管理主控台。
2. 確認您的 VPN 伺服器使用憑證式驗證。 
3. 匯出受信任的根憑證檔案。 其副檔名為 .cer，並在建立受信任的憑證設定檔時予以新增。
4. 將簽發驗證憑證的 CA 名稱新增至 VPN 伺服器。

    如果裝置顯示之 CA 符合 VPN 伺服器上信任 CA 清單中的某個 CA，VPN 伺服器就可成功驗證裝置。

## <a name="create-a-group-for-your-vpn-users"></a>為您的 VPN 使用者建立一個群組

為使用個別應用程式 VPN 的使用者或裝置，建立或選擇 Azure Active Directory (Azure AD) 中的現有群組。 若要建立新的群組，請參閱[新增群組來組織使用者和裝置](groups-add.md)。

## <a name="create-a-trusted-certificate-profile"></a>建立受信任的憑證設定檔

將 CA 發行的 VPN 伺服器根憑證匯入在 Intune 中建立的設定檔。 受信任的憑證設定檔會指示 iOS 裝置自動信任 VPN 伺服器顯示的 CA。

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
3. 輸入下列內容：
    - **名稱**
    - **描述**
    - **平台**：選取 [iOS]  。
    - **設定檔類型**：選取 [信任的憑證]  。
4. 選取資料夾圖示，並瀏覽至從您 VPN 管理主控台匯出的 VPN 憑證 (.cer 檔案)。 
5. 選取 [確定]   > [建立]  。

    ![在 Microsoft Intune 中建立 iOS 裝置的受信任憑證設定檔](./media/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-or-pkcs-certificate-profile"></a>建立 SCEP 或 PKCS 憑證設定檔

受信任的根憑證設定檔可讓裝置自動信任 VPN 伺服器。 SCEP 或 PKCS 憑證提供從 iOS VPN 用戶端連線到 VPN 伺服器的認證。 憑證可讓裝置以無訊息的方式進行驗證，不會提示輸入使用者名稱和密碼。 

若要設定並指派用戶端驗證憑證，請參閱下列其中一篇文章：

- [透過 Intune 設定並管理 SCEP 憑證](certificates-scep-configure.md)
- [透過 Intune 設定並管理 PKCS 憑證](certficates-pfx-configure.md)

請務必設定用戶端驗證的憑證。 您可以在 SCEP 憑證設定檔中 ([擴充金鑰使用方法]  清單 > [用戶端驗證]  )，直接設定此憑證。 若是 PKCS，請在憑證授權單位 (CA) 的憑證範本中設定用戶端驗證。

![在 Microsoft Intune 中建立 SCEP 憑證設定檔，包括主體名稱格式、金鑰使用方法、擴充金鑰使用方法等](./media/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>建立個別應用程式 VPN 設定檔

VPN 設定檔包含附有用戶端認證、VPN 連線資訊與個別應用程式 VPN 旗標的 SCEP 或 PKCS 憑證，讓 iOS 應用程式得以使用個別應用程式 VPN 功能。

1. 在 **Intune** 中，選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。 
2. 輸入下列內容： 
    - **名稱**
    - **描述**
    - **平台**：選取 [iOS]  。
    - **設定檔類型**：選取 [VPN]  。
3. 在 [連線類型]  中，選取您的 VPN 用戶端應用程式。
4. 選取 [基底 VPN]  。 [iOS VPN 設定](vpn-settings-ios.md)會列出並描述所有設定。 使用個別應用程式 VPN 時，請務必設定下列屬性： 
    
    - **驗證方法**：選取 [憑證]  。 
    - **驗證憑證**：選取現有的 SCEP 或 PKCS 憑證 > [確定]  。      
    - **分割通道**：選取 [停用]  可在 VPN 連線為使用中時，強制所有流量使用 VPN 通道。 

      ![在個別應用程式 VPN 設定檔中，輸入連線、IP 位址或 FQDN、驗證方法，並在 Microsoft Intune 中分割通道](./media/vpn-per-app-create-vpn-profile.png)

    如需其他設定的資訊，請參閱 [iOS VPN 設定](vpn-settings-ios.md)。

5. 選取 [自動 VPN]   > [自動 VPN 類型]   > [個別應用程式 VPN] 

    ![在 Intune 中，將 [自動 VPN] 設定為 iOS 裝置上的個別應用程式 VPN](./media/vpn-per-app-automatic.png)

6. 選取 [確定]   > [確定]   > [建立]  。

## <a name="associate-an-app-with-the-vpn-profile"></a>建立應用程式與 VPN 設定檔的關聯

在新增 VPN 設定檔之後，請對設定檔建立應用程式與 Azure AD 群組的關聯。

1. 在 **Intune** 中，選取 [用戶端應用程式]   > [應用程式]  。
2. 從清單中選取應用程式 > [指派]   > [新增群組]  。
3. 在 [指派類型]  中，選取 [必要]  或 [適用於已註冊的裝置]  。
4. 選取 [包含的群組]   > [選取要包含的群組]  > 選取您在本文中[建立](#create-a-group-for-your-vpn-users)的群組 > [選取]  。
5. 在 [VPN]  中，選取您在本文中[建立](#create-a-per-app-vpn-profile)的個別應用程式 VPN 設定檔。

    ![在 Microsoft Intune 中將應用程式指派給個別應用程式 VPN](./media/vpn-per-app-app-to-vpn.png)

6. 選取 [確定]   > [儲存]  。

在下次裝置簽入期間，當下列所有條件皆成立時，會移除應用程式與設定檔之間的關聯：

- 應用程式以必要安裝意圖為目標。
- 設定檔與應用程式都以相同的群組為目標。
- 您將個別應用程式 VPN 設定從應用程式指派移除。

當下列所有條件皆成立時，應用程式與設定檔之間的關聯會保存到使用者要求從公司入口網站重新安裝為止：

- 應用程式以可用安裝意圖為目標。
- 設定檔與應用程式都以相同的群組為目標。
- 終端使用者要求從公司入口網站安裝應用程式，這導致裝置上同時安裝應用程式與設定檔。
- 您將個別應用程式 VPN 設定從應用程式指派移除或變更。

## <a name="verify-the-connection-on-the-ios-device"></a>驗證 iOS 裝置上的連線

完成個別應用程式 VPN 設定，並建立其與您應用程式的關聯後，請從裝置驗證連線是否可運作。

### <a name="before-you-attempt-to-connect"></a>嘗試連線前

- 請確定您將上述提到的所有原則都部署到相同群組。 否則，個別應用程式 VPN 體驗將無法運作。
- 如果您使用 Pulse Secure VPN 應用程式或自訂 VPN 用戶端應用程式，您可以選擇使用應用程式層或封包層通道。 若是應用程式層通道，請將 [ProviderType]  值設定為 [應用程式 Proxy]  ，若是封包層通道，則設定為 [封包通道]  。 請參閱您 VPN 提供者的文件，以確定您使用的值正確。

### <a name="connect-using-the-per-app-vpn"></a>使用個別應用程式 VPN 來連線

在不選取 VPN 或鍵入認證的情況下連線，來驗證零觸控體驗。 零觸控體驗意味著：

- 裝置不會要求您信任 VPN 伺服器。 也就是說，使用者不會看到 [動態信任]  對話方塊。
- 使用者無須鍵入認證。
- 當使用者開啟其中一個相關聯的應用程式時，使用者的裝置已連線到 VPN。

<!-- ## Troubleshooting the per-app VPN

The user experiences the feature by silently connecting to the VPN. This experience, however, can provide little information for troubleshooting. You can review the event logs crated by the iOS device.

`Note -- use the Apple Configurator as the supported tool. Only runs on a mac.'

To review event logs:

1. Connect your iOS device to a PC
2. Open the **iPhone Configuration Utility** (IPCU). If you do not have a copy, you can install it from [CompatCenter](http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=iPhone%20Configuration%20Utility&vendor=Apple&Locale=1033%2C2057%2C3081%2C4105%2C16393&ModelOrVersion=3&BreadCrumbPath=iphone%20configuration%20utility&LastSearchTerm=iphone%2Bconfiguration%2Butility&Type=Software&tempOsid=Windows%208.1)
3. Review the logs. -->

## <a name="next-steps"></a>後續步驟

- 若要檢閱 iOS 設定，請參閱 [Microsoft Intune 中 iOS 裝置的 VPN 設定](vpn-settings-ios.md)。
- 若要深入了解 VPN 設定和 Intune，請參閱[在 Microsoft Intune 中進行 VPN 設定](vpn-settings-configure.md)。
