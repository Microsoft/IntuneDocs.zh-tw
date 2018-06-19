---
title: 將您的 MDM 授權單位變更為 Configuration Manager (混合式 MDM)
description: 了解如何將 MDM 授權單位從 Intune 獨立式變更為 Configuration Manager (混合式 MDM)。
keywords: ''
author: dougeby
manager: dougeby
ms.date: 10/04/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f1b4bce3-7932-4a0d-aa92-6dacc7060f42
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: dc73befb46f1f159d9a8c023bb5604517b9f73f4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31028056"
---
# <a name="change-the-mdm-authority"></a>變更 MDM 授權單位
自 Configuration Manager 1610 版開始，不需要連絡 Microsoft 支援服務，也不需要將現有受管理裝置解除註冊並重新註冊，您便可以變更 MDM 授權單位。 本主題提供步驟，讓您在無需將現有受管理裝置解除註冊並重新註冊的情況下，將從 Intune 設定且 MDM 授權單位設定為 [Microsoft Intune] \(獨立式) 的現有 Microsoft Intune 租用戶，設定為 [Configuration Manager] \(混合式 MDM)。

> [!Note]    
> 如果您要將現有的 Microsoft Intune 租用戶設定從 MDM 授權單位設為 **Configuration Manager** (混合式) 的 Configuration Manager 主控台 (混合式) 變更為 **Microsoft Intune 獨立式**，請參閱[將 MDM 授權單位從 Configuration Manager (混合式 MDM) 變更為 Intune 獨立式](https://docs.microsoft.com/sccm/mdm/deploy-use/change-mdm-authority)。 


## <a name="key-considerations"></a>重要考量
當您切換至新的 MDM 授權單位之後，在裝置簽入服務並完成同步處理之前，很可能需要經歷一些轉換時間 (最多 8 小時)。 您必須在新的 MDM 授權單位 (混合式) 中進行設定，以確保已註冊裝置在變更後會繼續受到管理及保護。 
- 裝置在變更後必須與服務連線，新的 MDM 授權單位 (Intune 獨立部署) 的設定才能取代裝置上的現有設定。
- 在您變更 MDM 授權單位之後，部分來自先前 MDM 授權單位 (Intune 獨立部署) 的基本設定 (例如設定檔)，將會在裝置上保留最多七天的時間，或直到裝置首次連線至服務為止。 建議您盡快在新的 MDM 授權單位 (混合式) 中設定應用程式及設定 (原則、設定檔、應用程式等)，並針對具有現有已註冊裝置的使用者，將設定部署至包含這些使用者的使用者群組。 在 MDM 授權單位變更之後，裝置在連線至服務時便會立即接收到來自新 MDM 授權單位的新設定，以避免管理及保護上出現間隙。
- Intune 和 Configuration Manager 中有相同的裝置類別時，在您切換至新 MDM 授權單位之後，不會保留裝置的任何裝置類別指派。 若要繼續使用裝置類別，必須在變更 MDM 授權單位之後將已移轉的裝置手動新增至適當的集合，而且裝置會顯示在 Configuration Manager 主控台中。
- 裝置若無關聯的使用者 (通常發生在 iOS 裝置註冊計劃或大量註冊的案例)，便不會移轉至新的 MDM 授權單位。 針對這些裝置，您需要連絡支援人員來取得協助，以便將這些裝置移至新的 MDM 授權單位。

## <a name="prepare-to-change-the-mdm-authority-to-configuration-manager-hybrid"></a>準備將 MDM 授權單位變更為 Configuration Manager (混合式)
檢閱下列資訊以準備變更 MDM 授權單位：
- 您必須有 Configuration Manager 1610 版或更新版本，才有變更 MDM 授權單位的選項可供選擇。
- 在您變更至新的 MDM 授權單位之後，裝置可能需要最多 8 小時的時間才能連線至服務。
- 建立具有目前由 Intune 獨立部署所管理之所有使用者的 Configuration Manager 使用者集合，當您在 Configuration Manager 主控台中設定 Intune 訂用帳戶時將會用到它。 這可在變更 MDM 授權單位之後，協助確保使用者及其裝置在混合式環境中將會被指派 Configuration Manager 授權並受到管理。
- 請確定 IT 管理使用者也位於此使用者集合之中。  
- 變更之前，MDM 授權單位在 Intune 管理主控台中會顯示為 [設定為 Microsoft Intune]\ (獨立部署)。
- 在變更 MDM 授權單位之前，Microsoft Intune 管理主控台的 MDM 授權單位應該會顯示 [設定為 Microsoft Intune] \(獨立租用戶)。
    > [!NOTE]    
    > 如果 MDM 授權單位顯示 [由 Intune 和 Office 365 管理]，則當您將 MDM 授權單位變更為 [Configuration Manager] (混合式) 之後，由 Office 365 管理的 MDM 裝置將不會再受到管理。 變更 MDM 授權單位之前，建議您為那些使用者提供 Intune 或 Enterprise Mobility Suite 的授權。   

- 在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移除「裝置註冊管理員」角色。 如需詳細資料，請參閱[從 Intune 刪除裝置註冊管理員](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune#delete-a-device-enrollment-manager-from-intune)。
- 關閉所有已設定的裝置群組對應。 如需詳細資料，請參閱[在 Microsoft Intune 使用裝置群組對應分類裝置](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune)。
- 變更 MDM 授權單位期間，應該不會對使用者造成明顯影響。 不過，您應該向使用者通知此變更，以確保他們的裝置已開啟，並會在變更後盡快連線至服務。 這能確保絕大多數的裝置都會以最快的速度透過新授權單位與服務進行連線及註冊。
- 如果您在變更 MDM 授權單位之前，是使用 Intune 獨立部署來管理 iOS 裝置，請務必確保先前用於 Intune 的 Apple Push Notification Service (APNs) 憑證已經更新，並已再次用來在 Configuration Manager (混合式) 中設定租用戶。    

    > [!IMPORTANT]  
    > 如果針對混合式使用不同的 APNs 憑證，先前註冊的所有 iOS 裝置都會取消註冊，且您必須再次執行重新註冊這些裝置的程序。 在變更 MDM 授權單位之前，請務必了解先前於 Intune 中用來管理 iOS 裝置的 APNs 憑證為何。 在 Apple Push Certificates 入口網站 (https://identity.apple.com)) 中尋找相同的憑證，識別擁有用來建立原始 APNs 憑證之 Apple 識別碼的使用者，並確定他可以更新該 APNs 憑證，以順利變更至新的 MDM 授權單位。  

## <a name="change-the-mdm-authority-to-configuration-manager"></a>將 MDM 授權單位變更為 Configuration Manager
將 MDM 授權單位變更至 Configuration Manager (混合式) 的程序包含下列高階步驟：  
- 在 Configuration Manager 主控台中，新增 Microsoft Intune 訂閱。
- 使用您已更新的相同 APNs 憑證來設定 Apple APNs 憑證。
- 在 Configuration Manager 主控台中，從新的 MDM 授權單位 (混合式) 設定並部署新的設定及應用程式。
- 當裝置再次連線至服務時，它將會進行同步處理，並從新的 MDM 授權單位接收新設定。

#### <a name="to-change-the-mdm-authority-to-configuration-manager"></a>將 MDM 授權單位變更為 Configuration Manager
1. 在 Configuration Manager 主控台中，移至 [系統管理] &gt; [概觀] &gt; [雲端服務] &gt; [Microsoft Intune 訂閱]，然後選取以新增 Intune 訂閱。
2. 登入至您原本在 Intune 中設定 MDM 授權單位時所使用的 Intune 租用戶，然後按一下 [下一步]。
3. 選取 [將我的 MDM 授權單位變更為 Configuration Manager]，然後按一下 [下一步]。
4. 針對將繼續由新的混合式 MDM 授權單位所管理的所有使用者，選取會包含這些使用者的使用者集合。
5. 按 [下一步]  ，並且完成精靈。 MDM 授權單位現已變更為 [Configuration Manager]。
6. 使用相同的 Intune 租用戶登入 [Microsoft Intune 管理主控台](http://manage.microsoft.com)，並確認 MDM 授權單位已變更為 [設定為 Configuration Manager]。


## <a name="enable-ios-enrollment"></a>啟用 iOS 註冊
當您具有 iOS 裝置時，必須在 Configuration Manager 中設定 APNs 憑證。

#### <a name="to-enable-ios-enrollment-and-configure-the-apns-certificate"></a>啟用 iOS 註冊並設定 APNs 憑證

1. **下載憑證簽署要求**

   1. 在 Configuration Manager 主控台中，移至 [系統管理] &gt; [雲端服務] &gt; [Microsoft Intune 訂閱]，然後選取 [建立 APNs 憑證要求] 來開啟 [要求 Apple Push Notification Service 憑證簽署要求] 對話方塊。  
   2. **瀏覽**至儲存新的憑證簽署要求 (.csr) 檔案的路徑。 在本機儲存憑證簽署要求 (.csr) 檔案。  
   3. 按一下 [下載] 。 下載新的 Microsoft Intune .csr 檔案，並由 Configuration Manager 儲存。   

      > [!IMPORTANT]
      > 您必須下載新的憑證簽署要求。 請不要使用現有的檔案，否則會失敗。  

2. 移至 [Apple Push Certificates 入口網站](http://go.microsoft.com/fwlink/?LinkId=269844) \(英文\)，然後以先前用來建立及更新用於 Intune 獨立部署之 APNs 憑證的「相同」Apple ID 進行登入。

   ![Apple Push Certificates 入口網站登入頁面](../media/mdm-change-apns-portal.png)

3. 選取您用於 Intune 獨立部署的 APNs 憑證，然後按一下 [更新]。

    ![更新 APNs 對話方塊](../media/mdm-change-renew-apns.png)

4. 選取您於本機下載的 APNs 憑證簽署要求 (.csr) 檔案，然後按一下 [上傳]。

    ![Apple Push Certificates 入口網站登入頁面](../media/mdm-change-renew-apns-upload.png)
 
5. 選取相同的 APNs，然後按一下 [下載]。 下載 APNs (.pem) 憑證，並將該檔案儲存在本機。  

    ![Apple Push Certificates 入口網站登入頁面](../media/mdm-change-renew-apns-download.png)

6. 使用和先前相同的 Apple ID，將更新的 APNs 憑證上傳至混合式租用戶。

    1.  在 Configuration Manager 主控台中，移至 [系統管理] &gt; [雲端服務] &gt; [Microsoft Intune 訂閱]，然後選擇 [設定平台] &gt; [iOS]。  
    2.  在 [Microsoft Intune 訂閱內容] 對話方塊中，選取 [APNs 憑證] 索引標籤並按一下以選取 [啟用 iOS 和 Mac OS X (MDM) 註冊] 核取方塊。  
    3.  按一下 [瀏覽]，然後移至從 Apple 下載的 APNs 憑證 (.cer) 檔案。 Configuration Manager 顯示 APNs 憑證的資訊。 按一下 [確定] 以將 APN 憑證儲存到 Intune。  

        ![Intune 訂閱內容頁面 - iOS](../media/mdm-change-subscription-properties-ios.png)

## <a name="enable-android-enrollment"></a>啟用 Android 註冊
1. 在 Configuration Manager 主控台中，移至 [系統管理] &gt; [雲端服務] &gt; [Microsoft Intune 訂閱]，然後選擇 [設定平台] &gt; [Android]。  
2. 選取 [啟用 Android 註冊] 並按一下 [確定]。

### <a name="enable-windows-enrollment"></a>啟用 Windows 註冊
1. 在 Configuration Manager 主控台中，移至 [系統管理] &gt; [雲端服務] &gt; [Microsoft Intune 訂閱]，然後選擇 [設定平台] &gt; [Windows]。  
2. 選取 [啟用 Windows 註冊] 並按一下 [確定]。

### <a name="enable-windows-phone-enrollment"></a>啟用 Windows Phone 註冊
1. 在 Configuration Manager 主控台中，移至 [系統管理] &gt; [雲端服務] &gt; [Microsoft Intune 訂閱]，然後選擇 [設定平台] &gt; [Windows Phone]。  
2. 選取您想要啟用的平台，然後按一下 [確定]。


## <a name="next-steps"></a>接下來的步驟
完成 MDM 授權單位的變更之後，請檢閱下列步驟：
- 當 Intune 服務偵測到租用戶的 MDM 授權單位已變更之後，將會向所有已註冊的裝置傳送通知訊息，以要求簽入服務並進行同步處理 (這有別於一般的排程簽入)。 因此，當租用戶的 MDM 授權單位從 Intune 獨立部署變更至混合式之後，所有電源已開啟並處於線上的裝置都會連線至服務，接收新的 MDM 授權單位，並由混合式進行管理。 這些裝置的管理和保護不會有任何中斷。
- 就算裝置在 MDM 授權單位變更期間 (或於結束後立即) 啟動電源並上線，在裝置能與處於新 MDM 授權單位之下的服務進行註冊之前，將會有最多 8 小時 (視下一個已排程一般簽入的時間而定) 的延遲。    

  > [!IMPORTANT]    
  > 從變更 MDM 授權單位到將更新的 APNs 憑證上傳至新授權單位的期間內，針對 iOS 裝置的新裝置註冊及裝置簽入會失敗。 因此，在變更 MDM 授權單位之後，請務必盡快檢閱並將 APNs 憑證上傳至新的授權單位。

- 使用者可以透過從裝置手動啟動服務簽入，來快速變更至新的 MDM 授權單位。 使用者可以使用公司入口網站應用程式並起始裝置合規性檢查，來輕鬆達成這項操作。
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