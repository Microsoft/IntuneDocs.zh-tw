---
title: "建立原則以及將應用程式發行給使用者 | Microsoft Docs"
description: "當您註冊免費 30 天的 Intune 評估版時，如何建立原則並發行應用程式"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 12/12/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3a17884-442a-44f5-bc81-4589e823f65e
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 53b05e0ad1be63315dcb5e5b9938a7d9459cb6c3
ms.openlocfilehash: edcef68c4dd6715c0e3b7c8a164d6266d1c154ae
ms.lasthandoff: 12/14/2016


---


# <a name="create-policies-and-publish-an-app-to-evaluation-users"></a>建立原則以及將應用程式發行給評估使用者

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 原則提供設定，協助您控制行動裝置上的安全性設定、維護電腦的 Windows 防火牆和 Endpoint Protection 設定，以及部署應用程式。 如果您打算在評估期過後，將 Intune 用於實際執行所設定的裝置，請務必遵循[透過 Microsoft Intune 原則管理裝置上的設定和功能](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)和[使用 Microsoft Intune 的 Endpoint Protection 協助保護 Windows 電腦](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)中的指示。

您可以使用 Intune 執行兩種類型的 App 安裝。 第一種是**必要安裝**，會自動將應用程式部署到受管理的裝置。 另一個則是**可用的安裝**，會部署應用程式或應用程式的連結到 Intune 公司入口網站，讓使用者可以選擇是否要將其安裝在電腦上，或安裝在行動裝置上。

使用 Intune 來部署 App 之前，請確定您有適當的授權，以發佈、散佈及使用該 App。 [授權] 工作區可讓您新增及管理透過 Microsoft 大量授權合約購買之應用程式或軟體的授權合約資訊，以及透過其他方式購買的 Microsoft 或非 Microsoft 應用程式或軟體的授權合約資訊。 然後您可以建立授權報表，顯示公司內受管理的授權使用量資訊，以便掌握授權使用活動。

在這些步驟中，當註冊這些裝置之後，您將設定行動裝置組態原則和 Windows 電腦防火牆原則，以及設定 Skype 為行動裝置的可用安裝。 加入並部署新的原則之後，您部署此原則的群組之所有使用者或裝置，都會繼承此設定，當做其基準原則。 稍後從系統管理主控台中的 [原則]  工作區，您隨時可以檢閱和編輯這些原則的詳細資料。

## <a name="create-and-deploy-a-mobile-device-configuration-policy"></a>建立並部署行動裝置組態原則

1.  開啟 [Intune 管理主控台](https://manage.microsoft.com/)。

2.  在左窗格中，選擇 [原則] 圖示。

3.  在 **[原則概觀]** 頁面的 **[工作]** 清單中，選擇 **[新增原則]**。

4.  在原則清單中，展開您想要為其建立原則的平台，選取 [一般設定]，並選擇 [建立及部署自訂原則]，然後選擇 [建立原則]。

5.  當提示您 [選取您要部署此原則的群組] 時，請從清單中選取 [My Trial Users] ，然後選擇 [新增] &gt; [確定]。

當您的原則會出現在設定原則的清單中時，表示已經部署到 **[我的試用使用者]** 群組。 按兩下原則以檢視其設定。

## <a name="publish-the-skype-app-for-mobile-devices"></a>發佈適用於行動裝置的 Skype App

1.  在 [Intune 管理主控台](https://manage.microsoft.com/)中，選擇**應用程式**圖示，然後選擇 [應用程式] &gt; [新增應用程式]。 如果出現提示，請輸入您的 Intune 認證。

    > [!NOTE]
    > 當您第一次啟動 **Intune 軟體發行者** 時，安裝應用程式時會出現短暫延遲的現象。

2.  檢閱安全性警告，然後選擇 [執行]。

3.  在 **[開始之前]** 頁面上，選擇 **[下一步]**。

4.  在 [軟體安裝程式]  頁面的 [選取將此軟體開放給裝置的方式] 中，選取 [外部連結] 。

5.  在 [指定 URL] 中輸入軟體的外部連結，然後選擇 [下一步]。 確定您會在 URL 前面加上 **https://**。 對於 Skype App，可以使用符合您所使用行動裝置平台的下列連結：

    -   **iOS：**[https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android：**[https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8.1**：[http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  在 [軟體描述] 頁面上，提供您要讓使用者在公司入口網站中看到的軟體資訊，然後選擇 [下一步]。 您可以使用下列設定 (在此範例中是 Skype)：

    -   **發行者：**輸入發行者的名稱：**Microsoft**

    -   **名稱：** 輸入 **Skype**

    -   **描述:** 輸入軟體的描述，例如 **Skype 通訊 App**

    -   **類別：** 選取最適合此軟體的類別，例如 [共同作業] 

    -   **在公司入口網站中將此項目顯示為熱門應用程式，並予以反白：**選取此選項可在行動裝置上以顯目的方式將應用程式顯示在公司入口網站中。

    -   **圖示：**  (選擇性) 選擇是否要讓圖示與軟體相關聯。 圖示的大小上限為 250 x 250 像素，但建議的圖示大小為 32 x 32 像素。

7.  在 [摘要] 頁面上，驗證軟體資訊，然後選擇 [上傳]。 選擇 [關閉] 以結束精靈。

8.  在 [Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [應用程式] &gt; [應用程式] &gt; [Skype] &gt; [管理部署]。

9. 在 [選取群組] 頁面上，選取 [My Trial Users]，將軟體部署到該使用者群組，然後選擇 [新增] &gt; [下一步]。

10. 在 [部署動作]  頁面中，從群組的 **[核准]** 欄選取 [可用安裝]  。

11. 選擇 **[完成]**。

## <a name="install-the-skype-app"></a>安裝 Skype App
在行動裝置上開啟公司入口網站，並選擇 [應用程式]，然後安裝 Microsoft Skype。

Intune 行動裝置管理指南到這裡已經結束，但您可以透過後續步驟小節中的連結深入了解 Intune。
## <a name="next-steps"></a>後續步驟
深入了解其他 [Intune 功能](get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)

閱讀[使用 Intune 的常見方式](common-ways-to-use-intune.md)

轉換為[付費訂閱](get-started-with-a-30-day-trial-of-microsoft-intune-step-7.md)

