---
title: Microsoft 365 中的裝置管理
description: Microsoft 365 企業版隨附 Microsoft Intune。 了解 Intune 如何為您的組織提供行動裝置管理與行動應用程式管理。 閱讀常見的案例，並使用 Intune 在您的環境中部署 Microsoft 365。
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/14/2019
ms.topic: conceptual
audience: ITPro
ms.service: microsoft-intune
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 99dcf53d7571dfa660ee669c1d7adcea65f0797e
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "71167723"
---
# <a name="what-is-device-management"></a>什麼是裝置管理？ 

任何系統管理員的一項主要工作是保護組織的資源和資料安全。 這項工作為「裝置管理」  。 使用者擁有許多裝置，他們可以在裝置上開啟及共用個人檔案、瀏覽網站，以及安裝應用程式和遊戲。 同樣的這些使用者也是員工和學生。 他們想要使用其裝置來存取工作和學校資源，例如電子郵件和 OneNote。 裝置管理可讓組織保護其資源和資料的安全。 

透過裝置管理提供者，組織可以確保只有授權的人員和裝置才能存取專屬資訊。 同樣地，裝置使用者可以放心從其手機存取工作資料，因為他們知道其裝置符合組織的安全性需求。 作為組織，您可能會詢問：**應該使用哪項服務來保護資源？**

答案是 [Microsoft Intune](introduction-intune.md)。 Intune 提供行動裝置管理 (MDM) 與行動應用程式管理 (MAM)。 任何 MDM 或 MAM 解決方案的一些主要工作包括：

- 支援不同的行動環境並安全地管理 iOS、Android、Windows 和 macOS 裝置。
- 確保裝置和應用程式都符合您組織的安全性需求。
- 建立原則來協助確保公司擁有和個人裝置上的組織資料安全。
- 使用單一整合的行動解決方案來實施這些原則，並協助管理裝置、應用程式、使用者和群組。

Intune 隨附於 Microsoft 365，並與 Azure Active Directory (Azure AD) 整合。 Azure AD 協助控制誰有權存取，以及可存取的內容。

## <a name="hello-intune"></a>Hello Intune！
Microsoft 等許多組織使用 Intune 來保護使用者有權從其公司擁有和個人行動裝置存取的專屬資料。 Intune 包含裝置和應用程式設定原則、軟體更新原則、安裝狀態 (圖表、資料表和報表)，以協助您保護及監視資料存取。

許多人員通常會有使用不同平台的多部裝置。 例如，員工可能會使用 Surface Pro 處理工作，並使用 Android 行動裝置處理其個人檔案。 此外，每個人員通常會從多部裝置存取組織資源，例如 Microsoft Outlook 和 SharePoint。

透過 Intune，您可以管理每個人員的多部裝置，以及在每部裝置上執行的不同平台，包括 iOS、macOS、Android 和 Windows。 Intune 會依裝置平台區隔原則和設定。 因此很容易管理及檢視特定平台的裝置。

**[常見案例](common-scenarios.md)** 是一個絕佳資源，可讓您了解 Intune 如何解決使用行動裝置時的常見問題。 您將找到下列相關案例：  
- 使用內部部署 Exchange 保護電子郵件
- 安全可靠地存取 Office 365
- 使用個人裝置存取組織資源

## <a name="integration-with-secure-and-protect-services"></a>與安全且受保護的服務整合
任何裝置管理解決方案的一項主要工作是提供安全性和保護。 Intune 很適合用來與其他服務整合，以達成這項工作。 例如：

- **Microsoft 365** 是簡化常見 IT 工作的關鍵元件。 在 Microsoft 365 系統管理中心中，您可以建立使用者，和管理群組。 您也可以存取其他服務，例如 Intune、Azure AD 等。

  例如，在 Microsoft 365 中建立 iOS 裝置群組。 然後，使用 Intune 將原則推送至 iOS 裝置群組以集中在 iOS 功能，例如存取 App Store、使用 AirDrop、備份到 iCloud、使用 Apple 網站篩選等。

- **Windows Defender** 包含許多安全性功能，可協助保護 Windows 10 裝置。 例如，Intune 與 Windows Defender 搭配使用，您可以： 

  - 啟用 [Windows Defender SmartScreen](endpoint-protection-windows-10.md) 以尋找行動裝置上檔案和應用程式中的可疑活動。 
  - 使用 [Microsoft Defender 進階威脅防護 (ATP)](advanced-threat-protection.md) 來協助防止行動裝置上的安全性缺口。 此外，您也可以封鎖使用者存取公司資源，協助限制安全性缺口的影響。

- **條件式存取**是 Azure Active Directory 功能，並與 Intune 完美整合。 使用[條件式存取](conditional-access.md)，確保只有符合規範的裝置才能存取電子郵件、SharePoint 與其他應用程式。 

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>選擇適合您的裝置管理解決方案

有兩種方法可用來進行裝置管理。 首先，您可以使用 Intune 內建的功能，來管理裝置的不同層面。 這個方法稱為**行動裝置管理 (MDM)** 。 使用者會「註冊」其裝置，並使用憑證與 Intune 通訊。 身為 IT 系統管理員，您會在裝置上推送應用程式、將裝置限制在特定作業系統、封鎖個人裝置及執行其他工作。 如果裝置遺失或遭竊，您也可以從裝置移除所有資料。 

在第二個方法中，您可以管理裝置上的應用程式。 這個方法稱為**行動應用程式管理 (MAM)** 。 使用者可以使用其個人裝置存取組織資源。 開啟應用程式時 (例如電子郵件或 SharePoint)，系統會提示使用者進行額外驗證。 如果裝置遺失或遭竊，您可以從裝置移除所有組織資料。 

您也可以使用 [MDM 與 MAM](byod-technology-decisions.md) 的組合。

當您設定 Intune 時，您也可以選擇只在 Azure 入口網站中管理裝置，或同時使用 Intune 和 Microsoft 365 來管理裝置。 [Migrating mobile device management to Intune in the Azure portal](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal) (在 Azure 入口網站中將行動裝置管理移轉到 Intune) 是 Microsoft IT 案例研究。 在此案例研究中，了解 Microsoft IT 如何選擇現代化裝置管理方法，並閱讀學習到的課程。

## <a name="simplify-it-tasks-using-the-device-management-admin-center"></a>使用裝置管理系統管理中心簡化 IT 工作

[裝置管理系統管理中心](https://devicemanagement.microsoft.com/)是您一次管理及完成行動裝置工作的位置。 此工作區包含用於裝置管理的服務 (包括 Intune 與 Azure Active Directory)，以及用於管理用戶端應用程式的服務。 

在 [裝置管理] 系統管理中心，您可以：

- [註冊裝置](device-enrollment.md)
- [設定裝置合規性](device-compliance-get-started.md)
- [管理裝置](device-management.md)
- [管理應用程式](app-management.md)  
- [iOS 電子書](vpp-ebooks-ios.md)  
- [安裝 Exchange 內部部署連接器](exchange-connector-install.md)  
- [管理角色](role-based-access-control.md)  
- 管理軟體更新
  - [管理 Windows 10 更新](windows-update-for-business-configure.md)  
  - [管理 iOS 更新](software-updates-ios.md)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [管理使用者](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [管理群組和成員](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [疑難排解](help-desk-operators.md)

## <a name="next-step"></a>後續步驟
當您準備好開始使用 MDM 或 MAM 解決方案時，您可以逐步執行不同的步驟來設定 Intune、註冊裝置，並開始建立原則。 [Mobile device management for Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure) (Microsoft 365 的行動裝置管理) 也是絕佳的資源。
