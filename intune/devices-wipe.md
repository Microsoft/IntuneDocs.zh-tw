---
title: 使用 Microsoft Intune 移除裝置上的公司資料 - Azure | Microsoft Docs
description: 移除裝置上的公司資料，或在使用 Microsoft Intune 的 Android、Android 工作設定檔、iOS、macOS 或 Windows 裝置上執行原廠重設。 也從 Azure Active Directory 中刪除裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 326622c324f75e216db69bd850b707e0fc1c0679
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2018
ms.locfileid: "37906051"
---
# <a name="remove-devices-by-using-factory-reset-removing-company-data-or-manually-unenrolling-the-device"></a>使用恢復出廠預設值、移除公司資料或手動取消註冊裝置來移除裝置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

透過使用 [移除公司資料] 或 [重設成出廠預設值] 動作，您可以從 Intune 移除不再需要、重新設定用途或者遺失的裝置。 使用者也可以從 Intune 公司入口網站，對使用 Intune 註冊的個人擁有裝置發出遠端命令。

> [!NOTE]
> 在您從 Azure Active Directory (Azure AD) 移除使用者之前，請對與該使用者建立關聯的所有裝置發出 [原廠重設] 或 [移除公司資料] 動作。 如果您從 Azure AD 移除有受控裝置的使用者，Intune 不會再對這些裝置發出原廠重設或移除公司資料的命令。

## <a name="factory-reset"></a>原廠重設

[原廠重設] 動作會將裝置還原成其出廠的預設設定。 如果您選擇 [保留註冊狀態和使用者帳戶] 核取方塊，則會保留使用者資料。 否則，會安全地清除磁碟機。

|重設成出廠預設值動作|**保留註冊狀態和使用者帳戶**|從 Intune 管理移除|說明|
|:-------------:|:------------:|:------------:|------------|
|**重設成出廠預設值**| 未勾選 | 是 | 清除所有的使用者帳戶、資料、MDM 原則及設定。 將作業系統重設為其預設狀態和設定。|
|**重設成出廠預設值**| 勾選 | 否 | 清除所有的 MDM 原則。 保留使用者帳戶和資料。 將使用者設定重設為預設值。 將作業系統重設為其預設狀態和設定。|

[保留註冊狀態和使用者帳戶] 選項僅適用於 Windows 10 版本 1709 或更新版本。

下次連線到 Intune 時，MDM 原則將會重新套用。

在您將裝置給予新使用者之前重設裝置，或當裝置遺失或遭竊的情況，原廠重設十分有用。 請小心選取 [原廠重設]。 裝置上的資料無法復原。

### <a name="factory-reset-a-device"></a>對裝置執行原廠重設

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置] > [所有裝置]。
4. 選擇您要執行原廠重設的裝置名稱。
5. 在顯示裝置名稱的窗格中，選取 [原廠重設]。
6. 在 Windows 10 的 1709 版或更新版本中，您也可以有 [Retain enrollment state and user account] (保留註冊狀態和使用者帳戶) 選項。 
    
    |重設為原廠設定時保留不變|不保留|
    | -------------|------------|
    |與裝置建立關聯的使用者帳戶|使用者檔案|
    |機器狀態 \(網域加入、已加入 Azure AD)| 使用者安裝的應用程式 \(市集和 Win32 應用程式)|
    |行動裝置管理 (MDM) 註冊|非預設的裝置設定|
    |OEM 安裝的應用程式 \(市集和 Win32 應用程式)||
    |使用者設定檔||
    |使用者設定檔外的使用者資料||
    |使用者自動登入|| 
    
         
7. 選取 [是] 確認執行原廠重設。

如果裝置已開啟且連線，則 [原廠重設] 動作過程會在 15 分鐘內傳播到所有的裝置類型。

## <a name="remove-company-data"></a>移除公司資料

[移除公司資料] 動作會移除使用 Intune 所指派的受控應用程式資料 (適用時)、設定和電子郵件設定檔。 並從 Intune 管理項目移除裝置。 當裝置下一次簽入並收到遠端 [移除公司資料] 動作時，便會發生。

[移除公司資料] 會將使用者的個人資料保留在裝置上。  

下表描述將移除哪些資料，以及移除公司資料後，[移除公司資料] 動作對保留在裝置上的資料有何影響。

### <a name="ios"></a>iOS

