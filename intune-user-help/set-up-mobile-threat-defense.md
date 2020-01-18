---
title: 在您的行動裝置上安裝 Mobile Threat Defense
description: 了解如何在您的行動裝置上安裝 Mobile Threat Defense。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/25/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 6b75712cf05626999c09e8d74fd28252666313c4
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75857869"
---
# <a name="install-mobile-threat-defense"></a>安裝 Mobile Threat Defense   

在您組織的安全性需求中，您可能需要安裝行動裝置威脅防護（MTD）廠商應用程式。 這種類型的應用程式會偵測並警示您裝置上的威脅，例如可疑的應用程式、網路或作業系統弱點。  

如果您沒有必要的 MTD 應用程式，系統將會禁止您使用工作或學校帳戶登入受保護的應用程式。 在本文中，您將瞭解[如何安裝 MTD 應用程式](set-up-mobile-threat-defense.md#install-app)以進行解除封鎖。  

有各種 MTD 廠商應用程式可供安裝;您的組織會讓您知道要使用哪一個。 


## <a name="information-your-organization-can-see"></a>您的組織可以看到的資訊   

您的組織在您的個人應用程式中看不到任何資料，例如文字、電子郵件和圖片。 MTD 應用程式會將您的應用程式相關資訊（例如名稱和版本）報告給您的組織。 所報告的實際資訊取決於您公司使用的 MTD 廠商。 您的組織可能會看到：   

* 應用程式名稱  
* 應用程式識別碼：在 Google Play 中識別應用程式的唯一名稱。  
* 應用程式版本和簡短版本號碼：應用程式的特定版本號碼。  
* 應用程式套件組合和動態大小：應用程式在您的裝置上使用的空間量。 


## <a name="install-app"></a>安裝應用程式    
當您登入受保護的應用程式時，系統會自動提示您安裝 MTD 應用程式。 請遵循畫面上的步驟來完成安裝。 使用本節中的步驟以取得其他協助。  
 
系統可能也會提示您註冊您的裝置。 必須註冊才能確認您的身分識別，並將您的學校或公司帳戶連線到您的裝置。 如果您尚未註冊，您會在安裝 MTD 應用程式之前，自動引導您完成該設定。 當您進入 [**取得存取**] 畫面時，就可以開始執行安裝步驟。  

如需裝置註冊的詳細資訊，請參閱在[組織的網路上註冊您的個人裝置](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)。  

### <a name="ios-setup"></a>iOS 安裝程式  

1. 在 [**取得存取**] 畫面上，依照指示安裝貴組織所需的 MTD 應用程式。   
2. 返回 [**取得存取**] 畫面，然後選取 [**開啟**]。  
3. MTD 應用程式會要求開啟 Microsoft Authenticator 的許可權。 選取 [開啟]  。 
4. 選取您的工作帳戶以進行登入。 
5. 請稍候，MTD 應用程式會掃描您的裝置是否有安全性威脅。 
6. 回到您原先嘗試存取的學校或公司應用程式。 此時，您的組織可能會提示您設定其他應用程式安全性需求，例如建立 PIN。   
7. 您現在應該可以存取應用程式。 如果您仍被封鎖：  
    * 在 [**取得存取**] 畫面上，選取 [重新**檢查**]。  
    * 移至 MTD 應用程式，並檢查現有的威脅。 完成建議的步驟以解決威脅並重新取得存取權。    

### <a name="android-setup"></a>Android 設定 

1. 在 [**取得存取**] 畫面上，依照指示安裝貴組織所需的 MTD 應用程式。  
2. 返回 [**取得存取**] 畫面，然後選取 [**開啟**]。  
3. MTD 應用程式會要求您的許可權，以存取裝置的特定區域（如有需要）。 為了讓此應用程式正常運作，您必須**允許**存取連絡人。 要求的許可權會因 MTD 廠商而異。  
4. 選取您的工作帳戶以進行登入。  
5. 請稍候，MTD 應用程式會掃描您的裝置是否有安全性威脅。  
6. 回到您原先嘗試存取的學校或公司應用程式。 此時，您的組織可能會提示您設定其他應用程式安全性需求，例如建立 PIN。  
7. 您現在應該可以存取應用程式。 如果您仍被封鎖：  
    * 在 [**取得存取**] 畫面上，選取 [重新**檢查**]。  
    * 移至 MTD 應用程式，並檢查現有的威脅。 完成建議的步驟以解決威脅並重新取得存取權。  

### <a name="installation-failed"></a>安裝失敗  

如果安裝失敗，請洽詢您的 IT 支援人員。 前往[公司入口網站網站](https://go.microsoft.com/fwlink/?linkid=2010980)來尋找您組織的連絡資訊。  

您也可以將您的應用程式記錄檔傳送給 IT 支援人員，以提供更多有關安裝的內容。  
* Android 使用者：[上傳公司入口網站的記錄，並將其傳送至電子郵件](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android)。   

* iOS 裝置使用者：從適用于 iOS 的 Microsoft Edge[取出並傳送您的記錄](https://docs.microsoft.com/intune/apps/manage-microsoft-edge#use-microsoft-edge-on-ios-to-access-managed-app-logs)。  

## <a name="resolve-a-threat"></a>解決威脅  
如果威脅超過貴組織定義的威脅層級，您的組織將會：  
   
* 封鎖存取：當您登入公司或學校帳戶時，會封鎖您使用組織的受保護應用程式。  
* 抹除資料：從您組織的一或多個受保護的應用程式中刪除您的工作或學校資料。  

若要解決威脅並重新取得存取權，請在您的裝置上開啟 MTD 應用程式。 閱讀所提供的資訊，以瞭解威脅如何影響您的裝置，以及如何解決此問題。 在您遵循解決威脅的步驟之後，請回到 MTD 應用程式，並起始新的掃描。 可能需要幾分鐘的時間才能重新取得您組織的存取權。  

## <a name="next-steps"></a>後續步驟  

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。

