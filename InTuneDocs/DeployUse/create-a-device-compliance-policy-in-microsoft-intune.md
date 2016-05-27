---
# required metadata

title: 在 Microsoft Intune 中建立裝置相容性原則 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5336dac0-a2cc-4cd4-8511-67e4f95bd700

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 在 Microsoft Intune 中建立裝置相容性原則
本主題概述您可用來建立裝置必須遵循的相容性原則步驟，以便視為相容。

##  步驟 1︰加入新原則
  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [原則] &gt; [相容性原則] &gt; [新增]

  ![Intune 管理主控台中相容性原則頁面的螢幕擷取畫面，顯示頁面頂端功能表中的新增選項](./media/intune-sa-3a-add-compliance-policy.png)

##  步驟 2：組態設定
在 [建立原則] 頁面上，視需要啟用設定：
  -   系統安全性設定 (例如密碼) 和加密
  -   裝置健全狀況設定，如裝置是否為 JB 破解，或者 Windows 裝置健全情況證明服務是否將裝置回報為狀況良好。
  -   裝置屬性設定，例如需要最低 OS 版本或允許最高 OS 版本。
![[建立原則] 頁面的 [一般] 索引標籤的螢幕擷取畫面 ](./media/intune-sa-3b-create-policy.png)

##  步驟 3：儲存原則
完成之後，請選擇 [儲存原則]

您可以選擇在儲存原則後立即部署原則，也可以選擇稍後再進行部署。 新的原則會顯示在 [原則] 工作區的 [相容性原則] 節點中。

## 支援的原則設定
下表列出相容性原則設定及其支援的平台。

-------------
|設定|iOS|Android|Windows|
|-----|----|-----|-----|
|需要密碼來解除鎖定行動裝置|iOS 6 和更新版本|Android 4.0 及更新版本 <br>Samsung KNOX 標準 4.0 及更新版本|Windows Phone 8 和更新版本|
|允許簡單密碼|iOS 6 和更新版本|不支援|Windows Phone 8 和更新版本|
|密碼長度下限|iOS 6 和更新版本| Android 4.0 及更新版本<br>Samsung KNOX 標準 4.0 及更新版本| Windows Phone 8 和更新版本<br>Windows 8.1|
|所需的密碼類型|iOS 6 和更新版本|無法使用|Windows Phone 8 和更新版本 <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|字元集數目下限|iOS 6 和更新版本|無法使用|Windows Phone 8 和更新版本 <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|密碼品質|無法使用|Android 4.0 及更新版本 <br>Samsung KNOX 標準 4.0 及更新版本|無法使用|
|要求密碼前的閒置分鐘數|iOS 6 和更新版本|Android 4.0 及更新版本<br>Samsung KNOX 標準 4.0 及更新版本|Windows Phone 8 和更新版本<br>Windows RT 和 Windows RT 8.1<br>Windows 8.1|
|密碼到期 (天數)|iOS 6 和更新版本|Android 4.0 及更新版本<br>Samsung KNOX 標準 4.0 及更新版本|Windows Phone 8 和更新版本<br>Windows RT 和 Windows RT 8.1<br>Windows 8.1|
|記住密碼歷程記錄|iOS 6 和更新版本|Android 4.0 及更新版本<br>Samsung KNOX 標準 4.0 及更新版本|Windows Phone 8 和更新版本<br>Windows RT 和 Windows RT 8.1<br>Windows 8.1|
|防止重複使用舊密碼|iOS 6 和更新版本|Android 4.0 及更新版本<br>Samsung KNOX 標準 4.0 及更新版本|Windows Phone 8 和更新版本<br>Windows RT 和 Windows RT 8.1<br>Windows 8.1|
|當裝置從閒置狀態返回時，需要密碼。| 無法使用| 無法使用|Windows 10 Mobile|
|在行動裝置上要求加密|不適用|Android 4.0 及更新版本<br>Samsung KNOX 標準 4.0 及更新版本|Windows Phone 8 和更新版本<br> Windows 8.1|
|需要裝置回報為狀況良好| 無法使用| 無法使用|Windows <br>Windows 10 Mobile|
|裝置不得 Jailbroken 或 Root 破解|iOS 6 和更新版本|Android 4.0 及更新版本<br>Samsung KNOX 標準 4.0 及更新版本|無法使用|
|電子郵件帳戶必須由 Intune 管理|iOS 6 和更新版本|無法使用| 無法使用|
|選取必須由 Intune 管理的電子郵件設定檔|iOS 6 和更新版本|無法使用| 無法使用|
|需要最低 OS|iOS 6 和更新版本|Android 4.0 及更新版本<br>Samsung KNOX 標準 4.0 及更新版本| Windows Phone 8 和更新版本<br>Windows 8.1|
|允許的最高 OS 版本|iOS 6 和更新版本|Android 4.0 及更新版本<br>Samsung KNOX 標準 4.0 及更新版本|Windows Phone 8 和更新版本<br>Windows 8.1|

選取下列其中一項以深入了解每個平台上支援的相容性設定︰
> [!div class="op_single_selector"]
- [IOS 裝置的相容性原則設定](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Android 裝置的相容性原則設定](android-compliance-policy-settings-in-microsoft-intune.md)
- [Windows 和 Windows Phone 的相容性原則設定 ](windows-compliance-policy-settings-in-microsoft-intune.md)


## 後續步驟
[部署和監視相容性原則](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### 請參閱
[裝置相容性原則簡介](introduction-to-device-compliance-policies-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


