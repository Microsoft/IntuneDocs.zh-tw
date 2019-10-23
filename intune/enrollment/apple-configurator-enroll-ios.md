---
title: iOS 裝置註冊 - Apple Configurator 與設定助理
titleSuffix: Microsoft Intune
description: 了解如何使用 Apple Configurator 透過設定助理，來註冊公司擁有的 iOS 裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 671e4d76-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 21ee59af8c6d24a42ce3f8c9fefedd0e5dba7ba7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503315"
---
# <a name="set-up-ios-device-enrollment-with-apple-configurator"></a>使用 Apple Configurator 設定 iOS 裝置註冊

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 支援註冊 iOS 裝置，這些裝置使用在 Mac 電腦執行上的 [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344)。 使用 Apple Configurator 註冊裝置時，會要求您透過 USB 連接方式，將每個 iOS 裝置連接至 Mac 電腦來設定公司註冊作業。 您可以透過兩種方式使用 Apple Configurator 將裝置註冊到 Intune 中：
- **設定助理註冊** - 抹除裝置，並準備好裝置在設定助理期間進行註冊。
- **直接註冊** - 不抹除裝置，而是透過 iOS 設定註冊裝置。 這個方法僅支援**無使用者親和性**的裝置。

Apple Configurator 註冊方法不能與[裝置註冊管理員](device-enrollment-manager-enroll.md)一起使用。

## <a name="prerequisites"></a>必要條件

- iOS 裝置的實體存取
- [設定 MDM 授權單位](../fundamentals/mdm-authority-set.md)
- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- 裝置序號 (僅設定助理註冊)
- USB 連接線
- 執行 [Apple Configurator 2.0](https://itunes.apple.com/app/apple-configurator-2/id1037126344) 的 macOS 電腦

## <a name="create-an-apple-configurator-profile-for-devices"></a>為建立裝置 Apple Configurator 設定檔

裝置註冊設定檔會在註冊期間定義套用的設定。 這些設定只套用一次。 請遵循下列步驟建立註冊設定檔，使用 Apple Configurator 註冊 iOS 裝置。

1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊]   > [Apple 註冊]   > [Apple Configurator]   > [設定檔]   > [建立]  。

    ![建立 Apple Configurator 設定檔](./media/apple-configurator-enroll-ios/apple-config-create-profile.png)

2. 或在 [建立註冊設定檔]  下，為設定檔輸入系統管理用的**名稱**以及**描述**。 使用者看不到這些詳細資料。 您可以使用此 [名稱] 欄位，在 Azure Active Directory 中建立動態群組。 設定檔名稱可用來定義 enrollmentProfileName 參數，以註冊具備此註冊設定檔的裝置。 深入了解 Azure Active Directory 動態群組。

    ![螢幕擷取畫面：選取了 [搭配使用者親和性進行註冊] 的設定檔建立畫面](./media/apple-configurator-enroll-ios/apple-configurator-profile-create.png)

