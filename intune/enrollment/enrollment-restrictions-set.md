---
title: 在 Microsoft Intune 中設定註冊限制
titleSuffix: ''
description: 在 Intune 中限制不同平台的註冊以及設定裝置註冊限制。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4246dab0cf22053d76fdd50f99de53e827332a23
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547823"
---
# <a name="set-enrollment-restrictions"></a>設定註冊限制

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

身為 Intune 管理員，您可以建立及管理註冊限制，定義哪些裝置可向 Intune 註冊以進行管理，包括：
- 裝置數目。
- 作業系統和版本。

您可以建立多項限制，並將它們套用至不同的使用者群組。 您可以設定不同限制的[優先順序](#change-enrollment-restriction-priority)。

>[!NOTE]
>註冊限制不是安全性功能。 遭盜用的裝置可以冒用身分。 這些限制是非惡意使用者的最佳屏障。

您可以建立的特定註冊限制包括：

- 已註冊裝置的數目上限。
- 可以註冊的裝置平台：
  - Android 裝置管理員
  - Android Enterprise 工作設定檔
  - iOS
  - macOS
  - Windows
  - Windows Mobile
- iOS、Android 裝置管理員、Android Enterprise 工作設定檔、Windows 和 Windows Mobile 的平台作業系統版本。 (只能使用 Windows 10 版本。 如果允許 Windows 8.1，請保留空白。)
  - 最低版本。
  - 最高版本。
- 限制[個人擁有的裝置](device-enrollment.md#bring-your-own-device) (僅限 iOS、Android 裝置管理員、Android Enterprise 工作設定檔、macOS、Windows 與 Windows Mobile)。

## <a name="default-restrictions"></a>預設限制

裝置類型和裝置限制註冊限制都會自動提供預設限制。 您可以變更預設選項。 預設限制適用於所有使用者和無使用者註冊。 您可以使用較高的優先順序建立新的限制，覆寫這些預設值。

## <a name="create-a-device-type-restriction"></a>建立裝置類型限制

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431) > [裝置]   > [註冊限制]   > [建立限制]   > [裝置類型限制]  。
2. 在 [基本]  頁面上，為限制提供 [名稱]  與選擇性的 [描述]  。
3. 選擇 [下一步]  以移至 [平台設定]  頁面。
4. 在 [平台]  底下，針對您想要此限制允許的平台，選擇 [允許]  。
    ![選擇平台設定的螢幕擷取畫面](./media/enrollment-restrictions-set/choose-platform-settings.png)
5. 在 [版本]  底下，選擇您希望可允許平台支援的最低與最高版本。 版本限制僅適用於已向公司入口網站註冊的裝置。
     支援的版本格式包含：
    - Android 裝置管理員與 Android Enterprise 工作設定檔支援 major.minor.rev.build。
    - iOS 支援 major.minor.rev。作業系統版本不適用於以裝置註冊計劃、Apple School Manager 或 Apple Configurator 應用程式註冊的 Apple 裝置。
    - Windows 支援 major.minor.build.rev，僅限 Windows 10。
    
    > [!IMPORTANT]
    > Android Enterprise (工作設定檔) 和 Android 裝置系統管理員平台具有下列行為：
    > - 如果同時針對相同的群組允許這兩個平台，則在使用者裝置支援的情況下，系統會搭配工作設定檔註冊該使用者，否則會以 DA 的形式註冊他們。 
    > - 如果同時針對群組允許這兩個平台，並針對特定及非重疊版本進行微調，則使用者將會接收到針對其 OS 版本所定義的註冊流程。 
    > - 如果同時允許這兩個平台，但針對相同的版本進行封鎖，則系統會將使用具有已封鎖版本之裝置的使用者從 Android 裝置系統管理員註冊流程中移除，並封鎖其註冊能力，然後提示以要求登出。 
    >
    > 值得注意的是，除非已在 [Android 註冊] 中完成適當的必要條件，否則工作設定檔和裝置系統管理員註冊都會無法正常執行。 
    
   > [!Note]
   > Windows 10 不會在註冊期間提供修訂編號，所以舉例來說，如果您輸入 10.0.17134.100 而裝置為 10.0.17134.174，則裝置在註冊期間將會被封鎖。

6. 在 [個人所擁有]  底下，針對您想要允許作為個人擁有裝置的平台，選擇 [允許]  。
7. 選擇 [下一步]  以移至 [指派]  頁面。
8. 選擇 [選取要納入的群組]  ，然後使用搜尋方塊來尋找您想要納入此限制的群組。 限制只適用於指派的群組。 如果限制不指派給至少一個群組，就不會產生任何效果。 然後選擇 [選取]  。 
    ![選擇平台設定的螢幕擷取畫面](./media/enrollment-restrictions-set/select-groups.png)
9. 選取 [下一步]  以移至 [檢閱 + 建立]  頁面。
10. 選取 [建立]  以建立限制。
11. 新建立的限制優先順序剛好在預設值前。 您可以[變更優先順序](#change-enrollment-restriction-priority)。


## <a name="create-a-device-limit-restriction"></a>建立裝置限制的限制

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431) > [裝置]   > [註冊限制]   > [建立限制]   > [裝置限制的限制]  。
2. 在 [基本]  頁面上，為限制提供 [名稱]  與選擇性的 [描述]  。
3. 選擇 [下一步]  以移至 [裝置限制]  頁面。
4. 針對 [裝置限制]  ，選取使用者可以註冊的裝置數目上限。
    ![選擇裝置限制的螢幕擷取畫面](./media/enrollment-restrictions-set/choose-device-limit.png)
5. 選擇 [下一步]  以移至 [指派]  頁面。
6. 選擇 [選取要納入的群組]  ，然後使用搜尋方塊來尋找您想要納入此限制的群組。 限制只適用於指派的群組。 如果限制不指派給至少一個群組，就不會產生任何效果。 然後選擇 [選取]  。 
    ![選取群組的螢幕擷取畫面](./media/enrollment-restrictions-set/select-groups-device-limit.png)
7. 選取 [下一步]  以移至 [檢閱 + 建立]  頁面。
8. 選取 [建立]  以建立限制。
9. 新建立的限制優先順序剛好在預設值前。 您可以[變更優先順序](#change-enrollment-restriction-priority)。

在 BYOD 註冊期間，當使用者達到已註冊裝置的限制時，他們會看到通知。 例如，在 iOS 上：

![iOS 裝置限制通知](./media/enrollment-restrictions-set/enrollment-restrictions-ios-set-limit-notification.png)

> [!IMPORTANT]
> 裝置限制不適用於下列 Windows 註冊類型：
> - 共同受控註冊
> - GPO 註冊
> - 加入 Azure Active Directory 的註冊
> - 加入大量 Azure Active Directory 的註冊
> - Autopilot 註冊
> - 裝置註冊管理員註冊
>
> 系統不會針對這些註冊類型強制執行裝置限制的限制，因為會將它們視為共用裝置案例。
> 您可以[在 Azure Active Directory 中](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal#configure-device-settings)，設定這些註冊類型的固定限制。


## <a name="change-enrollment-restrictions"></a>變更註冊限制

您可以遵循下列步驟來變更註冊限制的設定。 這些限制不會影響已經註冊的裝置。 使用此功能無法封鎖使用 [Intune PC 代理程式](../fundamentals/manage-windows-pcs-with-microsoft-intune.md)所註冊的裝置。

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431) > [裝置]   > [註冊限制]  > 選擇要變更的限制 > [屬性]  。
2. 選擇您要變更之設定旁邊的 [編輯]  。
3. 在 [編輯]  頁面上進行所需的變更並繼續前往 [檢閱並儲存]  頁面，然後選擇 [儲存]  。


## <a name="blocking-personal-android-devices"></a>封鎖個人 Android 裝置
- 若您封鎖個人擁有的 Android 裝置管理員裝置進行註冊，則個人擁有的 Android Enterprise 工作設定檔裝置仍能註冊。
- 根據預設，您的 Android Enterprise 工作設定檔裝置設定會與您的 Android 裝置管理員裝置的設定相同。 當您變更 Android Enterprise 工作設定檔或 Android 裝置管理員設定之後，情況就不再是如此。
- 若您封鎖個人的 Android 工作設定檔註冊，則只有公司擁有的 Android 裝置可以使用 Android Enterprise 工作設定檔進行註冊。

## <a name="blocking-personal-windows-devices"></a>封鎖個人 Windows 裝置
如果您從註冊封鎖個人擁有的 Windows 裝置，Intune 會檢查以確定每個新的 Windows 註冊要求都已獲授權為公司註冊。 將會封鎖未經授權的註冊。

下列方法限定成授權為 Windows 公司註冊：
- 註冊使用者會使用[裝置註冊管理員帳戶]( device-enrollment-manager-enroll.md)。
- 裝置透過 [Windows Autopilot](enrollment-autopilot.md) 註冊。
- 裝置已向 Windows Autopilot 註冊，但不是 Windows 設定中的 [僅限 MDM 註冊] 選項。
- 裝置的 IMEI 編號列在 [裝置註冊]   > [[公司裝置識別碼](corporate-identifiers-add.md)]  (不支援 Windows Phone 8.1)。
- 裝置透過[大量佈建套件](windows-bulk-enroll.md)註冊。
- 裝置透過 GPO 註冊，或透過[從 Configuration Manager 自動註冊以共同管理](https://docs.microsoft.com/configmgr/comanage/quickstart-paths#bkmk_path1)方式註冊。
 
Intune 會將下列註冊標示為公司。 但是，因為它們不會為 Intune 系統管理員提供每個裝置的控制，因此會遭到封鎖：
- [自動 MDM 註冊](windows-enroll.md#enable-windows-10-automatic-enrollment)，透過[在 Windows 安裝期間的 Azure Active Directory 加入](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*。
- [自動 MDM 註冊](windows-enroll.md#enable-windows-10-automatic-enrollment)，透過[從 Windows 設定的 Azure Active Directory 加入](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*。
 
也會封鎖下列個人註冊方法：
- [自動 MDM 註冊](windows-enroll.md#enable-windows-10-automatic-enrollment)，透過[從 Windows 設定新增公司帳戶](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*。
- [僅限 MDM 註冊]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device)選項，來自 Windows 設定。

\* 如果透過 Autopilot 註冊，這些裝置將不會遭到封鎖。


## <a name="blocking-personal-ios-devices"></a>封鎖個人 iOS 裝置
根據預設，Intune 會將 iOS 裝置分類為個人擁有。 若要分類為公司所有，iOS 裝置必須符合下列其中一項條件：
- 已使用序號或 IMEI 註冊。
- 使用自動裝置註冊 (先前為裝置註冊計劃) 註冊


## <a name="change-enrollment-restriction-priority"></a>變更註冊限制優先順序

當使用者屬於多個指派限制的群組時，會使用優先順序。 使用者只受制於所屬群組被指派的最高優先順序限制。 例如，Joe 屬於指派了優先順序 5 限制的群組 A，也屬於指派了優先順序 2 限制的群組 B。 Joe 只受制於優先順序 2 限制。

當您建立一項限制時，它會新增至清單，剛好高預設值一階。

裝置註刪包括裝置類型和裝置限制的預設限制。 除非為更高的優先順序限制所覆寫，否則這兩項限制適用於所有使用者。

您可以變更任何非預設限制的優先順序。

1. 登入 Azure 入口網站。
2. 選取 [更多服務]  並搜尋 **Intune**，然後選擇 [Intune]  。
3. 選取 [裝置註冊]   > [註冊限制]  。
4. 將滑鼠停留在優先順序清單的限制上。
5. 使用三個垂直點，將優先順序拖曳到所要的清單位置。
