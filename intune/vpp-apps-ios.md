---
title: "管理 iOS 大量採購的應用程式"
titleSuffix: Intune on Azure
description: "針對從 iOS Store 大量採購的應用程式，了解如何將應用程式同步到 Intune，然後管理及並追蹤其使用情況。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1433951e8c17ae226d37705223a80e2e79f7483b
ms.sourcegitcommit: 6a089eb45ea3fb18ae0b2dac96683466f52f95bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2017
---
# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

iOS App Store 可讓您購買多個想要在公司內執行的應用程式授權。 購買多個應用程式複本可協助您降低追蹤多個所購買應用程式複本的管理開銷。

Microsoft Intune 可藉由下列方式協助您管理透過此方案所購買的應用程式：

- 從應用程式市集報告授權資訊
- 追蹤您已經使用多少個授權
- 協助您不要安裝超過擁有數目的應用程式複本

您可以使用兩種方法來指派大量採購的應用程式：

### <a name="device-licensing"></a>裝置授權

當您將一個應用程式指派給多部裝置時，會使用一個應用程式授權，並與您指派的目標裝置保持關聯。
當您將大量採購的應用程式指派給一部裝置時，裝置的終端使用者不需要提供 Apple ID 來存取市集。 



### <a name="user-licensing"></a>使用者授權

當您將一個應用程式指派給多位使用者時，會使用一個應用程式授權，並與使用者相關聯。 該應用程式可以在使用者擁有的多部裝置上執行 (受 Apple 有限控制)。
當您將大量採購的應用程式指派給多位使用者時，每位終端使用者都必須具備有效和唯一的 Apple ID，才能存取 App Store。


此外，針對從 Apple 大量採購方案市集購買的書籍，您可以使用 Intune 來進行同步處理、管理及指派。 如需詳細資訊，請參閱[如何管理透過大量採購方案購買的 iOS 電子書](vpp-ebooks-ios.md)。


