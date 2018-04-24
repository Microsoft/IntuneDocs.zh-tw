---
title: 使用應用程式保護原則的 Android 應用程式
titlesuffix: Microsoft Intune
description: 了解對具有保護原則之 Android 應用程式的期望。
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a6816285-8e43-4dc8-bca0-e80ec5ef01e6
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 450bcd9c807bdfae16e9c2fa1eb813b00444df65
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>當 Android 應用程式交由應用程式保護原則管理時的行為 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

了解對具有應用程式保護原則之 Android 應用程式的期望。 只有在應用程式用於工作內容時，才會套用應用程式防護原則。 例如，當您以公司帳戶存取應用程式，或存取儲存在公司 OneDrive 位置的檔案時。
##  <a name="accessing-apps"></a>存取應用程式

在 Android 裝置上具有應用程式防護原則的所有應用程式，都需要公司入口網站應用程式。

請在所有未於 Intune 中註冊的裝置上，安裝公司入口網站。 使用者不需要登入公司入口網站應用程式，即可使用具有應用程式防護原則的應用程式。
您可透過公司入口網站應用程式，共用位於安全位置中的資料。 因此，即使是未註冊的裝置，仍需要該應用程式。


##  <a name="using-apps-with-multi-identity-support"></a>使用多重身分識別支援的應用程式

只有當使用者嘗試存取與工作相關的資料時，才會運用應用程式防護原則。  如果使用者存取供個人使用的應用程式，可能會出現不同的行為。

有些應用程式支援多重身分識別。 在此情況下，只有在使用者存取工作資料時，Intune 才會套用應用程式防護原則。  例如，使用者可能會收到 PIN 提示。  在 **Outlook 應用程式**中，當使用者啟動應用程式時，會出現提示。 在 **OneDrive 應用程式**中，當使用者輸入工作帳戶時，會出現提示。  在 Microsoft **Word**、**PowerPoint** 和 **Excel** 中，當使用者存取公司的 OneDrive 文件時，會出現提示。
##  <a name="managing-user-accounts-on-the-device"></a>管理裝置上的使用者帳戶

Intune 允許將應用程式防護原則部署到每部裝置上的一個使用者帳戶。

* 根據您所使用的應用程式，可能或不會封鎖裝置上的第二位使用者。 在所有情況下，只有套用應用程式保護原則的第一位使用者會受原則影響。

  * **Microsoft Word**、**Excel** 和 **PowerPoint** 不會封鎖能存取其他的使用者帳戶。 但使用者帳戶不會受到應用程式防護原則的影響。

  * 若為 **OneDrive 和 Outlook 應用程式**，您只能使用一個工作帳戶。  在這些應用程式中新增多個工作帳戶會遭到封鎖。  但您可以從裝置移除使用者，然後將不同的使用者新增至該裝置。


* 在部署應用程式防護原則之前，裝置上可能有多個現有的使用者帳戶。 在此情況下，應用程式防護原則所部署的第一個帳戶，會受到 Intune 應用程式防護原則的管理。


請閱讀下列案例範例，了解 Intune 如何處理多重使用者帳戶。

使用者 A 為兩家公司服務：**X 公司**和 **Y 公司**。使用者 A 在這兩家公司各有一個工作帳戶，且兩者全都使用 Intune 部署應用程式保護原則。 **X 公司**部署**先於** **Y 公司**部署應用程式保護原則。因此將會對與 **X 公司**相關聯的帳戶，套用應用程式防護原則，但不會對與 Y 公司相關聯的帳戶套用。若希望應用程式防護原則可管理 Y 公司的帳戶，使用者 A 必須移除 X 公司使用者帳戶。
### <a name="adding-a-second-account"></a>新增第二個帳戶
####  <a name="android"></a>Android
您可能會收到移除現有帳戶並新增新帳戶之提示。  若要移除現有帳戶，請前往 **[設定] &gt;[一般] &gt;[應用程式管理員] &gt;[公司入口網站]。然後選取 [清除資料]。**

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

|                                                                                 <strong>pfile</strong>                                                                                 |                                                                      <strong>text</strong>                                                                      |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Pfile 是受保護檔案的一般「包裝函式」格式。 其會封裝經過加密的內容以及 Azure 資訊保護授權。 它可用來保護任何檔案類型。 | 文字檔案，包括 XML、CSV 等可以在應用程式中開啟以便進行檢視，即使它們受保護也一樣。 檔案類型︰txt、ptxt、csv、pcsv、log、plog、xml、pxml。 |

---------------
## <a name="next-steps"></a>後續步驟
[當 iOS 應用程式交由應用程式防護原則管理時的行為](app-protection-enabled-apps-ios.md)

### <a name="see-also"></a>另請參閱
[使用 Microsoft Intune 建立及部署應用程式保護原則](app-protection-policies.md)
