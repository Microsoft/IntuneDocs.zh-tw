---
title: 使用 Microsoft Intune 進行 Windows 10 應用程式部署
titleSuffix: ''
description: 了解可使用 Microsoft Intune 進行的 Windows 10 應用程式部署案例。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8168cdaec4d6616b12fa4da225c84fa2d239994d
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2019
ms.locfileid: "67648647"
---
# <a name="windows-10-app-deployment-using-microsoft-intune"></a>使用 Microsoft Intune 進行 Windows 10 應用程式部署 

Microsoft Intune 目前支援 Windows 10 裝置上的各種應用程式類型和部署案例。 將應用程式新增至 Intune 之後，您可以將應用程式指派給使用者和裝置。 下列資訊提供與支援的 Windows 10 案例相關的更多詳細資料。 此外，下列資訊提供將應用程式部署到 Windows 時要注意的重要詳細資料。 

企業營運 (LOB) 應用程式和商務用 Microsoft Store 應用程式是 Windows 10 裝置上支援的應用程式類型。 Windows 應用程式的副檔名包括 **.msi**、 **.appx**，以及 **.appxbundle**。  

> [!Note]
> 部署現代化應用程式所需的最低 Windows 10 更新如下：
> - 針對 Windows 10 1803，[2018 年 5 月 23 日—KB4100403 (OS 組建 17134.81)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403)。
> - 針對 Windows 10 1709，[2018 年 6 月 21 日—KB4284822 (OS 組建 16299.522)](https://support.microsoft.com/help/4284822)。

## <a name="windows-10-line-of-business-apps"></a>Windows 10 企業營運應用程式

Windows 10 LOB 應用程式會簽署及上傳至 Intune 管理主控台，並可包含兩個現代化應用程式 (例如通用 Windows 平台 (UWP) 應用程式和 Windows 應用程式套件 (AppX))，以及 Win 32 應用程式 (例如簡單的 Microsoft 安裝程式封裝檔案 (MSI))。 系統管理員必須每次手動上傳及部署 LOB 應用程式的更新。部署的更新會自動安裝在已安裝應用程式的終端使用者裝置上，無需使用者介入。 使用者對更新沒有控制權。 

## <a name="microsoft-store-for-business-apps"></a>商務用 Microsoft 網上商店應用程式

商務用 Microsoft Store 應用程式是從商務用 Microsoft Store 管理入口網站購買，然後透過 Microsoft Intune 同步進行管理的現代化應用程式。 應用程式可以**線上授權**或**離線授權**。 商務用 Microsoft Store 應用程式的更新是由 Microsoft Store 直接管理，系統管理員不需要採取其他動作。系統管理員也可以使用自訂統一資源識別項 (URI) 來防止更新特定應用程式。 如需詳細資訊，請參閱 [Enterprise app management - Prevent app from automatic updates](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates) (企業應用程式管理 - 防止應用程式自動更新)。 在裝置上，終端使用者也可以停用裝置上所有商務用 Microsoft Store 應用程式的更新。 

## <a name="installing-apps-on-windows-10-devices"></a>在 Windows 10 裝置上安裝應用程式
視應用程式類型而定，您可以透過下列兩種方式之一在 Windows 10 裝置上安裝應用程式：

- **使用者內容**：當應用程式部署在使用者內容時，若使用者登入裝置，就會為裝置上的該使用者安裝受控應用程式。 請注意，在使用者登入裝置之前，應用程式安裝不會成功。 
    - 現代化企業營運應用程式和商務用 Microsoft Store 應用程式 (線上和離線) 可部署在使用者內容中，而且會支援「必要」和「可用」意圖。
    - 建置為 [使用者模式]  或 [雙螢幕模式]  的 Win32 應用程式可在使用者內容中部署，並且會同時支援 [必要]  及 [可用]  意圖。 
- **裝置內容**：當應用程式部署在裝置內容時，Intune 會將受控應用程式直接安裝在裝置上。
    - 只有現代化企業營運應用程式和離線授權的商務用 Microsoft Store 應用程式可部署在裝置內容中，而且只會支援「必要」意圖。
    - 建置為 [機器模式]  或 [雙螢幕模式]  的 Win32 應用程式可在使用者內容中部署，並且僅支援 [必要]  意圖。

> [!NOTE]
> 針對建置為 [雙螢幕模式]  的 Win32 應用程式，您 (系統管理員) 將需要挑選應用程式是否會針對所有與該執行個體建立關聯的指派作為 [使用者模式]  或 [機器模式]  運作。 部署內容無法根據每個指派進行變更。  

當應用程式部署在裝置內容時，只有以支援裝置內容的裝置為目標的安裝才會成功。 此外，在裝置內容中部署支援下列情況：
- 如果應用程式部署在裝置內容中，並以使用者為目標，安裝會失敗，並在管理主控台中顯示下列狀態和錯誤：
    - 狀態：失敗。
    - 錯誤：裝置內容安裝無法以使用者為目標。
- 如果應用程式部署在裝置內容中，但以不支援裝置內容的裝置為目標，安裝會失敗，並在管理主控台中顯示下列狀態和錯誤：
    - 狀態：失敗。
    - 錯誤：此平台不支援裝置內容安裝。 

> [!Note]
> 將應用程式指派與特定部署一起儲存之後，則無法變更該指派的內容，除了現代化應用程式以外。 若是現代化應用程式案例，內容可以從使用者內容變更為裝置內容。 

如果單一使用者/裝置上的原則出現衝突，以下是用來決定最終原則的原則優先順序：
- 裝置內容原則的優先順序高於使用者內容原則。 
- 安裝原則的優先順序高於解除安裝原則。

如需使用 Microsoft Intune 指派應用程式的詳細資訊，請參閱[使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)和 [Microsoft Intune 的包含與排除應用程式指派](apps-inc-exl-assignments.md)。 如需 Intune 應用程式類型的詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](apps-add.md)。

## <a name="next-steps"></a>後續步驟

- 若要深入了解如何應用程式指派給群組，請參閱[使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)。
- 若要深入了解監視應用程式指派，請參閱[如何監視應用程式](apps-monitor.md)。