## <a name="manage-volume-purchased-apps-for-ios-devices"></a>管理大量採購的 iOS 裝置應用程式
請透過[商務 Apple 大量採購方案](http://www.apple.com/business/vpp/)或[教育 Apple 大量採購方案](http://volume.itunes.apple.com/us/store)，購買多份 iOS 應用程式授權。 這項程序包括從 Apple 網站設定 Apple VPP 帳戶，並將 Apple VPP 權杖上傳到 Intune。  您可以將您的大量採購資訊與 Intune 同步處理，並追蹤大量採購的應用程式使用情況。

## <a name="before-you-start"></a>開始之前
在開始之前，您必須從 Apple 取得 VPP 權杖，並將它上傳至您的 Intune 帳戶。 此外，您還應該了解下列準則︰

* 您可將多份大量採購方案的權杖，與 Intune 帳戶相關聯。
* 之前如有其他產品已使用過 VPP 權杖，您必須產生新的權杖來搭配 Intune 使用。
* 每個權杖有效期限為一年。
* Intune 預設與 Apple VPP 服務一天進行兩次同步處理。 您可以在任何時間啟動手動同步處理。
* 開始搭配 Intune 使用 iOS VPP 之前，請移除任何以其他行動裝置管理 (MDM) 廠商所建立的現有 VPP 使用者帳戶。 基於安全性考量，Intune 不會把這些使用者帳戶同步處理到 Intune。 Intune 只會同步處理 Intune 所建立的 Apple VPP 服務資料。
* Intune 支援新增最多 256 個 VPP 權杖。
* 如果您為透過裝置註冊設定檔或 Apple Configurator 註冊的裝置，指派大量採購的應用程式，只有以裝置為目標的應用程式會運作。 您無法將大量採購的應用程式目標設為 DEP 裝置的使用者，DEP 裝置沒有任何使用者親和性。
原因是 ioS VPP 使用者授權可以使用相同的使用者帳戶註冊數千部裝置。 iOS VPP 使用者授權允許終端使用者在 5-10 部裝置上安裝應用程式。
這表示前幾個 DEM 已註冊裝置會利用使用者授權安裝 VPP 應用程式，其他裝置則無法取得應用程式。
* VPP 權杖只支援一次用於一個 Intune 帳戶。 請勿將相同的 VPP 權杖重複用於多個 Intune 租用戶。
* 當您使用使用者授權模型指派 VPP 應用程式給使用者或裝置 (具有使用者親和性) 時，每個 Intune 使用者在裝置上接受 Apple 條款和條件時，都必須與唯一的 Apple ID 或電子郵件地址建立關聯。
請確定當您為新 Intune 使用者設定裝置時，您用該使用者的唯一 Apple ID 或電子郵件地址來進行設定。 Apple ID 或電子郵件地址和 Intune 使用者形成唯一的組合，並可以用於多達 5 部裝置。

>[!IMPORTANT]
>在您將 VPP 權杖匯入到 Intune 之後，請不要將相同的權杖匯入到任何其他裝置管理解決方案。 這樣做會導致授權指派與使用者記錄遺失。

## <a name="to-get-and-upload-an-apple-vpp-token"></a>取得並上傳 Apple VPP 權杖

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗上，選擇 [行動應用程式]。
1.  在 [行動應用程式] 工作負載中，選擇 [安裝] > [iOS VPP 權杖]。
2.  在 [VPP 權杖清單] 刀鋒視窗中，按一下 [新增]。
3.  在 [新的 VPP 權杖] 刀鋒視窗中，指定下列資訊：
    - **VPP 權杖檔案** - 若您尚未註冊，請註冊商務大量採購方案或教育方案。 註冊之後，請下載您帳戶的 Apple VPP 權杖，然後在這裡選取它。
    - **Apple ID** - 輸入與大量採購方案相關聯之帳戶的 Apple ID。
    - **VPP 帳戶類型** - 請選擇 [商務] 或 [教育]。
4. 完成之後，請按一下 [上傳]。

該權杖會顯示在權杖清單刀鋒視窗內。


您可以隨時選擇 [立即同步處理]，使用 Intune 同步處理 Apple 所儲存的資料。

> [!NOTE]
> Microsoft Intune 只會同步可透過 iTunes Store 公開取得之應用程式的資訊。 尚不支援 **iOS 的自訂 B2B 應用程式**。 如果您的案例以這類應用程式為目標，將不會同步應用程式資訊。

## <a name="to-assign-a-volume-purchased-app"></a>指派大量採購應用程式

1.  在 [Mobile Apps] 工作負載中，選擇 [管理] > [應用程式授權]。
2.  在應用程式清單刀鋒視窗中，選擇您要指派的應用程式，然後選擇 [...] > [指派群組]。
3.  在 <app name> - [指派] 刀鋒視窗中，選擇 [管理] > [指派]。
4.  選擇 [選取群組]，然後在 [選取群組] 刀鋒視窗中，選擇要指派該應用程式的 Azure AD 使用者或裝置群組。
5.  針對您選取的每個群組，選擇下列設定：
    - **類型** - 選擇應用程式會是 [可用] (終端使用者可以從公司入口網站安裝應用程式) 或 [必要] (終端使用者的裝置會自動安裝應用程式)。
    - **授權類型** - 選擇 [使用者授權] 或 [裝置授權]。
6.  完成之後，請選擇 [儲存]。


>[!NOTE]
>顯示的應用程式清單與權杖建立關聯。 如果您的應用程式與多個 VPP 權杖建立關聯，您會看到相同的應用程式顯示多次；針對每個權杖各一次。

## <a name="further-information"></a>進一步資訊

若要回收授權，您必須將指派動作變更為「解除安裝」。 在應用程式解除安裝之後，將會回收授權。 如果您移除已指派給使用者的應用程式，則 Intune 會嘗試回收所有已與該使用者建立關聯的應用程式授權。

當具有合格裝置的使用者第一次嘗試將 VPP 應用程式安裝至裝置時，系統會要求他們加入 Apple 大量採購方案。 他們必須加入，應用程式安裝才會繼續執行。 對於加入 Apple 大量採購方案的邀請，需要使用者能夠在 iOS 裝置上使用 iTunes 應用程式。 如果您已經設定停用 iTunes Store 應用程式的原則，則 VPP 應用程式以使用者為基礎的授權將無法運作。 解決方法是移除原則以允許 iTunes 應用程式，或是使用以裝置為基礎的授權。



## <a name="next-steps"></a>後續步驟

請參閱[如何監視應用程式](apps-monitor.md)，以取得協助您監視應用程式指派的資訊。