---
title: 將 Windows 企業營運應用程式新增至 Microsoft Intune
titleSuffix: ''
description: 了解如何使用 Microsoft Intune 來新增 Windows 企業營運 (LOB) 應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6df77d168bb8be3775c566f63833b46130515b36
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601571"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>將 Windows 企業營運應用程式新增至 Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

企業營運 (LOB) 應用程式是您從應用程式安裝檔案新增的應用程式。 這類應用程式通常是在內部撰寫的。 下列步驟提供指引，協助您將 Windows LOB 應用程式新增至 Microsoft Intune。

> [!IMPORTANT]
> 當使用具有 *.msi* 副檔名的安裝檔案部署 Win32 應用程式時，請考慮使用 [Intune 管理延伸模組](../apps/intune-management-extension.md)。 若您在 AutoPilot 註冊期間混合 Win32 應用程式與企業營運系統應用程式安裝，應用程式安裝可能會失敗。  

## <a name="step-1-specify-the-software-setup-file"></a>步驟 1：指定軟體安裝檔

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在 [Intune]  窗格中，選取 [用戶端應用程式]  。
4. 在 [用戶端應用程式]  工作負載中，選取 [管理]   > [應用程式]  。
5. 從應用程式清單上方，選取 [新增]  。
6. 在 [新增應用程式]  窗格中，選取 [企業營運應用程式]  。

## <a name="step-2-configure-the-app-package-file"></a>步驟 2：設定應用程式套件檔案

1. 在 [新增應用程式]  窗格中，選取 [應用程式套件檔案]  。
2. 在 [應用程式套件檔案]  窗格中，選取 [瀏覽] 按鈕。 然後選取副檔名為 **.msi**、 **.appx** 或 **.appxbundle** 的 Windows 安裝檔案。

    > [!NOTE]
    > Windows 應用程式的副檔名包含 **.msi**、 **.appx**、 **.appxbundle**、 **.msix**、 和 **.msixbundle**。  

1. 完成後，按一下 [確定]  。


## <a name="step-3-configure-app-information"></a>步驟 3：設定應用程式資訊

1. 在 [新增應用程式]  窗格中，選取 [應用程式資訊]  。
2. 在 [應用程式資訊]  窗格中，設定下列資訊。 窗格中某些值可能會自動填入。
    - **名稱**：輸入在公司入口網站中顯示的應用程式名稱。 確定您使用的所有應用程式名稱都是唯一的。 如果有重複的應用程式名稱，只有一個應用程式會出現在公司入口網站中。
    - **描述**：輸入應用程式的描述。 此描述會出現在公司入口網站上。
    - **發行者**：輸入應用程式發行者的名稱。
    - **略過應用程式版本**：如果應用程式開發人員會自動更新應用程式，請設定為 [是]  。 此選項只適用於行動裝置的 .msi 應用程式。
    - **類別**：選取一或多個內建的應用程式類別，或選取您建立的類別。 類別可以讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式**：當使用者瀏覽應用程式時，在公司入口網站的主頁面上，以突顯的方式顯示應用程式。
    - **資訊 URL**：(選擇性) 輸入包含應用程式相關資訊的網站 URL。 此 URL 會出現在公司入口網站上。
    - **隱私權 URL**：(選擇性) 輸入包含應用程式隱私權資訊的網站 URL。 此 URL 會出現在公司入口網站上。
    - **命令列引數**：(選擇性) 輸入任何您想要在 .msi 檔案執行時套用的命令列引數。  **/q** 就是一個例子。 因為系統會自動使用 msiexec 命令或引數，例如 **/i** 或 **/x**，所以請不藥包含在內。 如需詳細資訊，請參閱[命令列選項](https://docs.microsoft.com/windows/desktop/Msi/command-line-options)。 如果 .MSI 檔案需要其他命令列選項，請考慮使用 [Win32 應用程式管理](app-management.md)。
    - **開發人員**：(選擇性) 輸入應用程式開發人員的姓名。
    - **擁有者**：(選擇性) 輸入此應用程式之擁有者的名稱。 **人力資源部門**就是一個例子。
    - **附註**：輸入要與此應用程式建立關聯的任何附註。
    - **標誌**：上傳與應用程式相關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
3. 完成後，按一下 [確定]  。

## <a name="step-4-finish-up"></a>步驟 4：完成

1. 在 [新增應用程式]  窗格中，確認您所設定的應用程式資訊正確無誤。
2. 選取 [新增]  ，將應用程式上傳至 Intune。

## <a name="step-5-update-a-line-of-business-app"></a>步驟 5：更新企業營運應用程式

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

   > [!NOTE]
   > 若要讓 Intune 服務成功地將新的 APPX 檔案部署到裝置，您必須對 APPX 套件內 AppxManifest.xml 檔案中的 `Version` 字串進行遞增處理。

## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>設定自行更新行動 MSI 應用程式略過版本檢查程序

您可以設定已知的自行更新行動 MSI 應用程式略過版本檢查程序。

應用程式開發人員或其他更新方法會自動更新某些 MSI 安裝程式應用程式。 對於這些自動更新的 MSI 應用程式，您可以在 [應用程式資訊]  窗格中設定 [略過應用程式版本]  設定。 當您將此設定切換為 [是]  時，Microsoft Intune 不會強制執行 Windows 用戶端上安裝的應用程式版本。

這項功能對於不陷入競爭狀況很有用。 例如，本應該由應用程式開發人員自動更新的應用程式，卻由 Intune 來進行更新，這時候就會發生競爭狀況。 二者或許想在 Windows 用戶端上強制執行某一版的應用程式，這樣就會發生衝突。

## <a name="next-steps"></a>後續步驟

- 您所建立的應用程式會出現在應用程式清單中。 您現在可以將它指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](apps-deploy.md)。

- 深入了解您可用來監視應用程式屬性和指派的方式。 請參閱[如何監視應用程式資訊和指派](apps-monitor.md)。

- 深入了解您應用程式在 Intune 中的內容。 請參閱 [Microsoft Intune 中的應用程式生命週期概觀](app-lifecycle.md)。
