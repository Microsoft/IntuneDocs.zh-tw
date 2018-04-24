---
title: 管理大量購買的 iOS 應用程式
description: 藉由匯入應用程式市集的授權資訊、追蹤已使用的授權數量，並避免您安裝超過所擁有數目的應用程式複本，來使用 Intune 管理您從 Apple 大量購買的應用程式。
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 10/11/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1dafc28a-7f8b-4fe0-8619-f977c93d1140
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 698b9513baf6f3d089b96ccd0cb5950e2290b3b5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>管理透過 Microsoft Intune 大量採購方案購買的 iOS 應用程式

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

iOS App Store 可讓您購買多個想要在公司內執行的應用程式授權。 這可協助您降低追蹤多個所購買應用程式複本的管理開銷。

Microsoft Intune 藉由從應用程式市集匯入授權資訊、追蹤您已經使用了多少個授權，並避免您安裝超過擁有數目的應用程式複本，來協助您管理透過此程式購買的應用程式。

> [!Important]
> 目前，Intune 會指派 iOS 企業大量採購方案 (VPP) 應用程式授權給使用者和裝置。 因此，使用者可能必須輸入其 Apple ID 密碼，才能安裝應用程式。

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>管理大量採購的 iOS 裝置應用程式
您可以透過 [Apple Volume Purchase Program for Business](http://www.apple.com/business/vpp/) 購買多個 iOS 應用程式的授權。 這項作業包括從 Apple 網站設定 Apple VPP 帳戶，並將 Apple VPP 權杖上傳到 Intune。  您可以將您的大量採購資訊與 Intune 同步處理，並追蹤大量採購的應用程式使用情況。

## <a name="before-you-start"></a>開始之前
在開始之前，您必須從 Apple 取得 VPP Token，並將它上傳至您的 Intune 帳戶。 此外，您還應該了解下列資訊︰

* Intune 支援新增最多 256 個 VPP 權杖。
* 之前如有其他產品已使用過 VPP 權杖，您必須產生新的權杖來搭配 Intune 使用。
* 每個權杖有效期限為一年。
* Intune 預設與 Apple VPP 服務一天進行兩次同步處理。 您可以在任何時間啟動手動同步處理。
* 在您將 VPP 權杖匯入到 Intune 之後，請不要將相同的權杖匯入到任何其他裝置管理解決方案。 這樣做會導致授權指派與使用者記錄遺失。
* 開始搭配 Intune 使用 iOS VPP 之前，請移除任何以其他行動裝置管理 (MDM) 廠商所建立的現有 VPP 使用者帳戶。 基於安全性考量，Intune 不會把這些使用者帳戶同步處理到 Intune。 Intune 只會同步處理 Intune 所建立的 Apple VPP 服務資料。
* 如果設定裝置的使用者親和性，則您只能將 iOS VPP 應用程式部署至使用裝置註冊通訊協定 (DEP) 所註冊的使用者裝置。

## <a name="to-get-and-upload-an-apple-vpp-token"></a>取得並上傳 Apple VPP 權杖

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [管理員] &gt; [iOS 和 Mac OS X] &gt; [大量採購方案]。

2.  選擇 **Apple VPP 帳戶**連結。 如果還沒有這麼做，請註冊企業大量採購方案。 在註冊之後，請下載您帳戶的 Apple VPP Token。

3.  在 Intune 主控台的 [管理 Apple 大量採購方案 (VPP)] 頁面上，選擇 [上傳 VPP 權杖]。

4.  在 **[上傳 VPP Token]** 對話方塊中，輸入或貼上 VPP Token 名稱及您的 Apple ID，然後選擇 **[上傳]**。

5.  在 [警告] 對話方塊中，選取方塊以表示您已了解之後您不能變更為其他 VPP 帳戶，然後選擇 **[是]**。

您現在可以在 **[大量採購方案]** 頁面上檢視 Apple VPP Token 的資訊，包括上次更新時間、到期時間，以及上次與 Intune 同步處理的時間。

您可以隨時選擇 [立即同步處理]，使用 Intune 同步處理 Apple 所儲存的資料。

## <a name="to-deploy-a-volume-purchased-app"></a>部署大量採購應用程式

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [應用程式] &gt; [應用程式] &gt; [大量採購的應用程式]。 此清單會顯示已從 Apple VPP 服務同步處理的所有應用程式。

2.  選擇您想要部署的應用程式，選擇 **[管理部署]**，然後使用[在 Microsoft Intune 中部署應用程式](deploy-apps-in-microsoft-intune.md)主題中的指示，完成上傳、建立和部署應用程式。

> [!TIP]
> 您必須選擇**必要**部署動作。 目前不支援可用的安裝。 此外，您只可以將應用程式部署至使用者群組。

當您將應用程式部署為**必要**安裝時，安裝應用程式的每位使用者都會使用授權。

若要回收授權，您必須變更部署動作為 [解除安裝]。 在應用程式解除安裝之後，將會回收授權。

當具有合格裝置的使用者第一次嘗試安裝 VPP 應用程式時，系統會要求他們加入 Apple 大量採購方案。 他們必須這麼做，應用程式安裝才會繼續執行。

如果沒有更多的可用授權，部署將會失敗。

## <a name="to-monitor-apple-vpp-apps"></a>監視 Apple VPP 應用程式
您可以從 [大量採購的應用程式] 節點中的 [應用程式] 工作區，監視已部署了哪些 VPP 應用程式，以及已使用了多少授權。

> [!TIP]
> 您也可以使用應用程式的 **[篩選器]** 來檢查每個應用程式的安裝狀態。

### <a name="see-also"></a>另請參閱
[在 Microsoft Intune 中部署應用程式](deploy-apps-in-microsoft-intune.md)
