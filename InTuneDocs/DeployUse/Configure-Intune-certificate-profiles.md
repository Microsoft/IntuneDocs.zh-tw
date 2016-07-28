---
title: "設定憑證設定檔 | Microsoft Intune"
description: "了解如何建立 Intune 憑證設定檔。"
keywords: 
author: nbigman
manager: Arob98
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 72288296d966b9b9fae4fd721b4460528213f626
ms.openlocfilehash: 40ae2ce3ea4393d24770c010bf5292ca1829a7f1


---

# 設定 Intune 憑證設定檔
依[設定 SCEP 的憑證設定檔](configure-certificate-infrastructure-for-scep.md)或[設定 PFX 的憑證基礎結構](configure-certificate-infrastructure-for-pfx.md)所述設定基礎結構和憑證之後，您可以設定憑證設定檔：

**工作 1** - 匯出信任的根 CA 憑證**工作 2** - 建立信任的 CA 憑證設定檔**工作 3** - 請執行下列兩項其中之一：

建立 SCEP 憑證設定檔

建立 .PFX 憑證設定檔

### 工作 1 - 匯出信任的根憑證
從發行 CA 或信任發行 CA 的任何裝置，將信任的根 CA 憑證匯出為 **.cer** 檔案。 不要匯出私密金鑰。

當您設定信任的憑證設定檔時，會將此憑證匯入。

### 工作 2 - 建立信任的憑證設定檔
您必須先建立**信任的憑證設定檔**，再建立 SCEP 或 .PFX 憑證設定檔。 每個行動裝置平台都需要一個信任的憑證設定檔和 SCEP 或 .PFS 設定檔。

##### 建立可信任的憑證設定檔

1.  開啟 [Intune 管理主控台](https://manage.microsoft.com)，然後按一下 [原則] &gt; [新增原則]。

2.  設定下列其中一種原則類型：

    **Android &gt; 信任的憑證設定檔 (Android 4 和更新版本)**

    **iOS &gt; 信任的憑證設定檔 (iOS 7.1 和更新版本)**

    **Mac OS X &gt; 信任的憑證設定檔 (Mac OS X 10.9 及更新版本)**

    **Windows &gt; 信任的憑證設定檔 (Windows 8.1 和更新版本)**

    **Windows &gt; 信任的憑證設定檔 (Windows Phone 8.1 和更新版本)**

    深入了解：[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

3.  提供必要的資訊，為 Android、iOS、Mac OS X、Windows 8.1 或 Windows Phone 8.1 設定信任的憑證設定檔設定。 在 [憑證檔案] 設定中，匯入從您的發行 CA 匯出的信任的根 CA 憑證 (**.cer**)。 [目的地存放區] 設定僅適用於執行 Windows 8.1 和更新版本的裝置，且僅當裝置有一個以上的憑證存放區時才適用。


4.  完成之後，請按一下 [儲存原則] 。

新的原則會顯示在 [原則]  工作區中，它現在可以部署。

### 工作 3 - 建立 SCEP 或 .PFX 憑證設定檔
建立信任的 CA 憑證設定檔之後，請為您想要使用的每個平台建立 SCEP 或 .PFX 憑證設定檔。 當您建立 SCEP 憑證設定檔時，必須為該個相同平台指定信任的憑證設定檔。 這會連結兩個憑證設定檔，不過您仍然必須分別部署每個設定檔。

##### 建立 SCEP 憑證設定檔

1.  開啟 [Intune 管理主控台](https://manage.microsoft.com)，然後按一下 [原則] &gt; [新增原則]。

2.  設定下列其中一種原則類型：

    **Android &gt; SCEP 憑證設定檔 (Android 4 和更新版本)**

    **iOS &gt; SCEP 憑證設定檔 (iOS 7.1 和更新版本)**

    **Mac OS X &gt; SCEP 憑證設定檔 (Mac OS X 10.9 及更新版本)**

    **Windows &gt; SCEP 憑證設定檔 (Windows 8.1 和更新版本)**

    **Windows &gt; SCEP 憑證設定檔 (Windows Phone 8.1 和更新版本)**

    深入了解：[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

3.  遵循設定檔設定頁面的指示來設定 SCEP 憑證設定檔設定。

4.  完成之後，請按一下 [儲存原則] 。

新的原則會顯示在 [原則]  工作區中，它現在可以部署。

##### 建立 .PFX 憑證設定檔

1.  開啟 [Intune 管理主控台](https://manage.microsoft.com)，然後按一下 [原則] &gt; [新增原則]。

2.  設定下列其中一種原則類型：



-   **Android &gt;.PFX 憑證設定檔 (Android 4 和更新版本)**

    -   **Windows &gt; PKCS #12 (.PFX) 憑證設定檔 (Windows 10 和更新版本)**

    -   **Windows &gt; PKCS #12 (.PFX) 憑證設定檔 (Windows Phone 10 和更新版本)**

    -    **iOS > PKCS #12 (.PFX) 憑證設定檔 (iOS 7.1 和更新版本)**    

    深入了解：[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

3.  提供原則表單上所要求的資訊。

4.  完成之後，請按一下 [儲存原則] 。

新的原則會顯示在 [原則]  工作區中，它現在可以部署。

## 部署憑證設定檔
當您部署憑證設定檔時，來自信任的 CA 憑證設定檔的憑證檔案會安裝在裝置上，並且裝置會使用 SCEP 或 .PFX 憑證設定檔來建立裝置的憑證要求。

只會根據在建立設定檔時所使用的平台，在適用裝置上安裝憑證設定檔。

-   您可以將憑證設定檔部署到使用者集合或裝置集合。

    > [!TIP]
    > 若要允許在裝置註冊之後快速將憑證發行至裝置，請將此憑證設定檔部署到使用者群組 (而不是裝置群組)。 如果您部署至裝置群組，必須先執行完整的裝置註冊，裝置才會接收原則。

-   雖然每個設定檔是個別部署，但必須同時部署信任的根和 SCEP/.PFX 設定檔，否則 SCEP/.PFX 憑證原則將會失敗。

您部署憑證設定檔的方式與部署 Intune 的其他原則相同：

1.  在 [原則]  工作區中，選取您要部署的原則，然後按一下 [管理部署] 。

2.  在 [管理部署]  對話方塊中：

    -   **部署原則** - 選取您要部署原則的一或多個群組，然後按一下 [新增] &gt; [確定]。

    -   **關閉對話方塊但不加以部署** - 按一下 [取消]。

當您選取某項已部署的原則時，您可以在原則清單下方檢視有關部署的進一步資訊。
###  後續步驟

您現在可以使用憑證來協助保護電子郵件、Wi-Fi 及 VPN 設定檔︰

-  [使用電子郵件設定檔來設定公司電子郵件存取權](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Microsoft Intune 中的 Wi-Fi 連線](wi-fi-connections-in-microsoft-intune.md)
-  [Microsoft Intune 中的 VPN 連線](vpn-connections-in-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->


