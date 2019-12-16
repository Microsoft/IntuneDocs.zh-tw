---
title: 在 Intune 中將裝置分組為群組
titleSuffix: Microsoft Intune
description: 了解如何將裝置分類成群組，以便管理。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8ee8bc3cdee9f61a901854e08000e9e2cbbb2864
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955366"
---
# <a name="categorize-devices-into-groups"></a>將裝置分類成群組

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

若要讓管理裝置變得更輕鬆，您可以使用 Microsoft Intune 裝置類別，以自動根據您定義的類別將裝置新增至群組。

裝置類別使用下列工作流程︰
1. 建立使用者註冊其裝置時可從中選擇的類別。
2. 當 iOS 和 Android 裝置的使用者註冊裝置時，他們必須從您設定的類別清單中選擇一個類別。 若要將類別指派給 Windows 裝置，使用者必須使用公司入口網站。
3. 您接著可以將原則和應用程式部署至這些群組。

您可以建立想要的任何裝置類別。 例如：
- 銷售點裝置
- 示範裝置
- 銷售額
- 帳戶處理
- Manager

## <a name="how-to-configure-device-categories"></a>如何設定裝置類別

### <a name="step-1-create-device-categories-on-the-intune-blade-of-the-azure-portal"></a>步驟 1：在 Azure 入口網站的 [Intune] 刀鋒視窗中，建立裝置類別
1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，選擇 [裝置]   > [裝置類別]  。
2. 在 [裝置類別]  頁面上，選擇 [建立]  以新增新的類別。
3. 在 [建立裝置類別]  刀鋒視窗中，為新類別輸入 [名稱]  ，以及選用的 [描述]  。
4. 完成之後，請選取 [建立]  。 您可以在類別清單中看到新類別。

當您在步驟 2 中建立 Azure Active Directory (Azure AD) 安全性群組時，將會使用裝置類別名稱。

### <a name="step-2-create-azure-active-directory-security-groups"></a>步驟 2：建立 Azure Active Directory 安全性群組
在此步驟中，您將根據裝置類別和裝置類別名稱，在 Azure 入口網站中建立動態群組。

若要繼續，請參閱 Azure AD 文件中的[使用屬性來建立進階規則](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects)。

請使用本節中的資訊，運用 **deviceCategory** 屬性來建立具有進階規則的裝置群組。 例如：**device.deviceCategory -eq** "*您從 Azure 入口網站取得的裝置類別名稱*"。

您設定好裝置群組之後，使用者註冊好其裝置，即會看到您設定的類別清單。 選擇類別並完成註冊之後，他們的裝置會新增至與其所選類別相對應的 Active Directory 安全性群組中。

### <a name="view-the-categories-of-devices-that-you-manage"></a>檢視您管理的裝置類別

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，選擇 [裝置]   > [所有裝置]  。

2. 在裝置清單中，檢查 [裝置類別]  資料行。

如果未顯示 [裝置類別]  資料行，請選取 [資料行]   > [類別]   > [套用]  。

### <a name="change-the-category-of-a-device"></a>變更裝置類別

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，選擇 [裝置]   > [所有裝置]  > 選擇想要的裝置 > [屬性]  。
2. 在下一個刀鋒視窗中，您可將所選裝置的 [裝置類別]  變更為任一您先前設定的類別名稱。

## <a name="after-you-configure-device-groups"></a>設定裝置群組之後

當 iOS 和 Android 裝置的使用者註冊其裝置時，他們必須從您設定的類別清單中選擇一個類別。 選擇類別並完成註冊之後，他們的裝置會新增至與其所選類別相對應的 Intune 裝置群組或 Active Directory 安全性群組。

Windows 使用者應該使用公司入口網站來選取類別。

無論何種平台，您的使用者一律都可在註冊裝置後，前往 portal.manage.microsoft.com。 請讓使用者存取公司入口網站，然後移至 [我的裝置]  。 使用者可以選擇該頁面上所列的已註冊裝置，然後選取類別。

選擇類別之後，裝置就會自動新增至您建立的對應群組。 如果某個裝置在您設定類別之前便已經註冊，使用者就會在公司入口網站上看到該裝置的相關通知。 這可讓使用者知道下次在 iOS 或 Android 上存取公司入口網站應用程式時，要選取一個類別。

## <a name="further-information"></a>進一步資訊
- 您可以在 Azure 入口網站中編輯裝置類別，但是必須手動更新所有參考此類別的 Azure AD 安全性群組。

- 若刪除某類別，指派給該類別的裝置會顯示類別名稱「未指派」  。
