---
title: "使用 Android for Work 適用的 Intune 應用程式設定原則"
titleSuffix: Intune on Azure
description: "了解如何使用應用程式設定原則在 Android for Work 應用程式執行時，將設定資料提供給該應用程式。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f9ea697cafa0f277c176e55443250d32ca378dbb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-android-for-work"></a>如何使用 Android for Work 適用的 Microsoft Intune 應用程式設定原則

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

您可以在 Microsoft Intune 中使用應用程式設定原則，來提供使用者執行 Android for Work 應用程式時可能可以使用的設定。 並非所有應用程式都支援應用程式設定。 請聯絡應用程式開發人員，以了解他們建置的應用程式是否支援應用程式設定原則。

應用程式設定原則可協助您在使用者執行應用程式之前，先為他們預先設定可用的應用程式設定。 某些 Android 應用程式支援受管理設定選項，您可以使用[設定設計工具](#use-configuration-designer)在 Intune 主控台中設定那些選項。 某些應用程式 (例如套件組合類型) 上的組態設定無法使用設定設計工具來設定。  您將需要使用 [JSON 編輯器](#use-json-editor)來編輯那些值。   安裝應用程式時，會自動將設定值提供給應用程式。

您不會直接將這些原則部署給使用者與裝置。 而是將原則與應用程式關聯，然後再指派應用程式。 每當應用程式檢查是否有原則設定時 (通常是第一次執行時)，便會使用這些原則設定。

## <a name="use-configuration-designer"></a>使用設定設計工具

1. 在 Intune 入口網站中，選擇 [行動應用程式]。 在 [管理] 下方，選擇 [應用程式設定原則]，然後按一下 [新增]。
2. 使用下列詳細資料：
    - **名稱** - 將在 Intune 主控台中顯示之設定檔的名稱
    - **描述** - 將在 Intune 主控台中顯示之設定檔的描述
    - **平台** - 選取 [Android]
    - **裝置註冊類型** - 已經預先為您選取 [已註冊到 Intune]。
3. 選取 [相關聯的應用程式] 來選擇您要定義設定原則的應用程式。  從 Android for Work 應用程式清單中選取您已經使用 Intune 核准並同步處理的應用程式
4. 選取 [組態設定]。
5. 對於 [組態設定格式]，選取 [使用設定設計工具]。
6. 選擇 [新增]。 就會顯示可用組態設定的清單。 此清單包括：
    - **設定金鑰** - 設定的名稱。
    - **值的類型** - 可以設定的值，例如 [布林值] 或 [字串]。
    - **描述** - 組態設定的描述。
7. 選取您要使用此設定檔設定之設定的核取方塊，然後按一下 [確定]。
8. 您選取之設定的清單就會顯示並顯示可用的**設定值**。 指定每項設定的值，然後按一下 [確定]。

## <a name="use-json-editor"></a>使用 JSON 編輯器

1. 在 Intune 入口網站中，選擇 [行動應用程式]。 在 [管理] 下方，選擇 [應用程式設定原則]，然後按一下 [新增]。
2. 使用下列詳細資料：
    - **名稱** - 將在 Intune 主控台中顯示之設定檔的名稱
    - **描述** - 將在 Intune 主控台中顯示之設定檔的描述
    - **平台** - 選取 [Android]
    - **裝置註冊類型** - 已經預先為您選取 [已註冊到 Intune]。
3. 選取 [相關聯的應用程式] 來選擇您要定義設定原則的應用程式。  從 Android for Work 應用程式清單中選取您已經使用 Intune 核准並同步處理的應用程式。
5. 選取 [組態設定]。
6. 對於 [組態設定格式]，請選取 [進入 JSON 編輯器]。
7. 您可以在編輯器中定義組態設定的 JSON 值。 您可以選擇 [下載 JSON 範本] 來下載之後可以設定的範例檔案。
8. 完成時，請選擇 [確定]，然後按一下 [新增]。

如此即可建立原則，並顯示在原則清單刀鋒視窗上。

接著一如往常般地繼續[指派](apps-deploy.md)及[監視](apps-monitor.md)應用程式。

當指派的應用程式在裝置上執行時，會依照您在應用程式組態原則中的設定執行。

## <a name="preconfigure-permissions-grant-state-for-apps"></a>預先設定應用程式的權限授與狀態

您也可以預先設定應用程式的權限，以存取 Android 裝置功能。 根據預設，需要裝置權限 (例如存取位置或裝置相機) 的 Android 應用程式會提示使用者接受或拒絕授與權限。 例如，若應用程式會使用裝置的麥克風，則系統會提示使用者授與應用程式使用麥克風的權限。

1. 在 Intune 入口網站中，選擇 [行動應用程式]。 在 [管理] 下方，選擇 [應用程式設定原則]，然後按一下 [新增]。
2. 使用下列詳細資料：
    - **名稱** - 將在 Intune 主控台中顯示之設定檔的名稱
    - **描述** - 將在 Intune 主控台中顯示之設定檔的描述
    - **平台** - 選取 [Android]
    - **裝置註冊類型** - 已經預先為您選取 [已註冊到 Intune]。
3. 選取 [相關聯的應用程式] 來選擇您要定義設定原則的應用程式。  從 Android for Work 應用程式清單中選取您已經使用 Intune 核准並同步處理的應用程式。
5. 選取 [權限]，然後選擇 [新增]。
6. 從可用應用程式權限的清單選取權限，然後選擇 [確定]。
7. 為每個權限選取要使用此原則授與的選項：
    - **提示** - 提示使用者接受或拒絕。
    - **自動授與** - 自動核准且不通知使用者。
    - **自動拒絕** - 自動拒絕且不通知使用者。
8. 若要指派應用程式設定原則，請選取應用程式設定原則，選取 [指派]，然後選取 [選取群組]。
9. 選取要指派的使用者群組，然後選擇 [選取]。
10. 選擇 [儲存] 來指派原則。
