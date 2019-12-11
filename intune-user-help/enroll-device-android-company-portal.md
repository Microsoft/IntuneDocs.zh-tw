---
title: 使用 Intune 公司入口網站註冊 Android 裝置 | Microsoft Docs
description: 描述如何使用 Intune 公司入口網站註冊 Android 裝置
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5baf0e9079cc148101a68e5cd2d3a4ed500f567f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "73414790"
---
# <a name="enroll-your-device-with-company-portal"></a>使用公司入口網站來註冊您的裝置  
註冊您個人或公司擁有的 Android 裝置，以安全地存取公司電子郵件、應用程式和資料。 公司入口網站支援執行 Android 4.4 及更新版本的 Android 裝置 (包括 Samsung Knox)。  
</br>
> [!VIDEO https://www.youtube.com/embed/k0Q_sGLSx6o?rel=0]

> [!NOTE]
> Samsung Knox 是某種類型的安全性，可供特定 Samsung 裝置使用，以提供原生 Android 所提供項目之外的額外保護。 若要查看裝置是否為 Samsung Knox 裝置，請移至 [設定]   > [關於裝置]  。 若該處未列出 **Knox 版本**，表示您的裝置是原生 Android 裝置。

## <a name="enroll-device"></a>註冊裝置  
請務必[從 Google Play 安裝免費 Intune 公司入口網站應用程式](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)。 

在註冊期間，系統可能會要求您選擇最能描述您裝置使用方式的類別。 公司支援人員會使用您的答案來檢查您可以存取的應用程式。  

1. 開啟公司入口網站應用程式並使用您的公司或學校帳戶登入。  

2. 若您收到提示，要求您接受組織的條款及條件，請點選 [全部接受]  。  

   ![[公司入口網站]、[詞彙] 畫面的範例影像，並反白顯示 [全部接受] 按鈕。](./media/accept-terms-1911.png)  


3. 審查您的組織可以查看和無法看到的內容。 然後點選 [繼續]  。


    ![公司入口網站的範例影像中，我們在意您的隱私權畫面，並反白顯示 [繼續] 按鈕。](./media/android-privacy-screen-1911.png)  
4. 在未來的步驟中，檢查預期的內容。 然後按 [**下一步]** 。  

    ![公司入口網站的影像範例、下一個畫面，並反白顯示 [下一步] 按鈕。](./media/android-whats-next-1911.png)  


5. 視您的 Android 版本而定，系統可能會提示您允許存取裝置的特定部分。 這些提示是 Google 要求的，不是由 Microsoft 所控制。  

    針對下列許可權，請按一下 [**允許**]：  
    * **允許公司入口網站進行和管理**通話：此許可權可讓您的裝置與 Intune （貴組織的裝置管理提供者）共用其國際行動工作站設備識別（IMEI）編號。 允許此許可權是安全的。 Microsoft 永遠不會進行或管理通話。  
    * **允許公司入口網站存取您的連絡人**：此許可權可讓公司入口網站應用程式建立、使用及管理您的工作帳戶。  允許此許可權是安全的。 Microsoft 永遠不會存取您的連絡人。 

    如果您拒絕許可權，下次登入公司入口網站時，系統會再次提示您。 若要關閉這些訊息，請選取 [不再詢問]  。 若要管理應用程式許可權，請移至 設定 應用程式 >**應用程式** > **公司入口網站** > 的**許可權** > **電話**。  

6. 啟用裝置管理應用程式。 

    公司入口網站需要裝置系統管理員許可權，才能安全地管理您的裝置。 啟用應用程式可讓您的組織找出可能的安全性問題，例如重複嘗試解除鎖定裝置的失敗，並適當地回應。  

    ![[啟用裝置系統管理員] 畫面的範例影像，其中反白顯示 [啟動] 按鈕。](./media/activate-device-administrator-1911.png)  

> [!NOTE]
> Microsoft 不會控制此畫面上的訊息。 我們瞭解其片語看起來可能有點極端。 公司入口網站無法指定與您的組織相關的限制和存取權。 如果您有關于組織如何使用應用程式的問題，請洽詢您的 IT 支援人員。 前往[公司入口網站網站](https://go.microsoft.com/fwlink/?linkid=2010980)來尋找您組織的連絡資訊。  


7. 您的裝置會開始註冊。 如果您使用 Samsung Knox 裝置，系統會提示您先檢查並確認榆樹代理程式隱私權原則。   

    ![註冊期間所出現之 Samsung Knox 隱私權原則畫面的範例影像。](./media/and-enroll-7-knox-privacy-policy.png)  

8. 在 [**公司存取設定**] 畫面上，確認您的裝置已註冊。 然後點選 [繼續]  。  

    ![[公司存取設定] 畫面公司入口網站的範例影像，顯示已管理的裝置已完成。](./media/update-settings-1911.png)  

9. 您的組織可能會要求您更新您的裝置設定。 請按 [**解析**] 來調整設定。 當您完成更新設定時，請按 [**繼續**]。  

   ![公司入口網站的影像範例、更新裝置設定、反白顯示 [解決] 和 [繼續] 按鈕。](./media/resolve-settings-1911.png)  

10. 當安裝程式完成時，請按一下 [**完成**]。    

    ![公司入口網站 [公司存取設定] 畫面的範例影像，其中顯示已完成的設定和反白顯示的 [完成] 按鈕。](./media/android-enrollment-done-1911.png) 

## <a name="next-steps"></a>後續步驟  

嘗試安裝學校或公司應用程式之前，請移至 [**設定**] [ > ] [**安全性**]，然後開啟 [**未知來源**]。 如果您未在嘗試安裝應用程式之前開啟此選項，則會看到下列訊息：「已封鎖安裝。 基於安全性理由，您的裝置設定成封鎖安裝從未知來源取得的應用程式。」 您可以在訊息上按 [**設定**]，直接移至 [**未知來源**]。  

> [!Note]
> 如果您的組織使用電信費用管理軟體，您需要完成幾個額外步驟，裝置才會完全註冊。 如需詳細資訊，請參閱[這裡](enroll-your-device-with-telecom-expense-management-android.md)。

如果在 Intune 中嘗試註冊裝置時出現錯誤，您可以[寄送電子郵件給您的公司支援人員](send-logs-to-your-it-admin-by-email-android.md)。  

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。  