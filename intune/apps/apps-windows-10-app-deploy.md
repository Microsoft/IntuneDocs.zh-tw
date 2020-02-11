---
title: 使用 Microsoft Intune 進行 Windows 10 應用程式部署
titleSuffix: ''
description: 了解可使用 Microsoft Intune 進行的 Windows 10 應用程式部署案例。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fa4510b95e1e84d9f94158833dac555daa33c690
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912551"
---
# <a name="windows-10-app-deployment-by-using-microsoft-intune"></a>使用 Microsoft Intune 進行 Windows 10 應用程式部署 

Microsoft Intune 支援 Windows 10 裝置上的各種應用程式類型和部署案例。 將應用程式新增至 Intune 之後，您可以將應用程式指派給使用者和裝置。 此文章提供支援的 Windows 10 情節的相關詳細資料，還涵蓋了將應用程式部署至 Windows 時要注意的重要詳細資料。 

企業營運 (LOB) 應用程式和商務用 Microsoft Store 應用程式是 Windows 10 裝置上支援的應用程式類型。 Windows 應用程式的副檔名包括 .msi、.appx 以及 .appxbundle。  

> [!Note]
> 若要部署新式應用程式，您至少需要：
> - 針對 Windows 10 1803，[2018 年 5 月 23 日—KB4100403 (OS 組建 17134.81)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403)。
> - 針對 Windows 10 1709，[2018 年 6 月 21 日—KB4284822 (OS 組建 16299.522)](https://support.microsoft.com/help/4284822)。
>
> 只有 Windows 10 1803 和更新版本才支援在沒有任何相關主要使用者的情況下安裝應用程式。
>
> 執行 Windows 10 家用版的裝置不支援 LOB 應用程式部署。

## <a name="supported-windows-10-app-types"></a>支援的 Windows 10 應用程式類型

根據您使用者正在執行的 Windows 10 版本，指定支援的應用程式類型。 下表提供應用程式類型和 Windows 10 支援能力。

| 應用程式類型 | 家庭 | 專業版 | Microsoft Store | 企業 | Education | S 模式 | HoloLens | SurfaceHub | WCOS | 行動電話 |
|----------------|------|-----|----------|------------|-----------|--------|-----------|------------|------|--------|
|  .MSI | 否 | 是 | 是 | 是 | 是 | 否 | 否 | 否 | 否 | 否 |
| .IntuneWin | 否 | 是 | 是 | 是 | 是 | 19H2+ | 否 | 否 | 否 | 否 |
| Office C2R | 否 | 是 | 是 | 是 | 是 | 否 | 否 | 否 | 否 | 否 |
| LOB:APPX/MSIX | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 |
| MSFB 離線 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 |
| MSFB 上線 | 是 | 是 | 是 | 是 | 是 | 是 | RS4+ | 是 | 是 | 是 |
| Web 應用程式 | 是 | 是 | 是 | 是 | 是 | 是 | 是<sup>1 | 是<sup>1 | 是 | 是 |
| 市集連結 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 |

<sup>1</sup> 僅限從公司入口網站啟動。

> [!NOTE]
> 所有 Windows 應用程式類型都需要註冊。

## <a name="windows-10-lob-apps"></a>Windows 10 LOB 應用程式

您可以簽署 Windows 10 LOB 應用程式，並將其上傳至 Intune 管理主控台。 這些可包含兩個新式應用程式 (例如通用 Windows 平台 (UWP) 應用程式和 Windows 應用程式套件 (AppX))，以及 Win 32 應用程式 (例如簡單的 Microsoft 安裝程式封裝檔案 (MSI))。 系統管理員必須手動上傳並部署 LOB 應用程式的更新。 這些更新會自動安裝在已安裝應用程式的使用者裝置上。 不需要使用者介入，使用者也無法控制更新。 

## <a name="microsoft-store-for-business-apps"></a>商務用 Microsoft Store 應用程式

商務用 Microsoft Store 應用程式是從商務用 Microsoft Store 管理入口網站購買。 然後透過 Microsoft Intune 同步處理進行管理。 應用程式可以線上授權或離線授權。 Microsoft Store 會直接管理更新，系統管理員不需要執行其他動作。您也可以使用自訂統一資源識別項 (URI) 來防止更新特定應用程式。 如需詳細資訊，請參閱 [Enterprise app management - Prevent app from automatic updates](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates) (企業應用程式管理 - 防止應用程式自動更新)。 使用者也可以停用裝置上所有商務用 Microsoft Store 應用程式的更新。 

### <a name="categorize-microsoft-store-for-business-apps"></a>分類商務用 Microsoft 網上商店應用程式 
若要分類商務用 Microsoft Store 應用程式： 

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [所有應用程式]  。 
3. 選取商務用 Microsoft Store 應用程式。 然後選取 [屬性]   > [應用程式資訊]   > [類別]  。 
4. 選取一個類別。

## <a name="install-apps-on-windows-10-devices"></a>在 Windows 10 裝置上安裝應用程式
視應用程式類型而定，您可以透過下列兩種方式之一在 Windows 10 裝置上安裝應用程式：

- **使用者內容**：當應用程式部署在使用者內容時，若使用者登入裝置，就會為裝置上的該使用者安裝受控應用程式。 請注意，在使用者登入裝置之前，應用程式安裝不會成功。 
  - 現代化 LOB 應用程式和商務用 Microsoft Store 應用程式 (線上和離線) 可部署在使用者內容中。 應用程式同時支援 [必要] 和 [可用] 意圖。
  - 建置為 [使用者模式] 或 [雙螢幕模式] 的 Win32 應用程式可在使用者內容中部署，並且同時支援 [必要] 及 [可用] 意圖。 
- **裝置內容**：當應用程式部署在裝置內容時，Intune 會將受控應用程式直接安裝在裝置上。
  - 只有現代化 LOB 應用程式和離線授權的商務用 Microsoft Store 應用程式可部署在裝置內容中。 這些應用程式僅支援 [必要] 意圖。
  - 建置為 [機器模式] 或 [雙螢幕模式] 的 Win32 應用程式可在裝置內容中部署，並且僅支援 [必要] 意圖。

> [!NOTE]
> 針對建置為 [雙螢幕模式] 的 Win32 應用程式，系統管理員必須選擇應用程式是否會針對所有與該執行個體建立關聯的指派作為 [使用者模式] 或 [機器模式] 應用程式運作。 部署內容無法根據每個指派進行變更。  

只有在裝置及 Intune 應用程式類型支援的情況下，才可以在裝置內容中安裝應用程式。 您可以在裝置內容中安裝下列應用程式類型，並將這些應用程式指派至裝置群組：

- Win32 應用程式
- 離線授權的商務用 Microsoft Store 應用程式
- LOB 應用程式 (MSI、APPX 及 MSIX)
- Office 365 專業增強版

您選取以在裝置內容中安裝的 Windows LOB 應用程式 (特別是 APPX 和 MSIX) 及商務用 Microsoft Store 應用程式 (離線應用程式)，必須指派至裝置群組。 如果其中一個這些應用程式是在使用者內容中部署，安裝將會失敗。 下列狀態和錯誤會出現在管理主控台中：
  - 狀態：失敗。
  - 錯誤：裝置內容安裝無法以使用者為目標。

> [!IMPORTANT]
> 搭配 Autopilot White Glove 佈建案例使用時，在裝置內容中部署的 LOB 應用程式和商務用 Microsoft Store 應用程式並不需要設定目標裝置群組。 如需詳細資訊，請參閱 [Windows Autopilot White Glove 部署](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) \(部分機器翻譯\)。

> [!Note]
> 將應用程式指派與特定部署一起儲存之後，除了新式應用程式以外，您無法變更該指派的內容。 針對新式應用程式，您可以將內容從 [使用者內容] 變更為 [裝置內容]。 

如果單一使用者或裝置上的原則有衝突，則適用下列優先順序：
- 裝置內容原則的優先順序高於使用者內容原則。 
- 安裝原則的優先順序高於解除安裝原則。

如需詳細資訊，請參閱 [Microsoft Intune 的包含與排除應用程式指派](apps-inc-exl-assignments.md)。 如需 Intune 應用程式類型的詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](apps-add.md)。

## <a name="next-steps"></a>後續步驟

- [使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)
- [如何監視應用程式](apps-monitor.md)
