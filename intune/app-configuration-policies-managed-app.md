---
title: 在不註冊裝置的情況下受控應用程式的設定原則
titleSuffix: Microsoft Intune
description: 了解如何在不註冊裝置的情況下設定受控應用程式的原則。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69340d8a5bee9dbeb74c0ed0792d53c770f3f3c3
ms.sourcegitcommit: 8c795b041cd39e3896595f64f53ace48be0ec84c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2019
ms.locfileid: "59587445"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>在不註冊裝置的情況下新增受管理應用程式的應用程式設定原則

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

即使在未註冊的裝置上，您仍然可以透過支援 Intune App SDK 的受管理應用程式使用應用程式設定原則。 

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 選擇 [用戶端應用程式] 工作負載。
4. 選擇 [管理] 群組中的 [應用程式設定原則]，然後選擇 [新增]。
5. 使用下列詳細資料：
    - **名稱**  
      將在 Azure 入口網站中顯示的設定檔名稱。
    - **描述**  
      將在 Azure 入口網站中顯示的設定檔描述。
    - **裝置註冊類型**  
      選擇 [管理應用程式]。
6. 選取 [相關聯的應用程式]  來選擇您要設定的應用程式。 從應用程式清單中選取您已經使用 Intune 核准並同步處理的應用程式。
7. 對於應用程式支援的每個組態設定，請鍵入 [名稱] 和 [值]，然後選擇省略符號 (**...**)。  
    若要刪除設定，請選擇省略符號 (**...**)，然後選取 [刪除]。  
    
啟用 Intune App SDK 的應用程式支援機碼值組中的設定。 請參閱每個應用程式的文件，以深入了解支援的機碼值設定。 請注意，您可以使用會動態填入應用程式所產生資料的權杖。 如需適用於 iOS 的 Outlook 應用程式設定原則設定的詳細資訊，請參閱[使用 Microsoft Intune 管理適用於 iOS 的 Outlook 應用程式](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx) \(機器翻譯\)。

## <a name="configuration-values-for-using-tokens"></a>使用權杖的設定值

Intune 可以產生特定的權杖，並將它們傳送給受管理的應用程式。 例如，如果您的應用程式設定可以使用電子郵件設定，則可以使用權杖新增動態電子郵件。 在 [名稱] 欄位中輸入應用程式所預期的名稱，然後在 [值] 欄位中輸入 `\{\{mail\}\}`。

Intune 支援組態設定中的下列權杖類型。 不支援其他自訂的索引鍵/值組。

- \{\{userprincipalname\}\} - 例如，John@contoso.com
- \{\{mail\}\} - 例如，John@contoso.com
- \{\{partialupn\}\} - 例如，John
- \{\{accountid\}\} - 例如，fc0dc142-71d8-4b12-bbea-bae2a8514c81
- \{\{userid\}\} - 例如，3ec2c00f-b125-4519-acf0-302ac3761822
- \{\{username\}\} - 例如，John Doe
- \{\{PrimarySMTPAddress\}\} - 例如，testuser@ad.domain.com


> [!Note]  
> \{\{ 和 \}\} 字元僅供權杖類型使用，絕不能用於其他用途。

## <a name="next-steps"></a>後續步驟

一如往常般地繼續[指派](apps-deploy.md)及[監視](apps-monitor.md)應用程式。
