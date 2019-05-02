---
title: 在 Microsoft Intune - Azure 中遠端管理裝置 | Microsoft Docs
description: 檢視所需的角色以使用 TeamViewer、如何安裝 TeamViewer 連接器、在 Azure 入口網站使用 Microsoft Intune 來遠端管理裝置的逐步指示
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/05/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dd2d9f0a0caf87eb75ba3a9cdc123e69425ceb8b
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61509719"
---
# <a name="use-teamviewer-to-remotely-administer-intune-devices"></a>使用 TeamViewer 來遠端管理 Intune 裝置

由 Intune 管理的裝置可以從遠端使用 [TeamViewer](https://www.teamviewer.com) 來管理。 TeamViewer 是可分開購買的第三方廠商程式。 本主題說明如何設定 TeamViewer 搭配 Intune，以及從遠端管理裝置。 

## <a name="prerequisites"></a>必要條件

- 使用支援的裝置。 Intune 受控的 Android、Windows、iOS 和 macOS 裝置支援遠端管理。 TeamViewer 可能不支援 Windows Holographic (HoloLens)、Windows Team (Surface Hub) 或 Windows 10 S。針對其支援性，請參閱 [TeamViewer](https://www.teamviewer.com) 以取得更新。

- Azure 入口網站中的 Intune 系統管理員必須有下列 [Intune 角色](role-based-access-control.md)：  

    - **更新遠端協助**：可讓系統管理員修改 TeamViewer 連接器設定
    - **要求遠端協助**：可讓系統管理員為任何使用者啟動新的遠端協助工作階段。 此角色的使用者不會受到範圍內的任何 Intune 角色限制。 此外，在一個範圍內受指派為 Intune 角色的使用者或裝置群組，也可以要求遠端協助。 

- 包含登入認證的 [TeamViewer](https://www.teamviewer.com) 帳戶。 只有一些 TeamViewer 授權才支援與 Intune 整合。 如需特定的 TeamViewer 需求，請參閱 [TeamViewer Integration Partner:Microsoft Intune](https://www.teamviewer.com/integrations/microsoft-intune/) (TeamViewer 整合夥伴：Microsoft Intune)。

藉由使用 TeamViewer，您允許適用於 Intune 連接器的 TeamViewer 建立 TeamViewer 工作階段、讀取 Active Directory 資料，以及儲存 TeamViewer 帳戶存取權杖。

## <a name="configure-the-teamviewer-connector"></a>設定 TeamViewer 連接器

若要為裝置提供遠端協助，請使用下列步驟來設定 Intune TeamViewer 連接器：

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，並搜尋 **Microsoft Intune**。
2. 在 [Microsoft Intune] 中，選取 [裝置]，然後選取 [TeamViewer 連接器]。
3. 選取 [連線] 並接受授權合約。
4. 選取 [登入 TeamViewer 進行授權]。
5. 隨即開啟一個網頁來顯示 TeamViewer 網站。 輸入您的 TeamViewer 授權認證，然後 [登入]。

## <a name="remotely-administer-a-device"></a>遠端管理裝置

設定連接器後，您可以從遠端管理裝置。 請使用下列步驟： 

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，並搜尋 **Microsoft Intune**。
2. 在 [Microsoft Intune] 中，選取 [裝置]，然後選取 [所有裝置]。
3. 從清單中，選取您想要遠端管理的裝置。 在裝置屬性中，選取 [新的遠端協助工作階段]。
4. 當 Intune 連線至 TeamViewer 服務之後，您將會看到一些裝置的相關資訊。 [連線] 以啟動遠端工作階段。

![使用 TeamViewer 從遠端管理 Android 裝置：範例](./media/android-teamviewer.png)

當您開始遠端工作階段時，使用者會在其裝置上的公司入口網站應用程式圖示上看到通知旗標。 當應用程式開啟時也會出現通知。 然後使用者就能接受遠端協助要求。

> [!NOTE]
> 使用「無使用者」方法 (例如 DEM 及 WCD) 註冊的 Windows 裝置不會在公司入口網站應用程式中顯示 TeamViewer 通知。 在這些情況下，建議使用 TeamViewer 入口網站來產生工作階段。

在 TeamViewer 中，您可以在裝置上完成一系列動作，包括控制裝置。 對於您可以執行的作業之完整詳細資料，請參閱 [TeamViewer guidance](https://www.teamviewer.com/support/documents/) (TeamViewer 指導)。

完成後，請關閉 TeamViewer 視窗。
