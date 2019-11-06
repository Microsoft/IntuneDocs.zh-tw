---
title: 使用 Intune 公司入口網站和 DISA Purebred 註冊 iOS 或 iPadOS 裝置
description: 瞭解如何註冊 iOS 或 iPadOS 裝置，並使用 DISA Purebred 設定衍生認證驗證。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilver
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c484b98466c1418016f4ebc6cc805e412d7891e
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415785"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-disa-purebred"></a>使用公司入口網站和 DISA Purebred 設定 iOS 或 iPadOS 裝置  

使用 Intune 公司入口網站應用程式註冊您的裝置，以安全地使用行動裝置存取您組織的電子郵件、檔案和應用程式。 您的裝置註冊之後，它就變成「受控」  。 您的組織可以透過 Intune 等行動裝置管理 (MDM) 提供者將原則和應用程式指派給裝置。  

在註冊期間，您也會在您的裝置上安裝衍生的認證。 您的組織可能會要求您在存取資源或簽署和加密電子郵件時，使用衍生的認證做為驗證方法。 

如果您使用智慧卡來執行下列動作，您可能需要設定衍生的認證：

* 登入學校或公司應用程式、Wi-fi 和虛擬私人網路（VPN）
* 使用 S/MIME 憑證簽署及加密學校或公司電子郵件  

在本文中，您將：  

   * 使用 Intune 公司入口網站註冊行動 iOS 或 iPadOS 裝置。  
   * 從您組織的衍生認證提供者（ [DISA Purebred](https://cyber.mil/pki-pke/purebred/)）取得衍生認證。  

## <a name="what-are-derived-credentials"></a>什麼是衍生認證？  
衍生的認證是衍生自智慧卡認證並安裝在您的裝置上的憑證。 它會授與您對工作資源的遠端存取許可權，同時防止未經授權的使用者存取機密資訊。  

衍生認證是用來： 
* 驗證登入學校或公司應用程式、Wi-fi 和 VPN 的學生和員工
* 使用 S/MIME 憑證簽署及加密學校或公司電子郵件

衍生認證是適用於衍生個人識別驗證 (PIV) 認證的國家標準暨技術研究院 (NIST) 指導方針實作，是特殊發行集 (SP) 800-157 的一部分。  

## <a name="prerequisites"></a>必要條件

 若要完成註冊，您必須擁有：

* 您學校或工作提供的智慧卡
* 存取可讓您使用智慧卡登入的電腦或 kiosk
* 您的行動裝置
* 適用于 iOS 和 iPadOS 的 Intune 公司入口網站應用程式已安裝在您的裝置上   

在安裝期間，您也必須聯絡 Purebred 代理程式或代表。      

## <a name="enroll-device"></a>註冊裝置  
1. 在您的行動裝置上開啟適用于 iOS/iPadOS 的公司入口網站應用程式，並使用您的工作帳戶登入。  

2. 寫下螢幕程式碼。  

    ![具有螢幕訊息和程式碼公司入口網站應用程式的範例影像。](./media/copy-code-intercede.png)  
3. 切換至已啟用智慧卡的裝置，然後移至 [https://microsoft.com/devicelogin ]。 
4. 輸入您先前記下的程式碼。  

    ![公司入口網站網站 [輸入碼] 提示的範例螢幕擷取畫面。](./media/enter-code-intercede.png)   

5. 插入智慧卡以進行登入。  
6. 返回行動裝置上的公司入口網站應用程式，並遵循畫面上的指示來註冊您的裝置。  
7. 註冊完成後，公司入口網站會通知您設定智慧卡。 點選通知。 如果您沒有收到通知，請檢查您的電子郵件。   

    ![裝置主畫面上公司入口網站推播通知的範例螢幕擷取畫面。](./media/action-required-in-app-intercede.png)  
8. 在 [**設定行動智慧卡存取**] 畫面上：  
    a. 請按下您組織設定指示的連結。 如果您的組織未提供其他指示，您將會收到這篇文章。  
    b. 按一下 [**開啟**] 以開啟 Purebred 應用程式。  

    ![公司入口網站設定 mobile 智慧卡存取畫面的範例螢幕擷取畫面。](./media/smart-card-open-disa-purebred.png)  
9. 當系統提示您允許公司入口網站開啟 Purebred 註冊應用程式時，請選取 [**開啟**]。   

    ![開啟 DISA Purebred 應用程式之公司入口網站提示的範例螢幕擷取畫面。](./media/open-app-prompt-disa-purbred.png)  
10. 當應用程式運作時，請與您組織的 Purebred 代理程式合作，以設定及下載 Purebred 預先註冊的設定檔。   
11. 移至 設定 應用程式 >**一般** > **設定檔 & 裝置管理** > **安裝設定檔**，然後按一下 **安裝**。  
12. 輸入您的裝置密碼。  
13. 安裝設定檔。 您可能需要再按一次 [**安裝**]，才能開始安裝。 
14. 返回 Purebred 註冊應用程式。 遵循您的 Purebred 代理程式指示繼續進行。  
 
15. 下載設定檔之後，請移至 設定 應用程式 > **一般** > **設定檔 & 裝置管理** > **安裝設定檔**，然後按一下 **安裝**。   
16.  輸入您的裝置密碼。
17. 安裝設定檔。 您可能需要再按一次 [**安裝**]，才能開始安裝。 
18. 安裝完成之後，請返回公司入口網站應用程式。  
19.  在 [**設定行動智慧卡存取**] 畫面上，按一下 [**繼續**]。  

20. 從 [匯**入憑證**] 畫面中，您將會抓取並匯入您從 DISA Purebred 取得的衍生認證。  

    a. 點選 [繼續]  。   

    ![[公司入口網站設定匯入憑證] 畫面的範例螢幕擷取畫面。](./media/import-certificate-disa-purebred.png)  
    b. 前往 iCloud 磁片磁碟機**流覽** > **位置**並點出**更多位置**。  

    ![iCloud 磁片磁碟機的範例螢幕擷取畫面，流覽功能表反白顯示更多位置選項。](./media/icloud-drive-more-locations.png)  
    c. 請按此開關以啟用**Purebred 金鑰鏈**。  

    ![ICloud 磁片磁碟機的範例螢幕擷取畫面，流覽視圖，反白顯示已啟用 Purebred 金鑰鏈參數。](./media/icloud-drive-enable-purebred-keychain.png)   

    d. 請按**Purebred 認證套件**。  

    ![iOS 畫面的範例螢幕擷取畫面，其中包含可選取的 Purebred 認證套件選項。](./media/purebred-credential-package.png)  
    f. 憑證清單隨即出現。 選取其中一個，然後按 [匯**入金鑰**]。  

    ![可選取憑證清單的範例螢幕擷取畫面，其中一個已選取。](./media/import-purebred-keychain.png) 
21. 返回公司入口網站應用程式，並等候公司入口網站完成裝置的設定。   

## <a name="next-steps"></a>後續步驟  
註冊完成之後，您就可以存取公司資源，例如電子郵件、Wi-fi，以及貴組織提供的任何應用程式。 如需如何在公司入口網站中取得、搜尋、安裝和卸載應用程式的詳細資訊，請參閱：

* [從公司入口網站網站管理應用程式](manage-apps-cpweb.md)  
* [在裝置上使用受管理的應用程式](use-managed-apps-on-your-device-ios.md)  

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。
