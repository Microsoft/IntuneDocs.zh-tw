---
title: 服務台疑難排解入口網站
titleSuffix: Microsoft Intune
description: 服務台人員使用疑難排解入口網站來解決使用者的技術問題。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/11/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a4e6cbf2d9edcff83ae756c2dbcf098cae0ae54
ms.sourcegitcommit: 73fbecf7cee4fdfc37d3c30ea2007d2a9a6d2d12
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "71301866"
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>使用疑難排解入口網站協助您公司的使用者

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

疑難排解入口網站可協助技術服務人員和 Intune 系統管理員檢視使用者資訊，以解決使用者協助要求。 包含技術服務人員的組織，可以指派**技術支援中心操作員**給使用者群組。 技術支援中心操作員角色現在可以使用 [疑難排解]  窗格。

[疑難排解]  窗格也會顯示使用者的註冊問題。 其中包含問題的詳細資料與建議的補救步驟，可協助系統管理員和技術服務人員針對相關問題進行疑難排解。 未擷取特定註冊問題，某些錯誤可能也沒有補救建議。

如需新增技術支援中心操作員角色的步驟，請參閱[以角色為基礎的系統管理 (RBAC) 搭配 Intune](/intune/role-based-access-control)

當使用者向支援人員諮詢 Intune 的技術問題時，技術支援中心操作員會輸入使用者的名稱。 Intune 會顯示可協助解決許多第 1 層問題的實用資料，包括：

- 使用者狀態
- 作業
- 相容性問題
- 裝置沒有回應
- 裝置無法取得 VPN 或 Wi-Fi 設定
- 應用程式安裝失敗

## <a name="to-review-troubleshooting-details"></a>檢閱疑難排解詳細資料

在 [疑難排解] 窗格中，選擇 [選取使用者]  來檢視使用者資訊。 使用者資訊可協助您了解使用者與其裝置的目前狀態。  

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在 [Intune]  窗格上，選擇 [疑難排解]  。
4. 按一下 [選取]  選取使用者進行疑難排解。
5. 鍵入名稱或電子郵件地址來選取使用者。 按一下 [選取]  。 在 [疑難排解] 窗格中，會顯示使用者的疑難排解資訊。 下表說明該資訊。

> [!Note]  
> 您也可以將瀏覽器指向 [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting)來存取 [疑難排解]  窗格。

## <a name="areas-of-troubleshooting-dashboard"></a>疑難排解儀表板的區域

您可以使用 [疑難排解]  窗格檢閱使用者資訊。

![針對儀表板進行疑難排解，並使用下表所述的編號區域](/intune/media/troubleshooting-dash.png)

| 區域 | 名稱 | 說明 |
| ---  | ---  | ---         |
| 1.   | 帳戶狀態  | 顯示目前 Intune 租用戶的狀態是 [使用中]  或 [非使用中]  。       |
| 2.   | 使用者選取  | 目前所選使用者的名稱。 按一下 [變更使用者]  選擇新的使用者。       |
| 3.   | 使用者狀態  | 顯示使用者的 Intune 授權狀態、裝置數目、每部裝置的合規性、應用程式數目，以及應用程式合規性。       |
| 4.   | 使用者資訊  | 使用清單來選取要在窗格中檢閱的詳細資料。 <br>您可以選取： <ul><li>用戶端應用程式<li>合規性政策<li> 設定原則<li>應用程式防護原則 <li>註冊限制</ul>      |
| 5.   | 群組成員資格  | 顯示所選使用者所屬的目前群組。       |

<!-- this section needs to be updated

## Client apps reference

The apps that are running devices
- managed by Intune and Azure Active Directory (AD) 
- owned by users managed by Intune and Azure Active Directory (AD).

### Properties

The properties of client apps.

| Property      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name          | The name of the application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| OS            | The operating system installed on the device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Type          | You can choose an assignment type for each app.  <br> **Available** - Users install the app from the Company Portal app or website.  <br> **Not Applicable** - The app is not installed or shown in the Company Portal. <br> **Uninstall** - The app is uninstalled from devices in the selected groups.  <br> **Available with or without enrollment** - Assign this app to groups of users whose devices are not enrolled with Intune. |
| Last Modified | The name of the type of device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| App install | Denotes whether an app install failure or success has occurred on the individual device. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection status

An app protection policy is available to mobile apps that integrate with Enterprise Mobility Solution (EMS) technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## App protection policies reference

An app protection policy is available to mobile apps that integrate with EMS technologies.These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

### Properties

The table summarizes app protection policies status for devices managed by Intune.

| Property    | Description                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Name        | The name of the application.                                                                                                        |
| Deployed    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Platform    | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Enrollment  | The name of the type of device.                                                                                                     |
| Last Update | The timestamp the policy was modified.                                                                                              |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Text                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device Name        | The name of the type of device.                                                                                                     |
| Managed By         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last Check in      | The name of the type of device.                                                                                                     |

## Compliance policies reference

Makes sure that the devices used to access company apps and data, comply with certain rules like using a PIN to access the device, and encryption of data stored on the device.

