---
title: Intune 傳送至 Apple 的資料
titleSuffix: Microsoft Intune
description: Intune 傳送至 Apple 的資料清單。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b204a956-18ec-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bbd0f0cafdf6de6b067e1350ce4c61e0980660d2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722510"
---
# <a name="data-intune-sends-to-apple"></a>Intune 傳送至 Apple 的資料

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

在裝置上啟用下列任何 Apple 服務時，Microsoft Intune 會建立與 Apple 的連線並與 Apple 共用使用者和裝置資訊： 

- [Apple 裝置註冊方案 (DEP)](../enrollment/device-enrollment-program-enroll-ios.md)
- [Apple MDM Push Certificate (APNS)](../enrollment/apple-mdm-push-certificate-get.md)
- [Apple School Manager (ASM)](https://docs.microsoft.com/schooldatasync/apple-school-manager-integration-with-intune-for-education-and-school-data-sync)
- [Apple 大量採購方案 (VPP)](../apps/vpp-apps-ios.md)

您必須先為每個 Apple 服務建立 Apple 帳戶，Microsoft Intune 才能建立連線。

下表列出 Microsoft Intune 從裝置傳送給已啟用 Apple 服務的資料。 

| Service | 傳送至 Apple 的資料 | 用途 |
|---|---| ---|
| [APNS](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 權杖, PushMagic | 如果伺服器接受裝置，裝置會提供其推播通知裝置權杖給伺服器。 伺服器應該使用這個權杖來傳送推播訊息至裝置。 此簽入訊息也包含 PushMagic 字串。 伺服器必須記住這個字串，並將它包含在它傳送至裝置的任何推播訊息中。 |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 伺服器權杖 | 用來向 Apple 服務進行驗證的推播通知裝置權杖。 |
| ASM/DEP | server_name | MDM 伺服器的可識別名稱。 |
| ASM/DEP | server_uuid | 由系統產生的伺服器識別碼。 |
| ASM/DEP | admin_id | 產生目前正在使用的權杖之人員的 Apple 識別碼。 |
| ASM/DEP | org_name | 組織的名稱。 |
| ASM/DEP | org_email | 組織的電子郵件地址。 |
| ASM/DEP | org_phone | 組織的電話。 |
| ASM/DEP | org_address | 組織的地址。 |
| ASM/DEP | org_id | DEP 客戶識別碼。 此索引鍵僅適用於通訊協定第 3 版和更新版本。 |
| ASM/DEP | serial_number | 裝置的序號 (字串)。 |
| ASM/DEP | 模型 | 模型名稱 (字串)。 |
| ASM/DEP | 描述 | 裝置的描述 (字串)。 |
| ASM/DEP | asset_tag | 裝置的資產標籤 (字串)。 |
| ASM/DEP | profile_status | 設定檔安裝的狀態。 可能的值：**空白**、**已指派**、**已推送**或**已移除**。 |
| ASM/DEP | profile_uuid | 指派之設定檔的唯一識別碼。 |
| ASM/DEP | device_assigned_by | 指派裝置之人員的電子郵件。 |
| ASM/DEP | os | 裝置作業系統：iOS、OSX 或 tvOS。 此索引鍵在 X-Server 通訊協定第 2 版和更新版本中有效。 |
| ASM/DEP | device_family | 裝置的 Apple 產品系列：iPad、iPhone、iPod、Mac 或 AppleTV。 此索引鍵在 X-Server 通訊協定第 2 版和更新版本中有效。 |
| ASM/DEP | profile_name | 字串。 人類看得懂的設定檔名稱。 |
| ASM/DEP | support_phone_number | 選擇性。 字串。 組織的支援電話號碼。 |
| ASM/DEP | support_email_address | 選擇性。 字串。 組織的支援電子郵件地址。 此索引鍵在 X-Server 通訊協定第 2 版和更新版本中有效。 |
| ASM/DEP | department | 選擇性。 字串。 使用者定義的部門或位置名稱。 |
| ASM/DEP | 裝置 | 包含裝置序號的字串陣列。 (可能是空的。) |
| VPP | Intune 使用者識別碼 GUID | Intune 所產生的 GUID。 |
| VPP | 受控的 AppleId UPN | 設定與 Apple 的 VPP 權杖連線時，由系統管理員所指定的 AppleID。 |
| VPP | 序號 | 受控裝置的序號。 |

若要停止與 Apple 服務使用搭配 Microsoft Intune 並刪除資料，您必須同時停用 Microsoft Intune 的 Apple 權杖並刪除您的 Apple 帳戶。 關於如何執行帳戶管理請參閱 Apple 帳戶。


