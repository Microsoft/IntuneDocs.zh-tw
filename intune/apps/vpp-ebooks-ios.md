---
title: 管理大量採購的 iOS/iPadOS 電子書
titleSuffix: Microsoft Intune
description: 針對從 iOS Store 大量採購的電子書，了解如何將電子書同步到 Intune，然後管理並追蹤其使用情況。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5617074-2384-4812-b913-dc94f64c0818
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ff2ed62695bad781b7b55ac590e9b97490ba2416
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216070"
---
# <a name="how-to-manage-iosipados-ebooks-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS/iPadOS 電子書


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

針對您想要散發給公司中多位使用者的書籍，Apple 大量採購方案 (VPP) 可讓您購買書籍的多份授權。 您可以從商務或教育市集散發書籍。

Microsoft Intune 可協助您同步、管理及指派透過此方案購買的書籍。 您可從市集匯入授權資訊，並追蹤您已使用的授權數。

管理書籍的程序與[管理 VPP 應用程式](../vpp-apps-ios.md)的程序類似。

## <a name="manage-volume-purchased-books-for-ios-devices"></a>管理大量採購的 iOS 裝置書籍
您可以透過[商務用 Apple 大量採購方案](https://www.apple.com/business/vpp/)或[教育用 Apple 大量採購方案](https://volume.itunes.apple.com/us/store)，購買多個 iOS/iPadOS 書籍授權。 這項程序包括從 Apple 網站設定 Apple VPP 帳戶，並將 Apple VPP 權杖上傳到 Intune。  您可以將大量採購資訊與 Intune 同步處理，並追蹤大量採購的書籍使用情況。

## <a name="before-you-start"></a>在您開始使用 Intune 之前
在開始之前，請從 Apple 取得 VPP 權杖，並將它上傳至您的 Intune 帳戶。 此外：

* 之前如有其他產品已使用過 VPP 權杖，您必須產生新的權杖來搭配 Intune 使用。
* 每個權杖有效期限為一年。
* Intune 預設與 Apple VPP 服務一天進行兩次同步處理。 您可以在任何時間啟動手動同步處理。
* 在您將 VPP 權杖匯入到 Intune 之後，請不要將相同的權杖匯入到任何其他裝置管理解決方案。 這樣做會導致授權指派與使用者記錄遺失。
* 開始搭配 Intune 使用 iOS/iPadOS 書籍之前，請移除搭配其他行動裝置管理 (MDM) 廠商所建立的任何現有 VPP 使用者帳戶。 基於安全性考量，Intune 不會把這些使用者帳戶同步處理到 Intune。 Intune 只會同步處理 Intune 所建立的 Apple VPP 服務資料。
* 當您將書籍指派給裝置時，該裝置必須已安裝內建的 iBooks 應用程式。 如果未安裝，則使用者必須重新安裝該應用程式才能閱讀書籍。 您目前無法使用 Intune 來還原已移除的內建應用程式。
* 您只能從 Apple 大量採購方案網站指派書籍。 您無法先上傳，然後再指派在內部建立的書籍。
* 您目前無法以指派應用程式的相同方式將書籍指派給使用者類別。
* 指派書籍之後，您便無法回收授權。
* 當擁有合格裝置的使用者第一次嘗試安裝 VPP 書籍時，必須先加入 Apple 大量採購方案才能安裝書籍。 您也可以將授權指派給擁有受管理 Apple 識別碼的安全性群組。 如果您這樣做，安裝書籍時將不會提示使用者輸入其 Apple 識別碼。
* 裝置必須向使用者親和性註冊，因為電子書只能指派給使用者群組。   


## <a name="to-get-and-upload-an-apple-vpp-token"></a>取得並上傳 Apple VPP 權杖

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [租用戶系統管理]   > [連接器與權杖]   > [Apple VPP 權杖]  。
3. 在 VPP 權杖清單窗格中，按一下 [建立]  。
5. 在 [新的 VPP 權杖]  窗格中，指定下列資訊：
    - **VPP 權杖檔案** - 確認您已註冊商務大量採購方案或教育大量採購方案。 然後，請下載您帳戶的 Apple VPP 權杖，然後在這裡選取它。
    - **Apple ID** - 輸入與大量採購方案相關聯之帳戶的 Apple ID。
    - **VPP 帳戶類型** - 請選擇 [商務]  或 [教育]  。
5. 完成時按一下 [建立]  。

該權杖會顯示在權杖清單窗格內。


您可以隨時選擇 [立即同步處理]  ，使用 Intune 同步處理 Apple 所儲存的資料。

## <a name="to-assign-a-volume-purchased-app"></a>指派大量採購應用程式

1. 選取 [應用程式]   > [電子書]   > [所有電子書]  。
2. 在書籍清單窗格中，選擇您要指派的書籍，然後選擇 [...]  > [指派群組]  。
3. 在 <書籍名稱  > - [指派的群組]  窗格中，選擇 [管理]   > [指派的群組]  。
4. 選擇 [指派群組]  ，然後在 [選取群組]  窗格中，選擇要指派該書籍的 Azure AD 使用者群組。 裝置群組目前尚未支援。
選擇指派動作：**可用**或**必要**。 
5. 完成之後，請選擇 [儲存]  。

## <a name="next-steps"></a>後續步驟

請參閱[如何監視應用程式](apps-monitor.md)，以取得協助您監視書籍指派的資訊。






