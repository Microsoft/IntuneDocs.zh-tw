---
# required metadata

title: Microsoft Intune 的網域名稱 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c3c136f0-330d-432a-a91f-16f7dd097e55

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---



# Microsoft Intune 的網域名稱

設定 Microsoft Intune 之前，請檢閱本主題及[啟動 Microsoft Intune 前的須知事項](what-to-know-before-you-start-microsoft-intune.md)列示的其他需求

當貴組織註冊 Intune 等的 Microsoft 雲端式服務時，您會取得如下所示的初始網域名稱：contoso.onmicrosoft.com。 在這個範例中，contoso 是您註冊時選擇的名稱，而 onmicrosoft.com 則是指派給新增至訂閱之帳戶的尾碼。 完成註冊程序之後，您便無法變更該網域名稱。 不過，身為全域管理員，您可以新增自己的自訂網域名稱供貴組織用於服務，或者您可以移除先前新增的網域。

根據預設，當您使用 onmicrosoft 網域時，您匯入的每個使用者的使用者主要名稱 (UPN) 都會收到 onmicrosoft.com 尾碼。

若要使用個人擁有的網域名稱，而非註冊時提供的名稱，可以將該個人網域名稱新增至 Azure Active Directory。 在您新增網域且系統已驗證您擁有該網域之後，您可以透過在 DNS 託管服務提供者變更 DNS 　資源記錄，以建立包含該網域名稱的帳戶和群組。 當您計劃使用自訂網域時，為了簡化使用者帳戶的管理，在開始從本機 Active Directory 同步處理使用者之前，請先設定自訂網域名稱到您的訂閱。

設定 Intune 的網域名稱和 DNS 資源記錄會與其他 Azure Active Directory 租用戶相同。 如需相關指示，請參閱[使用 Azure Active Directory 新增自訂網域名稱來簡化登入](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)。

### 請參閱
[啟動 Microsoft Intune 前的須知事項](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=May16_HO2-->