3. 針對 [使用者親和性]  ，為具備此設定檔的裝置選擇需要或不需要由指派的使用者來進行註冊。

    - **搭配使用者親和性進行註冊** - 針對屬於使用者的裝置，以及想要使用公司入口網站進行像是安裝應用程式等服務的裝置，選擇此選項。 裝置必須使用設定助理與使用者建立關聯，然後才能存取公司資料與電子郵件。 僅設定助理註冊提供支援。 使用者親和性需要 [WS-Trust 1.3 使用者名稱/混合端點](https://technet.microsoft.com/library/adfs2-help-endpoints)。 [深入了解](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。

    - **不搭配使用者親和性進行註冊** - 針對未與任何使用者相關的裝置選擇此選項。 針對執行工作而不需存取本機使用者資料的裝置使用此選項。 需要使用者關聯的應用程式 (包含用於安裝企業營運應用程式的公司入口網站應用程式) 將無法運作。 直接註冊的必要項。

     > [!NOTE]
     > 選取 [搭配使用者親和性進行註冊]  時，請確定裝置是在註冊的前 24 小時內，與使用設定輔助程式的使用者建立關聯。 否則註冊可能會失敗，而且需要重設成出廠預設值才能註冊裝置。

4. 如果您選擇 [搭配使用者親和性進行註冊]  ，則可以選擇讓使用者使用公司入口網站進行驗證，而不是 Apple 設定助理。

    > [!NOTE]
    > 如果您要執行以下任何操作，請將 [不向 Apple 設定輔助程式驗證，而向公司入口網站驗證]  設定為 [是]  。
    >    - 使用多重要素驗證
    >    - 提示第一次登入時必須變更密碼的使用者
    >    - 提示使用者在註冊期間重設其過期密碼
    >
    > 使用 Apple 設定助理進行驗證時，不支援這些功能。


6. 選擇 [建立]  以儲存該設定檔。

## <a name="setup-assistant-enrollment"></a>設定助理註冊

### <a name="add-apple-configurator-serial-numbers"></a>新增 Apple Configurator 序號

1. 建立內含兩個資料行，但不含標題的逗點分隔值 (.csv) 清單。 在左資料行中新增序號，然後在右資料行中新增詳細資料。 清單目前最多可容納 5,000 個資料列。 在文字編輯器中，.csv 清單會像這樣：

    F7TLWCLBX196,device details</br>
    DLXQPCWVGHMJ,device details

   了解[如何尋找 iOS 裝置序號](https://support.apple.com/HT204073)。
2. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊]   > [Apple 註冊]   > [Apple Configurator]   > [裝置]   > [新增]  。

5. 選取 [註冊設定檔]  套用到要匯入的序號。 如果您希望新的序號詳細資料覆寫任何現有的詳細資料，請選擇 [覆寫現有識別碼的詳細資料]  。
6. 在 [匯入裝置]  下，瀏覽至序號的 csv 檔案，並選取 [新增]  。

### <a name="reassign-a-profile-to-device-serial-numbers"></a>重新將設定檔指派給裝置序號

當您匯入 Apple Configurator 註冊的 iOS 序號時，可以指派註冊設定檔。 您也可以在 Azure 入口網站中的兩個位置指派設定檔：
- **Apple Configurator 裝置**
- **AC 設定檔**

#### <a name="assign-from-apple-configurator-devices"></a>從 Apple Configurator 裝置指派
1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊]   > [Apple 註冊]   > [Apple Configurator]   > [裝置]  > 選擇序號 > [指派設定檔]  。
2. 在 [指派設定檔]  下，選取您要指派的 [新設定檔]  ，然後選取 [指派]  。

#### <a name="assign-from-profiles"></a>從設定檔指派
1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊]   > [Apple 註冊]   > [Apple Configurator]   > [設定檔]  > 選擇設定檔。
2. 在設定檔中選擇 [指派的裝置]  ，然後選擇 [指派]  。
3. 篩選尋找您想要指派給設定檔的裝置序號、選取裝置，然後選擇 [指派]  。

### <a name="export-the-profile"></a>匯出設定檔
建立設定檔並指派序號之後，您必須從 Intune 匯出設定檔當作 URL。 然後將它匯入 Mac 的 Apple Configurator 部署裝置。

1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊]   > [Apple 註冊]   > [Apple Configurator]   > [設定檔]  > 選擇要匯出的設定檔。
2. 在設定檔中，選取 [匯出設定檔]  。
3. 複製 [設定檔 URL]  。 然後，您可以在 Apple Configurator 中加以新增，以定義 iOS 裝置使用的 Intune 設定檔。

   接著，以下列程序將此設定檔匯入 Apple Configurator，定義 iOS 裝置使用的 Intune 設定檔。

### <a name="enroll-devices-with-setup-assistant"></a>使用設定助理註冊 iOS 裝置

1. 在 Mac 電腦上，開啟 [Apple Configurator 2]  在功能表列中，選擇 [Apple Configurator 2]  ，然後選擇 [喜好設定]  。
    > [!WARNING]
    > 在註冊過程中，裝置會重設為原廠設定。 最佳做法是將裝置重設，並加以啟動。 當您將裝置連線時，裝置應該會在 **Hello** 畫面。
    > 如果裝置已使用 Apple ID 帳戶註冊，則必須先從 Apple iCloud 中刪除裝置，然後再開始註冊程序。 錯誤提示顯示為「無法啟用 [裝置名稱]」。

2. 在 [喜好設定]  窗格中，選取 [伺服器]  ，然後選擇加號 (+) 來啟動 [MDM 伺服器精靈]。 選擇 **[下一步]** 。
3. 透過 Microsoft Intune，在 iOS 裝置的 [設定助理] 註冊下輸入 MDM 伺服器的**主機名稱或 URL** 及**註冊 URL**。 對於 [註冊 URL]，輸入從 Intune 匯出的註冊設定檔 URL。 選擇 **[下一步]** 。  
    您可以放心地忽略指出「伺服器 URL 未經驗證」的警告。 請選擇 [下一步]  以繼續，直到精靈完成為止。
