---
title: 適用於 iOS 裝置的 Apple School Manager 計劃註冊
titleSuffix: Microsoft Intune
description: 了解如何設定 Apple School Manager 註冊計劃向 Intune 註冊公司擁有的 iOS 裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4c35a23e-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: fdda0edd8c7bf67dbfce9d428f1b3ce0266b3726
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032413"
---
# <a name="set-up-ios-device-enrollment-with-apple-school-manager"></a>使用 Apple School Manager 設定 iOS 裝置註冊

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

您可以將 Intune 設定為可註冊透過 [Apple School Manager](https://school.apple.com/) 計畫所購買的 iOS 裝置。 使用 Intune 與 Apple School Manager，您甚至不用碰到它們即可註冊大量的 iOS 裝置。 當學生或老師啟動裝置時，會以預先設定的設定來執行設定助理，並註冊裝置以接受管理。

若要啟用 Apple School Manager 註冊，您可以使用 Intune 和 Apple School Manager 入口網站。 需要序號或採購單編號的清單，以將裝置指派給 Intune 進行管理。 您可以建立 DEP 註冊設定檔，其中包含已在註冊期間套用至裝置的設定。

Apple School Manager 註冊無法搭配 [Apple 的裝置註冊計劃](device-enrollment-program-enroll-ios.md)或[裝置註冊管理員](device-enrollment-manager-enroll.md)使用。

**必要條件**
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- [MDM 授權單位](mdm-authority-set.md)
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- 若使用 ADFS，則使用者親和性需要 [WS-Trust 1.3 使用者名稱/混合端點](https://technet.microsoft.com/library/adfs2-help-endpoints)。 [深入了解](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。
- 從 [Apple School Management](http://school.apple.com) 方案購買的裝置

## <a name="get-an-apple-token-and-assign-devices"></a>取得 Apple 權杖並指派裝置

您必須先從 Apple 取得權杖 (.p7m) 檔案，才能為屬公司擁有的 iOS 裝置註冊 Apple School Manager。 此權杖可讓 Intune 同步 Apple School Manager 參與裝置的相關資訊。 它也允許 Intune 將註冊設定檔上傳至 Apple，並將這些設定檔指派給裝置。 當您在 Apple 入口網站時，也可以指派裝置序號以進行管理。

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-an-apple-token"></a>步驟 1： 下載建立 Apple 權杖所需的 Intune 公開金鑰憑證

1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > [新增]。

   ![取得註冊計劃權杖。](./media/device-enrollment-program-enroll-ios/image01.png)

2. 在 [註冊計劃權杖] 刀鋒視窗中，選擇 [下載您的公開金鑰憑證]，在本機下載並儲存加密金鑰 (.pem) 檔案。 這個 .pem 檔案會用於向 Apple School Manager 入口網站要求信任關係憑證。
     ![註冊計劃權杖刀鋒視窗。](./media/device-enrollment-program-enroll-ios/image02.png)

### <a name="step-2-download-a-token-and-assign-devices"></a>步驟 2： 下載權杖並指派裝置
1. 選擇 [透過 Apple School Manager 建立權杖]，並以您的公司 Apple ID 登入 Apple School。 您可以使用此 Apple ID 來更新 Apple School Manager 權杖。
2.  在 [Apple School Manager 入口網站](https://school.apple.com) 中，移至 [MDM 伺服器]，然後選擇 [新增 MDM 伺服器] (右上角)。
3.  輸入 **MDM 伺服器名稱**。 您可參考這個伺服器名稱，以識別行動裝置管理 (MDM) 伺服器， 但它不是 Microsoft Intune 伺服器的名稱或 URL。
   ![螢幕擷取畫面：選取序號選項的 Apple School Manager 入口網站](./media/asm-server-assignment.png)

4.  在 Apple 入口網站中選擇 [上傳檔案...]，瀏覽至 .pem 檔案，然後選擇 [儲存 MDM 伺服器] (右下角)。
5.  選擇 [取得權杖]，然後將伺服器權杖 (.p7m) 檔案下載到您的電腦。
6. 移至 [裝置指派]，然後手動輸入 [序號]、[訂單號碼]，或 [上傳 CSV 檔案] 來 [選擇裝置]。
     ![螢幕擷取畫面：選取序號選項的 Apple School Manager 入口網站](./media/asm-device-assignment.png)
7.  選擇 [指派給伺服器]，然後選擇您建立的 [MDM 伺服器]。
8. 指定 [選擇裝置] 的方式，然後提供裝置資訊和詳細資料。
9. 依序選擇 [Assign to Server]\(指派給伺服器)、針對 Microsoft Intune 指定的 &lt;伺服器名稱&gt; 以及 [確定]。

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>步驟 3： 儲存用以建立此權杖的 Apple ID

在 Azure 入口網站的 Intune 中，提供 Apple ID 供日後參考。

![指定要用於建立註冊計劃權杖的 Apple 識別碼，並瀏覽至註冊計劃權杖的螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>步驟 4： 上傳權杖
在 [Apple 權杖] 方塊中，瀏覽至憑證 (.pem) 檔案，選擇 [開啟]，然後選擇 [建立]。 使用推播憑證，透過將原則推送到已註冊的行動裝置，Intune 即可註冊和管理 iOS 裝置。 Intune 會從 Apple 自動同步處理您的 Apple School Manager 裝置。

## <a name="create-an-apple-enrollment-profile"></a>建立 Apple 註冊設定檔
安裝權杖之後，您可以為 Apple School 裝置建立註冊設定檔。 裝置註冊設定檔會定義要在註冊期間套用至裝置群組的設定。

1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖]。
2. 選取權杖，選擇 [設定檔]，然後選擇 [建立設定檔]。

3. 在 [建立設定檔] 下，為設定檔輸入系統管理用的**名稱**以及**描述**。 使用者看不到這些詳細資料。 您可以使用此 [名稱] 欄位，在 Azure Active Directory 中建立動態群組。 設定檔名稱可用來定義 enrollmentProfileName 參數，以註冊具備此註冊設定檔的裝置。 深入了解 [Azure Active Directory 動態群組](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects)。

    ![設定檔名稱與描述。](./media/device-enrollment-program-enroll-ios/image05.png)

4. 針對 [使用者親和性]，為具備此設定檔的裝置選擇需要或不需要由指派的使用者來進行註冊。
    - **搭配使用者親和性進行註冊** - 針對屬於使用者的裝置，以及想要使用公司入口網站進行像是安裝應用程式等服務的裝置，選擇此選項。 此選項也可讓使用者使用公司入口網站來驗證其裝置。 若使用 ADFS，則使用者親和性需要 [WS-Trust 1.3 使用者名稱/混合端點](https://technet.microsoft.com/library/adfs2-help-endpoints)。 [深入了解](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。   Apple School Manager 的「共用的 iPad」模式需要使用者不搭配使用者親和性進行註冊。

    - **不搭配使用者親和性進行註冊** - 針對未與任何使用者相關的裝置選擇此選項，例如共用的裝置。 針對執行工作而不需存取本機使用者資料的裝置使用此選項。 公司入口網站應用程式之類的應用程式無法運作。

5. 如果您選擇 [搭配使用者親和性進行註冊]，則可以選擇讓使用者使用公司入口網站進行驗證，而不是 Apple 設定助理。

    ![使用公司入口網站進行驗證。](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > 如果您要執行以下任何操作，請將 [不向 Apple 設定輔助程式驗證，而向公司入口網站驗證] 設定為 [是]。
    >    - 使用多重要素驗證
    >    - 提示第一次登入時必須變更密碼的使用者
    >    - 提示使用者在註冊期間重設其過期密碼
    >
    > 使用 Apple 設定助理進行驗證時，不支援這些功能。

6. 選擇 [裝置管理設定]，並選取您是否想要監督使用此設定檔的裝置。
    **受監督**裝置可提供您更多管理選項，並且預設會停用 [啟用鎖定]。 Microsoft 建議使用 DEP 作為啟用受監督模式的機制，特別是針對將部署大量 iOS 裝置的組織。

    有兩種方式可通知使用者其裝置收到監督：

   - 鎖定畫面顯示：「此 iPhone 受 Contoso 管理。」
   - [設定] > [一般] > [關於] 畫面顯示：「此 iPhone 受監督。 Contoso 可以監視您的網際網路流量並找到此裝置。」

     > [!NOTE]
     > 註冊為不受監督的裝置，僅可透過使用 Apple Configurator 重設為受監督。 以這種方式將裝置重設，需要使用 USB 纜線將 iOS 裝置連接至 Mac。 在 [Apple Configurator 文件](http://help.apple.com/configurator/mac/2.3)上，深入了解這項作業。

7. 選擇您是否想要針對使用此設定檔的裝置鎖定註冊。 **鎖定的註冊**會停用可將管理設定檔從 [設定] 功能表中移除的 iOS 設定。 註冊裝置之後，必須抹除裝置才能變更此設定。 這類裝置必須將**受監督**管理模式設為 [是]。 

8. 若要使用受控 Apple Id 來讓多個使用者登入已註冊的 iPad，請在 [共用的 iPad] (需要將 [不搭配使用者親和性進行註冊] 與 [受監督] 模式設為 [是]，才會有此選項) 之下選擇 [是]。受管理 Apple ID 是在 Apple School Manager 入口網站中建立的。 深入了解[共用的 iPad](education-settings-configure-ios-shared.md) 與 [Apple 共用的 iPad 需求](https://help.apple.com/classroom/ipad/2.0/#/cad7e2e0cf56) \(英文\)。

9. 選擇您是否想要讓使用此設定檔的裝置**與電腦同步處理**。 若選擇 [依據憑證允許 Apple Configurator]，則必須在 [Apple Configurator 憑證] 下選擇憑證。

10. 若您在前一個步驟中選擇 [依據憑證允許 Apple Configurator]，則請選擇要匯入的 Apple Configurator 憑證。

11. 選擇 [確定]。

12. 選擇 [設定助理設定]，對下列設定檔進行設定：![設定輔助程式自訂。](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


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


13. 選擇 [確定]。

14. 若要儲存該設定檔，請選擇 [建立]。

## <a name="connect-school-data-sync"></a>連線 School Data Sync
(選用) Apple School Manager 支援使用 Microsoft School Data Sync (SDS) 將類別名冊資料同步處理到 Azure Active Directory (AD)。 您僅可透過 SDS 同步處理一個權杖。 如果您透過 School Data Sync 設定另一個權杖，SDS 將會從之前擁有它的權杖中移除。 新的連線將取代目前的權杖。 請完成下列步驟以使用 SDS 同步學校資料。

1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖]。
2. 選取 Apple School Manager 權杖，然後選擇 [School Data Sync]。
3. 在 [School Data Sync] 下，選擇 [允許]。 此設定會允許 Intune 和 Office 365 中的 SDS 連線。
4. 若要啟用 Apple School Manager 與 Azure AD 之間的連線，請選擇 [設定 Microsoft School Data Sync]。深入了解[如何設定 School Data Sync](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1)。
5. 按一下 [儲存] > [確定]。

## <a name="sync-managed-devices"></a>同步受管理裝置

指派 Intune 權限以管理您的 Apple School Manager 裝置之後，就可以同步處理 Intune 與 Apple 服務，以便在 Intune 中查看受控裝置。

在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > 選擇清單中的權杖 > [裝置] > [同步處理]。![選取 [註冊計劃裝置] 節點並選擇 [同步] 連結的螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/image06.png)

  為了符合 Apple 規定的可接受註冊計劃流量，Intune 具有下列限制︰
  - 完整同步處理每 7 天只能執行一次。 完整同步期間，每當 Apple 序號指派至 Intune 時，Intune 都會重新整理一次。 如果在上一次完整同步處理過後的 7 天內嘗試進行完整同步處理，Intune 只會重新整理尚未列在 Intune 中的序號。
  - 任何同步處理要求都會在 15 分鐘內完成。 在此期間或直到要求成功，會停用 [同步處理] 按鈕。
  - Intune 每 24 小時會與 Apple 同步一次新增及移除的裝置。

>[!NOTE]
>您也可以從 [註冊計劃裝置] 刀鋒視窗，指派 Apple School Manager 序號給設定檔。

## <a name="assign-a-profile-to-devices"></a>將設定檔指派給裝置
在註冊由 Intune 管理的 Apple School Manager 裝置之前，必須將註冊設定檔指派給它們。

1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > 選擇清單中的權杖。
2. 選擇 [裝置] > 選擇清單中的裝置 > [指派設定檔]。
3. 在 [指派設定檔] 下，選擇裝置的設定檔，然後選擇 [指派]。

## <a name="distribute-devices-to-users"></a>將裝置散發給使用者

您已啟用 Apple 與 Intune 之間的管理和同步，並指派設定檔以供您的 Apple School 裝置註冊。 您現在可以將裝置散發給使用者。 當 iOS Apple School Manager 裝置開機時，就會加以註冊交由 Intune 管理。 如果裝置已啟動且正在使用中，則在抹除該裝置前，都無法套用設定檔。
