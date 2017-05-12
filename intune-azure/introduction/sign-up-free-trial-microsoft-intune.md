---
title: "註冊 30 天免費試用版"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰ 如何在 Azure 上註冊 Intune。"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 01/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: eaddfc647c5e755e6b033a7970e003ce516bba04
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017


---

# <a name="sign-up-for-a-microsoft-intune-free-trial-for-the-azure-portal-preview"></a>註冊 Azure 入口網站預覽版的 Microsoft Intune 免費試用版

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

這篇文章會逐步引導您完成註冊 Azure 入口網站適用的 Intune 獨立版預覽版的試用版。 <!---and prepares your trial with some users so that you can then follow the associated evaluation guide to see how Intune manages mobile devices. ---> <!---or app data when devices are not enrolled in Intune.--->

<!--- ## Assumptions
This sign-up article and the evaluation guide assume you are using the trial for evaluation purposes only and intend to start with a clean environment when you subscribe.

To make it easy for you to get started with the trial, we are setting up a very simple environment that uses only Intune and assumes it will be your sole method of managing devices (known as the mobile device management authority). However, throughout the guide we will point you to deeper technical content if you want to explore farther.

You can do everything in the trial version that you can do in a subscription version; the only difference is you are limited to 100 user accounts in the trial.--->

<!--- ## Sign up for your trial--->
1. 請造訪 [Intune 註冊](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) 頁面並填寫表格以註冊試用版訂閱。

 <!--- If you have a work or school account and want to use that for your Intune trial, follow [these sign-in instructions](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-1) instead. However, this article assumes that you are not using such an account.---><br/> ![註冊頁面的影像](./media/1-clicking-try.png)

 > [!TIP]
