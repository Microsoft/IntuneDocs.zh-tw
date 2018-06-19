---
title: 設定電信費用管理服務
titleSuffix: Microsoft Intune
description: 整合 Intune 與 Saaswedo 電信費用管理服務。
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ca0c0151bd90051d287c76f5d264030112b85cfd
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31834079"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>在 Intune 中設定電信費用管理服務
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 可讓您管理公司擁有之行動裝置上的資料使用量所造成的電信費用。 為了啟用此功能，Intune 已整合協力廠商軟體開發人員 Saaswedo 的 Datalert 電信費用管理解決方案。 Datalert 是即時的電信費用管理軟體，可讓您管理電信資料使用量。 這能夠協助您受 Intune 管理的裝置避免高額與預期外的資料和漫遊超額用量。

Intune 與 Datalert 整合可讓您集中設定、監視及強制限制漫遊與國內數據使用量。 當限制超過定義的閾值時，會觸發自動化警示。 您可以設定服務對個人或終端使用者群組套用不同的動作 (像是停用漫遊或超出閾值)。 Datalert 管理主控台也提供有關數據使用量與監視資訊的報表。

下圖顯示 Intune 如何整合 Datalert。

  ![Intune 與 Datalert 整合的圖表](./media/tem-datalert-intune-solution-diagram.png)

在開始使用 Intune 的 Datalert 服務之前，必須先個別在 Datalert 主控台與 Intune 中設定。 Datalert 服務與 Intune 都必須開啟連線。 若只有 Datalert 端的連線開啟，但 Intune 端未開啟，Intune 將會在收到通訊後予以忽略。

## <a name="supported-platforms"></a>支援的平台

- Samsung Knox
- iOS 8.0 和更新版本

## <a name="prerequisites"></a>必要條件

- Microsoft Intune 的訂用帳戶，以及對於 Azure 入口網站的存取。
- 訂閱 Datalert 電信費用管理服務

## <a name="list-of-telecom-expense-management-providers"></a>電信費用管理提供者清單

Intune 目前整合了下列電信費用管理提供者︰

