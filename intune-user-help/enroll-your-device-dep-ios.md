---
title: 在管理中註冊組織提供的 iOS 裝置。 | Microsoft Docs
description: 說明如何在 Intune 中註冊組織所購買和提供的 iOS 裝置
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: f4e7d87e-56d1-43e4-8e88-2f62cf0999e2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 6c1b6417489d1443596113a18476b9cbc8f3832e
ms.sourcegitcommit: 8cc3eca2bce847b0c2b40d8531698e21df848878
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75951464"
---
# <a name="enroll-your-organization-provided-ios-device-in-management"></a>在管理中註冊組織提供的 iOS 裝置

了解如何讓您的新 iOS 裝置在 Intune 中受控。  

通常公司或學校提供的 iOS 裝置會在您收到之前預先設定好。 在您開啟裝置並於第一次登入之後，您的組織會將這些預先設定的設定傳送到您的裝置。 在裝置完成設定之後，您便獲得公司或學校資源的存取權。  

若要開始設定，請開啟裝置電源，並使用公司或學校認證登入。 本文的其餘部分描述您在逐步執行設定助理時將看到的步驟和畫面。

## <a name="what-is-apple-dep"></a>什麼是 Apple DEP？

您的組織可能已透過稱為「Apple 裝置註冊計劃」  (DEP) 的某項服務來購買其裝置。 Apple DEP 可讓組織購買大量 iOS 或 macOS 裝置。 接著，組織可以在其慣用的行動裝置管理提供者 (例如 Intune) 內設定和管理這些裝置。 如果您是系統管理員，而且想要取得 Apple DEP 的詳細資訊，請參閱[使用 Apple 的裝置註冊計劃來自動註冊 iOS 裝置](/intune/enrollment/device-enrollment-program-enroll-ios)。

## <a name="set-up-your-ios-device"></a>設定您的 iOS 裝置

如果您要使用自己的 iOS 裝置，而不是組織提供的裝置，請遵循[個人和自備裝置](enroll-your-device-in-intune-ios.md)的步驟。  

1. 開啟 iOS 裝置。
2. 選取 [語言]  後，將裝置連上 Wi-Fi。
3. 在 [設定 iOS 裝置]  畫面上，選擇 [設定為新裝置]  。  
4. 連接到 Wi-Fi 後，即會出現 [設定]  畫面。 它會顯示： **[您的公司] 將會自動設定裝置。**

   **設定可讓 [您的公司] 無線管理此裝置。系統管理員可協助您設定電子郵件和網路帳戶、安裝和設定應用程式，以及遠端管理設定。系統管理員可以停用功能、安裝和移除應用程式、監視和限制您的網際網路流量，以及從遠端清除此裝置。**

   **設定提供者：[您的公司] 的 iOS 小組 [位址]**

5. 使用 Apple 識別碼登入。 登入可讓您安裝公司入口網站應用程式，並安裝管理設定檔，讓您的公司將其資源 (如電子郵件和應用程式) 的存取權授與您。
6. 同意**條款和條件**並決定是否將診斷資訊傳送至 Apple。
7. 完成註冊後，裝置可能會提示您執行更多動作。 其中一些步驟可能會輸入您的密碼來進行電子郵件存取，或設定密碼。

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。
