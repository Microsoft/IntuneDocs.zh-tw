---
# required metadata

title: 應用程式生命週期概觀 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 應用程式生命週期的概觀

加入應用程式並進行其他階段時即開始 Intune 應用程式生命週期，直到您將它們移除。

![應用程式生命週期](./media/applifecycle_nobg.png "the Intune app lifecycle")

## 新增

應用程式部署的第一個步驟是加入您想要管理和部署到 Intune 的應用程式。 雖然您可以使用許多不同的應用程式類型，基本程序都相同。 Intune 可讓您同時為[註冊的裝置](add-apps-for-mobile-devices-in-microsoft-intune.md)和[使用 Intune 用戶端軟體管理的 Windows 電腦](add-apps-for-windows-pcs-in-microsoft-intune.md)加入應用程式.

## 部署

一旦您已將應用程式加入 Intune，您可以接著[將它部署到您管理的裝置](deploy-apps.md)。 Intune 讓此程序非常簡便，並且在應用程式部署之後，您可以從 Intune 管理主控台[監視部署成功](monitor-apps-in-microsoft-intune.md)。 此外，某些應用程式市集，例如 [Apple](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md) 和 [Windows](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md) 應用程式市集，可讓您為公司大量購買應用程式授權。 Intune 可以與這些市集同步處理資料，讓您直接從 Intune 管理主控台中部署和追蹤這些類型應用程式的授權使用情況。

## 設定

隨著應用程式生命週期，會定期發佈新版本的應用程式。 Intune 提供的工具，可輕鬆地[更新您已部署為新版本的應用程式](update-apps-using-microsoft-intune.md)。 此外，某些應用程式可讓您設定額外的功能，例如︰
- [iOS 應用程式組態原則](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md)可讓您提供執行應用程式時所使用之相容 iOS 應用程式的設定。 例如，應用程式可能需要特定的商標設定或伺服器的名稱才能連接。
- [受管理的瀏覽器原則](manage-internet-access-using-managed-browser-policies.md)可協助您設定 Intune 受管理瀏覽器的設定，其會取代預設的裝置瀏覽器，並可讓您限制使用者可以瀏覽的網站。

## 保護

Intune 提供您許多方法來協助保護您的應用程式中的資料。 主要方法如下︰
- [條件式存取](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)可讓您根據您指定的條件 (如裝置類型) 或與您部署的[裝置相容性原則](introduction-to-device-compliance-policies-in-microsoft-intune.md)的相容性，來控制對電子郵件及其他服務的存取。
- [行動應用程式管理 (MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md) 適用於個別的應用程式，可協助保護他們使用的公司資料。 例如，您可以限制在未受管理的應用程式與您管理的應用程式之間複製資料，或是可以防止應用程式在已進行 JB 或 Root 破解的裝置上執行。

## 淘汰

最後，您部署的應用程式很可能會過時，因此必須移除。 Intune 可讓您輕鬆地[從服務淘汰應用程式](retire-apps-using-microsoft-intune.md).


<!--HONumber=May16_HO1-->


