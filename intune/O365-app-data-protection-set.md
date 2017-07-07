---
title: "在 Intune 中設定 Office 365 應用程式的基本資料管理"
titleSuffix: Intune on Azure
description: "管理 Office 365 應用程式精靈的支援文件。"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 01/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 852612ac-f146-4372-a900-3f6fdebd05ad
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ayesham
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 302f646bfb9ff0ac024687fa0b3926d83158995c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="how-your-users-will-experience-basic-protection-on-managed-office-365-apps"></a>您的使用者將如何體驗受管理 Office 365 應用程式的基本保護

[管理 Office 365 應用程式精靈] 會建立每個裝置平台的應用程式保護原則。

此精靈會開啟下列原則︰

**iOS**
* 加密應用程式資料

**Android**
* 加密應用程式資料
* 需要簡單的 PIN 碼才能存取

這些原則確保您可以管理 Office 365 應用程式，並讓您在必要時，能夠從 Office 應用程式抹除工作資料。 藉由確定工作資料已經加密，以及必須輸入 PIN 碼才能檢視 Office 365 應用程式中之資料等方式，這些原則也可在裝置遺失或遭竊時，確保裝置的基本保護。


本文使用商務用 OneDrive 作為範例，示範使用在 Intune 管理之應用程式上的體驗。


>[!NOTE]
>使用者通常會在個人裝置上下載應用程式。 若裝置由行動裝置管理 (MDM) 解決方案管理，您就能將應用程式部署到該裝置。

## <a name="user-experience-on-an-ios-device"></a>iOS 裝置上的使用者體驗

1. 啟動商務用 OneDrive 應用程式，以開啟登入頁面。  <br/> ![iOS 版 OneDrive 登入畫面的影像](./media/onedrive-ios-sign-in.png)
2. 輸入您的工作帳戶使用者名稱。 您會被重新導向至 Office 365 驗證 頁面輸入您的工作認證。 <br/> ![Office 365 登入頁面的影像](./media/o365-sign-in-ios.png)
3. 當您的認證成功通過 Azure AD 驗證之後，會套用行動應用程式管理 (MAM) 原則，而且會要求您重新啟動 商務用 OneDrive 應用程式。  <br/>![iOS 的重新啟動提示影像](./media/ios-restart-prompt.png)
>[!NOTE]
>只有未向 Intune 註冊的裝置上才會顯示 [需要重新啟動] 訊息。


4. 重新啟動商務用 OneDrive 應用程式。 應用程式啟動時，MAM 原則會隨即開啟，並會提示您設定裝置的 PIN 碼 (若裝置還未設定 PIN 碼)。 <br/> ![提示建立 PIN 碼的影像](./media/pin-prompt-ios.png)

>[!NOTE]
>大部分使用者都不會看到此提示。 只有 iOS 裝置還未啟用 PIN 碼的使用者會看到此提示。


5. 當您設定並確認 PIN 碼之後，請回到商務用 OneDrive。 您會看到一則通知指出您的 IT 系統管理員已在保護 OneDrive 中的工作資料；此通知只會顯示一次。 <br/> ![從您的 IT 系統管理員發出只會顯示一次的通知映像](./media/one-time-notice.png)
6. 按一下略過此通知之後，即可開始存取您商務用 OneDrive 上的檔案。 <br/> ![iOS 裝置上 OneDrive 檔案的影像](./media/onedrive-files-ios.png) <br/>

>[!NOTE]
>當您變更已部署的原則時，會在下次開啟應用程式時套用這些變更。


## <a name="user-experience-on-an-android-device"></a>Android 裝置上的使用者體驗

1. 啟動商務用 OneDrive 應用程式，以開啟登入頁面。  <br/> ![OneDrive 應用程式歡迎畫面的影像](./media/onedrive-android-welcome.png)
2. 輸入您的工作帳戶使用者名稱。 您會被重新導向至 Office 365 驗證 頁面輸入您的工作認證。 <br/> ![Android 上的 O365 登入影像](./media/o365-sign-in-android.png)
3. 當您的認證成功通過 Azure AD 驗證之後，若裝置上還未安裝公司入口網站應用程式，將會顯示一則訊息指示您加以安裝。 點選 [移至市集] 以繼續。 <br/> ![取得公司入口網站應用程式訊息的影像](./media/get-company-portal-android.png) <br/>若您的手機上已有安裝公司入口網站應用程式，商務用 OneDrive 將會自動啟動，您可以跳到結尾的注意事項。
>[!IMPORTANT]
>在 Android 上，當您將 Office 應用程式設定成交由 MAM 原則管理之後，裝置使用者**必須**安裝公司入口網站應用程式，才能存取工作電子郵件及文件，即使使用者不需要開啟或登入應用程式來實際閱讀的電子郵件或文件亦然。

