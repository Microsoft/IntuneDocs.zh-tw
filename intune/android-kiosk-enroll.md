---
title: 在 Intune 中註冊 Android 企業 kiosk 裝置
titlesuffix: Microsoft Intune
description: 了解如何在 Intune 中註冊 Android 企業 kiosk 裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 90cd71383e8f2f82bf9fd6a3dc579c1c0a954227
ms.sourcegitcommit: d99def6e4ceb44f3e7ca10fe7cdd7f222cf814c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "42903138"
---
# <a name="set-up-enrollment-of-android-enterprise-kiosk-devices"></a>設定 Android 企業 kiosk 裝置的註冊

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android 支援 kiosk 樣式的裝置，其已設定公司所擁有的單次使用解決方案。 這類裝置用於單一用途，例如數位招牌、票證列印或庫存管理等等。 系統管理員會針對一組有限的應用程式和 Web 連結鎖定裝置使用。 它也會防止使用者新增其他應用程式，或在裝置上採取其他動作。

Intune 可協助您將應用程式和設定部署到 Android kiosk 裝置。 如需 Android 企業的特定詳細資料，請參閱 [Android 企業需求](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)。

您以這種方式管理的裝置不需要使用者帳戶即可在 Intune 中註冊，也不會與任何終端使用者建立關聯。 它們不適用於個人使用的應用程式，或對使用者特定帳戶資料 (例如 Outlook 或 Gmail) 有強烈需求的應用程式。

## <a name="device-requirements"></a>裝置需求

裝置必須符合下列需求，才能作為 Android 企業 kiosk 裝置進行管理：

- Android OS 5.1 版和更新版本。
- 裝置必須執行具有 Google Mobile Services (GMS) 連線能力的 Android 發行版本。 裝置必須有可用的 GMS ，而且必須能夠連線至 GMS。

## <a name="set-up-android-kiosk-management"></a>設定 Android kiosk 管理

若要設定 Android Kosk 管理，請遵循下列步驟：

