---
title: 針對尚未註冊的裝置啟用 Mobile Threat Defense 連接器
titleSuffix: Microsoft Intune
description: 在 Microsoft Intune 中針對尚未註冊的裝置啟用 Mobile Threat Defense 連接器。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9571f7d0ae10f33007d5ae50b403580232c2e870
ms.sourcegitcommit: 06dce5c8111592ad774247e86e539dd3128117e5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/30/2019
ms.locfileid: "75545920"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>在 Intune 中針對尚未註冊的裝置啟用 Mobile Threat Defense 連接器

在 Mobile Threat Defense (MTD) 安裝期間，您已設定原則以在 Mobile Threat Defense 合作夥伴主控台中分類威脅，且已在 Intune 中建立應用程式防護原則。 如果您已在 MTD 夥伴主控台中設定 Intune 連接器，您現在可以啟用 MTD 合作夥伴應用程式的 MTD 連線。

> [!NOTE]
> 此文章適用於所有支援應用程式防護原則的 Mobile Threat Defense 合作夥伴：Better Mobile (Android)、Zimperium (Android/iOS)、Lookout for Work (Android/iOS)。

## <a name="classic-conditional-access-policies-for-mtd-apps"></a>適用於 MTD 應用程式的傳統條件式存取原則

當您將新的應用程式整合到 Intune Mobile Threat Defense 並啟用 Intune 連線時，Intune 會在 Azure Active Directory 中建立傳統條件式存取原則。 您整合的每個 MTD 應用程式 (包括 [Defender ATP](advanced-threat-protection.md) 或任何其他 [MTD 合作夥伴](mobile-threat-defense.md#mobile-threat-defense-partners)) 都會建立新的傳統條件式存取原則。 這些原則可以忽略，但不應編輯、刪除或停用。

如已刪除傳統原則，則需要刪除負責建立該原則的 Intune 連線，然後再次設定。 此程序會重新建立此傳統原則。 不支援將 MTD 應用程式的傳統原則移轉至條件式存取的新原則類型。

適用於 MTD 應用程式的傳統條件式存取原則：

- 由 Intune MTD 用於要求裝置必須在 Azure AD 中註冊，以便它們與 MTD 合作夥伴通訊之前擁有裝置識別碼。 此識別碼為必要，以便裝置成功向 Intune 報告其狀態。

- 不會影響任何其他雲端應用程式或資源。

- 不同於您可能會建立用來協助管理 MTD 的條件式存取原則。

- 根據預設，不會與您用於評估的其他條件式存取原則互動。

若要檢視傳統條件式存取原則，請前往 [Azure](https://portal.azure.com/#home) 中的 [Azure Active Directory]   > [條件式存取]   > [傳統原則]  。

## <a name="to-enable-the-mtd-connector"></a>啟用 MTD 連接器

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [租用戶系統管理]   > [連接器與權杖]   > [Mobile Threat Defense]  。

3. 在 [行動裝置威脅防護]  窗格中，選擇 [新增]  。

4. 從下拉式清單中選擇 MTD 解決方案作為**要設定的 Mobile Threat Defense 連接器**。

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. 根據組織的需求啟用切換選項。 可見的切換選項會根據 MTD 夥伴而不同。

## <a name="mobile-threat-defense-toggle-options"></a>Mobile Threat Defense 切換選項

您可以決定根據組織的需求必須啟用哪些 MTD 切換選項。 以下是更多詳細資料：

**應用程式防護原則設定**

- **將 4.4 版與更新版本的 Android 裝置連線至 \<MTD 合作夥伴名稱>  ，以進行應用程式防護原則評估**：當您啟用此選項時，使用裝置威脅等級規則的應用程式防護原則會評估裝置，包括來自此連接器的資料。

- **將 11 版與更新版本的 iOS 裝置連線至 \<MTD 合作夥伴名稱>  ，以進行應用程式防護原則評估**：當您啟用此選項時，使用裝置威脅等級規則的應用程式防護原則會評估裝置，包括來自此連接器的資料。

**一般共用設定**

- **合作夥伴無回應前的天數**：Intune 將合作夥伴視為因連線中斷而無回應之前的閒置天數。 針對沒有回應的 MTD 合作夥伴，Intune 會忽略其合規性狀態。

> [!TIP]
> 您可從 [Mobile Threat Defense] 窗格中看見 Intune 與 MTD 合作夥伴之間的 [連線狀態]  與 [上次同步處理]  時間。

## <a name="next-steps"></a>後續步驟

- [使用 Intune 建立 Mobile Threat Defense (MTD) 應用程式防護原則](~/protect/mtd-app-protection-policy.md)。
