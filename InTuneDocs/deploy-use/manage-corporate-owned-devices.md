---
title: "管理公司擁有的裝置 | Microsoft Docs"
description: "根據裝置的類型、其購買方式和組織的需求，透過各種不同的方式註冊屬公司擁有的裝置。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 521a37044d6721fe905db7740329688ba2c24b35
ms.openlocfilehash: ae077d80e05b33d625285d796917f4f6c153ca3f
ms.lasthandoff: 01/31/2017


---

# <a name="enroll-corporate-owned-devices-by-using-intune"></a>使用 Intune 註冊屬公司擁有的裝置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

您可以根據裝置的類型、裝置的購買方式和組織的需求，透過各種不同的方式註冊屬組織擁有或屬公司擁有的裝置，以使用 Intune 進行管理。 您也可以安裝公司入口網站應用程式，來註冊及管理屬公司擁有的裝置，例如在「攜帶您自己的裝置」(BYOD) 的情況下。

所有平台的裝置預設都可以在 Intune 中註冊。 若要阻擋註冊裝置，請以系統管理員認證登入 [Microsoft Intune 管理員入口網站](http://manage.microsoft.com)。 選擇 [管理員] > [行動裝置管理] > [註冊規則]，然後清除您要封鎖之平台的核取方塊。

## <a name="enroll-corporate-owned-ios-devices"></a>註冊公司所擁有的 iOS 裝置

屬公司擁有的裝置註冊方法適用於「選擇您自己的裝置」(CYOD) 的情況。 在 CYOD 環境中，是由組織支付使用者所選取的裝置，而且是由組織管理裝置。

如果您提供使用者可從中選擇的 iOS 裝置，您可以預先設定註冊，在使用者在第一次啟動裝置時，由 Intune 管理裝置。 Intune 支援透過 [Apple 裝置註冊方案 (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) 註冊，或使用 Mac 電腦上的 Apple Configurator 工具進行[直接](ios-direct-enrollment-in-microsoft-intune.md)或[設定助理](ios-setup-assistant-enrollment-in-microsoft-intune.md)註冊。

了解如何[註冊屬公司擁有的 iOS 裝置](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)。

## <a name="create-a-device-enrollment-manager-account"></a>建立裝置註冊管理員帳戶

您可以在 Intune 中建立單一使用者裝置註冊管理員 (DEM) 帳戶，為您的組織管理大量行動裝置。 建立 DEM 帳戶之後，指定的帳戶管理員可以註冊比標準使用者可註冊的 15 部裝置更多的裝置。

您可以使用 DEM 帳戶，只註冊不是由單一特定使用者使用的裝置。 比方說，這些類型的裝置適合銷售點或公用程式應用程式，但對於需要存取電子郵件或公司資源的使用者而言則不適合。

了解如何[使用 DEM 帳戶註冊屬公司擁有的裝置](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)。

## <a name="enroll-corporate-owned-windows-10-enterprise-devices"></a>註冊屬公司擁有的 Windows 10 企業版裝置

如果您在組織中使用 Azure Active Directory Premium 或 Microsoft Enterprise Mobility Suite，您可以[註冊 Windows 10 企業版裝置](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview)。 當使用者在裝置上新增工作或學校帳戶時，裝置會自動標記為「屬公司擁有」。

## <a name="import-imei-numbers"></a>匯入 IMEI 編號

許多行動裝置製造商使用其裝置上稱為國際行動設備識別 (IMEI) 的唯一號碼。 您可以匯入您的組織所擁有之裝置的 IMEI 編號。 當裝置變成由 Intune 管理時，會將它標記為屬公司擁有的裝置。

了解如何[使用 IMEI 編號標記屬公司擁有的裝置](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)。

## <a name="identify-a-device-as-corporate-owned"></a>識別屬公司擁有的裝置

當下列任一條件成立時，Intune 會將裝置辨識為「公司的」：

 - 裝置[使用 DEM 帳戶註冊](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) (所有平台)。
 - 裝置使用 [Apple DEP](ios-device-enrollment-program-in-microsoft-intune.md) 或 [Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md) 註冊 (僅限 iOS)。
 - 裝置製造商[使用 IMEI 編號預先宣告裝置](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) (具有 IMEI 編號的所有平台)。
 - 裝置在 [Azure Active Directory 或 Enterprise Mobility Suite 中註冊為 Windows 10 企業版裝置](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview) (僅限 Windows 10)。

當裝置標記為公司裝置時，您會在系統管理員主控台中，看到該裝置記錄的 [擁有權] 資料行為 [公司]。 

