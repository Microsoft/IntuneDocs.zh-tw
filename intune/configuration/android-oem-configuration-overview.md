---
title: 在 Microsoft Intune 中使用 Android Enterprise 裝置上的 OEMConfig - Azure | Microsoft Docs
description: 使用 Microsoft Intune 搭配 OEMConfig 來管理和使用執行 Android Enterprise 的裝置。 查看所有步驟 (包括概觀)，查看先決條件，在 Intune 中建立組態設定檔，然後查看支援的 OEMConfig 應用程式清單。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/02/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1bc811bcac80f8321284ece8d3860efc7164a270
ms.sourcegitcommit: a25f556aa9df4fcd9fdacccd12c9029bc6c5fe20
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78256317"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>在 Microsoft Intune 中透過 OEMConfig 使用和管理 Android Enterprise 裝置

在 Microsoft Intune 中，您可以使用 OEMConfig 來新增、建立及自訂適用於 Android Enterprise 裝置的 OEM 特定設定。 OEMConfig 通常是用於設定未內建在 Intune 中的設定。 不同的原始設備製造商 (OEM) 會包含不同的設定。 可用的設定取決於 OEM 包含在其 OEMConfig 應用程式中的內容。

本功能適用於：  

- Android 企業

此文章說明 OEMConfig、列出先決條件、示範如何建立組態設定檔，並列出 Intune 中支援的 OEMConfig 應用程式。

## <a name="overview"></a>概觀

OEMConfig 原則是特殊類型的裝置設定原則，類似[應用程式設定原則](../apps/app-configuration-policies-overview.md)。 OEMConfig 是由 Google 所定義的標準，其會使用 Android 中的應用程式設定來將裝置設定傳送到 OEM (原始設備製造商) 所撰寫的應用程式。 此標準可讓 OEM 和 EMM (企業行動管理) 以標準化的方式建置及支援 OEM 特定功能。 [深入了解 OEMConfig](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/) \(英文\)。

在過去，EMM (例如 Intune) 必須在 OEM 引進 OEM 特定功能之後，才能手動建置針對那些功能的支援。 此方法會導致重複性的工作並使採用速度變慢。

透過 OEMConfig，OEM 會建立結構描述來定義 OEM 特有的管理功能。 OEM 會將結構描述內嵌到應用程式中，然後將此應用程式放到 Google Play 上。 EMM 會從應用程式讀取結構描述，然後在 EMM 系統管理員主控台中公開該結構描述。 該主控台可讓 Intune 管理員設定結構描述中的設定。

在裝置上安裝 OEMConfig 應用程式時，該應用程式會使用 EMM 系統管理員中所設定的設定來管理該裝置。 裝置設定會由 OEMConfig 應用程式執行，而非由 EMM 所建置的 MDM 代理程式執行。

當 OEM 新增及改善管理功能時，OEM 也會更新 Google Play 中的應用程式。 身為系統管理員，您不需要等待 EMM 包含這些更新，便能取得這些新的功能和更新 (包括修正)。

> [!TIP]
> 您只能搭配支援 OEMConfig 且具有相對應 OEMConfig 應用程式的裝置使用此功能。 請連絡您的 OEM 以取得詳細資料。

## <a name="before-you-begin"></a>開始之前

使用 OEMConfig 時，請注意下列資訊：

- Intune 會公開 OEMConfig 應用程式的結構描述以供您加以設定。 Intune 不會驗證或變更應用程式所提供的結構描述。 因此，如果結構描述不正確，或具有不準確的資料，此資料仍然會傳送至裝置。 如果您找到源自結構描述的問題，請連絡 OEM 以取得指引。
- Intune 不會影響或控制應用程式結構描述的內容。 例如，Intune 無法對字串、語言、允許的動作等進行任何控制。 我們建議您連絡 OEM 以取得搭配 OEMConfig 來管理其裝置的詳細資訊。
- OEM 隨時可以更新其支援的功能和結構描述，並上傳新的應用程式至 Google Play。 Intune 一律會從 Google Play 同步最新版本的 OEMConfig 應用程式。 Intune 不會維護結構描述或應用程式的較舊版本。 如果您遇到版本衝突，建議您連絡 OEM 以取得詳細資訊。
- 為裝置指派單一 OEMConfig 設定檔。 如果為相同的裝置指派多個設定檔，您可能會遇到不一致的行為。 OEMConfig 模型針對每個裝置僅支援單一原則。

## <a name="prerequisites"></a>先決條件

若要在裝置上使用 OEMConfig，請確定您已滿足下列需求：

