---
title: 開始使用 Microsoft Intune
titleSuffix: ''
description: 逐步進行一系列的簡短實際操作快速入門，以了解 Intune。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 11/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 261d15a2731ef6b388eba0f0c6d5cd025e8c3509
ms.sourcegitcommit: d8edd1c3d24123762dd6d14776836df4ff2a31dd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2018
ms.locfileid: "51576714"
---
# <a name="what-can-intune-do-for-my-company"></a>Intune 對我的公司有何作用？
Microsoft Intune 是雲端式企業行動管理 (EMM) 服務，可協助提高您員工的生產力，同時保護公司資料。

使用 Intune，您可以︰

- 管理您的工作人員用來存取公司資料的行動裝置。
- 管理您的工作人員使用的行動應用程式。
- 藉由協助控制您的工作人員存取並共用公司資訊的方式，保護您的公司資訊。
- 確保裝置和應用程式都符合公司安全性需求。

## <a name="common-business-problems-that-intune-helps-solve"></a>Intune 協助解決的常見商務問題

* [保護內部部署電子郵件和資料，以透過行動裝置存取](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [保護 Office 365 電子郵件和資料，以透過行動裝置安全存取](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [向工作人員核發公司擁有的電話](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [將「攜帶您自己的裝置」(BYOD) 或個人裝置計劃提供給所有員工](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [讓您的員工從未受管理的公用 kiosk 中安全存取 Office 365](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [將有使用限制的共用平板電腦核發給工作人員](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)

## <a name="quickstarts"></a>快速入門

我們了解開始管理行動裝置可能十分困難，因為您必須代表您的公司進行許多不同決策。 下列快速入門會在最短時間內，協助您開始使用 Intune，並完成一些常見的工作。

您可以使用頁面左側的目錄，遵循想要的**快速入門**順序。

- [免費試用 Intune](free-trial-sign-up.md) - 建立免費訂用帳戶，以在測試環境中試用 Intune。    
- [建立使用者](quickstart-create-user.md) - 將使用者新增至 Intune，以允許他們存取行動裝置上的公司資源。
- [建立群組](quickstart-create-group.md) - 將使用者組織成群組，以更輕鬆地管理他們可存取的原則和應用程式。
- [設定自動註冊](quickstart-setup-auto-enrollment.md) - 設定 Microsoft Intune 在特定使用者登入 Windows 10 裝置時，自動註冊裝置。
- [註冊您的裝置](quickstart-enroll-windows-device.md) - 扮演 Intune 使用者角色並在 Microsoft Intune 中註冊您的裝置。 然後，返回 Intune 並確認已註冊的裝置。
- [建立裝置合規性政策](quickstart-set-password-length-android.md) - 建立裝置合規性政策，並將群組指派給政策。
- [傳送通知到不符合規範的裝置](quickstart-send-notification.md) - 藉由建立並指派合規性政策，將電子郵件通知傳送給您員工中具有不符合規範裝置的成員。
- [新增並指派應用程式](quickstart-add-assign-app.md) - 新增用戶端應用程式，並將其指派給您公司的員工。
- [建立並指派應用程式防護原則](quickstart-create-assign-app-policy.md) - 建立應用程式防護原則，並將其指派給終端使用者裝置上的用戶端應用程式。
- [建立並指派自訂角色](quickstart-create-custom-role.md) - 建立並指派具備安全性作業部門特定權限的自訂角色。 
- [建立適用於 iOS 的電子郵件裝置設定檔](quickstart-email-profile.md)：建立適用於 iOS 裝置的電子郵件裝置設定檔。

## <a name="prerequisites"></a>必要條件

開始之前，您必須啟用 Intune 系統管理員和租用戶帳戶。 建立免費訂用帳戶，以在測試環境中[免費試用 Intune](free-trial-sign-up.md)。 目前的訂閱者也可以在您的即時租用戶中完成這些活動。 這些入門文章假設您正在使用測試裝置。

您也需要確定您是組織的全域系統管理員，才能完成所有工作。

## <a name="intune-architecture"></a>Intune 架構

Intune 是管理行動裝置和應用程式的 Enterprise Mobility + Security (EMS) 元件。 它會與 Azure Active Directory (Azure AD) 這類其他 EMS 元件緊密整合以進行身分識別和存取控制，以及與 Azure 資訊保護緊密整合以進行資料保護。 將它與 Office 365 搭配使用時，您可以讓您的工作人員在所有裝置上都具有生產力，同時持續保護您的組織資訊。

![Microsoft Intune 的高階架構圖](/intune/media/intunearchitecture.svg)

## <a name="next-steps"></a>接下來的步驟

[開始使用 Azure](get-started-azure.md) - 了解 Azure 入口網站的結構以及如何變更您看到的頁面。

## <a name="learn-more"></a>深入了解

* [什麼是 Intune？](introduction-intune.md)
* [什麼是 Azure 入口網站？](what-is-intune.md)
* [裝置與應用程式生命週期](introduction-device-app-lifecycles.md)