---
title: 設定 Microsoft Intune
description: 開始使用 Intune 訂用帳戶的需求和必要條件
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7a45160fc0e728b4c53590455a2bd0b5d904ddb1
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504891"
---
# <a name="set-up-intune"></a>設定 Intune

這些設定步驟可協助您啟用行動裝置管理 (MDM)。 必須先管理裝置，您才能讓使用者存取公司資源或管理這些裝置上的設定。

在大部分情況下，需要一些步驟 (例如，設定 Intune 訂用帳戶，以及設定 MDM 授權單位)。 根據您公司的需求，其他步驟 (例如，設定自訂網域，或新增應用程式) 為選擇性。

如果您目前使用 Microsoft System Center Configuration Manager 來管理電腦和伺服器，則可以[透過共同管理雲端連接 Configuration Manager](https://docs.microsoft.com/sccm/comanage/overview)。

>[!TIP]
>凡在符合條件方案中購買至少 150 套 Intune 授權，即可享有「FastTrack Center 服務權益」  。 這項服務讓您和 Microsoft 專家一起整備 Intune 環境。 請參閱[適用於 Enterprise Mobility + Security (EMS) 的 FastTrack Center 權益](https://docs.microsoft.com/enterprise-mobility-security/Solutions/enterprise-mobility-fasttrack-program)。



| 步驟 |                                                                                                                       狀態                                                                                                                       |
|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   1   |                                        [支援的設定](supported-devices-browsers.md) - 開始之前需要知道的資訊。 這包含支援的設定和網路需求。                                         |
|   2   |                                                                 [登入 Intune](account-sign-up.md) - 登入試用訂用帳戶，或建立新的 Intune 訂用帳戶。                                                                  |
|   3   |                [設定網域名稱](custom-domain-name-configure.md) - 設定 DNS 註冊，以連線您公司的網域名稱與 Intune。 連線至 Intune 並使用資源時，這可將熟悉的網域提供給使用者。                |
|   4   |                                   [新增使用者](users-add.md) - 手動新增使用者，或連線 Active Directory 以同步使用者與 Intune。 例如，除非您的裝置是「無使用者」Kiosk 裝置，否則為必要項目。                                    |
|   5   |                                            [指派授權](../licenses-assign.md) - 將使用 Intune 的權限提供給使用者。 每個使用者或無使用者裝置都需要有 Intune 授權才能存取服務。                                             |
|   6   |                                               [新增群組](../groups-add.md) - 使用使用者和裝置群組來簡化管理工作。 群組用來指派應用程式、設定和其他資源。                                                |
|   7   |                                                                        [新增應用程式](../apps/apps-add.md) - 可以將應用程式指派給群組，並自動或選擇性地進行安裝。                                                                         |
|   8   | [設定裝置](../configuration/device-profiles.md) - 設定可管理裝置設定的設定檔。 裝置設定檔可以預先設定電子郵件、VPN、Wi-Fi 和裝置功能的設定。 它們也可以限制裝置，協助保護裝置和資料。 |
|   9   |       [自訂公司入口網站](../apps/company-portal-app.md) - 自訂使用者用來註冊裝置並安裝應用程式的 Intune 公司入口網站。 這些設定會顯示在公司入口網站應用程式和 Intune 公司入口網站中。       |
|  10   |                                [啟用裝置註冊](mdm-authority-set.md) - 設定 MDM 授權單位以及啟用特定平台，以啟用 iOS、Windows、Android 及 Mac 裝置的 Intune 管理。                                 |
|  11   |                                                        [設定應用程式原則](../apps/app-protection-policy.md) - 根據 Microsoft Intune 中的應用程式保護原則提供特定的設定。                                                         |

