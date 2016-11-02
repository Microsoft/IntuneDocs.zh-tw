---
title: "使用 MAM 原則的 Android 應用程式 | Microsoft Intune"
description: "本主題描述當您的應用程式受到行動應用程式管理原則所管理時需預期的情況。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: 546b909737b4ea34bd747880fe8ed2d366c6b18a


---

# 當 Android 應用程式由 MAM 原則管理時會發生的情況
本主題描述使用 MAM 原則之應用程式的使用者經驗。 只有在工作內容中使用應用程式時，才會套用行動應用程式管理 (MAM) 原則，例如，使用工作帳戶來存取應用程式，或存取公司 OneDrive 辦公室地點中所儲存的檔案。
##  存取應用程式

Android 裝置上 MAM 原則相關聯的所有應用程式都需要公司入口網站應用程式。

對於不在 Intune 中註冊的裝置，公司入口網站應用程式必須安裝在裝置上。 不過，使用者不需要先啟動或登入公司入口網站應用程式，即可使用 MAM 原則所管理的應用程式。
公司入口網站應用程式可讓 Intune 共用安全位置中的資料，因此這是必要的，即使未在 Intune 中註冊裝置也是一樣。


##  使用多重身分識別支援的應用程式

使用應用程式時，只會將 MAM 原則套用到工作內容，因此，根據內容 (工作或個人)，您可能會看到不同的應用程式行為。

針對支援多身分識別的應用程式，只有在使用者於工作內容中使用應用程式時，Intune 才會套用 MAM 原則。  例如，使用者會在存取工作資料時取得 PIN 提示。  針對 **Outlook 應用程式**，系統會提示使用者在啟動應用程式時輸入 PIN。 針對 **OneDrive 應用程式**，這發生在使用者輸入工作帳戶時。  針對 Microsoft **Word**、**PowerPoint* 和 **Excel**，這發生於使用者存取公司商務用 OneDrive 位置中所儲存的文件時。
##  管理裝置上的使用者帳戶

Intune 僅支援將 MAM 原則部署到每個裝置的一個使用者帳戶。

* 根據您所使用的應用程式，可能或不會封鎖裝置上的第二位使用者。 不過，在所有情況下，只有取得 MAM 原則的第一個使用者會受原則影響。

  * **Microsoft Word**、**Excel** 和 **PowerPoint** 不會封鎖第二個使用者帳戶，但第二個使用者帳戶不會受 MAM 原則影響。

  * 若為 **OneDrive 和 Outlook 應用程式**，您只能使用一個工作帳戶。  在這些應用程式中新增多個工作帳戶會遭到封鎖。  不過，您可以在裝置上移除使用者並新增不同的使用者。


* 如果裝置在 MAM 原則部署之前結束多個使用者帳戶，則 MAM 原則部署到的第一個帳戶會受 Intune MAM 原則影響。


閱讀下列案例範例以深入了解如何處理多個使用者帳戶。

使用者 A 為兩家公司服務 - **X 公司**和 **Y 公司**。使用者 A 在每個公司有一個工作帳戶，且兩者都使用 Intune 來部署 MAM 原則。 **X 公司**在 **Y 公司****之前**部署 MAM 原則。**X 公司**相關聯的帳戶將得到 MAM 原則，Y 公司的相關聯帳戶則否。如果您希望 Y 公司相關聯的使用者帳戶受 MAM 原則管理，您必須移除與 X 公司相關聯的使用者帳戶。
### 新增第二個帳戶
####  Android
如果您使用 Android 裝置，則可能會看到封鎖訊息，其中包含有關如何移除現有帳戶並新增帳戶的指示。  若要移除現有帳戶，請移至 [設定] &gt; [一般] &gt; [應用程式管理員] &gt; [公司入口網站]，然後選取 [清除資料]。

![移除該帳戶的錯誤訊息和指示的螢幕擷取畫面](../media/AppManagement/Android_SwitchUser.png)

##  使用 Azure Information Protection 應用程式 (前稱為 Rights Management 共用應用程式) 檢視媒體檔案
若要在 Android 裝置上檢視公司 AV、PDF 和影像檔，請使用 [Azure Information Protection 應用程式](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer)。

從 Google Play 商店下載這個應用程式。  

以下是支援的檔案類型：

* **音訊︰**AAC LC、HE-AACv1 (AAC+)、HE-AACv2 (增強 AAC+)、AAC ELD (增強低延遲 AAC)、AMR-NB、AMR-WB、FLAC、MP3、MIDI、Ogg Vorbis、PCM/WAVE。
* **視訊︰**H.263、H.264 AVC、MPEG-4 SP、VP8。
* **影像︰**jpg、pjpg、png、ppng、bmp、pbmp、gif、pgif、jpeg、pjpeg。
* **文件：**PDF、PPDF

------------
|**pfile**|**文字**|
|----|----|
|Pfile 是適用於受保護檔案的泛型「包裝函式」格式，它會封裝已加密的內容和 Azure Information Protection 授權，而且可以用來保護任何檔案類型。|文字檔案，包括 XML、CSV 等可以在應用程式中開啟以便進行檢視，即使它們受保護也一樣。 檔案類型︰txt、ptxt、csv、pcsv、log、plog、xml、pxml。|
---------------
## 後續步驟
[當 iOS 應用程式由 MAM 原則管理時會發生的情況](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

### 請參閱
[使用 Microsoft Intune 建立及部署行動應用程式管理原則](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO3-->


