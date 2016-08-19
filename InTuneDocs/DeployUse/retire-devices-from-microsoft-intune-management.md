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
ms.sourcegitcommit: 7bea7ba4ef59c6b1400414b59456e19dc1c152fb
ms.openlocfilehash: ad5e9453f8132d383f8c23886e48505769c7f44b


---

# 從 Intune 管理中淘汰裝置

無論是公司所擁有或個人的裝置，總有需要從 Intune 管理中移除受管理裝置的一刻。 裝置的淘汰相當簡單。 您可以替作為行動裝置而管理的裝置上執行選擇性抹除或完整抹除。 您也可以淘汰使用 Intune 用戶端軟體管理的電腦。

## 從裝置抹除資料和應用程式
選擇性抹除和完整抹除都是經由移除其原則和公司入口網站，而從 Intune 管理中移除裝置，這表示裝置不再有登入公司資源所需的認證，例如 Microsoft SharePoint、電子郵件或 Office 365。

如果員工已將自己的裝置註冊在 Intune 中，則[選擇性抹除](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe)是較適合的動作，因為這不會影響裝置上的個人資訊。 只會移除公司資料。

對於需要重新規劃用途的裝置，您也可以使用[完整抹除](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe)，將裝置重設為原廠預設值。

## 若要在 Azure Active Directory 入口網站中刪除裝置：

1.  使用您組織的認證登入 [http://aka.ms/accessaad](http://aka.ms/accessaad) 或 [https://portal.office.com](https://portal.office.com)，然後選擇 **[Admin centers] (系統管理員中心)** &gt; **[Azure AD]**。

2.  如果您沒有 Azure 訂用帳戶，請建立帳戶。 如果您有付費帳戶，應該不需要信用卡或付款 (請選擇 [Register your free Azure Active Directory] (註冊免費的 Azure Active Directory) 訂閱連結)。

4.  選取 [Active Directory]  ，然後選取您的組織。

5.  選取 [使用者]  索引標籤。

6.  選取您要刪除裝置的使用者。

7.  選擇 [裝置]。

8.  選取適當的裝置，然後選擇 **[刪除裝置]**。 裝置將會在下一次與 Active Directory 同步處理時刪除。 這通常發生在 4 個小時內。 同步處理之後，裝置會從管理中移除。 這會移除僅供此使用者使用的一部裝置。

## 淘汰受管理的電腦
可以從 Intune 管理主控台移除使用 Intune 用戶端軟體管理的電腦。 這也會解除安裝用戶端軟體，並從電腦刪除 Intune 原則。 請參閱[淘汰使用 Intune 用戶端軟體管理的電腦](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#retire-a-computer.md)的資訊。

## 封鎖裝置的存取
在裝置遺失或因為員工離職但未繳回公司擁有的硬體，使您必須淘汰裝置的情況下，也可以[重設密碼並從遠端鎖定](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)裝置。 這可防止公司資訊遭到誤用，不過您可能需要將裝置當作遺失來註銷。

您也需要從員工的 Intune 使用者帳戶撤銷授權。 這會釋出授權，以便您將其指派給新的使用者帳戶。

## 報廢硬體
有時候是裝置本身的使用壽命到期。 在這種情況下，[重設為原廠設定](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)加上完整抹除，就會移除所有資料並從 Intune 中移除裝置。 然後您可以根據公司政策來移除硬體。

### 請參閱
[使用完整抹除或選擇性抹除來協助保護資料](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)



<!--HONumber=Aug16_HO2-->


