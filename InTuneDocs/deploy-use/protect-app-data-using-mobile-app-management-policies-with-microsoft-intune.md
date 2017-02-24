---
title: "使用 MAM 原則保護應用程式資料 | Microsoft Docs"
description: "本主題說明行動應用程式管理原則如何協助您保護公司資料、避免資料遺失，以及區隔個人與工作的資訊。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: fbb41a8cf6fada76b72213b8cb04fdc0428515e9
ms.openlocfilehash: 651899219458f799e26ed7957ccef97d7ae2af09


---

# <a name="protect-app-data-using-app-protection-policies-with-microsoft-intune"></a>使用 Microsoft Intune 的應用程式保護原則保護應用程式資料

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="how-you-can-protect-app-data"></a>如何保護應用程式資料
您的員工使用行動裝置處理公私事務。 在您確保員工生產力的同時，也要防止故意和不小心的資料外洩。  此外，當員工使用並非由您管理的裝置來存取公司資料時，您會希望可以保護這些公司資料。

您可以使用 Intune 應用程式保護原則來協助保護您公司的資料。 因為 Intune 應用程式保護原則可以**獨立於任何行動裝置管理 (MDM) 解決方案之外**，所以無論裝置是否在裝置管理解決方案中註冊，都可以使用 MAM 來保護公司資料。 您可以實作**應用程式層級原則**，以限制存取公司資源，並將資料保留在 IT 部門範疇內。

您可以針對在下列裝置上執行之應用程式設定應用程式保護原則：

-   **在 Microsoft Intune 中註冊︰**此類別中的裝置通常是公司所擁有的裝置。

-   **在註冊協力廠商 MDM 解決方案中註冊：**此類別中的裝置通常是公司擁有的裝置。

  > [!NOTE]
  > 不建議您使用應用程式保護原則搭配協力廠商行動裝置應用程式管理或安全容器解決方案。

-   **未在任何 MDM 解決方案中註冊︰**此類別中的裝置通常是員工所擁有的裝置，且沒有在 Intune 或其他 MDM 解決方案中受到管理或註冊。

> [!IMPORTANT]
> 您可以為連線到 Office 365 服務的 Office mobile apps 建立應用程式保護原則。 應用程式保護原則不支援連線到內部部署 Exchange、商務用 Skype 或 SharePoint 服務的應用程式。

## <a name="benefits-of-using-app-protection-policies"></a>使用應用程式保護原則的優點

-   **它們可以協助於應用程式層級保護您的公司資料。** 因為行動應用程式管理不需要裝置管理，您可以同時在受管理與未受管理的裝置上保護公司資料。 管理的重心是使用者身分識別，不需要管理裝置。

-   **使用者生產力不受影響，當您在個人領域內使用應用程式時不套用原則。** 原則只會套用在工作內容上，所以您能夠在不碰到個人資料的情況下保護公司資料。

搭配應用程式保護原則使用 MDM 還有其他優點，不論是否同時搭配 MDM，公司都可以使用 MAM。 例如，員工可能使用公司核發的手機，也可能使用個人平板電腦。 在此情況下，公司的手機會在 MDM 中註冊，並受到應用程式保護原則的保護，而個人裝置只會受到應用程式保護原則的保護。

- **MDM 確保裝置受到保護。** 例如，您可以要求存取裝置的 PIN，或者將受管理的應用程式部署到裝置。 也可以透過 MDM 解決方案將應用程式部署到裝置，取得對應用程式管理的更多控制。

- **應用程式保護原則可確保應用程式層保護完全就位**。 例如，您可以設定如下的原則：在工作環境中需要有 PIN 才能開啟應用程式、禁止資料在應用程式之間共用，以及禁止公司應用程式資料儲存到個人存放區位置。

## <a name="devices-that-support-mam"></a>支援 MAM 的裝置
下列平台目前支援應用程式保護原則：
-   iOS 8.1 或更新版本
-   Android 4 或更新版本

