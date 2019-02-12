---
title: 在 Intune 中註冊 Android 專用裝置或完全受控裝置
titlesuffix: Microsoft Intune
description: 了解如何在 Intune 中註冊 Android 企業專用裝置或完全受控裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2a83676f67866bc81ea81f7bb721dec5825a95c9
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55843437"
---
# <a name="enroll-your-android-dedicated-devices-or-fully-managed-devices-preview"></a>註冊 Android 專用裝置或完全受控裝置 (預覽)

在 Intune 中設定 [Android 專用裝置](android-kiosk-enroll.md)或[完全受控裝置](android-fully-managed-enroll.md)後，即可註冊裝置。 註冊 Android 裝置的方式需視作業系統而定。

| 註冊方法 | 專用且完全受控裝置的最低 Android OS 版本 |
| ----- | ----- |
| 近距離無線通訊 | 5.1 |
| 權杖項目 | 6.0 |
| QR 代碼 | 7.0 |
| 零接觸 (Zero Touch)  | 8.0\* |

\* 僅限參與的製造商。

### <a name="enroll-by-using-near-field-communication-nfc"></a>使用近距離無線通訊 (NFC) 註冊

針對支援 NFC 的裝置，您可透過建立特殊格式化的 NFC 標籤，佈建您的裝置。 您可以使用自己的應用程式或任何 NFC 標記建立者工具。 如需詳細資訊，請參閱 [C-based Android Enterprise device enrollment with Microsoft Intune](https://blogs.technet.microsoft.com/cbernier/2018/10/15/nfc-based-android-enterprise-device-enrollment-with-microsoft-intune/) (使用 Microsoft Intune 註冊 C 型 Android Enterprise 裝置) 及 [Google's Android Management API documentation](https://developers.google.com/android/management/provision-device#nfc_method) (Google 的 Android 管理 API 文件)。

### <a name="enroll-by-using-a-token"></a>使用權杖註冊

針對 Android 6 和更新版本的裝置，您可以使用權杖來註冊裝置。 Android 6.1 和更新版本也可在使用 **afw#setup** 註冊方法時，利用 QR 代碼掃描。

1. 開啟已抹除的裝置。
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

1. 若要在 Android 裝置上啟動 QR 讀取，請在抹除之後看到的第一個畫面上點選多次。
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


## <a name="next-steps"></a>後續步驟
- [部署 Android 應用程式](apps-deploy.md)
- [新增 Android 設定原則](device-profiles.md)

