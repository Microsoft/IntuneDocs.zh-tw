---
title: 使用 Microsoft Intune 利用 PIN 登入 Windows 10 裝置 - Azure | Microsoft Docs
description: 使用 Windows Hello 企業版來允許使用者利用 PIN、指紋等方式登入裝置。 在 Intune 中使用這些設定為 Windows 10 裝置建立身分識別保護組態設定檔，然後將設定檔指派給使用者群組和裝置群組。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4f5d3a232cab25c60189132732a0ea3f347c74a
ms.sourcegitcommit: 107fef144013b01ed768ca8973373f9cb3f0f7dc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2020
ms.locfileid: "75683794"
---
# <a name="use-windows-hello-for-business-on-windows-10-devices-with-microsoft-intune"></a>搭配 Microsoft Intune 在 Windows 10 裝置上使用 Windows Hello 企業版

Windows Hello 企業版是一種能取代密碼、智慧卡及虛擬智慧卡來登入 Windows 裝置的方法。 Intune 包含內建設定，因此系統管理員可以設定及使用 Windows Hello 企業版。 例如，您可以使用這些設定來：

- 為裝置和使用者啟用 Windows Hello 企業版
- 設定裝置 PIN 需求，包括 PIN 長度下限或上限
- 允許使用者可以 (或不可以) 用來登入裝置的手勢 (例如指紋)

此功能適用於執行下列版本的裝置：

- Windows 10 及更新版本
- Windows 10 Mobile
- Windows Holographic for Business

Intune 會使用「組態設定檔」來依據貴組織的需求建立和自訂這些設定。 在您於設定檔中新增這些功能之後，請將這些設定推送或部署至貴組織中的使用者和裝置群組。

本文會示範如何建立裝置組態設定檔。 如需所有設定的清單及其用途，請參閱[用以啟用 Windows Hello 企業版的 Windows 10 裝置設定](identity-protection-windows-settings.md)。

## <a name="create-the-device-profile"></a>建立裝置設定檔

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。

3. 輸入下列內容：

   - **名稱**：為新的設定檔輸入描述性名稱。
   - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
   - **平台**：選取 [Windows 10 及更新版本]  。 只有執行 Windows 10 和更新版本的裝置支援 Windows Hello 企業版。
   - **設定檔類型**：選取 [Identity Protection]  。

4. 在 [Windows Hello 企業版]  窗格中，設定下列選項：

   - **設定 Windows Hello 企業版**：選擇希望如何設定 Windows Hello 企業版：

     - **未設定** (預設值)：在裝置上[佈建 Windows Hello 企業版](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) \(英文\)。 只將 Identity Protection 設定檔指派給使用者時，裝置內容預設為 [未設定]  。

     - **Disabled**：如果您不想要使用 Windows Hello 企業版，請選取此選項。 此選項會針對所有使用者停用 Windows Hello 企業版。

     - **啟用**：選擇此選項以在 Intune 中[佈建](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning)及設定 Windows Hello 企業版設定。 輸入您要設定的設定。 如需所有設定的清單及其用途，請參閱[用以啟用 Windows Hello 企業版的 Windows 10 裝置設定](identity-protection-windows-settings.md)。

   - **使用安全性金鑰登入**：讓 Windows Hello 安全性金鑰作為租用戶所有電腦的登入認證。

     - **啟用**
     - **未設定** (預設)

5. 當您完成時，請選取 [確定]   > [建立]  儲存變更。

設定檔隨即建立，並出現在設定檔清單中。 接下來，將此設定檔[指派](../configuration/device-profile-assign.md)給使用者和裝置群組以符合您的需求。

> [!IMPORTANT]
> 若要允許將多個使用者佈建到裝置，請指定將 Windows Hello 企業版原則套用至裝置。 如果原則只套用至使用者，則只能將一位使用者佈建到裝置。

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/identity-protection-configure/disable-android-camera.png)

-->

## <a name="next-steps"></a>後續步驟

- 查看所有[設定的清單及其用途](identity-protection-windows-settings.md)。
- [指派設定檔](../configuration/device-profile-assign.md)並[監視其狀態](../configuration/device-profile-monitor.md)。
