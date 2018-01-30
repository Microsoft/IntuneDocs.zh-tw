---
title: "為受管理的 Android 裝置新增應用程式設定原則 | Microsoft Docs"
titlesuffix: Azure portal
description: "了解如何使用應用程式設定原則在 Android for Work 應用程式執行時，將設定資料提供給該應用程式。"
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4fbf1466b02da66e5c7d115d60aa43912322ebeb
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>為受管理的 Android 裝置新增應用程式設定原則

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

在 Microsoft Intune 中使用應用程式設定原則，以提供使用者執行 Android for Work 應用程式時的設定。 您不會直接將這些原則部署給使用者與裝置。 而是將原則與應用程式關聯，然後再指派應用程式。 每當應用程式檢查是否有原則設定時 (通常是第一次執行時)，便會使用這些原則設定。

> [!Note]  
> 並非每個應用程式都支援應用程式設定。 請連絡應用程式開發人員，以了解他們建置的應用程式是否支援應用程式設定原則。

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  +  [Intune]。
3. 選擇 [Mobile Apps] 工作負載。
4. 選擇 [管理] 群組中的 [應用程式設定原則]，然後選擇 [新增]。
5. 使用下列詳細資料：
    - **名稱**  
      將在 Azure 入口網站中顯示的設定檔名稱。
    - **描述**  
      將在 Azure 入口網站中顯示的設定檔描述。
    - **裝置註冊類型**  
      選擇 [受管理裝置]。
6. 為 [平台] 選取 [Android]。
7. 選取 [相關聯的應用程式] 來選擇您要定義應用程式設定原則的應用程式。 從 Android for Work 應用程式清單中選取您已經使用 Intune 核准並同步處理的應用程式。
8. 選取 [組態設定]。 您可以透過下列方式設定組態：
    - [設定設計工具](#Use-the-configuration-designer)
    - [JSON 編輯器](#Enter-the-JSON-editor)
9. 選擇 [確定]，然後選擇 [新增]。

## <a name="use-the-configuration-designer"></a>使用設定設計工具

您可以在 Intune 中已註冊或未註冊的裝置上，針對應用程式使用設定設計工具。 設計工具可讓您設定特定的設定金鑰和值。 您也必須指定每個值的資料類型。

對於設定中的每個金鑰和值，請設定：

  - **設定金鑰**  
     唯一識別特定設定組態的金鑰。
  - **實值型別**  
    設定值的資料類型。 類型包括整數、實數、字串或布林值。
  - **設定值**  
    設定的值。 

## <a name="enter-the-json-editor"></a>進入 JSON 編輯器

某些應用程式 (例如套件組合類型) 上的組態設定無法使用設定設計工具來設定。 您需要使用 JSON 編輯器來編輯那些值。 安裝應用程式時，會自動將設定值提供給應用程式。

1. 對於 [組態設定格式]，請選取 [進入 JSON 編輯器]。
2. 您可以在編輯器中定義組態設定的 JSON 值。 您可以選擇 [下載 JSON 範本] 來下載之後可以設定的範例檔案。
3. 選擇 [確定]，然後選擇 [新增]。

已建立此原則，並顯示在 [原則清單] 刀鋒視窗上。

當指派的應用程式在裝置上執行時，會依照您在應用程式設定原則中的設定執行。

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>預先設定應用程式的權限授與狀態

您也可以預先設定應用程式的權限，以存取 Android 裝置功能。 根據預設，需要裝置權限 (例如存取位置或裝置相機) 的 Android 應用程式會提示使用者接受或拒絕授與權限。 例如，若應用程式會使用裝置的麥克風，則系統會提示使用者授與應用程式使用麥克風的權限。

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  +  [Intune]。
3. 選擇 [Mobile Apps]。 在 [管理] 下方，選擇 [應用程式設定原則]，然後選擇 [新增]。
4. 使用下列詳細資料：
    - **名稱**。 將在 Azure 入口網站中顯示的設定檔名稱。
    - **描述**。 將在 Azure 入口網站中顯示的設定檔描述。
    - **平台**。 選取 [Android]。
    - **裝置註冊類型**。 已經預先為您選取 [受管理的裝置]。
5. 選取 [相關聯的應用程式] 來選擇您要定義設定原則的應用程式。 從 Android for Work 應用程式清單中選取您已經使用 Intune 核准並同步處理的應用程式。
6. 選取 [權限]，然後選擇 [新增]。
7. 從可用應用程式權限的清單選取權限，然後選擇 [確定]。
8. 為每個權限選取要使用此原則授與的選項：
    - **提示**。 提示使用者接受或拒絕。
    - **自動授與**。 自動核准且不通知使用者。
    - **自動拒絕**。 自動拒絕且不通知使用者。
9. 若要指派應用程式設定原則，請選取應用程式設定原則，選取 [指派]，然後選取 [選取群組]。
10. 選取要指派的使用者群組，然後選擇 [選取]。
11. 選擇 [儲存] 來指派原則。

## <a name="next-steps"></a>接下來的步驟

繼續[指派](apps-deploy.md)及[監視](apps-monitor.md)應用程式。

