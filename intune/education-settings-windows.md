---
title: Microsoft Intune 中的 Windows 10 教育設定 - Azure | Microsoft Docs
description: 查看適用於 Windows 10 裝置的所有教育設定清單。 在 Intune 中搭配「進行測驗」應用程式在裝置組態設定檔中使用這些設定、選擇使用者或學生的登入方式、在測驗期間監視螢幕等等。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 206bc3276f3c175fe61852f235c722b835ad60b4
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57564851"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>使用 Intune 在 Windows 10 裝置上設定「進行測驗」應用程式

本文說明您可以在執行 Windows 10 和更新版本的裝置上設定的所有 Microsoft Intune 教育「進行測驗」應用程式設定。 使用此應用程式時，學生可以登入裝置並接受測驗。

這些設定會新增至裝置組態設定檔中，然後使用 Microsoft Intune 指派或部署到您的裝置。

[Intune 中的「進行測驗」應用程式](education-settings-configure.md)提供此功能的詳細資訊。

## <a name="before-you-begin"></a>開始之前

[建立裝置組態設定檔](education-settings-configure.md#create-a-device-profile)。

## <a name="take-a-test-settings"></a>「進行測驗」設定

- **帳戶類型**： 選擇使用者如何登入至測試。 選項包括：
  - Azure AD 帳戶
  - 網域帳戶
  - 本機帳戶
- **帳戶使用者名稱**：輸入用於「進行測驗」應用程式之帳戶的使用者名稱。 您可以使用下列格式來輸入帳戶：
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **評定 URL**：輸入您要讓使用者進行之測驗的 URL。 如需取得此 URL 的詳細資訊，請參閱[「進行測驗」文件](https://docs.microsoft.com/education/windows/take-tests-in-windows-10) \(部分機器翻譯\)。
- **螢幕監視**：選擇 [允許] 以在使用者接受測驗時監視螢幕活動。 [未設定] 會讓您無法在測驗期間監視螢幕。
- **文字建議**：選擇 [允許] 來讓受測者看見文字建議。 [未設定] 會在使用者接受測驗時封鎖文字建議。

## <a name="next-steps"></a>後續步驟

雖然設定檔已建立，但它可能還不會執行任何動作。 請務必[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