- 已在 Intune 中註冊的 Android Enterprise 裝置。
- 由 OEM 所建置並上傳至 Google Play 的 OEMConfig 應用程式。 如果其不在 Google Play 上，請連絡 OEM 以取得詳細資訊。
- Intune 管理員已具有 [行動應用程式]  、[裝置設定]  的角色型存取控制 (RBAC) 權限，以及 [Android for Work]  底下的「讀取」權限。 這些權限之所以為必要，是因為 OEMConfig 設定檔會使用受控應用程式設定來管理裝置設定。

## <a name="prepare-the-oemconfig-app"></a>準備 OEMConfig 應用程式

請確定裝置支援 OEMConfig，將正確的 OEMConfig 應用程式新增到 Intune，並將該應用程式安裝到裝置上。 請連絡 OEM 以取得此資訊。

> [!TIP] 
> OEMConfig 應用程式為 OEM 特定的。 例如，將 Sony 的 OEMConfig 應用程式安裝到 Zebra Technologies 裝置上並不會執行任何動作。

1. 從受控 Google Play 商店取得 OEMConfig 應用程式。 [將受控 Google Play 應用程式新增至 Android Enterprise 裝置](../apps/apps-add-android-for-work.md)列出步驟。
2. 某些 OEM 可能會以在裝置上預先安裝 OEMConfig 應用程式的方式出貨。 如果未預先安裝應用程式，請使用 Intune 來[新增應用程式並將其部署到裝置上](../apps/apps-deploy.md)。

## <a name="create-an-oemconfig-profile"></a>建立 OEMConfig 設定檔

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
3. 輸入下列內容：

    - **平台**：選取 [Android 企業]  。
    - **設定檔類型**：選取 [OEMConfig]  。

4. 選取 [建立]  。
5. 在 [基本資訊]  中，輸入下列內容：

    - **名稱**：為新的設定檔輸入描述性名稱。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **OEMConfig 應用程式**：選擇 [選取 OEMConfig 應用程式]  。

