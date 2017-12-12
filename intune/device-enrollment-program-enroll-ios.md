---
title: "註冊 iOS 裝置 - 裝置註冊方案"
titlesuffix: Azure portal
description: "了解如何使用裝置註冊計劃來註冊屬公司擁有的 iOS 裝置。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a10d158816f17c7fbe07fd14172d1a9abb9ed9b9
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>使用 Apple 的裝置註冊計劃來自動註冊 iOS 裝置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主題將協助您針對透過 Apple 的[裝置註冊計劃 (DEP)](https://deploy.apple.com) 購買的裝置啟用 iOS 裝置註冊。 您可以在完全不需要接觸的情況下，啟用大量裝置的 DEP 註冊。 您可以將 iPhone 和 iPad 等裝置直接交付給使用者。 當使用者啟動裝置時，會以預先設定的設定來執行設定助理，並註冊裝置以接受管理。

若要啟用 DEP 註冊，您要使用 Intune 與 Apple DEP 入口網站。 需要序號或採購單編號的清單，以將裝置指派給 Intune 進行管理。 您可以建立 DEP 註冊設定檔，其中包含已在註冊期間套用至裝置的設定。

此外，DEP 註冊不能與[裝置註冊管理員](device-enrollment-manager-enroll.md)一起使用。

## <a name="what-is-supervised-mode"></a>何謂受監督模式？
Apple 在 iOS 5 中引進受監督模式。 處於受監督模式的 iOS 裝置可以透過更多控制進行管理。 因此，特別適用於屬公司擁有的裝置。 Intune 支援針對受監督模式設定裝置，以作為 Apple 裝置註冊方案 (DEP) 的一部分。 

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>必要條件
- [Apple 的裝置註冊計劃](http://deploy.apple.com)中所購買的裝置
- [MDM 授權單位](mdm-authority-set.md)
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)

> [!NOTE]
> 在設定使用者親和性的 DEP 註冊期間，無法使用多重要素驗證 (MFA)。 註冊後，MFA 會如預期地在這些裝置上運作。 第一次登入時必須變更密碼的使用者不會收到裝置提示。 此外，密碼已過期的使用者也不會在註冊期間收到提示要重設其密碼。 使用者必須使用不同的裝置來重設密碼。

## <a name="get-the-apple-dep-token"></a>取得 Apple DEP 權杖

您必須先從 Apple 取得 DEP 權杖 (.p7m) 檔案，才能為 iOS 裝置註冊 DEP。 此權杖可讓 Intune 同步貴公司所擁有的 DEP 裝置資訊。 它也允許 Intune 將註冊設定檔上傳至 Apple，並將這些設定檔指派給裝置。

您可以使用 Apple DEP 入口網站建立 DEP 權杖。 您也可以使用 DEP 入口網站將裝置指派給 Intune 以便管理。

> [!NOTE]
> 若在移轉至 Azure 之前從 Intune 傳統入口網站刪除了權杖，Intune 可能會還原已刪除的 Apple DEP 權杖。 您可以從 Azure 入口網站再次刪除該 DEP 權杖。 您可以從 Azure 入口網站再次刪除該 DEP 權杖。

**步驟 1.下載建立 Apple DEP 權杖所需的 Intune 公開金鑰憑證。**<br>

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖]。

  ![[Apple 憑證] 工作區中，[註冊計劃權杖] 窗格的螢幕擷取畫面。](./media/enrollment-program-token-add.png)

2. 選擇 [下載您的公開金鑰]，在本機下載並儲存加密金鑰 (.pem) 檔案。 這個 .pem 檔案會用於向 Apple 裝置註冊程式入口網站要求信任關係憑證。

  ![[Apple 憑證] 工作區中 [註冊計劃權杖] 窗格下載公開金鑰的螢幕擷取畫面。](./media/enrollment-program-token-download.png)

