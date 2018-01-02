---
title: "如何在 Intune 中使用裝置類別"
titleSuffix: Azure portal
description: "了解如何運用使用者在 Intune 中註冊其裝置時可選擇的裝置類別。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ddcd4639c1f5a0949be46025e16e44d0b6ac6616
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2017
---
# <a name="map-device-groups"></a>對應裝置群組

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune 裝置類別，依據您所定義的類別，將裝置自動新增至群組，您即可更輕鬆地管理這些裝置。

裝置類別使用下列工作流程︰
1. 建立使用者註冊其裝置時將從中選擇的類別
3. 當 iOS 和 Android 裝置的使用者註冊其裝置時，他們必須從您設定的類別清單中選擇一個類別。 若要指派類別給 Windows 裝置，使用者必須使用公司入口網站 (如需更多詳細資料，請參閱本主題的**設定裝置群組之後**)。
4. 您接著可以將原則和應用程式部署至這些群組。

您可以建立任何想要的裝置類別，例如：
- 銷售點裝置
- 示範裝置
- 銷售額
- 帳戶處理
- Manager

## <a name="how-to-configure-device-categories"></a>如何設定裝置類別

### <a name="step-1---create-device-categories-in-the-intune-blade-of-the-azure-portal"></a>步驟 1 - 在 Azure 入口網站的 Intune 刀鋒視窗中，建立裝置類別
1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置註冊]。
3. 在 [裝置註冊] 刀鋒視窗中，選擇 [裝置類別]。
4. 在 [裝置類別] 頁面上，選擇 [建立] 以新增新的類別。
5. 在下一個刀鋒視窗中，為新類別輸入 [名稱]，以及選用的 [描述]。
6. 完成時按一下 [建立]。 您會看到剛才於類別清單中所建立的類別。

當您在步驟 2 中建立 Azure Active Directory 安全性群組時，您將會使用裝置類別名稱。

### <a name="step-2---create-azure-active-directory-security-groups"></a>步驟 2 - 建立 Azure Active Directory 安全性群組
在此步驟中，您將根據裝置類別和裝置類別名稱，在 Azure 入口網站中建立動態群組。

若要繼續，請參閱 Azure Active Directory 文件中的[使用屬性來建立進階規則](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects)主題。

您可以使用此章節中的資訊，運用 **deviceCategory** 屬性來建立具有進階規則的裝置群組。 例如 (**device.deviceCategory -eq** "*<the device category name you got from the Azure portal>*")

您設定好裝置群組之後，使用者註冊好其裝置，即會看到您設定的類別清單。 選擇類別並完成註冊之後，他們的裝置會新增至與其所選類別相對應的 Active Directory 安全性群組中。

### <a name="how-to-view-the-categories-of-devices-you-manage"></a>如何檢視您管理的裝置類別

1.  在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 Azure 入口網站的 [Intune] 刀鋒視窗中，選擇 [裝置和群組]。

3.  在 [管理] 之下，按一下 [所有裝置]。

4.  在裝置清單中，檢查 [類別] 資料行。

如果沒有顯示 [類別] 資料行，請按一下 [資料行]，從清單中選擇 [類別]，然後按一下 [套用]。

### <a name="to-change-the-category-of-a-device"></a>變更裝置類別

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置和群組]。
4. 在 [裝置和群組] 刀鋒視窗中，選擇 [管理]  > [所有裝置]。
5. 在裝置清單中，選擇您的裝置，然後在 [裝置屬性] 刀鋒視窗中，選擇 [管理]  > [屬性]。
6. 在下一個刀鋒視窗中，您可將所選裝置的 [裝置類別] 變更為任一您先前設定的類別名稱。

## <a name="after-you-configure-device-groups"></a>設定裝置群組之後

當 iOS 和 Android 裝置的使用者註冊其裝置時，他們必須從您設定的類別清單中選擇一個類別。 選擇類別並完成註冊之後，他們的裝置會新增至與其所選類別相對應的 Intune 裝置群組或 Active Directory 安全性群組。

無論何種平台，您的使用者一律可在註冊裝置後移至 portal.manage.microsoft.com。 讓使用者存取公司入口網站，並移至 [我的裝置]。 他們可以選擇頁面中列出的已註冊裝置，然後選取類別。

選擇類別之後，裝置就會自動新增至您建立的對應群組。 如果裝置在您設定類別之前就已註冊，則使用者將會在公司入口網站上看到關於該裝置的通知，並將在使用者下次於 iOS 或 Android 上存取公司入口網站應用程式時，要求他們選取類別。

## <a name="further-information"></a>進一步資訊
- 您可以在 Azure 入口網站中編輯裝置類別，但如果這麼做，就必須手動更新所有參考此類別的 Azure Active Directory 安全性群組。

- 如果刪除類別時，則所有指派給該類別的裝置，之後會顯示該類別名稱為**未指派**。
