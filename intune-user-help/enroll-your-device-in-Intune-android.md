---
title: 在 Intune 註冊 Android 裝置 | Microsoft Docs
description: 描述在 Intune 註冊 Android 裝置的方式
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 188c32a2fd38d3445380a9d1898b90a3bb080ae1
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57335202"
---
# <a name="enroll-your-android-device-in-intune"></a>在 Intune 註冊 Android 裝置

如果您的公司或學校使用 Microsoft Intune，您可以註冊 Android 裝置來存取公司電子郵件、檔案和其他資源。 當您註冊裝置時，您的 IT 部門可以管理這些公司或學校資源、保護它們的安全，並讓您能夠自由地使用慣用的裝置來完成工作。 若要深入了解註冊，請參閱[當我安裝公司入口網站應用程式並註冊我的裝置時，會發生什麼情況？](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-android.md)

> [!VIDEO https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment/player]

這些註冊指示適用於原生及 Samsung Knox Android 裝置。 Samsung Knox 是某種類型的安全性，可供特定 Samsung 裝置使用，以提供原生 Android 所提供之外的額外保護。 若要查看裝置是否為 Samsung Knox 裝置，請移至 [設定] > [關於裝置]。 若該處未列出「Knox 版本」，則您擁有原生 Android 裝置。

註冊之前或之後，系統可能會要求您選擇最能描述您裝置使用方式的類別。 公司的支援人員會使用此類別來協助查看您可存取的應用程式。

**註冊 Android 裝置：**

1. 從 [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) 安裝免費 Intune 公司入口網站應用程式。

2. 開啟公司入口網站應用程式。

3. 在公司入口網站的 [歡迎使用] 畫面上，點選 [登入]，然後使用您的公司或學校帳戶進行登入。

   ![Android 版的「公司入口網站」應用程式歡迎畫面，會要求使用者使用其所需的工作或學校帳戶登入。 它也會提醒您不接受 Microsoft 帳戶和其他個人帳戶。](./media/and-enroll-0-welcome-screen.png)   

4. 若公司的支援人員已設定公司條款及條件，請點選 [接受] 以接受條款。 視您目前使用的 Android 版本而定，這個畫面可能與下圖稍有不同。

   ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5. 使用您的公司或學校帳戶和密碼登入公司入口網站應用程式，然後點選 [登入]。

   ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6. 在 [公司存取設定] 畫面上，點選 [繼續]。

   ![公司存取設定畫面](/intune/media/android_cp_enroll_01_1709_new.png)

   > [!NOTE]
   > 黃色三角形並不代表您遇到錯誤。 這些圖示表示註冊程序仍有步驟要完成。

7. 檢閱公司支援人員在您的裝置上可查看及無法查看的項目清單，然後點選 [繼續]。

   ![隱私權設定](/intune/media/android_cp_enroll_02_after_1710.png)

