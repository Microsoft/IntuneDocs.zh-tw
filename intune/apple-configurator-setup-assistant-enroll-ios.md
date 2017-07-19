---
title: "註冊 iOS 裝置 - Apple Configurator 與設定助理"
titleSuffix: Intune on Azure
description: "了解如何使用 Apple Configurator 透過設定助理，來註冊公司擁有的 iOS 裝置。\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1d74fbcebfe89bbafc545d11dd6316cb602db8ee
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="enroll-ios-devices-with-apple-configurator"></a>使用 Apple Configurator 註冊 iOS 裝置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 支援使用 Mac 電腦上所執行的 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)，來註冊屬公司擁有的 iOS 裝置。 使用 Apple Configurator 註冊裝置時，會要求您透過 USB 連接方式，將每個 iOS 裝置連接至 Mac 電腦來設定公司註冊作業。 您可以透過兩種方式使用 Apple Configurator 將裝置註冊到 Intune 中：
- **設定助理註冊** - 將裝置重設為原廠設定，並將裝置備妥可執行設定助理，以及為裝置的新使用者安裝公司原則。 大多數的情況會需要將原則套用至 iOS 裝置 (包括使用者親和性)，以啟用 Intune 公司入口網站應用程式。
- **直接註冊** - 不會將裝置重設為原廠設定，並使用預先定義的原則來註冊裝置。 這個方法適用於**無使用者親和性**的裝置。

>[!NOTE]
>此註冊方法不能與[裝置註冊管理員](device-enrollment-manager-enroll.md)方法一起使用。

註冊 iOS 裝置的其他方法，詳述於 [Choose how to enroll iOS devices in Intune](enrollment-method-choose-ios.md) (選擇如何在 Intune 中註冊 iOS 裝置)。

## <a name="prerequisites"></a>必要條件

請於設定 iOS 裝置註冊之前，先完成下列必要條件︰

