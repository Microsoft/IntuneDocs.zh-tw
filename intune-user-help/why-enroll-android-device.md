---
title: 為什麼註冊您的 Android 裝置
description: 瞭解為何在 Intune 中註冊裝置非常重要
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d22f5aea-7be4-419b-b51b-a522ca037b69
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08b20ba59c0dabc680e0f5760ee4de892506b7e3
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72501593"
---
# <a name="why-enroll-your-android-device"></a>為什麼註冊您的 Android 裝置  

學校和雇主想要確保您使用安全且受信任的裝置來存取內部資源。 當您存取這些資源時，公司入口網站和 Microsoft Intune 應用程式會讓您的 Android 裝置和資料保持安全。 無論您的所在位置或使用的裝置為何，都能確保您可以安全地存取資源。 

如果您的組織要求您安裝並註冊其中一個應用程式，您必須先執行此動作，才能從您的裝置存取公司資源。 本文說明向這些應用程式註冊您的裝置的目的和優點。  

## <a name="gets-your-device-managed"></a>取得您的裝置管理  
 公司入口網站和 Microsoft Intune 應用程式會在 Intune 中註冊您的裝置。  Intune 是一種行動裝置管理提供者，可協助您的組織透過安全性和裝置原則來管理行動裝置和應用程式。 

應用程式會逐步引導您完成註冊的每個步驟，並設定您的裝置設定以符合您組織的原則。 它們也會警告您需要解決的問題或設定，才能取得公司存取權。  

您的組織可能要求的原則範例包括：  
* 設定密碼或 PIN
* 在設定的登入嘗試次數之後限制存取
* 確定您未使用已進行 JB 或 Root 破解的裝置
* 安裝工作所需的應用程式  

## <a name="gives-you-access-to-work-and-school-apps-work-files-and-email"></a>可讓您存取工作和學校應用程式、工作檔案和電子郵件  
在註冊期間，公司入口網站和 Microsoft Intune 應用程式會要求您連線至公司或學校帳戶。  在您驗證並設定裝置設定以符合貴組織的原則之後，您就可以存取您組織的電子郵件帳戶、網路、檔案和應用程式。  

組織有時會要求您安裝工作或安全性應用程式，例如 Microsoft Office 或 Mobile Threat Defense。 如果需要這些應用程式或可供您使用，您可以在公司入口網站或 Microsoft Intune 應用程式中找到它們。

## <a name="lets-you-remotely-reset-a-lost-or-stolen-device-if-device-supports-it"></a>讓您從遠端重設遺失或遭竊的裝置 (如果裝置支援)
如果裝置遺失或遭竊，您可以在任何其他裝置上登入公司入口網站應用程式或公司入口網站，並將您的手機重設為原廠預設值。 如果您遺失的裝置包含您不想要其他人存取的專屬工作資料，這項功能會很有幫助。 由於裝置已註冊管理，因此您公司的支援人員或 IT 管理員也可以協助重設。  

[重設] 功能無法在 Microsoft Intune 應用程式中使用。  

## <a name="notifies-you-of-policy-updates-and-requirements"></a>通知您原則更新與需求
公司入口網站或 Microsoft Intune 應用程式會每隔八小時自動簽入或同步處理 Intune。 如果您使用公司入口網站，而且想要更頻繁地簽入，您或您的公司支援人員可以起始手動同步處理。在簽入期間，應用程式將會：  

* 下載您公司支援人員提供的任何原則或應用程式更新。  
* 傳送硬體清查更新。 這些更新不含任何個人資訊。  
* 傳送公司應用程式清查更新。 這些更新不含任何個人資訊。  

當您的裝置已不同步或不再符合需求時，其狀態會顯示為 [*不符合規範*]。 您對工作和學校相關資源的存取權可能會被撤銷，直到您的裝置再次符合需求為止。 公司入口網站應用程式會通知您這些問題，以及您需要採取哪些步驟來修正它們。  


## <a name="permits-company-support-access-to-your-device"></a>允許公司支援人員存取您的裝置
當您註冊裝置時，即允許您公司的支援人員或 IT 管理員在有限且有意義的理由下存取裝置。 他們可以：  

* 將裝置重設為製造商的預設值。 如前所述，您也有權重設裝置。 不過，如果您無法立即存取公司入口網站應用程式，您的公司可以為您重設裝置。  

* 移除所有公司相關資料。 如果您離職或您的裝置變成不受管理，您的組織可能會從您的裝置移除公司相關資料。 您的個人資料和設定不會被移除，而會保留在裝置上。  

* 對裝置設定需求，例如要求您擁有裝置密碼或 PIN。 在此情況下，您會收到應用程式通知，指出您的裝置不符合規範。 您公司的支援人員也可能會限制您能在裝置上輸入錯誤密碼的次數。 過多的失敗密碼嘗試可能會導致您的裝置被鎖定。  

* 要求您接受條款和條件。  

* 停用相機功能。 此原則的目的是防止您拍攝專屬資訊，以及移除學校環境中分散注意力的事物。 學校可能會停用教室裝置上的相機功能，讓學生無法分享測驗教材。  

* 要求加密的裝置上的所有資料。 如果遺失或遭竊，此原則可協助保護您裝置上的資料。 它也會保護裝置或應用程式之間共用的資料。 

## <a name="next-steps"></a>後續步驟  

需要協助嗎？ 請連絡公司支援人員 (可查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)以取得連絡資訊)，或是撰寫電子郵件給 <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble installing the Company Portal app on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 小組</a>。
