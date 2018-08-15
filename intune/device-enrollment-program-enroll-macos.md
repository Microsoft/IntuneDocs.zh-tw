---
title: 註冊 macOS 裝置 - 裝置註冊計劃
titleSuffix: Microsoft Intune
description: 了解如何使用裝置註冊計劃來註冊屬公司擁有的 macOS 裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d6f9035b5a31d04e7d6ec6c5ec5b8f69a7c0943f
ms.sourcegitcommit: 0ac196d1d06f4f52f01610eb26060419d248168b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2018
ms.locfileid: "40090101"
---
# <a name="automatically-enroll-macos-devices-with-apples-device-enrollment-program"></a>使用 Apple 的裝置註冊計劃來自動註冊 macOS 裝置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

此文章將協助您針對透過 Apple 的[裝置註冊計劃 (DEP)](https://deploy.apple.com) 購買的裝置設定 macOS 裝置註冊。 您可以在完全不需要接觸的情況下，設定大量裝置的 DEP 註冊。 您可以將 macOS 裝置直接寄送給使用者。 當使用者開啟裝置電源時，會以預先設定的設定來執行設定助理，並註冊裝置以接受 Intune 管理。

若要設定 DEP 註冊，您要使用 Intune 與 Apple DEP 入口網站。 您可以建立 DEP 註冊設定檔，其中包含已在註冊期間套用至裝置的設定。

此外，DEP 註冊不能與[裝置註冊管理員](device-enrollment-manager-enroll.md)一起使用。

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
- 序號或採購單號碼的清單。 
- [MDM 授權單位](mdm-authority-set.md)
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>取得 Apple DEP 權杖

您必須先從 Apple 取得 DEP 權杖 (.p7m) 檔案，才能為 macOS 裝置註冊 DEP。 此權杖可讓 Intune 同步貴公司所擁有的 DEP 裝置資訊。 它也讓 Intune 得以將註冊設定檔上傳至 Apple，並將這些設定檔指定給裝置。

您可以使用 Apple DEP 入口網站建立 DEP 權杖。 您也可以使用 DEP 入口網站將裝置指派給 Intune 以便管理。

> [!NOTE]
> 若在移轉至 Azure 之前從 Intune 傳統入口網站刪除了權杖，Intune 可能會還原已刪除的 Apple DEP 權杖。 您可以從 Azure 入口網站再次刪除該 DEP 權杖。

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>步驟 1： 下載建立權杖所需的 Intune 公開金鑰憑證。

1. 在 [Azure 入口網站的 Intune ](https://aka.ms/intuneportal)中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > [新增]。

    ![取得註冊計劃權杖。](./media/device-enrollment-program-enroll-ios/image01.png)

2. 藉由選取 [我同意] 來將權限授與 Microsoft，以將使用者和裝置資訊傳送給 Apple。

   ![[Apple 憑證] 工作區中 [註冊計劃權杖] 窗格下載公開金鑰的螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. 選擇 [下載您的公開金鑰]，在本機下載並儲存加密金鑰 (.pem) 檔案。 這個 .pem 檔案會用於向 Apple 裝置註冊程式入口網站要求信任關係憑證。


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>步驟 2： 使用您的金鑰，下載來自 Apple 的權杖。

1. 選擇 [建立 Apple 裝置註冊計劃的權杖] 以開啟 Apple 的部署計劃入口網站，並使用您的公司 Apple ID 登入。 您可以使用此 Apple ID 來更新 DEP 權杖。
2.  在 Apple 的[部署計劃入口網站](https://deploy.apple.com)，針對 [裝置註冊計劃] 選擇 [開始使用]。

3. 在 [管理伺服器] 頁面上，選擇 [新增 MDM 伺服器]。
4. 輸入 [MDM 伺服器名稱]，然後選擇 [下一步] 。 您可參考這個伺服器名稱，以識別行動裝置管理 (MDM) 伺服器， 但它不是 Microsoft Intune 伺服器的名稱或 URL。

5. [新增 &lt;服器名稱&gt;] 對話方塊隨即開啟，指出**上傳您的公用金鑰**。 選擇 [選擇檔案...] 以上傳 .pem 檔案，然後選擇 [下一步]。

6. 移至 [部署計劃] &gt; [裝置註冊計劃] &gt; [管理裝置]。
7. 在 [選擇裝置依據] 下，指定識別裝置的方式：
    - **序號**
    - **訂單號碼**
    - **上傳 CSV 檔案**。

   ![指定依據序號選擇裝置、將選擇的動作設定為 [指派給伺服器]，然後選取伺服器名稱的螢幕擷取畫面。](./media/enrollment-program-token-specify-serial.png)

8. 針對 [選擇動作] 選擇 [Assign to Server] (指派給伺服器))，然後選擇指定給 Microsoft Intune 的 &lt;伺服器名稱&gt;，再選擇 [確定]。 Apple 入口網站會將指定的裝置指派給 Intune 伺服器以便管理 ，然後顯示 [指派完成]。

   在 Apple 入口網站中，移至 [部署計劃] &gt; [裝置註冊計劃] &gt; [檢視指派歷程記錄] 查看裝置及其 MDM 伺服器指派的清單。

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>步驟 3： 儲存用以建立此權杖的 Apple ID。

在 Azure 入口網站的 Intune 中，提供 Apple ID 供日後參考。

![指定要用於建立註冊計劃權杖的 Apple 識別碼，並瀏覽至註冊計劃權杖的螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>步驟 4： 上傳權杖。
在 [Apple 權杖] 方塊中，瀏覽至憑證 (.pem) 檔案，選擇 [開啟]，然後選擇 [建立]。 使用推播憑證，透過將原則推送到已註冊的裝置，Intune 即可註冊及管理 macOS 裝置。 Intune 會自動與 Apple 同步處理，以查看您的註冊計劃帳戶。

## <a name="create-an-apple-enrollment-profile"></a>建立 Apple 註冊設定檔

安裝權杖之後，您可以為 DEP 裝置建立註冊設定檔。 裝置註冊設定檔會定義要在註冊期間套用至裝置群組的設定。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖]。
2. 選取權杖，選擇 [設定檔]，然後選擇 [建立設定檔]。

    ![建立設定檔螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/image04.png)

3. 在 [建立設定檔] 下，為設定檔輸入系統管理用的**名稱**以及**描述**。 使用者看不到這些詳細資料。 您可以使用此 [名稱] 欄位，在 Azure Active Directory 中建立動態群組。 設定檔名稱可用來定義 enrollmentProfileName 參數，以註冊具備此註冊設定檔的裝置。 深入了解 [Azure Active Directory 動態群組](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects)。

    ![設定檔名稱與描述。](./media/device-enrollment-program-enroll-macos/createprofile.png)

4. 針對 [平台]，選擇 [macOS]。

5. 針對 [使用者親和性]，為具備此設定檔的裝置選擇需要或不需要由指派的使用者來進行註冊。
    - **搭配使用者親和性進行註冊** - 針對屬於使用者且想要使用公司入口網站 App 進行像是安裝應用程式等服務的裝置，選擇此選項。 若使用 ADFS，則使用者親和性需要 [WS-Trust 1.3 使用者名稱/混合端點](https://technet.microsoft.com/library/adfs2-help-endpoints)。 [深入了解](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。具有使用者親和性的 macOS DEP 裝置不支援多重要素驗證。

    - **不搭配使用者親和性進行註冊** - 針對未與任何使用者相關的裝置選擇此選項。 針對執行工作而不需存取本機使用者資料的裝置使用此選項。 公司入口網站應用程式之類的應用程式無法運作。

6. 選擇 [裝置管理設定]，並選擇您是否想要針對使用此設定檔的裝置鎖定註冊。 **鎖定的註冊**會停用可將管理設定檔從 [系統喜好設定] 功能表中或透過 [終端機] 移除的 macOS 設定。 註冊裝置之後，必須將裝置恢復出廠預設值才能變更此設定。

    ![裝置管理設定螢幕擷取畫面。](./media/device-enrollment-program-enroll-macos/devicemanagementsettingsblade-macos.png)
 
7. 選擇 [確定]。

8. 選擇 [設定助理設定] 以設定下列設定檔的設定：![自訂設定助理](./media/device-enrollment-program-enroll-macos/setupassistantcustom-macos.png)。


    |                 設定                  |                                                                                               說明                                                                                               |
    |------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |     <strong>部門名稱</strong>     |                                                             使用者在啟用期間點選 [關於設定] 時顯示。                                                              |
    |    <strong>部門電話</strong>     |                                                          在使用者在啟用期間按一下 [需要協助] 按鈕時顯示。                                                          |
    | <strong>設定助理選項</strong> |                                                     下列是選擇性設定，可稍後在 macOS [設定] 功能表中進行設定。                                                      |
    |        <strong>密碼</strong>         | 在啟用期間提示輸入密碼。 除非裝置受到保護，或以其他方式控制存取 (例如，將裝置限制為單一應用程式的 Kiosk 模式)，否則一律需要密碼。 |
    |    <strong>位置服務</strong>    |                                                                 啟用時，設定助理會在啟用期間提示此服務。                                                                  |
    |         <strong>還原</strong>         |                                                                啟用時，設定助理會在啟用期間提示 iCloud 備份。                                                                 |
    |   <strong>iCloud 與 Apple ID</strong>   |                         啟用時，設定助理會提示使用者登入 Apple ID，且 [應用程式與資料] 畫面可允許從 iCloud 備份還原裝置。                         |
    |  <strong>條款和條件</strong>   |                                                   啟用時，設定助理會在啟用期間提示使用者接受 Apple 的條款及條件。                                                   |
    |        <strong>Touch ID</strong>         |                                                                 啟用時，設定助理會在啟用期間提示此服務。                                                                 |
    |        <strong>Apple Pay</strong>        |                                                                 啟用時，設定助理會在啟用期間提示此服務。                                                                 |
    |          <strong>縮放</strong>           |                                                                 啟用時，設定助理會在啟用期間提示此服務。                                                                 |
    |          <strong>Siri</strong>           |                                                                 啟用時，設定助理會在啟用期間提示此服務。                                                                 |
    |     <strong>診斷資料</strong>     |                                                                 啟用時，設定助理會在啟用期間提示此服務。                                                                 |
    |     <strong>FileVault</strong>           |  |
    |     <strong>iCloud 診斷</strong>  |  |
    |     <strong>註冊</strong>        |  |


10. 選擇 [確定]。

11. 若要儲存該設定檔，請選擇 [建立]。

## <a name="sync-managed-devices"></a>同步受管理裝置
由於 Intune 有管理您裝置的權限，您可以同步處理 Intune 與 Apple，以在 Azure 入口網站的 Intune 中查看受管理裝置。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > 選擇清單中的權杖 > [裝置] > [同步處理]。![選取 [註冊計劃裝置] 節點並選擇 [同步] 連結的螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/image06.png)

   為了符合 Apple 規定的可接受註冊計劃流量，Intune 具有下列限制︰
   - 完整同步處理每 7 天只能執行一次。 在完整同步期間，Intune 會擷取指派至已連線 Intune 之 Apple MDM 伺服器的序號完整更新清單。 若註冊計劃裝置從 Intune 入口網站刪除，但未從 DEP 入口網站中的 Apple MDM 伺服器解除指派，則在執行完整同步之前，該裝置都不會重新匯入 Intune。   
   - 同步會每 24 小時自動執行一次。 您也可以按一下 [同步] 按鈕來進行同步 (請勿在 15 分鐘內重複點選)。 所有同步要求都必須在 15 分鐘內完成。 [同步] 按鈕在同步完成前都會處於停用狀態。 此同步會重新整理現有的裝置狀態，以及匯入指派至 Apple MDM 伺服器的新裝置。   


## <a name="assign-an-enrollment-profile-to-devices"></a>將註冊設定檔指派給裝置
必須先將註冊計劃設定檔指派至裝置，裝置才能註冊。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > 選擇清單中的權杖。
2. 選擇 [裝置] > 選擇清單中的裝置 > [指派設定檔]。
3. 在 [指派設定檔] 下，選擇裝置的設定檔，然後選擇 [指派]。

### <a name="assign-a-default-profile"></a>指派預設設定檔

您可以針對使用特定權杖註冊的所有裝置，挑選要套用的預設 macOS 和 iOS 設定檔。 

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊方案權杖] > 選擇清單中的權杖。
2. 選擇 [設定預設設定檔]、在下拉式清單中選擇設定檔，然後選擇 [儲存]。 此設定檔將套用到使用該權杖註冊的所有裝置。

## <a name="distribute-devices"></a>散發裝置
您已啟用 Apple 與 Intune 之間的管理和同步，並指派設定檔以供您的 DEP 裝置註冊。 您現在可以將裝置散發給使用者。 具有使用者親和性的裝置會需要為每個使用者指派 Intune 授權。 沒有使用者親和性的裝置需要裝置授權。 裝置恢復出廠預設值之前，已啟動的裝置無法套用註冊設定檔。

## <a name="renew-a-dep-token"></a>更新 DEP 權杖  
1. 前往 deploy.apple.com。  
2. 在 [管理伺服器] 下，選擇與您所欲更新之權杖檔案相關的 MDM 伺服器。
3. 選擇 [產生新權杖]。

    ![產生新權杖的螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. 選擇 [您的伺服器權杖]。  
5. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > 選擇權杖。
    ![註冊計劃權杖的螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. 選擇 [更新權杖]**Renew token**，然後輸入用於建立原始權杖的 Apple ID。  
    ![產生新權杖的螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. 上傳新下載的權杖。  
9. 選擇 [更新權杖]。 您會看到權杖已更新的確認。   
    ![確認的螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/confirmation.png)

## <a name="next-steps"></a>接下來的步驟

註冊 macOS 裝置之後，您可以開始[管理它們](device-management.md)。