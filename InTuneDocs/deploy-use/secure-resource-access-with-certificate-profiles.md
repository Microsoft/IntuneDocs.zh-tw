---
title: "用於資源存取的憑證設定檔 |Microsoft Docs"
description: "使用每部使用者裝置上安裝的憑證來保護 VPN、Wi-Fi 及電子郵件存取。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 9cf53cb240ba14317fbb680ad4f4c40c8320506d
ms.lasthandoff: 12/10/2016


---

# <a name="secure-resource-access-with-certificate-profiles-in-microsoft-intune"></a>使用 Microsoft Intune 中的憑證設定檔來保護資源存取

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

當您授與使用者透過 VPN、Wi-Fi 或電子郵件設定檔存取公司資源的權限時，您可以使用安裝在每部使用者裝置上的憑證來保護存取的安全。 它的運作方式如下：

1. 確定您已備妥正確的憑證基礎結構，如[設定 SCEP 的憑證基礎結構](configure-certificate-infrastructure-for-scep.md)及[設定 PFX 的憑證基礎結構](configure-certificate-infrastructure-for-pfx.md)中所述。

2. 在每部裝置上安裝根憑證或中繼憑證授權單位 (CA) 憑證，讓裝置可以辨識 CA 的合法性。 若要這樣做，請建立並部署**信任的憑證設定檔**。 當您部署這個設定檔時，您使用 Intune 管理的裝置就會要求並接收根憑證。 每個平台必須分別建立各自的設定檔。 **信任的憑證設定檔**適用於這些平台 ︰
 -  iOS 8.0 和更新版本
 -  Mac OS X 10.9 及更新版本
 -  Android 4.0 及更新版本
 -  Android for Work
 -  Windows 8.1 及更新版本
 -  Windows Phone 8.1 和更新版本

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

3. 建立憑證設定檔，讓每個裝置要求一個用於驗證 VPN、Wi-Fi 和電子郵件存取的憑證，如[設定 Intune 憑證設定檔](configure-intune-certificate-profiles.md)中所述。 您可以針對執行這些平台的裝置，建立並部署 **PKCS #12 (.PFX) 憑證設定檔**或 **SCEP 憑證設定檔**︰

  -  iOS 8.0 和更新版本
  -  Android 4.0 及更新版本
  -  Android for Work
  -  Windows 10 (桌面版和行動裝置版) 和更新版本

  針對執行這些平台的裝置使用 **SCEP 憑證設定檔**：
    -   Mac OS X 10.9 及更新版本
    -   Windows Phone 8.1

您必須為每個平台分別建立設定檔。 當您建立設定檔時，請將設定檔與您已建立之**受信任的根憑證設定檔**建立關聯。

> [!NOTE]           
> - 如果沒有企業憑證授權單位，您必須建立一個。
>- 如果您決定 (根據裝置平台) 使用簡單憑證註冊通訊協定 (SCEP) 設定檔，您也需要設定網路裝置註冊服務 (NDES) 伺服器。
>-  無論計劃使用 SCEP 或 .PFX 設定檔，您都必須下載及設定 Microsoft Intune 憑證連接器。
>-  在[設定 SCEP 的憑證基礎結構](configure-certificate-infrastructure-for-scep.md)或[設定 PFX 的憑證基礎結構](configure-certificate-infrastructure-for-pfx.md)中了解如何設定所有必要的服務。

### <a name="next-steps"></a>後續步驟
- [設定 SCEP 的憑證基礎結構](configure-certificate-infrastructure-for-scep.md)
- [設定 PFX 的憑證基礎結構](configure-certificate-infrastructure-for-pfx.md)
- [設定 Intune 憑證設定檔](configure-intune-certificate-profiles.md)

