---
title: "開始在 Microsoft Intune 中使用原則"
titlesuffix: 
description: "建立原則來協助保護公司資料及管理終端使用者用來存取公司資源的裝置。"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8af61eb207a8f9b2dc74650627fcab0e4d858904
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="get-started-with-creating-policies"></a>從建立原則開始

開始使用 Intune 時的其中一個主要目標是註冊裝置，以確定它們符合公司原則。 合規性原則不只可以協助您管理特殊裝置類型，例如公司擁有的 Kiosk，也能管理個人 (攜帶您自己) 的裝置、平板電腦和無使用者裝置。

![具有少數資料的相容性儀表板](/intune/media/generic-compliance-dashboard.png)

使用相容性原則管理下列區域的行動裝置：

* 管理每個使用者註冊的裝置數目
* 管理裝置設定 (例如裝置層級加密、密碼長度、相機使用方式)
* 提供應用程式、電子郵件設定檔、VPN 設定檔等。
* 評估安全性合規性原則的裝置層級準則

您要個別建立每個平台的合規性原則。 針對此練習，我們將著重於 iOS。 下列是 iOS 裝置可用的原則：

* PIN 碼或密碼設定
* 裝置加密
* 已進行 JB 破解的裝置
* 電子郵件設定檔
* 最低 OS 版本
* 最高 OS 版本

__如何建立原則？__

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 選取 [裝置合規性]。
4. 在 [裝置相容性] 窗格中，選取 [原則]。
5. 選取 [建立原則]，然後填入詳細資訊，例如 [名稱] 和 [描述]。 
6. 選擇 [iOS] 作為 [平台]。
6. 在 [設定] 中，選取 [系統安全性]，然後將 [需要密碼才可解除鎖定行動裝置] 切換至 [需要]。 您可以也設定其他規則，例如 [密碼長度下限]、[必要的密碼類型]和 [密碼中的非英數字元數目]。 設定完成您的原則之後，選取 [確定]。
7. 返回 [建立原則] 窗格，然後選取 [建立]。
8. 建立原則之後，選取 [指派] 將它指派給您的測試群組。 選取您的測試群組 - 群組中應該有您的測試使用者 - 然後按一下 [儲存] 將原則指派給該群組。
9. 等待幾分鐘的時間，您的已註冊裝置應該會提示您需要更新密碼，以維持符合公司原則。 您也可以在 **iOS 公司入口網站應用程式**手動檢查這點，方法是依序點選裝置名稱和 [同步] 按鈕。

## <a name="next-steps"></a>接下來的步驟

[開始註冊裝置](get-started-enroll.md) - 透過 iOS 裝置的完整註冊體驗，來學習註冊體驗。

## <a name="learn-more"></a>進一步了解

* [監視 Intune 裝置合規性原則](compliance-policy-monitor.md)
* [透過 Intune 使用條件式存取原則的常見方式](conditional-access-intune-common-ways-use.md)
