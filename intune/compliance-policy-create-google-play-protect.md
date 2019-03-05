---
title: 使用 Microsoft Intune 來啟用「Google Play 安全防護」合規性
titleSuffix: ''
description: 了解如何為 Android 裝置建立可啟用「Google Play 安全防護」的合規性原則。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E9810BEB-000A-4DFB-B5C7-A22A92082B22
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6c92115b3e5b5c0f13f60b7483905fef2f73c637
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230664"
---
# <a name="how-to-create-a-device-compliance-policy-to-enable-google-play-protect"></a>如何建立可啟用「Google Play 安全防護」的裝置合規性原則

您可以為 Android 平台建立新的合規性原則，以檢查「Google Play 安全防護 (GPP)」合規性。

之後，要求這些設定的合規性原則便能以 Android 使用者或裝置群組為目標。 如果裝置未啟用這些設定，便無法符合規範。

## <a name="create-a-compliance-policy"></a>建立合規性政策

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
2. 在 [管理群組] 中選擇 [裝置合規性]。 
3. 選擇 [原則]，然後選擇 [建立原則]。
4. 輸入原則 [名稱] 和 [描述]。
5. 為 [平台] 選取 [Android]。
6. 選擇 [設定] > [裝置健全狀況]。
7. 設定 [Google Play 安全防護] 設定。
8. 設定 [Google Play Protect] (Google Play 安全防護) 之後，請指定 [系統安全性] 與 [裝置屬性] 設定。 完成後，請選擇 [確定]。

## <a name="configure-the-google-play-protect-settings"></a>設定 [Google Play 安全防護] 設定

 - **已設定 Google Play 服務**  
   需要安裝並啟用「Google Play 服務」應用程式。 「Google Play 服務」可允許安全性更新，而且是 Google 認證裝置上許多安全性功能的基層相依服務。
 - **最新安全性提供者**  
   需要最新安全性提供者，以保護裝置已知的漏洞。
 - **對應用程式進行威脅掃描**  
   需要啟用 Android **驗證應用程式** 功能。
    > [!Note]  
    > 在舊版的 Android 平台上，此功能為合規性設定。 Intune 只能在裝置層級檢查是否已啟用此設定。 在具有 Android 工作設定檔的裝置上，此設定可作為設定原則設定。 如此可讓系統管理員啟用裝置的設定。

    如果您的企業使用 Android 工作設定檔，則您可以在已註冊的裝置上啟用 [對應用程式進行威脅掃描]。 建立裝置設定檔，並要求系統安全性設定。 如需詳細資訊，請參閱 [Microsoft Intune 中的 Android 工作設定檔裝置限制設定](device-restrictions-android-for-work.md)。

 - **SafetyNet 裝置證明**  
   設定必須符合的 SafetyNet 裝置證明完整性層級。 層級包括了 [未設定]、[檢查基本完整性]，以及 [檢查基本完整性與經過認證的裝置]。




## <a name="next-steps"></a>後續步驟

若要深入了解如何使用 Intune 裝置合規性原則，請參閱[開始使用 Intune 裝置合規性原則](device-compliance-get-started.md)。
