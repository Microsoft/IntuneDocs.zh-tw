---
title: 使用應用程式保護原則的 Android 應用程式
description: 本主題說明當應用程式交由應用程式保護原則管理時的行為。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 946ce31c613ddb3c7dd2bf4dfde7561dd56e4ca0
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "73414051"
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>當 Android 應用程式交由應用程式保護原則管理時的行為

本文說明具有應用程式保護原則的應用程式使用者體驗。 應用程式保護原則只適用於工作環境中使用的應用程式：例如，當使用者使用公司帳戶來存取應用程式，或存取儲存於商務用 OneDrive 位置的檔案。

## <a name="access-apps"></a>存取應用程式

所有與 Android 裝置上應用程式保護原則關聯的應用程式，都需要公司入口網站應用程式。

對於不在 Intune 中註冊的裝置，公司入口網站應用程式必須安裝在裝置上。 不過，使用者不需要先啟動或登入公司入口網站應用程式，即可使用應用程式保護原則所管理的應用程式。

公司入口網站應用程式可讓 Intune 分享在安全位置中的資料。 因此，即使裝置並未在 Intune 中註冊，應用程式保護原則關聯的所有應用程式仍都需要公司入口網站應用程式。

## <a name="use-apps-with-multi-identity-support"></a>使用具有多重身分識別支援的應用程式

應用程式保護原則只適用於工作環境。 因此，應用程式可能因工作環境或個人環境而有不同的行為。

例如，使用者會在存取工作資料時看到 PIN 提示。 針對 **Outlook 應用程式**，使用者在啟動應用程式時，系統會提示使用者輸入 PIN。 針對 **OneDrive 應用程式**，使用者輸入工作帳戶時，系統會提示使用者輸入 PIN。 針對 Microsoft **Word**、**PowerPoint** 和 **Excel**，當使用者存取公司商務用 OneDrive 位置中所儲存的文件時，系統會提示使用者輸入 PIN。

## <a name="manage-user-accounts-on-the-device"></a>管理裝置上的使用者帳戶

多重身分識別應用程式可讓使用者新增多個帳戶。  Intune 應用程式僅支援一個受控帳戶。  Intune 應用程式不會限制非受控帳戶的數目。

當應用程式中有受控帳戶時：

* 若使用者嘗試新增第二個受控帳戶，系統會要求使用者選取要使用哪個受控帳戶。  另一個帳戶會移除。
* 若 IT 系統管理員對第二個現有帳戶新增原則，系統會要求使用者選取要使用哪個受控帳戶。  另一個帳戶會移除。

閱讀下列案例範例以深入了解如何處理多個使用者帳戶。

使用者 A 為兩家公司服務 - **X 公司**和 **Y 公司**。使用者 A 在這兩家公司各有一個工作帳戶，且兩者全都使用 Intune 部署應用程式保護原則。 **X 公司**部署**先於** **Y 公司**部署應用程式保護原則。與**X 公司**建立關聯的帳戶會得到應用程式保護原則，與 Y 公司建立關聯的帳戶則否。如果您希望與 Y 公司建立關聯的使用者帳戶受控於應用程式保護原則，您必須移除與 X 公司建立關聯的使用者帳戶，然後新增與 Y 公司建立關聯的帳戶。

### <a name="add-a-second-account"></a>新增第二個帳戶

#### <a name="android"></a>Android

如果您使用 Android 裝置，則可能會看到封鎖訊息，其中包含有關如何移除現有帳戶並新增帳戶的指示。  若要移除現有帳戶，請移至 [設定] &gt; [一般] &gt; [應用程式管理員] &gt; [公司入口網站]  。 然後選擇 [清除資料]  。

![移除該帳戶的錯誤訊息和指示的螢幕擷取畫面](./media/end-user-mam-apps-android/Android_SwitchUser.png)

## <a name="view-media-files-with-the-azure-information-protection-app"></a>使用 Azure 資訊保護 App 檢視媒體檔案

若要在 Android 裝置上檢視公司 AV、PDF 和影像檔，請使用 [Azure 資訊保護 App](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer) (先前稱為 Rights Management 共用應用程式)。

從 Google Play 商店下載這個 App。  

支援下列檔案類型：

* **音訊：** AAC LC、HE-AACv1 (AAC+)、HE-AACv2 (增強 AAC+)、AAC ELD (增強低延遲 AAC)、AMR-NB、AMR-WB、FLAC、MP3、MIDI、Ogg Vorbis、PCM/WAVE
* **視訊：** H.263、H.264 AVC、MPEG-4 SP、VP8
* **影像︰** .jpg、.pjpg、.png、.ppng、.bmp、.pbmp、.gif、.pgif、.jpeg、.pjpeg
* **文件：** PDF、PPDF

|**pfile**|
|----|
|Pfile 是適用於受保護檔案的泛型「包裝函式」格式，它會封裝已加密的內容和 Azure 資訊保護授權。 它可用來保護任何檔案類型。|

## <a name="next-steps"></a>後續步驟
[當 iOS 應用程式交由應用程式防護原則管理時的行為](end-user-mam-apps-ios.md)
