---
title: "Microsoft Intune 的條件式存取"
titlesuffix: 
description: "了解裝置型和應用程式型條件式存取平常如何使用 Intune 條件式存取。"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9c34e6e2891769d64885d364f05dbedaa1fb7d57
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>常見的 Intune 條件式存取使用方式為何？

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 條件式存取有兩種類型：裝置型條件式存取和應用程式型條件式存取。 您需要設定相關的相容性原則以在您的組織推動條件式存取相容性。 條件式存取通常用於執行以下作業：允許或封鎖存取 Exchange 內部部署、控制存取網路，或與 Mobile Threat Defense 解決方案整合等等。

下列資訊可協助您了解如何使用 Intune 行動裝置性功能和 Intune 行動應用程式管理 (MAM) 功能。 

## <a name="device-based-conditional-access"></a>裝置型條件式存取

Intune 與 Azure Active Directory 會共同運作，以確保只有受管理且符合規範的裝置可以存取電子郵件、Office 365 服務、軟體即服務 (SaaS) 應用程式及[內部部署應用程式](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)。 此外，您可以在 Azure Active Directory 中設定原則，只讓加入網域的電腦或已在 Intune 中註冊的行動裝置存取 Office 365 服務。

Intune 提供裝置合規性政策功能來評估裝置的合規性狀態。 合規性狀態會回報給 Azure Active Directory，在使用者嘗試存取公司資源時，使用它來強制執行 Azure Active Directory 中所建立的條件式存取原則。

適用於 Exchange Online 和其他 Office 365 產品的裝置型條件式存取原則均透過 [Azure 入口網站](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)來設定。

