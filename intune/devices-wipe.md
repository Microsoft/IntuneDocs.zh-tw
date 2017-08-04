---
title: "使用 Intune 在裝置上完整或選擇性抹除"
titleSuffix: Intune on Azure
description: "了解如何選擇性地抹除裝置上的公司資料，或如何完整抹除資料，將裝置重設成出廠預設值。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 44d1695b3f0297276376fb9cb4367c1411aa31b2
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2017
---
# <a name="use-full-or-selective-wipe"></a>使用完整或選擇性抹除

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

當 Intune 管理的裝置不再被需要、重新設定用途，或是已經遺失時，您可以抹除其中的應用程式和資料。 若要這樣做，Intune 會提供選擇性抹除和完整抹除功能。 使用者也可以在已於 Intune 中註冊的私人擁有裝置上，從 Intune 公司入口網站應用程式發出遠端裝置抹除命令。

  > [!NOTE]
  > 本主題只會說明如何抹除受 Intune 行動裝置管理所管理的裝置。 您也可以使用 [Azure 入口網站](https://portal.azure.com)來[從應用程式抹除公司資料](https://docs.microsoft.com/intune-classic/deploy-use/wipe-managed-company-app-data-with-microsoft-intune)。 您也可以[淘汰使用 Intune 用戶端軟體管理的電腦](https://docs.microsoft.com/intune-classic/deploy-use/retire-a-windows-pc-with-microsoft-intune)。

## <a name="full-wipe"></a>完整抹除

[完整抹除] 會將裝置還原為其原廠預設值，移除所有的公司和使用者資料與設定， 並從 Intune 移除裝置。 完整抹除適用於在提供裝置給其裝置遺失或遭竊的新使用者或執行個體之前重設裝置。  **請小心選取完整抹除。裝置上的資料無法復原。**


> [!Warning]
> 擁有少於 4 GB RAM 的 Windows 10 RTM 裝置 (早於 Windows 10 1511 版的裝置) 於抹除後可能會變成無法存取。 若要存取沒有回應的 Windows 10 裝置，您可以透過 USB 磁碟機啟動該裝置。


**若要完全抹除裝置上的資料 (恢復出廠預設值)**：

1.  在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。

2.  選擇您要抹除之裝置的名稱。

3.  在顯示裝置名稱的刀鋒視窗中選擇 [恢復出廠預設值]，然後選擇 [是] 確認抹除。

如果裝置已開啟且連線，這過程將花費不到 15 分鐘的時間，以將抹除命令傳播到所有裝置類型。

### <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>若要在 Azure Active Directory 入口網站中刪除裝置：

1.  瀏覽至 [http://aka.ms/accessaad](http://aka.ms/accessaad)，或從 [https://portal.office.com](https://portal.office.com) 中選擇 [系統管理] &gt; [Azure AD]。

2.  利用頁面左側連結，以您的組織識別碼登入。

3.  如果您沒有 Azure 訂用帳戶，請建立帳戶。 如果您有付費帳戶，應該不需要信用卡或付款 (請選擇 [Register your free Azure Active Directory (註冊免費的 Azure Active Directory)] 訂閱連結)。

4.  選取 [Active Directory]  ，然後選取您的組織。

5.  選取 [使用者]  索引標籤。

6.  選取您要刪除裝置的使用者。

7.  選擇 [裝置]。

8.  視需要移除裝置，例如不再使用的裝置，或具有不正確定義的裝置。


## <a name="selective-wipe"></a>選擇性抹除

[選擇性抹除] 會移除公司資料，包括適用的行動應用程式管理 (MAM) 資料、設定和裝置的電子郵件設定檔。 選擇性抹除會將使用者的個人資料保留在裝置上。 並從 Intune 移除裝置。 下表說明將移除哪些資料，以及在選擇性抹除後對於保留在裝置上的資料有何影響 (此表格已依平台組織)。

**iOS**

|資料類型|iOS|
|-------------|-------|
|Intune 安裝的公司應用程式和相關資料|已將應用程式解除安裝。 將會移除公司應用程式資料。<br /><br />使用行動裝置應用程式管理之 Microsoft 應用程式的應用程式資料會予以移除。 應用程式不會移除。|
|設定|由 Intune 原則所設定的設定不再是強制性，而且可由使用者進行變更。|
|Wi-Fi 及 VPN 設定檔設定|已移除。|
|憑證設定檔設定|憑證會予以移除及撤銷。|
|管理代理程式|移除管理設定檔。|
|電子郵件|經由 Intune 佈建的電子郵件設定檔會予移除，並會刪除裝置上的快取電子郵件。|
|Outlook|適用於 iOS 的 Microsoft Outlook 應用程式所收到的電子郵件會予移除。|
|Azure Active Directory (AAD) 退出|已移除 AAD 記錄。|
|連絡人 | 移除直接從應用程式同步到原生通訊錄的連絡人。  無法清除從原生通訊錄同步處理到其他外部來源的任何連絡人。 <br /> <br />目前，只支援 Outlook 應用程式。

**Android**

|資料類型|Android|Android Samsung KNOX Standard|
|-------------|-----------|------------------------|
|網頁連結|已移除。|已移除。|
|未受管理的 Google Play 應用程式|應用程式和資料仍會保持安裝。|應用程式和資料仍會保持安裝。|
|未受管理的企業營運應用程式|應用程式和資料仍會保持安裝。|最後會將應用程式解除安裝並移除應用程式的本機資料。 未移除應用程式外 (例如 SD 記憶卡上) 的任何資料。|
|受管理的 Google Play 應用程式|將會移除應用程式資料。 應用程式不會移除。 應用程式外 (例如 SD 記憶卡上) 受 MAM 加密保護的資料仍維持加密狀態且無法使用，但未移除。|將會移除應用程式資料。 應用程式不會移除。 應用程式外 (例如 SD 記憶卡上) 受 MAM 加密保護的資料仍維持加密狀態，但未移除。|
|受管理的企業營運系統應用程式|將會移除應用程式資料。 應用程式不會移除。 應用程式外 (例如 SD 記憶卡上) 受 MAM 加密保護的資料仍維持加密狀態且無法使用，但未移除。|將會移除應用程式資料。 應用程式不會移除。 應用程式外 (例如 SD 記憶卡上) 受 MAM 加密保護的資料仍維持加密狀態且無法使用，但未移除。|
|設定|由 Intune 原則所設定的設定不再是強制性，而且可由使用者進行變更。|由 Intune 原則所設定的設定不再是強制性，而且可由使用者進行變更。|
|Wi-Fi 及 VPN 設定檔設定|已移除。|已移除。|
|憑證設定檔設定|憑證會予以撤銷，但不會移除。|憑證會予以移除及撤銷。|
|管理代理程式|撤銷裝置系統管理員權限。|撤銷裝置系統管理員權限。|
|電子郵件|n/a (Android 裝置不支援電子郵件設定檔)|經由 Intune 佈建的電子郵件設定檔會予移除，並會刪除裝置上的快取電子郵件。|
|Outlook|適用於 Android 的 Microsoft Outlook 應用程式所收到的電子郵件會予移除。|適用於 Android 的 Microsoft Outlook 應用程式所收到的電子郵件會予移除。|
|Azure Active Directory (AAD) 退出|已移除 AAD 記錄。|已移除 AAD 記錄。|
|連絡人 | 移除直接從應用程式同步到原生通訊錄的連絡人。  無法清除從原生通訊錄同步處理到其他外部來源的任何連絡人。 <br /> <br />目前，只支援 Outlook 應用程式。|移除直接從應用程式同步到原生通訊錄的連絡人。  無法清除從原生通訊錄同步處理到其他外部來源的任何連絡人。 <br /> <br />目前，只支援 Outlook 應用程式。

**Android for Work**

在 Android for Work 裝置上執行選擇性抹除會移除該裝置上工作設定檔中的所有資料、應用程式和設定。 這會從 Intune 管理淘汰裝置。 Android for Work 不支援完全抹除。

**Windows**

|資料類型|Windows 8.1 (MDM) 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Intune 安裝的公司應用程式和相關資料|受 EFS 保護的檔案將會撤銷其金鑰，且使用者將無法開啟檔案。|不會移除公司應用程式。|原本透過公司入口網站安裝的應用程式將會解除安裝。 將會移除公司應用程式資料。|將解除安裝應用程式並且移除側載金鑰。|
|設定|由 Intune 原則所設定的設定不再是強制性，而且可由使用者進行變更。|由 Intune 原則所設定的設定不再是強制性，而且可由使用者進行變更。|由 Intune 原則所設定的設定不再是強制性，而且可由使用者進行變更。|由 Intune 原則所設定的設定不再是強制性，而且可由使用者進行變更。|
|Wi-Fi 及 VPN 設定檔設定|已移除。|已移除。|不支援。|已移除。|
|憑證設定檔設定|憑證會予以移除及撤銷。|憑證會予以移除及撤銷。|不支援。|憑證會予以移除及撤銷。|
|電子郵件|移除已啟用 EFS 且包含 Windows 電子郵件與附件的郵件應用程式。|不支援。|經由 Intune 佈建的電子郵件設定檔會予移除，並會刪除裝置上的快取電子郵件。|移除已啟用 EFS 且包含 Windows 電子郵件與附件的郵件應用程式。 移除 Intune 佈建的郵件帳戶。|
|Azure Active Directory (AAD) 退出|否。|否。|已移除 AAD 記錄。|不適用。 Windows 10 不支援對已加入 Azure Active Directory 的裝置進行選擇性抹除。|

**若要執行選擇性抹：**：

1.  在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。

2.  選擇您要抹除之裝置的名稱。

3.  在顯示裝置名稱的刀鋒視窗中選擇 [移除公司...]\(代表移除公司資料)，然後選擇 [是] 確認抹除。

如果裝置已開啟且連線，這過程將花費不到 15 分鐘的時間，以將抹除命令傳播到所有裝置類型。
