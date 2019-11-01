---
title: 在 Microsoft Intune 中啟用 Mobile Threat Defense 連接器
titleSuffix: Microsoft Intune
description: 啟用 Mobile Threat Defense (MTD) 合作夥伴與 Microsoft Intune 之間的連接器。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4f917167baecc643e045610e86e582957e535978
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810299"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>在 Intune 中啟用 Mobile Threat Defense 連接器

> [!NOTE] 
> 此主題適用於所有 Mobile Threat Defense 合作夥伴。

在 Mobile Threat Defense (MTD) 安裝期間，您已設定原則以在 MTD 合作夥伴主控台中分類威脅，且已在 Intune 中建立裝置相容性原則。 如果您已在 MTD 夥伴主控台中設定 Intune 連接器，您現在可以啟用 MTD 合作夥伴應用程式的 MTD 連線。

當您將新的應用程式整合到 Intune Mobile Threat Defense 並啟用 Intune 連線時，Intune 會在 Azure Active Directory 中建立傳統條件式存取原則。 您整合的每個 MTD 應用程式 (包括 [Defender ATP](advanced-threat-protection.md) 或任何其他 [MTD 合作夥伴](mobile-threat-defense.md#mobile-threat-defense-partners)) 都會建立新的傳統條件式存取原則。 這些原則可以忽略，但不應編輯、刪除或停用。

適用於 MTD 應用程式的傳統條件式存取原則： 

- 由 Intune MTD 用於要求裝置必須在 Azure AD 中註冊，以便它們與 MTD 合作夥伴通訊之前擁有裝置識別碼。 此識別碼為必要，以便裝置成功向 Intune 報告其狀態。  
- 不會影響任何其他雲端應用程式或資源。  
- 不同於您可能會建立用來協助管理 MTD 的條件式存取原則。
- 根據預設，不會與您用於評估的其他條件式存取原則互動。  

若要檢視傳統條件式存取原則，請前往 [Azure](https://portal.azure.com/#home) 中的 [Azure Active Directory]   > [條件式存取]   > [傳統原則]  。


## <a name="to-enable-the-mobile-threat-defense-connector"></a>啟用 Mobile Threat Defense 連接器

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。

4. 在 [Intune 儀表板]  上，選擇 [裝置合規性]  ，然後選擇 [設定]  區段下的 [Mobile Threat Defense]  。

5. 在 [Mobile Threat Defense]  窗格中，選擇 [新增]  。

6. 從下拉式清單中選擇 MTD 解決方案作為**要設定的 Mobile Threat Defense 連接器**。

    ![Intune Azure 入口網站中的 MTD 設定](./media/mtd-connector-enable/enable-mtd-connector-1.png)

7. 根據組織的需求來啟用切換選項。 可見的切換選項會根據 MTD 夥伴而不同。

## <a name="mobile-threat-defense-toggle-options"></a>Mobile Threat Defense 切換選項

您可以根據組織的需求決定需要啟用哪些 Mobile Threat Defense 切換選項。 以下是更多詳細資料：

**MDM 合規性政策設定**
- **將 Android 4.1+ 裝置連線至 *\<MTD 合作夥伴名稱>***：當您啟用此選項時，可讓 Android 4.1+ 裝置將安全性風險回報給 Intune。
- **將 iOS 8.0+ 裝置連線至 *\<MTD 合作夥伴名稱>***：當您啟用此選項時，可讓 iOS 8.0+ 裝置將安全性風險回報給 Intune。
- **啟用 iOS 裝置的應用程式同步**：允許此 Mobile Threat Defense 合作夥伴向 Intune 要求 iOS 應用程式的中繼資料，以針對威脅分析用途使用。
- **封鎖不支援的 OS 版本**：如果裝置所執行的作業系統低於支援的最低版本，則將其封鎖。

**應用程式防護原則設定**
- **將 4.1 版和更新版本的 Android 裝置連線至 \<MTD 合作夥伴名稱>  ，以進行應用程式防護原則評估**：當您啟用此選項時，使用裝置威脅等級規則的應用程式防護原則會評估裝置，包括來自此連接器的資料。
- **將 8.0 版和更新版本的 iOS 裝置連線至 \<MTD 合作夥伴名稱>  ，以進行應用程式防護原則評估**：當您啟用此選項時，使用裝置威脅等級規則的應用程式防護原則會評估裝置，包括來自此連接器的資料。

若要深入了解如何將 Mobile Threat Defense 連接器用於 Intune 應用程式防護原則評估，請參閱[針對尚未註冊的裝置設定 Mobile Threat Defense](~/protect/mtd-enable-unenrolled-devices.md)。

**一般共用設定**
- **合作夥伴無回應前的天數**：Intune 將合作夥伴視為因連線中斷而無回應之前的閒置天數。 針對沒有回應的 MTD 合作夥伴，Intune 會忽略其合規性狀態。

> [!IMPORTANT] 
> 在情況允許時，建議您先新增並指派 MTD 應用程式，再建立裝置合規性和條件式存取原則規則。 這樣做有助於確保 MTD 應用程式已準備好供使用者進行安裝，安裝後使用者才能存取電子郵件或其他公司資源。

> [!TIP]
> 您可從 [Mobile Threat Defense] 窗格中看見 Intune 與 MTD 合作夥伴之間的 [連線狀態]  與 [上次同步處理]  時間。