>[!NOTE]
>在沒有註冊的情況下，MAM 中不支援 Windows 裝置。 不過，當您將 Windows 10 裝置註冊 Intune 時，即可使用 Windows 資訊保護，以提供類似的功能。 如需詳細資訊，請參閱[使用 Windows 資訊保護 (WIP) 保護您的企業資料](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)。


##  <a name="how-app-protection-policies-protect-app-data"></a>應用程式保護原則如何保護應用程式資料

###  <a name="apps-without-app-protection-policies"></a>沒有應用程式保護原則的應用程式

![此圖顯示在未設定應用程式保護原則的情況下，資料可以在應用程式之間自由移動](../media/Apps_without_MAM_policies.png)

當您在沒有條件限制下使用應用程式時，公司和個人資料會互相混合。 公司資料最終可能會存放在類似個人存放區的位置，或者傳送至您權限範圍以外的應用程式，而導致資料遺失。 圖中的箭號顯示資料在應用程式 (公司和個人) 之間無限制移動和移至儲存體位置。

### <a name="data-protection-with-app-protection-policies"></a>使用應用程式保護原則保護資料

![此圖顯示套用應用程式保護原則時如何保護公司資料](../media/Apps_with_mobile_app_policies.png)

您可以使用應用程式保護原則禁止將公司資料儲存到裝置的本機儲存體，以及限制資料不得移至不受應用程式保護原則保護的其他應用程式。 應用程式保護原則設定包括︰
- 資料重新配置原則，例如 [不可進行另存新檔]、[限制剪下、複製與貼上]。
- 存取原則設定，例如 [需要簡單 PIN 碼才可存取]、[禁止受管理的應用程式在經過破解或刷機的裝置上執行]。

### <a name="data-protection-with-app-protection-on-devices-that-are-managed-by-a-mdm-solution"></a>在 MDM 解決方案管理的裝置上使用應用程式保護來保護資料

![此圖顯示應用程式保護原則在「攜帶您自己的裝置」(BYOD) 裝置上的運作方式](../media/MAM_BYOD_November.png)

**在 MDM 解決方案中註冊的裝置**：上圖顯示 MDM 與應用程式保護原則共同提供的保護層。

MDM 解決方案：

-   註冊裝置。

-   將應用程式部署到裝置。

-   提供持續的裝置合規性和管理。

**應用程式保護原則藉由下列方式提升價值︰**

-   協助保護公司資料不外洩給消費性應用程式和服務。

-   對行動應用程式套用限制 (另存新檔、剪貼簿、PIN 等等)。

-   抹除應用程式中的公司資料，但不從裝置移除這些應用程式。


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>在未註冊的裝置上使用應用程式保護原則保護資料

![此圖顯示應用程式保護原則在受管理裝置上的運作方式](../media/MAM_ManagedDevices_November.png)

上圖說明資料保護原則在沒有 MDM 的情況，於應用程式層級的運作方式。

對於未在任何 MDM 解決方案中註冊的 BYOD 裝置，應用程式保護原則可在應用程式層級協助保護公司資料。

不過，有一些限制需要注意：

-   您無法將應用程式部署到裝置。 使用者必須從存放區取得應用程式。

-   您無法在這些裝置上佈建憑證設定檔。

-   您無法在這些裝置上設定公司 Wi-Fi 與 VPN 設定。


## <a name="multi-identity"></a>多重身分識別

當應用程式保護原則只有在工作環境中使用應用程式時才會套用，支援多重身分識別的應用程式讓您能夠使用不同的帳戶 (工作和個人) 來存取相同的應用程式。  

例如，當使用者使用其工作帳戶啟動 OneDrive 應用程式，他們無法將檔案移動至個人存放區位置。 不過，當使用者以個人帳戶使用 OneDrive 時，他們可以從個人 OneDrive 複製並移動資料，而沒有任何限制。  

所有的 Office 行動裝置應用程式都支援多重身分存取。

##  <a name="next-steps"></a>後續步驟
- [準備好設定應用程式保護原則](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

- [使用 Microsoft Intune 建立及部署應用程式保護原則](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Feb17_HO2-->


