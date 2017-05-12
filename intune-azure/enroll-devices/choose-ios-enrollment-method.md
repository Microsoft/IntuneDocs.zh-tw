---
title: "選擇 iOS 裝置在 Intune 中的註冊方式"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何在 Microsoft Intune 中設定 iOS 裝置。"
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
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 3015c5493e8b38b425309584430c372e6a4d90cf
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017


---

# <a name="choose-how-to-enroll-ios-devices"></a>選擇 iOS 裝置的註冊方式

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

本主題說用可用於註冊 iOS 裝置的方式，以及註冊的先決條件。

您可以使用下列資訊決定註冊 iOS 裝置時所要使用的方法。 下列所有方法皆可用於註冊公司擁有的裝置，但 BYOD 除外。

**必要條件：**需要 [Apple 推播通知服務憑證](get-an-apple-mdm-push-certificate.md)。

## <a name="user-owned-ios-devices-byod"></a>使用者擁有的 iOS 裝置 (BYOD)

使用者若要註冊個人 (BYOD (自攜裝置)) 的裝置，唯一可使用的註冊方式就是從 App Store 下載 iOS 版的公司入口網站應用程式，並依照應用程式中的指示註冊。 一經註冊之後，使用者就能連線到公司網路、加入網域或 Azure Active Directory 及存取公司資源。 您可以封鎖註冊個人擁有的 iOS 裝置。 如需指示，請參閱[設定裝置類型限制](set-enrollment-restrictions.md#set-device-type-restrictions)。

## <a name="apple-configurator"></a>Apple Configurator

您可以藉由匯出公司註冊設定檔，再將 iOS 裝置連接到執行 [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) 的 Mac 來註冊這些行動裝置。 Apple Configurator 支援兩種註冊方式：

- **設定助理註冊**：將裝置重設為原廠設定值，並準備好裝置以供裝置的新使用者進行設定。 此方法需要系統管理員透過 USB 將 iOS 裝置連接到執行 Apple Configurator 的 Mac 電腦來預先設定註冊。 裝置接著將會傳遞至其使用者，該使用者將會執行設定助理程序。 此程序會利用使用者的工作或學校憑證來設定裝置及完成註冊程序。 如需詳細資訊，請參閱[使用設定輔助程式的 Apple Configurator 註冊 iOS 裝置](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)。

- **直接註冊**：建立 Apple Configurator 相容的檔案以供裝置期間使用。 註冊的裝置不會恢復出廠預設值，與使用者之間也不會有任何關係。 若要註冊裝置，透過 USB 將 iOS 裝置連接到執行 Apple Configurator 的 Mac 電腦。 如需詳細資訊，請參閱[使用 Apple Configurator 和直接註冊來註冊 iOS 裝置](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md)。

## <a name="use-the-device-enrollment-program-dep"></a>使用裝置註冊方案 (DEP)

DEP 會以「無線」的方式將設定檔部署到透過 DEP 購買的裝置上。 當使用者在裝置上執行設定助理時，該裝置便會在 Intune 中註冊。 透過 DEP 註冊的裝置不能由使用者取消註冊。 如需詳細資訊，請參閱[使用裝置註冊方案註冊 iOS 裝置](enroll-ios-devices-using-device-enrollment-program.md)。

## <a name="use-the-device-enrollment-manager-dem"></a>使用裝置註冊管理員 (DEM)
裝置註冊管理員是一種使用者帳戶類型，最多可以註冊及管理 1000 部裝置。 將現有的使用者新增到 DEM 帳戶，就能賦予他們這些能力。 DEM 使用者註冊的每一部裝置皆會佔用一份 Intune 授權。 如需詳細資訊，請參閱[使用裝置註冊管理員註冊 iOS 裝置](enroll-devices-using-device-enrollment-manager.md)。

