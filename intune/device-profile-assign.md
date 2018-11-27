---
title: 在 Microsoft Intune - Azure 中指派裝置設定檔 | Microsoft Docs
description: 使用 Azure 入口網站將裝置設定檔和原則指派給使用者和裝置。 了解如何在 Microsoft InTune 的設定檔指派中排除群組。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2cd71eabf3efeb6b3eaa897745ed0441c456cd60
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182290"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>在 Microsoft Intune 中指派使用者和裝置設定檔

在您建立設定檔之後，可以將設定檔指派至 Azure Active Directory (Azure AD) 群組。

## <a name="assign-a-device-profile"></a>指派裝置設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，並搜尋 **Microsoft Intune**。
2. 在 **Microsoft Intune** 中，選取 [裝置設定]，然後選取 [設定檔]。
3. 在設定檔清單中，選取您要指派的設定檔，然後選取 [指派]。
4. 選擇 [包含] 群組或 [排除] 群組，然後選取群組。  

    ![在設定檔指派中包含或排除群組的選項螢幕擷取畫面](./media/group-include-exclude.png)

5. 當您選取群組時，會選擇 Azure AD 群組。 若要選取多個群組，請按住 **Ctrl** 鍵。
6. 完成之後，請選取 [儲存]。

## <a name="exclude-groups-from-a-profile-assignment"></a>從設定檔指派排除群組

Intune 裝置組態設定檔可讓您從原則指派排除群組。 例如，您可以將裝置設定檔指派給**所有公司使用者**群組，但排除**資深管理層**群組的任何成員。

如果您排除指派的群組、只排除使用者，或只排除裝置群組 (不是群組的混合)，則 Intune 不會視為任何使用者與裝置關聯性。 包含使用者群組的同時排除裝置群組，可能不會建立您預期的結果。 如果使用混合群組，或發生其他衝突，則包含的優先順序高於排除。

例如，您想要將裝置設定檔指派給組織中 Kiosk 裝置以外的所有裝置。 您包含**所有使用者**群組，但是排除**所有裝置**群組。 在此情況下，所有的使用者及其裝置都受原則約束，即使使用者的裝置屬於**所有裝置**群組。

排除只會查看群組的直屬成員，不包含與使用者建立關聯的裝置。 不過，沒有使用者的裝置則無法取得原則。 發生原因是這些裝置不具有與**所有使用者**群組的關聯性。

如果您包含**所有裝置**，並排除**所有使用者**，則所有裝置都會收到原則。 在此情況下，目的是要排除此原則中有相關聯使用者的裝置。 不過，它不會排除裝置，因為排除只會比對直屬群組成員。

## <a name="next-steps"></a>接下來的步驟
請參閱[如何監視裝置設定檔](device-profile-monitor.md)以取得監視裝置設定檔指派的指示。
