---
title: 註冊 iOS 裝置 - 裝置註冊方案
titleSuffix: Microsoft Intune
description: 了解如何使用裝置註冊計劃來註冊屬公司擁有的 iOS 裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 9f27d8b2334ff38146949c28898040da6a714e0a
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032464"
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>使用 Apple 的裝置註冊計劃來自動註冊 iOS 裝置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

您現在可以透過 Apple [裝置註冊程式 (DEP)](https://deploy.apple.com) 設定 Intune 來註冊 iOS 裝置。 您可以在完全不需要接觸的情況下，啟用大量裝置的 DEP 註冊。 您可以將 iPhone 和 iPad 等裝置直接交付給使用者。 當使用者啟動裝置時，會以預先設定的設定來執行設定助理，並註冊裝置以接受管理。

若要啟用 DEP 註冊，您要使用 Intune 與 Apple DEP 入口網站。 需要序號或採購單編號的清單，以將裝置指派給 Intune 進行管理。 您可以建立 DEP 註冊設定檔，其中包含已在註冊期間套用至裝置的設定。

此外，DEP 註冊不能與[裝置註冊管理員](device-enrollment-manager-enroll.md)一起使用。

## <a name="what-is-supervised-mode"></a>何謂受監督模式？
Apple 在 iOS 5 中引進受監督模式。 處於受監督模式的 iOS 裝置可以透過更多控制進行管理。 因此，特別適用於屬公司擁有的裝置。 Intune 支援針對受監督模式設定裝置，以作為 Apple 裝置註冊方案 (DEP) 的一部分。 

iOS 11 中對非監督式 DEP 裝置的支援已淘汱。 在 iOS 11 與更新版本中，應一律監督 DEP 設定裝置。 在未來的 iOS 版本中，將會忽略 DEP is_supervised 旗標。

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>先決條件
- [Apple 的裝置註冊計劃](http://deploy.apple.com)中所購買的裝置
- [MDM 授權單位](mdm-authority-set.md)
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>取得 Apple DEP 權杖

您必須先從 Apple 取得 DEP 權杖 (.p7m) 檔案，才能為 iOS 裝置註冊 DEP。 此權杖可讓 Intune 同步貴公司所擁有的 DEP 裝置資訊。 它也允許 Intune 將註冊設定檔上傳至 Apple，並將這些設定檔指派給裝置。

您可以使用 Apple DEP 入口網站建立 DEP 權杖。 您也可以使用 DEP 入口網站將裝置指派給 Intune 以便管理。

> [!NOTE]
> 若在移轉至 Azure 之前從 Intune 傳統入口網站刪除了權杖，Intune 可能會還原已刪除的 Apple DEP 權杖。 您可以從 Azure 入口網站再次刪除該 DEP 權杖。

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>步驟 1： 下載建立權杖所需的 Intune 公開金鑰憑證。

1. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊方案權杖] > [新增]。

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

> [!NOTE]
> 如果 VPP 權杖沒有足夠的公司入口網站授權，或如果權杖已過期，將會封鎖裝置。 當權杖即將到期或授權偏低時，Intune 將會顯示警示。
 

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖]。
2. 選取權杖，選擇 [設定檔]，然後選擇 [建立設定檔]。

    ![[建立設定檔] 螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/image04.png)

3. 在 [建立設定檔] 下，為設定檔輸入系統管理用的**名稱**以及**描述**。 使用者看不到這些詳細資料。 您可以使用此 [名稱] 欄位，在 Azure Active Directory 中建立動態群組。 設定檔名稱可用來定義 enrollmentProfileName 參數，以註冊具備此註冊設定檔的裝置。 深入了解 [Azure Active Directory 動態群組](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects)。

    ![設定檔名稱與描述。](./media/device-enrollment-program-enroll-ios/image05.png)

