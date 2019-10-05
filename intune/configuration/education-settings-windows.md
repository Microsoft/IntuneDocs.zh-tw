---
title: Microsoft Intune 中的 Windows 10 教育設定 - Azure | Microsoft Docs
description: 查看適用於 Windows 10 裝置的所有教育設定清單。 在 Intune 中搭配「進行測驗」應用程式在裝置組態設定檔中使用這些設定、選擇使用者或學生的登入方式、在測驗期間監視螢幕等等。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: kakyker
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 07d3488d509339fc48eb8449b12725b757775eb5
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734683"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>使用 Intune 在 Windows 10 裝置上設定「進行測驗」應用程式

「進行測試」應用程式可讓您在教室的 Windows 10 裝置上安全地管理線上測試。 若要設定「進行測試」應用程式，您必須在 Intune 中建立裝置設定檔，並設定安全評估設定。 本文說明您將會找到的「進行測試」應用程式的設定。 

設定設定檔之後，請將它指派給您的學生並加以部署。 

[Intune 中的「進行測驗」應用程式](education-settings-configure.md)提供此功能的詳細資訊。

## <a name="before-you-begin"></a>開始之前

[建立裝置組態設定檔](education-settings-configure.md#create-a-device-profile)。

## <a name="take-a-test-settings"></a>「進行測驗」設定
建立裝置設定檔之後，請移至 [**配置檔案類型**]，然後選取 **[安全評量（教育）** ]。 您會發現下列的「進行測試」應用程式設定。 


- **帳戶類型**：選擇使用者登入測驗的方式。 選項包括：
  - Azure AD 帳戶
  - 網域帳戶
  - 本機帳戶
  - 本機來賓帳戶：僅適用于執行 Windows 10 1903 版和更新版本的裝置。    
- **帳戶使用者名稱**：輸入用於「進行測驗」應用程式之帳戶的使用者名稱。 您可以使用下列格式來輸入帳戶：
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **帳戶名稱**：若要設定本機來賓帳戶類型，請輸入與「進行測試」應用程式搭配使用的帳戶名稱。 帳戶名稱會顯示為登入畫面上的磚。 學生可以按一下磚來啟動測試。  
- **評定 URL**：輸入您要讓使用者進行之測驗的 URL。 如需取得此 URL 的詳細資訊，請參閱[「進行測驗」文件](https://docs.microsoft.com/education/windows/take-tests-in-windows-10) \(部分機器翻譯\)。
- **印表機**連線：選擇 [**需要**]，只允許從連線到印表機的裝置存取 [進行測試] 應用程式。 此設定也會讓應用程式的 [列印] 按鈕可用於測試受測者。 [**未設定] 會**允許學生從未連線到印表機的裝置存取應用程式。  
- **螢幕監視**：選擇 [允許]  以在使用者接受測驗時監視螢幕活動。 [未設定]  會讓您無法在測驗期間監視螢幕。
- **文字建議**：選擇 [允許]  ，以便受測者可以看到文字建議。 [未設定]  會在使用者接受測驗時封鎖文字建議。

## <a name="next-steps"></a>後續步驟

請務必[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
