---
title: 在 Microsoft Intune 中使用 Android Enterprise 裝置上的 OEMConfig - Azure | Microsoft Docs
description: 使用 Microsoft Intune 來管理及使用執行 Android Enterprise with OEMConfig 的裝置。 請參閱所有步驟，包括總覽、查看必要條件、在 Intune 中建立設定檔，以及查看支援的 OEMConfig 應用程式清單。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c3108364850641cd85abf6b97a2b981735f59895
ms.sourcegitcommit: 8934b1abec96e18cee15a77107d37551766f7666
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71303900"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>在 Microsoft Intune 中使用和管理 Android 企業裝置與 OEMConfig

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

在 Microsoft Intune 中，您可以使用 OEMConfig 來新增、建立和自訂 Android 企業裝置的 OEM 特定設定。 OEMConfig 通常用來設定未內建在 Intune 中的設定。 不同的原始設備製造商（OEM）包含不同的設定。 可用的設定取決於 OEM 在其 OEMConfig 應用程式中包含的內容。

本功能適用於：  

- Android 企業

本文說明 OEMConfig、列出必要條件、示範如何建立設定設定檔，以及在 Intune 中列出支援的 OEMConfig 應用程式。

## <a name="overview"></a>概觀

OEMConfig 原則是一種特殊類型的裝置設定原則，類似于[應用程式設定原則](app-configuration-policies-overview.md)。 OEMConfig 是 Google 所定義的標準，利用 Android 中的應用程式設定，將裝置設定傳送給 Oem 所撰寫的應用程式（原始設備製造商）。 此標準可讓 Oem 和 Emm （企業行動管理）以標準化的方式建立和支援 OEM 特定的功能。 [深入瞭解 OEMConfig](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/)。

在過去，Emm （如 Intune）在 OEM 推出後，會以手動方式建立 OEM 特有功能的支援。 這種方法會導致重複的工作和採用速度變慢。

使用 OEMConfig，OEM 會建立架構來定義 OEM 特定的管理功能。 OEM 會將架構內嵌到應用程式中，然後將此應用程式放在 Google Play 上。 EMM 會從應用程式讀取架構，並在 EMM 系統管理員主控台中公開架構。 主控台可讓 Intune 系統管理員設定架構中的設定。

當 OEMConfig 應用程式安裝在裝置上時，它會使用 EMM 系統管理員主控台中設定的設定來管理裝置。 裝置上的設定是由 OEMConfig 應用程式執行，而不是由 EMM 所建立的 MDM 代理程式。

當 OEM 新增並改善管理功能時，OEM 也會更新 Google Play 中的應用程式。 身為系統管理員，您可以取得這些新功能和更新（包括修正），而不需要等待 Emm 包含這些更新。

> [!TIP]
> 您只能將 OEMConfig 與支援這項功能的裝置搭配使用，並具有對應的 OEMConfig 應用程式。 請參閱您的 OEM 以取得特定的詳細資料。

## <a name="before-you-begin"></a>開始之前

使用 OEMConfig 時，請注意下列資訊：

- Intune 會公開 OEMConfig 應用程式的架構，讓您可以進行設定。 Intune 不會驗證或變更應用程式所提供的架構。 因此，如果架構不正確或資料不准確，則此資料仍會傳送到裝置。 如果您發現源自于架構的問題，請洽詢 OEM 以取得指導方針。
- Intune 不會影響或控制應用程式架構的內容。 例如，Intune 不會對字串、語言、允許的動作等等進行任何控制。 我們建議您與 OEM 聯絡，以取得使用 OEMConfig 管理其裝置的詳細資料和最佳作法。
- Oem 可以隨時更新其支援的功能和架構，並將新的應用程式上傳至 Google Play。 Intune 一律會從 Google Play 同步處理最新版本的 OEMConfig 應用程式。 Intune 不會維護較舊版本的架構或應用程式。 如果您遇到版本衝突，建議您聯繫 OEM 以取得詳細資訊。
- 將一個 OEMConfig 設定檔指派給裝置。 如果將多個設定檔指派給相同的裝置，您可能會看到不一致的行為。 OEMConfig 模型只支援每個裝置一個原則。

## <a name="prerequisites"></a>必要條件

若要在您的裝置上使用 OEMConfig，請確定您具有下列需求：

- 在 Intune 中註冊的 Android 企業裝置。
- OEM 所建立的 OEMConfig 應用程式，並上傳至 Google Play。 如果不在 Google Play 上，請洽詢 OEM 以取得詳細資訊。
- Intune 管理員具有**Mobile apps**和**DeviceConfigurations**的角色型存取控制（RBAC）許可權。 這些許可權是必要的，因為 OEMConfig 設定檔會使用受管理的應用程式設定來管理裝置設定。

## <a name="prepare-the-oemconfig-app"></a>準備 OEMConfig 應用程式

請確定裝置支援 OEMConfig、將正確的 OEMConfig 應用程式新增至 Intune，並將應用程式安裝在裝置上。 請洽詢 OEM 以取得此資訊。

> [!TIP] 
> OEMConfig 應用程式是 OEM 專用的。 例如，安裝在 Zebra 技術裝置上的索尼 OEMConfig 應用程式不會執行任何動作。

1. 從受控 Google Play 商店取得 OEMConfig 應用程式。 [將受控 Google Play 應用程式新增至 Android Enterprise 裝置](apps-add-android-for-work.md)列出步驟。
2. 有些 Oem 可能會隨附預先安裝 OEMConfig 應用程式的裝置。 如果未預先安裝應用程式，請使用 Intune[將應用程式新增並部署至裝置](apps-deploy.md)。

