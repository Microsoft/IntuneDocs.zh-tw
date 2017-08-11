---
title: "使用應用程式保護原則的 Android 應用程式"
titleSuffix: Intune on Azure
description: "本主題說明當 Android 應用程式交由應用程式保護原則管理時的行為。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a6816285-8e43-4dc8-bca0-e80ec5ef01e6
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6d48725852e26b9e4b9c66a3d614bfc1c95dc58f
ms.sourcegitcommit: 2ee1e8248814d74cef80b609a8e43f59fa0b2618
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2017
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>當 Android 應用程式交由應用程式保護原則管理時的行為 

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主題說明應用程式保護原則所管理應用程式的使用者體驗。 僅當應用程式在工作內容中使用時 (例如使用工作帳戶存取應用程式，或存取公司 OneDrive 上公司位置內儲存的檔案)，才會套應用程式保護原則。
##  <a name="accessing-apps"></a>存取應用程式

所有與 Android 裝置上之應用程式保護原則相關聯的應用程式，都需要公司入口網站應用程式。

對於不在 Intune 中註冊的裝置，公司入口網站應用程式必須安裝在裝置上。 但使用者無須啟動或登入公司入口網站應用程式，即可使用應用程式保護原則管理的應用程式。
公司入口網站應用程式可讓 Intune 共用安全位置中的資料，因此這是必要的，即使未在 Intune 中註冊裝置也是一樣。


##  <a name="using-apps-with-multi-identity-support"></a>使用多重身分識別支援的應用程式

使用應用程式時，因為只會對工作內容套用應用程式保護原則，所以原則的行為會隨內容 (工作或個人) 而不同。

對於支援多種身分識別的應用程式，Intune 只會在使用者於工作內容中使用應用程式時，才套用應用程式保護原則。  例如，使用者會在存取工作資料時取得 PIN 提示。  針對 **Outlook 應用程式**，系統會提示使用者在啟動應用程式時輸入 PIN。 針對 **OneDrive 應用程式**，這發生在使用者輸入工作帳戶時。  對於 Microsoft **Word**、**PowerPoint*、及 **Excel**，這會在終端使用者存取儲存在公司商務用 OneDrive 位置中的文件時發生。
##  <a name="managing-user-accounts-on-the-device"></a>管理裝置上的使用者帳戶

Intune 只允許將應用程式保護原則部署到每部裝置上的一個使用者帳戶。

* 根據您所使用的應用程式，可能或不會封鎖裝置上的第二位使用者。 在所有情況下，只有套用應用程式保護原則的第一位使用者會受原則影響。

  * **Microsoft Word**、**Excel** 及 **PowerPoint** 不會封鎖第二個使用者帳戶，但第二個使用者帳戶不會受應用程式保護原則影響。

  * 若為 **OneDrive 和 Outlook 應用程式**，您只能使用一個工作帳戶。  在這些應用程式中新增多個工作帳戶會遭到封鎖。  不過，您可以在裝置上移除使用者並新增不同的使用者。


* 若裝置在應用程式保護原則部署之前已有多個使用者帳戶，則應用程式保護原則所部署的第一個帳戶將由 Intune 應用程式保護原則管理。


閱讀下列案例範例以深入了解如何處理多個使用者帳戶。

使用者 A 為兩家公司服務 - **X 公司**和 **Y 公司**。使用者 A 在這兩家公司各有一個工作帳戶，且兩者全都使用 Intune 部署應用程式保護原則。 **X 公司**部署**先於** **Y 公司**部署應用程式保護原則。因此將會對 **X 公司**所關聯的帳戶套用應用程式保護原則，而不會對 Y 公司所關聯的帳戶套用。若希望 Y 公司所關聯的使用者帳戶也能交由應用程式保護原則管理，必須移除 X 公司所關聯的使用者帳戶。
### <a name="adding-a-second-account"></a>新增第二個帳戶
####  <a name="android"></a>Android
如果您使用 Android 裝置，則可能會看到封鎖訊息，其中包含有關如何移除現有帳戶並新增帳戶的指示。  若要移除現有帳戶，請移至 [設定] &gt; [一般] &gt; [應用程式管理員] &gt; [公司入口網站]，然後選取 [清除資料]。

![移除該帳戶的錯誤訊息和指示的螢幕擷取畫面](./media/android-switch-user.png)

##  <a name="viewing-media-files-with-the-azure-information-protection-app-previously-known-as-rights-management-sharing-app"></a>使用 Azure Information Protection 應用程式 (前稱為 Rights Management 共用應用程式) 檢視媒體檔案
若要在 Android 裝置上檢視公司 AV、PDF 和影像檔，請使用 [Azure Information Protection 應用程式](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer)。

從 Google Play 商店下載這個應用程式。  

以下是支援的檔案類型：

* **音訊︰**AAC LC、HE-AACv1 (AAC+)、HE-AACv2 (增強 AAC+)、AAC ELD (增強低延遲 AAC)、AMR-NB、AMR-WB、FLAC、MP3、MIDI、Ogg Vorbis、PCM/WAVE。
* **視訊︰**H.263、H.264 AVC、MPEG-4 SP、VP8。
* **影像︰**jpg、pjpg、png、ppng、bmp、pbmp、gif、pgif、jpeg、pjpeg。
* **文件：**PDF、PPDF

------------
|**pfile**|**text**|
|----|----|
|Pfile 是適用於受保護檔案的泛型「包裝函式」格式，它會封裝已加密的內容和 Azure Information Protection 授權，而且可以用來保護任何檔案類型。|文字檔案，包括 XML、CSV 等可以在應用程式中開啟以便進行檢視，即使它們受保護也一樣。 檔案類型︰txt、ptxt、csv、pcsv、log、plog、xml、pxml。|
---------------
## <a name="next-steps"></a>後續步驟
[當 iOS 應用程式交由應用程式保護原則管理時的行為](app-protection-enabled-apps-ios.md)

### <a name="see-also"></a>請參閱
[使用 Microsoft Intune 建立及部署應用程式保護原則](app-protection-policies.md)