8. 在 [What's next?] \(新功能) 畫面上，閱讀註冊期間會進行的作業，然後點選 [註冊]。

   ![接下來要做什麼畫面](/intune/media/android_cp_enroll_03_after_1710.png)

9. 如果您是使用 Android 6.0 或更新版本，請執行此步驟。 否則請移到下一個步驟。

   如果公司的支援人員已設定特定原則，您可能會看到下列訊息：
   - **是否允許公司入口網站進行和管理通話？**

     ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

   如果您看到此訊息，請點選 [允許]。 您可以放心地點選 [允許]，因為 **Microsoft 絕不會撥打或管理您的電話**！ Google 控制訊息文字，而且 Microsoft 無法變更它。 當您允許存取時，其實是允許您的裝置將裝置的國際移動站設備識別 (IMEI) 編號傳送至 Intune。 IMEI 編號類似於序號，可唯一識別行動裝置。

   如果您拒絕存取，則下次登入公司入口網站時會再次出現此訊息，但點選 [不要再詢問] 方塊，即可關閉未來訊息。 如果您稍後決定允許存取，請移至 [設定] &gt; [應用程式] &gt; [公司入口網站] &gt; [權限] &gt; [電話]，然後開啟權限。

   - **是否允許公司入口網站存取您的連絡人？**

     ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

     如果您看到此訊息，請點選 [允許]。 您可以放心地點選 [允許]，因為 **Microsoft 絕不會存取您的連絡人！** Google 控制訊息文字，而且 Microsoft 無法變更它。 當您允許存取時，其只可讓公司入口網站應用程式建立、使用和管理您的工作帳戶。

     如果您拒絕存取，則下次登入公司入口網站時會再次出現此訊息，但點選 [不要再詢問] 方塊，即可關閉未來訊息。 如果您稍後決定允許存取，請移至 [設定] &gt; [應用程式] &gt; [公司入口網站] &gt; [權限] &gt; [電話]，然後開啟權限。

10. 在 [啟用裝置管理員] 畫面上，點選 [啟用]。

    ![啟用裝置管理員畫面](./media/and-enroll-5-activate.png)

    公司入口網站需要裝置管理員角色來管理您的裝置。 裝置管理員角色可讓您的系統管理員查看特定項目 (例如您嘗試將畫面解除鎖定的次數) 並採取某些動作。

    請記住，這些動作都是為了實現安全性而執行。 公司支援人員不會毫無理由地嘗試侵犯您的隱私權或清除您的資訊，而是要確保公司資料的安全。

    Microsoft 不會控制此訊息，而且我們了解其措辭可能顯得有點極端。 公司入口網站無法只顯示與您組織相關聯的限制和存取。 它們全部都會同時顯示於此畫面上。 如果您針對個別組織的使用方式有疑問，請使用[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)中的連絡資訊，連絡您公司的支援人員以取得詳細資訊。

11. 遵循提示以輸入 PIN 或密碼。 如果您在這部裝置上已設定 PIN 或密碼，您將不會看到這個畫面，或需要輸入新的 PIN 或密碼。

    ![輸入 PIN 或密碼](./media/and-enroll-6-PIN-native.png)

12. 如果您使用 Samsung Knox 裝置，請點選 **[確認]**，然後您會看到一個訊息，指出您的裝置已註冊。 如果您使用原生 Android 裝置，則請注意下方畫面，該畫面顯示您的裝置已註冊。

    ![Samsung Knox 隱私權原則](./media/and-enroll-7-knox-privacy-policy.png)

    此畫面會顯示您的裝置已註冊。

    ![註冊裝置畫面](./media/and-enroll-8-device-enrolling.png)

13. 出現 [公司存取設定] 畫面時，點選 [繼續]。 如果訊息指出您的裝置不相容，請遵循指示來修正問題，然後點選 [繼續]。

    ![裝置不符合規範但已註冊](/intune/media/android_cp_enroll_05_post_1709.png)

    ![出現需要解決的裝置合規性問題](/intune/media/android_cp_enroll_03_post_1709.png)

    點選它們便可以知道有關問題的詳細資訊。

    ![裝置合規性問題展開](/intune/media/android_cp_enroll_04_post_1709.png)

    ![公司存取設定畫面](./media/and-enroll-9d-comp-access-setup.png)  

14. 在 [公司存取設定完成] 畫面上，點選 [完成]。 您的裝置現在已經註冊。

    ![公司存取設定完成畫面](./media/and-enroll-10-comp-access-setup-complete.png)

嘗試安裝公司應用程式之前，請移至 [設定] &gt; [安全性]，然後開啟 [未知來源]。 如果您未在嘗試安裝應用程式之前開啟此選項，則會看到下列訊息：「已封鎖安裝。 基於安全性理由，您的裝置設定成封鎖安裝從未知來源取得的應用程式。」 您可以點選錯誤對話方塊上的 [設定]，移至 [未知來源] 選項。

> [!Note]
> 如果您的組織使用電信費用管理軟體，您需要完成幾個額外步驟，裝置才會完全註冊。 如需詳細資訊，請參閱[這裡](enroll-your-device-with-telecom-expense-management-android.md)。

如果在 Intune 嘗試註冊裝置時出現錯誤，您可以[將註冊錯誤傳送給公司的支援人員](send-enrollment-errors-to-your-it-admin-android.md)。

是否仍需要協助？ 請連絡公司支援人員 (可查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)以取得連絡資訊)，或是撰寫電子郵件給 <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 小組</a>。
