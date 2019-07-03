---
title: 在 Microsoft Intune 中啟用 Mobile Threat Defense 連接器
titleSuffix: Microsoft Intune
description: 啟用 Mobile Threat Defense (MTD) 合作夥伴與 Microsoft Intune 之間的連接器。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 45bcafad3dc6c2a407e1b7b88e07f4021e8b5a36
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67528301"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>在 Intune 中啟用 Mobile Threat Defense 連接器

> [!NOTE] 
> 此主題適用於所有 Mobile Threat Defense 合作夥伴。

在 Mobile Threat Defense (MTD) 安裝期間，您已設定原則以在 MTD 合作夥伴主控台中分類威脅，且已在 Intune 中建立裝置相容性原則。 如果您已在 MTD 合作夥伴主控台中設定 Intune 連接器，現在可以在 Intune 中啟用 MTD 連線。

## <a name="to-enable-the-mtd-connector"></a>啟用 MTD 連接器

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。

4. 在 [Intune 儀表板]  上，選擇 [裝置合規性]  ，然後選擇 [設定]  區段下的 [Mobile Threat Defense]  。

5. 在 [Mobile Threat Defense]  窗格中，選擇 [新增]  。

6. 從下拉式清單中選擇 MTD 解決方案作為**要設定的 Mobile Threat Defense 連接器**。

    ![Intune Azure 入口網站中的 MTD 設定](./media/enable-mtd-connector-1.png)

7. 根據組織的需求來啟用切換選項。 可見的切換選項會根據 MTD 夥伴而不同。

## <a name="mtd-toggle-options"></a>MTD 切換選項

您可以決定根據組織的需求必須啟用哪些 MTD 切換選項。 以下是更多詳細資料：

- **將 Android 4.1+ 裝置連線至 [MTD 合作夥伴名稱] for Work MTD**：當您啟用此選項時，可讓 Android 4.1+ 裝置將安全性風險回報給 Intune。
    - **如果收不到任何資料，標記為不符合規範**：如果 Intune 沒有從 MTD 合作夥伴收到有關此平台上裝置的資料，則將此裝置視為不符合規範。
<br></br>
- **將 iOS 8.0+ 裝置連線至 [MTD 合作夥伴名稱] for Work MTD**：當您啟用此選項時，可讓 iOS 8.0+ 裝置將安全性風險回報給 Intune。
    - **如果收不到任何資料，標記為不符合規範**：如果 Intune 沒有從 MTD 合作夥伴收到有關此平台上裝置的資料，則將此裝置視為不符合規範。
<br></br>
- **啟用 iOS 裝置的應用程式同步**：允許此 Mobile Threat Defense 合作夥伴向 Intune 要求 iOS 應用程式的中繼資料，以針對威脅分析用途使用。

- **封鎖不支援的 OS 版本**：如果裝置所執行的作業系統低於支援的最低版本，則將其封鎖。

- **合作夥伴無回應前的天數**：Intune 將合作夥伴視為因連線中斷而無回應之前的閒置天數。 針對沒有回應的 MTD 合作夥伴，Intune 會忽略其合規性狀態。

> [!IMPORTANT] 
> 在情況允許時，建議您先新增並指派 MTD 應用程式，再建立裝置合規性和條件式存取原則規則。 這樣做有助於確保 MTD 應用程式已準備好供使用者進行安裝，安裝後使用者才能存取電子郵件或其他公司資源。

> [!TIP]
> 您可從 [Mobile Threat Defense] 窗格中看見 Intune 與 MTD 合作夥伴之間的 [連線狀態]  與 [上次同步處理]  時間。