-   深入了解 [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。

-   深入了解 [Intune 裝置相容性](device-compliance.md)。

-   深入了解[透過 Intune 使用條件式存取來保護電子郵件、Office 365 和其他服務](https://docs.microsoft.com/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)。

### <a name="conditional-access-for-exchange-on-premises"></a>Exchange 內部部署的條件式存取

條件式存取可依據裝置合規性政策與註冊狀態，用來允許或封鎖對 **Exchange 內部部署**的存取。 當條件式存取與裝置合規性政策一起使用時，只有符合規範的裝置可以存取 Exchange 內部部署。

您可以設定條件式存取的進階設定，以進行更細微的控制，例如：

-   允許或封鎖特定平台。

-   立即封鎖不受 Intune 管理的裝置。

若已套用裝置合規性政策和條件式存取原則，即會檢查任何用來存取 Exchange 內部部署之裝置的合規性。

若裝置不符合條件設定，將逐步引導使用者進行註冊裝置的程序，以修正使裝置不相容的問題。

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Exchange 內部部署的條件式存取如何運作

Intune Exchange Connector 會提取 Exchange Server 中現有的所有 Exchange Active Sync (EAS) 記錄，使 Intune 能夠取得這些 EAS 記錄，並將它們對應至 Intune 裝置記錄。 這些記錄是已註冊並且由 Intune 所辨識的裝置。 此程序會允許或封鎖電子郵件存取。

如果 EAS 記錄是全新的，而 Intune 並不知道它，則 Intune 會發出封鎖存取電子郵件的 Cmdlet。 以下是關於此程序如何運作的更詳細說明：

![透過 CA 流程圖的 Exchange 內部部署](./media/ca-intune-common-ways-1.png)

1.  使用者嘗試存取裝載於 Exchange 內部部署 2010 SP1 或更新版本上的公司電子郵件。

2.  如果裝置不受 Intune 管理，系統將會封鎖它對電子郵件的存取。 Intune 會將封鎖通知傳送至 EAS 用戶端。

3.  EAS 會收到封鎖通知，將該裝置移到隔離，並傳送含有補救步驟的隔離電子郵件，其中包含可供使用者註冊其裝置的連結。

4.  Workplace Join 程序即會進行，這是讓 Intune 管理裝置的第一個步驟。

5.  讓裝置向 Intune 註冊。

6.  Intune 會將 EAS 記錄對應至裝置記錄，並儲存裝置合規性狀態。

7.  EAS 用戶端識別碼已由 Azure AD 裝置註冊程序註冊，這會在 Intune 裝置記錄與 EAS 用戶端識別碼之間建立關聯性。

8.  Azure AD 裝置註冊會儲存裝置狀態資訊。

9.  如果使用者符合條件式存取原則，Intune 會透過 Intune Exchange Connector 發出 Cmdlet，允許信箱進行同步。

10. Exchange Server 會傳送通知給 EAS 用戶端，讓使用者可以存取電子郵件。

#### <a name="whats-the-intune-role"></a>Intune 扮演何種角色？

Intune 會評估和管理裝置狀態。

#### <a name="whats-the-exchange-server-role"></a>Exchange Server 扮演何種角色？

Exchange Server 提供 API 和基礎結構，以將裝置移到它的隔離。

> [!IMPORTANT]
> 請注意，裝置使用者必須具備合規性設定檔指派，該裝置才能接受合規性評估。 若使用者未獲部署合規性政策，便會將其裝視為符合規範，而且會對其套用沒有存取權限的限制。

### <a name="conditional-access-based-on-network-access-control"></a>以網路存取控制為依據的條件式存取

Intune 已與夥伴 (例如 Cisco ISE、Aruba Clear Pass 及 Citrix NetScaler) 整合，以根據 Intune 註冊與裝置合規性狀態提供存取控制。

當使用者嘗試存取公司 Wi-Fi 或 VPN 資源時，可根據裝置是否受到管理及是否符合 Intune 裝置合規性政策的規範來允許或拒絕使用者存取。

-   深入了解 [NAC 與 Intune 整合](network-access-control-integrate.md)。

### <a name="conditional-access-based-on-device-risk"></a>以裝置風險為依據的條件式存取

Intune 已與 Mobile Threat Defense 廠商建立夥伴關係，可提供安全性解決方案來偵測行動裝置上的惡意程式碼、特洛伊程式和其他威脅。

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Intune 與 Mobile Threat Defense 整合的運作方式

當行動裝置已安裝 Mobile Threat Defense 代理程式時，該代理程式就可將合規性狀態訊息傳回 Intune，以回報是否已在行動裝置本身發現威脅。

Intune 與 Mobile Threat Defense 整合在以裝置風險為依據的條件式存取決策中扮演一個重要因素。

-   深入了解 [Intune Mobile Threat Defense](https://docs.microsoft.com/intune-classic/deploy-use/mobile-threat-defense)。

### <a name="conditional-access-for-windows-pcs"></a>Windows 電腦的條件式存取

電腦的條件式存取提供適用於行動裝置的類似功能。 讓我們來談談當您使用 Intune 管理電腦時，可使用條件式存取的方式。

#### <a name="corporate-owned"></a>屬公司擁有

-   **已加入內部部署 AD 網域：**對組織而言，這是最常見的條件式存取部署選項，原因在於他們已經透過 AD 群組原則和/或使用 System Center Configuration Manager 管理其電腦。

-   **已加入 Azure AD 網域和 Intune 管理：**這種情況通常適用於「選擇您自己的裝置」(CYOD)，以及使用膝上型電腦漫遊的情況，而其中的這些裝置很少會連線到公司網路。 裝置會加入 Azure AD 並向 Intune 註冊，以移除內部部署 AD 與網域控制站上的任何相依性。 這可在存取公司資源時，用來做為條件式存取準則。

-   **已加入 AD 網域和 System Center Configuration Manager：**截至最新分支，除了作為加入網域的電腦之外，System Center Configuration Manager 還提供可評估特定合規性準則的條件式存取功能：

    -   電腦是否加密？

    -   是否有安裝惡意程式碼？ 是否為最新狀態？

    -   裝置是否已進行越獄或破解？

#### <a name="bring-your-own-device-byod"></a>攜帶您自己的裝置 (BYOD)

-   **Workplace Join 和 Intune 管理：**使用者可以在這裡加入其個人裝置來存取公司資源和服務。 您可以使用 Workplace Join，並向 Intune 註冊裝置，以接收裝置層級原則，這也是評估條件式存取準則的另一個選項。

## <a name="app-based-conditional-access"></a>以應用程式為基礎的條件式存取

Intune 與 Azure Active Directory 會共同運作，以確保只有受管理的應用程式可以存取公司電子郵件或其他 Office 365 服務。

-   深入了解[搭配 Intune 使用以應用程式為基礎的條件式存取](app-based-conditional-access-intune.md)。

## <a name="next-steps"></a>接下來的步驟

[如何在 Azure Active Directory 中設定條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[如何使用 Intune 安裝內部部署 Exchange Connector](https://docs.microsoft.com/intune/exchange-connector-install)。

[如何建立 Exchange 內部部署的條件存取原則](conditional-access-exchange-create.md)
