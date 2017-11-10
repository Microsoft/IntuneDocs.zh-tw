---
title: "在不註冊裝置的情況下新增受管理應用程式的應用程式設定原則 | Microsoft Docs"
titlesuffix: Azure portal
description: "了解如何在不註冊裝置的情況下使用受管理應用程式的應用程式設定原則。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 750ce7dbb0dccf08757e076826e2d3650b6e6ab5
ms.sourcegitcommit: 67c037af31c1f167ec9b4f4baa754631c817e7d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2017
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>在不註冊裝置的情況下新增受管理應用程式的應用程式設定原則

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

即使在未註冊的裝置上，您仍然可以透過支援 Intune App SDK 的受管理應用程式使用應用程式設定原則。 

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  +  [Intune]。
3. 選擇 [Mobile Apps] 工作負載。
4. 按一下 [管理] 群組中的 [應用程式設定原則]，然後按一下 [新增]。
5. 使用下列詳細資料：
    - **名稱**  
      將在 Azure 入口網站中顯示的設定檔名稱。
    - **說明**  
      將在 Azure 入口網站中顯示的設定檔描述。
    - **裝置註冊類型**  
      選擇 [管理應用程式]。
6. 選取 [相關聯的應用程式] 來選擇您要設定的應用程式。 從應用程式清單中選取您已經使用 Intune 核准並同步處理的應用程式。
7. 對於應用程式支援的每個組態設定，請輸入 [名稱] 和 [值]，然後按一下省略符號 (**...**)。  
    若要刪除設定，請按一下省略符號 (**...**)，然後選取 [刪除]。  
    啟用 Intune App SDK 的應用程式支援索引鍵/值組中的設定。 請參閱每個應用程式的文件，以深入了解支援的索引鍵/值設定。  
    此外，您可以使用權杖，其會動態填入應用程式所產生的資料。

## <a name="configuration-values-using-tokens"></a>使用權杖的設定值

Intune 可以產生特定權杖，並傳送至受管理的應用程式。 比方說，如果您的應用程式設定可以使用電子郵件設定，則可以使用權杖新增動態電子郵件。 在 [名稱] 欄位中輸入應用程式所預期的名稱，然後在 [值] 欄位中輸入 `\{\{mail\}\}`。

Intune 支援組態設定中的下列權杖類型：

- \{\{userprincipalname\}\} - (範例：**John@contoso.com**)
- \{\{mail\}\} - (範例：**John@contoso.com**)
- \{\{partialupn\}\} - (範例：**John**)
- \{\{accountid\}\} - (範例：**fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
- \{\{deviceid\}\} - (範例：**b9841cd9-9843-405f-be28-b2265c59ef97**)
- \{\{userid\}\} - (範例：**3ec2c00f-b125-4519-acf0-302ac3761822**)
- \{\{username\}\} - (範例：**John Doe**)
- \{\{PrimarySMTPAddress\}\} - (範例：testuser@ad.domain.com) 


> [!Note]  
> \{\{ 和 \}\} 字元僅供權杖類型使用，絕不能用於其他用途。

## <a name="next-steps"></a>後續步驟

一如往常般地[指派](apps-deploy.md)及[監視](apps-monitor.md)應用程式。