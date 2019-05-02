---
title: 在 Microsoft Intune 中使用 Windows 10 裝置的範本 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中使用系統管理範本為 Windows 10 裝置建立設定群組。 使用裝置組態設定檔中的這些設定，來控制 Office 程式、保護 Internet Explorer 中的功能、控制對 OneDrive 的存取、使用遠端桌面功能、啟用 [自動播放]、設定電源管理設定、使用 HTTP 列印、使用不同的使用者登入選項，以及控制事件記錄檔大小。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/27/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 704abe5e03410b52d54c7729e1832e527ae4dfb6
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61504268"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>在 Microsoft Intune 中使用 Windows 10 範本設定群組原則設定

當您管理組織中的裝置時，您想要建立一組設定來套用至不同的裝置群組。 例如，您有數個裝置群組。 針對群組 A，您想要指派一組特定設定。 針對群組 B，您想要指派另一組設定。 您也需要可進行之設定的簡單檢視。

您可以在 Microsoft Intune 中使用 [系統管理範本] 來完成這項工作。 系統管理範本包含數百項設定，可控制 Internet Explorer 中的功能、Microsoft Office 程式、遠端桌面、對 OneDrive 的存取、使用圖片密碼或 PIN 進行登入，以及執行其他作業。 這些範本類似於 Active Directory (AD) 中的群組原則 (GPO) 設定，且是使用 XML 之 [ADMX 支援的設定](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies) (開啟另一個 Docs 網站)。 但 Intune 中的範本是 100% 雲端架構。 它們提供更簡單直接的方法來進行設定，以及尋找您想要的設定。

**系統管理範本**內建於 Intune 中，並不需要任何自訂項目，包括使用 OMA-URI。 作為行動裝置管理 (MDM) 解決方案的一部分，請使用這些範本設定作為您一次管理 Windows 10 裝置的位置。

本文列出建立 Windows 10 裝置範本的步驟，並示範如何篩選 Microsoft Intune 中的所有可用設定。 當您建立範本時，它會建立裝置組態設定檔。 您可以接著將此設定檔指派或部署到您組織中的 Windows 10 裝置。

## <a name="create-a-template"></a>建立範本

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務] > 篩選 [Intune] > 選取 [Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入下列內容：

    - **名稱**：輸入設定檔的名稱。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取 [Windows 10 及更新版本]。
    - **設定檔類型**：選取 [系統管理範本 (預覽)]。

4. 選取 [建立]。 在新視窗中，選取 [設定]。 列出每項設定，且您可以使用上一個和下一個箭號來查看更多設定：

    ![查看設定清單範例並使用上一個和下一個按鈕](./media/administrative-templates-windows/sample-settings-list-next-page.png)

5. 選取任何設定。 例如，選取 [允許檔案下載]。 設定的詳細描述會隨即顯示。 選擇 [啟用]、[停用]，或將設定保留為 [未設定] (預設)。 此詳細描述也會說明當您選擇 [啟用]、[停用] 或 [未設定] 時所發生的情況。
6. 按一下 [確定] 以儲存您的變更。

繼續檢閱設定清單，並設定您環境中所需的設定。 以下是一些範例：

- 使用 [VBA 巨集通知設定] 設定來處理不同 Microsoft Office 程式 (包括 Word 和 Excel) 中的 VBA 巨集。
- 使用 [允許檔案下載] 設定來允許或防止從 Internet Explorer 下載。
- 使用 [喚醒電腦時必須使用密碼 (一般電源)] 設定，在裝置從睡眠模式喚醒時提示使用者輸入密碼。
- 使用 [下載未簽署的 ActiveX 控制項] 設定來防止使用者從 Internet Explorer 下載未簽署的 ActiveX 控制項。
- 使用 [關閉系統還原] 設定來允許或防止使用在裝置上執行系統還原。
- 還有更多項目...

## <a name="find-some-settings"></a>尋找一些設定

這些範本提供數百項設定。 若要更輕鬆地尋找特定設定，請使用內建功能：

- 在您的範本中，選取 [設定]、[狀態] 或 [路徑] 資料行來排序清單。 例如，選取 [路徑] 資料行來查看 `Microsoft Excel` 路徑中的所有設定：

  ![按一下 [路徑] 以依字母順序排序](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- 在您的範本中，使用 [搜尋] 方塊來尋找特定設定。 例如，搜尋 `copy`。 這會顯示包含 `copy` 的所有設定：

  ![按一下 [路徑] 以依字母順序排序](./media/administrative-templates-windows/search-copy-settings.png)

  在另一個範例中，搜尋 `microsoft word`。 您會看到可為 Microsoft Word 程式設定的所有設定。 搜尋 `explorer` 來查看您可以新增至範本的所有 Internet Explorer 設定。

這項功能會使用 [Windows policy CSPs](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies) (Windows 原則 CSP) (開啟另一個 Docs 網站)。 CSP 適用於不同版本的 Windows，例如 Home、Professional、Enterprise 等。 若要查看 CSP 是否適用於特定版本，請前往 [Windows policy CSPs](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies) (Windows 原則 CSP) (開啟另一個 Docs 網站)。

## <a name="next-steps"></a>後續步驟

範本已建立，但還不會執行任何動作。 接下來，[指派範本 (也稱為設定檔)](device-profile-assign.md) 並[監視其狀態](device-profile-monitor.md)。
