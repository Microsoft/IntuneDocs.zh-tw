---
title: "設定憑證設定檔 | Microsoft Intune"
description: "了解如何建立 Intune 憑證設定檔。"
keywords: 
author: nbigman
ms.author: nbigman
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7b4acce1b1861ca2c2d1432b0258ad1e95e46d2a
ms.openlocfilehash: d4fd80ad7819911b6bf47ccd51e62bebdec24f04


---

# 設定 Intune 憑證設定檔
依[設定 SCEP 的憑證設定檔](configure-certificate-infrastructure-for-scep.md)或[設定 PFX 的憑證基礎結構](configure-certificate-infrastructure-for-pfx.md)所述設定基礎結構和憑證之後，您就可以建立憑證設定檔。 程序如下︰

- **工作 1**：匯出可信任的根 CA 憑證
- **工作 2**：建立可信任的憑證設定檔
- **工作 3**：建立兩種憑證設定檔類型其中之一：
  - SCEP 憑證設定檔
  - .PFX 憑證設定檔

## **工作 1**：匯出可信任的根 CA 憑證
從發行 CA 或信任發行 CA 的任何裝置，將可信任的根憑證授權單位匯出為 **.cer** 檔案。 不要匯出私密金鑰。

當您設定信任的憑證設定檔時，會將此憑證匯入。

## **工作 2**：建立可信任的憑證設定檔
您必須先建立信任的憑證設定檔，才能建立簡單憑證註冊通訊協定 (SCEP) 或 PKCS #12 (.PFX) 憑證設定檔。 每個行動裝置平台都需要一個信任的憑證設定檔和 SCEP 或 .PFX 設定檔。

### 建立信任的憑證設定檔

1.  在 [Intune 管理主控台](https://manage.microsoft.com)中，選擇 [原則] &gt; [新增原則]，然後選擇裝置平台。 您可以為這些裝置建立信任的憑證設定檔：

-  Android 4 及更新版本

-  Android for Work

-  iOS 7.1 和更新版本

-  Mac OS X 10.9 及更新版本

-  Windows 8.1 及更新版本

-  Windows Phone 8.1 和更新版本


2.  新增 [信任的憑證設定檔] 原則。

    深入了解：[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

3.  輸入必要的資訊，為 Android、iOS、Mac OS X、Windows 8.1 或 Windows Phone 8.1 進行信任的憑證設定檔設定。 
4.  在 [憑證檔案] 設定中，匯入從您的發行 CA 匯出的可信任的根 CA 憑證 (.cer 檔案)。 [目的地存放區] 設定僅適用於執行 Windows 8.1 和更新版本的裝置，且僅當裝置有一個以上的憑證存放區時才適用。
    
4.  選擇 [儲存原則]。

新的原則即會顯示在 [原則] 工作區中。 您現在可加以部署。

> [!NOTE]
>
> Android 和 Android for Work 裝置會顯示協力廠商已安裝受信任憑證的通知。
    

## **工作 3**：建立 SCEP 或 .PFX 憑證設定檔
建立信任的 CA 憑證設定檔之後，請為您想要使用的每個平台建立 SCEP 或 .PFX 憑證設定檔。 當您建立 SCEP 憑證設定檔時，必須為該相同平台指定信任的憑證設定檔。 這會連結兩個憑證設定檔，不過您仍然必須分別部署每個設定檔。

### 建立 SCEP 憑證設定檔

1.  在 [Intune 管理主控台](https://manage.microsoft.com)中，選擇 [原則] &gt; [新增原則]，然後選擇裝置平台。  您可以為這些裝置建立 SCEP 憑證設定檔：

-  Android 4 及更新版本

-  Android for Work

-  iOS 7.1 和更新版本

-  Mac OS X 10.9 及更新版本

-  Windows 8.1 及更新版本

-  Windows Phone 8.1 和更新版本

2.  新增 [SCEP 憑證設定檔] 原則
    
    深入了解：[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

3.  遵循設定檔設定頁面的指示來設定 SCEP 憑證設定檔設定。
    > [!NOTE]
    >
    > 在 **[主體名稱格式]** 下，選取 **[自訂]** 以輸入自訂主體名稱格式 (僅在 iOS 設定檔中)。
    >
    > 自訂格式目前支援的兩個變數為 `Common Name (CN)` 和 `Email (E)`。 您可以結合使用這些變數和靜態字串，建立自訂的主體名稱格式如下︰

    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US

    > 在本範例中，管理員建立的主體名稱格式除了有 `CN` 與 `E` 變數之外，還會使用組織單位、組織、位置、狀態及國家/地區值的字串。 [CertStrToName 函式](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx)列出了支援的字串。

4.  選擇 [儲存原則]。

新的原則即會顯示在 [原則] 工作區中。 您現在可加以部署。

### 建立 .PFX 憑證設定檔

1.  在 [Intune 管理主控台](https://manage.microsoft.com)中，選擇 [原則] &gt; [新增原則]，然後選擇裝置平台。 下列平台支援 .PFX 憑證：
  - Android 4 及更新版本
  - Android for Work
  - Windows 10 及更新版本
  - Windows Phone 10 及更新版本
  - iOS 8.0 及更新版本)    

    
2.  新增 [PFX 憑證設定檔] 原則。 
      深入了解：[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。
3.  輸入原則表單上所要求的資訊。
4.  選擇 [儲存原則]。

新的原則即會顯示在 [原則] 工作區中。 您現在可加以部署。

## 部署憑證設定檔
當您部署憑證設定檔時，來自可信任 CA 憑證設定檔的憑證檔案即安裝在裝置上。 裝置會使用 SCEP 或 .PFX 憑證設定檔建立憑證要求。

憑證設定檔只安裝在執行於您建立設定檔時所使用平台的裝置上。

-   您可以將憑證設定檔部署到使用者集合或裝置集合。

    > [!TIP]
    > 若要在裝置註冊之後快速將憑證發行至裝置，請將憑證設定檔部署到使用者群組，而不是裝置群組。 如果您部署至裝置群組，必須先執行完整的裝置註冊，裝置才會接收原則。

-   雖然您分別部署每個設定檔，還是必須部署可信任的根 CA 與 SCEP 或 .PFX 設定檔。 否則 SCEP 或 .PFX 憑證原則會失敗。

部署憑證設定檔的方式與部署 Intune 的其他原則相同：

1.  在 [原則] 工作區中，選取您要部署的原則，然後選擇 [管理部署]。
2.  在 [管理部署]  對話方塊中：
    -   **若要部署原則**，請選取您要部署原則的一或多個群組，然後選擇 [新增] &gt; [確定]。
    -   **若要關閉對話方塊但不加以部署**，請選擇 [取消]。

當您選取某項已部署的原則時，可以在原則清單下方查看部署的詳細資訊。

### 後續步驟

接著了解如何使用憑證來協助保護電子郵件、Wi-Fi 及 VPN 設定檔。

-  [使用電子郵件設定檔來設定公司電子郵件存取權](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Microsoft Intune 中的 Wi-Fi 連線](wi-fi-connections-in-microsoft-intune.md)
-  [Microsoft Intune 中的 VPN 連線](vpn-connections-in-microsoft-intune.md)



<!--HONumber=Oct16_HO2-->


