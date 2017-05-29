---
title: "如何在 Intune 中使用裝置類別"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何運用使用者在 Intune 中註冊其裝置時可選擇的裝置類別。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 0ac86a48c00c278b4d65dd7aabb096673fb2c00d
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="map-device-groups"></a>對應裝置群組


[!INCLUDE[azure_preview](./includes/azure_preview.md)]

使用 Microsoft Intune 裝置類別，依據您所定義的類別，將裝置自動新增至群組，您即可更輕鬆地管理這些裝置。

裝置類別使用下列工作流程︰
1.    建立使用者註冊其裝置時將從中選擇的類別
4.    當使用者註冊其裝置時，他們必須從您設定的類別清單中選擇一個類別。 如果裝置已註冊，則會在使用者下次存取公司入口網站應用程式時，要求使用者選取一個類別。


您可以建立任何想要的裝置類別，例如：
- 銷售點裝置
- 示範裝置
- 銷售額
- 帳戶處理
- Manager

## <a name="how-to-configure-device-categories"></a>如何設定裝置類別

### <a name="step-1---create-device-categories-in-the-intune-blade-of-the-azure-portal"></a>步驟 1 - 在 Azure 入口網站的 Intune 刀鋒視窗中，建立裝置類別
1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [註冊裝置]。
3. 在 [註冊] 刀鋒視窗中，選擇 [裝置類別]。
4. 在 [裝置類別] 頁面上，選擇 [建立] 以新增新的類別。
5. 在下一個刀鋒視窗中，為新類別輸入 [名稱]，以及選用的 [描述]。
6. 完成時按一下 [建立]。 您會看到剛才於類別清單中所建立的類別。

當您在步驟 2 中建立 Azure Active Directory 安全性群組時，您將會使用裝置類別名稱。

### <a name="step-2---create-azure-active-directory-security-groups"></a>步驟 2 - 建立 Azure Active Directory 安全性群組
在此步驟中，您將根據裝置類別和裝置類別名稱，在 Azure 入口網站中建立動態群組。

若要繼續，請參閱 Azure Active Directory 文件中的[使用屬性來建立進階規則](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects)主題。 

您可以使用此章節中的資訊，運用 **deviceCategory** 屬性來建立具有進階規則的裝置群組。 例如 (**device.deviceCategory -eq** "*<the device category name you got from the Intune portal>*")

您設定好裝置群組之後，使用者註冊好其裝置，即會看到您設定的類別清單。 選擇類別並完成註冊之後，他們的裝置會新增至與其所選類別相對應的 Active Directory 安全性群組中。

### <a name="how-to-view-the-categories-of-devices-you-manage"></a>如何檢視您管理的裝置類別

1.    在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 Azure 入口網站的 [Intune] 刀鋒視窗中，選擇 [裝置和群組]。

3.    在 [管理] 之下，按一下 [所有裝置]。

4.    在裝置清單中，檢查 [類別] 資料行。

如果沒有顯示 [類別] 資料行，請按一下 [資料行]，從清單中選擇 [類別]，然後按一下 [套用]。

### <a name="to-change-the-category-of-a-device"></a>變更裝置類別

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置和群組]。
4. 在 [裝置和群組] 刀鋒視窗中，選擇 [管理]  > [所有裝置]。
5. 在裝置清單中，選擇您的裝置，然後在 [裝置屬性] 刀鋒視窗中，選擇 [管理]  > [屬性]。
6. 在下一個刀鋒視窗中，您可將所選裝置的 [裝置類別] 變更為任一您先前設定的類別名稱。



## <a name="further-information"></a>進一步資訊
- 您可以在 Azure 入口網站中編輯裝置類別，但如果這麼做，就必須手動更新所有參考此類別的 Azure Active Directory 安全性群組。

- 如果刪除類別時，則所有指派給該類別的裝置，之後會顯示該類別名稱為**未指派**。



