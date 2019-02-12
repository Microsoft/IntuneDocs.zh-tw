---
title: 教學課程 - 保護非受控裝置上的 Exchange Online 電子郵件
titlesuffix: Microsoft Intune
description: 了解如何使用 Intune 應用程式保護原則和 Azure AD 條件式存取來保護 Office 365 Exchange Online。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/11/2018
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8339f91468abca548b3923df4d4380aabb88c5a8
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848707"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>教學課程：保護非受控裝置上的 Exchange Online 電子郵件

了解如何即使在裝置未向裝置管理解決方案 (例如 Intune) 註冊的情況下，也能使用應用程式保護原則搭配條件式存取來保護 Exchange Online。 您將在本教學課程中了解如何： 

> [!div class="checklist"]
> * 建立適用於 Outlook 應用程式的 Intune 應用程式保護原則。 您將透過禁止執行「另存新檔」及限制剪下、複製和貼上等動作，限制使用者能夠對應用程式資料執行的動作。 
> * 建立只允許 Outlook 應用程式存取 Exchange Online 中公司電子郵件的 Azure Active Directory (Azure AD) 條件式存取原則。 此外，您也會針對新式驗證用戶端 (例如 iOS 版和 Android 版 Outlook) 要求使用多重要素驗證 (MFA)。

