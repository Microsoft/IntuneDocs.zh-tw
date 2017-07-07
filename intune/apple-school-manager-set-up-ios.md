---
title: "設定 Apple School Manager 註冊計劃註冊 iOS 裝置"
titleSuffix: Intune on Azure
description: "了解如何設定 Apple School Manager 註冊計劃向 Intune 註冊公司擁有的 iOS 裝置\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 73556209c88759ffe0747d9927cbcbb49600e0c0
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="enable-ios-device-enrollment-with-apple-school-manager"></a>使用 Apple School Manager 啟用 iOS 裝置註冊

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主題將協助 IT 系統管理員針對透過 [Apple School Manager](https://school.apple.com/) \(ASM\) 計劃購買的裝置啟用 iOS 裝置註冊。 Microsoft Intune 可以「線上」部署註冊設定檔，註冊 ASM 裝置以進行管理。 系統管理員完全不需實際取得每個受管理的裝置。 ASM 設定檔會包含在包括設定助理選項的註冊期間要套用至裝置的管理設定。

**ASM 註冊步驟**
1. [取得 ASM 權杖並指派裝置](#get-the-asm-token-and-assign-devices)
2. [建立註冊設定檔](#create-an-apple-enrollment-profile)
3. [連線 School Data Sync](#connect-school-data-sync) \(選用\)
4. [同步處理 ASM 管理的裝置](#sync-asm-managed-devices)
5. [將 ASM 設定檔指派給裝置](#assign-an-asm-profile-to-devices)
6. [將裝置散發給使用者](#distribute-devices-to-users)

>[!NOTE]
>ASM 註冊無法和 Apple 的 [裝置註冊計劃 (DEP)](device-enrollment-program-enroll-ios.md) 或 Intune 的[裝置註冊管理員](device-enrollment-manager-enroll.md)帳戶搭配使用。

## <a name="get-the-apple-asm-token-and-assign-devices"></a>取得 Apple ASM 權杖並指派裝置

您必須先從 Apple 取得 ASM 權杖 (.p7m) 檔案，才能為屬公司擁有的 iOS 裝置註冊 Apple School Manager (ASM)。 此權杖可讓 Intune 同步處理 ASM 參與裝置相關資訊。 它也允許 Intune 將註冊設定檔上傳至 Apple，並將這些設定檔指派給裝置。 當您在 Apple 入口網站時，也可以指派裝置序號以進行管理。

**先決條件**
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- 註冊 [Apple School Management](http://school.apple.com)

**步驟 1.下載建立 Apple ASM 權杖所需的 Intune 公開金鑰憑證。**<br>
1. 在 Azure [Intune 入口網站](https://aka.ms/intuneportal)中，選擇 [裝置註冊]，然後選取 [註冊計劃權杖]。
2. 在 [註冊計劃權杖] 刀鋒視窗中，選取 [下載您的公開金鑰憑證]，在本機下載並儲存加密金鑰 (.pem) 檔案。 這個 .pem 檔案會用於向 Apple School Manager 入口網站要求信任關係憑證。

**步驟 2.下載 ASM 權杖並指派裝置**<br>
選取 [透過 Apple School Manager 建立權杖]，並以您的公司 Apple ID 登入。 您可以使用此 Apple ID 來更新 ASM 權杖。

   1.  在 [Apple School Manager 入口網站](https://school.apple.com) 中，移至 [MDM 伺服器]，然後選取 [新增 MDM 伺服器] \(右上角\)。
   2.  輸入 **MDM 伺服器名稱**。 您可參考這個伺服器名稱，以識別行動裝置管理 (MDM) 伺服器， 但它不是 Microsoft Intune 伺服器的名稱或 URL。
   3.  在 Apple 入口網站中選取 [上傳檔案...]，瀏覽至 .pem 檔案，然後選取 [儲存 MDM 伺服器] \(右下角\)。
   4.  選取 [取得權杖]，然後將伺服器權杖 (.p7m) 檔案下載到您的電腦。
   5. 移至 [裝置指派]，然後手動輸入 [序號]、[訂單號碼]，或 [上傳 CSV 檔案] 來 [選擇裝置]。
   6.   選擇 [指派給伺服器]，然後選取您建立的 [MDM 伺服器]。
   7. 指定您**選擇裝置**的方式，然後提供裝置資訊，並利用裝置的 [序號]、[訂單號碼] 或 [上傳 CSV 檔案] 的方式，指定詳細資料。
   8. 依序選擇 [Assign to Server]\(指派給伺服器)、針對 Microsoft Intune 指定的 &lt;伺服器名稱&gt; 以及 [確定]。

**步驟 3.輸入用以建立 ASM 權杖的 Apple ID。**<br>此 ID 應用來更新您的 Apple ASM 權杖，並加以儲存以供未來參考。

**步驟 4.找出並上傳您的權杖。**<br>
移至憑證 (.p7m) 檔案，選擇 [開啟]，然後選擇 [上傳]。 Intune 會自動同步您的 Apple ASM 裝置。

## <a name="create-an-apple-enrollment-profile"></a>建立 Apple 註冊設定檔
裝置註冊設定檔會定義要在註冊期間套用至裝置群組的設定。

1. 在 Intune 入口網站中，選擇 [裝置註冊]，然後選擇 [Apple 註冊]。
2. 在 [註冊計劃] 下方，選取 [註冊計劃設定檔]。
3. 在 [註冊計劃設定檔] 刀鋒視窗中，選取 [建立]。
4. 在 [建立註冊設定檔] 刀鋒視窗中，為 Intune 入口網站中顯示的設定檔輸入 [名稱] 和 [描述]。
5. 為 [使用者親和性] 選擇具備此設定檔的裝置，在註冊時要或不要有使用者親和性。

 - **搭配使用者親和性進行註冊** - 裝置必須在初始設定期間與使用者建立關聯，之後便可以存取公司資料與電子郵件。 為使用者使用其受管理 Apple ID 登入之 ASM 管理的裝置選擇使用者親和性。

 >[!NOTE]
 >在具有使用者親和性的 ASM 裝置註冊期間，無法使用多重要素驗證 (MFA)。 註冊後，MFA 會如預期地在這些裝置上運作。

  Apple School Manager 的「共用的 iPad」模式需要使用者搭配使用者親和性進行註冊。

 >[!NOTE]
    >具有使用者親和性的 ASM 必須啟用 [WS-Trust 1.3 使用者名稱/混合端點](https://technet.microsoft.com/library/adfs2-help-endpoints) \(英文\)，才能要求使用者權杖。 [深入了解 WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

 - **不搭配使用者親和性進行註冊** - 該裝置不會與使用者建立關聯。 針對執行工作而不需存取本機使用者資料的裝置，請使用此關係。 需要使用者親和性的應用程式 (包含用於安裝企業營運應用程式的公司入口網站應用程式) 將無法運作。

6. 選取 [裝置管理設定]。 這些項目是在啟用期間設定，且需要重設為原廠設定才能進行變更。 設定下列設定檔設定，然後選取 [儲存]：

    - **受監督** - 啟用更多管理選項，且預設會停用 [啟用鎖定] 的管理模式。 若將核取方塊留為空白，則管理功能有限。

    - **鎖定的註冊** - (需要管理模式 = 受監督) 停用允許移除管理設定檔的 iOS 設定。 若將核取方塊留為空白，表示允許從 [設定] 功能表移除管理設定檔。

  - **共用的 iPad** - (需要**搭配使用者親和性進行註冊**與**受監督**模式)。允許多個使用者使用受管理 Apple ID 登入註冊的 iPad。 受管理 Apple ID 是在 Apple School Manager 入口網站中建立的。

  >[!NOTE]
  >如果入口網站已經啟用「共用的 iPad」模式，且「使用者親和性」或「受監督」模式設定為 [關]就會針對註冊設定檔停用「共用的 iPad」模式。

  - **快取使用者上限** - (需要 **共用的 iPad** = **是**) 在每個使用者的裝置上建立分割區。 建議的值為某段時間內可能使用裝置的學生人數。 例如，如果六位學生在週間定時使用裝置，請將此數字設為 6。  

    - **允許配對** - 指定 iOS 裝置是否可與電腦同步。 若選擇 [依據憑證允許 Apple Configurator]，則必須在 [Apple Configurator 憑證] 下選擇憑證。

    - **Apple Configurator 憑證** - 如果在 [允許配對] 下選擇了 [依據憑證允許 Apple Configurator]，則請選取要匯入的 Apple Configurator 憑證。

7. 選取 [設定助理設定]，設定下列設定檔設定，然後選取 [儲存]：

    - **部門名稱** - 使用者於啟用期間點選 [About Configuration] (關於設定) 時顯示。

    - **部門電話號碼** - 使用者於啟用期間按一下 [需要協助] 按鈕時顯示。
    - **設定輔助程式選項** - 如果從設定輔助選項排除，稍後可以在 iOS [設定] 功能表中進行設定。
        - **密碼** - 在啟用期間提示輸入密碼。 除非裝置受到保護，或以其他方式控制存取 (例如，將裝置限制為單一應用程式的 Kiosk 模式)，否則一律需要密碼。
        - **定位服務** - 啟用時，設定助理會在啟用期間提示服務
        - **還原** - 啟用時，設定助理會在啟用期間提示 iCloud 備份
        - **Apple ID** - 啟用時，如果 Intune 嘗試不使用 Apple ID 來安裝應用程式，iOS 會提示使用者輸入 Apple ID。 若要下載 iOS App Store 應用程式 (包含 Intune 所安裝的應用程式)，您必須提供 Apple ID。
        - **條款及條件** - 啟用時，設定助理會在啟用期間提示使用者接受 Apple 的條款及條件
        - **Touch ID** - 啟用時，設定助理會在啟用期間提示此服務
        - **Apple Pay** - 啟用時，設定助理會在啟用期間提示此服務
        - **縮放** - 啟用時，設定助理會在啟用期間提示此服務
        - **Siri** - 啟用時，設定助理會在啟用期間提示此服務
        - **診斷資料** - 啟用時，設定助理會在啟用期間提示此服務

8. 若要儲存設定檔設定，請於 [建立註冊設定檔] 刀鋒視窗上，選取 [建立]。

## <a name="connect-school-data-sync"></a>連線 School Data Sync
(選用) ASM 支援使用 Microsoft School Data Sync (SDS) 將類別名冊資料同步到 Azure Active Directory (AD)。 請完成下列步驟以使用 SDS 同步學校資料。

1. 在 [註冊程式權杖] 刀鋒視窗中，選取藍色資訊橫幅或 [連線 SDS]。
2. 選取 [允許 Microsoft School Data Sync 使用此權杖]，設定為 [允許]。 此設定會允許 Intune 和 Office 365 中的 SDS 連線。
3. 若要啟用 ASM 與 Azure AD 之間的連線，請選取 [設定 Microsoft School Data Sync]。 深入了解[如何設定 School Data Sync](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1)。
4. 按一下 [確定] 以儲存並繼續。

## <a name="sync-asm-managed-devices"></a>同步處理 ASM 管理的裝置
由於 Intune 已被指派管理您 ASM 裝置的權限，您可以同步處理 Intune 與 ASM 服務，以在 Intune 入口網站中查看受管理裝置。

1. 在 [Intune] 入口網站中，選擇 [裝置註冊]，然後選擇 [Apple 註冊]。
2. 在 [註冊計劃裝置] 下方，選取 [同步]。 進度列會顯示再次要求進行同步之前，必須要等待的總時間。

    為了符合 Apple 規定的可接受 ASM 流量，Intune 具有下列限制︰
     -  完整 ASM 同步處理每 7 天只能執行一次。 在完整同步處理期間，Intune 會重新整理 Apple 已指派給 Intune 的每個序號，不論先前是否已同步處理序號。 如果在上一次完整同步處理過後的 7 天內嘗試進行完整同步處理，Intune 只會重新整理尚未列在 Intune 中的序號。
     -  任何同步處理要求都會在 15 分鐘內完成。 在此期間或直到要求成功，會停用 [同步處理] 按鈕。

>[!NOTE]
>您也可以從 [註冊計劃裝置] 刀鋒視窗，指派 ASM 序號給設定檔。

## <a name="assign-an-asm-profile-to-devices"></a>將 ASM 設定檔指派給裝置
在註冊由 Intune 管理的 ASM 裝置之前，必須將 ASM 設定檔指派給它們。

1. 在 [Intune] 入口網站中，依序選擇 [裝置註冊] > [Apple 註冊]，然後選取 [註冊計劃設定檔]。
2. 從 [註冊計劃設定檔] 清單中，選取您想要指派給裝置的設定檔，然後選取 [裝置指派]
3. 選取 [指派]，然後選取您想要指派此設定檔的 ASM 裝置。 您可以篩選以檢視可用的 ASM 裝置︰
  - **未指派**
  - **任何**
  - **&lt;ASM 設定檔名稱&gt;**
4. 選取您想要指派的裝置。 資料行上方的核取方塊可選取最多 1000 個列出的裝置。 按一下 [指派]。 若要註冊 1000 個以上的裝置，請重複指派步驟，直到將 ASM 設定檔指派給所有的裝置為止。

## <a name="distribute-devices-to-users"></a>將裝置散發給使用者

現在已可將公司擁有的裝置提供給使用者。 當 iOS ASM 裝置開機時，就會加以註冊交由 Intune 管理。 如果裝置已啟動且正在使用中，則在該裝置重設為原廠設定之前，將無法套用設定檔。

### <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>使用者在其裝置安裝及使用公司入口網站的方式

已設定使用者親和性的裝置可以安裝並執行公司入口網站 App，以下載 App 及管理裝置。 使用者收到裝置之後，他們必須執行設定助理並安裝公司入口網站 App。
