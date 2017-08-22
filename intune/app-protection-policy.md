---
title: "什麼是應用程式保護原則？"
titleSuffix: Intune on Azure
description: "本主題可讓您了解如何使用 Microsoft Intune 應用程式保護原則來保護您的公司資料。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 01/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5a776de8a27c5fc7b1c472df067610ba7140b07b
ms.sourcegitcommit: 45204e0fb8cb4cce449e65f2f1d7bb6f6ac4ccf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2017
---
# <a name="what-are-app-protection-policies"></a>什麼是應用程式保護原則？


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune 應用程式保護原則可協助保護公司資料，避免資料遺失。

## <a name="how-you-can-protect-app-data"></a>如何保護應用程式資料
您的員工使用行動裝置處理公私事務。  確保員工生產力的同時，也要防止故意和不小心的資料外洩。  此外，即使您並不管理裝置，您也想要保護使用裝置所存取的公司資料。

您可以使用 Intune 應用程式保護原則來協助保護您公司的資料。 因為 Intune 原則可**自外於任何行動裝置管理 (MDM) 解決方案之外**，所以無論裝置是否在裝置管理解決方案中註冊，都可以這些原則來保護公司資料。 您可以實作**應用程式層級原則**，以限制存取公司資源，並將資料保留在 IT 部門範疇內。

裝置上執行可以設定應用程式保護原則的應用程式包括：

- **在 Microsoft Intune 中註冊︰**此類別中的裝置通常是公司所擁有的裝置。

-   **在協力廠商的行動裝置管理 (MDM) 解決方案中註冊︰**此類別中的裝置通常是公司所擁有的裝置。

  > [!NOTE]
  > 行動裝置應用程式管理原則不應搭配使用協力廠商的行動裝置應用程式管理或安全容器解決方案。

-   **未註冊任何行動裝置管理解決方案︰**此類別中的裝置通常是員工所擁有的裝置，且沒有在 Intune 或其他 MDM 解決方案中受到管理或註冊。

> [!IMPORTANT]
> 您可以為連接至 Office 365 服務的 Office 行動應用程式建立行動應用程式管理原則。 應用程式保護原則不支援連線到內部部署 Exchange、商務用 Skype 或 SharePoint 服務的應用程式。

**使用應用程式保護原則的重要優點包括：**

-   在應用程式層級保護公司資料。  因為行動裝置應用程式管理不需要裝置管理，所以您可以保護受管理和不受管理裝置上的公司資料。 管理的重心是使用者身分識別，不需要管理裝置。

-   使用者生產力不受影響，在個人領域內使用應用程式時不套用原則。  原則只會套用在公務內容上，所以您能夠在不碰到個人資料的情況下保護公司資料。

並用 MDM 與應用程式保護原則還有其他多項優點，而且公司可以同時在使用或不使用 MDM 的狀況下使用應用程式保護原則。 例如，員工可能使用公司核發的手機，也可以使用及個人的平板電腦。  在此情況下，公司的手機會在 MDM 中註冊，並受到 MAM 原則的保護，而個人裝置只會受到 MAM 原則的保護。

- **MDM 確保裝置受到保護**。  例如，您可以要求存取裝置的 PIN，或者將受管理的應用程式部署到裝置。 也可以透過 MDM 解決方案將應用程式部署到裝置，取得對應用程式管理的更多控制。

- **應用程式保護原則可確保應用程式層保護完全就位**。 例如，如果資料可以在應用程式間共用，您可以要求在公務內容中開啟應用程式的 PIN，或防止公司應用程式資料儲存到個人的存放位置。


### <a name="supported-platforms-for-app-protection-polices"></a>支援應用程式保護原則的平台
-   iOS 8.1 或更新版本

-   Android 4 或更新版本

目前不支援 Windows 裝置。 不過，當您將 Windows 10 裝置註冊 Intune 時，即可使用 Windows 資訊保護，以提供類似的功能。 如需詳細資訊，請參閱[使用 Windows 資訊保護 (WIP) 保護您的企業資料](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)。
##  <a name="how-app-protection-policies-protect-app-data"></a>應用程式保護原則如何保護應用程式資料

####  <a name="apps-without-app-protection-policies"></a>沒有應用程式保護原則的應用程式

![此圖顯示在沒有設定應用程式保護原則的情況下，資料可以在應用程式之間自由移動](./media/apps-without-protection-policies.png)

在沒有條件限制下使用應用程式時，公司和個人資料會互相混合。  公司資料最終可能放在個人存放裝置或傳送到外部應用程式，導致資料外洩。 圖中的箭號顯示資料在應用程式 (公司和個人) 之間無限制移動和移至儲存體位置。

### <a name="data-protection-with-app-protection-policies"></a>使用應用程式保護原則保護資料

![此圖顯示套用應用程式保護原則後公司資料受到保護的情況 ](./media/apps-with-protection-policies.png)


您可以使用應用程式保護原則禁止將公司資料儲存到裝置的本機儲存體，以及限制資料不得移至不受應用程式保護原則保護的其他應用程式。 應用程式保護原則設定包括︰
- 資料重新配置原則，例如 [不可進行另存新檔]、[限制剪下、複製與貼上]。
- 存取原則設定，例如 [需要簡單 PIN 碼才可存取]、[禁止受管理的應用程式在經過破解或刷機的裝置上執行]。

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mdm-solution"></a>在 MDM 解決方案管理的裝置上使用應用程式保護原則保護資料

![此圖顯示應用程式保護原則在 BYOD 裝置上的運作方式](./media/app-protection-policies-with-mdm.png)

**在 MDM 解決方案中註冊的裝置**-

上列圖例顯示 MDM 與應用程式保護原則共同提供的多層保護。

MDM 解決方案：

-   註冊裝置

-   將應用程式部署至裝置

-   提供持續的裝置合規性和管理

**應用程式保護原則藉由下列方式提升價值︰**

-   協助保護公司資料不外洩給消費性應用程式和服務

-   對行動應用程式套用限制 (另存新檔、剪貼簿、PIN 等等)

-   抹除應用程式中的公司資料，但不從裝置移除這些應用程式


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>在未註冊的裝置上使用資料保護原則保護資料

![此圖顯示應用程式保護原則在受管理裝置上的運作方式](./media/app-protection-policies-without-mdm.png)

上圖顯示不使用 MDM 時資料保護原則在應用程式層級上的運作方式。

對於未在任何 MDM 解決方案中註冊的 BYOD 裝置，應用程式保護原則可在應用程式層級保護公司資料。
但有一些限制需要注意，例如：

-   您無法將應用程式部署到裝置。  使用者必須從存放區取得應用程式。

-   您無法在這些裝置上佈建憑證設定檔。

-   您無法在這些裝置上佈建公司 Wi-Fi 和 VPN 設定。


## <a name="multi-identity"></a>多重身分識別

當應用程式保護原則只有在工作環境中使用應用程式時才會套用，支援多重身分識別的應用程式讓您能夠使用不同的帳戶 (工作和個人) 來存取相同的應用程式。

例如，當使用者使用其工作帳戶啟動 OneDrive 應用程式，他們無法將檔案移動至個人存放區位置。 不過，當使用者以個人帳戶使用 OneDrive 時，他們可以從個人 OneDrive 複製並移動資料，而沒有任何限制。

- 深入了解支援 Intune 的 [MAM 和多重身分識別](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的應用程式。

##  <a name="next-steps"></a>後續步驟

[如何使用 Microsoft Intune 建立及部署應用程式保護原則](app-protection-policies.md)
