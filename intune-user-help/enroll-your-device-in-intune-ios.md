---
title: 設定 iOS 裝置對您公司資源的存取 | Microsoft Docs
description: 描述如何讓 Intune 管理您的 iOS 裝置
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/05/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d0c7ac239a67a51ba7165771206883f3c46f5f55
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292419"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>設定 iOS 裝置對公司資源的存取  

使用 Intune 公司入口網站應用程式註冊您的 iOS 裝置，以安全地存取您組織的電子郵件、檔案和應用程式。

您的裝置註冊之後，它就*受控*。 您的組織可以將原則和應用程式，指派給透過行動裝置管理 (MDM) 提供者，例如 Intune 的裝置。  

若要維護從您的裝置存取公司或學校資訊，您必須設定裝置以符合組織的偏好設定。 本文說明如何使用公司入口網站來註冊您的裝置及維護您的組織設定需求。 

> [!NOTE]
> 如果您已嘗試在郵件應用程式中存取公司電子郵件，並且收到提示讓您管理裝置，則您位於正確位置。 請遵循以下指示，在 iOS 裝置上存取電子郵件以及其他公司資源。  

## <a name="what-to-expect-from-the-company-portal-app"></a>公司入口網站應用程式的預期行為  

### <a name="security"></a>安全性  
在初始設定期間，應用程式需要您向組織自我驗證。 應用程式接著會通知您必須更新的任何裝置設定。 例如，組織通常會設定您必須符合的密碼字元數下限或上限需求。     

### <a name="protection"></a>保護  
註冊裝置之後，公司入口網站應用程式會繼續確保您的裝置受到保護。 例如，如果您從未受信任的來源安裝應用程式，應用程式會提醒您有時會撤銷公司資料的存取權。 這種原則在組織中很常見，而且通常需要您先解除安裝未受信任的應用程式，然後您才能重新取得存取。  

### <a name="setting-notifications"></a>設定通知  
如果在註冊之後，您的組織強制執行新的安全性需求 (例如多重要素驗證)，公司入口網站應用程式會通知您。 您將有機會調整設定，以便繼續在裝置上工作。  

若要深入了解註冊，請參閱[當我安裝公司入口網站應用程式並註冊我的裝置時，會發生什麼情況？](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios)  

## <a name="enroll-your-ios-device"></a>註冊 iOS 裝置  

移至 App store 下載並安裝[Intune 公司入口網站應用程式](install-and-sign-in-to-the-intune-company-portal-app-ios.md)您裝置上。 您也需要維護的 Wi-fi 連線，並在註冊期間存取 Safari。 

暫停超過幾分鐘，在註冊期間，可能會導致應用程式關閉或結束安裝程式。 如果發生這種情況，請開啟公司入口網站應用程式，並再試一次。  

1. 開啟公司入口網站並使用您的公司或學校帳戶登入。 

    ![公司入口網站應用程式中，登入的範例螢幕擷取畫面。](./media/ios-01-cp-enroll-1903.PNG)  

2. 當系統提示您收到 公司入口網站通知，請點選 **允許。** 公司入口網站會使用通知來警示您，如果您的裝置設定，例如需要更新。 

    ![公司入口網站首頁上，[通知] 提示字元的範例螢幕擷取畫面。](./media/ios-04-cp-enroll-1903.PNG)  

3. 在 **設定存取**畫面上，選取**開始。**  

     ![公司入口網站中，[設定存取權] 畫面的範例螢幕擷取畫面。](./media/ios-05-cp-enroll-1903.PNG)  

4. 閱讀您的組織可以和無法看到的裝置資訊的清單。 然後點選**繼續**。  

5. 閱讀指示，在**後續步驟為何？** 螢幕。 當您準備要下載並安裝管理設定檔，請點選**繼續**。  

 > [!IMPORTANT]
> 這些下一個步驟和螢幕會依您的 iOS 版本而有所不同。 請依照您的 iOS 版本。 

