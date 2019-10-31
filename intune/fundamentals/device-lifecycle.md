---
title: Microsoft Intune MDM 生命週期概觀
description: 了解 Intune 如何協助您從註冊、設定至淘汰的裝置生命週期中管理裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 816ad4bb5b17f3a480fbf834280c4e9792c394a9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502975"
---
# <a name="overview-of-the-microsoft-intune-mobile-device-management-mdm-lifecycle"></a>Microsoft Intune 行動裝置管理 (MDM) 生命週期的概觀

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

您所管理的所有裝置都有「生命週期」  。 Intune 可協助您管理這個生命週期：從註冊開始 (透過設定和保護)，一直到不再需要裝置時將其淘汰。

![裝置生命週期](./media/device-lifecycle/device-lifecycle.png "Intune 裝置生命週期")

## <a name="enroll"></a>註冊
現今的行動裝置管理 (MDM) 策略可以處理各種行動電話、平板電腦和個人電腦 (iOS、Android、Windows 和 Mac OS X)。 如果您需要管理裝置 (通常是管理公司裝置的情況)，第一個步驟是[設定裝置註冊](../enrollment/device-enrollment.md)。 您也可以向 Intune (MDM) 註冊 Windows 電腦或[安裝 Intune 用戶端軟體](../manage-windows-pcs-with-microsoft-intune.md)，以管理電腦。

## <a name="configure"></a>設定
註冊您的裝置是第一個步驟。 若要充分利用 Intune 提供的選項，並確定您的裝置安全且與公司標準相容，您可以從各種不同的原則中進行選擇。 這可讓您設定受管理裝置操作上的大部分層面。 例如，使用者是否應該擁有內含公司資料之裝置的密碼？ 您可以擁有密碼。 您擁有公司的 Wi-Fi 嗎？ 您可以自動設定它。 以下是可供使用的設定選項類型︰

- [**裝置設定**](../configuration/device-profiles.md)。 這些原則可讓您設定您所管理裝置的特性和功能。 比方說，您可以在 Windows Phone 上要求使用密碼，或在 iPhone 上停用相機。
- [**公司資源存取**](../configuration/device-profiles.md)。 讓使用者在其個人裝置上存取其工作時，這可能會形成挑戰。 例如，您如何確保已正確設定所有需要存取公司電子郵件的裝置？ 您如何確保使用者可以使用 VPN 連線來存取公司網路，而不需要了解複雜的設定？ 透過將您管理的裝置自動設定為可存取常用的公司資源，Intune 有助於減輕此項負擔。
- [**Windows 電腦的管理原則 (使用 Intune 用戶端軟體)** ](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)。 雖然使用 Intune 註冊 Windows 電腦，可提供您最多的裝置管理功能，Intune 會繼續支援使用 Intune 用戶端軟體來管理 Windows 電腦。 如果您需要可使用電腦執行之部分工作的資訊，請從這裡開始。

## <a name="protect"></a>保護
在現代的 IT 世界裡，防止裝置未經授權的存取是您會執行的其中一項最重要工作。 除了裝置生命週期的**設定**步驟中的項目，Intune 提供的這些功能，可協助保護您管理的裝置不受未經授權的存取或惡意攻擊︰
- [**多重要素驗證**](../enrollment/multi-factor-authentication.md)。 在使用者登入中加入了額外一層的驗證，可協助讓裝置更為安全。 許多裝置支援多重要素驗證，其在使用者能夠進行存取之前，要求第二個層級的驗證 (例如通話或簡訊)。
- [**Windows Hello 企業版設定**](../protect/windows-hello.md)。 Windows Hello 企業版是替代的登入方法，可讓使用者使用*手勢* (例如指紋或 Windows Hello) 登入，而不需要密碼。
- [**保護 Windows 電腦的原則 (使用 Intune 用戶端軟體)** ](../policies-to-protect-windows-pcs-in-microsoft-intune.md)。 當您使用 Intune 用戶端軟體來管理 Windows 電腦時，原則可供使用，讓您控制 Endpoint Protection、軟體更新以及您管理之電腦上的 Windows 防火牆設定。

## <a name="retire"></a>淘汰
當裝置遺失或遭竊而必須進行取代，或當使用者移至另一個位置時，通常是[淘汰或抹除](../remote-actions/device-management.md)裝置的時候。 有數種方式可執行此動作，包含重設裝置、從管理中移除裝置，或抹除裝置上的公司資料。

## <a name="next-steps"></a>後續步驟

- 深入了解 [Microsoft Intune 裝置管理](../remote-actions/device-management.md)
