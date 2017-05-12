---
title: "為 iOS 裝置註冊 Apple Configurator 以及直接註冊"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何使用 Apple Configurator 透過直接註冊，來註冊公司擁有的 iOS 裝置。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 02675b6fe9872cb634d0515172f696cedc7e6463
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017


---

# <a name="enroll-ios-devices-with-apple-configurator-and-direct-enrollment"></a>為 iOS 裝置註冊 Apple Configurator 以及直接註冊 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune 支援使用 Mac 電腦上所執行的 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)，來註冊屬公司擁有的 iOS 裝置。 此程序並不會將裝置重設成出廠預設值，並使用預先定義的原則來註冊裝置。 此方法適用於**無使用者親和性**的裝置，且需要透過 USB 將 iOS 裝置連線到 Mac 電腦，以設定公司註冊。

>[!NOTE]
>此註冊方法不能與[裝置註冊管理員](enroll-devices-using-device-enrollment-manager.md)方法一起使用。

直接註冊 iOS 裝置時，您不需要該裝置的序號即可註冊裝置。 您也可以在 Intune 於註冊階段擷取裝置名稱之前，先命名該裝置以供識別。 直接註冊的裝置不支援公司入口網站應用程式。 本指南假設您在 Mac 電腦上使用 Apple Configurator 2.0。

註冊 iOS 裝置的其他方法，詳述於 [Choose how to enroll iOS devices in Intune](choose-ios-enrollment-method.md) (選擇如何在 Intune 中註冊 iOS 裝置)。


## <a name="prerequisites"></a>必要條件

請於設定 iOS 裝置註冊之前，先完成下列必要條件︰

- [設定網域](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [設定 MDM 授權單位](set-mdm-authority.md)
- [建立群組](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [設定公司入口網站](../manage-apps/company-portal-app.md)
- 指派 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)中的使用者授權
- [取得 Apple MDM Push Certificate](get-an-apple-mdm-push-certificate.md)
- 確認您確實可存取 iOS 裝置
- 具有裝置序號 (請參閱 [How to get an iOS serial number](https://support.apple.com//HT204308) (如何取得 iOS 序號))
- 備好 USB 連接線
- 請確定的 Mac 電腦已安裝有 [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)

## <a name="create-an-apple-configurator-profile-for-devices"></a>為建立裝置 Apple Configurator 設定檔

裝置註冊設定檔會定義套用至裝置群組的設定。 下列步驟示範如何針對使用 Apple Configurator 註冊的 iOS 裝置，建立裝置註冊設定檔。

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 Intune 刀鋒視窗上，選擇 [註冊裝置]，然後選擇 [Apple 註冊]。

3. 在 [管理 Apple Configurator 註冊設定] 下，選取 [AC 設定檔]。

4. 在 [Apple Configurator 註冊設定檔] 刀鋒視窗中，選取 [建立]。

5. 在 [建立註冊設定檔] 刀鋒視窗中，為設定檔輸入名稱以及描述。

6. 為 [使用者親和性] 選擇 [不搭配使用者親和性進行註冊]，以確保該裝置與使用者不會相關。 針對執行工作而不需存取本機使用者資料的裝置，請使用此關係。 需要使用者關聯的應用程式 (包含用於安裝企業營運應用程式的公司入口網站應用程式) 將無法運作。

7. 選取 [建立]儲存該設定檔。

## <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>將設定檔匯出為 iOS 裝置的 .mobileconfig

1. 在 [匯出設定檔] 刀鋒視窗中，將註冊設定檔下載到 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)，以直接推送到連線的 iOS 裝置，作為管理設定檔。 此方法不會將裝置恢復成出廠預設值。

2. 利用下列步驟，為裝置準備好 Apple Configurator。

   a. 在 Mac 電腦上，開啟 [Apple Configurator 2.0]。

   b。 將 iOS 裝置以 USB 線連接到 Mac 電腦。 關閉相片、iTunes 以及偵測到裝置時，為該裝置開啟的其他應用程式。

   c. 在 Apple Configurator 中，依序選擇已連線的 iOS 裝置和 [新增] 按鈕。 可以新增至裝置的選項會出現在下拉式清單中。 選擇 [設定檔]。

   d. 使用檔案選擇器選取您從 Intune 匯出的 .mobileconfig 檔案，然後選擇 [新增]。 設定檔會新增至裝置。 如果裝置「不受監督」，則需要在裝置上接受該安裝。

3. 使用下列步驟可在 iOS 裝置上安裝設定檔。 裝置必須已完成 [設定助理]，而且可供使用。 如果註冊需要應用程式部署，裝置應該要設定 Apple ID，因為應用程式部署將需要您具備登入 App Store 的 Apple ID。

   a. 解除鎖定 iOS 裝置。

   b。 在 [管理設定檔] 的 [安裝設定檔]對話方塊中，選擇 [安裝]。

   c. 提供裝置密碼或 Apple ID (如有必要時)。

   d. 接受**警告**，然後選擇 [安裝]。

   e. 接受**遠端警告**，然後選擇 [信任]。

   f. 當 [Profile Installed]\(安裝的設定檔) 方塊確認設定檔為 [已安裝] 時，選擇 [完成]。

4. 在 iOS 裝置上，開啟 [設定]，並前往 [一般]  >  [裝置管理]  >  [管理設定檔]。 確認其中有列出設定檔的安裝，並檢查 iOS 原則限制和已安裝的應用程式。 原則限制和應用程式可能需要 10 分鐘的時間才會出現在裝置上。

5. 散發裝置。 iOS 裝置現在已向 Intune 註冊並且受管理。

