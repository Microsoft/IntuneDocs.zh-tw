---
# required metadata

title: 使用行動應用程式管理原則保護應用程式資料 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: joglocke
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用行動應用程式管理原則搭配 Microsoft Intune 保護應用程式資料

## 如何保護應用程式資料
您的員工使用行動裝置處理公私事務。  確保員工生產力的同時，也要防止故意和不小心的資料外洩。  此外，即使您並不管理裝置，您也想要保護使用裝置所存取的公司資料。

您可以使用行動裝置應用程式管理 (MAM) 原則來協助保護公司的資料。 因為 Intune MAM 原則可獨立於任何行動裝置管理 (MDM) 解決方案之外使用，不論是否在裝置管理解決方案中註冊裝置，都可以用它來保護公司的資料。 您可以實作**應用程式層級原則**，以限制存取公司資源，並將資料保留在 IT 部門範疇內。

MAM 原則支援下列裝置上執行的應用程式︰

-   在 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 中**管理和註冊的裝置**。 此類別中的裝置通常是公司管理的裝置。

  > [!IMPORTANT]
  > 如果您使用 Intune 管理 iOS 和 Android 裝置，您可以為連接至 Office 365 服務的 Office 行動應用程式建立行動應用程式管理原則。 連線到內部部署 Exchange 或 SharePoint 服務的應用程式不支援 MAM 原則。

-   **在協力廠商行動裝置管理解決方案中管理和註冊的裝置**。   此類別中的裝置通常是公司管理的裝置。

  > [!NOTE]行動裝置應用程式管理原則不應與協力廠商行動裝置應用程式管理或安全容器解決方案一起使用。

-   **未受管理的裝置**。  此類別中的裝置通常是不在 Intune 或其他 MDM 解決方案中管理或註冊的員工個人裝置。

**使用 MAM 原則的重要優點為：**

-   在應用程式層級保護公司資料。  因為行動裝置應用程式管理不需要裝置管理，所以您可以保護受管理和不受管理裝置上的公司資料。 管理的重心是使用者身分識別，不需要管理裝置。

-   使用者生產力不受影響，在個人領域內使用應用程式時不套用原則。  原則只會套用在公務內容上，所以您能夠在不碰到個人資料的情況下保護公司資料。

搭配 MAM 原則使用 MDM 還有其他優點，不論是否同時搭配 MDM，公司都可以使用 MAM。 例如，員工可能使用公司以及個人平板電腦核可的電話。  在此情況下，公司電話在 MDM 註冊並受 MAM 原則保護，而個人裝置只受到 MAM 原則保護。

- **MDM 確保裝置受到保護**。  例如，您可以要求存取裝置的 PIN，或者將受管理的應用程式部署到裝置。 也可以透過 MDM 解決方案將應用程式部署到裝置，取得對應用程式管理的更多控制。

- **MAM 原則確保應用程式層保護就定位**。 例如，如果資料可以在應用程式間共用，您可以要求在公務內容中開啟應用程式的 PIN，或防止公司應用程式資料儲存到個人的存放位置。


### 下列平台目前支援 MAM：
-   iOS 8.1 或更新版本

-   Android 4 或更新版本

目前不支援 Windows 裝置。
##  MAM 原則如何保護應用程式資料

####  使用 MAM 原則的應用程式：

![此圖顯示沒有 MAM 原則時可在應用程式之間自由移動資料](../media/Apps_without_MAM_policies.png)

在沒有條件限制下使用應用程式時，公司和個人資料會互相混合。  公司資料最終可能放在個人存放裝置或傳送到外部應用程式，導致資料外洩。 圖中的箭號顯示資料在應用程式 (公司和個人) 之間無限制移動和移至儲存體位置。

### 不使用 MAM 原則的資料保護：

![此圖顯示套用 MAM 原則時如何保護公司資料 ](../media/Apps_with_mobile_app_policies.png)

您可以使用 MAM 原則來防止公司資料儲存至裝置的本機儲存體，並禁止資料移至未受 MAM 原則保護的其他應用程式。 MAM 原則設定包括：
- 資料重新配置原則，例如 [不可進行另存新檔]、[限制剪下、複製與貼上]。
- 存取原則設定，例如 [需要簡單 PIN 碼才可存取]、[禁止受管理的應用程式在經過破解或刷機的裝置上執行]。

### 在 MDM 解決方案所管理的裝置上使用 MAM 原則保護資料︰

![此圖顯示 MAM 原則在 BYOD 裝置上的運作方式](../media/MAM_BYOD_November.png)

**在 MDM 解決方案中註冊的裝置**-

此圖顯示 MDM 和 MAM 原則一起提供的多層保護。

MDM 解決方案：

-   註冊裝置

-   將應用程式部署至裝置

-   提供持續的裝置相容性和管理

**MAM 原則加入值的方法：**

-   協助保護公司資料不外洩給消費性應用程式和服務

-   對行動應用程式套用限制 (另存新檔、剪貼簿、PIN 等等)

-   抹除應用程式中的公司資料，但不從裝置移除這些應用程式


### 在未註冊的裝置上使用 MAM 原則保護資料

![此圖顯示 MAM 原則在受管理裝置上的運作方式](../media/MAM_ManagedDevices_November.png)

上圖顯示不使用 MDM 時資料保護原則在應用程式層級上的運作方式。

對於未在任何 MDM 解決方案中註冊的 BYOD 裝置，MAM 原則可以協助在應用程式層級保護公司資料。
但有一些限制需要注意，例如：

-   您無法將應用程式部署到裝置。  使用者必須從存放區取得應用程式。

-   您無法在這些裝置上佈建憑證設定檔。

-   您無法在這些裝置上佈建公司 Wi-Fi 和 VPN 設定。


## 多重身分識別

在工作環境中使用應用程式且套用 MAM 原則時，多重身分識別讓您能夠使用不同的帳戶 (工作和個人) 來存取相同的應用程式。  

例如，當使用者使用工作帳戶啟動 OneDrive 應用程式時，無法將檔案移至個人儲存體位置。 不過，當使用者以個人帳戶使用 OneDrive 時，他們可以從個人 OneDrive 複製並移動資料，而沒有任何限制。  

如需使用與 MAM 原則相關聯的應用程式時有何體驗，以及支援多重身分識別的應用程式如何只能在工作環境中套用 MAM 原則的詳細說明，請參閱[搭配多重身分識別支援使用應用程式](end-user-experience-for-mam-enabled-apps-with-microsoft-intune.md#using-apps-with-multi-identity-support)

所有的 Office 行動裝置應用程式都支援多重身分識別。

##  後續步驟
[準備設定行動應用程式管理原則](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

[使用 Microsoft Intune 建立及部署行動應用程式管理原則](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->