**步驟 2.建立並下載 Apple DEP 權杖。**<br>
1. 選擇 [Create a token via Apple's Device Enrollment Program] (透過 Apple 裝置註冊計劃建立權杖) 開啟 Apple 的部署計劃入口網站，並使用您的公司 Apple ID 登入。 您可以使用此 Apple ID 來更新 DEP 權杖。
2.  在 Apple 的[部署計劃入口網站](https://deploy.apple.com)，針對 [裝置註冊計劃] 選擇 [開始使用]。

3. 在 [管理伺服器] 頁面上，選擇 [新增 MDM 伺服器]。
4. 輸入 [MDM 伺服器名稱]，然後選擇 [下一步] 。 您可參考這個伺服器名稱，以識別行動裝置管理 (MDM) 伺服器， 但它不是 Microsoft Intune 伺服器的名稱或 URL。

   ![新增 DEP 的 MDM 伺服器名稱，然後按一下 [下一步] 的螢幕擷取畫面。](./media/enrollment-program-token-add-server.png)

5. [新增 &lt;服器名稱&gt;] 對話方塊隨即開啟，指出**上傳您的公用金鑰**。 選擇 [選擇檔案...] 以上傳 .pem 檔案，然後選擇 [下一步]。


7. 移至 [部署計劃] &gt; [裝置註冊計劃] &gt; [管理裝置]。
8. 在 [選擇裝置依據] 下，指定識別裝置的方式：
    - **序號**
    - **訂單號碼**
    - **上傳 CSV 檔案**。

   ![指定依據序號選擇裝置、將選擇的動作設定為 [指派給伺服器]，然後選取伺服器名稱的螢幕擷取畫面。](./media/enrollment-program-token-specify-serial.png)

9. 針對 [選擇動作] 選擇 [Assign to Server] (指派給伺服器))，然後選擇指定給 Microsoft Intune 的 &lt;伺服器名稱&gt;，再選擇 [確定]。 Apple 入口網站會將指定的裝置指派給 Intune 伺服器以便管理 ，然後顯示 [指派完成]。

   在 Apple 入口網站中，移至 [部署計劃] &gt; [裝置註冊計劃] &gt; [檢視指派歷程記錄] 查看裝置及其 MDM 伺服器指派的清單。

**步驟 3.輸入用以建立註冊計劃權杖的 Apple ID。**<br>在 Azure 入口網站的 Intune 中，提供 Apple ID 供日後參考。 使用此 ID 來更新註冊計劃權杖，以避免未來需要重新註冊所有裝置。

![指定要用於建立註冊計劃權杖的 Apple 識別碼，並瀏覽至註冊計劃權杖的螢幕擷取畫面。](./media/enrollment-program-token-apple-id.png)

**步驟 4.瀏覽至要上傳的註冊計劃權杖。**<br>
前往憑證 (.pem) 檔案，選擇 [開啟]，然後選擇 [上傳]。 使用推播憑證，透過將原則推送到已註冊的行動裝置，Intune 即可註冊和管理 iOS 裝置。 Intune 會自動與 Apple 同步處理，以查看您的註冊計劃帳戶。

## <a name="create-an-apple-enrollment-profile"></a>建立 Apple 註冊設定檔

安裝權杖之後，您可以為 DEP 裝置建立註冊設定檔。 裝置註冊設定檔會定義要在註冊期間套用至裝置群組的設定。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊]。
2. 在 [Apple 的註冊計劃] 下，選擇 [註冊計劃設定檔] > [建立]。
3. 或在 [建立註冊設定檔] 上，為設定檔輸入系統管理用的 [名稱] 以及 [描述]。 使用者看不到這些詳細資料。 您可以使用此 [名稱] 欄位，在 Azure Active Directory 中建立動態群組。 設定檔名稱可用來定義 enrollmentProfileName 參數，以註冊具備此註冊設定檔的裝置。 深入了解 [Azure Active Directory 動態群組](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects)。

  為 [使用者親和性] 選擇具備此設定檔的裝置，在註冊時要或不要有指派的使用者。

 - **搭配使用者親和性進行註冊** - 針對屬於使用者的裝置，以及需要使用公司入口網站進行像是安裝應用程式等服務的裝置，選擇此選項。 使用者親和性需要 [WS-Trust 1.3 使用者名稱/混合端點](https://technet.microsoft.com/library/adfs2-help-endpoints)。 [深入了解](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

 - **不搭配使用者親和性進行註冊** - 針對未與任何使用者相關的裝置選擇此選項。 用於執行工作而不需存取本機使用者資料的裝置。 公司入口網站應用程式之類的應用程式無法運作。

4. 選擇 [裝置管理設定] 以對下列設定檔進行設定：

  ![選擇管理模式的螢幕擷取畫面。 裝置具有下列設定：受監督、鎖定的註冊、允許配對設定為全部拒絕。 Apple Configurator 憑證已為新的註冊計劃設定檔變灰。](./media/enrollment-program-profile-mode.png)
    - **受監督** - 啟用更多管理選項，且預設會停用 [啟用鎖定] 的管理模式。 若將核取方塊留為空白，則管理功能有限。 Microsoft 建議使用 DEP 作為啟用受監督模式的機制，特別是針對將部署大量 iOS 裝置的組織。

 > [!NOTE]
 > 註冊裝置之後，使用 Intune 無法針對受監督模式設定裝置。 註冊之後，啟用受監督模式的唯一方式是使用 USB 纜線將 iOS 裝置連接至 Mac，並使用 Apple Configurator。 這會重設裝置，並使用受監督模式進行設定。 在 [Apple Configurator 文件](http://help.apple.com/configurator/mac/2.3)上，深入了解這項作業。受監督裝置將在鎖定畫面上指出「此 iPhone 是由 Contoso 所管理。」， 以及「會監督此 iPhone。 Contoso 可以監視您的網際網路流量並找到此裝置。」 (在 [設定] > [一般] > [關於] 中)。

    - **鎖定的註冊** - (需要管理模式 = 受監督) 停用允許移除管理設定檔的 iOS 設定。 若將核取方塊留為空白，表示允許從 [設定] 功能表移除管理設定檔。 註冊裝置之後，必須將裝置恢復出廠預設值才能變更此設定。

  - **啟用共用 iPad** - Apple 的裝置註冊計劃不支援共用 iPad。

    - **允許配對** - 指定 iOS 裝置是否可與電腦同步。 若選擇 [依據憑證允許 Apple Configurator]，則必須在 [Apple Configurator 憑證] 下選擇憑證。

    - **Apple Configurator 憑證** - 如果在 [允許配對] 下選擇了 [依據憑證允許 Apple Configurator]，則請選擇要匯入的 Apple Configurator 憑證。

  選擇 [儲存]。

5. 選擇 [設定助理設定]，對下列設定檔進行設定：

  ![為新註冊計劃設定檔使用可用設定選取組態設定的螢幕擷取畫面。](./media/enrollment-program-profile-settings.png)
    - **部門名稱** - 使用者於啟用期間點選 [About Configuration] (關於設定) 時顯示。

    - **部門電話** - 在使用者於啟用期間按一下 [需要協助] 按鈕時顯示。
    - **設定輔助程式選項** - 這些是選用設定，稍後可以在 iOS [設定] 功能表中進行設定。
        - **密碼**
        - **位置服務**
        - **還原**
        - **Apple ID**
        - **條款和條件**
        - **Touch ID**
        - **Apple Pay**
        - **縮放**
        - **Siri**
        - **診斷資料**

    選擇 [儲存]。

9. 若要儲存設定檔設定，請在 [建立註冊設定檔] 刀鋒視窗中，選擇 [建立]。 註冊設定檔會出現在 Apple 註冊計劃註冊設定檔清單。

## <a name="sync-managed-devices"></a>同步受管理裝置
由於 Intune 有管理您裝置的權限，您可以同步處理 Intune 與 Apple，以在 Azure 入口網站的 Intune 中查看受管理裝置。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃裝置] > [同步]。進度列會顯示再次要求進行同步之前，必須要等待的總時間。

  ![已選取註冊計劃裝置節點，且正在選擇 [同步] 連結的螢幕擷取畫面。](./media/enrollment-program-device-sync.png)
  
2. 在 [同步] 刀鋒視窗中，選擇 [要求同步]。進度列會顯示再次要求進行同步之前，必須要等待的總時間。

  ![[同步] 刀鋒視窗，以及正在選擇 [要求同步] 連結的螢幕擷取畫面。](./media/enrollment-program-device-request-sync.png)

  為了符合 Apple 規定的可接受註冊計劃流量，Intune 具有下列限制︰
     -  完整同步處理每 7 天只能執行一次。 完整同步期間，每當 Apple 序號指派至 Intune 時，Intune 都會重新整理一次。 如果在上一次完整同步處理過後的 7 天內嘗試進行完整同步處理，Intune 只會重新整理尚未列在 Intune 中的序號。
     -  任何同步處理要求都會在 15 分鐘內完成。 在此期間或直到要求成功，會停用 [同步處理] 按鈕。
     - Intune 每 24 小時會與 Apple 同步一次新增及移除的裝置。

3. 在 [註冊計劃裝置] 工作區中，選擇 [重新整理] 以查看您的裝置。

## <a name="assign-an-enrollment-profile-to-devices"></a>將註冊設定檔指派給裝置
必須先將註冊計劃設定檔指派至裝置，裝置才能註冊。

>[!NOTE]
>您也可以從 [Apple 序號] 刀鋒視窗中，將序號指派給設定檔。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊]，然後選擇 [註冊計劃設定檔]。
2. 從 [註冊計劃設定檔] 清單中，選擇您想要指派給裝置的設定檔，然後選擇 [指派裝置]。

 ![選取 [指派] 的 [裝置指派] 螢幕擷取畫面。](./media/enrollment-program-device-assign.png)

3. 選擇 [指派]，然後選擇您想要指派此設定檔的裝置。 您可以篩選以檢視可用的裝置︰
  - **未指派**
  - **任何**
  - **&lt;設定檔名稱&gt;**
4. 選擇您想要指派的裝置。 資料行上方的核取方塊最多可選取 1000 個列出的裝置，然後按一下 [指派]。 若要註冊 1000 部以上的裝置，請重複指派步驟，直到將註冊設定檔指派給所有的裝置為止。

  ![在 Intune 中用來指派註冊計劃設定檔的 [指派] 按鈕螢幕擷取畫面](media/dep-profile-assignment.png)

## <a name="distribute-devices"></a>散發裝置
您已啟用 Apple 與 Intune 之間的管理和同步，並指派設定檔以供您的 DEP 裝置註冊。 您現在可以將裝置散發給使用者。 具有使用者親和性的裝置會需要為每個使用者指派 Intune 授權。 沒有使用者親和性的裝置需要裝置授權。 裝置恢復出廠預設值之前，已啟動的裝置無法套用註冊設定檔。

請參閱[以裝置註冊計劃在 Intune 註冊 iOS 裝置](/intune-user-help/enroll-your-device-dep-ios)。
