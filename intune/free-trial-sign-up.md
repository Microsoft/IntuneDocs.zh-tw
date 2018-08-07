---
title: 註冊 Microsoft Intune 的 30 天免費試用
titleSuffix: Microsoft Intune
description: 了解如何註冊 Microsoft Intune 的 30 天免費試用。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/04/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.suite: ems
ms.custom: ''
ms.openlocfilehash: b68c2d93071d545bf25f7810a6908099988fb902
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31024663"
---
# <a name="sign-up-for-a-microsoft-intune-free-trial"></a>註冊 Microsoft Intune 免費試用


這篇文章會逐步引導您完成註冊 Azure 入口網站適用的獨立式 Intune 試用版。

1. 請造訪 [Intune 註冊](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) 頁面並填寫表格以註冊試用版訂閱。
2. 如果您已經有工作或學校帳戶，而且想要將它用於您的 Intune 試用版，請改為依照[這些登入指示](/intune/account-sign-up)執行作業。

* 若您大部分的 IT 作業與使用者分屬於不同的地區設定，建議您從 [Where's your company located?]\(您的公司位置？) 選取該語言設定。

2. 在註冊程序結束時，會顯示訊息提供您新帳戶的資訊。 <br/> 

![帳戶資訊的影像](./media/2-end-of-sign-up-process.png) <br/>

此時，若您按一下 [您可以開始使用]，您就能進入 Office 365 系統管理中心將使用者新增到您的測試環境。 <br/><br/>不過，如果您要直接前往 Intune Azure 入口網站，請開啟新的瀏覽器視窗，然後在網址列中輸入 **https://portal.azure.com** 。 您將會被導向至 Azure 登入頁面，讓您使用提供給您的認證登入。 請在每次登入您的 Intune 試用版時使用此位址。 <br/> ![Azure 入口網站登入頁面的影像](./media/azure-portal-signin.png)

第一次登入 Intune [Azure 入口網站](https://portal.azure.com)時，Intune 可能不會出現在 Azure 儀表板上。 將 Intune 服務新增至 Azure 儀表板︰
1. 請從儀表板左側的 Azure 服務清單中選擇 [All services] (所有服務)，然後在搜尋方塊中輸入 **Intune**。
2. 從清單中選擇 [Intune]，然後選取星號將服務加入服務清單中。<br/> ![在 Azure 入口網站內選取 Microsoft Intune 的影像](./media/azure-add-intune1.png)
3. 在服務清單中選擇 [Intune]，以開啟 Intune 儀表板。

當您註冊試用版時，您在註冊期間提供的電子郵件地址也會收到一封內含您帳戶資訊的電子郵件訊息。 本電子郵件可確認您的試用版是使用中的狀態。

## <a name="keeping-the-admin-experiences-straight"></a>讓管理體驗有條理

您可能使用的有兩個入口網站：
- Azure 中的 Intune 儀表板 ([portal.azure.com](https://portal.azure.com))，您可以瀏覽 [Intune 功能](what-is-intune.md)。 一般是在 Intune 儀表板中執行工作。
- Office 365 系統管理中心 ([portal.office.com](https://portal.office.com))，若您未使用 Azure Active Directory 新增及管理使用者，可於此處執行這些作業。 您也可以管理您帳戶的其他事宜，包括計費及支援。

## <a name="next-steps"></a>接下來的步驟

### <a name="integration-with-other-products"></a>與其他產品整合
深入了解搭配 Intune 使用您的 Azure Active Directory 使用者帳戶：
- [身分識別需求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [目錄同步作業需求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [Multi-Factor Authentication 需求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

深入了解使用 [Intune 搭配 System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management)