[Saaswedo Datalert 電信費用管理服務](http://www.datalert.biz/)

## <a name="deploy-the-intune-and-datalert-integrated-solution"></a>部署 Intune 和 Datalert 整合式解決方案

開始之前，請確定您已有 Intune 和 Datalert 電信費用管理服務訂閱。

### <a name="step-1-connect-the-datalert-service-to-microsoft-intune"></a>步驟 1︰將 Datalert 服務連線到 Microsoft Intune

1. 使用系統管理員認證來登入 Datalert 管理主控台。

2. 在 Datalert 管理主控台上，移至 [設定] 索引標籤，然後移至 [MDM 設定]。

3. 選取 [解除鎖定]，讓您可以在該頁面上輸入設定。

4. 為 [Server MDM] (伺服器的 MDM) 選擇 [ Microsoft Intune]。

5. 在 [Azure AD 網域] 中輸入您的 Azure 租用戶識別碼，然後選取 [連線] 按鈕。

    選取 [連線] 會指定 Datalert 簽入 Intune，確保 Datalert 之前與 Intune 之間沒有任何連線。 Microsoft [登入] 頁面會在幾秒後出現，然後是 Datalert Azure 驗證。

6. 在 Microsoft 驗證頁面上選取 [接受]。 您會被重新導向至 Datalert 的 [Thank you] 頁面，並於幾秒之後關閉。 Datalert 會驗證連線，並在驗證過的項目清單旁顯示綠色核取記號。 如果驗證失敗，您會看到一則紅色的訊息，並應連絡 Datalert 支援以取得協助。

    下列螢幕擷取畫面會顯示您可預期在連線成功後看到的綠色核取記號。

   ![顯示成功連線的 Datalert 頁面](./media/tem-mdm-configuration-mdm-server-page.png)

### <a name="step-2-check-that-the-telecom-expense-management-feature-is-active-in-intune"></a>步驟 2︰檢查 Intune 中已啟用電信費用管理功能

完成上述步驟 1 之後，應該會自動啟用您的連線，而且應該會在 Azure 入口網站中顯示 [使用中] 連線狀態。 這些步驟示範如何檢查 [使用中] 狀態。

1. 登入 [Azure 入口網站](https://portal.azure.com)。

2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。

3. 在 [Intune] 窗格中，選擇 [裝置設定]。

4. 在 [裝置設定] 窗格中，選擇 [設定]   >  [電信費用管理]。

   尋找頁面頂端的 [使用中] 連線狀態。

   ![顯示 [使用中] Datalert 連線狀態的 Intune 頁面](./media/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-corporate-enrolled-devices"></a>步驟 3︰將 Datalert 應用程式部署到公司註冊的裝置

若要確保只會從公司擁有的線路收集數據使用量，您必須做兩件事：
- 在 Intune 中建立裝置類別
- 僅將 Datalert 應用程式的目標設為公司電話。

#### <a name="define-device-categories-and-device-groups-mapped-to-the-categories"></a>定義裝置分類以及對應至分類的裝置群組。

根據組織需求，建立至少兩個裝置分類 (例如，公司和個人)。 接著，為每個類別目錄建立動態裝置群組。 您可以視需要為組織建立更多的分類。

在註冊期間，會向使用者顯示這些分類。 根據使用者所選擇的分類，註冊的裝置將會移至對應的裝置群組。 如需如何建立裝置分類的步驟，請參閱 [Map devices to groups](device-group-mapping.md) (將裝置對應到群組)。

  ![[新增原則] 窗格的螢幕擷取畫面](./media/tem-dynamic-membership-rules.png)

#### <a name="create-the-datalert-app-in-intune"></a>在 Intune 中建立 Datalert 應用程式

請遵循下列步驟，以在 Intune 中建立每個平台的 Datalert 應用程式。 iOS 是作為這些步驟中的範例。

1. 在 [Azure 入口網站](https://portal.azure.com)的 [Intune] 窗格上，選擇 [Mobile Apps]。

2. 在 [Mobile Apps] 窗格上，選擇 [管理] > [應用程式]。

3. 選取 [新增] 來新增應用程式。

4. 選取應用程式類型。 例如，若是 iOS，您需要選取 [iOS 市集應用程式]。

5. 在 [搜尋 App Store] 中，於搜尋視窗中鍵入 **Datalert** 來尋找 Datalert 應用程式。

6. 選取 [Datalert] 應用程式，然後選擇 [選取]。

   ![[新增原則] 窗格的螢幕擷取畫面](./media/tem-select-app-from-apple-app-store.png)

7. 完成其餘步驟，以建立 iOS 的應用程式。

   ![[新增原則] 窗格的螢幕擷取畫面](./media/tem-steps-to-create-the-app.png)

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>將 Datalert 應用程式指派給公司裝置群組

1. 從 [Mobile Apps] 窗格，選取您在前一個步驟中建立的 iOS Datalert 應用程式。

2. 在 [應用程式] 窗格上，選擇 [管理] > [指派]。

3. 選擇 [新增群組]，並遵循步驟來選取公司裝置群組。

4. 選擇是要讓應用程式安裝成為群組的必要或選擇性項目。 下列範例螢幕擷取畫面顯示所需的安裝，這表示使用者必須在註冊其裝置之後安裝 Datalert 應用程式安裝。

   ![[新增原則] 窗格的螢幕擷取畫面](./media/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-corporate-paid-phone-lines-to-the-datalert-console"></a>步驟 4︰將公司付費電話線路新增至 Datalert 主控台

您現在已設定 Intune 和 Datalert 服務彼此通訊。 您現在需要將公司付費電話線路新增至 Datalert 主控台，並定義任何行動或漫遊使用情況違規的臨界值和動作。 您可以手動將公司付費電話線路新增至 Datalert 主控台，或是讓線路在裝置註冊到 Intune 後自動新增。

若要設定這些項目，請移至 [Microsoft Intune 的 Datalert 設定頁面](http://www.datalert.fr/microsoft-intune/intune-setup) (http://www.datalert.fr/microsoft-intune/intune-setup)，然後依照安裝精靈 [Settings] \(設定\) 索引標籤下的步驟進行操作。

  ![[新增原則] 窗格的螢幕擷取畫面](./media/tem-add-phone-lines-to-datalert-console.png)


Datalert 服務現在已上線執行，會開始監視數據使用量，並停用超出設定使用量限制之裝置的行動數據與漫遊數據。

## <a name="client-enrollment-experience"></a>用戶端註冊體驗
針對用戶端註冊體驗，請參閱下列內容：
-   [在電信費用管理中註冊您的 iOS 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
-   [在電信費用管理中註冊您的 Android 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turning-off-the-datalert-service"></a>關閉 Datalert 服務

若在 Azure 入口網站停用 Datalert 服務︰

- 所有因為過去違反使用量限制而對裝置套用的動作都會復原。
- 使用者不再受限於數據存取與漫遊。
- Intune 仍會接收來自服務的訊號，但會予以忽略。

**關閉服務**

1. 在 Azure 入口網站的 [電信費用管理] 窗格中選取 [停用]。

2. 選取 [儲存]。

## <a name="viewing-data-usage-and-roaming-reports"></a>檢視數據使用量及漫遊報表

目前只會在 Saaswedo 的 Datalert 管理主控台中提供數據使用量報告。

即將新增終端使用者安裝 Datalert 應用程式所遵循的指示。