1. 若要準備管理行動裝置，您必須[將行動裝置管理 (MDM) 授權單位設定為 **Microsoft Intune**](mdm-authority-set.md) 以取得相關指示。 此項目只會設定一次，也就是第一次為行動裝置管理設定 Intune 之時。
2. [將 Intune 租用戶帳戶連線至 Android 企業帳戶](connect-intune-android-enterprise.md)。
3. [建立註冊設定檔](#create-an-enrollment-profile)
4. [建立裝置群組](#create-a-device-group)。
5. [註冊 kiosk 裝置](#enroll-the-kiosk-devices)。

### <a name="create-an-enrollment-profile"></a>建立註冊設定檔

您必須建立註冊設定檔，才能註冊您的 kiosk 裝置。 建立設定檔時，它會為您提供註冊權杖 (隨機字串) 和 QR 代碼。 視 Android OS 和裝置的版本而定，您可以使用權杖或 QR 代碼來[註冊 kiosk 裝置](#enroll-the-kiosk-devices)。

1. 前往 [Intune 入口網站](https://portal.azure.com)，並選擇 [裝置註冊] > [Android 註冊] > [Kiosk 及工作裝置註冊]。
2. 選擇 [建立] 並填寫必要的欄位。
    - **名稱**：鍵入將設定檔指派給動態裝置群組時，您要使用的名稱。
    - **權杖到期日**：權杖到期的日期。 Google 最多可強制執行 90 天。
3. 選擇 [建立] 以儲存該設定檔。

### <a name="create-a-device-group"></a>建立裝置群組

您可以將應用程式和原則的目標設為指派的裝置群組或動態裝置群組。 透過遵循下列步驟，即可設定動態 AAD 裝置群組，以自動填入使用特定註冊設定檔註冊的裝置：

1. 前往 [Intune 入口網站](https://portal.azure.com)，並選擇 [群組] > [所有群組] > [新增群組]。
2. 在 [群組] 刀鋒視窗中填寫必要的欄位，如下所示：
    - **群組類型**：安全性
    - **群組名稱**：鍵入直覺式名稱 (例如 Factory 1 裝置)
    - **成員資格類型**：動態裝置
3. 選擇 [新增動態查詢]。
4. 在 [動態成員資格規則] 刀鋒視窗中填寫欄位，如下所示：
    - **新增動態成員資格規則**：簡單規則
    - **新增裝置，其中**：enrollmentProfileName
    - 在中間方塊中，選擇 [比對]。
    - 在最後一個欄位中，輸入您稍早建立的註冊設定檔名稱。
5. 選擇 [新增查詢] > [建立]。

### <a name="replace-or-remove-tokens"></a>取代或移除權杖

您可以取代或移除權杖和 QR 代碼。

- **取代權杖**：您可以在權杖/QR 代碼接近到期日時，使用 [取代權杖] 產生新的權杖/QR 代碼。
- **撤銷權杖**：您可以立即使權杖/QR 代碼過期。 從此時開始，權杖/QR 代碼不再可用。 在下列情況下，您可以使用此選項：
    - 意外地與未經授權的合作對象共用權杖/QR 代碼
    - 完成所有註冊，而不再需要權杖/QR 代碼

取代或撤銷權杖/QR 代碼不會對已註冊的裝置產生任何影響。

1. 前往 [Intune 入口網站](https://portal.azure.com)，並選擇 [裝置註冊] > [Android 註冊] > [Kiosk 及工作裝置註冊]。
2. 選擇您想要使用的設定檔。
3. 選擇 [權杖]。
4. 若要取代權杖，請選擇 [取代權杖]。
5. 若要撤銷權杖，請選擇 [撤銷權杖]。

## <a name="enroll-the-kiosk-devices"></a>註冊 kiosk 裝置

在建立註冊設定檔和動態裝置群組之後，您就可以註冊 kiosk 裝置。 註冊 Android 裝置的方式需視作業系統而定。

| 註冊方法 | 支援的最低 Android OS 版本 |
| ----- | ----- |
| 近距離無線通訊 | 5.1 |
| 權杖項目 | 6.0 |
| QR 代碼 | 7.0 |
| 零接觸 (Zero Touch) | 8.0，沒有參與的製造商 |

### <a name="enroll-by-using-near-field-communication-nfc"></a>使用近距離無線通訊 (NFC) 註冊

針對支援 NFC 之 Android 5.1 和更新版本的裝置，您可以建立特殊格式化的 NFC 標記來佈建您的裝置。 您可以使用自己的應用程式或任何 NFC 標記建立者工具。 如需詳細資訊，請參閱 [Google 的 Android 管理 API 文件](https://developers.google.com/android/management/provision-device#nfc_method)。

### <a name="enroll-by-using-a-token"></a>使用權杖註冊

針對 Android 6 和更新版本的裝置，您可以使用權杖來註冊裝置。 Android 6.1 和更新版本也可在使用 **aft#setup** 註冊方法時，利用 QR 代碼掃描。

1. 開啟恢復出廠預設值的裝置。
2. 在 [歡迎使用] 畫面上選取您的語言。
3. 連線至您的 [Wifi]，然後選擇 [下一步]。
4. 接受 Google 的條款和條件，然後選擇 [下一步]。
5. 在 Google 登入畫面上，輸入 **afw#setup** 而不是 Gmail 帳戶，然後選擇 [下一步]。
6. 針對 [Android 裝置原則] 應用程式選擇 [安裝]。
7. 繼續安裝此原則。  某些裝置可能需要接受額外的條款。 
8. 在 [註冊此裝置] 畫面上，允許您的裝置掃描 QR 代碼或選擇手動輸入權杖。
9. 遵循螢幕上的提示來完成註冊。 

### <a name="enroll-by-using-a-qr-code"></a>使用 QR 代碼註冊

在 Android 7 和更新版本的裝置上，您可以從註冊設定檔掃描 QR 代碼來註冊裝置。

> [!Note]
> 瀏覽器縮放可能會導致裝置無法掃描 QR 代碼。 增加瀏覽器縮放比例可解決此問題。

1. 若要在 Android 裝置上啟動 QR 讀取，請在恢復出廠預設值之後看到的第一個畫面上點選多次。
2. 若為 Android 7 和 8 的裝置，系統會提示您安裝 QR 讀取器。 Android 9 和更新版本的裝置已安裝 QR 讀取器。
3. 使用 QR 讀取器來掃描註冊設定檔的 QR 代碼，然後遵循螢幕上的提示進行註冊。

### <a name="enroll-by-using-google-zero-touch"></a>使用 Google 零接觸 (Zero Touch) 註冊

若要使用 Google 的零接觸系統，裝置必須支援該系統，並與屬於服務一部分的供應商建立關聯。  如需詳細資訊，請參閱 [Google 的零接觸方案網站](https://www.android.com/enterprise/management/zero-touch/)。 


1. 在零接觸主控台中建立新的設定。
2. 從 EMM DPC 下拉式清單中選擇 [Microsoft Intune]。
3. 在 Google 的零接觸主控台中，將下列 JSON 複製/貼上至 DPC extra 欄位中。 以您建立為註冊設定檔一部分的註冊權杖取代 *YourEnrollmentToken* 字串。 請務必用雙引號括住註冊權杖。

```
{ 
    "android.app.extra.PROVISIONING_DEVICE_ADMIN_COMPONENT_NAME": "com.google.android.apps.work.clouddpc/.receivers.CloudDeviceAdminReceiver", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_SIGNATURE_CHECKSUM": "I5YvS0O5hXY46mb01BlRjq4oJJGs2kuUcHvVkAPEXlg", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_PACKAGE_DOWNLOAD_LOCATION": "https://play.google.com/managed/downloadManagingApp?identifier=setup", 

    "android.app.extra.PROVISIONING_ADMIN_EXTRAS_BUNDLE": { 
        "com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "YourEnrollmentToken" 
    } 
} 
```
4. 選擇 [套用]。

## <a name="managing-apps-on-android-kiosk-devices"></a>在 Android kiosk 裝置上管理應用程式

只有指派類型[設定為必要](apps-deploy.md#to-assign-an-app)的應用程式可以安裝在 Android kiosk 裝置上。 應用程式從受控 Google Play 商店安裝的方式與 Android 工作設定檔裝置相同。

當應用程式開發人員將更新發佈至 Google Play 時，應用程式就會在受控裝置上自動更新。

若要從 Android kiosk 裝置移除應用程式，您可以執行下列其中一項：
-   刪除所需的應用程式部署。
-   建立應用程式的解除安裝部署。


## <a name="next-steps"></a>接下來的步驟
- [部署 Android kiosk 應用程式](apps-deploy.md)
- [新增 Android kiosk 設定原則](device-profiles.md)
