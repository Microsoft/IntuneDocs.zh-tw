---
title: "淘汰裝置 | Microsoft Intune"
description: "Intune 同時支援選擇性抹除和完整抹除，可藉由移除原則與公司入口網站，從 Intune 管理中移除裝置。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e9cbf5858cc4e860b540f421b6d463b8e7a429cf
ms.openlocfilehash: 42b723f99c34f03060140e5f280b87287d108ae1


---

# 從 Intune 管理中淘汰裝置

無論是公司所擁有或個人的裝置，總有那麼一刻需要從 Intune 管理中淘汰受管理的裝置。 裝置淘汰相當直截了當，您可以執行選擇性抹除或完整抹除。
## 從裝置抹除資料和應用程式
選擇性抹除和完整抹除都是經由移除其原則和公司入口網站，而從 Intune 管理中移除裝置，這表示裝置不再有登入公司資源所需的認證，例如 Microsoft SharePoint、電子郵件或 Office 365。

如果員工已將自己的裝置註冊在 Intune 中，則[選擇性抹除](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe)是較適合的動作，因為這不會影響裝置上的個人資訊。 只會移除公司資料。

對於公司擁有的裝置，您也可以使用[完整抹除](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe)，將裝置重設為原廠設定。

## 撤銷公司網路的存取權
如果您淘汰裝置是因為員工離職，但他們忘了交回公司擁有的硬體，您也可以[遠端鎖定](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)裝置。 這可防止公司資訊和公司硬體遭到誤用，不過您可能需要將裝置當做遺失來註銷。

您也需要從員工的 Intune 使用者帳戶撤銷授權。 這會釋出授權，以便您將其指派給新的使用者帳戶。

## 報廢硬體
有時候是裝置本身的使用壽命到期。 在這種情況下，[重設為原廠設定](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)加上完整抹除，就會移除所有資料並從 Intune 中移除裝置。 然後您可以根據公司政策來移除硬體。

### 請參閱
[使用完整抹除或選擇性抹除來協助保護資料](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