6. Safari 中開啟您裝置上的公司入口網站。 當系統提示您下載的組態設定檔時，點選**允許**。 如果您是執行的裝置上：  
    * iOS 12.2 及更新版本： 下載完成時，點選 **完成。** 繼續進行這篇文章中的步驟 7。
    * 12.1 及更早版本的 iOS： 您將會自動重新導向至 [設定] 應用程式。 請跳至這篇文章中的步驟 8。  
 
    如果您不小心按**忽略**，重新整理頁面。 系統會提示您開啟公司入口網站應用程式。 您可以從應用程式中，點選**再次下載**。

  > [!NOTE]
  > 您必須安裝管理設定檔中所述的下一個步驟中下載它的 8 分鐘。 如果不這麼做，將會移除的設定檔，您必須重新啟動註冊。  

7. 12.2 和更新版本的 iOS： 當系統提示開啟公司入口網站，請點選**開啟**。 **安裝管理設定檔**畫面會列出安裝設定檔的步驟。

    ![公司入口網站中，安裝管理設定檔 畫面的範例螢幕擷取畫面。](./media/ios-1904-settings-icon.PNG)  

8. 移至 [設定] 應用程式，並點選**下載設定檔**。  

    如果**下載設定檔**不會顯示為選項，請移至**一般** > **設定檔**。 如果您仍看不到設定檔，您可能需要再次進行下載。  

    ![範例螢幕擷取畫面設定 應用程式，設定下載設定檔。](./media/ios-1904-settings-badge.PNG)  

9. 點選 [安裝]。  
    
10. 變更您的裝置密碼 然後點選**安裝**。    

    ![範例螢幕擷取畫面設定 應用程式，安裝設定檔畫面中，與資料指標上的 安裝 按鈕。](./media/ios-1904-password-install.PNG)  


11. 下一個畫面是裝置管理的標準系統警告。 若要繼續進行安裝，請點選**安裝**。 如果系統提示您信任遠端管理，請點選**信任**。  

    ![範例螢幕擷取畫面設定 應用程式中，根憑證及行動裝置管理的標準系統警告畫面。](./media/ios-15-cp-enroll-1903.PNG)  

12. 安裝完成後，點選**完成**。 若要確認已安裝設定檔，請前往**設定檔與裝置管理**設定。 您應該會看到底下所列的設定檔**行動裝置管理**。   

    ![設定應用程式設定檔與裝置管理的範例螢幕擷取畫面顯示 管理設定檔的設定。](./media/ios-00-cp-enroll-1903.PNG)  

13. 返回公司入口網站應用程式。 公司入口網站就會開始同步處理，並設定您的裝置。 公司入口網站可能會提示您更新其他裝置設定。 如果它存在，請點選**繼續**。  

    ![範例螢幕擷取畫面的公司入口網站中，[設定存取] 的螢幕，以設定需求旁的黃色三角形。](./media/ios-12-cp-enroll-1903.PNG)  

14. 您知道該安裝程式時，完成清單中的所有項目顯示綠色的圓形。 點選 [完成]。   
    
    ![用公司入口網站的範例螢幕擷取畫面，「 您已大功告成 ！ 」 畫面，其中顯示所有的綠色圓圈。](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> 如果您的組織監視語音和資料的限制，或您提供公司擁有的裝置，您可能必須完成幾個步驟。 如果系統提示您安裝**Datalert**應用程式，請參閱[在電信費用管理註冊裝置](enroll-your-device-with-telecom-expense-management-ios.md)。 如果您的組織是 Apple 的裝置註冊計劃的一部分，找出[如何註冊公司擁有裝置](enroll-your-device-dep-ios.md)。  

## <a name="next-steps"></a>後續步驟  
尋找可協助您在公司或學校的應用程式。 了解[如何應用程式都會提供](use-managed-apps-on-your-device-ios.md)您透過公司入口網站。  

是否仍需要協助？ 請向公司支援人員確認。 您可以在[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)中找到他們的連絡資訊。  