|資料類型|iOS|
|-------------|-------|
|Intune 安裝的公司應用程式和相關資料|已將應用程式解除安裝。 將會移除公司應用程式資料。<br /><br />使用行動裝置應用程式管理之 Microsoft 應用程式的應用程式資料會予以移除。 應用程式不會移除。|
|設定|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|
|Wi-Fi 及 VPN 設定檔設定|已移除。|
|憑證設定檔設定|憑證會予以移除及撤銷。|
|管理代理程式|已移除管理設定檔。|
|電子郵件|已移除經由 Intune 佈建的電子郵件設定檔。 已刪除裝置上的快取電子郵件。|
|Outlook|已移除 iOS 版 Microsoft Outlook 應用程式收到的電子郵件。 先決條件是要將 Outlook 行動應用程式部署為 iOS 使用者的「必要」應用程式。|
|Azure AD 退出|已移除 Azure AD 記錄。|
|連絡人 |已移除直接從應用程式同步到原生通訊錄的連絡人。 無法移除從原生通訊錄同步到其他外部來源的任何連絡人。 <br /> <br />目前只支援 Outlook 應用程式。

### <a name="android"></a>Android

|資料類型|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|網頁連結|已移除。|已移除。|
|未受管理的 Google Play 應用程式|應用程式和資料仍會保持安裝。|應用程式和資料仍會保持安裝。|
|非受控企業營運應用程式|應用程式和資料仍會保持安裝。|已解除安裝應用程式並移除應用程式的本機資料。 不會移除應用程式外的任何資料 (例如 SD 記憶卡)。|
|受管理的 Google Play 應用程式|將會移除應用程式資料。 不會移除應用程式。 應用程式外受行動應用程式管理 (MAM) 加密保護的資料 (例如 SD 記憶卡)，仍維持加密狀態且無法使用，但不會移除。|將會移除應用程式資料。 不會移除應用程式。 應用程式外受 MAM 加密保護的資料 (例如 SD 記憶卡)，仍維持加密狀態，但不會移除。|
|非受控企業營運應用程式|將會移除應用程式資料。 不會移除應用程式。 應用程式外受 MAM 加密保護的資料 (例如 SD 記憶卡)，仍維持加密狀態且無法使用，但不會移除。|將會移除應用程式資料。 不會移除應用程式。 應用程式外受 MAM 加密保護的資料 (例如 SD 記憶卡)，仍維持加密狀態且無法使用，但不會移除。|
|設定|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|
|Wi-Fi 及 VPN 設定檔設定|已移除。|已移除。|
|憑證設定檔設定|憑證會予以撤銷，但不會移除。|憑證會予以移除及撤銷。|
|管理代理程式|撤銷裝置系統管理員權限。|撤銷裝置系統管理員權限。|
|電子郵件|N/A (Android 裝置不支援電子郵件設定檔)|經由 Intune 佈建的電子郵件設定檔已移除。 已刪除裝置上的快取電子郵件。|
|Outlook|僅當 Android 版 Outlook 應用程式受到 MAM 原則保護時，才會移除其所接收的電子郵件。 否則，取消註冊裝置時不會抹除 Outlook。|僅當 Android 版 Outlook 應用程式受到 MAM 原則保護時，才會移除其所接收的電子郵件。 否則，取消註冊裝置時不會抹除 Outlook。|
|Azure AD 退出|已移除 Azure AD 記錄。|已移除 Azure AD 記錄。|
|連絡人 |已移除直接從應用程式同步到原生通訊錄的連絡人。 無法移除從原生通訊錄同步到其他外部來源的任何連絡人。 <br /> <br />目前只支援 Outlook 應用程式。|已移除直接從應用程式同步到原生通訊錄的連絡人。 無法移除從原生通訊錄同步到其他外部來源的任何連絡人。 <br /> <br />目前只支援 Outlook 應用程式。

### <a name="android-work-profile"></a>Android 工作設定檔

從 Android 工作設定檔裝置移除公司資料會移除該裝置上工作設定檔中的所有資料、應用程式和設定。 Intune 管理已淘汰該裝置。 Android 工作設定檔不支援恢復出廠預設值。

### <a name="android-enterprise-kiosk-devices"></a>Android 企業 Kiosk 裝置

您只可以將 Android Kiosk 裝置恢復為出廠預設值。 您無法從 Android Kiosk 裝置移除公司資料。


### <a name="macos"></a>macOS

|資料類型|macOS|
|-------------|-------|
|設定|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|
|Wi-Fi 及 VPN 設定檔設定|已移除。|
|憑證設定檔設定|透過 MDM 部署的憑證將會移除並撤銷。|
|管理代理程式|已移除管理設定檔。|
|Outlook|若已啟用條件式存取，裝置就不會收到新的郵件。|
|Azure AD 退出|已移除 Azure AD 記錄。|