### Properties

The properties of the compliance policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## Configuration policies reference

An app configuration policy is available to mobile apps with vendor-specific configuration. 

### Properties

The properties of the configuration policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |


### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

-->

## <a name="enrollment-failure-reference"></a>註冊失敗參考

「註冊失敗」表格列出失敗的註冊嘗試。 下表列出的裝置之後可能會在另一次嘗試時成功註冊。 某些失敗的嘗試可能不會列出。 並非所有失敗都有風險降低資訊。

| 表格欄位 | 說明 |
|-------------|----------|
| 註冊開始 | 使用者首次開始註冊時的開始時間。 |
| OS | 裝置的作業系統。 |
| OS 版本 | 裝置的作業系統版本。 |
| 失敗 | 失敗的原因。 |

### <a name="failure-details"></a>失敗詳細資料

當您選擇失敗列時，會提供更多詳細資料。

| 區段 | 說明 |
|-------------|----------|
| 失敗詳細資料 | 失敗的更詳細說明。 |
| 可能的補救措施 | 解決錯誤的建議步驟。 某些失敗可能沒有補救措施。 |
| 資源 (選擇性) | 延伸閱讀連結或在入口網站中採取動作的區域連結。 |

### <a name="enrollment-errors"></a>註冊錯誤

| 錯誤 | 詳細資料 |
|-------------|----------|
| iOS 逾時或失敗 | 裝置與 Intune 之間因使用者花太多時間完成註冊裝置所導致的逾時。 |
| 找不到使用者或使用者未獲授權 | 使用者缺少授權或已從服務移除。 |
| 裝置已註冊 | 有人嘗試在其他使用者仍在註冊中的裝置上，使用公司入口網站來註冊裝置。 |
| 尚未向 Intune 啟用 | 嘗試在未設定 Intune 行動裝置管理 (MDM) 授權單位時註冊。 |
| 註冊授權失敗 | 嘗試使用舊版的公司入口網站註冊。 |
| 不支援裝置 | 裝置不符合 Intune 註冊的最低需求。 |
| 不符合註冊限制 | 此註冊因為管理員所設定的註冊限制而被封鎖。 |
| 裝置版本太低 | 系統管理員設定了需要較高裝置版本的註冊限制。 |
| 裝置版本太高 | 系統管理員設定了需要較低裝置版本的註冊限制。 |
| 無法將裝置註冊為個人 | 系統管理員設定了封鎖個人註冊的註冊限制，且失敗的裝置未預先定義為公司。 |
| 已封鎖裝置平台 | 系統管理員設定了封鎖此裝置平台的註冊限制。 |
| 大量權杖已過期 | 佈建套件中的大量權杖已過期。 |
| 找不到 Autopilot 裝置或詳細資料 | 嘗試註冊時，找不到 Autopilot 裝置。 |
| 找不到或未指派 Autopilot 設定檔 | 裝置沒有使用中的 Autopilot 設定檔。 |
| 未預期的 Autopilot 註冊方法 | 裝置嘗試使用不允許的方法進行註冊。 |
| 已移除 Autopilot 裝置 | 已從此帳戶的 Autopilot 中移除嘗試註冊的裝置。 |
| 已到達裝置上限 | 此註冊因為管理員所設定的裝置限制而被封鎖。 |
| Apple 啟用 | 所有 iOS 裝置目前都無法註冊，因為 Intune 中缺少 Apple MDM Push Certificate 或該憑證已過期。 |
| 裝置未預先註冊 | 裝置未預先註冊為公司，而且管理員已封鎖所有個人註冊項目。 |
| 不支援功能 | 使用者可能正在嘗試透過與 Intune 設定不相容的方法進行註冊。 |

## <a name="collect-available-data-from-mobile-device"></a>從行動裝置收集可用的資料

針對使用者的裝置問題進行疑難排解時，使用下列資源來協助收集裝置資料：
- [將 iOS 註冊錯誤傳送給 IT 系統管理員](/intune-user-help/send-errors-to-your-it-admin-ios)
- [使用詳細資訊記錄來協助公司支援人員修正裝置問題](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android)
- [使用 USB 纜線將 Android 記錄傳送給公司支援人員](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
- [使用電子郵件將 Android 診斷資料記錄傳送給 IT 系統管理員](/intune-user-help/send-logs-to-your-it-admin-by-email-android)
- [將 Android 註冊錯誤傳送給 IT 系統管理員](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)

## <a name="next-steps"></a>後續步驟

您可以進一步了解以角色為基礎的系統管理控制 (RBAC)，來定義組織裝置中的角色、行動應用程式管理、資料保護工作。 如需詳細資訊，請參閱[以角色為基礎的系統管理 (RBAC) 搭配 Intune](/intune/role-based-access-control)。

深入了解 Microsoft Intune 的任何已知問題。 如需詳細資訊，請參閱 [Microsoft Intune 中的已知問題](/intune/known-issues)。

了解在需要時如何建立支援票證並取得協助。 [取得支援](/intune/get-support)。