4. 您現在進入了 Google Play 商店，可從中下載及安裝公司入口網站應用程式。 此應用程式可協助您持續保護資料的安全。 <br/> ![Google Play 商店中應用程式的影像](./media/google-play-get-app-android.png)
5. 完成應用程式安裝之後，請選擇 [接受] 接受條款。 商務用 OneDrive 會自動啟動。


>[!NOTE]
>您的 IT 如有要求您設定 PIN 碼，可能會您下次開啟商務用 OneDrive 時，要求您設定 PIN 碼。 設定並確認 PIN 碼之後，便能繼續使用商務用 OneDrive。

![提示輸入 PIN 碼的影像](./media/pin-prompt-android.png)


<!--- Original steps: 6. The next time you open OneDrive for Business, you may be asked to set a PIN, if your IT requires one to use the OneDrive for Business app. ART 7. After you set and confirm the PIN, you can continue on to OneDrive for Business. -->

## <a name="what-policies-does-this-wizard-set"></a>此精靈設定哪些原則？
|     |       | |
|----|--------|-|
|**名稱**|管理 Office 365 應用程式| |
| **說明**|由 [管理 Office 365 應用程式精靈] 所建立| |
| |  | |
| **設定名稱** |**iOS 原則值** | **Android 原則值** |
|禁止 iTunes 與 iCloud 備份| 否 | N/A |
|禁止 Android 備份 |N/A | 否|
|允許應用程式將資料傳送到其他應用程式 | 所有應用程式 | 所有應用程式|
|允許應用程式接收來自其他應用程式的資料| 所有應用程式 | 所有應用程式|
|禁止執行 [另存新檔] | 否 | 否|
|限制利用其他應用程式剪下、複製及貼上 | 任何應用程式 | 任何應用程式 |
|限制要在公司管理的瀏覽器中顯示網頁內容 | 否| 否|
|加密應用程式資料 | 當裝置鎖住時 | 是|
|停用聯絡人同步 | 否| 否|
|停用列印 | 否 | 否|
|需要 PIN 碼才可存取 | 否 | 是|
|PIN 重設之前的嘗試次數 | N/A |5|
|允許簡單的 PIN | N/A |是|
|PIN 長度 | N/A | 4|
|允許指紋而非 PIN | N/A | 是 |
|需要公司認證才能存取 | 否 | 否|
|封鎖受管理的應用程式在已進行 JB 或 Root 破解的裝置上執行 | 否 | 否|
|多少分鐘後重新檢查存取需求 (分鐘) - 逾時 | 30 | 30|
|多少分鐘後重新檢查存取需求 (分鐘) - 離線寬限期 | 720 |720|
|離線間隔幾天後抹除 App 資料 | 90 | 90|
|封鎖螢幕擷取 (僅限 Android 裝置) | N/A | 否 |

### <a name="why-is-an-app-pin-policy-only-configured-for-android-devices"></a>為什麼只有 Android 裝置才需要設定應用程式 PIN 碼原則？
iOS 與 Android 的加密運作方式不相同。

在 iOS 上，對於關聯到 Intune MAM 原則的應用程式，資料加密會透過作業系統提供的裝置層級加密於資料靜止時進行。 因此，當您開啟應用程式加密原則時，也會自動要求使用者設定及輸入裝置 PIN 碼才能存取資料。 尚未建立裝置 PIN 碼的使用者將會收到建立裝置 PIN 碼的提示。

在 Android 上，對於關聯 Intune MAM 原則關聯的應用程式，資料會在檔案 I/O 工作期間同步加密。 裝置儲存空間上的內容將一律加密。 在不是由 MDM 管理的裝置上，MAM 原則無法強制要求設定裝置 PIN 碼。 為確保使用者使用同一組 PIN 碼存取工作資料，此精靈會啟用應用程式 PIN 碼原則。

您隨時都能依照組織的需求編輯這些原則設定。

### <a name="how-can-i-view-and-edit-the-policies-created-by-the-wizard"></a>如何檢視及編輯精靈所建立的原則？
若要查看或更新這些原則，或任何您在 Intune Azure 入口網站中建立的原則，請從儀表板中選擇 [管理應用程式] > [應用程式保護原則]。 原則清單會在右側開啟。 選擇您要檢視的原則來查看及編輯其設定。 <br/>
![檢視原則的使用者介面路徑影像](./media/image-for-faq.png)

## <a name="next-steps"></a>後續步驟
深入了解[應用程式保護原則](https://docs.microsoft.comapp-protection-policy.md)。
