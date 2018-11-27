---
title: 在 Microsoft Intune 中設定註冊限制
titlesuffix: ''
description: 在 Intune 中限制不同平台的註冊以及設定裝置註冊限制。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d9a7ad5d77f0c085fc1e91b6991657e6b848b3f3
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187832"
---
# <a name="set-enrollment-restrictions"></a>設定註冊限制

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

身為 Intune 系統管理員，您可以建立和管理註冊限制，定義可以註冊使用 Intune 管理的裝置數目和類型。 您可以建立多項限制，並將它們套用至不同的使用者群組。 您可以設定不同限制的[優先順序](#change-enrollment-restriction-priority)。

>[!NOTE]
>註冊限制不是安全性功能。 遭盜用的裝置可以冒用身分。 這些限制是非惡意使用者的最佳屏障。

您可以建立的特定註冊限制包括：

- 已註冊裝置的數目上限。
- 可以註冊的裝置平台：
  - Android
  - Android 工作設定檔
  - iOS
  - macOS
  - Windows
- iOS、Android、Android 工作設定檔和 Windows 的平台作業系統版本。 (只能使用 Windows 10 版本。 如果允許 Windows 8.1，請保留空白。)
  - 最低版本。
  - 最高版本。
- 限制個人擁有的裝置 (僅限 iOS、Android、Android 工作設定檔、macOS、Windows)。

## <a name="default-restrictions"></a>預設限制

裝置類型和裝置限制註冊限制都會自動提供預設限制。 您可以變更預設選項。 預設限制適用於所有使用者和無使用者註冊。 您可以使用較高的優先順序建立新的限制，覆寫這些預設值。

## <a name="create-a-restriction"></a>建立限制

1. 登入 Azure 入口網站。
2. 選取 [更多服務] 並搜尋 **Intune**，然後選擇 [Intune]。
3. 選取 [裝置註冊] > [註冊限制]。
4. 選取 [建立限制]。
5. 提供限制的名稱和描述。
6. 選擇 [限制類型]，然後選取 [建立]。
7. 針對裝置限定限制，請選取 [裝置限制] 設定使用者能夠註冊的裝置數上限。
8. 針對裝置類型限制，請選取 [平台] 和 [平台設定] 允許或封鎖各種平台和版本。
9. 選取 [指派] > [+ 選取群組]。
10. 在 [選取群組] 下，選取一或多個群組，然後選擇 [選取]。 限制只適用於指派的群組。 如果限制不指派給至少一個群組，就不會產生任何效果。
11. 選取 [儲存]。
12. 新建立的限制優先順序剛好在預設值前。 您可以[變更優先順序](#change-enrollment-restriction-priority)。

## <a name="set-device-type-restrictions"></a>設定裝置類型限制

您可以遵循下列步驟，變更裝置類型限制的設定。 這些限制不會影響已註冊的裝置。 使用此功能無法封鎖使用 [Intune PC 代理程式](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune)所註冊的裝置。

1. 登入 Azure 入口網站。
2. 選取 [更多服務] 並搜尋 **Intune**，然後選擇 [Intune]。
3. 選取 [裝置註冊] > [註冊限制]。
4. 在 [裝置類型限制] 下 > 選擇您想要設定的限制 > [屬性] > [選取平台]。 為每個列出的平台選擇 [允許] 或 [封鎖]。
    ![允許或封鎖平台的螢幕擷取畫面](media/enrollment-restrictions-set/platform-allow-block.png)
5. 選擇 [確定]。
6. 選擇 [設定平台]。
    ![設定平台的螢幕擷取畫面](media/enrollment-restrictions-set/configure-platforms.png)
7. 選擇所列平台的最低和最高**版本**。 支援的版本格式包含：
    - Android 工作設定檔支援 major.minor.rev.build。
    - iOS 支援 major.minor.rev。作業系統版本不適用於以裝置註冊計劃、Apple School Manager 或 Apple Configurator 應用程式註冊的 Apple 裝置。
    - Windows 支援 major.minor.rev.build，僅限 Windows 10。
8. 選擇要 [允許] 還是 [封鎖] 每個平台列出的**個人所有**裝置。
9. 選擇 [確定]。

### <a name="blocking-personal-android-devices"></a>封鎖個人 Android 裝置
- 若您從註冊封鎖個人擁有的 Android 裝置，則個人擁有的 Android 工作設定檔裝置仍可以註冊。
- 根據預設，Android 工作設定檔裝置設定與您的 Android 裝置設定相同。 變更 Android 工作設定檔設定後，就不再是那麼回事了。
- 若您封鎖個人的 Android 工作設定檔註冊，則只有公司的 Android 裝置可以註冊為 Android 工作設定檔。

### <a name="blocking-personal-windows-devices"></a>封鎖個人 Windows 裝置
如果您從註冊封鎖個人擁有的 Windows 裝置，Intune 會檢查以確定每個新的 Windows 註冊要求都已獲授權為公司註冊。 將會封鎖未經授權的註冊。

下列方法限定成授權為 Windows 公司註冊：
 - 註冊使用者會使用[裝置註冊管理員帳戶]( device-enrollment-manager-enroll.md)。
- 裝置透過 [Windows AutoPilot](enrollment-autopilot.md) 註冊。
- 裝置已透過 Windows Autopilot 註冊，但不是 Windows 設定中的 [僅限 MDM 註冊] 選項。
- 裝置的 IMEI 編號列在 [裝置註冊] > [[公司裝置識別碼](corporate-identifiers-add.md)] (不支援 Windows Phone 8.1)。
- 裝置透過[大量佈建套件](windows-bulk-enroll.md)註冊。
- 裝置透過[從 SCCM 自動註冊以共同管理](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management.md)註冊。
 
Intune 將下列註冊標示為公司，但因為它們未將每個裝置控制提供給 Intune 系統管理員，因此將會予以封鎖：
 - [自動 MDM 註冊](windows-enroll.md#enable-windows-10-automatic-enrollment)，透過[在 Windows 安裝期間的 Azure Active Directory 加入](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*。
- [自動 MDM 註冊](windows-enroll.md#enable-windows-10-automatic-enrollment)，透過[從 Windows 設定的 Azure Active Directory 加入](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*。
 
也會封鎖下列個人註冊方法：
- [自動 MDM 註冊](windows-enroll.md#enable-windows-10-automatic-enrollment)，透過[從 Windows 設定新增公司帳戶](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*。
- [僅限 MDM 註冊]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device)選項，來自 Windows 設定。

\* 如果透過 Autopilot 註冊，這些裝置將不會遭到封鎖。

## <a name="set-device-limit-restrictions"></a>設定裝置限制

您可以遵循下列步驟變更裝置限制的設定：

1. 登入 Azure 入口網站。
2. 選取 [更多服務] 並搜尋 **Intune**，然後選擇 [Intune]。
3. 選取 [裝置註冊] > [註冊限制]。
4. 在 [裝置限制] 下選擇您想要設定的限制。
5. 選取 [裝置限制]，然後在下拉式清單中，選取使用者可以註冊的裝置數目上限。
    ![具有裝置限制的 [device limit restrictions] (裝置數量限制) 刀鋒視窗](./media/device-restrictions-limit.png)
6. 選取 [儲存]。


使用者會看到通知，告訴他們何時符合其已註冊裝置的限制。 例如，在 iOS 上，它看起來會像這樣：

![iOS 裝置限制通知](./media/enrollment-restrictions-ios-set-limit-notification.png)

## <a name="change-enrollment-restriction-priority"></a>變更註冊限制優先順序

當使用者屬於多個指派限制的群組時，會使用優先順序。 使用者只受制於所屬群組被指派的最高優先順序限制。 例如，Joe 屬於指派了優先順序 5 限制的群組 A，也屬於指派了優先順序 2 限制的群組 B。 Joe 只受制於優先順序 2 限制。

當您建立一項限制時，它會新增至清單，剛好高預設值一階。

裝置註刪包括裝置類型和裝置限制的預設限制。 除非為更高的優先順序限制所覆寫，否則這兩項限制適用於所有使用者。

您可以變更任何非預設限制的優先順序。

1. 登入 Azure 入口網站。
2. 選取 [更多服務] 並搜尋 **Intune**，然後選擇 [Intune]。
3. 選取 [裝置註冊] > [註冊限制]。
4. 將滑鼠停留在優先順序清單的限制上。
5. 使用三個垂直點，將優先順序拖曳到所要的清單位置。
