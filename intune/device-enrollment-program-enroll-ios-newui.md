---
title: 註冊 iOS 裝置 - 裝置註冊方案
titleSuffix: Microsoft Intune
description: 了解如何使用裝置註冊計劃來註冊公司擁有的 iOS 裝置 (新 UI)。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5532e00f90702b820ec5bed6bf2fdb3d5e9d37df
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>使用 Apple 的裝置註冊計劃來自動註冊 iOS 裝置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> ### <a name="temporary-user-interface-differences"></a>暫時的使用者介面差異
> 本頁所述功能的使用者介面正在進行更新。 這些更新將會在 4 月底推出給所有的使用者帳戶。
>
> 如果您的**裝置註冊**頁面如下圖所示，代表您已經有最新的使用者介面，並且可以使用此說明頁面。
>
> ![新的使用者介面](./media/appleenroll-newui.png)
>
> 否則，如果您的**裝置註冊**頁面如下圖所示，代表您的帳戶尚未更新至新的使用者介面。 移至[此說明頁面](device-enrollment-program-enroll-ios.md)。
>
> ![舊的使用者介面](./media/appleenroll-oldui.png)

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

## <a name="get-an-apple-dep-token"></a>取得 Apple DEP 權杖

您必須先從 Apple 取得 DEP 權杖 (.p7m) 檔案，才能為 iOS 裝置註冊 DEP。 此權杖可讓 Intune 同步貴公司所擁有的 DEP 裝置資訊。 它也允許 Intune 將註冊設定檔上傳至 Apple，並將這些設定檔指派給裝置。

您可以使用 Apple DEP 入口網站建立 DEP 權杖。 您也可以使用 DEP 入口網站將裝置指派給 Intune 以便管理。

> [!NOTE]
> 若在移轉至 Azure 之前從 Intune 傳統入口網站刪除了權杖，Intune 可能會還原已刪除的 Apple DEP 權杖。 您可以從 Azure 入口網站再次刪除該 DEP 權杖。 您可以從 Azure 入口網站再次刪除該 DEP 權杖。

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>步驟 1： 下載建立權杖所需的 Intune 公開金鑰憑證。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > [新增]。

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
在 [Apple 權杖] 方塊中，瀏覽至憑證 (.pem) 檔案，選擇 [開啟]，然後選擇 [建立]。 使用推播憑證，透過將原則推送到已註冊的行動裝置，Intune 即可註冊和管理 iOS 裝置。 Intune 會自動與 Apple 同步處理，以查看您的註冊計劃帳戶。

## <a name="create-an-apple-enrollment-profile"></a>建立 Apple 註冊設定檔

安裝權杖之後，您可以為 DEP 裝置建立註冊設定檔。 裝置註冊設定檔會定義要在註冊期間套用至裝置群組的設定。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖]。
2. 選取權杖，選擇 [設定檔]，然後選擇 [建立設定檔]。
    ![建立設定檔螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/image04.png)
3. 在 [建立設定檔] 下，為設定檔輸入系統管理用的**名稱**以及**描述**。 使用者看不到這些詳細資料。 您可以使用此 [名稱] 欄位，在 Azure Active Directory 中建立動態群組。 設定檔名稱可用來定義 enrollmentProfileName 參數，以註冊具備此註冊設定檔的裝置。 深入了解 [Azure Active Directory 動態群組](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects)。
    ![設定檔名稱與描述。](./media/device-enrollment-program-enroll-ios/image05.png)

