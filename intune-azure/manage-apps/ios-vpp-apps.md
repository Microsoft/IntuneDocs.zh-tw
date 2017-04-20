---
title: "管理 iOS 大量購買的應用程式"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解可如何將從 iOS 市集大量採購的應用程式，同步到 Intune，然後管理及並追蹤其使用方式。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 771aed4e1c57171183b9a9ea7d9e0f702dc1859c
ms.openlocfilehash: 3b0a674fadf30c660ff3e8e8db172a590f07c8be
ms.lasthandoff: 04/06/2017

---

# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

iOS App Store 可讓您購買多個想要在公司內執行的應用程式授權。 這可協助您降低追蹤多個所購買應用程式複本的管理開銷。

Microsoft Intune 藉由從應用程式市集匯入授權資訊、追蹤您已經使用了多少個授權，並避免您安裝超過擁有數目的應用程式複本，來協助您管理透過此程式購買的應用程式。

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>管理大量採購的 iOS 裝置應用程式
您可透過[商務 Apple 大量採購方案](http://www.apple.com/business/vpp/)或[教育 Apple](http://volume.itunes.apple.com/us/store)，購買多份 iOS 應用程式授權。 這項作業包括從 Apple 網站設定 Apple VPP 帳戶，並將 Apple VPP 權杖上傳到 Intune。  您可以將您的大量採購資訊與 Intune 同步處理，並追蹤大量採購的應用程式使用情況。

## <a name="before-you-start"></a>開始之前
在開始之前，您必須從 Apple 取得 VPP Token，並將它上傳至您的 Intune 帳戶。 此外，您還應該了解下列資訊︰

* 您可將多份大量採購方案的權杖，與 Intune 帳戶相關聯。
* 之前如有其他產品已使用過 VPP Token，您必須產生新的 Token 來搭配 Intune 使用。
* 每個權杖有效期限為一年。
* Intune 預設與 Apple VPP 服務一天進行兩次同步處理。 您可以在任何時間啟動手動同步處理。
* 在您將 VPP Token 匯入 Intune 之後，請不要將相同的權杖匯入任何其他裝置管理解決方案。 以免導致授權指派及使用者記錄遺失。
* 開始搭配 Intune 使用 iOS VPP 之前，請移除任何以其他行動裝置管理 (MDM) 廠商所建立的現有 VPP 使用者帳戶。 基於安全性考量，Intune 不會把這些使用者帳戶同步處理到 Intune。 Intune 只會同步處理 Intune 所建立的 Apple VPP 服務資料。
* 您無法將 iOS VPP 應用程式指派至使用裝置註冊通訊協定 (DEP) 所註冊的裝置。

## <a name="to-get-and-upload-an-apple-vpp-token"></a>取得並上傳 Apple VPP 權杖

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 **Intune** 刀鋒視窗上選擇 [管理應用程式]。
1.  在 [管理應用程式] 工作負載中，選擇 [安裝]  > [iOS VPP 權杖]。
2.  在 [VPP 權杖清單] 刀鋒視窗中，按一下 [新增]。
3.  在 [新的 VPP 權杖] 刀鋒視窗中，指定下列資訊：
    - **VPP 權杖檔案** - 若您尚未註冊，請註冊商務大量採購方案或教育大量採購方案。 註冊之後，請下載您帳戶的 Apple VPP 權杖，然後請於此處加以選取。
    - **Apple ID** - 輸入與大量採購方案相關聯之帳戶的 Apple ID。
    - **VPP 帳戶類型** - 請選擇 [商務] 或 [教育]。
4. 完成之後，請按一下 [上傳]。

在權杖清單刀鋒視窗內，會顯示該權杖。


您可以隨時選擇 [立即同步處理]，使用 Intune 同步處理 Apple 所儲存的資料。

## <a name="to-assign-a-volume-purchased-app"></a>指派大量採購應用程式

1. 在 [管理應用程式] 工作負載中，選擇 [管理]  > [授權的應用程式]。
2. 在應用程式清單刀鋒視窗中，選擇您要指派的應用程式，然後選擇 '**...**' > [指派群組]。
3. 在 <*應用程式名稱*> - [指派的群組] 刀鋒視窗中，選擇 [管理]  > [指派的群組]。
4. 選擇 [指派群組]，然後在 [選取群組] 刀鋒視窗中，選擇要指派該應用程式的 Azure AD 使用者或裝置群組。
您必須選擇指派動作**必要**。 目前不支援可用的安裝。 此外，在 2017 年 1 月之後建立的新租用戶將可以指派給裝置群組。 如果您的租用戶在這之前建立，而無法選擇將 VPP 應用程式指派給裝置群組，請連絡 Intune 支援。
5. 完成之後，請選擇 [儲存]。

請參閱[如何監視應用程式](monitor-apps.md)，以取得協助您監視應用程式指派的資訊。

## <a name="further-information"></a>進一步資訊

當您將應用程式指派為**必要**安裝時，安裝該應用程式的每位使用者，都會使用授權。

若要回收授權，您必須將指派動作變更為**解除安裝**。 在應用程式解除安裝之後，將會回收授權。

當具有合格裝置的使用者第一次嘗試安裝 VPP 應用程式時，系統會要求他們加入 Apple 大量採購方案。 他們必須這麼做，應用程式安裝才會繼續執行。

