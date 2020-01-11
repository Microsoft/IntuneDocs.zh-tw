---
title: 在 Intune 公司入口網站中註冊 Windows 10 裝置 | Microsoft Docs
description: 在 Intune 公司入口網站中註冊 Windows 10 裝置的步驟
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/21/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 812e82df-76df-402b-bfe9-29302838f40e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: df83f2763d5fe7ae26ad30fecca56128aaa8437c
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856230"
---
# <a name="enroll-windows-10-devices-with-intune-company-portal"></a>使用 Intune 公司入口網站註冊 Windows 10 裝置

使用 Intune 公司入口網站，在組織的管理下註冊 Windows 10 裝置。 本文描述如何註冊 Windows 10 版本 1607 及更新版本，以及 Windows 10 版本 1511 及先前的版本。 在您開始前，請先[驗證您裝置上的版本](windows-enrollment-company-portal.md#find-windows-10-version-number)，以確認您可以遵循正確的步驟。  

Windows 10 已在各種裝置類型上獲得支援，包括桌面、電話及平板電腦。 無論您使用的裝置為何，註冊步驟都是相同的。 但是，您的畫面可能會和本文中顯示的影像有些不同。  
</br>
> [!VIDEO https://www.youtube.com/embed/TKQxEckBHiE?rel=0]

## <a name="enroll-windows-10-version-1607-and-later-device"></a>註冊 Windows 10 版本 1607 及更新版本的裝置 
下列步驟描述如何註冊執行 Windows 10 版本 1607 及更新版本的裝置。  

1. 移至 [開始]  。 若您是使用 Windows 10 行動裝置版裝置，請繼續前往 [所有應用程式]  清單。

2. 開啟 [設定]  應用程式。 若應用程式無法在您的應用程式清單中取得，請前往搜尋列並鍵入「設定」。

3. 選取 [帳戶]   > [存取公司或學校資源]   > [連接]  。  


    ![選取 [存取公司或學校帳戶]](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

4. 若要前往貴組織的 Intune 登入頁面，請輸入您的公司或學校電子郵件地址。 然後選取 [下一步]  。  


   ![輸入您的工作或學校帳戶](./media/w10-enroll-rs1-set-up-work-or-school-account.png)  

5. 使用您的工作或學校帳戶登入 Intune。  


    ![新增工作或學校帳戶](./media/w10-enroll-rs1-enter-your-credentials.png)  

    最後，您會看到一則訊息，指出您的公司或學校正在註冊您的裝置。

6. 若您的組織要求您為 Windows Hello 設定 PIN，您將會收到提示，要求您輸入驗證碼。 輸入驗證碼，並繼續遵循畫面上的步驟來建立 PIN。  

7. 位於**已全部完成！** 的畫面時，請選取 [完成]。  您的裝置現在已經註冊。  

8. 若要再次檢查您的連線，請返回 [設定]   > [帳戶]   > [存取公司或學校帳戶]  。  您的帳戶現在應該會列出。  


    ![驗證連線已正確設定](./media/w10-enroll-rs1-validate-successful-enrollment.png)  

仍然無法存取您的工作或學校電子郵件、檔案或其他資料嗎？ 了解如何[針對帳戶問題進行疑難排解](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school)。  

## <a name="enroll-windows-10-version-1511-and-earlier-device"></a>註冊 Windows 10 版本 1511 及先前版本的裝置  
下列步驟描述如何註冊執行 Windows 10 版本 1511 及先前版本的裝置。  

1. 移至 [開始]  。 若您是使用 Windows 10 行動裝置版裝置，請繼續前往 [所有應用程式]  清單。

2. 開啟 [設定]  應用程式。 若應用程式無法在您的應用程式清單中取得，請前往搜尋列並鍵入「設定」。

3. 選取 [帳戶]   > [您的帳戶]  。  


    ![選取 [您的帳戶]](./media/W10-enroll-2-accounts-your-account.png)  

5. 選取 [新增公司或學校帳戶]  。  


    ![選取 [新增公司或學校帳戶]](./media/w10-enroll-3-add-work-school-acct.png)  

6. 使用工作或學校認證登入。  


    ![登入](./media/W10-enroll-4-sign-in.png)  

仍然無法存取您的工作或學校電子郵件、檔案或其他資料嗎？ 了解如何在註冊期間[針對帳戶相關問題進行疑難排解](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-your-account)。  

## <a name="it-administrator-support"></a>IT 系統管理員支援   

若您是 IT 系統管理員並在註冊裝置期間發生問題，請參閱[針對 Microsoft Intune 中的 Windows 裝置註冊問題進行疑難排解](https://support.microsoft.com/help/4469913)。 本文列出常見錯誤、其原因，以及解決這些問題的步驟。 

## <a name="next-steps"></a>後續步驟  
若您需要公司入口網站或註冊的協助，請連絡您組織的 IT 支援小組。 您會在[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)中找到他們的連絡資訊。 使用您的工作或學校帳戶登入該網站。  

 