> 若您大部分的 IT 作業與使用者分屬於不同的地區設定，建議您從 [Where's your company located?]\(您的公司位置？) 選取該語言設定。

2. 在註冊程序結束時，會顯示訊息提供您新帳戶的資訊。 <br/> ![帳戶資訊的影像](./media/2-end-of-sign-up-process.png) <br/>此時，若您按一下 [You're ready to go]\(您已可開始)，您就能進入 Office 365 系統管理中心將使用者新增到您的測試環境。 <br/><br/>但若要直接前往 Intune Azure 入口網站預覽版，請開啟新的瀏覽器視窗，然後在網址列中輸入**https://portal.azure.com**。 您將會被導向至 Azure 登入頁面，讓您使用提供給您的認證登入。 請在每次登入您的 Intune 試用版時使用此位址。 <br/> ![Azure 入口網站登入頁面的影像](./media/azure-portal-signin.png)

第一次登入 Intune Azure 預覽版時，Intune 可能不會出現在 Intune Azure 儀表板上。 將 Intune 服務新增至 Azure 儀表板︰
1. 請從儀表板左側的 Azure 服務清單中選擇 [更多服務 >]，然後在搜尋方塊中輸入 **Intune**。
2. 從清單中選擇 [Intune]，然後選取星號將服務加入服務清單中。<br/> ![從服務清單中選取 Intune 的映像](./media/azure-add-intune1.png)
3. 在服務清單中選擇 [Intune]，以開啟 Intune 儀表板。

當您註冊試用版時，您在註冊期間提供的電子郵件地址也會收到一封內含您帳戶資訊的電子郵件訊息。 本電子郵件可確認您的試用版是使用中的狀態。


<!--- ## Add users
Before you leave the Office 365 Admin center for Intune, you need to add some users to your trial account.

In the Office 365 Admin center, you can add users individually or in bulk by uploading a .csv file. We will do both to set up your trial. However, in your production environment, you will probably want to take advantage of your Azure Active Directory user accounts, which you can learn more about in our [Getting Started guide](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) and in the [Next steps](#Next-steps) section of this article.

### Add an individual user
1. Choose either of the options to add a use to open a form that allows you to create a user. Only the items starred with an asterisk (\*) are required.
![Image of add user button options](./media/sign-up/add-user.png)


2.  When you add the user, the final step will be to send the user an email with their temporary Intune password. For the purposes of this evaluation, use your own work email address so you will receive the log-on information and see the email your users will get. You can then use these user identities to enroll test devices.<br/>

 ![Image of add user final step](./media/sign-up/new-user-2.png)

3. If you want to assign a user an admin role after you create it, you can edit the role in the Office 365 Admin center by selecting the user name from your list of users, and then choosing **Edit** in the Role line to see the list of user roles you can select from and assign to that user.

 ![Image of user  role options](./media/sign-up/change-user-role.png)

### Import multiple users
1. You will find the wizard for importing multiple users in the **More** list.

 ![Image of option to add multiple users](./media/sign-up/add-multiple-users.png)

2. To help you set up your .csv file correctly, you can download a template file to populate with your user data. Download the .csv file that contains headers and sample user information to see exactly the kind of data is needed for each field.

 ![Image of first step in bulk enrollment wizard](./media/sign-up/bulk-enroll-step-1.png)


3. After you’ve created and saved your .csv file, choose **Browse** to select the file. Verify, and choose **Next**. Your users will be uploaded and added to your list of active users.

> [!NOTE]
> Your users won't show up in Intune until they've enrolled a device to be managed.

Now it’s time to head over to Intune to start managing your users, their devices, and their apps.--->

## <a name="keeping-the-admin-experiences-straight"></a>讓管理體驗有條理
<!---### Classic Intune
There are two portals you will use for classic Intune:
- The Office 365 Admin center ([portal.office.com](https://portal.office.com))
- The Intune administration console ([manage.microsoft.com](https://manage.microsoft.com))

Normally, you’ll do your work in the Intune administration console, shown below. This is the site where you set up and manage your groups, policies, devices, and apps.

![Image of Intune administration console](./media/sign-up/intune-admin-console.png)

However, you will use the Office 365 Admin center, shown below, to add and manage your users and other aspects of your account, including billing and support.

![Image of Office 365 Admin center](./media/sign-up/office-admin-center.png)

You can navigate from the Office 365 Admin center to the Intune admin console. The admin centers are under the last item in the left navigation pane. Choose **Intune** to open the Intune admin console in a new tab.

![Image of link to Intune administration console](./media/sign-up/link-to-intune.png)

To get from Intune back to the Office 365 Admin center, choose the **Add Users** task on the Groups Overview page.

![Image of link back to Office 365  Admin center](./media/sign-up/task-add-users.png)--->

<!---### Intune Azure preview--->
Intune Azure 預覽使用三個入口網站︰
- Azure 中的 Intune 儀表板 ([portal.azure.com](https://portal.azure.com))，您可以瀏覽[Azure 入口網站中的 Intune 功能 ](what-is-microsoft-intune.md)。
- Office 365 系統管理中心 ([portal.office.com](https://portal.office.com))，若您未使用 Azure Active Directory 新增及管理使用者，可利用此處執行這些作業。 您也可以管理您帳戶的其他事宜，包括計費及支援。
- 傳統的 Intune 管理主控台 ([manage.microsoft.com](https://manage.microsoft.com))，可讓您探索尚未新增到 Azure 的功能。

一般是在 Intune 儀表板中執行工作，如下所示。 這是您設定及管理您的群組、原則、裝置及應用程式的網站。

您可以選擇 [開啟傳統 Intune 入口網站] 磚，從儀表板移至傳統的 Intune 管理主控台。

若要返回 Intune Azure 預覽，請在瀏覽器網址列中輸入 https://portal.azure.com，然後再次從服務清單中選擇 [Intune]。

 ![Intune 儀表板的映像](./media/intune-azure-dashboard.png)


但是，您將會使用 Office 365 系統管理中心 (如下所示) 來新增及管理您的使用者和您帳戶的其他層面，包括帳單與支援。

![Office 365 系統管理中心的影像](./media/office-admin-center.png)

若要從 Office 365 系統管理中心前往 Intune 儀表板，請在瀏覽器網址列中輸入 https://portal.azure.com。 在服務清單中選擇 [Intune]。

若要從 Intune 回到 Office 365 系統管理中心，請在瀏覽器位址列中輸入 https://portal.office.com。 如已登入 Intune，您會直接跳到 Office 365 系統管理中心。

## <a name="next-steps"></a>後續步驟

### <a name="intune-azure-preview"></a>Intune Azure 預覽
深入了解 [Introduction to Microsoft Intune in the Azure portal preview](what-is-microsoft-intune.md) (Azure 入口網站預覽的 Microsoft Intune 簡介)。
### <a name="classic-intune"></a>傳統的 Intune
評估案例：[評估 Microsoft Intune 中的行動裝置管理功能](https://docs.microsoft.com/intune/understand-explore/mobile-device-management-trial-guide-microsoft-intune)

### <a name="integration-with-other-products"></a>與其他產品整合
深入了解搭配 Intune 使用您的 Azure Active Directory 使用者帳戶：
- [身分識別需求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [目錄同步作業需求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [Multi-Factor Authentication 需求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

深入了解使用 [Intune 搭配 System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management)

