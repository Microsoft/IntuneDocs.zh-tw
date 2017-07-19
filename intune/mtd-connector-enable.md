---
title: "搭配 Intune 啟用 Mobile Threat Defense 連接器"
titleSuffix: Intune on Azure
description: "在 Intune 中啟用 Mobile Threat Defense 連接器。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 38fb9977ed8af05380a265ee254259acef7b43f0
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="enable-mobile-threat-defense-in-intune"></a>在 Intune 中啟用 Mobile Threat Defense

若要在 Intune 中啟用 Mobile Threat Defense (MTD) 連線，您應該已在 MTD 解決方案主控台中設定 Intune 連接器。

## <a name="to-enable-the-mtd-connector"></a>啟用 MTD 連接器

1. 移至 [Azure 入口網站](https://portal.azure.com)，並使用您的 Intune 認證登入。 成功登入之後，您會看到 [Azure 儀表板]。

2. 在 [Azure 儀表板] 中，選擇左功能表中的 [更多服務]，然後在文字方塊篩選中輸入 **Intune**。

3. 選擇 [Intune]，即會開啟 [Intune 儀表板]。

4. 在 [Intune 儀表板] 上，選擇 [裝置合規性]，然後選擇 [設定] 區段下的 [Mobile Threat Defense]。

5. 在 [Mobile Threat Defense] 刀鋒視窗上，選擇 [新增]。

6. 從下拉式清單中選擇 MTD 解決方案作為**要設定的 Mobile Threat Defense 連接器**。

    ![Intune Azure 入口網站中的 MTD 設定](./media/enable-mtd-connector-1.png)

7. 根據組織的需求來啟用切換選項。

## <a name="mtd-toggle-options"></a>MTD 切換選項

您可以根據組織的需求決定需要啟用哪些 MTD 切換選項。 以下是更多詳細資料：

- **將 Android 4.1+ 裝置連線至 [MTD 夥伴名稱] for Work MTD**：當您啟用此選項時，可讓 Android 4.1+ 裝置將安全性風險回報給 Intune。
    - **如果收不到任何資料，標記為不合規**：如果 Intune 沒有從 MTD 合作夥伴收到有關此平台上裝置的資料，則將此裝置視為不合規。
<br></br>
- **將 iOS 8.0+ 裝置連線至 [MTD 夥伴名稱] for Work MTD**：當您啟用此選項時，可讓 Android 4.1+ 裝置將安全性風險回報給 Intune。
    - **如果收不到任何資料，標記為不合規**：如果 Intune 沒有從 MTD 合作夥伴收到有關此平台上裝置的資料，則將此裝置視為不合規。
<br></br>
- **封鎖不支援的作業系統版本**：如果裝置所執行的作業系統低於支援的最低版本，則將其封鎖。

- **夥伴無回應前的天數**：Intune 將夥伴視為因連線中斷而無回應之前的閒置天數。 針對沒有回應的 MTD 合作夥伴，Intune 會忽略其合規性狀態。

> [!IMPORTANT] 
> 您必須新增並指派 MTD 應用程式，再建立裝置相容性和條件式存取原則規則。 這樣做可確保 MTD 應用程式已準備好供使用者進行安裝，安裝後使用者才能存取電子郵件或其他公司資源。

> [!TIP]
> 您可從 [Mobile Threat Defense] 刀鋒視窗中看見 Intune 與 MTD 合作夥伴之間的 [連線狀態] 與 [上次同步處理] 時間。

## <a name="next-steps"></a>後續步驟

[搭配 Intune 建立 Mobile Threat Defense 裝置合規性原則](mtd-device-compliance-policy-create.md)
