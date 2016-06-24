---
# required metadata

title: 建立原則及發行應用程式 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 建立原則及發行 App
Intune 原則提供設定，協助您控制行動裝置上的安全性設定、維護電腦的 Windows 防火牆和 Endpoint Protection 設定，以及部署應用程式。 若要深入了解，請參閱[透過 Microsoft Intune 原則管理裝置上的設定和功能](/Intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)和[使用 Microsoft Intune 的 Endpoint Protection 協助保護 Windows 電腦](/Intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)。

您可以使用 Intune 執行兩種類型的 App 安裝。 第一個是 **必要的安裝**，會自動將 App 部署到受管理的電腦。 另一個則是**可用的安裝**，會部署應用程式或應用程式的連結到 Intune 公司入口網站，讓使用者可以選擇是否要將其安裝在電腦上，或安裝在行動裝置上。

<!-- this section really isn't necessary and confuses a lot of people because most mobile device apps aren't licensed this way (and our licensing/reporting features aren't super helpful). I think it's best to avoid this during a quick start guide.

Before using Intune to deploy apps, make sure that you have the appropriate licenses to publish, distribute, and use the app. The Licenses workspace lets you add and manage license agreement information for apps or software purchased through Microsoft Volume Licensing agreements, and for Microsoft or non-Microsoft software that was purchased by other means. You can then create license reports that display managed license usage information throughout your company to stay informed of license usage activity.
-->

下列步驟協助您設定行動裝置組態原則、Windows 電腦防火牆原則，並將 Skype 設定為可供行動裝置在註冊後安裝。

> [!TIP]
> 加入並部署新的原則之後，您部署此原則的群組之所有使用者或裝置，都會繼承此設定，當做其基準原則。 稍後從 [原則] 工作區，您隨時可以檢閱和編輯這些原則的詳細資料。


## 建立並部署行動裝置組態原則

1.  開啟 [Intune 管理主控台](https://manage.microsoft.com/)。

2.  在左窗格中，選擇 [原則] 圖示。

    ![admin-console-policy-workspace](./media/policy.png)

3.  在 **[原則概觀]** 頁面的 **[工作]** 清單中，選擇 **[新增原則]**。

4.  在原則清單中，展開您想要建立原則的平台，然後選擇 **[一般設定]** > **[使用建議的設定建立及部署原則]** > **[建立原則]**。

5.  當提示 **[選取您要部署此原則的群組]** 時，請從可用群組的清單中選擇群組，再依序選擇 **[新增]**  >  **[確定]**。

您的原則會出現在設定原則清單中，而且已經部署到 [Intune 使用者] 群組。 按兩下原則以檢視其設定。

## 發佈適用於行動裝置的 Skype App

1.  在 [Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [應用程式] 圖示，然後選擇 [應用程式] > [新增應用程式]。 如果出現提示，請輸入您的 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 認證。

    ![admin-console-apps-workspace](./media/apps.png)

    > [!NOTE] 當您第一次啟動 **Intune 軟體發佈者**時，安裝應用程式時會出現短暫延遲的現象。

2.  檢閱安全性警告，然後選擇 **[執行]**。

3.  在 **[開始之前]** 頁面上，選擇 **[下一步]**。

4.  在 **[軟體安裝程式]** 頁面的 **[選取將此軟體開放給裝置使用的方式]** (Select how this software is made available to devices) 中，選擇 **[外部連結]**。

5.  在 [指定 URL] 中輸入軟體的外部連結，然後選擇 [下一步]。 請確定您會在 URL 前面加上 **http://**。 對於 Skype App，可以使用符合您所使用行動裝置平台的下列連結：

    -   **iOS：**[https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android：**[https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8 或 Windows Phone 8.1：**[http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  在 [軟體描述] 頁面上，提供您要讓使用者在公司入口網站中看到的軟體資訊，然後選擇 [下一步]。 您可以使用下列設定 (在此範例中是 Skype)：

    -   **發行者：** 輸入發行者的名稱："Microsoft"。

    -   **名稱：** 輸入 **Skype**

    -   **描述:** 輸入軟體的描述，例如 **Skype 通訊 App**

    -   **類別：** 選取最適合此軟體的類別，例如 [共同作業] 

    -   **在公司入口網站中將此項目顯示為熱門應用程式，並予以反白：**選取此選項可在行動裝置上以顯目的方式將應用程式顯示在公司入口網站中。

    -   **圖示：**選擇是否要讓圖示與軟體相關聯。 選擇性圖示的大小上限為 250 x 250 像素，建議的大小為 32 x 32 像素。

7.  在 [摘要] 頁面上，驗證軟體資訊，然後選擇 [上傳]。 選擇 [關閉] 以結束精靈。

8.  在 [Intune 管理主控台](https://manage.microsoft.com/)中，選擇 **[應用程式]** > **[應用程式]** > **[Skype]** > **[管理部署]**。

9. 在 **[選取群組]** 頁面上，選擇 **[Intune 使用者]**，將軟體部署到該使用者群組，然後選擇 **[新增]** > **[下一步]**。

10. 在 [部署動作]  頁面中，從群組的 **[核准]** 欄選取 [可用安裝]  。

11. 選擇 **[完成]**。

現在可以從公司入口網站將 Skype 應用程式安裝到行動裝置，但首先您必須在電腦和行動裝置上安裝 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 軟體。


### 後續步驟
恭喜！ 您剛完成 *Intune 快速入門指南*的步驟 6。

>[!div class="step-by-step"]

>[&larr; **組織使用者和裝置**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)       [**自訂公司入口網站** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-7.md)  


<!--HONumber=Jun16_HO3-->


