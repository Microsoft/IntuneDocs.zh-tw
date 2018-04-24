---
title: 裝置註冊疑難排解
description: 裝置註冊問題的疑難排解建議。
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 09/15/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6982ba0e-90ff-4fc4-9594-55797e504b62
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4c69dec5903f25b9e7f09f6a20fc35068f3329d4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshoot-device-enrollment-in-intune"></a>Intune 的裝置註冊疑難排解

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

本主題提供裝置註冊問題的疑難排解建議。 如果此資訊無法解決您的問題，請參閱[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)，以尋找更多方法來取得協助。


## <a name="initial-troubleshooting-steps"></a>初始疑難排解步驟

在您開始進行疑難排解之前，請先確定您已正確設定 Intune，以便啟用註冊。 您可以閱讀有關那些設定需求︰

-   [準備在 Microsoft Intune 中註冊裝置](/intune-classic/deploy-use/prerequisites-for-enrollment)
-   [設定 iOS 和 Mac 裝置管理](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
-   [設定 Windows 裝置管理](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune)
-   [設定 Android 裝置管理](/intune-classic/deploy-use/set-up-android-management-with-microsoft-intune) - 不需要其他步驟
-   [設定 Android for Work 裝置管理](/intune-classic/deploy-use/set-up-android-for-work)

您也可以確認使用者裝置上的時間與日期是否設定正確：

1. 重新啟動裝置。
2. 請務必將時間與日期設定成接近相較於終端使用者時區的 GMT 標準時間 (+ 或 - 12 個小時)。
3. 將「Intune 公司入口網站」解除安裝並重新安裝 (如果適用)。

您所管理的裝置使用者可以收集註冊與診斷記錄檔，以供您檢閱。 提供有關收集記錄檔使用者指示之處如下：

- [將 Android 註冊錯誤傳送給 IT 系統管理員](https://docs.microsoft.com/intune-user-help/send-enrollment-errors-to-your-it-admin-android)
- [將 iOS 錯誤傳送給 IT 系統管理員](https://docs.microsoft.com/intune-user-help/send-errors-to-your-it-admin-ios)


## <a name="general-enrollment-issues"></a>一般註冊問題
所有的裝置平台都可能發生這些問題。

### <a name="device-cap-reached"></a>已到達裝置上限
**問題**：使用者於註冊期間在其裝置上收到錯誤 (例如 iOS 裝置上的 [公司入口網站暫時無法使用] 錯誤)，而且 Configuration Manager 上的 DMPdownloader.log 包含錯誤 **DeviceCapReached**。

**解決方法：**

#### <a name="check-number-of-devices-enrolled-and-allowed"></a>檢查已註冊及允許的裝置數目

1.  在 Intune 管理入口網站中，驗證指派給使用者的裝置未超過允許的 15 部上限。

2.  在 Intune 管理主控台的 [管理員] > [行動裝置管理] > [註冊規則] 下，確認已將裝置註冊限制設定為 15。

<!--- Mobile device users can delete devices at the following URL: [https://byodtestservice.azurewebsites.net/](https://byodtestservice.azurewebsites.net/). --->

系統管理員可以在 Azure Active Directory 入口網站中刪除裝置。

#### <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>若要在 Azure Active Directory 入口網站中刪除裝置：

1.  瀏覽至 [http://aka.ms/accessaad](http://aka.ms/accessaad)，或從 [https://portal.office.com](https://portal.office.com) 中選擇 [Admin] &gt; [Azure AD]。

2.  利用頁面左側連結，以您的組織識別碼登入。

3.  如果沒有帳戶，請選擇 [Register your free Azure Active Directory]\(註冊免費的 Azure Active Directory) 訂閱連結來建立 Azure 訂用帳戶。 如已有付費帳戶，應該不需要信用卡或付款。

4.  選取 [Active Directory]  ，然後選取您的組織。

5.  選取 [使用者]  索引標籤。

6.  選取您要刪除裝置的使用者。

7.  選擇 [裝置]。

8.  視需要移除裝置，例如不再使用的裝置，或具有不正確定義的裝置。

> [!NOTE]
> 
> 您可以如[使用 Microsoft Intune 中的裝置註冊管理員註冊公司所擁有的裝置](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)中所述，使用裝置註冊管理員帳戶來避免達到裝置註冊上限。
> 
> 當強制執行條件式存取原則讓特定使用者登入時，新增至裝置註冊管理員帳戶的使用者帳戶將無法完成註冊。

### <a name="company-portal-temporarily-unavailable"></a>公司入口網站暫時無法使用
**問題：**使用者在裝置上收到**公司入口網站暫時無法使用**錯誤。

**解決方法：**

1.  從裝置移除 Intune 公司入口網站應用程式。

2.  在裝置上，開啟瀏覽器，並瀏覽至 [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com)，然後嘗試使用者登入。

3.  如果使用者無法登入，請其嘗試其他網路。

4.  如果失敗，請驗證使用者的認證已正確地與 Azure Active Directory 同步處理。

5.  如果使用者成功登入，iOS 裝置會提示您安裝並註冊 Intune 公司入口網站應用程式。 在 Android 裝置上，您必須手動安裝 Intune 公司入口網站應用程式，才能重試註冊。

### <a name="mdm-authority-not-defined"></a>MDM 授權單位未定義
**問題**：使用者收到 [MDM 授權單位未定義] 錯誤。

**解決方法：**

1.  確認所設定的 MDM 授權單位適用於您使用的 Intune 服務類型，這些服務包括 Intune、Office 365 或 System Center Configuration Manager (含 Intune)。 若是 Intune，MDM 授權單位會在 [管理員] &gt; [行動裝置管理] 中設定。 若是具備 Intune 的 Configuration Manager，您會在設定 Intune 連接器時進行設定；至於 Office 365，則為 [行動裝置] 設定。

    > [!NOTE]    
    > 在 Configuration Manager 1610 版或更新版本及 Microsoft Intune 1705 版中，您可以在不需要連絡 Microsoft 支援服務的情況下變更 MDM 授權單位，且不需要取消註冊並重新註冊您現有的受管理裝置。 如需詳細資訊，請參閱[選擇錯誤的 MDM 授權單位設定時該怎麼辦](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting)。

2.  確認使用者的認證已正確地與 Azure Active Directory 同步處理，方法是檢查使用者的 UPN 是否符合 Office 365 入口網站中的 Active Directory 資訊。
    如果 UPN 與 Active Directory 資訊不符：

    1.  關閉本機伺服器上的 DirSync。

    2.  從 **Intune 帳戶入口網站** 使用者清單刪除不相符的使用者。

    3.  等候約一小時，讓 Azure 服務移除不正確的資料。

    4.  重新開啟 DirSync，然後檢查使用者現在是否已正確地同步處理。

3.  如果您使用 System Center Configuration Manager (含 Intune)，請確認使用者具有有效的雲端使用者識別碼：

    1.  開啟 SQL Management Studio。

    2.  連線到適當的 DB。

    3.  開啟資料庫資料夾，然後尋找並開啟 **CM_DBName** 資料夾，其中 DBName 是客戶資料庫的名稱。

    4.  選擇頂端的 [新增查詢] 並執行下列查詢：

        -   查看所有使用者：`select * from [CM_ DBName].[dbo].[User_DISC]`

        -   若要查看特定使用者，請使用下列查詢，其中 %testuser1% 代表您要查閱之使用者的 username@domain.com：`select * from [CM_ DBName].[dbo].[User_DISC] where User_Principal_Name0 like '%testuser1%'`

        撰寫查詢之後，請選擇 [!Execute]。
        傳回結果之後，請尋找雲端使用者識別碼。  如果找不到任何識別碼，則不會授權使用者使用 Intune。

### <a name="unable-to-create-policy-or-enroll-devices-if-the-company-name-contains-special-characters"></a>如果公司名稱包含特殊字元，就無法建立原則或註冊裝置
**問題︰**您無法建立原則或註冊裝置。

**解決方式︰**在 [Office 365 系統管理中心](https://portal.office.com/)中，移除公司名稱的特殊字元並儲存公司資訊。

### <a name="unable-to-log-in-or-enroll-devices-when-you-have-multiple-verified-domains"></a>如果您有多個以驗證的網域，您無法登入或註冊裝置
**問題**︰當您將第二個已驗證的網域新增至您的 ADFS，擁有第二個網域之使用者主要名稱 (UPN) 尾碼的使用者可能無法登入入口網站或註冊裝置。


<strong>解決方式︰</strong>透過 AD FS 2.0 利用單一登入 (SSO)，而且在其組織中有多個頂層網域以提供使用者 UPN 尾碼 (例如 @contoso.com 或 @fabrikam.com) 的 Microsoft Office 365 客戶，必須為每個尾碼部署個別的 AD FS 2.0 同盟服務執行個體。 現在有 [AD FS 2.0 的彙總套件](http://support.microsoft.com/kb/2607496)可搭配 <strong>SupportMultipleDomain</strong> 切換運作來啟用 AD FS 伺服器，以支援這個案例，而不需要額外的 AD FS 2.0 伺服器。 如需詳細資訊，請參閱[這個部落格](https://blogs.technet.microsoft.com/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/)。


## <a name="android-issues"></a>Android 的問題

### <a name="android-enrollment-errors"></a>Android 註冊錯誤

下表列出使用者在 Intune 中註冊 Android 裝置時可能會遇到的錯誤。

|錯誤訊息|問題|解決方案|
|---|---|---|
|**IT 管理員需要指派存取權**<br>您的 IT 管理員未授與您使用此應用程式的存取權。 請向您的 IT 管理員尋求協助，或稍後再試。|無法註冊裝置，因為使用者的帳戶沒有所需的授權。|使用者必須先獲指派所需的授權，才可以註冊其裝置。 這則訊息表示他們擁有的授權類型錯誤，不能用於指定的行動裝置管理授權單位。 例如，如果已指定 Intune 做為行動裝置管理授權單位，而他們使用的是 System Center 2012 R2 Configuration Manager 授權，他們就會發現這個錯誤。<br><br>相關資訊請參閱如何[將 Intune 授權指派給使用者帳戶](/intune/licenses-assign)。
|**IT 系統管理員需要設定 MDM 授權單位**<br>您的 IT 管理員似乎尚未設定 MDM 授權單位。 請向您的 IT 管理員尋求協助，或稍後再試。|尚未定義行動裝置管理授權單位。|尚未在 Intune 中指定行動裝置管理授權單位。 如需相關資訊，請參閱如何[設定行動裝置管理授權單位](/intune/mdm-authority-set)。|


### <a name="devices-fail-to-check-in-with-the-intune-service-and-display-as-unhealthy-in-the-intune-admin-console"></a>裝置無法使用 Intune 服務簽入，並在 Intune 管理主控台中顯示為「狀況不良」
**問題：**一些執行 Android 版本 4.4.x 和 5.x 的 Samsung 裝置可能會停止使用 Intune 服務來簽入。 如果裝置未簽入：

- 它們就無法從 Intune 服務接收原則、應用程式及遠端命令。
- 它們會在系統管理員主控台中顯示其管理狀態為**狀況不良**。
- 受條件式存取原則所保護的使用者可能會遺失對公司資源的存取權。

Samsung 已確認 Samsung Smart Manager 軟體 (隨附於某些 Samsung 裝置上) 會停用 Intune 公司入口網站及其元件。 當公司入口網站處於已停用狀態時，就不能在背景中執行，因而無法連絡 Intune 服務。

**解決方法 1：**

告知使用者手動啟動公司入口網站應用程式。 一旦應用程式重新啟動之後，裝置就會使用 Intune 服務進行簽入。

> [!IMPORTANT]
> 手動開啟公司入口網站應用程式是暫時性解決方案，因為 Samsung Smart Manager 可能會再次停用公司入口網站應用程式。

**解決方法 2：**

告訴使用者嘗試升級到 Android 6.0。 停用問題在 Android 6.0 裝置上不會發生。 若要檢查是否有可用的更新，使用者可以前往 [設定] > [關於裝置] > [手動下載更新]，然後依照裝置上的提示執行。

**解決方法 3：**

如果解決方案 2 無法運作，請使用者遵循下列步驟，好讓 Smart Manager 排除公司入口網站應用程式：

1. 在裝置上啟動 Smart Manager 應用程式。

   ![選取裝置上的 Smart Manager 圖示](./media/smart-manager-app-icon.png)

2. 選擇 [電池] 磚。

   ![選取 [電池] 磚](./media/smart-manager-battery-tile.png)

3. 在 [應用程式省電] 或 [應用程式最佳化] 下方，選取 [詳細資料]。

   ![在 [應用程式省電] 或 [應用程式最佳化] 下方選取 [詳細資料]](./media/smart-manager-app-power-saving-detail.png)

4. 從應用程式清單中選擇 [公司入口網站]。

   ![從應用程式清單中選取 [公司入口網站]](./media/smart-manager-company-portal.png)

5. 選擇 [關閉]。

   ![從 [應用程式最佳化] 對話方塊中選取 [關閉]](./media/smart-manager-app-optimization-turned-off.png)

6. 在 [應用程式省電] 或 [應用程式最佳化] 下方，確認公司入口網站已關閉。

   ![確認公司入口網站已關閉](./media/smart-manager-verify-comp-portal-turned-off.png)


### <a name="profile-installation-failed"></a>設定檔安裝失敗
**問題**：使用者的 Android 裝置收到「設定檔安裝失敗」錯誤。

**解決方法：**

1.  確認已將您使用之 Intune 服務版本的適當授權指派給使用者。

2.  確認未向其他 MDM 提供者註冊裝置，而且裝置尚未安裝管理設定檔。

3.  確認 Chrome (適用於 Android) 是預設瀏覽器，而且已啟用 Cookie。

### <a name="android-certificate-issues"></a>Android 憑證問題

**問題**：使用者在裝置上收到下列訊息：「您無法登入，因為您的裝置缺少必要的憑證」。

**解決方法 1**：

使用者可能可以遵循[您的裝置遺漏必要的憑證](/intune-user-help/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator)中的指示來擷取遺漏的憑證。 如果仍然發生錯誤，請嘗試＜解決方法 2＞。

**解決方法 2**：

如果使用者輸入其公司認證後仍看到遺漏憑證的錯誤，並被重新導向至同盟登入，表示您的 Active Directory 同盟服務 (AD FS) 伺服器可能遺失中繼憑證。

發生憑證錯誤是因為 Android 裝置需要中繼憑證包含在 [SSL Server Hello](https://technet.microsoft.com/library/cc783349.aspx) 中。 目前，預設的 AD FS 伺服器或 WAP - AD FS Proxy 伺服器安裝在對 SSL 用戶端 Hello 的 SSL 伺服器 Hello 回應中，只傳送 AD FS 服務 SSL 憑證。

若要修正問題，請按照下列步驟將憑證匯入 AD FS 伺服器或 Proxy 上的 Computers Personal Certificates：

1.  在 ADFS 伺服器和 Proxy 伺服器上，以滑鼠右鍵按一下 [開始] > [執行] > [certlm.msc]。 這會啟動 [本機電腦憑證管理主控台]。
2.  展開 [個人] 並選擇 [憑證]。
3.  尋找您的 AD FS 服務通訊的憑證 (公開簽署的憑證)，然後按兩下來檢視其內容。
4.  選擇 [憑證路徑] 索引標籤來查看憑證的父憑證。
5.  在每個父憑證上，選擇 [檢視憑證]。
6.  選擇 [詳細資料] 索引標籤 > [複製到檔案...]。
7.  遵循精靈的提示，將父憑證的公開金鑰匯出或儲存到想要的檔案位置。
8.  以滑鼠右鍵按一下 [憑證] > [所有工作] > [匯入]。
9.  遵循精靈的提示，將父憑證匯入至 [本機電腦]\[個人]\[憑證]。
10. 重新啟動 AD FS 伺服器。
11. 在您的所有 AD FS 和 Proxy 伺服器上重複上述步驟。

若要驗證憑證是否正確安裝，您可以使用 [https://www.digicert.com/help/](https://www.digicert.com/help/) 上的診斷工具。 在 [Server Address] \(伺服器位址\) 方塊中，輸入您 ADFS 伺服器的 FQDN (即 sts.contso.com)，然後按一下 [Check Server]\(檢查伺服器\)。

**驗證憑證已正確安裝**：

下列步驟僅描述可用來驗證憑證以正確安裝之數種方法和工具的其中一種。

1. 移至[免費的 Digicert 工具](ttps://www.digicert.com/help/)。
2. 輸入您的 AD FS 伺服器的完整網域名稱 (例如，sts.contoso.com) 並選取 [CHECK SERVER]。

如果伺服器憑證已正確安裝，您就會在結果中看到所有核取記號。 如果上述問題存在，您會看到報告的 [Certificate Name Matches] 和 [SSL Certificate is correctly Installed] 區段中有紅色 X。


## <a name="ios-issues"></a>iOS 問題

### <a name="ios-enrollment-errors"></a>iOS 註冊錯誤
下表列出使用者在 Intune 中註冊 iOS 裝置時可能會遇到的錯誤。

|錯誤訊息|問題|解決方案|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|NoEnrollmentPolicy|找不到註冊原則|請檢查所有註冊必要條件 (例如 APNs 憑證)，並確認已設定並啟用 [iOS as a platform]\(iOS 即平台)。 如需指示，請參閱[設定 iOS 和 Mac 裝置管理](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)。|
|DeviceCapReached|已經註冊過多行動裝置。|註冊其他行動裝置之前，使用者必須先從公司入口網站移除目前已註冊的其中一部行動裝置。 請參閱您所使用的裝置類型的指示︰[Android](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android)、[iOS](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-ios)、[Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-windows)。|
|APNSCertificateNotValid|可讓行動裝置與貴公司網路通訊的憑證發生問題。<br /><br />|Apple Push Notification Service (APNs) 是可用來連接已註冊 iOS 裝置的管道。 若未執行取得 APNs 憑證的步驟，或者 APNs 憑證已過期，則嘗試註冊將會失敗，且會出現此訊息。<br /><br />如需如何設定使用者的資訊，請檢閱[同步處理 Active Directory 並將使用者新增至 Intune](/intune/users-permissions-add) 和[組織使用者和裝置](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5)。|
|AccountNotOnboarded|可讓行動裝置與貴公司網路通訊的憑證發生問題。<br /><br />|Apple Push Notification Service (APNs) 是可用來連接已註冊 iOS 裝置的管道。 若未執行取得 APNs 憑證的步驟，或者 APNs 憑證已過期，則嘗試註冊將會失敗，且會出現此訊息。<br /><br />如需詳細資訊，請檢閱[使用 Microsoft Intune 設定 iOS 和 Mac 管理](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)。|
|DeviceTypeNotSupported|使用者可能嘗試使用非 iOS 裝置進行註冊。 您嘗試註冊的行動裝置類型不受支援。<br /><br />確認裝置正在執行 iOS 8.0 版或更新版本。<br /><br />|確定您的使用者裝置正在執行 iOS 8.0 版或更新版本。|
|UserLicenseTypeInvalid|裝置無法註冊，因為使用者帳戶還不是必要使用者群組的成員。<br /><br />|使用者必須是正確使用者群組的成員，才可以註冊裝置。 這則訊息表示他們擁有的授權類型錯誤，不能用於指定的行動裝置管理授權單位。 例如，如果已指定 Intune 做為行動裝置管理授權單位，而他們使用的是 System Center 2012 R2 Configuration Manager 授權，他們就會發現這個錯誤。<br /><br />如需詳細資訊，請檢閱下列內容：<br /><br />檢閱[使用 Microsoft Intune 設定 iOS 和 Mac 管理](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)，以及[同步處理 Active Directory 並將使用者新增至 Intune](/intune/users-permissions-add) 和[組織使用者和裝置](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5)，以取得如何設定使用者的資訊。|
|MdmAuthorityNotDefined|尚未定義行動裝置管理授權單位。<br /><br />|尚未在 Intune 中指定行動裝置管理授權單位。<br /><br />檢閱[開始使用 Microsoft Intune 30 天試用版](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune)中＜步驟 6：註冊行動裝置並安裝應用程式＞一節中的項目 #1。|

### <a name="devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>裝置處於非使用狀態或管理員主控台無法與它們通訊
**問題︰**iOS 裝置未簽入 Intune 服務。 裝置必須定期簽入服務，才能維護受保護公司資源的存取權。 如果裝置未簽入：

- 它們就無法從 Intune 服務接收原則、應用程式及遠端命令。
- 它們會在系統管理員主控台中顯示其管理狀態為**狀況不良**。
- 受條件式存取原則所保護的使用者可能會遺失對公司資源的存取權。

**解決方式︰**與您的使用者共用下列解決方法，協助他們重新取得公司資源的存取權。

當使用者啟動 iOS 公司入口網站應用程式時，它會通知您裝置是否與 Intune 失去連絡。 如果偵測到沒有連絡，它會自動嘗試與 Intune 同步處理以重新連線，使用者會看到**正在嘗試同步...** 內嵌的通知。

  ![正在嘗試同步通知](./media/ios_cp_app_trying_to_sync_notification.png)

如果同步處理成功，您會在 iOS 公司入口網站應用程式中看到**同步處理成功**內嵌通知，指出裝置處於狀況良好狀態。

  ![同步處理成功通知](./media/ios_cp_app_sync_successful_notification.png)

如果同步處理失敗，使用者會在 iOS 公司入口網站應用程式中看到**無法同步**內嵌通知。

  ![無法同步通知](./media/ios_cp_app_unable_to_sync_notification.png)

若要修正此問題，使用者必須選取位在**無法同步**通知右邊的 [設定] 按鈕。 [設定] 按鈕會將使用者帶到公司存取設定流程畫面，他們可以在這裡遵循提示以註冊裝置。

  ![公司存取設定畫面](./media/ios_cp_app_company_access_setup.png)

註冊完成後，裝置會回復到正常狀態，並重新取得公司資源的存取權。

### <a name="verify-ws-trust-13-is-enabled"></a>確認已啟用 WS-Trust 1.3
**問題**：裝置註冊計劃 (DEP) 無法註冊 iOS 裝置

註冊具有使用者親和性的裝置註冊計劃裝置，必須啟用 WS-Trust 1.3 使用者名稱/混合端點，才能要求使用者權杖。 Active Directory 預設會啟用此端點。 您可以使用 Get-AdfsEndpoint PowerShell Cmdlet 並尋找 trust/13/UsernameMixed 端點，來取得已啟用的端點清單。 例如：

      Get-AdfsEndpoint -AddressPath “/adfs/services/trust/13/UsernameMixed”

如需詳細資訊，請參閱 [Get-AdfsEndpoint 文件 (英文)](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

如需詳細資訊，請參閱[保護 Active Directory 同盟服務的最佳做法](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/operations/best-practices-securing-ad-fs)。 如果您使用 ADFS 或第三方識別廠商，並需要協助以判斷 WS-Trust 1.3 使用者名稱/混合是否已在識別同盟提供者中啟用，請連絡 Microsoft 支援服務。


### <a name="profile-installation-failed"></a>設定檔安裝失敗
**問題**：使用者的 iOS 裝置收到「設定檔安裝失敗」錯誤。

### <a name="troubleshooting-steps-for-failed-profile-installation"></a>設定檔安裝失敗的疑難排解步驟

1.  確認已將您使用之 Intune 服務版本的適當授權指派給使用者。

2.  確認未向其他 MDM 提供者註冊裝置，而且裝置尚未安裝管理設定檔。

3.  巡覽至 [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com)，然後在系統提示時嘗試安裝設定檔。

4.  確認適用於 iOS 的 Safari 是預設瀏覽器，而且已啟用 Cookie。

### <a name="enrolled-ios-device-doesnt-appear-in-console-when-using-system-center-configuration-manager-with-intune"></a>使用 System Center Configuration Manager (含 Intune) 時，已註冊的 iOS 裝置不會出現在主控台
**問題︰**使用者會註冊 iOS 裝置，但它不會出現在 Configuration Manager 管理員主控台。 裝置並未指出它已註冊。 可能的原因：

- 您 Configuration Manager 網站中的 Microsoft Intune Connector 沒有和 Intune 服務通訊。
- 資料探索管理員 (ddm) 元件或狀態管理員 (statmgr) 元件沒有處理來自 Intune 服務的訊息。
- 您可能已從一個帳戶下載 MDM 憑證，然後將其用於另一個帳戶。


**解決方法：**檢閱下列記錄檔以尋找可能的錯誤：

- dmpdownloader.log
- ddm.log
- statmgr.log

很快就會新增和要在這些記錄檔中尋找哪些項目有關的範例。


## <a name="issues-when-using-system-center-configuration-manager-with-intune"></a>使用具有 Intune 的 System Center Configuration Manager 時發生問題
### <a name="mobile-devices-disappear"></a>行動裝置消失
**問題：** 成功向 Configuration Manager 註冊行動裝置之後，該裝置會從行動裝置集合中消失，但仍有管理設定檔並列於 CSS 閘道中。

**解決方式**：發生這個問題的原因可能是您具有移除非加入網域裝置的自訂處理序，或使用者嘗試從訂用帳戶移除裝置。 若要驗證及查看哪個處理序或使用者帳戶從 Configuration Manager 主控台移除裝置，請執行下列步驟。

#### <a name="check-how-device-was-removed"></a>檢查裝置的移除方式

1.  在 Configuration Manager 管理主控台中，選取 [監視] &gt; [系統狀態] &gt; [狀態訊息查詢]。

2.  以滑鼠右鍵按一下 [手動刪除的集合成員資源]，然後選取 [顯示訊息]。

3.  選擇適當的時間/日期或 [過去 12 小時]。

4.  尋找有問題的裝置並檢閱裝置的移除方式。 下列範例顯示帳戶 SCCMInstall 已透過未知的應用程式刪除裝置。

    ![裝置刪除診斷的螢幕擷取畫面](./media/CM_With_Intune_Unknown_App_Deleted_Device.jpg)

5.  檢查 Configuration Manager 未排定任何可能會自動清除非網域、行動或相關裝置的工作、指令碼或其他處理序。




### <a name="other-ios-enrollment-errors"></a>其他 iOS 註冊錯誤
[Troubleshooting iOS device enrollment problems in Microsoft Intune](https://support.microsoft.com/help/4039809/troubleshooting-ios-device-enrollment-in-intune) (針對 Microsoft Intune 中的 iOS 裝置註冊問題進行疑難排解) 這份文件提供 iOS 註冊錯誤清單。

## <a name="pc-issues"></a>電腦問題


|錯誤訊息|問題|解決方案|
|---|---|---|
|**IT 管理員需要指派存取權**<br>您的 IT 管理員未授與您使用此應用程式的存取權。 請向您的 IT 管理員尋求協助，或稍後再試。|無法註冊裝置，因為使用者的帳戶沒有所需的授權。|使用者必須先獲指派所需的授權，才可以註冊其裝置。 這則訊息表示他們擁有的授權類型錯誤，不能用於指定的行動裝置管理授權單位。 例如，如果已指定 Intune 做為行動裝置管理授權單位，而他們使用的是 System Center 2012 R2 Configuration Manager 授權，他們就會發現這個錯誤。<br>參閱[如何將 Intune 授權指派至使用者帳戶](https://docs.microsoft.com/intune/licenses-assign)的相關資訊。|



### <a name="the-machine-is-already-enrolled---error-hr-0x8007064c"></a>電腦已註冊 - 錯誤 hr 0x8007064c
**問題 ︰**註冊失敗，並顯示**電腦已註冊**錯誤。 註冊記錄檔會顯示錯誤 **hr 0x8007064c**。

這可能是因為電腦先前已註冊，或具有已註冊之電腦的複製映像。 上一個帳戶的帳戶憑證仍存在於電腦上。



**解決方法：**

1. 從 [開始] 功能表，鍵入 [執行] -> [MMC]。
1. 選擇 [檔案] > [Add/ Remove Snap-ins]\(新增/移除嵌入式管理單元)。
1. 按兩下 [憑證]，並選擇 [電腦帳戶] > [下一步]，然後選取 [本機電腦]。
1. 按兩下 [憑證 (本機電腦)]，然後選擇 [個人/憑證]。
1. 尋找 Sc_Online_Issuing 發出的 Intune 憑證，然後在它出現時刪除。
1. 如果下列登錄機碼存在，請刪除它︰**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey** 和所有子機碼。
1. 嘗試重新註冊。
1. 如果仍然無法註冊電腦，請尋找並刪除此機碼 (如果它存在)︰**KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95**。
1. 嘗試重新註冊。

    > [!IMPORTANT]
    > 此節、方法或工作包含告訴您如何修改登錄的步驟。 然而，如果您不當修改登錄，可能會發生嚴重的問題。 因此，請務必小心遵循下列步驟。 為加強保護，請在修改登錄之前先加以備份。 之後如果發生問題，您還可以還原登錄。
    > 如需如何備份和還原登錄的詳細資訊，請參閱[如何備份和還原 Windows 中的登錄](https://support.microsoft.com/kb/322756)

## <a name="general-enrollment-error-codes"></a>一般註冊錯誤代碼

|錯誤碼|可能的問題|建議的解決方式|
|--------------|--------------------|----------------------------------------|
|0x80CF0437 |用戶端電腦上的時鐘未設定成正確的時間。|確定用戶端電腦上的時鐘和時區已設成正確的時間和時區。|
|0x80240438、0x80CF0438、0x80CF402C|無法連線至 Intune 服務。 請檢查用戶端 Proxy 設定。|確認 Intune 支援用戶端電腦上的 Proxy 設定，而且用戶端電腦可以存取網際網路。|
|0x80240438、0x80CF0438|未設定 Internet Explorer 和本機系統中的 Proxy 設定。|無法連線至 Intune 服務。 請檢查用戶端 Proxy 設定，並確認 Intune 所支援的用戶端電腦上的 Proxy 組態，且用戶端電腦可以存取網際網路。|
|0x80043001、0x80CF3001、0x80043004、0x80CF3004|註冊套件已過期。|從 [系統管理] 工作區下載並安裝最新的用戶端軟體套件。|
|0x80043002、0x80CF3002|帳戶處於維護模式。|您不能在帳戶處於維護模式時註冊新的用戶端電腦。 若要檢視您的帳戶設定，請登入您的帳戶。|
|0x80043003、0x80CF3003|已刪除帳戶。|確認您的帳戶和 Intune 訂閱仍然有效。 若要檢視您的帳戶設定，請登入您的帳戶。|
|0x80043005、0x80CF3005|已淘汰用戶端電腦。|等待幾個小時，並從電腦移除所有的舊版用戶端軟體，然後再次嘗試安裝用戶端軟體。|
|0x80043006、0x80CF3006|已達到帳戶允許的基座數目上限。|貴組織必須購買額外的基座，您才可以在服務中註冊更多用戶端電腦。|
|0x80043007、0x80CF3007|在與安裝程式相同的資料夾中找不到憑證檔案。|在開始安裝之前先解壓縮所有檔案。 請勿重新命名任何已解壓縮的檔案或改變其位置：所有檔案都必須位於同一個資料夾，否則安裝將會失敗。|
|0x8024D015、0x00240005、0x80070BC2、0x80070BC9、0x80CFD015|由於用戶端電腦仍在等待重新啟動，因此無法安裝軟體。|重新啟動電腦，然後再次嘗試安裝用戶端軟體。|
|0x80070032|用戶端電腦不符合安裝用戶端軟體的一或多個必要條件。|確定用戶端電腦已安裝所有必要更新，然後再次嘗試安裝用戶端軟體。|
|0x80043008、0x80CF3008|無法啟動 Microsoft Online Management Updates 服務。|連絡 Microsoft 支援服務 (如[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)所述)。|
|0x80043009、0x80CF3009|用戶端電腦已註冊到服務中。|您必須先淘汰用戶端電腦，才能重新將它註冊到服務中。|
|0x8004300B、0x80CF300B|用戶端軟體安裝套件無法執行，因為不支援用戶端上執行的 Windows 版本。|Intune 不支援用戶端電腦上執行的 Windows 版本。|
|0xAB2|Windows Installer 無法存取自訂動作的 VBScript 執行階段。|這個錯誤是由以動態連結程式庫 (DLL) 為基礎的自訂動作所造成。 在為 DLL 疑難排解時，您可能必須使用 [Microsoft 支援服務 KB198038：實用的封裝與部署工具](https://support.microsoft.com/kb/198038)中所述的工具。|
|0x80cf0440|與服務端點的連線已終止。|試用或付費帳戶已暫止。 建立新的試用或付費帳戶，然後重新註冊。|




### <a name="next-steps"></a>接下來的步驟
如果此疑難排解資訊對您沒有幫助，請連絡 Microsoft 支援服務 (如[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)中所述)。
