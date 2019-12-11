---
title: 條件式存取案例
titleSuffix: Microsoft Intune
description: 了解通常如何針對以裝置為基礎與以應用程式為基礎的條件式存取使用 Intune 條件式存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b9795ca8a585fd926cc269d493760b37aa7666eb
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74051967"
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>搭配 Intune 使用條件式存取的常見方式為何？

[!INCLUDE [azure_portal](../includes/azure_portal.md)]


Intune 條件式存取有兩種類型：裝置型條件式存取和應用程式型條件式存取。 您需要設定相關的相容性原則以在您的組織推動條件式存取相容性。 條件式存取通常用於執行諸如以下的作業：允許或封鎖存取 Exchange、控制對網路的存取，或與 Mobile Threat Defense 解決方案整合。
 
此文章中的資訊可協助您了解如何使用 Intune 行動「裝置」  合規性功能和 Intune 行動「應用程式」  管理 (MAM) 功能。 

> [!NOTE]
> 條件式存取是 Azure Active Directory Premium 授權隨附的 Azure Active Directory 功能。 Intune 透過新增行動裝置合規姓與行動應用程式管理到解決方案以加強其功能。 從 *Intune* 存取的條件式存取節點，與從 *Azure AD* 存取的節點相同。  

## <a name="device-based-conditional-access"></a>以裝置為基礎的條件式存取

Intune 與 Azure Active Directory 會共同運作，以確保只有受控且符合規範的裝置可以存取電子郵件、Office 365 服務、軟體即服務 (SaaS) 應用程式與[內部部署應用程式](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) \(部分機器翻譯\)。 此外，您可以在 Azure Active Directory 中設定原則，只讓已加入網域的電腦或已在 Intune 中註冊的行動裝置存取 Office 365 服務。

Intune 提供裝置合規性政策功能來評估裝置的合規性狀態。 合規性狀態會回報給 Azure Active Directory，它會在使用者嘗試存取公司資源時，使用該狀態來強制執行於 Azure Active Directory 中建立的條件式存取原則。

適用於 Exchange Online 和其他 Office 365 產品的以裝置為基礎的條件式存取原則都是透過 [Azure 入口網站](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)來設定。  

