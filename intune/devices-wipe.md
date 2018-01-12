---
title: "透過 Intune 使用恢復出廠預設值或移除裝置上的公司資料"
titlesuffix: Azure portal
description: "了解如何移除裝置上的公司資料或將裝置恢復出廠預設值。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 54def958cb82709f55b3c5f75d85f3b530e3d70b
ms.sourcegitcommit: 229f9bf89efeac3eb3d28dff01e9a77ddbf618eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="remove-devices-by-using-factory-reset-or-remove-company-data"></a>使用恢復出廠預設值或移除公司資料來移除裝置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

您可以從 Intune 移除不再需要、重新設定用途或已遺失的裝置。 您可以藉由發出 [移除公司資料] 或 [恢復出廠預設值] 命令來執行這項作業。 使用者也可以從 Intune 公司入口網站，對 Intune 中註冊的個人擁有裝置發出遠端命令。

> [!NOTE]
> 在您從 Azure Active Directory 移除使用者之前，請對與該使用者建立關聯的所有裝置發出 [恢復出廠預設值] 或 [移除公司資料] 命令。 如果您從 Azure Active Directory 移除使用者和受管理的裝置，Intune 不會再對這些裝置發出恢復出廠預設值或移除公司資料。

## <a name="factory-reset"></a>原廠重設

[恢復出廠預設值] 會將裝置還原為其出廠預設值，移除所有的公司和使用者資料與設定， 並從 Intune 管理項目移除裝置。 恢復出廠預設值可用於在提供裝置給新使用者之前重設裝置，或用於裝置遺失或遭竊的情況。 請小心選取恢復出廠預設值。 裝置上的資料無法復原。

### <a name="to-factory-reset-a-device"></a>將裝置恢復出廠預設值

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。
4. 選擇您要恢復出廠預設值之裝置的名稱。
5. 在顯示裝置名稱的刀鋒視窗中選擇 [恢復出廠預設值]
6. 若為 Windows 10 1709 版或更新版本，還有額外選項 [Retain enrollment state and user account] (保留註冊狀態及使用者帳戶)。 
    
    |透過恢復出廠預設值來保留|不保留|
    | -------------|------------|
    |與裝置建立關聯的使用者帳戶|使用者檔案|
    |電腦狀態 \(網域加入，已加入 Azure Active Directory)| 使用者安裝的應用程式 \(市集和 Win32 應用程式)|
    |MDM 註冊|非預設的裝置設定|
    |OEM 安裝的應用程式 \(市集和 Win32 應用程式)||
    |使用者設定檔||
    |使用者設定檔外的使用者資料||
    |使用者自動登入|| 
    
         
7. 選擇 [是] 確認恢復出廠預設值。

如果裝置已開啟且連線，這過程將花費不到 15 分鐘的時間，以將恢復出廠預設值命令傳播到所有裝置類型。

## <a name="remove-company-data"></a>移除公司資料

[移除公司資料] 命令會移除使用 Intune 所指派的受管理應用程式資料 (適用時)、設定和電子郵件設定檔。 移除公司資料會將使用者的個人資料保留在裝置上， 並從 Intune 管理項目移除裝置。 下表說明將移除哪些資料，以及在移除公司資料後對於保留在裝置上的資料有何影響。

### <a name="ios"></a>iOS

|資料類型|iOS|
|-------------|-------|
|Intune 安裝的公司應用程式和相關資料|已將應用程式解除安裝。 將會移除公司應用程式資料。<br /><br />使用行動裝置應用程式管理之 Microsoft 應用程式的應用程式資料會予以移除。 應用程式不會移除。|
|設定|由 Intune 原則所設定的設定不再是強制性，而且可由使用者進行變更。|
|Wi-Fi 及 VPN 設定檔設定|已移除。|
|憑證設定檔設定|憑證會予以移除及撤銷。|
|管理代理程式|移除管理設定檔。|
|電子郵件|經由 Intune 佈建的電子郵件設定檔會予移除，並會刪除裝置上的快取電子郵件。|
|Outlook|適用於 iOS 的 Microsoft Outlook 應用程式所收到的電子郵件會予移除。|
|Azure Active Directory (AD) 退出|已移除 Azure AD 記錄。|
|連絡人 | 移除直接從應用程式同步到原生通訊錄的連絡人。  無法移除從原生通訊錄同步到其他外部來源的任何連絡人。 <br /> <br />目前，只支援 Outlook 應用程式。

### <a name="android"></a>Android

