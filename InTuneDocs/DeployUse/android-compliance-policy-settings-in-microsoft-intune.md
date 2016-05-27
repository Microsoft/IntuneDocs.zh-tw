---
# required metadata

title: Android 裝置的相容性原則設定 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Microsoft Intune 中的 Android 裝置的相容性原則設定

本主題所述的原則設定適用於執行 Android 4.0 及更新版本，或 Samsung KNOX 4.0 及更新版本的裝置。

如果您正在尋找其他平台的相關資訊，請選取下列其中一項︰
> [!div class="op_single_selector"]
- [IOS 裝置的相容性原則設定](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Windows 裝置的相容性原則設定](windows-compliance-policy-settings-in-microsoft-intune.md)

## 系統安全性設定
### 密碼
- 需要密碼來解除鎖定行動裝置︰先將此選項設為 [是] 以要求使用者輸入密碼，

-  再允許使用者存取其裝置。

- 密碼長度下限：指定使用者密碼中至少必須包含的數字位數或字元數。 密碼品質：啟用此設定以設定 Android 裝置的密碼需求。
  -   **從下列選項進行選擇：**
  - **低安全性生物識別**
  -   **必要**
  -   **至少包含數字**
  -   **至少包含英數字元**
  -   **[至少包含英數字元]**

- 英數字元與符號

- 要求密碼前的閒置分鐘數：指定使用者必須重新輸入密碼之前的閒置時間。

- 密碼到期 (天數)︰選取使用者密碼到期，

- 且必須建立一個新密碼之前的天數。

- 記住密碼歷程記錄：共同使用此設定與 [不得重複使用以前用過的密碼] 可限制使用者 建立先前使用過的密碼。

### 不得重複使用以前用過的密碼︰如果選取 [記住密碼歷程記錄]，請指定
- 不得重複使用的舊密碼數。 當裝置從閒置狀態返回時，需要密碼：

## 這項設定應該與 [在非使用狀態幾分鐘後需要輸入密碼] 設定一起使用。

- 系統將提示使用者輸入密碼，來存取

## [在非使用狀態幾分鐘後需要輸入密碼] 設定所指定時間未作用的裝置。
- Encryption
  在行動裝置上要求加密：將此選項設為 [是]，要求先加密 裝置才能連接到資源。

- 裝置是在進行 [需要密碼來解除鎖定行動裝置]**
  ** 設定時加密


<!--HONumber=May16_HO2-->