- 深入了解[在 Azure Active Directory 中使用條件式存取來要求受控裝置](https://docs.microsoft.com/azure/active-directory/conditional-access/require-managed-devices) \(部分機器翻譯\)。

- 深入了解 [Intune 裝置相容性](device-compliance-get-started.md)。

- 深入了解 [Azure Active Directory 中條件式存取支援的瀏覽器](https://docs.microsoft.com/azure/active-directory/conditional-access/technical-reference#supported-browsers) \(部分機器翻譯\)。

> [!NOTE]
> 在 Android 裝置上，當您針對 SharePoint Online 啟用以裝置為基礎的存取，或針對 Exchange Online 啟用以瀏覽器為基礎的存取時，使用者都必須在註冊的裝置上啟用 [啟用瀏覽器存取]  選項，如下所示：
> 1. 啟動公司入口網站應用程式  。
> 2. 透過三個點 (...) 或硬體功能表按鈕，移至 [設定]  頁面。
> 3. 按下 **[啟用瀏覽器存取]** 按鈕。 
> 4. 在 Chrome 瀏覽器中，登出 Office 365 並重新啟動 Chrome。

### <a name="conditional-access-based-on-network-access-control"></a>以網路存取控制為依據的條件式存取

Intune 與 Cisco ISE、Aruba Clear Pass 和 Citrix NetScaler 等合作夥伴整合，以根據 Intune 註冊與裝置合規性狀態提供存取控制。

系統可以根據使用者所使用的裝置是否受控且符合 Intune 裝置合規性原則的規範，來允許或拒絕他們存取公司 Wi-Fi 或 VPN 資源。

- 深入了解 [NAC 與 Intune 整合](network-access-control-integrate.md)。

### <a name="conditional-access-based-on-device-risk"></a>以裝置風險為依據的條件式存取

Intune 已與 Mobile Threat Defense 廠商建立合作夥伴關係，可提供安全性解決方案來偵測行動裝置上的惡意程式碼、特洛伊木馬程式與其他威脅。

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Intune 與 Mobile Threat Defense 整合的運作方式

當行動裝置已安裝 Mobile Threat Defense 代理程式時，該代理程式就會在於行動裝置本身發現威脅時，將合規性狀態訊息傳回 Intune 進行回報。

Intune 與 Mobile Threat Defense 整合在以裝置風險為基礎的條件式存取決策中扮演重要因素。

- 深入了解 [Intune Mobile Threat Defense](mobile-threat-defense.md)。

### <a name="conditional-access-for-windows-pcs"></a>Windows 電腦的條件式存取

電腦的條件式存取提供適用於行動裝置的類似功能。 讓我們來談談當您使用 Intune 管理電腦時，可使用條件式存取的方式。

#### <a name="corporate-owned"></a>屬公司擁有

- **已加入內部部署 AD 網域：** 此選項通常是由已充分了解其目前透過 AD 群組原則或 System Center Configuration Manager 來管理其電腦之方式的組織所使用。

- **已加入 Azure AD 網域和 Intune 管理：** 此案例適用於想要成為雲端優先 (也就是主要使用雲端服務，並以減少使用內部部署基礎結構為目標) 或僅限雲端 (沒有內部部署基礎結構) 的組織。 Azure AD Join 適用於混合式環境，可讓您同時存取雲端與內部部署應用程式與資源。 裝置會加入 Azure AD 並向 Intune 註冊；這可在存取公司資源時作為條件式存取準則使用。

- **已加入 AD 網域和 System Center Configuration Manager：** 截至最新分支，除了作為加入網域的電腦之外，System Center Configuration Manager 還提供可評估特定合規性準則的條件式存取功能：

  - 電腦是否加密？

  - 是否已安裝反惡意程式碼？ 是否為最新狀態？

  - 裝置是否已進行越獄或破解？

#### <a name="bring-your-own-device-byod"></a>攜帶您自己的裝置 (BYOD)

- **Workplace Join 和 Intune 管理：** 使用者可以在這裡加入其個人裝置來存取公司資源和服務。 您可以使用「加入工作場所網路」並向 Intune MDM 註冊裝置，以接收裝置層級原則，這是評估條件式存取準則的另一個選項。

深入了解 [Azure Active Directory 中的裝置管理](https://docs.microsoft.com/azure/active-directory/devices/overview)。

## <a name="app-based-conditional-access"></a>以應用程式為基礎的條件式存取

Intune 與 Azure Active Directory 會共同運作，以確保只有受管理的應用程式可以存取公司電子郵件或其他 Office 365 服務。

- 深入了解[搭配 Intune 使用以應用程式為基礎的條件式存取](app-based-conditional-access-intune.md)。

### <a name="intune-conditional-access-for-exchange-on-premises"></a>適用於 Exchange 內部部署的 Intune 條件式存取

條件式存取可依據裝置合規性政策與註冊狀態，用來允許或封鎖對 **Exchange 內部部署**的存取。 當條件式存取與裝置合規性政策一起使用時，只有符合規範的裝置可以存取 Exchange 內部部署。

您可以設定條件式存取的進階設定，以進行更細微的控制，例如：

- 允許或封鎖特定平台。

- 立即封鎖不受 Intune 管理的裝置。

若已套用裝置合規性政策和條件式存取原則，即會檢查任何用來存取 Exchange 內部部署之裝置的合規性。

當裝置不符合所設定的條件時，系統就會逐步引導使用者進行註冊裝置的程序，以修正使裝置不符合規範的問題。

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Exchange 內部部署的條件式存取如何運作

適用於 Exchange 內部部署的條件式存取，與以 Azure 條件式存取為基礎之原則的運作方式不同。 您會安裝 Intune Exchange 內部部署連接器來直接與 Exchange 伺服器互動。 Intune Exchange Connector 會提取 Exchange Server 中現有的所有 Exchange Active Sync (EAS) 記錄，使 Intune 能夠取得這些 EAS 記錄，並將它們對應至 Intune 裝置記錄。 這些記錄是已註冊並且由 Intune 所辨識的裝置。 此程序會允許或封鎖電子郵件存取。

如果 EAS 記錄是新的，而 Intune 並不知道它，則 Intune 會發出指示 Exchange 伺服器封鎖電子郵件存取的 Cmdlet (發音為 "command-let")。 以下將更詳細地說明此程序的運作方式：

![透過 CA 流程圖的 Exchange 內部部署](./media/conditional-access-intune-common-ways-use/ca-intune-common-ways-1.png)

1. 使用者嘗試存取裝載於 Exchange 內部部署 2010 SP1 或更新版本上的公司電子郵件。

2. 如果裝置不受 Intune 管理，系統將會封鎖它對電子郵件的存取。 Intune 會將封鎖通知傳送至 EAS 用戶端。

3. EAS 會收到封鎖通知，將該裝置移到隔離，並傳送含有補救步驟的隔離電子郵件，其中包含可供使用者註冊其裝置的連結。

4. Workplace Join 程序即會進行，這是讓 Intune 管理裝置的第一個步驟。

5. 讓裝置向 Intune 註冊。

6. Intune 會將 EAS 記錄對應至裝置記錄，並儲存裝置合規性狀態。

7. EAS 用戶端識別碼已由 Azure AD 裝置註冊程序註冊，這會在 Intune 裝置記錄與 EAS 用戶端識別碼之間建立關聯性。

8. Azure AD 裝置註冊會儲存裝置狀態資訊。

9. 如果使用者符合條件式存取原則，Intune 會透過 Intune Exchange Connector 發出 Cmdlet，允許信箱進行同步處理。

10. Exchange Server 會傳送通知給 EAS 用戶端，讓使用者可以存取電子郵件。


#### <a name="whats-the-intune-role"></a>Intune 扮演何種角色？

Intune 會評估及管理裝置狀態。

#### <a name="whats-the-exchange-server-role"></a>Exchange Server 扮演何種角色？

Exchange Server 提供 API 和基礎結構，以便將裝置移到隔離。

> [!IMPORTANT]
> 請記住，使用裝置的使用者必須被指派合規性設定檔與 Intune 授權，以便評估裝置的合規性。 若使用者未獲部署合規性政策，便會將其裝視為符合規範，而且會對其套用沒有存取權限的限制。

## <a name="next-steps"></a>後續步驟

[如何在 Azure Active Directory 中設定條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[設定以應用程式為基礎的條件式存取原則](app-based-conditional-access-intune-create.md)

[如何使用 Intune 安裝內部部署 Exchange Connector](exchange-connector-install.md)。

[如何建立 Exchange 內部部署的條件式存取原則](conditional-access-exchange-create.md)