## <a name="prerequisites"></a>必要條件
  - 您將需要在本教學課程中，使用以下訂用帳戶測試租用戶：
    - Azure Active Directory Premium ([免費試用](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
    - Intune 訂用帳戶 ([免費試用](free-trial-sign-up.md))
    - 包含 Exchange ([免費試用](https://go.microsoft.com/fwlink/p/?LinkID=510938)) 的 Office 365 商務版訂用帳戶

## <a name="sign-in-to-intune"></a>登入 Intune

請以全域管理員或 Intune 服務管理員身分登入 [Intune](https://aka.ms/intuneportal)。 您可以透過選擇 [所有服務] > [Intune]，在 Azure 入口網站中找到 Intune。

## <a name="create-the-app-protection-policy"></a>建立應用程式保護原則
針對本教學課程，我們將設定適用於 Outlook 應用程式的 Intune 應用程式保護原則，以在應用程式層級設置適當的保護。 我們將需要有 PIN 碼才能在工作環境中開啟應用程式。 我們也會限制應用程式間的資料共用，以及防止公司資料被儲存到個人位置。

1.  在 Intune 中，選取 [用戶端應用程式] > [應用程式保護原則] > [新增原則]。
2.  在 [名稱] 中，輸入 **Outlook 應用程式原則測試**。
3.  在 [描述] 中，輸入 **Outlook 應用程式原則測試**。
4.  選取 [應用程式]。 在應用程式清單中，選取 [Outlook]，然後選擇 [選取]。
5.  選取 [設定]。 
6.  在 [資料位置] 底下，針對本教學課程，請選取下列設定：

    - 針對 [允許應用程式將資料傳送到其他應用程式]，選取 [無]。
    - 針對 [允許應用程式接收其他應用程式的資料]，選取 [無]。
    - 針對 [禁止執行 [另存新檔]]，選取 [是]。
    - 針對[限制利用其他應用程式剪下、複製及貼上]，選取 [已封鎖]。
   
     ![選取 Outlook 應用程式保護原則資料重新配置設定](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-data-relocation.png)
    
7.  在 [存取動作] 底下，針對本教學課程，請選取下列設定：

    - 針對 [需要 PIN 碼才可存取]，選取 [是]。
    - 針對 [需要公司認證以進行存取]，選取 [是]。
    - 將所有其他設定保留為其預設值。
 
     ![選取 Outlook 應用程式保護原則存取動作](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-access-actions.png)

9.  選取 [確定]。
10. 選取 [建立]。

隨即會建立適用於 Outlook 的應用程式保護原則。 現在，您可以設定條件式存取來要求裝置使用 Outlook 應用程式。

## <a name="create-conditional-access-policies"></a>建立條件式存取原則
現在，我們將建立兩個條件式存取原則來涵蓋所有裝置平台。 第一個原則將需要新式驗證用戶端 (例如 iOS 版 Outlook 和 Android 版 Outlook)，以使用已核准的 Outlook 應用程式和 MFA。 第二個原則將需要 Exchange ActiveSync 用戶端，以使用已核准的 Outlook 應用程式。 (目前，Exchange Active Sync 不支援裝置平台以外的條件)。 您可以在 Azure AD 入口網站或 Intune 入口網站中設定條件式存取原則。 因為我們已經在 Intune 入口網站中，所以我們將在這裡建立原則。
### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>建立適用於新式驗證用戶端的 MFA 原則
1.  在 Intune 中，選取 [條件式存取] > [原則] > [新原則]。
1.  在 [名稱] 中，輸入**適用於新式驗證用戶端的測試原則**。 
3.  在 [指派] 底下，選取 [使用者和群組]。 在 [包含] 索引標籤中，選取 [所有使用者]，然後選取 [完成]。

4.  在 [指派] 底下，選取 [雲端應用程式]。 因為我們想要保護 Office 365 Exchange Online 電子郵件，所以我們將依照下列步驟選取它：
     
    1. 在 [包含] 索引標籤上，選擇 [選取應用程式]。
    2. 選擇 [選取]。 
    3. 在應用程式清單中，選取 [Office 365 Exchange Online]，然後選擇 [選取]。 
    4. 選取 [完成]。
  
    ![選取 Office 365 Exchange Online 應用程式](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

5.  在 [指派] 底下，選取 [條件] > [裝置平台]。
     
    1. 在 [設定] 底下，選取 [是]。
    2. 在 [包含] 索引標籤上，選取 [所有平台 (包括未受支援的)]。 
    3. 選取 [完成]。
   
6.  在 [條件] 窗格上，選取 [用戶端應用程式]。
     
    1. 在 [設定] 底下，選取 [是]。
    2. 選取 [行動應用程式與桌面用戶端] 和 [新式驗證用戶端]。
    3. 取消選取其他核取方塊。
    4. 選取 [完成]，然後再次選取 [完成]。
    
    ![選取 Office 365 Exchange Online 應用程式](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

7.  在 [存取控制] 底下，選取 [授與]。 
     
    1. 在 [授與] 窗格中，選取 [授與存取權]。
    2. 選取 [需要多重要素驗證]。
    4. 選取 [需要經過核准的用戶端應用程式]。
    5. 在 [針對多個控制項] 底下，選取 [需要所有選取的控制項]。 此設定可確保選取的兩項需求會在裝置嘗試存取電子郵件時強制執行。
    6. 選擇 [選取]。
     
    ![選取 Office 365 Exchange Online 應用程式](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

8.  在 [啟用原則] 底下，選取 [開啟]。
     
    ![選取 Office 365 Exchange Online 應用程式](media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)

9.  選取 [建立]。

隨即會建立適用於新式驗證用戶端的條件式存取原則。 現在，您可以建立適用於 Exchange Active Sync 用戶端的原則。

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>建立適用於 Exchange Active Sync 用戶端的原則
1.  在 Intune 中，選取 [條件式存取] > [原則] > [新原則]。
2.  在 [名稱] 中，輸入**適用於 EAS 用戶端的測試原則**。 
3.  在 [指派] 底下，選取 [使用者和群組]。 在 [包含] 索引標籤中，選取 [所有使用者]，然後選取 [完成]。

4.  在 [指派] 底下，選取 [雲端應用程式]。 透過下列步驟選取 Office 365 Exchange Online 電子郵件：
     
    1. 在 [包含] 索引標籤上，選擇 [選取應用程式]。
    2. 選擇 [選取]。 
    3. 在應用程式清單中，選取 [Office 365 Exchange Online]，然後選擇 [選取]。 
    4. 選取 [完成]。

5.  在 [指派] 底下，選取 [條件] > [裝置平台]。
     
    1. 在 [設定] 底下，選取 [是]。
    2. 在 [包含] 索引標籤中，選取 [所有平台 (包括未受支援的)]，然後選取 [完成]。 
    3. 再次選取 [完成]。

6.  在 [條件] 窗格上，選取 [用戶端應用程式]。
     
    1. 在 [設定] 底下，選取 [是]。
    2. 選取 [行動應用程式與桌面用戶端]。
    3. 選取 [Exchange ActiveSync 用戶端] 和 [僅將原則套用至支援的平台]。 
    4. 清除所有其他核取方塊。
    5. 選取 [完成]，然後再次選取 [完成]。
    
    ![選取 Office 365 Exchange Online 應用程式](media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)

7.  在 [存取控制] 底下，選取 [授與]。 
     
    1. 在 [授與] 窗格中，選取 [授與存取權]。
    4. 選取 [需要經過核准的用戶端應用程式]。 清除所有其他核取方塊。
    6. 選擇 [選取]。
     
    ![選取 Office 365 Exchange Online 應用程式](media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)

8.  在 [啟用原則] 底下，選取 [開啟]。

9.  選取 [建立]。

您的應用程式保護原則和條件式存取現已準備就緒，可供進行測試。 

## <a name="try-it-out"></a>試試看
有了您已建立的原則之後，裝置將必須在 Intune 中註冊並使用 Outlook 行動應用程式，才能存取 Office 365 電子郵件。 若要在 iOS 裝置上測試此案例，請嘗試使用您測試租用戶中使用者的認證登入 Exchange Online。
1. 若要在 iPhone 上測試，請前往 [設定] > [密碼與帳戶] > [新增帳戶] > [Exchange]。
2. 輸入您測試租用戶中使用者的電子郵件地址，然後按 [下一步]。
3. 按 [登入]。
4. 輸入測試使用者的密碼，然後按 [登入]。
5. 隨即會出現「需要更多資訊」訊息，這表示系統將提示您設定 MFA。 請繼續操作並設定額外的驗證方法。
6. 接下來，您會看到一則訊息，指出您嘗試使用尚未經 IT 部門核准的應用程式來開啟此資源。 這表示系統目前封鎖您使用原生郵件應用程式。 請取消登入。
7.  開啟 Outlook 應用程式，然後選取 [設定] > [新增帳戶] > [新增電子郵件帳戶]。
8. 輸入您測試租用戶中使用者的電子郵件地址，然後按 [下一步]。
9. 按 [使用 Office 365 登入]。 系統將會提示您進行額外的驗證和註冊。 在您登入之後，即可測試剪下、複製、貼上及「另存新檔」等動作。

## <a name="clean-up-resources"></a>清除資源
當不再需要測試原則時，您可以將它們移除。
1. 請以全域管理員或 Intune 服務管理員身分登入 [Intune](https://aka.ms/intuneportal)。
2. 選取 [裝置合規性] > [原則]。
3. 在 [原則名稱] 清單中，選取測試原則的操作功能表 (**...**)，然後選取 [刪除]。 選取 [確定] 以確認。
4. 選取 [條件式存取] > [原則]。
5. 在 [原則名稱] 清單中，選取每個測試原則的操作功能表 ([...])，然後選取 [刪除]。 選取 [是] 確認。

 ## <a name="next-steps"></a>後續步驟 
在本教學課程中，您已建立應用程式保護原則來限制使用者能夠使用 Outlook 應用程式來執行的動作，並已建立條件式存取原則來要求使用 Outlook 應用程式，以及針對新式驗證用戶端要求使用 MFA。 若要了解如何使用 Intune 搭配條件式存取來保護其他應用程式和服務，請參閱[設定條件式存取](conditional-access.md)。
