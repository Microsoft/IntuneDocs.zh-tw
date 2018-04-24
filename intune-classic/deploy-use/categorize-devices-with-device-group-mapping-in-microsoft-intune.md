---
title: 使用裝置群組對應分類裝置
description: 使用 Microsoft Intune 裝置群組對應來將裝置分組成定義的類別，以便讓您更輕鬆地管理那些裝置。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 06/06/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5a346c321147656d748d3abde78575268b20e9ab
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="categorize-devices-with-device-group-mapping-in-microsoft-intune"></a>在 Microsoft Intune 使用裝置群組對應分類裝置

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

使用 Microsoft Intune [裝置群組對應] 根據您定義的類別將裝置自動新增至群組，以便讓您更輕鬆地管理這些裝置。 

裝置群組對應會使用下列工作流程︰
1. 建立使用者註冊其裝置時將從中選擇的類別
2. 為想要使用的每個類別建立群組，或使用現有的群組。 根據您使用的 Intune 版本，這些群組將會是 Intune 群組或 Azure Active Directory 安全性群組。
2. 您可以設定規則，將所選擇的類別對應至所建立的裝置群組。
3. 當 iOS 和 Android 裝置的使用者註冊其裝置時，他們必須從您設定的類別清單中選擇一個類別。 若要指派類別給 Windows 裝置，使用者必須使用公司入口網站 (如需更多詳細資料，請參閱本主題的**設定裝置群組之後**)。
4. 您接著可以將原則和應用程式部署至這些群組。

您可以建立任何想要的裝置類別，例如：
* 銷售點裝置
* 示範裝置
* 銷售額
* 帳戶處理
* Manager

## <a name="important-information-about-a-change-in-group-management-for-intune"></a>Intune 群組管理變更的重要資訊

我們正根據您的意見反應來整合跨 Enterprise Mobility + Security 的群組和目標體驗。 因此，我們很快就會將 Intune 群組轉換成以 Azure Active Directory 為基礎的安全性群組。 這項變更之後，您將無法再使用 Intune 建立群組。 相反地，您將在 Azure 入口網站中建立。 這項變更將會以漸進方式進行，您可以在[此主題](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)中閱讀這項變更的完整詳細資訊及其時程表。

### <a name="which-procedure-in-this-topic-should-you-use-to-configure-device-group-mapping"></a>您應該使用此主題中的哪項程序來設定裝置群組對應？

由於會分階段實作以 Azure Active Directory 為基礎的安全性群組，因此您必須開啟 [Intune 管理主控台](https://manage.microsoft.com)中的 [群組] 工作區來識別要使用的程序：

-  如果您看到 Azure 入口網站連結，則無法再使用 Intune 群組。 請遵循下方[如何設定 Azure Active Directory 群組的裝置群組對應](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune#how-to-configure-device-group-mapping-for-azure-active-directory-groups)程序。
-  如果您看不到 Azure 入口網站連結，則仍在使用 Intune 群組。 請遵循下方[如何設定 Intune 群組的裝置群組對應](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune#how-to-configure-device-group-mapping-for-intune-groups)程序。

## <a name="how-to-configure-device-group-mapping-for-intune-groups"></a>如何設定 Intune 群組的裝置群組對應
1. 對於想要使用的每個裝置類別，建立一個 Intune 裝置群組，或識別現有的群組。 如需如何建立群組的資訊，請參閱[在 Microsoft Intune 中使用群組來管理使用者和裝置](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)。
2. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 **[系統管理]**。
3. 在 [系統管理] 工作區中，展開 [行動裝置管理]，然後選擇 [裝置群組對應]。
4. 在 [裝置群組對應] 頁面上，啟用裝置群組對應。
5. 選擇 [新增] 建立新的對應規則。
6. 在 [新增裝置群組對應規則] 對話方塊中，輸入您想要建立的類別名稱，然後從下拉式清單中，選擇要將此類別對應到的裝置集合。 完成時，選擇 [新增]。
7. 完成新增類別和群組時，選擇 [儲存]。



## <a name="how-to-configure-device-group-mapping-for-azure-active-directory-groups"></a>如何設定 Azure Active Directory 群組的裝置群組對應

### <a name="step-1---create-device-categories-in-the-intune-administration-console"></a>步驟 1 - 在 Intune 管理主控台中建立裝置類別
1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 **[系統管理]**。
2. 在 [管理] 工作區中，展開 [行動裝置管理]，然後選擇 [裝置類別]。
3. 在 [裝置類別] 頁面上，您會看到可設定裝置類別的清單： 
4. 您可以輸入名稱，然後按一下 [新增] 以新增為新的裝置類別。
5. 此外，您可以選取一個類別，然後將它**刪除**。

當您在步驟 2 中建立 Azure Active Directory 安全性群組時，您將會使用裝置類別名稱。

### <a name="step-2---create-azure-active-directory-security-groups"></a>步驟 2 - 建立 Azure Active Directory 安全性群組

在此步驟中，您將根據裝置類別和裝置類別名稱，在 Azure 入口網站中建立動態群組。

若要繼續，請參閱 Azure Active Directory 文件中的[使用屬性來建立進階規則](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects)主題。
您可以使用此主題中的資訊，透過 **deviceCategory** 屬性來建立具有進階規則的裝置群組。
例如 (**device.deviceCategory -eq** "<*您從 Intune 管理主控台取得的裝置類別名稱*>")


## <a name="after-you-configure-device-groups"></a>設定裝置群組之後

當 iOS 和 Android 裝置的使用者註冊其裝置時，他們必須從您設定的類別清單中選擇一個類別。 選擇類別並完成註冊之後，他們的裝置會新增至與其所選類別相對應的 Intune 裝置群組或 Active Directory 安全性群組。

若要指派類別給 Windows 裝置，使用者必須在註冊裝置之後使用公司入口網站 (portal.manage.microsoft.com)。 在 Windows 裝置上，存取該網站並移至 [功能表] > [我的裝置]。 選擇頁面中列出的已註冊裝置，然後選取類別。 

選擇類別之後，裝置就會自動新增至您建立的對應群組。 如果設定類別之前，裝置已經註冊，使用者將會在公司入口網站上看到和裝置有關的通知，並且將會在使用者下次於 iOS 或 Android 裝置上存取公司入口網站 App 時，要求他們選取類別。



### <a name="see-also"></a>另請參閱
[利用 Microsoft Intune，使用群組管理使用者和裝置](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)
