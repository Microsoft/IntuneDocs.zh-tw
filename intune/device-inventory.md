---
title: 使用 Microsoft Intune 來檢視裝置詳細資料 - Azure | Microsoft Docs
description: 檢視您的裝置詳細資料，包括作業系統、儲存空間、製造商和型號等等。 在 Azure 中使用 Microsoft Intune 取得已安裝的應用程式清單、檢查相容性原則，以及設定 TeamViewer。 類似檢視清查您管理的裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f66c0695c7e3d1f4bb7a5ca3abceeb13f6af41f2
ms.sourcegitcommit: 3c4ea8d6809a63042705b5ed4f25ba80f522070e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2018
ms.locfileid: "34051601"
---
# <a name="see-device-details-in-intune"></a>在 Intune 中查看裝置詳細資料

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

[裝置] 功能提供您管理之裝置其他詳細資料，包括其硬體及安裝的應用程式。

這篇文章會示範如何在 Azure 入口網站中檢視您的所有裝置及其屬性。

## <a name="view-the-device-details"></a>檢視裝置詳細資料

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置] > [所有裝置] > 選取其中一個列出的裝置以開啟其詳細資料：

   - [概觀] 會在裝置簽入後，顯示裝置名稱並列出該裝置的一些重要屬性，包括它是否為「攜帶您自己的裝置」(BYOD) 裝置等。 選取 [更多] 以一併執行下列操作：
     - 移除公司資料
     - 刪除裝置
     - 從遠端鎖定裝置
     - 清除
     - 啟動遠端協助工作階段
   - 使用 [內容] 來指派[您所建立的類別](device-group-mapping.md)，以及將裝置的擁有權變更為個人裝置或公司裝置。
   - [硬體] 包含裝置的許多相關詳細資料，包括裝置識別碼、作業系統和版本、儲存空間、型號和製造商、條件式存取設定等詳細資料。
   - [探索到的應用程式] 會列出 Intune 找到已安裝在裝置上的所有應用程式，以及應用程式版本。 您也可以將應用程式清單 [匯出] 成 .csv 檔案。
   - [裝置合規性] 會列出所有已指派的合規性原則，以及裝置是否符合規範。
   - [裝置設定]會顯示已指派給裝置的所有裝置設定原則，以及原則是否成功。

Intune 只會在公司擁有的裝置上收集應用程式清單。 不檢查個人裝置上的應用程式。 若為 Windows 10 電腦，只會列出公司擁有裝置上的新式應用程式。 Intune 不會收集裝置上的 Win32 應用程式相關資訊。 視裝置使用的電訊廠商而定，不會收集所有的應用程式。

|平台|屬個人擁有的裝置|屬公司擁有的裝置|  
|--------------|---------------------------------|--------------------------------|  
|Windows 10 (不含 Configuration Manager 用戶端)|僅限受管理的應用程式|僅限受管理的應用程式|
|Windows 8.1 (不含 Configuration Manager 用戶端)|僅限受管理的應用程式|僅限受管理的應用程式|  
|Windows Phone 8|僅限受管理的應用程式|僅限受管理的應用程式|  
|Windows RT|僅限受管理的應用程式|僅限受管理的應用程式|  
|iOS|僅限受管理的應用程式|安裝在裝置上的所有應用程式|
|macOS|安裝在裝置上的所有應用程式|安裝在裝置上的所有應用程式|  
|Android|僅限受管理的應用程式|安裝在裝置上的所有應用程式|  

## <a name="next-steps"></a>接下來的步驟
看看您還可以怎麼使用 Intune [管理您的裝置](device-management.md)。