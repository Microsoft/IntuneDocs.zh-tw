---
title: "疑難排解裝置註冊的問題 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解如何疑難排解裝置註冊的問題。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c324c74e-e225-40ad-88b7-72a6d9ea09b5
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: 8d56b6600ca86faabbb50d29405969385eb29940
ms.lasthandoff: 02/15/2017


---

# <a name="troubleshoot-device-enrollment-in-intune"></a>Intune 的裝置註冊疑難排解

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

本主題提供裝置註冊問題的疑難排解建議。 如果此資訊無法解決您的問題，請參閱[如何取得 Microsoft Intune 支援](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)，以尋找更多方法來取得協助。


## <a name="initial-troubleshooting-steps"></a>初始疑難排解步驟

在您開始疑難排解問題之前，請確定您的 Intune 設定正確，可以註冊。 如需每個平台的註冊步驟連結，請參閱[註冊 Android 與 Standard Knox 裝置](/intune-azure/enroll-devices/enroll-android-and-knox-standard-devices.md)。

您所管理的裝置使用者可以收集註冊與診斷記錄檔，以供您檢閱。 提供有關收集記錄檔使用者指示之處如下：

- [將 Android 註冊錯誤傳送給 IT 系統管理員](https://docs.microsoft.com/intune/enduser/send-enrollment-errors-to-your-it-admin-android)
- [將 iOS 錯誤傳送給 IT 系統管理員](https://docs.microsoft.com/intune/enduser/send-errors-to-your-it-admin-ios)

## <a name="general-enrollment-issues"></a>一般註冊問題
所有的裝置平台都可能發生這些問題。

### <a name="device-cap-reached"></a>已到達裝置上限
**問題**：使用者於註冊期間在其裝置上收到錯誤 (例如 iOS 裝置上的 [公司入口網站暫時無法使用] 錯誤)，而且 Configuration Manager 上的 DMPdownloader.log 包含錯誤 **DeviceCapReached**。

**解決方法：**

#### <a name="check-number-of-devices-enrolled-and-allowed"></a>檢查已註冊及允許的裝置數目

在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。 在 Azure 入口網站的 [Intune] 刀鋒視窗中，選取 [註冊裝置]  >  [註冊限制]，確定使用者未超過 15 部指派裝置數上限。

<!--- Mobile device users can delete devices at the following URL: [https://byodtestservice.azurewebsites.net/](https://byodtestservice.azurewebsites.net/). --->

系統管理員可以在 Azure Active Directory 入口網站中刪除裝置。

#### <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>若要在 Azure Active Directory 入口網站中刪除裝置：

1.  瀏覽至 [http://aka.ms/accessaad](http://aka.ms/accessaad)，或從 [https://portal.office.com](https://portal.office.com) 中選擇 [系統管理] &gt; [Azure AD]。

2.  利用頁面左側連結，以您的組織識別碼登入。

3.  如果您沒有 Azure 訂用帳戶，請建立帳戶。 如果您有付費帳戶，應該不需要信用卡或付款 (請選擇 [Register your free Azure Active Directory (註冊免費的 Azure Active Directory)] 訂閱連結)。

4.  選取 [Active Directory]  ，然後選取您的組織。

5.  選取 [使用者]  索引標籤。

6.  選取您要刪除裝置的使用者。

7.  選擇 [裝置]。

8.  視需要移除裝置，例如不再使用的裝置，或具有不正確定義的裝置。

> [!NOTE]

> 如[使用裝置註冊管理員註冊裝置](/intune-azure/enroll-devices/enroll-devices-using-device-enrollment-manager.md)所述，您可以使用裝置註冊管理員避開裝註冊限制。
>
> 如有對新增到裝置註冊管理員群組中的特定使用者帳戶實施條件式存取原則，則該特定使用者登入將無法完成註冊。

### <a name="company-portal-temporarily-unavailable"></a>公司入口網站暫時無法使用
**問題**：使用者在裝置上收到 [公司入口網站暫時無法使用] 錯誤。

**解決方法：**

1.  從裝置移除 Intune 公司入口網站應用程式。

2.  在裝置上開啟瀏覽器，瀏覽至 [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com)，然後嘗試使用者登入。

3.  如果使用者無法登入，請他們嘗試其他網路。

4.  如果失敗，請驗證使用者的認證已正確地與 Azure Active Directory 同步處理。

5.  如果使用者成功登入，iOS 裝置會提示您安裝並註冊 Intune 公司入口網站應用程式。 在 Android 裝置上，您必須手動安裝 Intune 公司入口網站應用程式，才能重試註冊。

### <a name="mdm-authority-not-defined"></a>MDM 授權單位未定義
**問題**：使用者收到 [MDM 授權單位未定義] 錯誤。

**解決方法：**

1.  確認您要使用的 Intune 服務 (亦即 Intune、Office 365 或 Intune 的 System Center Configuration Manager) 類型已正確設定了 MDM 授權單位。 如需指示，請參閱[設定行動裝置管理授權單位](https://docs.microsoft.com/en-us/intune-azure/enroll-devices/set-mdm-authority)。

    > [!NOTE]
    > 設定 MDM 授權單位之後，您只能遵循[如何取得 Microsoft Intune 支援](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)中所述來連絡支援人員以進行變更。

2.  確認使用者的認證已正確地與 Azure Active Directory 同步處理，方式是檢查其 UPN 是否符合帳戶入口網站中的 Active Directory 資訊。
    如果 UPN 與 Active Directory 資訊不符：

    1.  關閉本機伺服器上的 DirSync。

    2.  從 **Intune 帳戶入口網站** 使用者清單刪除不相符的使用者。

    3.  等候約一小時，讓 Azure 服務移除不正確的資料。

    4.  重新開啟 DirSync，然後檢查使用者現在是否已正確地同步處理。

3.  如果您使用 System Center Configuration Manager (含 Intune)，請確認使用者具有有效的雲端使用者識別碼：

    1.  開啟 SQL Management Studio。

    2.  連線到適當的資料庫。

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


**解決方式**︰透過 AD FS 2.0 利用單一登入 (SSO)，而且在其組織中有多個頂層網域以提供使用者 UPN 尾碼 (例如 @contoso.com 或 @fabrikam.com)) 的 Microsoft Office 365 客戶，必須為每個尾碼部署個別的 AD FS 2.0 同盟服務執行個體。  現在有 [AD FS 2.0 的彙總套件](http://support.microsoft.com/kb/2607496)可搭配 **SupportMultipleDomain** 切換運作來啟用 AD FS 伺服器，以支援這個案例，而不需要額外的 AD FS 2.0 伺服器。 如需詳細資訊，請參閱[這個部落格](https://blogs.technet.microsoft.com/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/)。


## <a name="android-issues"></a>Android 的問題
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

要求您的使用依照[您的裝置遺漏必要的憑證](https://docs.microsoft.com/intune/enduser/your-device-is-missing-a-required-certificate-landing-android#your-device-is-missing-a-certificate-required-by-your-it-administrator)中的指示解決問題。 如果使用者依照指示進行之後仍出現錯誤，請嘗試「解決方法 2」。

**解決方法 2**：

如果使用者輸入其公司認證並被重新導向至聯盟登入體驗之後，仍看到遺漏憑證的錯誤，表示您的 Active Directory 同盟服務 (AD FS) 伺服器可能遺失中繼憑證。

出現憑證錯誤是因為 Android 裝置需要在 [SSL Server hello](https://technet.microsoft.com/library/cc783349.aspx) 中包含中繼憑證，但目前預設的 AD FS 伺服器或 AD FS Proxy 伺服器安裝只會在對 SSL Client hello 的 SSL Server hello 回應中傳送 AD FS 的服務 SSL 憑證。

若要修正問題，請按照下列步驟將憑證匯入 AD FS 伺服器或 Proxy 上的 Computers Personal Certificates：

1.    在 ADFS 和 Proxy 伺服器上，以滑鼠右鍵按一下 [開始] 按鈕，選擇 [執行] 並輸入 **certlm.msc**，以啟動本機電腦的「憑證管理」主控台。
2.    展開 [個人] 並選取 [憑證]。
3.    尋找您的 AD FS 服務通訊的憑證 (公開簽署的憑證)，然後按兩下來檢視其內容。
4.    選取 [憑證路徑] 索引標籤來查看憑證的父憑證。
5.    在每個父憑證上，選取 [檢視憑證]。
6.    按一下 [詳細資料] 索引標籤，然後按一下 [複製到檔案]。
7.    按照精靈的提示將憑證的公開金鑰匯出或儲存到想要的檔案位置。
8.    以滑鼠右鍵按一下 [憑證]，選取 [所有工作] > [匯入]並按照精靈的提示進行，以將在步驟 3 匯出的父憑證匯入到 Computer\Personal\Certificates。
9.    重新啟動 AD FS 伺服器。
10.    在您的所有 AD FS 和 Proxy 伺服器上重複上述步驟。
使用者現在應該能夠在 Android 裝置上登入公司入口網站。

**驗證憑證已正確安裝**：

下列步驟僅描述可用來驗證憑證以正確安裝之數種方法和工具的其中一種。

1. 移至[免費的 Digicert 工具](ttps://www.digicert.com/help/)。
2. 輸入您的 AD FS 伺服器的完整網域名稱 (例如，sts.contoso.com) 並選取 [CHECK SERVER]。

如果伺服器憑證已正確安裝，您就會在結果中看到所有核取記號。 如果上述問題存在，您會看到報告的 [Certificate Name Matches] 和 [SSL Certificate is correctly Installed] 區段中有紅色 X。


## <a name="ios-issues"></a>iOS 問題

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

### <a name="profile-installation-failed"></a>設定檔安裝失敗
**問題**：使用者的 iOS 裝置收到「設定檔安裝失敗」錯誤。

### <a name="troubleshooting-steps-for-failed-profile-installation"></a>設定檔安裝失敗的疑難排解步驟

1.  確認已將您使用之 Intune 服務版本的適當授權指派給使用者。

2.  確認未向其他 MDM 提供者註冊裝置，而且裝置尚未安裝管理設定檔。

3.  請瀏覽至 [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com)，並在出現提示時嘗試安裝設定檔。

4.  確認適用於 iOS 的 Safari 是預設瀏覽器，而且已啟用 Cookie。

### <a name="enrolled-ios-device-doesnt-appear-in-console-when-using-system-center-configuration-manager-with-intune"></a>使用 System Center Configuration Manager (含 Intune) 時，已註冊的 iOS 裝置不會出現在主控台
**問題︰**使用者會註冊 iOS 裝置，但它不會出現在 Configuration Manager 管理員主控台。 裝置並未指出它已註冊。 可能的原因：

- 您可能已將 Intune 連接器註冊到一個帳戶，然後將它註冊到另一個帳戶。
- 您可能已從一個帳戶下載 MDM 憑證，然後將其用於另一個帳戶。


**解決方式：**執行下列步驟：

1. 在 Windows Intune 連接器內部停用 iOS。
    1. 以滑鼠右鍵按一下 Intune 訂閱，然後選取 [內容]。
    1. 在 [iOS] 索引標籤，取消核取 [啟用 iOS 註冊]。



2. 在 SQL 中，在 CAS DB 上執行下列步驟

    1. 更新 SC_ClientComponent_Property set Value2 = '' where Name like '%APNS%'
    1. 從 MDMPolicy where PolicyType = 7 刪除
    1. 從 MDMPolicyAssignment where PolicyType = 7 刪除
    1. 更新 SC_ClientComponent_Property set Value2 = '' where Name like '%APNS%'
    1. 從 MDMPolicy where PolicyType = 11 刪除
    1. 從 MDMPolicyAssignment where PolicyType = 11 刪除
    1. 刪除 Drs_Signals
3. 重新啟動 SMS Executive 服務，或重新啟動 CM 伺服器。

4. 取得新的 APN 憑證並予以上傳。 若要執行此動作，請在 Configuration Manager 左窗格中的 Intune 訂閱上按一下滑鼠右鍵。 選取 [建立 APN 憑證要求] 並遵循指示。
5. 
## <a name="issues-when-using-system-center-configuration-manager-with-intune"></a>使用具有 Intune 的 System Center Configuration Manager 時發生問題

### <a name="mobile-devices-disappear"></a>行動裝置消失

**問題：**成功向 Configuration Manager 註冊行動裝置之後，該裝置會從行動裝置集合中消失，但仍有管理設定檔，並會繼續列名於 CSS 閘道中。

**解決方法：**您如有自訂處理序會移除未加入網域的裝置，或使用者淘汰了訂用帳戶中的裝置，即可能發生此問題。 若要驗證及檢查哪個處理序或使用者帳戶從 Configuration Manager 主控台移除了裝置，請執行下列步驟，確認裝置的移除方式。

1.  在 Configuration Manager 系統管理主控台中，選取 [監視] &gt; [系統狀態] &gt; [狀態訊息查詢]。

2.  以滑鼠右鍵按一下 [手動刪除的集合成員資源]，然後選取 [顯示訊息]。

3.  選擇適當的時間/日期或 [過去 12 小時]。

4.  尋找有問題的裝置並檢閱裝置的移除方式。 下列範例顯示帳戶 SCCMInstall 透過未知的應用程式刪除了裝置。

    ![裝置刪除診斷的螢幕擷取畫面](./media/cm-with-intune-unknown-app-deleted-device.png)

5.  確認 Configuration Manager 未排程任何可能會自動清除不屬於網域、行動裝置或相關裝置的工作、指令碼或其他處理序。




### <a name="other-ios-enrollment-errors"></a>其他 iOS 註冊錯誤

您可以檢視可能會對使用者顯示的 [iOS 註冊錯誤](https://docs.microsoft.com/intune/enduser/you-see-errors-while-trying-to-enroll-your-device-in-intune-ios)清單。 此清單提供的資訊包括可能會對使用者顯示的錯誤訊息，以及您解決此問題所要採取的步驟。

## <a name="pc--issues"></a>電腦問題

### <a name="the-machine-is-already-enrolled---error-hr-0x8007064c"></a>電腦已註冊 - 錯誤 hr 0x8007064c
**問題 ︰**註冊失敗，並顯示**電腦已註冊**錯誤。 註冊記錄檔會顯示錯誤 **hr 0x8007064c**。

此錯誤能是因為電腦先前已經註冊過，或具有已經註冊之電腦的複製映像。 上一個帳戶的帳戶憑證仍存在於電腦上。

**解決方法：**

1.. 從 [開始] 功能表，鍵入 [執行] -> [MMC]。
1. 選擇 [檔案] > [Add/ Remove Snap-ins] (新增/移除嵌入式管理單元)。
1. 按兩下 [憑證]，並選擇 [電腦帳戶] > [下一步]，然後選取 [本機電腦]。
1. 按兩下 [憑證 (本機電腦)]，然後選擇 [個人/憑證]。
1. 尋找 Sc_Online_Issuing 發出的 Intune 憑證，然後在它出現時刪除。
1. 如果下列登錄機碼存在，請刪除它︰**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey** 和所有子機碼。
1. 嘗試重新註冊。
1. 如果仍然無法註冊電腦，請尋找並刪除此機碼 (如果它存在)︰**KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95**。
1. 嘗試重新註冊。

    > [!IMPORTANT]
    > 此節、方法或工作包含告訴您如何修改登錄的步驟。 然而，如果您不當修改登錄，可能會發生嚴重的問題。 因此，請務必小心遵循下列步驟。 為加強保護，請在修改登錄之前先加以備份。 之後如果發生問題，您還可以還原登錄。
    > 如需如何備份及還原登錄的詳細資訊，請參閱[如何備份及還原 Windows 中的登錄](https://support.microsoft.com/en-us/kb/322756)。

## <a name="general-enrollment-error-codes"></a>常見註冊錯誤代碼

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
|0x80043008、0x80CF3008|無法啟動 Microsoft Online Management Updates 服務。|連絡 Microsoft 支援服務 (如[如何取得 Microsoft Intune 支援](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)所述)。|
|0x80043009、0x80CF3009|用戶端電腦已註冊到服務中。|您必須先淘汰用戶端電腦，才能重新將它註冊到服務中。|
|0x8004300B、0x80CF300B|用戶端軟體安裝套件無法執行，因為不支援用戶端上執行的 Windows 版本。|Intune 不支援用戶端電腦上執行的 Windows 版本。|
|0xAB2|Windows Installer 無法存取自訂動作的 VBScript 執行階段。|這個錯誤是由以動態連結程式庫 (DLL) 為基礎的自訂動作所造成。 在為 DLL 疑難排解時，您可能必須使用 [Microsoft 支援服務 KB198038：實用的封裝與部署工具](https://support.microsoft.com/en-us/kb/198038)中所述的工具。|
|0x80cf0440|與服務端點的連線已終止。|試用或付費帳戶已暫止。 建立新的試用或付費帳戶，然後重新註冊。|




### <a name="next-steps"></a>後續步驟
如果這項疑難排解資訊對您沒有幫助，請連絡 Microsoft 支援服務 (如[如何取得 Microsoft Intune 支援](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)中所述)。

