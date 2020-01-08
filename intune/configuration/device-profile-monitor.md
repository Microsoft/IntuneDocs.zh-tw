---
title: 使用 Microsoft Intune 查看裝置設定檔 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中檢視和管理裝置組態設定檔、查看獲指派某個設定檔之裝置數目的圖形化圖表，以及查看已指派或部署設定檔的裝置。 也可以針對具有衝突設定的設定檔進行疑難排解。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 25983117864f44b8131fdc49e60b7d24048da9fe
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206647"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>在 Microsoft Intune 中監視裝置設定檔



Intune 包含了一些功能以協助監視及管理您的裝置組態設定檔。 例如，您可以檢查設定檔的狀態、查看已指派的裝置，以及更新設定檔的內容。

## <a name="view-existing-profiles"></a>檢視現有的設定檔

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]  。

所有您現有的設定檔都會列出，包含平台之類的詳細資料，並顯示該設定檔是否已指派給任何裝置。

## <a name="view-details-on-a-profile"></a>檢視設定檔的詳細資料

當您建立裝置設定檔之後，Intune 會提供圖形化圖表。 這些圖表顯示設定檔的狀態，例如它已經成功地指派給裝置，或者該設定檔顯示有衝突。

1. 選取現有的設定檔。 例如，選取 macOS 設定檔。
2. 選取 [概觀]  索引標籤。

    頂端的圖形化圖表顯示指派給裝置設定檔的裝置數量。 例如，如果組態裝置設定檔套用到 macOS 裝置，圖表就會列出 macOS 裝置的計數。

    它也會顯示指派相同設定檔之其他平台的裝置數目。 例如，它會顯示非 macOS 裝置的計數。

    ![檢視指派給裝置設定檔的裝置數目](./media/device-profile-monitor/device-configuration-profile-graphical-chart.png)

    底部的圖形化圖表顯示指派給裝置設定檔的使用者數量。 例如，如果設定裝置設定檔套用到 macOS 使用者，圖表就會列出 macOS 使用者的計數。

3. 選取頂端圖形化圖表中的圓形。 隨即開啟 [裝置狀態]  。

    其中列出指派給設定檔的裝置，而且它會顯示設定檔是否已成功部署。 另請注意，它只會列出特定平台的裝置 (例如 macOS)。

    關閉 [裝置狀態]  詳細資料。

4. 選取底端圖形化圖表中的圓形。 隨即開啟 [使用者狀態]  。 

    其中列出指派給設定檔的使用者，而且它會顯示設定檔是否已成功部署。 另請注意，它只會列出特定平台 (例如 macOS) 的使用者。

    關閉 [使用者狀態]  詳細資料。

5. 回到 [設定檔]  清單中，選取一個特定的設定檔。 您也可以變更現有的屬性：
    - [內容]  ：變更名稱或更新現有設定。
    - **指派**：包含或排除應該套用原則的裝置。 選擇 [選取的群組]  來選擇特定群組。
    - **裝置狀態**：其中列出指派給設定檔的裝置，而且它會顯示設定檔是否已成功部署。 您可以選取特定的裝置以取得更多詳細資料，包括安裝的應用程式。
    - **使用者狀態**：列出具有被此設定檔影響之裝置的使用者名稱，以及設定檔是否已成功部署。 您可以選取特定的使用者以取得更多詳細資料。
    - **每個設定的狀態**：藉由顯示設定檔內的個別設定來篩選輸出，並顯示是否已成功套用設定。

## <a name="view-conflicts"></a>檢視衝突

在 [裝置]   > [所有裝置]  中，您可以查看任何會造成衝突的設定。 發生衝突時，您也會看見包含此設定的所有組態設定檔。 系統管理員可以使用此功能來協助進行疑難排解，並修正任何與設定檔不一致的地方。

1. 在 Intune 中，選取 [裝置]   > [所有裝置]  > 選取清單中現有的裝置。 終端使用者可以從他們的公司入口網站應用程式中取得裝置名稱。
2. 選取 [裝置設定]  。 隨即列出所有套用至裝置的設定原則。
3. 選取原則。 它會顯示該原則中套用至裝置的所有設定。 若裝置具有**衝突**狀態，請選取該資料列。 在新視窗中，您會看到所有的設定檔，以及所含設定造成衝突的設定檔名稱。

既然您已經知道發生衝突的設定，以及包含該設定的原則，應該可以輕鬆地解決該衝突。 

## <a name="device-firmware-configuration-interface-profile-reporting"></a>裝置韌體設定介面設定檔報告

> [!WARNING]
> 監視目前正在建立的 DFCI 設定檔。 在 DFCI 處於公開預覽狀態期間，監視資料可能會遺失或不完整。

DFCI 設定檔會以每個設定為基礎進行報告，和其他裝置組態設定檔相同。 視製造商對 DFCI 的支援而定，某些設定可能不適用。

針對您的 DFCI 設定檔設定，您可能會看見下列狀態：

- **符合規範**：此狀態會在設定檔中的設定值符合裝置上的設定值時顯示。 此狀態會在下列案例中發生：

  - DFCI 設定檔已成功對設定檔中的設定進行設定。
  - 裝置沒有由該設定所控制的硬體功能，且設定檔的設定是 [已停用]  。
  - UEFI 不允許 DFCI 停用該功能，且設定檔的設定是 [已啟用]  。
  - 裝置缺乏停用該功能的硬體，且設定檔的設定是 [已啟用]  。

- **不適用**：此狀態會在設定檔中的設定值是 [已啟用]  ，且系統在裝置上找不到相符的設定時顯示。 此狀態可能會在裝置硬體不具備該功能時發生。

- **不符合規範**：此狀態會在設定檔中的設定值不符合裝置上的設定值時顯示。 此狀態會在下列案例中發生：

  - UEFI 不允許 DFCI 停用設定，且設定檔的設定是 [已停用]  。
  - 裝置缺乏停用該功能的硬體，且設定檔的設定是 [已停用]  。
  - 裝置沒有最新的 DFCI 韌體版本。
  - 在於 Intune 中註冊 DFCI 之前，已於 UEFI 功能表中使用本機「退出」控制項來停用 DFCI。
  - 裝置是在 Autopilot 註冊之外註冊至 Intune。
  - 裝置不是由 Microsoft CSP 註冊至 Autopilot，或是由 OEM 直接註冊。

## <a name="next-steps"></a>後續步驟

[對於裝置設定檔的常見疑問、問題和解決方式](device-profile-troubleshoot.md)  
[針對 Intune 中的原則和設定檔進行疑難排解](troubleshoot-policies-in-microsoft-intune.md)
