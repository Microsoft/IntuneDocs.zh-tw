---
title: "使用 Microsoft Intune 檢視您的裝置 - Azure | Micrososft Docs"
description: "檢視您的裝置詳細資料，包括作業系統、儲存空間、製造商和型號等等。 在 Azure 中使用 Microsoft Intune 取得已安裝的應用程式清單、檢查相容性原則、設定 TeamViewer，以及執行其他更多作業。 類似檢視清查您管理的裝置。"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 934ba0853f8bee851f7027580c276a9fff911b7f
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="see-device-details-in-intune"></a>在 Intune 中查看裝置詳細資料

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**裝置**功能提供您管理的裝置其他詳細資料，包括其硬體及安裝的應用程式。 

這篇文章會示範如何在 Azure 入口網站中檢視您的所有裝置及其屬性。

## <a name="view-your-device-details"></a>檢視裝置詳細資料

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置]。 在 [裝置] 中您有幾個選擇：

  - **概觀** - 取得您註冊的裝置及每部裝置執行之作業系統的資訊。
  - **管理** - 選擇 [所有裝置] 或 [Azure AD 裝置] 可查看您管理的所有裝置清單。
    在清單中選取其中一部裝置。 此步驟會開啟 <*裝置名稱*> [概觀]，您可在此選取下列項目：
    - **概觀** - 如果它是「攜帶您自己的裝置」(BYOD) 裝置，當它登入時，可以查看裝置名稱、擁有者，以及更多詳細資料
    - **硬體** - 查看裝置的可用儲存空間、型號及製造商，以及詳細資訊
    - **探索到的應用程式** - 列出 Intune 找到已安裝在裝置上的所有應用程式
    - **裝置相容性** - 顯示所有已指派給裝置之相容性原則的狀態
    - **裝置設定** - 顯示所有指派給裝置之所有裝置設定原則的相容性狀態
- **監視** - 選擇 [裝置動作] 可查看您管理之裝置已完成的動作清單，以及其目前的狀態。 **稽核記錄**顯示不同工作的狀態。
- **安裝程式** > **TeamViewer 連接器** - 使用 TeamViewer 軟體在裝置上設定遠端管理。 如需詳細資料，請參閱[對 Intune 管理的 Android 裝置提供遠端協助](device-profile-android-teamviewer.md)。

Intune 只會在公司擁有的裝置上收集應用程式清單。 不檢查個人裝置上的應用程式。 若為 Windows 10 電腦，只會列出公司擁有裝置上的新式應用程式。 Intune 不會收集裝置上的 Win32 應用程式相關資訊。 視裝置的電訊廠商用途而定，不會收集所有的應用程式。

## <a name="next-steps"></a>接下來的步驟
看看您還可以怎麼使用 Intune [管理您的裝置](device-management.md)。
