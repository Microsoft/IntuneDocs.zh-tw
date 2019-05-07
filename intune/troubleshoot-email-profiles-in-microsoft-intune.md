---
title: 針對 Microsoft Intune 中的電子郵件設定檔進行疑難排解 - Azure | Microsoft Docs
description: 電子郵件設定檔問題，以及進行疑難排解並解決它們的方法。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 02eac7eaa42f6f9c97426e0536e48a4bc399ed08
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57461017"
---
# <a name="troubleshoot-email-profiles-in-microsoft-intune"></a>Microsoft Intune 的電子郵件設定檔疑難排解

檢閱一些常見的電子郵件設定檔問題，以及如何進行疑難排解並予以解決。

如果這項資訊對您沒有幫助，您也可以[取得 Microsoft Intune 支援](get-support.md)。

## <a name="unable-to-send-images-from--email-account"></a>無法從電子郵件帳戶傳送映像
適用於 Azure 傳統入口網站中的 Intune。

已自動設定電子郵件帳戶的使用者將無法從他們的裝置傳送圖片或映像。 如果未啟用 [允許從協力廠商應用程式傳送電子郵件] ，就會發生此情況。

### <a name="intune-solution"></a>Intune 解決方案

1. 開啟 Microsoft Intune 系統管理主控台，並選取 [原則] 工作負載 > [設定原則]。

2. 選取電子郵件設定檔，然後選擇 **[編輯]**。

3. 選取 [允許從協力廠商應用程式傳送電子郵件]。

### <a name="configuration-manager-integrated-with-intune-solution"></a>Configuration Manager 與 Intune 解決方案整合

1. 開啟 [Configuration Manager 主控台] > [資產與合規性]。

2. 展開 [概觀] > [合規性設定] > [公司資源存取]，並選取 [電子郵件設定檔]。

3. 以滑鼠右鍵按一下電子郵件設定檔，然後開啟 **[內容]**。

4. 選取 **[同步處理設定]** 索引標籤上的 **[允許從協力廠商應用程式傳送電子郵件]**。

## <a name="device-already-has-an-email-profile-installed"></a>裝置已經安裝電子郵件設定檔

如果使用者在佈建 Intune 設定檔前，已先安裝電子郵件設定檔，則 Intune 電子郵件設定檔部署的結果會根據裝置平台而有所不同：

- **iOS**：Intune 依據主機名稱和電子郵件地址偵測到現有的重複電子郵件設定檔。 使用者建立的重複電子郵件設定檔會封鎖 Intune 系統管理員所建立設定檔的部署作業。 因為 iOS 使用者通常會先建立電子郵件設定檔再註冊，所以這個問題很常見。 公司入口網站會通知使用者，因為他們手動設定電子郵件設定檔，所以其不符合規範，並提示使用者移除該設定檔。 使用者應該移除其電子郵件設定檔，才能部署 Intune 設定檔。 若要避免這個問題，請指示使用者先註冊，再讓 Intune 部署設定檔。 然後安裝使用者建立的電子郵件設定檔。

- **Windows**：Intune 依據主機名稱和電子郵件地址偵測到現有的重複電子郵件設定檔。 Intune 會覆寫使用者建立的現有電子郵件設定檔。

- **Samsung KNOX Standard**：Intune 會根據電子郵件地址識別重複的電子郵件帳戶，並使用 Intune 設定檔予以覆寫。 如果使用者設定了該帳戶，Intune 設定檔會再次予以覆寫。 這可能會對帳戶設定遭覆寫的使用者造成混淆。

Samsung KNOX 不會使用主機名稱來識別設定檔。 建議您不要建立多個電子郵件設定檔來部署至不同主機上的相同電子郵件地址，因為他們會互相覆寫。

## <a name="error--0x87d1fde8-for-knox-standard-device"></a>KNOX Standard 裝置的錯誤 0x87D1FDE8
**問題**：在針對各種 Android 裝置建立及部署 Samsung KNOX Standard 的 Exchange Active Sync 電子郵件設定檔後，在裝置的 [屬性] > [原則] 索引標籤中回報了錯誤 **0x87D1FDE8** 或**補救失敗**。

檢閱 Samsung KNOX 的 EAS 設定檔和來源原則的組態。 不再支援 Samsung Note 同步處理選項，因此不應該在您的設定檔中選取該選項。 請確認裝置有足夠的時間來處理原則，最多需要 24 小時。

## <a name="next-steps"></a>後續步驟
如果這項資訊對您沒有幫助，您也可以[取得 Microsoft Intune 支援](get-support.md)。
