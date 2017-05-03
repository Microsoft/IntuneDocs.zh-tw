---
title: "設定 Windows 10 的 Intune 教育設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何在您管理的裝置上使用 Intune 來設定 Windows 10 教育設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: d3fdf8884a0b7c035cde89da930ef74172b76873
ms.lasthandoff: 04/19/2017


---

# <a name="how-to-configure-windows-10-education-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中設定 Windows 10 教育設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

教育設定檔可讓您指定設定 Windows「進行測驗」應用程式的詳細資料，包括帳戶詳細資料和測驗 URL。 當您設定此項目時，「進行測驗」應用程式會以您指定的測驗開啟，且裝置將無法執行其他應用程式，直到測驗完成為止。

使用本主題中的資訊，可深入了解設定裝置限制設定檔的相關基本概念，然後可深入閱讀每個平台的主題，以了解裝置專屬內容。

## <a name="create-a-device-profile-containing-education-profile-settings"></a>建立包含教育設定檔設定的裝置設定檔

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置設定]。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
3. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗中，為裝置限制設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取 [Windows 10 及更新版本]。
6. 從 [設定檔類型] 下拉式清單中，選擇 [教育設定檔]。 
7. 選擇 [設定] > [設定]，然後在 [進行測驗] 刀鋒視窗上，設定下列各項：
    - **帳戶使用者名稱**：輸入用於「進行測驗」之帳戶的使用者名稱。 這可以是網域帳戶、Azure Active Directory (AAD) 帳戶，或是本機電腦帳戶。
    - **評定 URL**：提供您要讓使用者進行之測驗的 URL。 如需詳細資訊，請參閱《進行測驗》文件。
    - **畫面監視**：指定您是否要在使用者進行測驗時監視畫面活動。
    - **文字建議**：允許或封鎖使用者進行測驗時的文字建議功能。
8. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。
若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](how-to-assign-device-profiles.md)。




