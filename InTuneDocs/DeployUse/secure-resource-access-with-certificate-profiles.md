---
# required metadata

title: 透過 Microsoft Intune 利用憑證設定檔存取公司資源 | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 中的憑證設定檔來保護資源存取
當您能夠透過 VPN、Wi-Fi 或電子郵件設定檔來存取公司資源時，您就可以選擇使用每部使用者裝置上安裝的憑證來保護該存取權。 它的運作方式如下：

1. 確定您已備妥正確的憑證基礎結構，如[設定憑證基礎結構](configure-certificate-infrastructure.md)中所述

2. 在每個裝置上安裝根憑證 (或中繼 CA 憑證)，讓裝置辨識憑證授權單位的合法性。 方法是建立和部署 信任的憑證設定檔。 當您部署這個設定檔時，您使用 Intune 管理的裝置就會要求並接收根憑證。 每個平台必須分別建立各自的設定檔。 信任的憑證設定檔適用於這些平台 ︰
 -  iOS 7.1 和更新版本
 -  Mac OS X 10.9 及更新版本
 -  Android 4.0 及更新版本
 -  Windows 8.1 及更新版本
 -  Windows Phone 8.1 和更新版本

3. 讓每個裝置要求一個要用於驗證電子郵件、VPN 和 Wi-Fi 存取的憑證，如[設定 Intune 憑證設定檔](configure-intune-certificate-profiles.md)中所述。 您可以針對這些平台上的裝置，建立和部署 PKCS #12 (.PFX) 憑證設定檔或 SCEP 憑證設定檔︰
 
-  Android 4.0 及更新版本
-  iOS 7.1 和更新版本
-  Windows 10 (桌面版和行動裝置版) 和更新版本 

將 SCEP 憑證設定檔用於：
-   Mac OS X 10.9 及更新版本
-   Windows Phone 8.1 和更新版本

每個平台必須分別建立各自的設定檔。 設定檔建立後，請將其與已建立之 受信任的根憑證設定檔 相關聯。

> [!NOTE]           
> -    如果沒有企業憑證授權單位，就必須建立一個。 
>- 如果您決定 (根據裝置平台) 使用簡單憑證註冊通訊協定 (SCEP) 設定檔，您也需要設定網路裝置註冊服務 (NDES) 伺服器。
>-  無論計劃使用 SCEP 或 .PFX 設定檔，您都必須下載及設定 Microsoft Intune Certificate Connector。
> [設定憑證基礎結構](configure-certificate-infrastructure.md)主題中說明所有這些項目的設定。

### 後續步驟
- [設定憑證基礎結構](configure-certificate-infrastructure.md)
- [設定 Intune 憑證設定檔](configure-intune-certificate-profiles.md)



<!--HONumber=May16_HO2-->


