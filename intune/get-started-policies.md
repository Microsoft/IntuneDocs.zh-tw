---
title: "開始使用原則"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 232ec25c34df5e71f70737ca5f0f8a2ef12a05f0
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2017
---
# <a name="getting-started-with-policies"></a>開始使用原則

開始使用 Intune 的其中一個主要目標是註冊裝置，以確定它們符合公司原則。 合規性原則不只可以協助您管理特殊裝置類型，例如公司擁有的 Kiosk，也能管理個人 (攜帶您自己) 的裝置、平板電腦和無使用者裝置。

![具有極少資料的合規性儀表板](/intune/media/generic-compliance-dashboard.png)

合規性原則提供行動裝置的下列管理功能：

* 管理每個使用者註冊的裝置數目
* 管理裝置設定 (如裝置層級加密、密碼長度、相機使用方式)
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
2. 使用 [搜尋資源]，搜尋 **Intune**。
3. 選取 [裝置合規性]。
4. 在 [裝置合規性] 刀鋒視窗中，選取 [原則]。
5. 選取 [建立原則]，然後填入詳細資訊，例如 [名稱] 和 [描述]。 選擇 [iOS] 作為 [平台]。
6. 在 [設定] 中，選取 [系統安全性]，然後將 [需要密碼才可解除鎖定行動裝置] 切換至 [需要]。 您可以也設定其他規則，例如 [密碼長度下限]、[必要的密碼類型]和 [密碼中的非英數字元數目]。 設定完成您的原則之後，選取 [確定]。
7. 返回 [建立原則] 刀鋒視窗，然後選取 [建立]。
8. 建立原則之後，選取 [指派] 將它指派給您的測試群組。 選取您的測試群組 - 群組中應該有您的測試使用者 - 然後按一下 [儲存] 將原則指派給該群組。
9. 等待幾分鐘的時間，您的已註冊裝置應該會提示您需要更新密碼，以維持符合公司原則。 您也可以在 **iOS 公司入口網站應用程式**手動檢查這點，方法是依序點選裝置名稱和 [同步] 按鈕。
