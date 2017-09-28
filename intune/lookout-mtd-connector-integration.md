---
title: "設定 Lookout 與 Intune 的整合"
titlesuffix: Azure portal
description: "使用 Intune 設定 Lookout 訂閱"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6a9925b91b009f43c08533222a5fdfc765ea51c2
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2017
---
# <a name="set-up-your-lookout-mobile-threat-defense-integration-with-intune"></a>設定 Lookout Mobile Threat Defense 與 Intune 的整合

設定 Lookout Mobile Threat Defense 訂閱需要下列步驟：

| #        |步驟  |
| ------------- |:-------------|
| 1 | [收集 Azure AD 資訊](#collect-azure-ad-information) |
| 2 | [設定訂閱](#configure-your-subscription) |
| 3 | [設定註冊群組](#configure-enrollment-groups) |
| 4 | [設定狀態同步處理](#configure-state-sync) |
| 5 | [設定錯誤報告電子郵件收件者資訊](#configure-error-report-email-recipient-information) |
| 6 | [設定註冊設定](#configure-enrollment-settings) |
| 7 | [設定電子郵件通知](#configure-email-notifications) |
| 8 | [設定威脅分類](#configure-threat-classification) |
| 9 | [監控註冊](#watching-enrollment) |

> [!IMPORTANT]
> 尚未與 Azure AD 租用戶建立關聯的現有 Lookout Mobile Endpoint Security 租用戶無法用來整合 Azure AD 與 Intune。 請與 Lookout 支援部門連絡，以建立新的 Lookout Mobile Endpoint Security 租用戶。 請使用新的租用戶來連接 Azure AD 使用者。

## <a name="collect-azure-ad-information"></a>收集 Azure AD 資訊
您的 Lookout Mobility Endpoint Security 租用戶與 Azure AD 訂用帳戶將會建立關聯，以將 Lookout 及 Intune 整合在一起。 若要啟用 Lookout Mobile Threat Defense 服務訂閱，您必須提供下列資訊給 Lookout 支援 (enterprisesupport@lookout.com)︰

* **Azure AD 租用戶識別碼**
* 可**完整存取** Lookout 主控台的 **Azure AD 群組物件識別碼**
* 可**限制存取** Lookout 主控台的 **Azure AD 群組物件識別碼** (選擇性)

請使用下列步驟收集您需要提供給 Lookout 支援小組的資訊。

1. 登入 [Azure 入口網站](https://portal.azure.com)，然後選取您的訂閱。 

2. 當您選擇訂閱名稱時，產生的 URL 會包含訂閱識別碼。  如果您在尋找訂用帳戶 ID 時發生任何問題，可參閱這篇 [Microsoft 支援文章](https://support.office.com/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b)以取得尋找訂用帳戶 ID 的提示。

3. 尋找您的 Azure AD 群組識別碼。 Lookout 主控台支援 2 個存取層級：  
  * **完整存取**︰Azure AD 系統管理員可以建立擁有「完整存取」權限的使用者群組，並選擇性地建立擁有「限制存取」權限的使用者群組。  只有這些群組中的使用者才能夠登入 **Lookout 主控台**。
  * **限制存取**︰此群組中的使用者無法存取 Lookout 主控台的幾項設定及註冊相關模組，但可唯讀存取 Lookout 主控台的 [安全性原則] 模組。  

    > [!TIP] 
    > 如需權限的詳細資訊，請參閱 Lookout 網站上的[這篇文章](https://personal.support.lookout.com/hc/articles/114094105653)。

    > [!NOTE] 
    > 在 **Azure AD 管理入口網站**中，您可以在群組的 [屬性] 頁面上找到 [群組物件識別碼]。

4. 收集這項資訊之後，請連絡 Lookout 支援 (電子郵件︰enterprisesupport@lookout.com)。 Lookout 支援部門會與您的主要連絡人合作，一同登入您的訂用帳戶，並使用您收集的資訊來建立 Lookout 企業帳戶。

## <a name="configure-your-subscription"></a>設定訂閱

1. 當 Lookout 支援建立了您的 Lookout Enterprise 帳戶後，Lookout 會傳送電子郵件給貴公司的主要連絡人，並提供下列登入 URL 的連結：https://aad.lookout.com/les?action=consent。

2.  第一次登入 Lookout 主控台必須使用具有 Azure AD 全域管理員角色的使用者帳戶，才能註冊您的 Azure AD 租用戶。 以後的登入不需要此層級的 Azure AD 權限。 隨即顯示同意頁面。 選擇 [接受] 以完成註冊。 接受並同意之後，會將您重新導向至 Lookout 主控台。

    ![Lookout 主控台之第一次登入頁面的螢幕擷取畫面](./media/lookout_mtp_initial_login.png)
    > [注意] 如需登入問題的說明，請參閱 [Lookout 整合疑難排解](https://docs.microsoft.com/intune/troubleshoot/troubleshooting-lookout-integration)。

3.  在 [Lookout 主控台](https://aad.lookout.com)中，從 [系統] 模組選擇 [連接器] 索引標籤，然後選取 [Intune]。

    ![開啟 [連接器] 索引標籤並醒目提示 [Intune] 選項之 Lookout 主控台的螢幕擷取畫面](./media/lookout_mtp_setup-intune-connector.png)

4.  移至 [連接器] > [連線設定]，設定 [Heartbeat Frequency]\(活動訊號頻率) (以分鐘為單位)。

    ![顯示已設定 [活動訊號頻率] 之 [連線設定] 索引標籤的螢幕擷取畫面](./media/lookout-mtp-connection-settings.png)

## <a name="configure-enrollment-groups"></a>設定註冊群組
1. 最佳做法是在包含少數使用者的 [Azure AD 管理入口網站](https://manage.windowsazure.com)建立 Azure AD 安全性群組，以測試 Lookout 整合。

    > [注意] Azure AD 註冊群組中所識別及支援的使用者所有支援 Lookout、註冊 Intune 的裝置，都已註冊且有資格在 Lookout MTD 主控台中啟用。

2. 在 [Lookout 主控台](https://aad.lookout.com)中，選擇 [系統] 模組的 [連接器] 索引標籤，然後選取 [Enrollment Management]\(註冊管理) 定義裝置應該註冊 Lookout 的一組使用者。 新增 Azure AD 安全性群組 [顯示名稱] 以進行註冊。

    ![Intune 連接器註冊頁面的螢幕擷取畫面](./media/lookout-mtp-enrollment.png)

    >[!IMPORTANT]
    > [顯示名稱] 區分大小寫，如 Azure 入口網站安全性群組的 [內容] 所示。 如下圖所示，當標題全部小寫時，安全性群組的 [顯示名稱] 使用駝峰式命名法。 在 Lookout 主控台中比對安全性群組 [顯示名稱] 的大小寫。
    >![Azure 入口網站中 Azure Active Directory 服務的屬性頁面螢幕擷取畫面](./media/aad-group-display-name.png)

    >[!NOTE] 
    >針對檢查新裝置的時間遞增量，最佳做法是使用預設的 5 分鐘。 目前的限制：**Lookout 無法驗證群組顯示名稱：**請確定 Azure 入口網站的 [顯示名稱] 欄位與 Azure AD 安全性群組完全一致。 **不支援建立巢狀群組：**Lookout 使用的 Azure AD 安全性群組必須只包含使用者。 不能包含其他群組。

3.  一旦加入群組，下次使用者在其支援的裝置上開啟 Lookout for Work 應用程式時，裝置會在 Lookout 中啟用。

4.  對結果滿意後，請將註冊延伸到其他使用者群組。

## <a name="configure-state-sync"></a>設定狀態同步處理
在 「State Sync」 (狀態同步處理) 選項中，指定應傳送至 Intune 的資料類型。  裝置狀態和威脅狀態要同時存在，Lookout 與 Intune 的整合才能正常運作。 預設會啟用這些設定。

## <a name="configure-error-report-email-recipient-information"></a>設定錯誤報告電子郵件收件者資訊
在 「Error Management」 (錯誤管理) 選項中，輸入應接收錯誤報告的電子郵件地址。

![Intune 連接器之 [錯誤管理] 頁面的螢幕擷取畫面](./media/lookout-mtp-connector-error-notifications.png)

## <a name="configure-enrollment-settings"></a>設定註冊設定
在 [系統] 模組的 [連接器] 頁面上，指定經過天數，在這之後裝置會視為中斷連線。  已中斷連線的裝置會視為不相容，而且根據 Intune 條件式存取原則，將無法存取您的公司應用程式。 您可以指定 1 到 90 天之間的值。

![Lookout 註冊設定](./media/lookout-console-enrollment-settings.png)

## <a name="configure-email-notifications"></a>設定電子郵件通知
若要接收威脅的電子郵件警示，請使用要用來接收通知的使用者帳戶登入 [Lookout 主控台](https://aad.lookout.com)。 在 [系統] 模組的 [喜好設定] 索引標籤上，選擇應該通知的威脅層級，並設定為 [開啟]。 儲存您的變更。

![顯示使用者帳戶喜好設定頁面的螢幕擷取畫面](./media/lookout-mtp-email-notifications.png) 如果您不想再收到電子郵件通知，請將通知設定為 [關閉]，然後儲存變更。

### <a name="configure-threat-classification"></a>設定威脅分類
Lookout Mobile Threat Defense 會將各種類型的行動裝置威脅進行分類。 [Lookout 威脅分類](http://personal.support.lookout.com/hc/articles/114094130693)具有相關聯的預設風險層級。 您可以隨時變更這些層級，以符合您公司的需求。

![顯示威脅和分類之原則頁面的螢幕擷取畫面](./media/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> 風險層級對於 Mobile Threat Defense 而言很重要，因為 Intune 整合會根據這些風險層級，在執行階段計算裝置合規性。 Intune 管理員可在原則中設定規則，以判斷裝置的現行威脅最低層級為何 (**高**、**中**或**低**) 時，要將其識別為不相容。 Lookout Mobile Threat Defense 中的威脅分類原則會直接在 Intune 中驅動裝置合規性計算。

## <a name="watching-enrollment"></a>監控註冊
完成設定之後，Lookout Mobile Threat Defense 就會開始輪詢 Azure AD，找出對應至指定註冊群組的裝置。  您可以在 [裝置] 模組中找到已註冊裝置的相關資訊。  裝置的初始狀態會顯示為 [擱置中]。  在裝置上安裝、開啟及啟用 Lookout for Work 應用程式之後，裝置狀態將會變更。  如需如何取得推送至裝置之 Lookout for Work 應用程式的詳細資訊，請參閱[使用 Intune 新增 Lookout for Work 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)主題。

## <a name="next-steps"></a>後續步驟

[設定 Lookout 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)