- [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- iOS 裝置的實體存取
- 裝置序號 (請參閱[尋找 Apple 產品的序號](https://support.apple.com//HT204308))
- USB 連接線
- 使用 [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 的 Mac 電腦
- [新增 Apple Configurator 序號](apple-configurator-serial-numbers-add.md)

## <a name="setup-assistant-enrollment"></a>設定助理註冊

### <a name="create-an-apple-configurator-profile-for-devices"></a>為建立裝置 Apple Configurator 設定檔

裝置註冊設定檔會定義套用至裝置群組的設定。 下列步驟示範如何針對使用 Apple Configurator 註冊的 iOS 裝置，建立裝置註冊設定檔。

1. 在 [Intune] 入口網站中，選擇 [裝置註冊]，然後選擇 [Apple 註冊]。
2. 在 [管理 Apple Configurator 註冊設定] 下，選取 [AC 設定檔]。
3. 在 [Apple Configurator 註冊設定檔] 刀鋒視窗中，選取 [建立]。
4. 在 [建立註冊設定檔] 刀鋒視窗中，為設定檔輸入名稱以及描述。
5. 為 [使用者親和性] 選擇具備此設定檔的裝置，在註冊時要或不要有使用者親和性。

   - **搭配使用者親和性進行註冊** - 裝置必須在初始設定期間與使用者建立關聯，之後便可以存取公司資料與電子郵件。 應要為受管理的裝置 (屬於使用者且需要將公司入口網站用於安裝應用程式等服務) 設定使用者親和性。
   - **不搭配使用者親和性進行註冊** - 該裝置不會與使用者建立關聯。 針對執行工作而不需存取本機使用者資料的裝置，請使用此關係。 需要使用者關聯的應用程式 (包含用於安裝企業營運應用程式的公司入口網站應用程式) 將無法運作。

6. 選取 [建立]儲存該設定檔。

### <a name="add-apple-configurator-serial-numbers"></a>新增 Apple Configurator 序號

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

想要[使用設定輔助程式的 Apple Configurator 註冊公司擁有的 iOS 裝置](apple-configurator-setup-assistant-enroll-ios.md)時，請使用下列步驟將序號新增至 Intune。 您可以一次新增一個序號，或上傳序號的逗點分隔值 (CSV) 檔案。 新增序號之後，可以為其指派一個設定檔。 設定檔包含您要套用到裝置的特定管理設定。

註冊 iOS 裝置的其他方法，詳述於 [Choose how to enroll iOS devices in Intune](enrollment-method-choose-ios.md) (選擇如何在 Intune 中註冊 iOS 裝置)。

**將 Apple Configurator 序號新增至 Intune**

1. 建立內含兩個資料行，但不含標題的逗點分隔值 (.csv) 清單。 在左資料行中新增 IMEI 識別碼，在右資料行中新增詳細資料。 清單目前最多可容納 500 個資料列。 在文字編輯器中，.csv 的外觀類似如下：

    F7TLWCLBX196,device details</br>
    DLXQPCWVGHMJ,device details

2. 在 Azure 入口網站中，選擇 [註冊裝置]，然後選擇 [Apple 註冊]。
3. 從 [管理 Apple Configurator 註冊設定] 下選取[Apple Configurator 序號]。
4. 在 [Apple Configurator 序號] 刀鋒視窗中選取 [新增]。
5. 在 [新增序號] 刀鋒視窗中，選取要套用到所匯入之序號的設定檔。 若要匯入的檔案內含會覆寫現有詳細資料的新詳細資料，請選取 [覆寫現有識別碼的詳細資料]，以新的詳細資料取代現有的詳細資料。
6. 瀏覽至序號的 .csv 檔案，並選取 [新增]。

### <a name="assign-a-profile-to-specific-serial-numbers"></a>將設定檔指派給特定的序號

Intune 可讓您從 Azure 入口網站中兩個的不同位置指派設定檔。 您可以透過 Apple Configurator 設定檔指派，或透過裝置指派。

#### <a name="assign-by-devices"></a>透過裝置指派
1. 在 [Intune] 入口網站中，選擇 [裝置註冊]，然後選擇 [Apple 註冊]。
3. 在 [Apple Configurator 裝置] 刀鋒視窗中，選取您要指派以設定檔的序號，然後選取 [指派設定檔]。
4. 在 [指派設定檔] 刀鋒視窗中，選取您要指派的設定檔，然後選取 [指派]。

#### <a name="assign-by-profiles"></a>透過設定檔指派
1. 在 [Intune] 入口網站中，選擇 [裝置註冊]，然後選擇 [Apple 註冊]。
2. 選擇 [AC 設定檔]，然後選取您要指派序號的設定檔。
3. 在為設定檔命名的刀鋒視窗中，選取 [序號]  >  [指派]。
4. 選取要指派給設定檔的序號，然後選取 [指派] 按鈕。

### <a name="export-the-profile-to-ios-devices"></a>將設定檔匯出到 iOS 裝置
在建立設定檔並指派序號之後，必須從 Intune 匯出設定檔 URL 或如下所述之格式的檔案。 然後手動將其匯入 Mac 上的 Apple Configurator 方案，Apple Configurator 方案接著會將其部署到裝置。

1. 在 Intune 入口網站中，選擇 [Apple Configurator 註冊設定檔] 刀鋒視窗，然後選擇要匯出的設定檔。
2. 在 [設定檔] 刀鋒視窗中，選取 [匯出設定檔]。
3. 在連結著 iOS 裝置的情況下，將設定檔 URL 複製到 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 中。 您稍後將在 Apple Configurator 中上傳它，以定義 iOS 裝置所使用的 Intune 設定檔。

  您將在下列程序中使用 Apple Configurator 將這個設定檔 URL 上傳至 Apple 服務，以定義 iOS 裝置所使用的 Intune 設定檔。
4. 使用 Apple Configurator 將此設定檔 URL 上傳至 Apple 服務，以定義 iOS 裝置所使用的 Intune 設定檔。
 1.  在 Mac 電腦上，開啟 [Apple Configurator 2] 在功能表列中，選擇 [Apple Configurator 2]，然後選擇 [喜好設定]。
  > [!WARNING]
  > 在註冊過程，會將裝置重設為原廠設定。 最佳做法是將裝置重設，並加以啟動。 當您將裝置連線時，裝置應該會在 **Hello** 畫面。
  2. 在 [喜好設定] 窗格中，選取 [伺服器]，然後選擇加號 (+) 來啟動 [MDM 伺服器精靈]。 選擇 **[下一步]**。
  3. 透過 Microsoft Intune，在 iOS 裝置的 [設定助理] 註冊下輸入 MDM 伺服器的**主機名稱或 URL** 及**註冊 URL**。 對於 [註冊 URL]，輸入從 Intune 匯出的註冊設定檔 URL。 選擇 **[下一步]**。  

    您可以放心地忽略指出「伺服器 URL 未經驗證」的警告。 請選擇 [下一步] 以繼續，直到精靈完成為止。
  4.  將 iOS 行動裝置連線到具有 USB 介面卡的 Mac 電腦。
  > [!WARNING]
  > 在註冊過程，會將裝置重設為原廠設定。 最佳做法是將裝置重設，並加以啟動。 當您啟動設定助理時，裝置應該會在 [Hello] 畫面上。
  5.  選擇 [準備]。 在 [準備 iOS 裝置] 窗格上，選取 [手動]，然後選擇 [下一步]。
  6. 在 [Enroll in MDM Server]\(在 MDM 伺服器中註冊) 窗格上，選取您建立的伺服器名稱，然後選擇 [下一步]。
  7. 在 [監督裝置]窗格上，選取監督層級，然後選擇 [下一步]。
  8. 在 [Create an Organization]\(建立組織) 窗格上，選擇 [組織] 或建立新的組織，然後選擇 [下一步]。
  9. 在 [Configure iOS Setup Assistant]\(設定 iOS 設定助理) 窗格上，選擇要呈現給使用者的步驟，然後選擇 [準備]。 若出現提示，請驗證以更新信任設定。  
  10. 當 iOS 裝置完成準備時，請拔除 USB 纜線。  
6.  **散發裝置**。
    裝置現在已準備好進行公司註冊。 關閉裝置，並將它們散發給使用者。 當使用者啟動其裝置時，設定助理就會啟動。

## <a name="direct-enrollment"></a>直接註冊
使用 Apple Configurator 直接註冊 iOS 裝置時，您不需要該裝置的序號即可註冊裝置。 您也可以在 Intune 於註冊階段擷取裝置名稱之前，先命名該裝置以供識別。 直接註冊的裝置不支援公司入口網站應用程式。 本指南假設您在 Mac 電腦上使用 Apple Configurator 2.0。

1. 在 [Intune] 入口網站中，依序選擇 [裝置註冊]、[Apple 註冊]，以及 [AC 設定檔]。
2. 在 [Apple Configurator 註冊設定檔] 刀鋒視窗中，選取 [建立]。
3. 在 [建立註冊設定檔] 刀鋒視窗中，為設定檔輸入名稱以及描述。
4. 為 [使用者親和性] 選擇 [不搭配使用者親和性進行註冊]，以確保該裝置與使用者不會相關。 針對執行工作而不需存取本機使用者資料的裝置，請使用此關係。 需要使用者關聯的應用程式 (包含用於安裝企業營運應用程式的公司入口網站應用程式) 將無法運作。
5. 選取 [建立]儲存該設定檔。

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>將設定檔匯出為 iOS 裝置的 .mobileconfig

1. 在 [匯出設定檔] 刀鋒視窗中，將註冊設定檔下載到 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)，以直接推送到連線的 iOS 裝置，作為管理設定檔。 此方法不會將裝置恢復成出廠預設值。
2. 利用下列步驟，為裝置準備好 Apple Configurator。
  1. 在 Mac 電腦上，開啟 [Apple Configurator 2.0]。
  2. 將 iOS 裝置以 USB 線連接到 Mac 電腦。 關閉相片、iTunes 以及偵測到裝置時，為該裝置開啟的其他應用程式。
  3. 在 Apple Configurator 中，依序選擇已連線的 iOS 裝置和 [新增] 按鈕。 可以新增至裝置的選項會出現在下拉式清單中。 選擇 [設定檔]。
  4. 使用檔案選擇器選取您從 Intune 匯出的 .mobileconfig 檔案，然後選擇 [新增]。 設定檔會新增至裝置。 如果裝置「不受監督」，則需要在裝置上接受該安裝。
3. 使用下列步驟可在 iOS 裝置上安裝設定檔。 裝置必須已完成 [設定助理]，而且可供使用。 如果註冊需要應用程式部署，裝置應該要設定 Apple ID，因為應用程式部署將需要您具備登入 App Store 的 Apple ID。
   1. 解除鎖定 iOS 裝置。
   2. 在 [管理設定檔] 的 [安裝設定檔]對話方塊中，選擇 [安裝]。
   3. 提供裝置密碼或 Apple ID (如有必要時)。
   4. 接受**警告**，然後選擇 [安裝]。
   5. 接受**遠端警告**，然後選擇 [信任]。
   6. 當 [Profile Installed]\(安裝的設定檔) 方塊確認設定檔為 [已安裝] 時，選擇 [完成]。

    4. 在 iOS 裝置上，開啟 [設定]，並前往 [一般]  >  [裝置管理]  >  [管理設定檔]。 確認其中有列出設定檔的安裝，並檢查 iOS 原則限制和已安裝的應用程式。 原則限制和應用程式可能需要 10 分鐘的時間才會出現在裝置上。

    5. 散發裝置。 iOS 裝置現在已向 Intune 註冊並且受管理。


## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>使用者在其裝置安裝及使用公司入口網站的方式

已設定使用者親和性的裝置可以安裝並執行公司入口網站 App，以下載 App 及管理裝置。 使用者收到裝置之後，必須如下所示完成一些額外的步驟，來完成設定助理並安裝公司入口網站應用程式。