|資料類型|Android|Android Samsung Knox Standard|
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
|Outlook|僅當 Android 版 Microsoft Outlook 應用程式受到 MAM 原則保護時，才會移除其所接收的電子郵件。 否則解除註冊時不會抹除 Outlook 的資料。|僅當 Android 版 Microsoft Outlook 應用程式受到 MAM 原則保護時，才會移除其所接收的電子郵件。 否則解除註冊時不會抹除 Outlook 的資料。|
|Azure Active Directory (AD) 退出|已移除 Azure AD 記錄。|已移除 Azure AD 記錄。|
|連絡人 | 移除直接從應用程式同步到原生通訊錄的連絡人。  無法移除從原生通訊錄同步到其他外部來源的任何連絡人。 <br /> <br />目前，只支援 Outlook 應用程式。|移除直接從應用程式同步到原生通訊錄的連絡人。  無法移除從原生通訊錄同步到其他外部來源的任何連絡人。 <br /> <br />目前，只支援 Outlook 應用程式。

### <a name="android-for-work"></a>Android for Work

從 Android for Work 裝置移除公司資料會移除該裝置上工作設定檔中的所有資料、應用程式和設定。 這會從 Intune 管理淘汰裝置。 Android for Work 不支援恢復出廠預設值。

### <a name="windows"></a>Windows

|資料類型|Windows 8.1 (MDM) 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Intune 安裝的公司應用程式和相關資料|受 EFS 保護的檔案將會撤銷其金鑰，且使用者將無法開啟檔案。|不會移除公司應用程式。|原本透過公司入口網站安裝的應用程式將會解除安裝。 將會移除公司應用程式資料。|將解除安裝應用程式並且移除側載金鑰。<br>針對 Windows 10 版本 1703 (Creator Update) 和更新版本，不會移除 Office 365 ProPlus 應用程式。|
|設定|由 Intune 原則所設定的設定不再是強制性，而且可由使用者進行變更。|由 Intune 原則所設定的設定不再是強制性，而且可由使用者進行變更。|由 Intune 原則所設定的設定不再是強制性，而且可由使用者進行變更。|由 Intune 原則所設定的設定不再是強制性，而且可由使用者進行變更。|
|Wi-Fi 及 VPN 設定檔設定|已移除。|已移除。|不支援。|已移除。|
|憑證設定檔設定|憑證會予以移除及撤銷。|憑證會予以移除及撤銷。|不支援。|憑證會予以移除及撤銷。|
|電子郵件|移除已啟用 EFS 且包含 Windows 電子郵件與附件的郵件應用程式。|不支援。|經由 Intune 佈建的電子郵件設定檔會予移除，並會刪除裝置上的快取電子郵件。|移除已啟用 EFS 且包含 Windows 電子郵件與附件的郵件應用程式。 移除 Intune 佈建的郵件帳戶。|
|Azure Active Directory (AD) 退出|否。|否。|已移除 Azure AD 記錄。|不適用。 Windows 10 不支援對已加入 Azure Active Directory 的裝置移除其公司資料。|

### <a name="to-remove-company-data"></a>移除公司資料

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。
4. 選擇您要從中移除公司資料之裝置的名稱。
5. 在顯示裝置名稱的刀鋒視窗中選擇 [移除公司資料]，然後選擇 [是] 進行確認。

如果裝置已開啟且連線，將移除資料命令傳播到所有裝置類型的過程將花費不到 15 分鐘的時間。

## <a name="delete-devices-from-the-azure-active-directory-portal"></a>從 Azure Active Directory 入口網站刪除裝置

由於通訊問題或遺失裝置，您可能需要從 Azure Active Directory (AD) 刪除裝置。 刪除命令不會從管理項目中移除裝置，但您可以使用 [刪除] 來移除 Azure 入口網站中已知無法連線且不太可能與 Azure 再次通訊的裝置記錄。

1.  以系統管理員認證登入 [Azure 入口網站中的 Azure Active Directory](http://aka.ms/accessaad)。 您也可以登入 [Office 365 入口網站](https://portal.office.com)，然後使用頁面左側的連結來選擇 [管理] &gt; [Azure AD]。
3.  如果您沒有 Azure 訂用帳戶，請建立帳戶。 如果您有付費帳戶，應該不需要信用卡或付款 (請選擇 [Register your free Azure Active Directory (註冊免費的 Azure Active Directory)] 訂閱連結)。
4.  選取 [Active Directory]  ，然後選取您的組織。
5.  選取 [使用者]  索引標籤。
6.  選取您要刪除裝置的使用者。
7.  選擇 [裝置]。
8.  視需要移除裝置，例如不再使用的裝置，或具有不正確定義的裝置。
