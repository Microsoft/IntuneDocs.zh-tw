---
title: 在 S 模式裝置上啟用 Win32 應用程式
titleSuffix: Microsoft Intune
description: 了解如何使用 Microsoft Intune 在 S 模式裝置上啟用 Win32 應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/08/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3074b30921a4daba7469e670a17ad29ee1edc00
ms.sourcegitcommit: 8f56220e7cafc5bc43135940575a9acb5afde730
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827797"
---
# <a name="enable-win32-apps-on-s-mode-devices"></a>在 S 模式裝置上啟用 Win32 應用程式

[Windows 10 S 模式](https://docs.microsoft.com/windows/deployment/s-mode) \(部分機器翻譯\) 是鎖定的作業系統，只會執行 Store 應用程式。 根據預設，Windows S 模式的裝置不允許安裝及執行 Win32 應用程式。 這些裝置包括單一 *Win 10S 基本原則*，此原則會鎖定 S 模式裝置，使所有 Win32 應用程式都無法在其上執行。 不過，在 Intune 中建立及使用 **S 模式補充原則**，您就可以在 Windows 10 S 模式受控裝置上安裝及執行 Win32 應用程式。 透過使用 [Microsoft Defender 應用程式控制 (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) PowerShell 工具，您可以為 Windows S 模式建立一或多個補充原則。 您必須使用 [Device Guard 簽署服務 (DGSS)](https://go.microsoft.com/fwlink/?linkid=2095629) 或 [SignTool.exe](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/signing-policies-with-signtool) 簽署補充原則，然後透過 Intune 上傳並散發這些原則。 或者，您可以使用組織中的程式碼簽署憑證簽署補充原則，不過，慣用的方法是使用 DGSS。 在您使用組織中的程式碼簽署憑證的執行個體中，程式碼簽署憑證所鏈結的根憑證必須存在於裝置上。

透過在 Intune 中指派 S 模式補充原則，您可以讓裝置成為裝置現有 S 模式原則的例外，以允許上傳對應的已簽署應用程式目錄。 該原則會設定可在 S 模式裝置上使用的應用程式允許清單 (應用程式目錄)。

> [!NOTE]
> 只有 Windows 10 2019 年 11 月更新 (組建 18363) 或更新版本才支援 S 模式裝置上的 Win32 應用程式。

<!-- Add WDAC tooling diagram  -->

允許 Win32 應用程式在 S 模式的 Windows 10 裝置上執行的步驟如下：

1. 在 Windows 10 S 註冊程序中透過 Intune 啟用 S 模式裝置。
2. 建立補充原則以允許 Win32 應用程式：
   - 您可以使用 [Microsoft Defender 應用程式控制 (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) 工具來建立補充原則。 原則中的基本原則識別碼必須符合 S 模式的基本原則識別碼 (在用戶端上為硬式編碼)。 此外，請確定原則版本高於先前的版本。
   - 您可以使用 DGSS 來簽署補充原則。 如需詳細資訊，請參閱[使用 Device Guard 簽署來簽署程式碼完整性原則](https://docs.microsoft.com/microsoft-store/sign-code-integrity-policy-with-device-guard-signing) \(部分機器翻譯\)。
   - 您可以透過建立 Windows 10 S 模式補充原則，將簽署的補充原則上傳至 Intune (請參閱下文)。
3. 您可以透過 Intune 允許 Win32 應用程式目錄：
   - 您會建立目錄檔案 (每個應用程式 1 個)，並使用 DGSS 或其他憑證基礎結構來簽署它們。
   - 您可以使用 [Microsoft Win32 內容準備工具](https://go.microsoft.com/fwlink/?linkid=2065730)，將已簽署的目錄封裝到 *.intunewin* 檔案中。 使用 [Microsoft Win32 內容準備工具](https://go.microsoft.com/fwlink/?linkid=2065730) \(英文\) 來建立類別目錄檔案時，並沒有任何命名限制。 從特定的來源資料夾和安裝檔產生 *.intunewin* 檔案時，您可以使用 -a cmdline 選項來提供僅包含類別目錄檔案的個別資料夾。 如需詳細資訊，請參閱 [Win32 應用程式管理 - 準備要上傳的 Win32 應用程式內容](~/apps/apps-win32-app-management.md#prepare-the-win32-app-content-for-upload)。
   - Intune 會套用已簽署的應用程式目錄，以使用 [Intune 管理延伸模組](~/apps/intune-management-extension.md)，在 S 模式裝置上安裝 Win32 應用程式。

> [!NOTE]
> 透過商務用 Microsoft Store (MSFB) 簽署將支援 Windows 10 S 模式下的企業營運應用程式 (LOB) `.appx` 與 `.appx` 套件組合。
>
> 應用程式的 **S 模式補充原則**必須透過 Intune 管理延伸模組來傳遞。
>
> S 模式原則會在裝置層級強制執行。 多個目標原則將在裝置上合併。 合併的原則將會在裝置上強制執行。

若要建立 Windows 10 S 模式補充原則，請使用下列步驟：

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [S 模式補充原則]   > [建立原則]  。
3. 在新增**原則檔案**之前，您必須先建立並簽署它。 如需詳細資訊，請參閱：
    - [使用 PowerShell 工具建立 WDAC 原則，並將它轉換成二進位格式](https://go.microsoft.com/fwlink/?linkid=2095387)
    - [使用 Device Guard 簽署服務簽署](https://go.microsoft.com/fwlink/?linkid=2095629) **(建議)**

4. 在 [基本]  頁面上，新增下列值：

    | 值 | 說明 |
    |--------------|------------------------------------------------|
    | 原則檔案 | 包含 WDAC 原則的檔案。 |
    | Name | 此原則的名稱。 |
    | 說明 | [選擇性] 此原則的描述。 |

5. 按一下 [下一步:  範圍標籤]。<br>
   在 [範圍標籤]  頁面上，您可以選擇性地設定範圍標籤，以決定誰可以在 Intune 中查看應用程式原則。 如需範圍標籤的詳細資訊，請參閱[針對分散式 IT 使用角色型存取控制和範圍標籤](~/fundamentals/scope-tags.md)。

6. 按一下 [下一步:  指派]。<br>
   [指派]  頁面可讓您將原則指派給使用者與裝置。 請務必注意，不論裝置是否由 Intune 管理，您都可以將原則指派給該裝置。
7. 按一下 [下一步:  檢閱 + 建立]，以檢閱您針對設定檔輸入的值。
8. 完成後，請按一下 [建立]  ，在 Intune 中建立 S 模式補充原則。 

建立原則之後，您會看到系統將它新增至 Intune 中的 S 模式補充原則清單。 指派原則之後，原則就會部署到裝置。 請注意，您必須將應用程式部署到與補充原則相同的安全性群組。 您可以開始將應用程式設為目標，並將其指派給那些裝置。 這可讓您的終端使用者在 S 模式裝置上安裝並執行應用程式。

## <a name="removal-of-s-mode-policy"></a>移除 S 模式原則

目前，若要從裝置移除 S 模式補充原則，您必須指派並部署空白原則，以覆寫現有的 S 模式補充原則。

## <a name="policy-reporting"></a>原則報告

在裝置層級強制執行的 S 模式補充原則只有裝置層級的報告。 裝置層級報告適用於成功與錯誤情況。 

針對 S 模式報告原則，在 Intune 主控台中顯示的報告值：
- **成功**：S 模式補充原則已生效。
- **未知**：S 模式補充原則的狀態未知。
- **TokenError**：S 模式補充原則的結構良好，但授權權杖時發生錯誤。
- **NotAuthorizedByToken**：權杖不會授權此 S 模式補充原則。
- **PolicyNotFound**：找不到 S 模式補充原則。

## <a name="next-steps"></a>後續步驟

- 如需詳細資訊，請參閱 [S 模式上的 Win32 應用程式](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/lob-win32-apps-on-s) \(部分機器翻譯\)。
- 如需將應用程式新增至 Intune 的詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](apps-add.md)。
- 如需 Win32 應用程式的詳細資訊，請參閱 [Intune Win32 應用程式管理](~/apps/apps-win32-app-management.md)。
