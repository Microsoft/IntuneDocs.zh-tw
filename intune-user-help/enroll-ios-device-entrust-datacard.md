---
title: 使用 Intune 公司入口網站和 Entrust Datacard 註冊 iOS 或 iPadOS 裝置
description: 註冊 iOS 或 iPadOS 裝置，並使用 Entrust Datacard 設定衍生認證驗證。
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
ms.openlocfilehash: bfafa4f35d0b8f1255d66a70c3f7cd0acf01a889
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "73415759"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-entrust-datacard"></a>使用公司入口網站和 Entrust Datacard 設定 iOS 或 iPadOS 裝置

使用 Intune 公司入口網站應用程式註冊您的裝置，以安全地使用行動裝置存取您組織的電子郵件、檔案和應用程式。 您的裝置註冊之後，它就變成「受控」  。 您的組織可以透過 Intune 等行動裝置管理 (MDM) 提供者將原則和應用程式指派給裝置。  

在註冊期間，您也會在您的裝置上安裝衍生的認證。 您的組織可能會要求您在存取資源或簽署和加密電子郵件時，使用衍生的認證做為驗證方法。 

如果您使用智慧卡來執行下列動作，您可能需要設定衍生的認證：  

* 登入學校或公司應用程式、Wi-fi 和虛擬私人網路（VPN）
* 使用 S/MIME 憑證簽署及加密學校或公司電子郵件  

在本文中，您將：  

   * 使用 Intune 公司入口網站註冊行動 iOS 或 iPadOS 裝置。  
   * 從您組織的衍生認證提供者取得衍生認證， [Entrust Datacard](https://www.entrustdatacard.com/)。  

### <a name="what-are-derived-credentials"></a>什麼是衍生認證？  
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
    a. 請按您組織設定指示的連結。 如果您的組織未提供其他指示，您將會收到這篇文章。  
    b. 按一下 [**開始**]。  

    ![公司入口網站設定 mobile 智慧卡存取畫面的範例螢幕擷取畫面。](./media/smart-card-info-intercede.png)

9. 切換至已啟用智慧卡的裝置，並開啟 IdentityGuard。 
10. 尋找 [智慧認證登入] 區域，然後選取 [登入] 按鈕。  
11. 當系統提示您選取憑證時，請挑選您的智慧卡認證。 然後選取 **[確定]** 。 
12. 輸入您的智慧卡 PIN。  
13. 系統會要求您從動作清單中選擇。 選取可讓您註冊衍生的行動智慧認證的帳戶。 連結或按鈕可能會假設**我想要註冊衍生的行動智慧卡認證。**  
14. 選取您已成功下載並安裝具備智慧認證功能的應用程式。 然後繼續前往下一個畫面。   
15. 輸入您的衍生智慧卡認證的相關資訊。  
    a. 針對 [身分識別名稱]，輸入任何名稱，例如*Entrust 衍生*的認證。  
    b. 在下拉式功能表中，選取 [ **Entrust IdentityGudard Mobile 智慧型認證**]。  
    c. 繼續前往下一個畫面。 您會在其下看到具有數位密碼的 QR 代碼。  

16. 返回您的行動裝置。 在 [公司入口網站 >**取得 QR 代碼**] 畫面上，按一下 [**繼續**]。 

    ![公司入口網站取得 QR 代碼畫面的範例螢幕擷取畫面。](./media/get-qr-code-intercede.png)  
17. 請**按 [使用相機** **] > [確定]** 。  

    ![公司入口網站提示的範例螢幕擷取畫面，要求允許相機存取的許可權。](./media/allow-cp-camera-access-intercede.png)  
18. 掃描已啟用智慧卡之裝置上的 QR 代碼影像。  
19. 輸入出現在 QR 代碼底下的數值密碼。  

    ![公司入口網站需要密碼 畫面的範例螢幕擷取畫面，請輸入密碼欄位。](./media/enter-password-derived-credentials.png)   

20. 等候公司入口網站完成裝置的設定。  


## <a name="next-steps"></a>後續步驟  
註冊完成之後，您就可以存取公司資源，例如電子郵件、Wi-fi，以及貴組織提供的任何應用程式。 如需如何在公司入口網站中取得、搜尋、安裝和卸載應用程式的詳細資訊，請參閱：

* [從公司入口網站網站管理應用程式](manage-apps-cpweb.md)  
* [在裝置上使用受管理的應用程式](use-managed-apps-on-your-device-ios.md)  

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。  
