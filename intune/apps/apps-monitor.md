---
title: 監視應用程式資訊和指派
titleSuffix: Microsoft Intune
description: 在您將應用程式指派給使用者或裝置之後，可以使用此資訊協助您監視應用程式的狀態。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 03c38472a3100ec2d717e802e07e189a53ac0866
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725006"
---
# <a name="monitor-app-information-and-assignments-with-microsoft-intune"></a>使用 Microsoft Intune 監視應用程式資訊和指派

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 提供數種方式，可讓您監視您所管理應用程式的內容，以及管理它們的指派狀態。

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在 [Intune]  窗格中，選取 [用戶端應用程式]  。
4. 在功能表的 [管理]  區段，選取 [應用程式]  。
5. 在應用程式清單中，選取要監視的應用程式。 您接著會看到內含裝置狀態和使用者狀態概觀的應用程式窗格。

> [!NOTE]
> 部署為**可用**的 Android 市集應用程式不會報告其安裝狀態。

## <a name="app-overview-pane"></a>應用程式概觀窗格

在應用程式窗格中，您可以檢閱環境中應用程式狀態的詳細資料。

### <a name="essentials"></a>Essentials
[程式集]  區段包含應用程式下列資訊：

 | **應用程式詳細資料**            | **描述**                                                      |
|------------------------|------------------------------------------------------------------|
| **發佈者**          | 應用程式的發行者。                                            |
| **作業系統**   | 應用程式作業系統 (Windows、iOS、Android 等等)。 |
| **建立時間**             | 此修訂建立的日期和時間。 <b>**注意**：IT 系統管理員變更應用程式中繼資料 (例如變更應用程式類別或應用程式描述) 時，會更新這個日期值。                        |
| **已指派**           | 是否已指派應用程式 ([是]  或 [否]  )。                  |

### <a name="device-and-user-status-graphs"></a>裝置和使用者狀態圖表
圖表會顯示下列狀態的應用程式數目：

| **裝置狀態**       | **描述**                                       |
|-----------------------|-------------------------------------------------------|
| **已安裝**         | 安裝的應用程式數目。                         |
| **未安裝**     | 未安裝的應用程式數目。                     |
| **失敗**            | 安裝失敗的數目。                   |
| **安裝擱置中**   | 正在安裝的應用程式數目。 |
| **不適用**           | 狀態不適用的應用程式數目。            |

> [!NOTE]
> 請注意，部署為 [無論是否已註冊皆可使用]  的 Android LOB 應用程式 (.APK) 只會報告已註冊裝置的應用程式安裝狀態。 對於未在 Intune 中註冊的裝置，則無法提供應用程式安裝狀態。

### <a name="device-install-status"></a>裝置安裝狀態

當您選取功能表 [監視]  區段中的 [裝置安裝狀態]  時，會顯示裝置狀態清單。 詳細資料表包含下列資料行：

| **裝置資料行**      | **描述**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **裝置名稱**      | 允許命名裝置之平台上的裝置名稱。 在其他平台上，Intune 會從其他屬性建立名稱。 此屬性不適用於任何其他裝置。                                                                       |
| **使用者名稱**        | 使用者的名稱。                                                                                                                                                                                                                                      |
| **平台**         | 裝置的作業系統 (Windows、iOS、Android 等等)。                                                                                                                                                                                           |
| **版本**          | 應用程式的版本號碼。 針對企業營運 (LOB) 應用程式和商務用 Microsoft Store 應用程式，會顯示應用程式的完整版本號碼。 完整的版本號碼可識別特定的應用程式版本。 此號碼會顯示為_版本_(_組建_)。 例如，2.2(2.2.17560800)。 針對市集應用程式，不會顯示任何版本。 |
| **狀態**           | 應用程式的狀態。                                                                                                                                                                                                                                     |
| **狀態詳細資料**   | 狀態的詳細資料。                                                                                                                                                                                                                                     |
| **上次簽入**    | 裝置上次與 Intune 同步處理的日期。                                                                                                                                                                                                                  |


### <a name="user-install-status"></a>使用者安裝狀態

當您選取功能表 [監視]  區段中的 [使用者安裝狀態]  時，會顯示使用者狀態清單。 詳細資料表包含下列資料行：

| **使用者資料行**     | **描述**                           |
|---------------------|-------------------------------------------|
| **名稱**            | Azure Active Directory 中的使用者名稱。         |
| **使用者名稱**       | 使用者的唯一名稱。              |
| **安裝**   | 使用者安裝的應用程式數目。 |
| **失敗**        | 使用者安裝失敗的應用程式數目。     |
| **未安裝**   | 使用者未安裝的應用程式數目。 |


## <a name="next-steps"></a>後續步驟

- 若要深入了解如何使用 Intune 資料，請參閱[使用 Intune 資料倉儲](../reports-nav-create-intune-reports.md)。
- 若要了解應用程式設定原則，請參閱 [Intune 的應用程式設定原則](app-configuration-policies-overview.md)。
