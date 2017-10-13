---
title: "設定 Apple School Manager 註冊計劃註冊 iOS 裝置"
titlesuffix: Azure portal
description: "了解如何設定 Apple School Manager 註冊計劃向 Intune 註冊公司擁有的 iOS 裝置\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: afb3aeff7a7c6cc481d24bac3a61de0816b4d34b
ms.sourcegitcommit: 001577b700f634da2fec0b44af2a378150d1f7ac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2017
---
# <a name="enable-ios-device-enrollment-with-apple-school-manager"></a>使用 Apple School Manager 啟用 iOS 裝置註冊

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主題將協助您針對透過 [Apple School Manager](https://school.apple.com/) 計劃購買的裝置啟用 iOS 裝置註冊。 使用 Intune 與 Apple School Manager，您甚至不用碰到它們即可註冊大量的 iOS 裝置。 當學生或老師啟動裝置時，會以預先設定的設定來執行設定助理，並註冊裝置以接受管理。

若要啟用 Apple School Manager 註冊，您可以使用 Intune 和 Apple School Manager 入口網站。 需要序號或採購單編號的清單，以將裝置指派給 Intune 進行管理。 您可以建立 DEP 註冊設定檔，其中包含已在註冊期間套用至裝置的設定。

另外，Apple School Manager 註冊無法搭配 [Apple 的裝置註冊計劃](device-enrollment-program-enroll-ios.md)或[裝置註冊管理員](device-enrollment-manager-enroll.md)使用。

**先決條件**
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- [MDM 授權單位](mdm-authority-set.md)
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- 使用者親和性需要 [WS-Trust 1.3 使用者名稱/混合端點](https://technet.microsoft.com/library/adfs2-help-endpoints)。 [深入了解](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。
- 從 [Apple School Management](http://school.apple.com) 方案購買的裝置

>[!NOTE]
>在具有使用者親和性的 Apple School Manager 裝置註冊期間，無法使用多重要素驗證 (MFA)。 註冊後，MFA 會如預期地在這些裝置上運作。 註冊後，MFA 會如預期地在這些裝置上運作。 第一次登入時必須變更密碼的使用者不會收到裝置提示。 此外，密碼已過期的使用者也不會在註冊期間收到提示要重設其密碼。 使用者必須使用不同的裝置來重設密碼。

## <a name="get-the-apple-token-and-assign-devices"></a>取得 Apple 權杖並指派裝置

您必須先從 Apple 取得權杖 (.p7m) 檔案，才能為屬公司擁有的 iOS 裝置註冊 Apple School Manager。 此權杖可讓 Intune 同步 Apple School Manager 參與裝置的相關資訊。 它也允許 Intune 將註冊設定檔上傳至 Apple，並將這些設定檔指派給裝置。 當您在 Apple 入口網站時，也可以指派裝置序號以進行管理。

**步驟 1.下載建立 Apple 權杖所需的 Intune 公開金鑰憑證。**<br>
1. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊]，然後選擇 [註冊計劃權杖]。

  ![[Apple 憑證] 工作區中 [註冊計劃權杖] 窗格下載公開金鑰的螢幕擷取畫面。](./media/enrollment-program-token-download.png)

2. 在 [註冊計劃權杖] 刀鋒視窗中，選擇 [下載您的公開金鑰憑證]，在本機下載並儲存加密金鑰 (.pem) 檔案。 這個 .pem 檔案會用於向 Apple School Manager 入口網站要求信任關係憑證。

**步驟 2.下載權杖並指派裝置。**<br>
1. 選擇 [透過 Apple School Manager 建立權杖]，並以您的公司 Apple ID 登入。 您可以使用此 Apple ID 來更新 Apple School Manager 權杖。
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

**步驟 3.輸入用以建立 Apple School Manager 權杖的 Apple ID。**<br>此 ID 應用來更新您的 Apple School Manager 權杖，並加以儲存以供未來參考。

![指定要用於建立註冊計劃權杖的 Apple 識別碼，並瀏覽至註冊計劃權杖的螢幕擷取畫面。](./media/enrollment-program-token-apple-id.png)

**步驟 4.找出並上傳您的權杖。**<br>
移至憑證 (.p7m) 檔案，選擇 [開啟]，然後選擇 [上傳]。 Intune 會從 Apple 自動同步您的 Apple School Manager 裝置。

## <a name="create-an-apple-enrollment-profile"></a>建立 Apple 註冊設定檔
裝置註冊設定檔會定義要在註冊期間套用至裝置群組的設定。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊]，然後選擇 [Apple 註冊]。
2. 在 [註冊計劃] 下方，選擇 [註冊計劃設定檔]。
3. 在 [註冊計劃設定檔] 刀鋒視窗中，選擇 [建立]。
4. 在 [建立註冊設定檔] 刀鋒視窗中，為 Intune 顯示的設定檔輸入 [名稱] 和 [描述]。
5. 為 [使用者親和性] 選擇具備此設定檔的裝置，在註冊時要或不要有使用者親和性。

 - **搭配使用者親和性進行註冊** - 在安裝期間建立裝置與使用者的關聯。

  Apple School Manager 的「共用的 iPad」模式需要使用者不搭配使用者親和性進行註冊。

 - **不搭配使用者親和性進行註冊** - 針對未與任何使用者相關的裝置選擇此選項，如共用裝置。 用於執行工作而不需存取本機使用者資料的裝置。 公司入口網站應用程式之類的應用程式無法運作。

6. 選擇 [裝置管理設定]。 這些項目是在啟用期間設定，且需要重設為原廠設定才能進行變更。 設定下列設定檔設定，然後選擇 [儲存]：

  ![選擇管理模式的螢幕擷取畫面。 裝置具有下列設定：受監督、鎖定的註冊、允許配對設定為全部拒絕。 Apple Configurator 憑證已為新的註冊計劃設定檔變灰。](./media/enrollment-program-profile-mode.png)

    - **受監督** - 啟用更多管理選項，且預設會停用 [啟用鎖定] 的管理模式。 若將核取方塊留為空白，則管理功能有限。

     - **鎖定的註冊** - (需要管理模式 = 受監督) 停用允許移除管理設定檔的 iOS 設定。 若將核取方塊留為空白，表示允許從 [設定] 功能表移除管理設定檔。
   - **共用的 iPad** - (需要 [不搭配使用者親和性進行註冊] 與受監督模式)。允許多位使用者使用受管理 Apple ID 登入註冊的 iPad。 受管理 Apple ID 是在 Apple School Manager 入口網站中建立的。 深入了解[共用的 iPad](education-settings-configure-ios-shared.md)。 您也應檢閱 [Apple 的共用 iPad 需求](https://help.apple.com/classroom/ipad/2.0/#/cad7e2e0cf56)。

   >[!NOTE]
   >如果將 [使用者親和性] 設定為 [搭配使用者親和性]，或將 [受監督] 模式設定為 [關閉]，就會停用註冊設定檔的「共用的 iPad」模式。

        - **Maximum Cached Users** - (Requires **Shared iPad** = **Yes**) Creates a partition on the device for each user. The recommended value is the number of students likely to use the device over a period of time. For example, if six students use the device regularly during the week, set this number to six.  

    - **允許配對** - 指定 iOS 裝置是否可與電腦同步。 若選擇 [依據憑證允許 Apple Configurator]，則必須在 [Apple Configurator 憑證] 下選擇憑證。

      - **Apple Configurator 憑證** - 如果在 [允許配對] 下選擇了 [依據憑證允許 Apple Configurator]，則請選擇要匯入的 Apple Configurator 憑證。

7. 選擇 [設定助理設定]，設定下列設定檔設定，然後選擇 [儲存]：

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

8. 若要儲存設定檔設定，請在 [建立註冊設定檔] 刀鋒視窗中，選擇 [建立]。

## <a name="connect-school-data-sync"></a>連線 School Data Sync
(選用) Apple School Manager 支援使用 Microsoft School Data Sync (SDS) 將類別名冊資料同步到 Azure Active Directory (AD)。 請完成下列步驟以使用 SDS 同步學校資料。

1. 在 [註冊程式權杖] 刀鋒視窗中，選擇藍色資訊橫幅或 [連線 SDS]。
2. 選擇 [允許 Microsoft School Data Sync 使用此權杖]，設定為 [允許]。 此設定會允許 Intune 和 Office 365 中的 SDS 連線。
3. 若要啟用 Apple School Manager 與 Azure AD 之間的連線，請選擇 [設定 Microsoft School Data Sync]。深入了解[如何設定 School Data Sync](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1)。
4. 按一下 [確定] 以儲存並繼續。

## <a name="sync-managed-devices"></a>同步受管理裝置
由於 Intune 已被指派管理您 Apple School Manager 裝置的權限，您可以同步處理 Intune 與 Apple 服務，以在 Intune 中查看受管理裝置。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊]，然後選擇 [Apple 註冊]。
2. 在 [註冊計劃裝置] 下，選擇 [同步]。進度列會顯示再次要求進行同步之前，必須要等待的總時間。
3. 在 [同步] 刀鋒視窗中，選擇 [要求同步]。進度列會顯示再次要求進行同步之前，必須要等待的總時間。

  ![[同步] 刀鋒視窗，以及正在選擇 [要求同步] 連結的螢幕擷取畫面。](./media/enrollment-program-device-request-sync.png)

  為了符合 Apple 規定的可接受流量，Intune 具有下列限制：
   -    完整同步處理每 7 天只能執行一次。 在完整同步處理期間，Intune 會重新整理 Apple 已指派給 Intune 的每個序號，不論先前是否已同步處理序號。 如果在上一次完整同步處理過後的 7 天內嘗試進行完整同步處理，Intune 只會重新整理尚未列在 Intune 中的序號。
   -    任何同步處理要求都會在 15 分鐘內完成。 在此期間或直到要求成功，會停用 [同步處理] 按鈕。

>[!NOTE]
>您也可以從 [註冊計劃裝置] 刀鋒視窗，指派 Apple School Manager 序號給設定檔。

## <a name="assign-a-profile-to-devices"></a>將設定檔指派給裝置
在註冊由 Intune 管理的 Apple School Manager 裝置之前，必須將註冊設定檔指派給它們。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊]，然後選擇 [註冊計劃設定檔]。
2. 從 [註冊計劃設定檔] 清單中，選擇您想要指派給裝置的設定檔，然後選擇 [Device Assignments] (裝置指派)。

 ![選取 [指派] 的 [裝置指派] 螢幕擷取畫面。](./media/enrollment-program-device-assign.png)

3. 選擇 [指派]，然後選擇您想要指派此設定檔的 Apple School Manager 裝置。 您可以篩選以檢視可用的裝置︰
  - **未指派**
  - **任何**
  - **&lt;設定檔名稱&gt;**
4. 選擇您想要指派的裝置。 資料行上方的核取方塊可選取最多 1000 個列出的裝置。 按一下 [指派]。 若要註冊 1000 部以上的裝置，請重複指派步驟，直到將註冊設定檔指派給所有的裝置為止。

  ![在 Intune 中用來指派註冊計劃設定檔的 [指派] 按鈕螢幕擷取畫面](media/dep-profile-assignment.png)

## <a name="distribute-devices-to-users"></a>將裝置散發給使用者

現在已可將公司擁有的裝置提供給使用者。 當 iOS Apple School Manager 裝置開機時，就會加以註冊交由 Intune 管理。 如果裝置已啟動且正在使用中，則在該裝置重設為原廠設定之前，將無法套用設定檔。
