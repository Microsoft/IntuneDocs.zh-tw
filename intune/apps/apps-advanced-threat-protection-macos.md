---
title: 使用 Microsoft Intune 將 Microsoft Defender ATP 新增至 macOS 裝置
titleSuffix: ''
description: 了解使用 Microsoft Intune 將 Microsoft Defender ATP 新增至 macOS 裝置。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ae6e8a621b10ec969fa3fcfb2dfeabb8d5a7bdd
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569556"
---
# <a name="add-microsoft-defender-atp-to-macos-devices-using-microsoft-intune"></a>使用 Microsoft Intune 將 Microsoft Defender ATP 新增至 macOS 裝置

您必須先將應用程式新增至 Intune，才可以部署、設定、監視或保護它們。 其中一個[應用程式類型](~/apps/apps-add.md#app-types-in-microsoft-intune)是 Microsoft Defender 進階威脅防護 (ATP)。 透過在 Intune 中選取此應用程式類型，您可以將 Microsoft Defender ATP 指派及安裝到您所管理並執行 macOS 的裝置。 此應用程式類型可讓您輕易地將 Microsoft Defender ATP 指派給 macOS 裝置，而無須使用 macOS 應用程式包裝工具。 為了讓您保有最安全以及最新版的應用程式，這些應用程式也自帶 Microsoft AutoUpdate (MAU)。

## <a name="prerequisites"></a>先決條件
- macOS 裝置必須執行 macOS 10.13 或更新版本。
- macOS 裝置必須至少有 650 MB 的磁碟空間。
- 在 Intune 中部署核心延伸模組。 如需詳細資訊，請參閱[在 Intune 中新增 macOS 核心延伸模組](~/configuration/kernel-extensions-overview-macos.md)。

> [!IMPORTANT]
> 核心延伸模組只有在安裝 Microsoft Defender ATP 應用程式之前已存在於裝置上時，才能自動核准。 否則，使用者將會在 Mac 上看到「已封鎖系統延伸模組」訊息，且必須前往 [安全性喜好設定]  或 [系統喜好設定]   > [安全性與隱私]  ，然後選取 [允許]  來核准延伸模組。 如需詳細資訊，請參閱[針對 Microsoft Defender ATP for Mac 中的核心延伸模組問題進行疑難排解](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-support-kext)。

## <a name="add-microsoft-defender-atp-to-intune"></a>將 Microsoft Defender ATP 新增至 Intune
您可以使用下列步驟，將 Microsoft Defender ATP 新增至 Intune：

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [所有應用程式]   > [新增]  。
3. 在 [應用程式類型]  清單中的 [Microsoft Defender ATP]  下方，選取 [macOS]  。

## <a name="configure-app-information"></a>設定應用程式資訊
在此步驟中，您要提供應用程式部署的相關資訊。 這項資訊可協助您在 Intune 中識別應用程式，並幫助使用者在公司入口網站中尋找應用程式。

1. 按一下 [應用程式資訊]  以顯示 [應用程式資訊]  窗格。
2. 在 [應用程式資訊]  窗格中，您會提供此應用程式部署的相關資訊。 這項資訊可協助您在 Intune 中識別應用程式，並幫助使用者在公司入口網站中尋找應用程式。
    - **名稱**：輸入要顯示在公司入口網站中的應用程式名稱。 請確定所有名稱都是唯一的。 如果有重複的應用程式名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **描述**：輸入應用程式的描述。 例如，您可以在 [描述] 中列出目標使用者。
    - **發行者**：Microsoft 會顯示為發行者。
    - **類別**：(選擇性) 選取一或多個內建的應用程式類別，或選取您建立的類別。 此設定可讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式**：若要在使用者瀏覽應用程式時，於公司入口網站的主頁面上以醒目方式顯示應用程式，請選取此選項。
    - **資訊 URL**：(選用) 輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL**：(選擇性) 輸入包含這個應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員**：Microsoft 會顯示為開發人員。
    - **擁有者**：Microsoft 會顯示為擁有者。
    - **附註**：(選擇性) 輸入要與此應用程式建立關聯的任何附註。
3. 選取 [確定]  。

## <a name="select-scope-tags-optional"></a>選取範圍標籤 (選擇性)
您可以使用範圍標籤來決定可在 Intune 中看見用戶端應用程式資訊的人員。 如需範圍標籤的完整詳細資料，請參閱針對分散式 IT 使用角色型存取控制和範圍標籤。
1.  選取 [範圍 (標籤)]   > [新增]  。
2.  使用 [選取]  方塊來搜尋範圍標籤。
3.  選取您想要指派至此應用程式之範圍標籤旁邊的核取方塊。
4.  按一下 [選取]   > [確定]  。

## <a name="add-the-app"></a>新增應用程式
當您完成設定時，請從 [應用程式]  窗格中選取 [新增]  。 

您建立的應用程式即會顯示在應用程式清單中，而您可從中將該應用程式指派給所選的群組。 

> [!NOTE]
> 目前，Apple 未提供讓 Intune 在 macOS 裝置上解除安裝 Microsoft Defender ATP 的方法。

## <a name="next-steps"></a>後續步驟
- 若要了解如何在 macOS 裝置上設定 Microsoft Defender ATP，請參閱[在 macOS 裝置上設定 Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-preferences)。
- 若要深入了解包含和排除使用者群組的應用程式指派，請參閱[包含與排除應用程式指派](~/apps/apps-inc-exl-assignments.md)。
- [將應用程式指派給群組](~/apps/apps-deploy.md)