### <a name="windows"></a>Windows

|資料類型|Windows 8.1 (MDM) 和 Windows RT 8.1|Windows RT|Windows Phone 8.1 和 Windows Phone 8|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Intune 安裝的公司應用程式和相關資料|會撤銷受 EFS 保護之檔案的索引鍵。 使用者無法開啟檔案。|不會移除公司應用程式。|原本透過公司入口網站安裝的應用程式將會解除安裝。 將會移除公司應用程式資料。|已將應用程式解除安裝。 已移除側載金鑰。<br>針對 Windows 10 版本 1703 (Creators Update) 和更新版本，不會移除 Office 365 ProPlus 應用程式。|
|設定|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|由 Intune 原則所設定的設定不再是強制性。 使用者可以變更這些設定。|
|Wi-Fi 及 VPN 設定檔設定|已移除。|已移除。|不支援。|已移除。|
|憑證設定檔設定|憑證會予以移除及撤銷。|憑證會予以移除及撤銷。|不支援。|憑證會予以移除及撤銷。|
|電子郵件|移除已啟用 EFS 的電子郵件。 這包括 Windows 郵件應用程式中的電子郵件和附件。|不支援。|已移除經由 Intune 佈建的電子郵件設定檔。 已刪除裝置上的快取電子郵件。|移除已啟用 EFS 的電子郵件。 這包括 Windows 郵件應用程式中的電子郵件和附件。 移除 Intune 佈建的郵件帳戶。|
|Azure AD 退出|否。|否。|已移除 Azure AD 記錄。|不適用。 在 Windows 10 中，您無法移除已加入 Azure AD 裝置中的公司資料。|

### <a name="remove-company-data"></a>移除公司資料

1. 登入 [Azure 入口網站中的 Intune](https://aka.ms/intuneportal)。
2. 在 [裝置] 窗格中，選取 [所有裝置]。
3. 選取您要從中移除公司資料之裝置的名稱。
4. 在顯示裝置名稱的窗格中，選取 [移除公司資料]。 選取 [是] 確認。

如果裝置已開啟且連線，則 [移除公司資料] 動作過程會在 15 分鐘內傳播到所有的裝置類型。

## <a name="delete-devices-from-the-intune-portal"></a>從 Intune 入口網站中刪除裝置

如果您想要從 Intune 入口網站移除裝置，則可以從特定的裝置窗格來刪除裝置。 下一次裝置簽入時，會移除裝置上所有的公司資料。

1. 登入 [Azure 入口網站中的 Intune](https://aka.ms/intuneportal)。
2. 選擇 [裝置] > [所有裝置] > 選擇您要刪除的裝置 > [刪除]。

### <a name="automatically-delete-devices-with-cleanup-rules"></a>使用清除規則自動刪除裝置
您可以將 Intune 設定為自動刪除看似非作用中、過時、或是沒有回應的裝置。 這些清除規則會持續監視您的裝置清查，以便您的裝置記錄保持最新狀態。 以這種方法刪除的裝置會從 Intune 管理移除。
1. 登入 [Azure 入口網站中的 Intune](https://aka.ms/intuneportal)。
2. 選擇 [裝置] > [裝置清除規則] > [確定]。
3. 在 [刪除已多日未簽入的裝置] 方塊中，輸入 90 到 270 之間的數字。
4. 選擇 [儲存]。



## <a name="delete-devices-from-the-azure-active-directory-portal"></a>從 Azure Active Directory 入口網站刪除裝置

由於通訊問題或遺失裝置，您可能需要從 Azure AD 刪除裝置。 您可以使用 [刪除] 動作來移除 Azure 入口網站中已知無法連線且不太可能與 Azure 再次通訊的裝置記錄。 [刪除] 動作不會從管理移除裝置。

1.  使用您的管理員認證登入 [Azure 入口網站中的 Azure Active Directory](http://aka.ms/accessaad)。 您也可以登入 [Office 365 入口網站](https://portal.office.com)。 從功能表中，選取 [系統管理中心] > [Azure AD]。
2.  如果您沒有 Azure 訂用帳戶，請建立帳戶。 如果您有付費帳戶，應該不需要信用卡或付款 (請選取 [註冊免費的 Azure Active Directory]  訂閱連結)。
3.  選取 [Azure Active Directory]，然後選取您的組織。
4.  選取 [使用者]  索引標籤。
5. 選取您想要刪除之與裝置建立關聯的使用者。
6.  選取 [裝置]。
7.  視狀況移除裝置。 例如，您可能需要移除不再使用的裝置，或定義不正確的裝置。