4. 針對 [使用者親和性]，為具備此設定檔的裝置選擇需要或不需要由指派的使用者來進行註冊。
    - **搭配使用者親和性進行註冊** - 針對屬於使用者的裝置，以及想要使用公司入口網站進行像是安裝應用程式等服務的裝置，選擇此選項。 此選項也可讓使用者使用公司入口網站來驗證其裝置。 使用者親和性需要 [WS-Trust 1.3 使用者名稱/混合端點](https://technet.microsoft.com/library/adfs2-help-endpoints)。 [深入了解](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

    - **不搭配使用者親和性進行註冊** - 針對未與任何使用者相關的裝置選擇此選項。 針對執行工作而不需存取本機使用者資料的裝置使用此選項。 公司入口網站應用程式之類的應用程式無法運作。

5. 如果您選擇 [搭配使用者親和性進行註冊]，則可以選擇讓使用者使用公司入口網站進行驗證，而不是 Apple 設定助理。

    ![使用公司入口網站進行驗證。](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > 如果您將設定檔屬性設定為 [使用使用者親和性註冊] 且未使用公司入口網站，多重要素驗證 (MFA) 在 DEP 註冊期間將無法運作。 註冊後，MFA 會如預期地在這些裝置上運作。 第一次登入時必須變更密碼的使用者不會收到裝置提示。 此外，密碼已過期的使用者也不會在註冊期間收到提示要重設其密碼。 使用者必須使用不同的裝置來重設密碼。

6. 選擇 [裝置管理設定]，並選取您是否想要監督使用此設定檔的裝置。
    **受監督**裝置可提供您更多管理選項，並且預設會停用 [啟用鎖定]。 Microsoft 建議使用 DEP 作為啟用受監督模式的機制，特別是針對將部署大量 iOS 裝置的組織。

    有兩種方式可通知使用者其裝置收到監督：

   - 鎖定畫面指出：「此 iPhone 受 Contoso 管理。」
   - [設定] > [一般] > [關於] 畫面指出：「此 iPhone 受監督。 Contoso 可以監視您的網際網路流量並找到此裝置。」

     > [!NOTE]
     > 註冊為不受監督的裝置，僅可透過使用 Apple Configurator 重設為受監督。 以這種方式將裝置重設，需要使用 USB 纜線將 iOS 裝置連接至 Mac。 在 [Apple Configurator 文件](http://help.apple.com/configurator/mac/2.3)上，深入了解這項作業。

7. 選擇您是否想要針對使用此設定檔的裝置鎖定註冊。 **鎖定的註冊**會停用可將管理設定檔從 [設定] 功能表中移除的 iOS 設定。 註冊裝置之後，必須將裝置恢復出廠預設值才能變更此設定。 這類裝置必須將**受監督**管理模式設為 [是]。 

8. 選擇您是否想要讓使用此設定檔的裝置**與電腦同步處理**。 若選擇 [依據憑證允許 Apple Configurator]，則必須在 [Apple Configurator 憑證] 下選擇憑證。

9. 若您在前一個步驟中選擇 [依據憑證允許 Apple Configurator]，則請選擇要匯入的 Apple Configurator 憑證。

10. 選擇 [確定]。

11. 選擇 [設定助理設定]，以設定下列設定檔的設定：![自訂設定助理](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)。


    |                 設定                  |                                                                                               說明                                                                                               |
    |------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |     <strong>部門名稱</strong>     |                                                             使用者在啟用期間點選 [關於設定] 時顯示。                                                              |
    |    <strong>部門電話</strong>     |                                                          在使用者在啟用期間按一下 [需要協助] 按鈕時顯示。                                                          |
    | <strong>設定助理選項</strong> |                                                     下列是選用設定，可稍後在 iOS [設定] 功能表中進行設定。                                                      |
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


12. 選擇 [確定]。

13. 若要儲存該設定檔，請選擇 [建立]。

## <a name="sync-managed-devices"></a>同步受管理裝置
由於 Intune 有管理您裝置的權限，您可以同步處理 Intune 與 Apple，以在 Azure 入口網站的 Intune 中查看受管理裝置。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > 選擇清單中的權杖 > [裝置] > [同步處理]。![選取 [註冊計劃裝置] 節點並選擇 [同步] 連結的螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/image06.png)

   為了符合 Apple 規定的可接受註冊計劃流量，Intune 具有下列限制︰
   - 完整同步處理每 7 天只能執行一次。 完整同步期間，每當 Apple 序號指派至 Intune 時，Intune 都會重新整理一次。 如果在上一次完整同步處理過後的 7 天內嘗試進行完整同步處理，Intune 只會重新整理尚未列在 Intune 中的序號。
   - 任何同步處理要求都會在 15 分鐘內完成。 在此期間或直到要求成功，會停用 [同步處理] 按鈕。
   - Intune 每 24 小時會與 Apple 同步一次新增及移除的裝置。

## <a name="assign-an-enrollment-profile-to-devices"></a>將註冊設定檔指派給裝置
必須先將註冊計劃設定檔指派至裝置，裝置才能註冊。

>[!NOTE]
>您也可以從 [Apple 序號] 刀鋒視窗中，將序號指派給設定檔。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > 選擇清單中的權杖。
2. 選擇 [裝置] > 選擇清單中的裝置 > [指派設定檔]。
3. 在 [指派設定檔] 下，選擇裝置的設定檔，然後選擇 [指派]。

### <a name="assign-a-default-profile"></a>指派預設設定檔

您可以針對使用特定權杖註冊的所有裝置，挑選要套用的預設設定檔。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > 選擇清單中的權杖。
2. 選擇 [設定預設設定檔]、在下拉式清單中選擇設定檔，然後選擇 [儲存]。 此設定檔將套用到使用該權杖註冊的所有裝置。

## <a name="distribute-devices"></a>散發裝置
您已啟用 Apple 與 Intune 之間的管理和同步，並指派設定檔以供您的 DEP 裝置註冊。 您現在可以將裝置散發給使用者。 具有使用者親和性的裝置會需要為每個使用者指派 Intune 授權。 沒有使用者親和性的裝置需要裝置授權。 裝置恢復出廠預設值之前，已啟動的裝置無法套用註冊設定檔。

請參閱[以裝置註冊計劃在 Intune 註冊 iOS 裝置](/intune-user-help/enroll-your-device-dep-ios)。


