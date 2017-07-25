---
title: "註冊 iOS 裝置 - 裝置註冊方案"
titleSuffix: Intune on Azure
description: "了解如何使用裝置註冊計劃來註冊屬公司擁有的 iOS 裝置。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 654a19dd6f1e5f4fd2bda771b0df95b87944db75
ms.sourcegitcommit: 2a6ad3c233d15a9fb441362105f64b2bdd550c34
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2017
---
# <a name="set-up-ios-device-enrollment-with-device-enrollment-program"></a>使用裝置註冊計劃來設定 iOS 裝置註冊

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主題將協助 IT 系統管理員針對透過 Apple 的[裝置註冊計劃 (DEP)](https://deploy.apple.com) 購買的裝置啟用 iOS 裝置註冊。 Microsoft Intune 可以「無線」的方式將註冊設定檔部署到透過 DEP 購買的裝置上。 系統管理員完全不需實際取得每個受管理的裝置。 DEP 設定檔會包含在包括設定助理選項的註冊期間要套用至裝置的管理設定。

若要啟用 DEP 註冊，您要使用 Intune 與 Apple DEP 入口網站。 此外也需要識別碼或購買訂單編號的清單，以將其指派到 Intune 在 Apple 入口網站中進行管理。

>[!NOTE]
>DEP 註冊不能與[裝置註冊管理員](device-enrollment-manager-enroll.md)一起使用。

**從 Apple 啟用註冊計劃的步驟**
1. [取得 Apple DEP 權杖並指派裝置](#get-the-apple-dep-token)
2. [建立註冊設定檔](#create-an-apple-enrollment-profile)
3. [同步處理 DEP 管理的裝置](#sync-managed-device)
4. [將 DEP 設定檔指派給裝置](#assign-an-enrollment-profile-to-devices)
5. [將裝置散發給使用者](#end-user-experience-with-managed-devices)

## <a name="get-the-apple-dep-token"></a>取得 Apple DEP 權杖

您必須先從 Apple 取得 DEP 權杖 (.p7m) 檔案，才能為屬公司擁有的 iOS 裝置註冊 Apple 的裝置註冊計劃 (DEP)。 此權杖可讓 Intune 同步處理貴公司所擁有的 DEP 參與裝置資訊。 它也允許 Intune 將註冊設定檔上傳至 Apple，並將這些設定檔指派給裝置。

> [!NOTE]
> 若您在遷移至 Azure 之前從 Intune 傳統主控台刪除了權杖，Intune 可能會還原已刪除的 Apple DEP 權杖。 您可以從 Azure 入口網站再次刪除該 DEP 權杖。 您可以從 Azure 入口網站再次刪除該 DEP 權杖。

**先決條件**
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- 已註冊 [Apple 的裝置註冊計劃](http://deploy.apple.com)

**步驟 1.下載建立 Apple DEP 權杖所需的 Intune 公開金鑰憑證。**<br>
1. 在 Intune 入口網站中，依序選擇 [裝置註冊]、[Apple 註冊] 及 [註冊計劃權杖]。

  ![[Apple 憑證] 工作區中，[註冊計劃權杖] 窗格的螢幕擷取畫面。](./media/enrollment-program-token-add.png)

2. 選取 [下載您的公開金鑰憑證]，在本機下載並儲存加密金鑰 (.pem) 檔案。 這個 .pem 檔案會用於向 Apple 裝置註冊程式入口網站要求信任關係憑證。

  ![[Apple 憑證] 工作區中 [註冊計劃權杖] 窗格下載公開金鑰的螢幕擷取畫面。](./media/enrollment-program-token-download.png)

**步驟 2.建立並下載 Apple DEP 權杖。**<br>
1. 選取 [透過 Apple 裝置註冊計劃建立權杖] 開啟 Apple 的部署計劃入口網站，並使用您的公司 Apple ID 登入。 您可以使用此 Apple ID 來更新 DEP 權杖。

  ![[Apple 憑證] 工作區中，[註冊計劃權杖] 窗格的螢幕擷取畫面。](./media/enrollment-program-token-create.png)

  ![[Apple 憑證] 工作區中 [註冊計劃權杖] 窗格下載公開金鑰的螢幕擷取畫面。](./media/enrollment-program-token-sign.png)
2.  在 Apple 的[部署計劃入口網站](https://deploy.apple.com)，針對 [裝置註冊計劃] 選取 [開始使用]。

   ![按一下裝置註冊計畫的 [開始使用] 時，註冊計劃的螢幕擷取畫面。](./media/enrollment-program-token-started.png)

3. 在 [管理伺服器] 頁面上，選擇 [新增 MDM 伺服器]。
4. 輸入 [MDM 伺服器名稱]，然後選擇 [下一步] 。 您可參考這個伺服器名稱，以識別行動裝置管理 (MDM) 伺服器， 但它不是 Microsoft Intune 伺服器的名稱或 URL。

   ![新增 DEP 的 MDM 伺服器名稱，然後按一下 [下一步] 的螢幕擷取畫面。](./media/enrollment-program-token-add-server.png)

5. [新增 &lt;服器名稱&gt;] 對話方塊隨即開啟，指出**上傳您的公用金鑰**。 選擇 [選擇檔案...] 以上傳 .pem 檔案，然後選擇 [下一步]。

   ![選擇公開金鑰檔案按鈕，然後按一下 [下一步] 的螢幕擷取畫面。](./media/enrollment-program-token-choose-file.png)
6.  [新增 &lt;伺服器名稱&gt;] 對話方塊會顯示 [您的伺服器權杖] 連結。 將伺服器權杖 (.p7m) 檔案下載到您的電腦，然後選擇 [完成]。
   ![選擇公用金鑰檔案按鈕，然後按一下 [下一步] 的螢幕擷取畫面。](./media/enrollment-program-token-your-token.png)
7. 移至 [部署計劃] &gt; [裝置註冊計劃] &gt; [管理裝置]。
8. 在 [選擇裝置依據] 下，指定識別裝置的方式：
    - **序號**
    - **訂單號碼**
    - **上傳 CSV 檔案**。

   ![指定依據序號選擇裝置、將選擇的動作設定為 [指派給伺服器]，然後選取伺服器名稱的螢幕擷取畫面。](./media/enrollment-program-token-specify-serial.png)

9. 接著，針對 [選擇動作] 選取 [指派給伺服器]，然後選取針對 Microsoft Intune 指定的 &lt;伺服器名稱&gt;，然後選擇 [確定]。 Apple 入口網站會將指定的裝置指派給 Intune 伺服器以便管理 ，然後顯示 [指派完成]。

   在 Apple 入口網站中，移至 [部署計劃] &gt; [裝置註冊計劃] &gt; [檢視指派歷程記錄] 查看裝置及其 MDM 伺服器指派的清單。

**步驟 3.輸入用以建立註冊計劃權杖的 Apple ID。**<br>在 Intune 入口網站中，提供 Apple ID 供日後參考。 使用此 ID 來更新註冊計劃權杖，以避免需要重新註冊所有裝置。

![指定要用於建立註冊計劃權杖的 Apple 識別碼，並瀏覽至註冊計劃權杖的螢幕擷取畫面。](./media/enrollment-program-token-apple-id.png)

**步驟 4.瀏覽至要上傳的註冊計劃權杖。**<br>
前往憑證 (.pem) 檔案，選擇 [開啟]，然後選擇 [上傳]。 使用推播憑證，透過將原則推送到已註冊的行動裝置，Intune 即可註冊和管理 iOS 裝置。 Intune 會自動與 Apple 同步處理，以查看您的註冊計劃帳戶。

## <a name="create-an-apple-enrollment-profile"></a>建立 Apple 註冊設定檔

裝置註冊設定檔會定義要在註冊期間套用至裝置群組的設定。

1. 在 Intune 入口網站中，選擇 [裝置註冊]，然後選擇 [Apple 註冊]。
2. 在 [Apple 註冊計劃] 下，選取 [註冊計劃設定檔]，然後選取 [註冊計劃設定檔] 刀鋒視窗上的 [建立]。

  ![選擇 [建立] 連結以建立新註冊計劃設定檔的螢幕擷取畫面。](./media/enrollment-program-profile-create.png)

3. 在 [建立註冊設定檔] 刀鋒視窗上，為設定檔輸入系統管理用的 [名稱] 以及 [描述]。 使用者看不到這些詳細資料。

  ![為新的註冊計劃設定檔指定名稱和描述，然後選擇 [搭配使用者親和性進行註冊] 的螢幕擷取畫面。](./media/enrollment-program-profile-name.png)
為 [使用者親和性] 選擇具備此設定檔的裝置，在註冊時要或不要有使用者親和性。

 - **搭配使用者親和性進行註冊** - 使用者在設定期間與裝置建立關聯，之後便可以存取公司資料與電子郵件。 為屬於使用者的裝置，以及使用公司入口網站進行像是安裝應用程式等服務的裝置，選擇 [使用者親和性]。

 > [!NOTE]
 > 在具有使用者親和性的註冊計劃管理的裝置註冊期間，無法使用多重要素驗證 (MFA)。 註冊後，MFA 會如預期地在這些裝置上運作。 當第一次登入時必須變更密碼的新使用者，在裝置上進行註冊期間無法收到提示。 此外，密碼已過期的使用者也不會在註冊期間收到提示要重設其密碼，且必須從不同的裝置重設密碼。

 >[!NOTE]
 >具有使用者親和性的註冊計劃管理，必須啟用 [WS-Trust 1.3 使用者名稱/混合端點](https://technet.microsoft.com/library/adfs2-help-endpoints)，才能要求使用者權杖。 [深入了解 WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

 - **不搭配使用者親和性進行註冊** - 該裝置不會與使用者建立關聯。 針對執行工作而不需存取本機使用者資料的裝置，請使用此關係。 需要使用者關係 (包含用於安裝企業營運應用程式的公司入口網站應用程式) 的應用程式無法運作。

4. 選取 [裝置管理設定] 以對下列設定檔進行設定：

  ![選擇管理模式的螢幕擷取畫面。 裝置具有下列設定：受監督、鎖定的註冊、允許配對設定為全部拒絕。 Apple Configurator 憑證已為新的註冊計劃設定檔變灰。](./media/enrollment-program-profile-mode.png)
    - **受監督** - 啟用更多管理選項，且預設會停用 [啟用鎖定] 的管理模式。 若將核取方塊留為空白，則管理功能有限。

    - **鎖定的註冊** - (需要管理模式 = 受監督) 停用允許移除管理設定檔的 iOS 設定。 若將核取方塊留為空白，表示允許從 [設定] 功能表移除管理設定檔。 註冊裝置之後，必須將裝置恢復出廠預設值才能變更此設定。

    - **允許配對** - 指定 iOS 裝置是否可與電腦同步。 若選擇 [依據憑證允許 Apple Configurator]，則必須在 [Apple Configurator 憑證] 下選擇憑證。

    - **Apple Configurator 憑證** - 如果在 [允許配對] 下選擇了 [依據憑證允許 Apple Configurator]，則請選取要匯入的 Apple Configurator 憑證。

  選擇 [儲存]。

5. 選取 [設定助理設定]，對下列設定檔進行設定：

  ![為新註冊計劃設定檔使用可用設定選取組態設定的螢幕擷取畫面。](./media/enrollment-program-profile-settings.png)
    - **部門名稱** - 使用者於啟用期間點選 [About Configuration] (關於設定) 時顯示。

    - **部門電話** - 在使用者於啟用期間按一下 [需要協助] 按鈕時顯示。
    - **設定輔助程式選項** - 這些是選用設定，稍後可以在 iOS [設定] 功能表中進行設定。
        - **密碼** - 在啟用期間提示輸入密碼。 除非裝置受到保護，或存取以其他某種方式受到控制，否則一律需要密碼。 例如，kiosk 模式會將裝置限制為一個應用程式。
        - **定位服務** - 啟用時，設定助理會在啟用期間提示服務
        - **還原** - 啟用時，設定助理會在啟用期間提示 iCloud 備份
        - **Apple ID** - 啟用時，如果 Intune 嘗試不使用 Apple ID 來安裝應用程式，iOS 會提示使用者輸入 Apple ID。 若要下載 iOS App Store 應用程式 (包含 Intune 所安裝的應用程式)，您必須提供 Apple ID。
        - **條款及條件** - 啟用時，設定助理會在啟用期間提示使用者接受 Apple 的條款及條件
        - **Touch ID** - 啟用時，設定助理會在啟用期間提示此服務
        - **Apple Pay** - 啟用時，設定助理會在啟用期間提示此服務
        - **縮放** - 啟用時，設定助理會在啟用期間提示此服務
        - **Siri** - 啟用時，設定助理會在啟用期間提示此服務
        - **診斷資料** - 啟用時，設定助理會在啟用期間提示此服務

    選擇 [儲存]。
9. 若要儲存設定檔設定，請於 [建立註冊設定檔] 刀鋒視窗上，選取 [建立]。 註冊設定檔會出現在 Apple 註冊計劃註冊設定檔清單。

## <a name="sync-managed-devices"></a>同步受管理裝置
由於 Intune 有管理您的裝置的權限，您可以同步處理 Intune 與 Apple，以在 Intune 入口網站中查看受管理裝置。

1. 在 Intune 入口網站中，依序選擇 [裝置註冊] &gt; [Apple 註冊] &gt; [註冊計劃裝置]。
2. 在 [註冊計劃裝置] 下方，選取 [同步]。 [同步] 刀鋒視窗隨即出現。

  ![已選取註冊計劃裝置節點，且正在選擇 [同步] 連結的螢幕擷取畫面。](./media/enrollment-program-device-sync.png)
3. 在 [同步] 刀鋒視窗中，選取 [要求同步]。 進度列會顯示再次要求進行同步之前，必須要等待的總時間。

  ![[同步] 刀鋒視窗，以及正在選擇 [要求同步] 連結的螢幕擷取畫面。](./media/enrollment-program-device-request-sync.png)

  為了符合 Apple 規定的可接受註冊計劃流量，Intune 具有下列限制︰
     -  完整同步處理每 7 天只能執行一次。 完整同步期間，每當 Apple 序號指派至 Intune 時，Intune 都會重新整理一次。 如果在上一次完整同步處理過後的 7 天內嘗試進行完整同步處理，Intune 只會重新整理尚未列在 Intune 中的序號。
     -  任何同步處理要求都會在 15 分鐘內完成。 在此期間或直到要求成功，會停用 [同步處理] 按鈕。
     - Intune 每 24 小時會與 Apple 同步一次新增及移除的裝置。
     
4. 在 [註冊計劃裝置] 工作區中，選擇 [重新整理] 以查看您的裝置。

## <a name="assign-an-enrollment-profile-to-devices"></a>將註冊設定檔指派給裝置
必須先將註冊計劃設定檔指派至裝置，裝置才能註冊。

>[!NOTE]
>您也可以從 [Apple 序號] 刀鋒視窗中，將序號指派給設定檔。

1. 在 Intune 入口網站中，依序選擇 [裝置註冊] > [Apple 註冊]，然後選取 [註冊計劃設定檔]。
2. 從 [註冊計劃設定檔] 清單中，選取您想要指派給裝置的設定檔，然後選取 [指派裝置]。

 ![[同步] 刀鋒視窗，以及正在選擇 [要求同步] 連結的螢幕擷取畫面。](./media/enrollment-program-device-assign.png)

3. 選取 [指派]，然後選取您想要指派此設定檔的裝置。 您可以篩選以檢視可用的裝置︰
  - **未指派**
  - **任何**
  - **&lt;設定檔名稱&gt;**
4. 選取您想要指派的裝置。 資料行上方的核取方塊最多可選取 1000 個列出的裝置，然後按一下 [指派]。 若要註冊 1000 部以上的裝置，請重複指派步驟，直到將註冊設定檔指派給所有的裝置為止。

  ![在 Intune 入口網站中用來指派註冊計劃設定檔的 [指派] 按鈕螢幕擷取畫面](media/dep-profile-assignment.png)

## <a name="end-user-experience-with-managed-devices"></a>終端使用者的受管理裝置體驗

您現在可以將裝置散發給使用者。 具有使用者親和性的裝置會需要為每個使用者指派 Intune 授權。 裝置恢復出廠預設值之前，已啟動的裝置無法套用註冊設定檔。 當開啟註冊計劃管理的 iOS 裝置時，使用者會在裝置上看到下列選項：  

1. **設定 iOS 裝置** - 使用者可以選擇下列選項：
  - **設定為新的裝置**
  - **從 iCloud 備份還原**
  - **從 iTunes 備份還原**
2. 使用者會收到通知：**&lt;您的組織&gt;會自動設定您的裝置。** 還有下列其他設定詳細資料：

  **設定可讓&lt;您的組織&gt;無線管理此裝置。**

  **系統管理員可協助您設定電子郵件和網路帳戶、安裝和設定應用程式，以及遠端管理設定。**

  **系統管理員可以停用功能、安裝和移除應用程式、監視和限制您的網際網路流量，以及從遠端清除此裝置。**

  **設定提供者：<br> &lt;您的組織&gt; iOS 小組<br> &lt;位址&gt;**

3. 使用者會收到提示，要求輸入其公司或學校的使用者名稱和密碼。
4. 使用者會收到提示，要求輸入其 Apple ID。 需要有 Apple ID 才能安裝 Intune 公司入口網站應用程式與其他應用程式。 提供認證之後，裝置會安裝管理設定檔，且無法移除。 Intune 管理設定檔會顯示在裝置上的 [設定]  >  [一般]  >  [裝置管理] 中。

使用者現在可以完成設定其公司所擁有的裝置，不論是使用 Intune 公司入口網站還是 Apple 設定助理。
