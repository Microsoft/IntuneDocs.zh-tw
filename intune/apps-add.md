---
title: "如何將應用程式新增至 Microsoft Intune"
titleSuffix: Intune on Azure
description: "這些程序可協助您將應用程式加入 Intune，讓您可以指派給使用者與裝置。 \""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6a4dfa9e0066a2ac6f410aa9f8e4d77a40484ea5
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-add-an-app-to-microsoft-intune"></a>如何將應用程式新增至 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

若要管理您使用者的應用程式及為其指派應用程式，必須先將應用程式新增到 Intune。 Intune 支援各種不同的應用程式類型，而每種類型的選項可能各不相同。

Intune 可讓您新增及指派下列應用程式類型：

![Intune 支援的應用程式類型](./media/app-types.png)

以下是支援的平台。

- Android 市集應用程式
- Android 企業營運 (LOB) 應用程式
- iOS 市集應用程式
- iOS 企業營運 (LOB) 應用程式
- Web 應用程式
- Windows Phone 8.1 市集應用程式
- Windows Phone 企業營運應用程式 (.xap 檔案)
- Windows 市集應用程式
- Windows 企業營運應用程式 (僅限 .msi 檔案)

>[!TIP]
> 企業營運 (LOB) 應用程式不是從應用程式市集安裝，而是從應用程式安裝檔案安裝。 例如，若要安裝 iOS LOB 應用程式，您必須新增應用程式封存檔案 (副檔名是 .ipa)。 這些通常是在內部撰寫的應用程式。

## <a name="before-you-start"></a>開始之前

在您開始新增和指派應用程式之前，請考慮下列事項。

- 當您新增及指派來自市集的應用程式時，使用者必須擁有該市集的帳戶，才能安裝應用程式。
- 您指派的某些應用程式或項目可能相依於內建的 iOS 應用程式。 例如，如果您指派來自 iOS Store 的書籍，則裝置上必須有 iBooks 應用程式。 如果您已經移除了 iBooks 內建應用程式，您將無法使用 Intune 來恢復該應用程式。

## <a name="cloud-storage-space"></a>雲端儲存空間
使用軟體安裝程式安裝類型所建立的所有應用程式 (例如企業營運應用程式)，都必須封裝並上傳至 Intune 雲端儲存空間。 Intune 的試用版訂閱內容包含 2 GB 的雲端式儲存空間，可用來儲存受管理的應用程式和更新。 完整訂閱將包含 20 GB 的儲存空間。

您可以使用原始購買方法來購買 Intune 的額外儲存空間。  如果您是用發票或信用卡支付，請前往[訂用帳戶管理入口網站](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions)。  否則，請連絡合作夥伴或銷售人員。

雲端儲存空間需求如下：

-   所有應用程式安裝檔案必須位於相同的資料夾。
-   您上傳的任何檔案其檔案大小上限都是 2 GB。

## <a name="how-to-create-and-edit-categories-for-apps"></a>如何建立及編輯應用程式的類別

應用程式類別可協助您排序應用程式，以利使用者在公司入口網站中執行搜尋。 您可以指派一或多個類別給應用程式，例如**開發人員應用程式**或**通訊應用程式**。
當您將應用程式新增到 Intune 時，可以自由選取所需的類別。 使用平台相關的主題來新增應用程式及指派類別。 若要建立及編輯您自己的類別，請使用下列程序︰

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗上，選擇 [行動應用程式]。
4. 在**行動應用程式**工作負載中，選擇 [安裝] >  [應用程式類別]。
5. 在 [應用程式類別] 刀鋒視窗中會列出目前的類別。 請選擇下列其中一個動作：
    - **建立類別**︰在 [建立類別] 刀鋒視窗中輸入新類別的名稱。 名稱只能以一種語言輸入，而且 Intune 不會翻譯它。 完成時按一下 [建立]。
    - **編輯類別** - 為清單中的類別選擇 [...]。 您可以在 [內容] 刀鋒視窗中，輸入類別的新名稱或刪除類別。


## <a name="apps-added-automatically-by-intune"></a>Intune 自動新增的應用程式

下列由 Microsoft 發佈的應用程式內建於 Intune 中，且可以供您指派：

|||
|-|-|
|名稱|平台|應用程式類型|
|Azure 資訊保護|Android|受管理的 Android Store 應用程式|
|適用手機的 Dynamics CRM|Android|受管理的 Android Store 應用程式|
|適用於平板電腦的 Dynamics CRM|Android|受管理的 Android Store 應用程式|
|Excel|iOS|受管理的 iOS Store 應用程式|
|Excel|Android|受管理的 Android Store 應用程式|
|受管理的瀏覽器|Android|受管理的 Android Store 應用程式|
|受管理的瀏覽器|iOS|受管理的 iOS Store 應用程式|
|適用於手機的 Microsoft Dynamics CRM|iOS|受管理的 iOS Store 應用程式|
|適用於平板電腦的 Microsoft Dynamics CRM|iOS|受管理的 iOS Store 應用程式|
|Microsoft Power BI|iOS|受管理的 iOS Store 應用程式|
|Microsoft Power BI|Android|受管理的 Android Store 應用程式|
|Microsoft SharePoint|iOS|受管理的 iOS Store 應用程式|
|Microsoft SharePoint|Android|受管理的 Android Store 應用程式|
|Microsoft Teams|Android|受管理的 Android Store 應用程式|
|Microsoft Teams|iOS|受管理的 iOS Store 應用程式|
|OneDrive|iOS|受管理的 iOS Store 應用程式|
|OneDrive|Android|受管理的 Android Store 應用程式|
|OneNote|iOS|受管理的 iOS Store 應用程式|
|Outlook|Android|受管理的 Android Store 應用程式|
|Outlook|iOS|受管理的 iOS Store 應用程式|
|Outlook Groups|Android|受管理的 Android Store 應用程式|
|Outlook Groups|iOS|受管理的 iOS Store 應用程式|
|PowerPoint|iOS|受管理的 iOS Store 應用程式|

## <a name="next-steps"></a>後續步驟

選擇下列其中一個主題，以了解如何針對各平台將應用程式新增到 Intune：

- [Android 市集應用程式](store-apps-android.md)
- [Android LOB 應用程式](lob-apps-android.md)
- [iOS 市集應用程式](store-apps-ios.md)
- [iOS LOB 應用程式](lob-apps-ios.md)
- [Web 應用程式 (適用於所有平台)](web-app.md)
- [Windows Phone 8.1 市集應用程式](store-apps-windows-phone-8-1.md)
- [Windows Phone LOB 應用程式](lob-apps-windows-phone.md)
- [Windows 市集應用程式](store-apps-windows.md)
- [Windows LOB 應用程式](lob-apps-windows.md)

