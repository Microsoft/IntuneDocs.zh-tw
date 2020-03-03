---
title: 設定行動裝置管理授權單位
titleSuffix: Microsoft Intune
description: 在 Intune 中設定行動裝置管理授權單位。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b611b2307b7b4f7e789e7db9d070e4b6b3f1350c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514484"
---
# <a name="set-the-mobile-device-management-authority"></a>設定行動裝置管理授權單位

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

行動裝置管理 (MDM) 授權單位設定會決定您管理裝置的方式。 身為 IT 系統管理員，您必須在使用者可以註冊裝置以進行管理之前，設定 MDM 授權單位。

可能的設定如下︰

- **Intune 獨立版** - 雲端版管理解決方案，可透過 Azure 入口網站設定。 包含 Intune 提供的完整功能集。 [在 Intune 主控台中設定 MDM 授權單位](#set-mdm-authority-to-intune)。

- **Intune 共同管理** - Windows 10 裝置的 Intune 雲端解決方案與 Configuration Manager 整合版。 您可以使用 Configuration Manager 主控台設定 Intune。 [設定針對 Intune 自動註冊裝置](https://docs.microsoft.com/configmgr/comanage/tutorial-co-manage-clients#configure-auto-enrollment-of-devices-to-intune)。 

- **Office 365 的行動裝置管理** - Office 365 與 Intune 雲端解決方案的整合版。 您可以從 Microsoft 365 系統管理中心設定 Intune。 包含 Intune 獨立版提供的功能子集。 在 Microsoft 365 系統管理中心中設定 MDM 授權單位。

- **Office 365 MDM 共存**：您可以在租用戶上同時啟動並使用適用於 Office 365 的 MDM 與 Intune，並針對每個使用者將管理授權單位設定為 Intune 或適用於 Office 365 的 MDM，以指示將使用哪個服務來管理其行動裝置。 使用者的管理授權單位會根據指派給使用者的授權來定義。 如需詳細資訊，請參閱 [Microsoft Intune 與適用於 Office 365 的 MDM 共存](https://blogs.technet.microsoft.com/configmgrdogs/2016/01/04/microsoft-intune-co-existence-with-mdm-for-office-365) \(英文\)

## <a name="set-mdm-authority-to-intune"></a>將 MDM 授權單位設為 Intune

如果您尚未設定 MDM 授權單位，請遵循下列步驟。

1. 在 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選取橙色橫幅以開啟 [行動裝置管理授權單位]  設定。 只有在您尚未設定 MDM 授權單位時，才會顯示橙色橫幅。
2. 在 [行動裝置管理授權單位]  下，從下列選項中選擇您的 MDM 授權單位：
   - **Intune MDM 授權單位**
   - **無**

   ![Intune 設定行動裝置管理授權單位畫面的螢幕擷取畫面](./media/mdm-authority-set/set-mdm-auth.png)

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
當您切換至新的 MDM 授權單位之後，在裝置簽入服務並完成同步處理之前，很可能需要經歷一些轉換時間 (最多 8 小時)。 您必須在新的 MDM 授權單位中進行設定，以確保已註冊裝置在變更後會繼續受到管理及保護。 
- 裝置在變更後必須與服務連線，新的 MDM 授權單位 (Intune 獨立部署) 的設定才能取代裝置上的現有設定。
- 在您變更 MDM 授權單位之後，部分來自先前 MDM 授權單位的基本設定 (例如設定檔)，將會在裝置上保留最多七天的時間，或直到裝置首次連線至服務為止。 建議您盡快在新的 MDM 授權單位中設定應用程式及設定 (原則、設定檔、應用程式等)，並針對擁有現有已註冊裝置的使用者，將設定部署至包含這些使用者的使用者群組。 在 MDM 授權單位變更之後，裝置在連線至服務時便會立即接收到來自新 MDM 授權單位的新設定，以避免管理及保護上出現間隙。
- 裝置若無相關聯的使用者 (通常發生在 iOS/iPadOS 裝置註冊計劃或大量註冊的案例)，便不會遷移至新的 MDM 授權單位。 針對這些裝置，您需要連絡支援人員來取得協助，以便將這些裝置移至新的 MDM 授權單位。

## <a name="change-mdm-authority-to-office-365"></a>將 MDM 授權單位變更為 Office 365

若要啟用 Office 365 MDM (或除了您現有的 Intune 服務之外，啟動 MDM 共存)，請移至 [https://protection.office.com](https://protection.office.com)，然後選擇 [資料外洩防護]   >  [裝置安全性原則]   >  [檢視受控裝置清單]   >  [讓我們開始吧]  。

如需詳細資訊，請參閱[在 Office 365 中設定行動裝置管理 (MDM)](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)。

如果您只想透過 Office 365 MDM 管理終端使用者，請移除啟用 Office 365 MDM 之後所指派的任何 Intune 及/或 EMS 授權。

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 憑證到期後的行動裝置清除

當行動裝置與 Intune 服務通訊時，會自動更新 MDM 憑證。 若行動裝置被抹除，或有一段時間無法與 Intune 服務通訊，便無法更新 MDM 憑證。 當 MDM 憑證過期 180 天後，該裝置便會從 Azure 入口網站上移除。

## <a name="remove-mdm-authority"></a>移除 MDM 授權單位

MDM 授權單位無法變更回「未知」。 服務會使用 MDM 授權單位，來決定已註冊的裝置要向哪個入口網站回報 (Microsoft Intune 或 Office 365 MDM)。

## <a name="what-to-expect-after-changing-the-mdm-authority"></a>變更 MDM 授權單位之後預期會發生的情況

- 當 Intune 服務偵測到租用戶的 MDM 授權單位已變更之後，將會向所有已註冊的裝置傳送通知訊息，以要求簽入服務並進行同步處理 (此通知有別於一般的排程簽入)。 因此，當租用戶的 MDM 授權單位從 Intune 獨立部署變更之後，所有電源已開啟並處於線上的裝置都會連線至服務，接收新的 MDM 授權單位，並由新的 MDM 授權單位進行管理。 這些裝置的管理和保護不會有任何中斷。
- 就算裝置在 MDM 授權單位變更期間 (或於結束後立即) 啟動電源並上線，在裝置能與處於新 MDM 授權單位之下的服務進行註冊之前，將會有最多 8 小時 (視下一個已排程一般簽入的時間而定) 的延遲。    

  > [!IMPORTANT]    
  > 從變更 MDM 授權單位到將更新的 APN 憑證上傳至新授權單位的期間內，針對 iOS/iPadOS 裝置的新裝置註冊及裝置存回會失敗。 因此，在變更 MDM 授權單位之後，請務必盡快檢閱並將 APNs 憑證上傳至新的授權單位。

- 使用者可以透過從裝置手動啟動服務簽入，來快速變更至新的 MDM 授權單位。 使用者可以使用公司入口網站應用程式並起始裝置合規性檢查，來輕鬆執行此變更。
- 在變更 MDM 授權單位之後，若要在裝置簽入服務並完成同步處理後確認一切是否正常，請在新的 MDM 授權單位中尋找該裝置。
- 從 MDM 授權單位變更到裝置簽入服務這段期間，裝置會有一段過渡時間是處於離線狀態。 為了協助確保裝置在此過度期間能獲得保護並持續運作，下列設定檔將會在裝置上保留最多 7 天 (或直到裝置與新的 MDM 授權單位連線，並接收覆寫現有設定的新設定為止)：
  - 電子郵件設定檔
  - VPN 設定檔
  - 憑證設定檔
  - Wi-Fi 設定檔
  - 組態設定檔
- 當您變更至新的 MDM 授權單位之後，Microsoft Intune 管理主控台中的合規性資料可能需要最多一週的時間才能正確回報。 不過，位於 Azure Active Directory 中和裝置上的相容性狀態將會正確，因此裝置仍然會受到保護。
- 請確定要覆寫現有設定之新設定的名稱與先前的設定相同，以使它能確實覆寫舊設定。 否則，裝置可能會有多餘的設定檔和原則。    

  > [!TIP]    
  > 最佳做法是在變更 MDM 授權單位之後，便立即建立所有管理設定和組態，以及部署。 這可協助確保裝置在過渡期間獲得保護並受到主動管理。

- 在您變更 MDM 授權單位之後，請執行下列步驟以確認新裝置已成功註冊至新的授權單位：   
  - 註冊新裝置
  - 確定新註冊的裝置顯示在新的 MDM 授權單位中。
  - 從管理主控台對裝置執行某個動作 (例如遠端鎖定)。 如果成功，便代表該裝置已由新的 MDM 授權單位管理。
- 如果您在特定裝置上遇到問題，可以將該裝置解除註冊並重新註冊，來盡快使它們連線至新的授權單位並受到管理。

## <a name="next-steps"></a>後續步驟

設定 MDM 授權單位之後，您可以開始[註冊裝置](../enrollment/device-enrollment.md)。