## <a name="create-an-oemconfig-profile"></a>建立 OEMConfig 設定檔

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
3. 輸入下列內容：

    - **名稱**：為新的設定檔輸入描述性名稱。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取 [Android 企業]  。
    - **配置檔案類型**：選取 [ **OEMConfig**]。

4. 選取 [**相關聯的應用程式**]，選取您先前新增的現有 OEMConfig 應用程式 > **[確定]** 。 請務必為您要指派原則的裝置選擇正確的 OEMConfig 應用程式。

    如果您沒有看到任何列出的應用程式，則設定受控 Google Play，並從受管理的 Google Play 存放區取得應用程式。 [將受控 Google Play 應用程式新增至 Android Enterprise 裝置](apps-add-android-for-work.md)列出步驟。

    > [!IMPORTANT]
    > 如果您已新增 OEMConfig 應用程式，並將其同步至 Google Play，但未列為**相關聯的應用程式**，您可能必須聯絡 Intune 以將應用程式上架。 請參閱[新增應用程式](#supported-oemconfig-apps)（在本文中）。

5. 在 [**使用設定**] 中，選擇使用 [設定**設計**工具] 或 [ **JSON 編輯器**]：

    > [!TIP]
    > 請閱讀 OEM 檔，以確定您是正確設定屬性。 這些應用程式屬性是由 OEM 所包含，而不是 Intune。 Intune 會對屬性進行最低限度的驗證，或您輸入的內容。 例如，如果您為埠號碼輸入 `abcd`，則設定檔會依當時的方式儲存，並使用您設定的值部署至您的裝置。 請務必輸入正確的資訊。

    - 設定**設計**工具：當您選取此選項時，會顯示應用程式架構內可用的屬性，供您設定。

      - 設定設計工具中的內容功能表表示有更多可用的選項。 例如，內容功能表可讓您新增、刪除和重新排列設定。 OEM 會包含這些選項。 請務必閱讀 OEM 應用程式檔，以瞭解如何使用這些選項來建立設定檔。

      - 許多設定都具有 OEM 提供的預設值。 若要查看是否有預設值，請將滑鼠停留在設定旁的資訊圖示上。 [工具提示] 會顯示該設定的預設值（如果適用的話），以及 OEM 提供的更多詳細資料。

      - 按一下 [**清除**] 會刪除設定檔中的設定。 如果設定不在設定檔中，當套用設定檔時，裝置上的值將不會變更。
        
      - 如果您在設定設計工具中建立空的（未設定）組合，則會在切換至 JSON 編輯器時予以刪除。

    - **Json 編輯器**：當您選取此選項時，json 編輯器會開啟，其中包含內嵌在應用程式中的完整設定架構範本。 在編輯器中，使用不同設定的值自訂範本。 如果您使用設定**設計**工具來變更您的值，JSON 編輯器會以設定設計工具中的值來覆寫範本。
    
      - 如果您要更新現有的設定檔，JSON 編輯器會顯示上次與設定檔一起儲存的設定。

      - OEMConfig 架構可能很大而且複雜。 如果您想要使用不同的編輯器來更新這些設定，請選取 [**下載 JSON 範本**] 按鈕。 使用您選擇的編輯器，將您的設定值新增至範本。 然後，將您已更新的 JSON 複製並貼到**JSON 編輯器**屬性中。

      - 您可以使用 JSON 編輯器來建立設定的備份。 進行設定之後，請使用此功能以您的值取得 JSON 設定。 將 JSON 複製並貼到檔案中，並加以儲存。 現在您已有備份檔案。

    在設定設計工具中所做的任何變更也會在 JSON 編輯器中自動進行。 同樣地，在 [JSON 編輯器] 中所做的任何變更都會自動在設定設計工具中進行。 如果您的輸入包含不正確值，您就無法在 [設定設計工具] 和 [JSON 編輯器] 之間切換，直到您修正問題為止。

6. 選取**確定** > **新增** 以儲存變更。 原則隨即建立，並顯示在清單中。

請確認會[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

 > [!NOTE]
 > 將一個設定檔指派到每部裝置。 OEMConfig 模型僅針對每個裝置支援一個原則。

下一次裝置檢查設定更新時，您所設定的 OEM 特定設定會套用至 OEMConfig 應用程式。

> [!NOTE]
> OEMConfig 標準目前不包含狀態報表。 因此，根據預設，設定檔會顯示 [**暫**止] 狀態。

## <a name="supported-oemconfig-apps"></a>支援的 OEMConfig 應用程式

相較于標準應用程式，OEMConfig apps 會擴充 Google 授與的受管理設定許可權，以支援更複雜的架構。 Intune 目前支援下列 OEMConfig 應用程式：

-----------------

| OEM | 套件組合識別碼 | OEM 檔（如果有的話） |
| --- | --- | ---|
| Samsung | .com. knox. kpu | [Knox 服務外掛程式管理指南](https://docs.samsungknox.com/knox-service-plugin/admin-guide/welcome.htm) |
| Zebra 技術 | zebra. oemconfig common | [Zebra OEMConfig 總覽](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | datalogic. oemconfig | [Datalogic OEMConfig 的使用者檔](https://datalogic.github.io/oemconfig/) |
| Honeywell | honeywell. oemconfig |  |

-----------------

如果您的裝置有 OEMConfig 應用程式，但它不在上表中，或未顯示在 Intune 主控台中，請以電子郵件 `IntuneOEMConfig@microsoft.com`。

> [!NOTE]
> OEMConfig apps 必須在 Intune 內部上線，才能使用 OEMConfig 設定檔來設定。 一旦支援應用程式，您就不需要與 Microsoft 連線，就能在您的租使用者中設定它。 請遵循此頁面上的指示。

## <a name="next-steps"></a>後續步驟

- [指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
