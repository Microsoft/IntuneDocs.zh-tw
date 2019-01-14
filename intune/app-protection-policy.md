---
title: 什麼是應用程式保護原則？
titleSuffix: Microsoft Intune
description: 了解 Microsoft Intune 應用程式保護原則如何協助保護公司資料，避免資料遺失。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: 49ecdebc2777112ce8c8c97af1f98b3c12b200e1
ms.sourcegitcommit: 0dc977795ff80abb6a3b989ca633cba410f06c64
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54006279"
---
# <a name="what-are-app-protection-policies"></a>什麼是應用程式保護原則？


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune 應用程式保護原則可協助保護公司資料，避免資料遺失。

## <a name="how-you-can-protect-app-data"></a>如何保護應用程式資料
您的員工使用行動裝置處理公私事務。 確保員工生產力的同時，想要防止故意和不小心的資料外洩。 您還想要保護從您非受控裝置存取的公司資料。

您可以使用 Intune 應用程式保護原則，而**不受任何行動裝置管理 (MDM) 解決方案影響**。 不論是否在裝置管理解決方案中註冊裝置，這項獨立性都可協助您保護貴公司的資料。 您可以實作**應用程式層級原則**，以限制存取公司資源，並將資料保留在 IT 部門範疇內。

可為裝置上執行的應用程式所設定應用程式保護原則，包括下列：

- **在 Microsoft Intune 中註冊：** 這些裝置通常是公司所擁有的裝置。

- **在協力廠商的行動裝置管理 (MDM) 解決方案中註冊：** 這些裝置通常是公司所擁有的裝置。

  > [!NOTE]
  > 行動應用程式管理原則不應搭配使用協力廠商的行動應用程式管理或安全容器解決方案。

- **未在任何行動裝置管理解決方案中註冊：** 這些裝置通常是員工所擁有的裝置，且沒有在 Intune 或其他 MDM 解決方案中受控或註冊。

> [!IMPORTANT]
> 您可以為連接至 Office 365 服務的 Office 行動應用程式建立行動應用程式管理原則。 您也可以透過建立適用於 iOS 版 Outlook 以及已啟用混合式新式驗證的 Android 的 Intune 應用程式保護原則，來保護對 Exchange 內部部署信箱的存取。 開始使用此功能之前，請確定您符合 [iOS 版和 Android 版 Outlook 的需求](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx)。 連線到內部部署 Exchange 或 SharePoint 服務的其他應用程式不支援應用程式保護原則。

**使用應用程式保護原則的重要優點包括：**

-   在應用程式層級保護公司資料。 因為行動應用程式管理不需要裝置管理，您可以同時在受控與非受控的裝置上保護公司資料。 管理的重心是使用者身分識別，不需要管理裝置。

-   終端使用者生產力不受影響，且在個人環境內使用應用程式時，不會套用原則。 原則只會套用在工作內容上，所以您能夠在不碰到個人資料的情況下保護公司資料。

搭配使用 MDM 與應用程式保護原則還有其他多項優點，且公司可以在使用或不使用 MDM 的狀況下使用應用程式保護原則。 例如，請考慮使用公司所核發手機和自己個人平板電腦的員工。 公司的手機會在 MDM 中註冊，並受到應用程式保護原則的保護，而個人裝置只會受到應用程式保護原則的保護。

- **MDM 確保裝置受到保護**。 例如，您可以要求存取裝置的 PIN，或者將受管理的應用程式部署到裝置。 也可以透過 MDM 解決方案將應用程式部署到裝置，取得對應用程式管理的更多控制。

- **應用程式保護原則可確保應用程式層保護完全就位**。 例如，您可以：
  - 需要 PIN 才能在工作環境中開啟應用程式 
  - 控制應用程式之間的資料共用 
  - 防止將公司應用程式資料儲存到個人儲存位置


### <a name="supported-platforms-for-app-protection-policies"></a>支援應用程式保護原則的平台
Intune 應用程式保護原則平台支援與 Office 行動應用程式平台支援，在針對 Android 和 iOS 上是一致的。 如需詳細資料，請參閱 [Office 系統需求](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg)的**行動應用程式**一節。

目前不支援 Windows 裝置。 不過，您可以使用 Windows 資訊保護，其能提供類似的功能。 如需詳細資訊，請參閱[使用 Windows 資訊保護 (WIP) 保護您的企業資料](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)。


## <a name="how-app-protection-policies-protect-app-data"></a>應用程式保護原則如何保護應用程式資料

#### <a name="apps-without-app-protection-policies"></a>沒有應用程式保護原則的應用程式

![沒有原則時在應用程式之間移動資料的概念影像](./media/apps-without-protection-policies.png)

在沒有條件限制下使用應用程式時，公司和個人資料會互相混合。 公司資料最終會放在個人儲存空間等位置或傳送到範圍外的應用程式，進而導致資料外洩。 上圖中的箭號顯示資料在公司與個人應用程式之間無限制地移動和移至儲存位置。


