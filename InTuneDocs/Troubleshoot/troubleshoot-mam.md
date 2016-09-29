---
title:
- "行動應用程式管理疑難排解 | Microsoft Intune"
description: 
keywords: 
author: karaman
manager: angerobe
ms.date: 09/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
translationtype: Human Translation
ms.sourcegitcommit: 9cfb3694b2fae919fd0554a6e21b497cdcf19c72
ms.openlocfilehash: f33e8de82ee07bb4571a5bfaff63af72f9086376


---

# 行動應用程式管理疑難排解

如果您有行動應用程式管理的問題，請從這裡開始。 本主題包含一些您在使用解決方案上可能會遇到的常見問題。


**問題**︰Azure 主控台中不使用註冊的 MAM 原則不適用於 iOS 和 Android 裝置上的商務用 Skype 應用程式。

解決方法︰商務用 Skype 必須設定為使用新式驗證。  請依照 [Enable your tenant for modern authentication](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) (啟用租用戶的新式驗證) 中的指示，設定 Skype 的新式驗證。

**問題**︰不使用註冊的 MAM 原則不適用於任何使用者 (支援的 Office 應用程式)[https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners]。
 
解決方法︰確認已針對 Intune 授權使用者。  

**問題**︰IT 系統管理員使用者無法在 Azure 入口網站中設定 MAM 原則

解決方法︰下列角色可以存取 Azure 入口網站：

- 全域管理員，您可以在 [Office 入口網站](http://portal.office.com/)中設定
- 擁有者，您可以在 [Azure 入口網站](https://portal.azure.com/)中設定。
- 參與者，您可以在 [Azure 入口網站](https://portal.azure.com/)中設定。

如需設定這些角色的說明，請參閱[準備使用 Microsoft Intune 設定行動應用程式管理原則](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)。 

**問題**︰應用程式報告未顯示 MAM 原則的最近目標使用者。

解決方法︰如果是 MAM 原則最近才設為目標的使用者，可能需要花費 24 小時，該使用者才會顯示在報表中成為目標使用者。 

**問題**︰原則變更/更新最多可能需要花費 8 小時來套用。  

解決方法︰使用者可以登出應用程式並重新登入，來強制與服務同步處理。  

**問題**︰MAM 原則不適用於 Apple DEP 裝置

解決方法︰請確定您搭配 Apple 裝置註冊方案 (DEP) 使用使用者親和性。 需要在 DEP 下進行使用者驗證的任何應用程式都需要有使用者親和性。
如需 iOS DEP 註冊的詳細資訊，請參閱[註冊屬公司擁有的裝置註冊方案 iOS 裝置](https://docs.microsoft.com/en-us/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune)。


### 請參閱
- [驗證您的行動應用程式管理設定](https://docs.microsoft.com/en-us/intune/deploy-use/validate-mobile-application-management)
- [準備使用 Microsoft Intune 設定行動應用程式管理原則](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) 





<!--HONumber=Sep16_HO2-->