4. 針對 [使用者親和性]，為具備此設定檔的裝置選擇需要或不需要由指派的使用者來進行註冊。
    - **搭配使用者親和性進行註冊** - 針對屬於使用者的裝置，以及想要使用公司入口網站進行像是安裝應用程式等服務的裝置，選擇此選項。 如果使用 ADFS 並且註冊設定檔將 [不向設定輔助程式驗證，而向公司入口網站驗證] 設定為 [否]，則需要 [WS-Trust 1.3 使用者名稱/混合端點](https://technet.microsoft.com/library/adfs2-help-endpoints) [深入了解](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

    - **不搭配使用者親和性進行註冊** - 針對未與任何使用者相關的裝置選擇此選項。 針對執行工作而不需存取本機使用者資料的裝置使用此選項。 公司入口網站應用程式之類的應用程式無法運作。

5. 如果您選擇 [搭配使用者親和性進行註冊]，則可以選擇讓使用者使用公司入口網站進行驗證，而不是 Apple 設定助理。

    ![使用公司入口網站進行驗證。](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > 如果您要執行以下任何操作，請將 [不向 Apple 設定輔助程式驗證，而向公司入口網站驗證] 設定為 [是]。
    >    - 使用多重要素驗證
    >    - 提示第一次登入時必須變更密碼的使用者
    >    - 提示使用者在註冊期間重設其過期密碼
    >
    > 使用 Apple 設定助理進行驗證時，不支援這些功能。

6. 如果您針對 [使用公司入口網站進行驗證，而不使用 Apple 設定助理] 選擇 [是]，您可以選擇使用大量採購方案 (VPP) 權杖在裝置上自動安裝公司入口網站，而不需要使用者提供 Apple ID。 若要使用 VPP 安裝公司入口網站，請在 [使用 VPP 安裝公司入口網站] 下選擇權杖。 請確定權杖未過期，而且您有足夠的公司入口網站應用程式裝置授權。 如果權杖過期或授權不足，則 Intune會改為安裝 App Store 公司入口網站，並提示您輸入 Apple ID。

    ![[使用 VPP 安裝公司入口網站] 的螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/install-cp-with-vpp.png)

7. 如果您為 [使用 VPP 安裝公司入口網站] 選擇權杖，您可以選擇在設定助理完成之後，立即以單一應用程式模式 (具體來說就是公司入口網站應用程式) 鎖定裝置。 在 [Run Company Portal in Single App Mode until authentication] \(驗證前以單一應用程式模式執行公司入口網站\) 選擇 [是]，設定此選項。 若要使用裝置，使用者必須先使用公司入口網站登入進行驗證。
    此功能僅針對 iOS 11.3.1 和更新版本支援。

8. 選擇 [裝置管理設定]，並選取您是否想要監督使用此設定檔的裝置。

    ![裝置管理設定螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/devicemanagementsettingsblade.png)

    **受監督**裝置可提供您更多管理選項，並且預設會停用 [啟用鎖定]。 Microsoft 建議使用 DEP 作為啟用受監督模式的機制，特別是針對將部署大量 iOS 裝置的組織。

    有兩種方式可通知使用者其裝置收到監督：

   - 鎖定畫面顯示：「此 iPhone 受 Contoso 管理。」
   - [設定] > [一般] > [關於] 畫面顯示：「此 iPhone 受監督。 Contoso 可以監視您的網際網路流量並找到此裝置。」

     > [!NOTE]
     > 註冊為不受監督的裝置，僅可透過使用 Apple Configurator 重設為受監督。 以這種方式將裝置重設，需要使用 USB 纜線將 iOS 裝置連接至 Mac。 在 [Apple Configurator 文件](http://help.apple.com/configurator/mac/2.3)上，深入了解這項作業。

9. 選擇您是否想要針對使用此設定檔的裝置鎖定註冊。 **鎖定的註冊**會停用可將管理設定檔從 [設定] 功能表中移除的 iOS 設定。 註冊裝置之後，必須抹除裝置才能變更此設定。 這類裝置必須將**受監督**管理模式設為 [是]。 

10. 選擇您是否想要讓使用此設定檔的裝置**與電腦同步處理**。 若選擇 [依據憑證允許 Apple Configurator]，則必須在 [Apple Configurator 憑證] 下選擇憑證。

11. 若您在前一個步驟中選擇 [依據憑證允許 Apple Configurator]，則請選擇要匯入的 Apple Configurator 憑證。

12. 選擇 [確定]。

13. 選擇 [設定助理自訂]，對下列設定檔設定進行設定：![設定助理自訂。](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    | 部門設定 | 描述 |
    |---|---|
    | <strong>部門名稱</strong> | 使用者在啟用期間點選 [關於設定] 時顯示。 |
    |    <strong>部門電話</strong>     | 在使用者在啟用期間按一下 [需要協助] 按鈕時顯示。 |

  您可以選擇當使用者設定裝置時，要在裝置上顯示或隱藏各種不同的設定助理畫面。
  - 如果您選擇 [隱藏]，則不會在設定期間顯示畫面。 設定好裝置之後，使用者仍然可以進入 [設定] 功能表來設定此功能。
  - 如果您選擇 [顯示]，將會在設定期間顯示畫面。 使用者有時可以跳過畫面而不採取動作。 但是他們隨後可以進入裝置的 [設定] 功能表來設定此功能。 


    | 設定助理畫面設定 | 如果您選擇 [顯示]，裝置會在設定期間... |
    |------------------------------------------|------------------------------------------|
    | <strong>密碼</strong> | 提示使用者輸入密碼。 除非裝置受到保護，或以其他方式控制存取 (例如，將裝置限制為單一應用程式的 Kiosk 模式)，否則一律需要密碼。 |
    | <strong>位置服務</strong> | 提示使用者輸入其位置。 |
    | <strong>還原</strong> | 顯示 [應用程式與資料] 畫面。 此畫面可讓使用者選擇在設定裝置時，要從 iCloud 備份還原或傳送資料。 |
    | <strong>iCloud 與 Apple ID</strong> | 可讓使用者選擇使用其 **Apple ID** 登入並使用 **iCloud**。                         |
    | <strong>條款和條件</strong> | 需要使用者接受 Apple 的條款及條件。 |
    | <strong>Touch ID</strong> | 可讓使用者選擇設定裝置的指紋識別。 |
    | <strong>Apple Pay</strong> | 可讓使用者選擇在裝置上設定 Apple Pay。 |
    | <strong>縮放</strong> | 可讓使用者選擇在設定裝置時縮放顯示畫面。 |
    | <strong>Siri</strong> | 可讓使用者選擇設定 Siri。 |
    | <strong>診斷資料</strong> | 向使用者顯示 [診斷] 畫面。 此畫面可讓使用者選擇將診斷資料傳送給 Apple。 |


14. 選擇 [確定]。

15. 若要儲存該設定檔，請選擇 [建立]。

## <a name="sync-managed-devices"></a>同步受管理裝置
由於 Intune 有管理您裝置的權限，您可以同步處理 Intune 與 Apple，以在 Azure 入口網站的 Intune 中查看受管理裝置。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > 選擇清單中的權杖 > [裝置] > [同步處理]。![選取 [註冊計劃裝置] 節點並選擇 [同步] 連結的螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/image06.png)

   為了符合 Apple 規定的可接受註冊計劃流量，Intune 具有下列限制︰
   - 完整同步處理每 7 天只能執行一次。 在完整同步期間，Intune 會擷取指派至已連線 Intune 之 Apple MDM 伺服器的序號完整更新清單。 若註冊計劃裝置從 Intune 入口網站刪除，但未從 DEP 入口網站中的 Apple MDM 伺服器解除指派，則在執行完整同步之前，該裝置都不會重新匯入 Intune。   
   - 同步會每 24 小時自動執行一次。 您也可以按一下 [同步] 按鈕來進行同步 (請勿在 15 分鐘內重複點選)。 所有同步要求都必須在 15 分鐘內完成。 [同步] 按鈕在同步完成前都會處於停用狀態。 此同步會重新整理現有的裝置狀態，以及匯入指派至 Apple MDM 伺服器的新裝置。   


## <a name="assign-an-enrollment-profile-to-devices"></a>將註冊設定檔指派給裝置
必須先將註冊計劃設定檔指派至裝置，裝置才能註冊。

>[!NOTE]
>您也可以從 [Apple 序號] 刀鋒視窗中，將序號指派給設定檔。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > 選擇清單中的權杖。
2. 選擇 [裝置] > 選擇清單中的裝置 > [指派設定檔]。
3. 在 [指派設定檔] 下，選擇裝置的設定檔 > [指派]。

### <a name="assign-a-default-profile"></a>指派預設設定檔

您可以針對使用特定權杖註冊的所有裝置，挑選要套用的預設設定檔。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > 選擇清單中的權杖。
2. 選擇 [設定預設設定檔]、在下拉式清單中選擇設定檔，然後選擇 [儲存]。 此設定檔將套用到使用該權杖註冊的所有裝置。

## <a name="distribute-devices"></a>散發裝置
您已啟用 Apple 與 Intune 之間的管理和同步，並指派設定檔以供您的 DEP 裝置註冊。 您現在可以將裝置散發給使用者。 具有使用者親和性的裝置會需要為每個使用者指派 Intune 授權。 沒有使用者親和性的裝置需要裝置授權。 在抹除裝置前，已啟動的裝置無法套用註冊設定檔。

請參閱[以裝置註冊計劃在 Intune 註冊 iOS 裝置](/intune-user-help/enroll-your-device-dep-ios)。

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