4. 將 iOS 行動裝置連線到具有 USB 介面卡的 Mac 電腦。
5. 選取您要管理的 iOS 裝置，然後選擇 [準備]  。 在 [準備 iOS 裝置]  窗格上，選取 [手動]  ，然後選擇 [下一步]  。
6. 在 [Enroll in MDM Server]\(在 MDM 伺服器中註冊)  窗格上，選取您建立的伺服器名稱，然後選擇 [下一步]  。
7. 在 [監督裝置]  窗格上，選取監督層級，然後選擇 [下一步]  。
8. 在 [Create an Organization]\(建立組織)  窗格上，選擇 [組織]  或建立新的組織，然後選擇 [下一步]  。
9. 在 [Configure iOS Setup Assistant]\(設定 iOS 設定助理)  窗格上，選擇要呈現給使用者的步驟，然後選擇 [準備]  。 若出現提示，請驗證以更新信任設定。  
10. 當 iOS 裝置完成準備時，請拔除 USB 纜線。  

### <a name="distribute-devices"></a>散發裝置
裝置現在已準備好進行公司註冊。 關閉裝置，並將它們散發給使用者。 當使用者啟動其裝置時，設定助理就會啟動。

使用者收到裝置之後，他們必須完成設定助理。 已設定使用者親和性的裝置可以安裝並執行公司入口網站應用程式，以下載應用程式及管理裝置。

## <a name="direct-enrollment"></a>直接註冊
使用 Apple Configurator 直接註冊 iOS 裝置時，您不需要該裝置的序號即可註冊裝置。 您也可以在 Intune 於註冊階段擷取裝置名稱之前，先命名該裝置以供識別。 直接註冊的裝置不支援公司入口網站應用程式。 這個方法不會抹除裝置。

無法安裝需要使用者關係的應用程式，包括用於安裝企業營運應用程式的公司入口網站應用程式。

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>將設定檔匯出為 iOS 裝置的 .mobileconfig

1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊]   > [Apple 註冊]   > [Apple Configurator]   > [設定檔]  > 選擇要匯出的設定檔 > [匯出設定檔]  。
2. 在 [直接註冊]  下，選擇 [下載設定檔]  ，並儲存檔案。 註冊設定檔僅在兩週內有效，到期後您就必須重新建立。
3. 將檔案傳輸到執行 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 的 Mac 電腦，以直接推送為 iOS 裝置的管理設定檔。
4. 利用下列步驟，使用 Apple Configurator 來準備裝置：
    1. 在 Mac 電腦上，開啟 [Apple Configurator 2.0]。
    2. 將 iOS 裝置以 USB 線連接到 Mac 電腦。 關閉相片、iTunes 以及偵測到裝置時，為該裝置開啟的其他應用程式。
    3. 在 Apple Configurator 中，依序選擇已連線的 iOS 裝置和 [新增]  按鈕。 可以新增至裝置的選項會出現在下拉式清單中。 選擇 [設定檔]  。

        ![匯出設定助理註冊的螢幕擷取畫面，並醒目提示設定檔 URL](./media/apple-configurator-enroll-ios/ios-apple-configurator-add-profile.png)

    4. 使用檔案選擇器選取您從 Intune 匯出的 .mobileconfig 檔案，然後選擇 [新增]  。 設定檔會新增至裝置。 如果裝置「不受監督」，則需要在裝置上接受該安裝。
5. 使用下列步驟可在 iOS 裝置上安裝設定檔。 裝置必須已完成 [設定助理]，而且可供使用。 如果註冊需要應用程式部署，裝置應該要設定 Apple ID，因為應用程式部署需要您具備登入 App Store 的 Apple ID。
    1. 解除鎖定 iOS 裝置。
    2. 在 [管理設定檔]  的 [安裝設定檔]  對話方塊中，選擇 [安裝]  。
    3. 如有必要，請提供裝置密碼或 Apple ID。
    4. 接受**警告**，然後選擇 [安裝]  。
    5. 接受**遠端警告**，然後選擇 [信任]  。
    6. 當 [Profile Installed]\(安裝的設定檔)  方塊確認設定檔為 [已安裝] 時，選擇 [完成]  。

6. 在 iOS 裝置上，開啟 [設定]  ，並前往 [一般]   >  [裝置管理]   >  [管理設定檔]  。 確認其中有列出設定檔的安裝，並檢查 iOS 原則限制和已安裝的應用程式。 原則限制和應用程式可能需要 10 分鐘的時間才會出現在裝置上。

7. 散發裝置。 iOS 裝置現在已向 Intune 註冊並且受管理。