### <a name="data-protection-with-app-protection-policies"></a>使用應用程式保護原則保護資料

![顯示公司資料正受原則保護的概念影像](./media/apps-with-protection-policies.png)


您可以使用應用程式保護原則來防止公司資料儲存到裝置的本機儲存體。 您也可以限制將資料移到其他未受應用程式保護原則保護的應用程式。 應用程式保護原則設定包括︰
- 資料重新配置原則，例如 [不可進行另存新檔] 和 [限制剪下、複製與貼上]。
- 存取原則設定，例如 [需要簡單 PIN 碼才可存取]、[禁止受控應用程式在經 JB 或 Root 破解的裝置上執行]。

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mobile-device-management-solution"></a>在行動裝置管理解決方案管理的裝置上使用應用程式保護原則保護資料

![此圖顯示應用程式保護原則在 BYOD 裝置上的運作方式](./media/app-protection-policies-with-mdm.png)

**在 MDM 解決方案中註冊的裝置**-

上圖顯示 MDM 與應用程式保護原則共同提供的多層保護。

MDM 解決方案：

-   註冊裝置

-   將應用程式部署至裝置

-   提供持續的裝置合規性和管理

**應用程式保護原則藉由下列方式提升價值︰**

-   協助保護公司資料不外洩給取用者應用程式和服務

-   將「另存新檔」、「剪貼簿」或 *PIN* 等限制套用到用戶端應用程式

-   抹除應用程式中的公司資料，但不從裝置移除這些應用程式


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>在未註冊的裝置上使用資料保護原則保護資料

![此圖顯示應用程式保護原則在受管理裝置上的運作方式](./media/app-protection-policies-without-mdm.png)

上圖說明資料保護原則在沒有 MDM 的情況下，於應用程式層級的運作方式。

對於未在任何 MDM 解決方案中註冊的 BYOD 裝置，應用程式保護原則可在應用程式層級保護公司資料。
但有一些限制需要注意，例如：

-   您無法將應用程式部署到裝置。 使用者必須從存放區取得應用程式。

-   您無法在這些裝置上佈建憑證設定檔。

-   您無法在這些裝置上佈建公司 Wi-Fi 和 VPN 設定。

## <a name="app-protection-global-policy"></a>應用程式保護的全域原則

如果 OneDrive 系統管理員瀏覽至 **admin.office.com** 並選取 [裝置] 存取，他們可以設定 OneDrive 和 SharePoint 用戶端應用程式的 [行動應用程式管理] 控制項。 

這些設定會開放給 OneDrive 管理主控台使用，可設定稱為**全域**原則的特殊 Intune 應用程式保護原則。 此全域原則適用於租用戶中的所有使用者，且無法控制原則目標。 

一旦啟用，適用於 iOS 和 Android 的 OneDrive 和 SharePoint 應用程式預設會以選取的設定進行保護。 IT 專業人員可以在 Intune 主控台中編輯此原則，以新增更多目標應用程式，並修改任何原則設定。 

根據預設，每個租用戶只能有一個**全域**原則。 不過，您可以使用 [Intune 圖形 API](intune-graph-apis.md) 來建立每個租用戶的額外全域原則，但不建議這樣做。 因為針對這類原則的實作進行疑難排解會變得很複雜，所以不建議建立額外的全域原則。

雖然**全域**原則會套用到租用戶中的所有使用者，但任何標準的 Intune 應用程式保護原則都會覆寫這些設定。


## <a name="multi-identity"></a>多重身分識別

如果應用程式保護原則只有在工作環境中使用應用程式時才適用，支援多重身分識別的應用程式可讓您使用不同帳戶 (工作和個人) 來存取相同應用程式。

舉一個個人內容的範例，想像有一個使用者在 Word 中開始一個新文件，這會被系統視為個人內容，因此不會套用 Intune 應用程式防護原則。 當該使用者把文件儲存到公司 OneDrive 帳戶上時，系統便會把該文件視為公司內容，並套用 Intune 應用程式防護原則。

舉一個工作內容的範例，想像有一個使用其工作帳戶來啟動 OneDrive 應用程式的使用者。 在工作環境中，他們無法將檔案移至個人儲存位置。 之後，當使用者以個人帳戶使用 OneDrive 時，他們可以從個人 OneDrive 複製並移動資料，而沒有任何限制。

- 深入了解支援 Intune 的 [MAM 和多重身分識別](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的應用程式。

## <a name="next-steps"></a>後續步驟

[如何使用 Microsoft Intune 建立及部署應用程式保護原則](app-protection-policies.md)

## <a name="see-also"></a>請參閱
協力廠商應用程式 (例如 Salesforce 行動應用程式) 可以特定方式與 Intune 搭配使用來保護公司資料。 若要深入了解 Salesforce 應用程式與 Intune 搭配使用的特定方式 (包括 MDM 應用程式組態設定)，請參閱 [Salesforce 應用程式和 Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf) \(英文\)。
