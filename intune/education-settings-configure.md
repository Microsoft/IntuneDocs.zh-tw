---
title: 設定 Windows 10 的 Intune 教育設定
titleSuffix: Microsoft Intune
description: 了解如何在管理的裝置上使用 Intune 來設定 Windows 10 教育設定。
keywords: ''
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6fa631cfb799fe02aee935f524a4012f381973d8
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2018
---
# <a name="how-to-configure-windows-10-education-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中設定 Windows 10 教育設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

教育設定檔可讓您指定設定 Windows「進行測驗」應用程式的詳細資料，包括帳戶詳細資料和測驗 URL。 當您設定此項目時，「進行測驗」應用程式會以您指定的測驗開啟，且裝置將無法執行其他應用程式，直到測驗完成為止。

如需進行測驗應用程式的詳細資料，請參閱[在 Windows 10 中進行測驗](https://docs.microsoft.com/education/windows/take-tests-in-windows-10)。

## <a name="create-a-device-profile-containing-education-profile-settings"></a>建立包含教育設定檔設定的裝置設定檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [裝置設定]。
2. 在 [裝置設定] 窗格的 [管理] 區段下，選擇 [設定檔]。
3. 在 [設定檔] 窗格中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 窗格上，輸入裝置限制設定檔的 [名稱] 和 [描述]。
5. 從 [平台] 下拉式清單中，選取 [Windows 10 及更新版本]。
6. 從 [設定檔類型] 下拉式清單中，選擇 [教育設定檔]。 
7. 選擇 [設定] > [設定]，然後在 [Take a Test] (進行測驗) 窗格中，設定下列各項：
    - **帳戶類型** - 從下拉式欄位選取一個帳戶類型。
    - **帳戶使用者名稱**：輸入用於「進行測驗」之帳戶的使用者名稱。 這可以是網域帳戶、Azure Active Directory (AAD) 帳戶，或是本機電腦帳戶。
    - **評定 URL**：提供您要讓使用者進行之測驗的 URL。 如需詳細資訊，請參閱《進行測驗》文件。
    - **畫面監視**：指定您是否要在使用者進行測驗時監視畫面活動。
    - **文字建議**：允許或封鎖使用者進行測驗時的文字建議功能。
8. 當您完成時，請返回 [建立設定檔] 窗格，然後點擊 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 窗格上。

## <a name="next-steps"></a>接下來的步驟

若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。



