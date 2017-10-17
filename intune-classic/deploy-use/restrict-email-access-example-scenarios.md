---
title: "保護電子郵件案例"
description: "一些範例案例，以及透過條件式存取實作它們的方式。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 454eab79-b620-42c9-b8e6-fada6e719fcd
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1ca486ca9eab1ebb8a446b560ff5e265eb4d2712
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2017
---
# <a name="protect-access-to-email-with-microsoft-intune-example-scenarios"></a>使用 Microsoft Intune 限制存取電子郵件：範例案例

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="scenario-1-block-users-from-using-noncompliant-devices-to-access-exchange-online"></a>案例 1：禁止使用者使用不符合規範的裝置存取 Exchange Online
### <a name="scenario-requirements"></a>案例需求
- 對於 **Accounting** Azure Active Directory 安全性群組中的所有使用者，若其裝置不符合您部署的合規性原則，則必須禁止存取 Exchange Online。
- 如果此群組中有任何使用者的裝置不受 Intune 支援，則必須禁止他們在該裝置上存取 Exchange Online。
- 對於 **Finance** Azure Active Directory 安全性群組中的使用者，即使同樣隸屬於 **Accounting** 安全性群組，也必須豁免於此原則。

若要達到此目的，請使用下列設定來設定 Exchange Online 的條件式存取原則：

- 選擇 [啟用條件式存取原則]。

- 選擇您想要允許從應用程式使用新式驗證來存取的平台。
- 對於 Exchange ActiveSync 應用程式，選擇 [在 Microsoft Intune 支援的平台上封鎖不符合規範的裝置] 和 [在 Microsoft Intune 不支援的平台上封鎖其他所有裝置]。
-   在 [目標群組] 區段的 [已選取的安全性群組] 下，選擇 [Accounting] 使用者群組。

-   在 [豁免群組] 區段的 [已選取的安全性群組] 下，選擇 [Finance] 使用者群組。


下列流程在案例中用於決定可存取 Exchange Online 的裝置：

![裝置存取流程](./media/ConditionalAccess8-5.png)

## <a name="scenario-2-all-ios-devices-that-access-exchange-on-premises-must-be-managed-by-intune"></a>案例 2：存取 Exchange 內部部署的所有 iOS 裝置都必須由 Intune 管理
### <a name="scenario-requirements"></a>案例需求
- 應該只允許執行 iOS 的裝置存取 Exchange 內部部署。
- 裝置也必須在 Intune 中註冊，並符合相容性原則規則，才能用於存取 Exchange。

若要達到此目的，請使用下列設定來設定 Exchange 內部部署的下列條件式存取原則：

-   選擇 [封鎖不符合規範或未向 Microsoft Intune 註冊之裝置的電子郵件應用程式存取 Exchange 內部部署] 選項。 選擇此選項會啟用條件式存取原則，要求所有裝置必須在 Microsoft Intune 中註冊且符合相容性原則規則，才能存取 Exchange。

-   在進階 Exchange Active Sync 設定中，請建立：

  -   允許執行 iOS 之裝置存取 Exchange 的平台例外。   

  -   預設規則，指定當平台例外規則未涵蓋裝置時，應該禁止此裝置存取 Exchange。 此規則可確保不是執行 iOS 的裝置無法存取 Exchange。

您可以使用下列流程決定可以存取 Exchange 的裝置：

![裝置存取流程](./media/ConditionalAccess8-3.png)

## <a name="scenario-3-no-android-devices-can-access-exchange-on-premises"></a>案例 3：沒有任何 Android 裝置能夠存取 Exchange 內部部署
### <a name="scenario-requirements"></a>案例需求
- 應該禁止所有 Android 裝置存取 Exchange。
- 只要其他所有支援的裝置由 Intune 管理，就可存取 Exchange。

若要達到此目的，請使用下列設定來設定 Exchange 內部部署的條件式存取原則：

-   選擇 [封鎖不符合規範或未向 Microsoft Intune 註冊之裝置的電子郵件應用程式存取 Exchange 內部部署] 選項。 選擇此選項會要求任何裝置都必須在 Intune 中註冊，且符合合規性原則規則。

- 在進階 Exchange Active Sync 設定中，請建立：
  -   封鎖執行 Android 之裝置存取 Exchange 的平台例外。 此規則可確保 Android 裝置無法用來存取 Exchange。

  -   預設規則，指定當其他規則未涵蓋裝置時，應該允許此裝置存取 Exchange。 此預設規則可確保執行 Android 以外平台，但 Microsoft Intune 支援的裝置，可以用來存取 Exchange。 不過，這些裝置必須在 Intune 中註冊並符合合規性原則規則。

您可以使用下列流程決定可以存取 Exchange 的裝置：

![裝置存取流程](./media/ConditionalAccess8-4.png)