6. 在 [相關聯的應用程式]  中，選取您先前所新增的現有 OEMConfig 應用程式 > [選取]  。 請務必針對您要指派原則的裝置選擇正確的 OEMConfig 應用程式。

    如果您沒有看到任何列出的應用程式，請設定 [受控的 Google Play]，然後從受控 Google Play 商店取得應用程式。 [將受控 Google Play 應用程式新增至 Android Enterprise 裝置](../apps/apps-add-android-for-work.md)會列出步驟。

    > [!IMPORTANT]
    > 如果您新增 OEMConfig 應用程式並將其同步至 Google Play，但其沒有列為 [相關聯的應用程式]  ，您可能需要連絡 Intune 以將應用程式上架。 請參閱[新增應用程式](#supported-oemconfig-apps) (在此文章中)。

7. 選取 [下一步]  。
8. 在 [組態設定]  中，選取 [設定設計工具]  或 [JSON 編輯器]  ：

    > [!TIP]
    > 請參閱 OEM 文件以確保您能夠正確地設定屬性。 這些應用程式屬性是由 OEM 所包含，而非 Intune。 Intune 對屬性或是您所輸入的內容會進行最低限度的驗證。 例如，如果您針對連接埠號碼輸入 `abcd`，設定檔將會直接儲存，並搭配您所設定的值部署到您的裝置。 請確定您輸入的資訊是正確的。

    - **設定設計工具**：當您選取此選項時，系統會向您顯示應用程式結構描述內的可用屬性以供您設定。

      - 設定設計工具中的操作功能表會指出有更多選項可用。 例如，操作功能表可能會讓您新增、刪除及重新排列設定。 這些選項是由 OEM 所包含。 請務必閱讀 OEM 應用程式文件，以了解應該如何使用這些選項來建立設定檔。

      - 許多設定都有由 OEM 所提供的預設值。 若要查看是否有預設值，請將滑鼠暫留在設定旁邊的資訊圖示上。 工具提示會顯示該設定的預設值 (若適用的話)，以及由 OEM 所提供的詳細資料。

      - 按一下 [清除]  會從設定檔刪除設定。 如果設定不在設定檔中，套用設定檔時，其在裝置上的值將不會變更。

      - 如果您在設定設計工具中建立空的 (未設定的) 配套，系統會在切換至 JSON 編輯器時加以刪除。

    - **JSON 編輯器**：當您選取此選項時，JSON 編輯器即會開啟，並附帶內嵌在應用程式中的完整設定結構描述範本。 在編輯器中，搭配適用於不同設定的值自訂範本。 如果您使用 [設定設計工具]  來變更值，JSON 編輯器會使用來自 [設定設計工具] 的值覆寫範本。

      - 如果您更新現有設定檔，JSON 編輯器會顯示最後一次搭配設定檔儲存的設定。

      - OEMConfig 結構描述可能會很龐大且複雜。 如果您偏好使用不同的編輯器來更新這些設定，請選取 [下載 JSON 範本]  按鈕。 使用您偏好的編輯器來將設定值新增到範本。 然後，將您更新的 JSON 複製並貼到 [JSON 編輯器]  屬性。

      - 您可以使用 JSON 編輯器來建立設定的備份。 在您設定好設定之後，請使用此功能來取得具有您的值的 JSON 設定。 將 JSON 複製並貼到檔案中，然後加以儲存。 您現在有備份檔案了。

    在設定設計工具中所做的任何變更，也會自動在 JSON 編輯器中進行。 同樣地，在 JSON 編輯器中所做的任何變更，也會自動在設定設計工具中進行。 如果您的輸入包含無效的值，便無法在設定設計工具和 JSON 編輯器之間切換，直到您修正該問題為止。

9. 選取 [下一步]  。
10. 在 [範圍標籤]  (選擇性) 中，指派標籤來針對特定 IT 群組篩選設定檔，例如 `US-NC IT Team` 或 `JohnGlenn_ITDepartment`。 如需範圍標籤的詳細資訊，請參閱[針對分散式 IT 使用 RBAC 和範圍標籤](../fundamentals/scope-tags.md)。

    選取 [下一步]  。

11. 在 [指派]  中，選取將接收您設定檔的使用者或群組。 將一個設定檔指派到每部裝置。 OEMConfig 模型針對每個裝置僅支援單一原則。

    如需指派設定檔的詳細資訊，請參閱[指派使用者和裝置設定檔](device-profile-assign.md)。

    選取 [下一步]  。

12. 在 [檢閱 + 建立]  中，檢閱您的設定。 當您選取 [建立]  時，系統會儲存您的變更，然後指派設定檔。 原則也會顯示在設定檔清單中。

當裝置下一次檢查設定更新時，您所設定的 OEM 特定設定將會套用到 OEMConfig 應用程式。

> [!NOTE]
> OEMConfig 標準目前不會包含狀態報告。 因此根據預設，設定檔會顯示 [擱置]  狀態。

## <a name="supported-oemconfig-apps"></a>支援的 OEMConfig 應用程式

與標準應用程式相比，OEMConfig 應用程式會擴充 Google 所授與的受控設定權限，以支援更複雜的結構描述。 Intune 目前支援下列 OEMConfig 應用程式：

-----------------

| OEM | 套件組合識別碼 | OEM 文件 (若有的話) |
| --- | --- | ---|
| Samsung | com.samsung.android.knox.kpu | [Knox Service Plugin 系統管理指南](https://docs.samsungknox.com/knox-service-plugin/admin-guide/index.htm) \(英文\) |
| Zebra Technologies | com.zebra.oemconfig.common | [Zebra OEMConfig 概觀](http://techdocs.zebra.com/oemconfig ) \(英文\) |
| Datalogic | com.datalogic.oemconfig | [Datalogic OEMConfig 的使用者文件](https://datalogic.github.io/oemconfig/) \(英文\) |
| Honeywell | com.honeywell.oemconfig |  |
| Kyocera | jp.kyocera.enterprisedeviceconfig |  |
| Spectralink - Barcodes | com.spectralink.barcode.service |  |
| Spectralink - Buttons | com.spectralink.buttons |  |
| Spectralink - Device | com.spectralink.slnkdevicesettings  |  |
| Spectralink - Logging | com.spectralink.slnklogger |  |
| Spectralink - VQO | com.spectralink.slnkvqo |  |
| Seuic | com.seuic.seuicoemconfig | |
| Unitech Electronics | com.unitech.oemconfig | |

-----------------

如果您的裝置上存在 OEMConfig 應用程式，但其沒有列於上表中，或是沒有顯示在 Intune 主控台中，請傳送電子郵件到 `IntuneOEMConfig@microsoft.com`。

> [!NOTE]
> OEMConfig 應用程式必須先由 Intune 上架，才能搭配 OEMConfig 設定檔進行設定。 在支援該應用程式之後，您不需要連絡 Microsoft 便能在租用戶中加以設定。 只要依照此頁面上的指示執行即可。
>
> 如果 OEMConfig 應用程式的行為不正確，請連絡 OEMConfig 應用程式的開發人員。 Intune 對個別 OEMConfig 應用程式的技術問題概不負責。

## <a name="next-steps"></a>後續步驟

[監視設定檔狀態](device-profile-monitor.md)。
