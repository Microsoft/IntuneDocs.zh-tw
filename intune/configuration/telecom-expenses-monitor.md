---
title: 在 Microsoft Intune 中設定電信費用管理服務 - Azure | Microsoft Docs
titleSuffix: ''
description: 將 Microsoft Intune 與 Saaswedo 電信費用管理服務整合來監視數據使用量，並在 Android、iOS 和 iPadOS 裝置上設定閾值或限制。
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6c4d08d1010654a16e13981a0d3353b2418524a
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512869"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>在 Intune 中設定電信費用管理服務

使用 Intune，您可以在組織擁有的行動裝置上管理來自數據使用量的電信費用。 Intune 會與 Saaswedo 的 [Datalert 電信費用管理](http://datalert.biz/get-started) \(英文\) 整合。 Datalert 是可管理電信數據使用量的即時電信費用管理解決方案。 這可協助受 Intune 管理的裝置避免產生高額與預期外的數據與漫遊費用。

與 Datalert 整合可以設定、監視及強制限制漫遊與國內數據使用量。 當限制超過定義的閾值時，即會自動觸發警示。 您也可以設定服務來對個人或群組套用不同的動作 (例如，停用漫遊或超出閾值)。 Datalert 管理主控台包括顯示數據使用量與監視資訊的報表。

下圖顯示 Intune 如何與 Datalert 整合：

  ![Intune 與 Datalert 整合的圖表](./media/telecom-expenses-monitor/tem-datalert-intune-solution-diagram.png)

若要搭配 Intune 使用 Datalert 服務，Datalert 與 Intune 中有一些組態設定。 本文將示範下列項目的作法：

- 設定 Datalert 主控台中的設定，以將 Datalert 服務連線至 Intune。
- 確認此連線處於作用中狀態且已在 Intune 中啟用。
- 使用 Intune 將 Datalert 應用程式新增至您的裝置。
- 關閉 Datalert 服務與 Intune (選擇性)。

## <a name="supported-platforms"></a>支援的平台

- 具備 Knox 功能的 Android 4.4 與更新版本裝置 (Samsung)

  [支援 Knox 的 Android 版本](https://seap.samsung.com/faq/what-versions-android-support-knox-standard-and-knox-premium-sdks-0) \(英文\) (開啟 Samsung 的網站) 列出 Knox 支援的版本。

- iOS 8.0 與更新版本
- iPadOS 13.0 和更新版本

## <a name="prerequisites"></a>先決條件

- Microsoft Intune 的訂用帳戶，以及 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)的存取權
- [Datalert](http://www.datalert.biz/) 的訂用帳戶 \(英文\) (開啟 Datalert 的網站)

## <a name="telecom-expense-management-providers"></a>電信費用管理提供者

Intune 可與下列電信費用管理提供者整合：

- [Saaswedo Datalert 電信費用管理服務](http://www.datalert.biz/) \(英文\) (開啟 Datalert 的網站)

## <a name="deploy-the-intune-and-datalert-solution"></a>部署 Intune 與 Datalert 解決方案

### <a name="step-1-connect-the-datalert-service-to-intune"></a>步驟 1：將 Datalert 服務連結到 Intune

1. 使用系統管理員認證登入 Datalert 管理主控台。

2. 在主控台中，移至 [Settings]  \(設定\) 索引標籤 > [MDM configuration]  \(MDM 設定\)。

3. 選取 [Unblock]  \(解除封鎖\)。 [Unblock]  \(解除封鎖\) 可讓您變更或更新頁面上的設定。

4. 在 [Intune / Datalert Connection]  \(Intune / Datalert 連線\) > [Server MDM]  \(伺服器 MDM\) 中，選取 [Microsoft Intune]  。

5. 針對 [Azure AD domain]  \(Azure AD 網域\)，輸入您的 Azure 租用戶識別碼。 選取 [Connection]  \(連線\)。

    當您選取 [Connection]  \(連線\) 時，Datalert 服務會簽入 Intune。 它會確認目前沒有任何 Datalert 連線。 Microsoft 登入頁面會在片刻之後出現，然後是 Datalert Azure 驗證。

6. 在 Microsoft 驗證頁面上選取 [接受]  。

    系統會將您重新導向至 Datalert 的 [thank you]  \(感謝您\) 頁面，並在片刻之後關閉。 Datalert 會驗證連線，並在驗證過的項目旁邊顯示綠色核取記號。 若驗證失敗，您將會看見紅色訊息。 請連絡 Datalert 支援服務以尋求協助。

    下圖顯示連線成功時的綠色核取記號：

      ![顯示成功連線的 Datalert 頁面](./media/telecom-expenses-monitor/tem-datalert-connection.png)

7. 在 [Datalert App / ADAL Consent]  \(Datalert 應用程式 / ADAL 同意\) 中，將開關設定為 [On]  \(開啟\)。 在 Microsoft 驗證頁面上選取 [接受]  。

    系統會將您重新導向至 Datalert 的 [thank you]  \(感謝您\) 頁面，並在片刻之後關閉。 Datalert 會驗證連線，並在驗證過的項目旁邊顯示綠色核取記號。 若驗證失敗，您將會看見紅色訊息。 請連絡 Datalert 支援服務以尋求協助。

    下圖顯示連線成功時的綠色核取記號：

      ![顯示成功連線的 Datalert 頁面](./media/telecom-expenses-monitor/tem-datalert-adal-consent.png)

8. 在 [MDM Profiles management (optional)]  \(MDM 設定檔管理 (選擇性)\) 中，將開關設定為 [On]  \(開啟\)。 此設定讓 Datalert 能夠讀取 Intune 中的可用設定檔，以協助您設定原則。 

    在 Microsoft 驗證頁面上選取 [接受]  。

    系統會將您重新導向至 Datalert 的 [thank you]  \(感謝您\) 頁面，並在片刻之後關閉。 Datalert 會驗證連線，並在驗證過的項目旁邊顯示綠色核取記號。 若驗證失敗，您將會看見紅色訊息。 請連絡 Datalert 支援服務以尋求協助。

    下圖顯示連線成功時的綠色核取記號：

   ![顯示成功連線的 Datalert 頁面](./media/telecom-expenses-monitor/tem-datalert-mdm-profiles.png)

### <a name="step-2-confirm-telecom-expense-management-is-active-in-intune"></a>步驟 2：在 Intune 中確認電信費用管理為作用中狀態

完成步驟 1 之後，您的連線即會自動啟用。 在 Intune 中，連線狀態會顯示 [作用中]  。 若要確認狀態為作用中，請使用下列步驟：

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [租用戶系統管理]   > [連接器與權杖]   > [電信費用管理]  。 尋找 [作用中]  連線狀態：

   ![顯示 [使用中] Datalert 連線狀態的 Intune 頁面](./media/telecom-expenses-monitor/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-devices"></a>步驟 3：將 Datalert 應用程式部署至裝置

若要確認只會收集來自組織擁有之線路的數據使用量，請務必：

- 在 Intune 中建立裝置類別。
- 將 Datalert 應用程式的目標設定為僅限組織電話。

此節列出這些步驟。

#### <a name="create-device-categories-and-device-groups-mapped-to-your-categories"></a>建立裝置類別與對應至類別的裝置群組

根據組織需求，至少建立兩個裝置類別 (例如，公司與個人)。 接著，為每個類別目錄建立動態裝置群組。 您可以視需要為組織建立更多的分類。

若要在 Intune 中建立裝置類別，請參閱[將裝置對應到群組](../enrollment/device-group-mapping.md)。

系統會在註冊期間 ([註冊 Android 裝置](../enrollment/android-enroll.md)) 向使用者顯示這些類別。 根據使用者選擇的類別，系統會將註冊的裝置移至對應的裝置群組。

  ![[新增原則] 窗格的螢幕擷取畫面](./media/telecom-expenses-monitor/tem-dynamic-membership-rules.png)

#### <a name="add-the-datalert-app-to-intune"></a>將 Datalert 應用程式新增至 Intune

下列步驟會新增 Datalert 應用程式。 我們在此範例中使用 iOS/iPadOS。 [新增應用程式](../apps/apps-add.md)與[使用範圍標籤](../fundamentals/scope-tags.md)提供更多有關這些步驟的具體資訊。

1. 在 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)內，選取 [應用程式]   > [所有應用程式]   > [新增]  。

2. 選取您的 [應用程式類型]  。 例如，針對 iOS/iPadOS，選取 [Store 應用程式 - iOS/iPadOS]  。

3. 在 [搜尋 App Store]  中，輸入 **Datalert** 以尋找 Datalert 應用程式。

4. 選擇 [Datalert]  應用程式 > [選取]  ：

   ![將 Datalert 應用程式從 App Store 新增至 Intune 用戶端應用程式](./media/telecom-expenses-monitor/tem-select-app-from-apple-app-store.png)

5. 輸入任何其他屬性，例如應用程式資訊與範圍標籤：

   ![輸入應用程式屬性，包括名稱、描述、選擇 OS，以及 Intune 中應用程式的其他設定](./media/telecom-expenses-monitor/tem-steps-to-create-the-app.png)

6. 選取 [確定]   > [新增]  以儲存您的變更。 Datalert 應用程式會顯示於清單中。

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>將 Datalert 應用程式指派給公司裝置群組

1. 在 [應用程式]   > [所有應用程式]  中，選取您在上一個步驟新增的 Datalert 應用程式。

2. 選取 [指派]   > [加入群組]  。 選擇指派應用程式的方式。 [在 Intune 中將應用程式指派給群組](../apps/apps-deploy.md)提供更多有關這些設定的詳細資料。

    在這些步驟中，您將選擇要讓應用程式安裝成為群組的必要或選擇性項目。 下列範例會視需要顯示安裝。 必要時，使用者必須在註冊其裝置之後，安裝 Datalert 應用程式。

   ![[新增原則] 窗格的螢幕擷取畫面](./media/telecom-expenses-monitor/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-organization-phone-lines-to-the-datalert-console"></a>步驟 4：將組織電話線路新增至 Datalert 主控台

Intune 與 Datalert 服務現在會設定為與彼此通訊。 接下來，將組織付費電話線路新增至 Datalert 主控台。 然後，輸入任何行動數據或漫遊使用量違規的閾值與動作。 您可以手動將公司付費電話線路新增至 Datalert 主控台，或是讓線路在裝置註冊到 Intune 後自動新增。

若要設定這些項目，請移至[適用於 Microsoft Intune 的 Datalert 設定](http://www.datalert.fr/microsoft-intune/intune-setup) \(英文\) (開啟 Datalert 的網站)。 在 [Settings]  \(設定\) 下方，遵循設定精靈中的步驟。

  ![[新增原則] 窗格的螢幕擷取畫面](./media/telecom-expenses-monitor/tem-add-phone-lines-to-datalert-console.png)

Datalert 服務目前為作用中狀態。 它會開始監視數據使用量，並在超出所設定使用量限制的裝置上停用行動數據與漫遊數據。

## <a name="end-user-enrollment"></a>終端使用者註冊

針對終端使用者體驗，下列文章或許能提供協助：

- [在電信費用管理中註冊您的 iOS/iPadOS 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
- [在電信費用管理中註冊您的 Android 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turn-off-the-datalert-service"></a>關閉 Datalert 服務

1. 在 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)內，選取 [租用戶系統管理]   > [連接器與權杖]   > [電信費用管理 ]  。
2. 將 [啟用電信費用管理，並在裝置上封鎖超出設定之使用量配額的行動數據或漫遊數據]  設定為 [停用]  。
3. [儲存]  變更。

> [!IMPORTANT]
> 如果您在 Intune 中停用 Datalert 服務：
>
> - 所有因為過去違反使用量限制而對裝置套用的動作都會復原。
> - 使用者不再受限於數據存取與漫遊。
> - Intune 仍會接收來自服務的訊號，但 Intune 會忽略訊號。

## <a name="next-steps"></a>後續步驟

您可以在 Saaswedo 的 Datalert 管理主控台中取得數據使用量報告。
