---
# required metadata

title: iOS 裝置的相容性原則設定| Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4a59d24f-ed58-49b1-b874-b2d4aea3ec76

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Microsoft Intune 中 iOS 裝置的相容性原則設定

本主題所述的原則設定適用於執行 iOS 6 和更新版本的裝置。

如果您正在尋找其他平台的相關資訊，請選取下列其中一項︰
> [!div class="op_single_selector"]
- [Android 裝置的相容性原則設定](android-compliance-policy-settings-in-microsoft-intune.md)
- [Windows 裝置的相容性原則設定](windows-compliance-policy-settings-in-microsoft-intune.md)

## 系統安全性設定
### 密碼
- 需要密碼來解除鎖定行動裝置︰    先將此選項設為 [是] 以要求使用者輸入密碼， 再允許使用者存取其裝置。

- 會加密使用密碼的 iOS 裝置。

-  允許簡單密碼︰    先將此選項
- 設為 [是]，讓使用者建立簡單密碼，

- 例如，‘1234’ 或 ‘1111’。 密碼長度下限：
  -   指定使用者密碼中至少必須包含的
  -   數字位數或字元數下限。
  -   必要的密碼類型︰指定使用者必須建立
  -   英數字元還是數字密碼。

  字元集數目下限：如果 [必要的密碼類型] 設定為

  [英數字元]，請使用此設定指定密碼必須包含之
- 字元集數目下限。

- 四個字元集為：

- 小寫字母

- 大寫字母

- 符號 數字

### 若要將此設定設為較高的數目，使用者必須建立更複雜的密碼。
- 針對 iOS 裝置，此設定表示密碼中必須包含的特殊字元數 (例如 !、#、&amp;)。 在非使用狀態幾分鐘後需要輸入密碼：指定使用者必須重新輸入密碼之前的閒置時間。
  - 密碼到期 (天數)︰選取使用者密碼到期，
  - 且必須建立一個新密碼之前的天數。 記住密碼歷程記錄：共同使用此設定與 [不得重複使用以前用過的密碼] 可限制使用者 建立先前使用過的密碼。


- 不得重複使用以前用過的密碼︰如果選取 [記住密碼歷程記錄]，請指定 不得重複使用的舊密碼數。

     當裝置從閒置狀態返回時，需要密碼：

## 這項設定應該與 [在非使用狀態幾分鐘後需要輸入密碼] 設定一起使用。

- 系統將提示使用者輸入密碼，來存取

##  [在非使用狀態幾分鐘後需要輸入密碼] 設定所指定時間未作用的裝置。
- 電子郵件設定檔
必須由 Intune 管理電子郵件帳戶：將此選項設定為 [是] 時，裝置必須使用部署到裝置的電子郵件不相容。 在下列情況下，裝置視為不相容︰

- 電子郵件設定檔也必須部署至相同的使用者群組，做為相容性原則設為目標的使用者群組，否則使用者的裝置會視為不相容。 如果使用者已在符合部署到裝置之 Intune 電子郵件設定檔的裝置上設定電子郵件帳戶，則會將該裝置回報為不相容。


<!--HONumber=May16_HO2-->


