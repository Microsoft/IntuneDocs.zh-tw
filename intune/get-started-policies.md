---
title: 在 Microsoft Intune 中開始使用原則 - Azure | Microsoft Docs
description: 建立原則來協助保護公司資料及管理終端使用者用來存取公司資源的裝置。 然後，將原則指派給群組。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d7fa1b596a1800971919cfc0ab3e94d2d16ec328
ms.sourcegitcommit: afda8a0fc0f615e976b18ddddf81d56d7ae3566e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271519"
---
# <a name="get-started-with-creating-policies"></a>從建立原則開始

Intune 原則是註冊裝置並確保其符合您公司原則的絶佳方法。 合規性原則可協助管理特殊裝置類型，例如公司擁有的 Kiosk，以及管理個人 (攜帶您自己) 的裝置、平板電腦和無使用者裝置。

![具有少數資料的相容性儀表板](/intune/media/generic-compliance-dashboard.png)

使用合規性原則可管理行動裝置，包括：

* 管理使用者在 Intune 中註冊的裝置數目
* 管理裝置設定，例如裝置層級加密、密碼長度和相機使用方式
* 提供應用程式、電子郵件設定檔、VPN 設定檔等
* 評估安全性合規性原則的裝置層級準則

為每個平台建立合規性原則，例如 iOS、Android、Windows 等。 在此練習中，請使用 iOS。 下列是 iOS 裝置可用的原則：

* PIN 碼或密碼設定
* 裝置加密
* 已進行 JB 破解的裝置
* 電子郵件設定檔
* 最低 OS 版本
* 最高 OS 版本

## <a name="create-a-policy"></a>建立原則

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置相容性] > [原則] > [建立原則]。
4. 輸入原則的 [名稱] 和 [描述]。 
5. 針對 [平台]，選取 [iOS]。
6. 在 [設定] 中，選取 [系統安全性]，然後將 [需要密碼才可解除鎖定行動裝置] 設定為 [需要]。 

    您也可以設定其他規則，例如： 
    - **密碼長度下限**
    - **必要的密碼類型**
    - **密碼中的非英數字元數**
    
    設定完成您的原則之後，選取 [確定]。
  
7. 回到 [建立原則]，然後選取 [建立]。 此步驟會建立原則，並在 [裝置合規性] > [原則] 中列出您的原則。
8. 選取您的新原則，然後選擇 [指派]。 您可以包含或排除 Azure Active Directory (AD) 安全性群組。
選擇 [選取的群組] 以查看您現有的 Azure AD 安全性群組。 選取要套用這項原則的使用者群組，然後選擇 [儲存] 將原則部署給使用者。

為符合新的公司原則，幾分鐘後，您的已註冊裝置會提示輸入更新的密碼。 您可在 **iOS 版公司入口網站應用程式**中手動檢查更新。 開啟公司入口網站應用程式，選取裝置名稱，然後選取 [同步]。

> [!NOTE]
> 套用至動態裝置群組的新原則最多可能需要八小時才能套用至群組中的所有裝置。

## <a name="next-steps"></a>接下來的步驟

[開始註冊裝置](get-started-enroll.md) - 透過 iOS 裝置的完整註冊體驗，來學習註冊體驗。

## <a name="learn-more"></a>深入了解

* [監視 Intune 裝置合規性原則](compliance-policy-monitor.md)
* [透過 Intune 使用條件式存取原則的常見方式](conditional-access-intune-common-ways-use.md)
