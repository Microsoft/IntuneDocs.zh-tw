---
title: 設定行動裝置管理授權單位
titlesuffix: Microsoft Intune
description: 在 Intune 中設定行動裝置管理授權單位。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 99b913b23638a507ed9b0a5cb32afff66679a164
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231905"
---
# <a name="set-the-mobile-device-management-authority"></a>設定行動裝置管理授權單位

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

行動裝置管理 (MDM) 授權單位設定會決定您管理裝置的方式。 身為 IT 系統管理員，您必須在使用者可以註冊裝置以進行管理之前，設定 MDM 授權單位。

可能的設定如下︰

- **Intune 獨立版** - 雲端版管理解決方案，可透過 Azure 入口網站設定。 包含 Intune 提供的完整功能集。 [在 Intune 主控台中設定 MDM 授權單位](#set-mdm-authority-to-intune)。

- **Intune 混合版** - Intune 雲端解決方案與 System Center Configuration Manager 的整合版。 您可以使用 Configuration Manager 主控台設定 Intune。 [在 Configuration Manager 中設定 MDM 授權單位](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription)。 

    > [!Important]
    >即將推出的版本中將會關閉新混合式 MDM 客戶的上架功能。 如需詳細資訊，請參閱 [Move from Hybrid Mobile Device Management to Intune on Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) (從混合式行動裝置管理移到 Azure 上的 Intune) 部落格文章。

- **Office 365 的行動裝置管理** - Office 365 與 Intune 雲端解決方案的整合版。 您可以從 Office 365 系統管理中心設定 Intune。 包含 Intune 獨立版提供的功能子集。 在 Office 365 系統管理中心中設定 MDM 授權單位。

> [!IMPORTANT]
> 在 Configuration Manager 1610 版或更新版本及 Microsoft Intune 1705 版中，您可以在不需要連絡 Microsoft 支援服務的情況下變更 MDM 授權單位，且不需要取消註冊並重新註冊您現有的受管理裝置。 如需詳細資訊，請參閱[準備將 MDM 授權單位變更為 Configuration Manager](mdm-authority-set.md#prepare-to-change-the-mdm-authority-to-configuration-manager)。

## <a name="set-mdm-authority-to-intune"></a>將 MDM 授權單位設為 Intune

如果您尚未設定 MDM 授權單位，請遵循下列步驟。 若要從某個 MDM 授權單位變更為另一個，請參閱下面的[變更 MDM 授權單位](#prepare-to-change-the-mdm-authority-to-configuration-manager)一節。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 選取橙色橫幅，以開啟 [行動裝置管理授權單位] 設定。 只有在您尚未設定 MDM 授權單位時，才會顯示橙色橫幅。
4. 在 [行動裝置管理授權單位] 下，從下列選項中選擇您的 MDM 授權單位：
   - **Intune MDM 授權單位**
   - **Configuration Manager MDM 授權單位**
   - **無**

   ![Intune 設定行動裝置管理授權單位畫面的螢幕擷取畫面](media/set-mdm-auth.png)

   接著會顯示一則訊息指出您已成功將 Intune 設定為 MDM 授權單位。

### <a name="workflow-of-intune-administration-ui"></a>Intune 系統管理使用者介面的工作流程
啟用 Android 或 Apple 裝置管理時，Intune 會傳送裝置與使用者資訊，以便與這些協力廠商服務整合來管理其各自的裝置。

下列案例會另外詢問是否同意共用資料：
- 啟用 Android 工作設定檔。
- 啟用並上傳 Apple MDM Push Certificate 時。
- 啟用任何 Apple 服務時，例如裝置註冊計劃、School Manager 或大量採購方案。

在每個案例中，同意與執行行動裝置管理服務密切相關。 例如，確認 IT 系統管理員已授權 Google 或 Apple 裝置註冊。 當下列位置推出新的工作流程時，會提供文件說明哪些資訊為共用：
- [Intune 傳送至 Google 的資料](https://aka.ms/Data-intune-sends-to-google)
- [Intune 傳送至 Apple 的資料](https://aka.ms/data-intune-sends-to-apple)

## <a name="key-considerations"></a>重要考量
當您切換至新的 MDM 授權單位之後，在裝置簽入服務並完成同步處理之前，很可能需要經歷一些轉換時間 (最多 8 小時)。 您必須在新的 MDM 授權單位 (混合式) 中進行設定，以確保已註冊裝置在變更後會繼續受到管理及保護。 
- 裝置在變更後必須與服務連線，新的 MDM 授權單位 (Intune 獨立部署) 的設定才能取代裝置上的現有設定。
- 在您變更 MDM 授權單位之後，部分來自先前 MDM 授權單位 (Intune 獨立部署) 的基本設定 (例如設定檔)，將會在裝置上保留最多七天的時間，或直到裝置首次連線至服務為止。 建議您盡快在新的 MDM 授權單位 (混合式) 中設定應用程式及設定 (原則、設定檔、應用程式等)，並針對擁有現有已註冊裝置的使用者，將設定部署至包含這些使用者的使用者群組。 在 MDM 授權單位變更之後，裝置在連線至服務時便會立即接收到來自新 MDM 授權單位的新設定，以避免管理及保護上出現間隙。
- Intune 和 Configuration Manager 中有相同的裝置類別時，在您切換至新 MDM 授權單位之後，不會保留裝置的任何裝置類別指派。 若要繼續使用裝置類別，必須在變更 MDM 授權單位之後將已移轉的裝置手動新增至適當的集合，而且裝置會顯示在 Configuration Manager 主控台中。
- 裝置若無關聯的使用者 (通常發生在 iOS 裝置註冊計劃或大量註冊的案例)，便不會移轉至新的 MDM 授權單位。 針對這些裝置，您需要連絡支援人員來取得協助，以便將這些裝置移至新的 MDM 授權單位。

## <a name="prepare-to-change-the-mdm-authority-to-configuration-manager"></a>準備將 MDM 授權單位變更為 Configuration Manager

檢閱下列資訊以準備變更 MDM 授權單位：
- 您必須有 Configuration Manager 1610 版或更新版本，才有變更 MDM 授權單位的選項可供選擇。
- 在您變更至新的 MDM 授權單位之後，裝置可能需要最多 8 小時的時間才能連線至服務。
- 建立具有目前由 Intune 獨立部署所管理之所有使用者的 Configuration Manager 使用者集合，當您在 Configuration Manager 主控台中設定 Intune 訂用帳戶時將會用到它。 此集合可在變更 MDM 授權單位之後，協助確保使用者及其裝置在混合式環境中將會被指派 Configuration Manager 授權並受到管理。
- 請確定 IT 管理使用者也位於此使用者集合之中。  
- 變更之前，MDM 授權單位在 Intune 管理主控台中會顯示為 [設定為 Microsoft Intune]\ (獨立部署)。
- 在變更 MDM 授權單位之前，Microsoft Intune 管理主控台的 MDM 授權單位應該會顯示 [設定為 Microsoft Intune] \(獨立租用戶)。
    > [!NOTE]    
    > 如果 MDM 授權單位顯示 [由 Intune 和 Office 365 管理]，則當您將 MDM 授權單位變更為 [Configuration Manager] (混合式) 之後，由 Office 365 管理的 MDM 裝置將不會再受到管理。 變更 MDM 授權單位之前，建議您為那些使用者提供 Intune 或 Enterprise Mobility Suite 的授權。   

- 在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移除「裝置註冊管理員」角色。 如需詳細資料，請參閱[從 Intune 刪除裝置註冊管理員](device-enrollment-manager-enroll.md#remove-device-enrollment-manager-permissions)。
- 關閉所有已設定的裝置群組對應。 如需詳細資料，請參閱[在 Microsoft Intune 使用裝置群組對應分類裝置](device-group-mapping.md)。
- 變更 MDM 授權單位期間，應該不會對使用者造成明顯影響。 不過，您應該向使用者通知此變更，以確保他們的裝置已開啟，並會在變更後盡快連線至服務。 此預防措施能確保絕大多數的裝置都會以最快的速度透過新授權單位與服務進行連線及註冊。
- 如果您在變更 MDM 授權單位之前，是使用 Intune 獨立部署來管理 iOS 裝置，請務必確保先前用於 Intune 的 Apple Push Notification Service (APNs) 憑證已經更新，並已再次用來在 Configuration Manager (混合式) 中設定租用戶。    

    > [!IMPORTANT]  
    > 如果針對混合式使用不同的 APNs 憑證，先前註冊的所有 iOS 裝置都會取消註冊，且您必須再次執行重新註冊這些裝置的程序。 在變更 MDM 授權單位之前，請務必了解先前於 Intune 中用來管理 iOS 裝置的 APNs 憑證為何。 在 Apple Push Certificates 入口網站 (https://identity.apple.com)) 中尋找相同的憑證，識別擁有用來建立原始 APNs 憑證之 Apple 識別碼的使用者，並確定他可以更新該 APNs 憑證，以順利變更至新的 MDM 授權單位。

## <a name="change-the-mdm-authority-to-configuration-manager"></a>將 MDM 授權單位變更為 Configuration Manager

1. 在 Configuration Manager 主控台中，移至 [系統管理] &gt; [概觀] &gt; [雲端服務] &gt; [Microsoft Intune 訂閱]，然後選取以新增 Intune 訂閱。
2. 登入至您原本在 Intune 中設定 MDM 授權單位時所使用的 Intune 租用戶，然後按一下 [下一步]。
3. 選取 [將我的 MDM 授權單位變更為 Configuration Manager]，然後按一下 [下一步]。
4. 針對將繼續由新的混合式 MDM 授權單位所管理的所有使用者，選取會包含這些使用者的使用者集合。
5. 按 [下一步]  ，並且完成精靈。 MDM 授權單位現已變更為 [Configuration Manager]。
6. 使用相同的 Intune 租用戶登入 [Microsoft Intune 管理主控台](http://manage.microsoft.com)，並確認 MDM 授權單位已變更為 [設定為 Configuration Manager]。
7. 將 MDM 授權單位變更為 Configuration Manager 之後，您可以設定 [iOS 註冊](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac)和 [Android 註冊](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-android)。
8. 在 Configuration Manager 主控台中，從新的 MDM 授權單位 (混合式) 設定並部署新的設定及應用程式。

當裝置再次連線至服務時，它將會進行同步處理，並從新的 MDM 授權單位接收新設定。

## <a name="change-mdm-authority-to-office-365"></a>將 MDM 授權單位變更為 Office 365

除了您現有的 Intune 服務，若要啟用 Office 365 MDM，請前往 [https://protection.office.com](https://protection.office.com)，然後選擇 [資料外洩防護] > [裝置安全性原則] > [View list of Managed Devices] \(檢視受控裝置清單\) > [馬上開始]。

如需詳細資訊，請參閱[在 Office 365 中設定行動裝置管理 (MDM)](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)。

如果您只想透過 Office 365 MDM 管理終端使用者，請移除啟用 Office 365 MDM 之後所指派的任何 Intune 及/或 EMS 授權。

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 憑證到期後的行動裝置清除

當行動裝置與 Intune 服務通訊時，會自動更新 MDM 憑證。 若行動裝置被抹除，或有一段時間無法與 Intune 服務通訊，便無法更新 MDM 憑證。 當 MDM 憑證過期 180 天後，該裝置便會從 Azure 入口網站上移除。

## <a name="remove-mdm-authority"></a>移除 MDM 授權單位

MDM 授權單位無法變更回「未知」。 Microsoft 伺服器使用 MDM 授權單位來決定已註冊裝置回報的入口網站 (ConfigMGR、Azure Intune、Office 365 MDM)。

## <a name="what-to-expect-after-changing-the-mdm-authority"></a>變更 MDM 授權單位之後預期會發生的情況

- 當 Intune 服務偵測到租用戶的 MDM 授權單位已變更之後，將會向所有已註冊的裝置傳送通知訊息，以要求簽入服務並進行同步處理 (此通知有別於一般的排程簽入)。 因此，當租用戶的 MDM 授權單位從 Intune 獨立部署變更至混合式之後，所有電源已開啟並處於線上的裝置都會連線至服務，接收新的 MDM 授權單位，並由混合式進行管理。 這些裝置的管理和保護不會有任何中斷。
- 就算裝置在 MDM 授權單位變更期間 (或於結束後立即) 啟動電源並上線，在裝置能與處於新 MDM 授權單位之下的服務進行註冊之前，將會有最多 8 小時 (視下一個已排程一般簽入的時間而定) 的延遲。    

  > [!IMPORTANT]    
  > 從變更 MDM 授權單位到將更新的 APNs 憑證上傳至新授權單位的期間內，針對 iOS 裝置的新裝置註冊及裝置簽入會失敗。 因此，在變更 MDM 授權單位之後，請務必盡快檢閱並將 APNs 憑證上傳至新的授權單位。

- 使用者可以透過從裝置手動啟動服務簽入，來快速變更至新的 MDM 授權單位。 使用者可以使用公司入口網站應用程式並起始裝置合規性檢查，來輕鬆執行此變更。
- 在變更 MDM 授權單位之後，若要在裝置簽入服務並完成同步處理後確認一切是否正常，請在 Configuration Manager 管理主控台中尋找裝置。 先前由 Intune 所管理的裝置，現在會在 Configuration Manager 主控台中顯示為受管理的裝置。    
- 從 MDM 授權單位變更到裝置簽入服務這段期間，裝置會有一段過渡時間是處於離線狀態。 為了協助確保裝置在此期間能獲得保護並持續運作，下列設定檔會在裝置上保留最多七天 (或直到裝置與新的 MDM 授權單位連線，並接收會覆寫現有設定的新設定為止)：
    - 電子郵件設定檔
    - VPN 設定檔
    - 憑證設定檔
    - Wi-Fi 設定檔
    - 組態設定檔
- 當您變更至新的 MDM 授權單位之後，Microsoft Intune 管理主控台中的合規性資料可能需要最多一週的時間才能正確回報。 不過，位於 Azure Active Directory 中和裝置上的相容性狀態將會正確，因此裝置仍然會受到保護。
- 請確定要覆寫現有設定之新設定的名稱與先前的設定相同，以使它能確實覆寫舊設定。 否則，裝置可能會有多餘的設定檔和原則。    

  > [!TIP]    
  > 最佳做法是在變更 MDM 授權單位之後，便立即建立所有管理設定和組態，以及部署。 這可協助確保裝置在過渡期間獲得保護並受到主動管理。

-  在您變更 MDM 授權單位之後，請執行下列步驟以確認新裝置已成功註冊至新的授權單位：   
    - 註冊新裝置
    - 確定新註冊的裝置已顯示在 Configuration Manager 主控台中。
    - 從管理主控台對裝置執行某個動作 (例如遠端鎖定)。 如果成功，便代表該裝置已由新的 MDM 授權單位管理。
- 如果您在特定裝置上遇到問題，可以將該裝置解除註冊並重新註冊，來盡快使它們連線至新的授權單位並受到管理。

## <a name="next-steps"></a>後續步驟

設定 MDM 授權單位之後，您可以開始[註冊裝置](device-enrollment.md)。
