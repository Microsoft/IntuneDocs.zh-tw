---
title: "淘汰裝置 | Microsoft Intune"
description: "Intune 同時支援選擇性抹除和完整抹除，可藉由移除原則與公司入口網站，從 Intune 管理中移除裝置。"
keywords: 
author: NathBarn
ms.author: nathbarn
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
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: 834f20a0280c2e3c4301e1a0769ed44c82a6bad0


---

# <a name="retire-devices-from-intune-management"></a>從 Intune 管理中淘汰裝置

無論是公司擁有的或個人擁有的裝置，最後都需要從 Intune 管理中移除受管理裝置。 您可能會因各種原因而需要淘汰裝置：

-   使用者有計畫地離開公司 (在「受管理」狀況下離開)
-   使用者突然離開 (遭到解雇、離職等等)。
-   裝置遺失
-   裝置再利用 (移至另一位使用者，重複使用於不同用途等等)

您可以在作為行動裝置管理的裝置上執行選擇性抹除或完整抹除，也可以鎖定裝置並重設其密碼。 藉由抹除裝置，您可以釋出使用者的訂閱以新增其他裝置。 您也可以淘汰使用 Intune 用戶端軟體管理的電腦。

## <a name="wipe-data-and-apps-from-devices"></a>從裝置抹除資料和應用程式
選擇性抹除和完整抹除會移除原則與公司入口網站，以從 Intune 管理中移除裝置。 因此，裝置不再具有登入公司資源 (例如 Microsoft SharePoint、電子郵件或 Office 365) 所需的認證。

如果員工已將自己的裝置註冊在 Intune 中，則[選擇性抹除](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe)是較適合的動作，因為這不會影響裝置上的個人資訊。 只會移除公司資料。

對於需要重新規劃用途的裝置，您也可以使用[完整抹除](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe)，將裝置重設為原廠預設值。

## <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>若要在 Azure Active Directory 入口網站中刪除裝置：

1.  使用您組織的認證登入 [http://aka.ms/accessaad](http://aka.ms/accessaad) 或 [https://portal.office.com](https://portal.office.com)，然後選擇 [Admin centers] (系統管理員中心) &gt; [Azure AD]。

2.  如果您沒有 Azure 訂用帳戶，請建立帳戶。 如果您有付費帳戶，這應該不需要信用卡或付款。 選擇 [Register your free Azure Active Directory] (註冊免費的 Azure Active Directory) 訂閱連結。

4.  選擇 [Active Directory]，然後選擇您的組織。

5.  選擇 [使用者] 索引標籤。

6.  選擇您要刪除裝置的使用者。

7.  選擇 [裝置]。

8.  選擇適當的裝置，然後選擇 [刪除裝置]。 裝置將會在下一次與 Active Directory 同步處理時刪除。 這通常發生在四個小時內。 同步處理之後，裝置會從管理中移除。 這會移除僅供此使用者使用的一部裝置。

## <a name="retire-managed-computers"></a>淘汰受管理的電腦
在 Intune 管理主控台中，可以移除 Intune 用戶端軟體所管理的電腦不進行管理。 這也會解除安裝用戶端軟體，並從電腦刪除 Intune 原則。 請參閱[淘汰使用 Intune 用戶端軟體管理的電腦](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#retire-a-computer.md)的資訊。

## <a name="block-access-a-device"></a>封鎖裝置的存取
如果裝置遺失，或因員工離職但未繳回公司擁有的硬體，使您必須淘汰裝置的情況下，也可以[重設密碼並從遠端鎖定](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)裝置。 這可防止公司資訊遭到誤用，不過您可能需要將裝置當作遺失來註銷。

您也需要從員工的 Intune 使用者帳戶撤銷授權。 這會釋出授權，以便您將其指派給新的使用者帳戶。

## <a name="retire-hardware"></a>報廢硬體
有時候是裝置本身的使用壽命到期。 在這種情況下，[重設為原廠設定](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)加上完整抹除，就會移除所有資料並從 Intune 中移除裝置。 然後您可以根據公司原則來移除硬體。

### <a name="see-also"></a>請參閱
[使用完整抹除或選擇性抹除來協助保護資料](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)



<!--HONumber=Nov16_HO1-->


