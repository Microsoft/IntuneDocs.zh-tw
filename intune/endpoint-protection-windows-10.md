---
title: "適用於 Windows 10 的 Intune Endpoint Protection 設定"
titleSuffix: Intune on Azure
description: "了解 Windows 10 裝置上可用以控制BitLocker 等 Endpoint Protection 設定的 Intune 設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4994656afcf1cdb97fdcd3877f6dabdadfb7d374
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-microsoft-intune"></a>Microsoft Intune 中適用於 Windows 10 和更新版本的 Endpoint Protection 設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Endpoint Protection 設定檔可讓您控制 Windows 10 裝置上 BitLocker 等安全性功能。

請使用本主題中的資訊，以了解如何建立 Endpoint Protection 設定檔。

## <a name="create-an-endpoint-protection-profile"></a>建立 Endpoint Protection 設定檔

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置設定]。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
3. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗上，為裝置功能設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取 [Windows 10 及更新版本]。
6. 從 [設定檔類型] 下拉式清單中，選擇 [Endpoint Protection]。 
7. 在 [Windows 加密] 刀鋒視窗中，設定想要的設定。 請使用本主題中的詳細資料，以協助您了解每個設定的用途。 完成之後，請選擇 [確定]。
8. 返回 [建立設定檔] 刀鋒視窗，然後選擇 [建立]。

設定檔隨即建立，並出現在 [設定檔清單] 刀鋒視窗上。

## <a name="endpoint-protection-profile-settings-reference"></a>Endpoint Protection 設定檔設定參考

### <a name="windows-settings"></a>Windows 設定

- **要求裝置加密 (僅限桌面版)** - 啟用時，系統會提示使用者啟用裝置加密。 此外，還會要求他們確認尚未啟用來自其他提供者的加密。 如果已在另一種加密方法為使用中時開啟 Windows 加密，裝置可能會變得不穩定。
- **要求儲存卡加密 (僅限行動裝置)** - 啟用此設定可加密裝置使用的任何抽取式儲存卡。


### <a name="bitlocker-base-settings"></a>BitLocker 基本設定

- **設定加密方法** - 啟用此設定可設定作業系統、資料和抽取式磁碟機的加密演算法。
    - **作業系統磁碟機的加密** - 選擇作業系統磁碟機的加密方法。 建議您使用 XTS-AES 演算法。
    - **固定式資料磁碟機的加密** - 選擇固定式 (內建) 資料磁碟機的加密方法。 建議您使用 XTS-AES 演算法。
    - **抽取式資料磁碟機的加密** - 選擇抽取式資料磁碟機的加密方法。 如果抽取式磁碟機與不是執行 Windows 10 的裝置搭配使用，建議您使用 AES-CBC 演算法。


### <a name="bitlocker-os-drive-settings"></a>BitLocker 作業系統磁碟機設定

- **啟動時需要其他驗證** - 
    - **禁止在沒有相容 TPM 晶片的裝置上使用 BitLocker** - 
    - **TPM 啟動** - 設定 TPM 晶片是已允許、不允許還是必要。 
    - **TPM 啟動 PIN** - 設定搭配 TPM 晶片使用啟動 PIN 是已允許、不允許還是必要。 
    - **TPM 啟動金鑰** - 設定搭配 TPM 晶片使用啟動金鑰是已允許、不允許還是必要。 
    - **TPM 啟動金鑰及 PIN** - 設定搭配 TPM 晶片使用啟動金鑰及 PIN 是已允許、不允許還是必要。
- **最小 PIN 長度** - 啟用此設定可設定 TPM 啟動 PIN 的最小長度。
    - **字元數下限** - 輸入啟動 PIN 所需的字元數 (**4**-**20**)。
- **啟用 OS 磁碟機修復** - 啟用此設定可控制在未提供必要的啟動資訊時，如何復原受 BitLocker 保護的作業系統磁碟機。
    - **允許以憑證為基礎的資料修復代理** - 如果您希望資料修復代理能夠與受 BitLocker 保護的作業系統磁碟機搭配使用，請啟用此設定。
    - **使用者的修復密碼建立** - 設定使用者是允許、需要還是不允許產生 48 位數的修復密碼。
    - **使用者的修復金鑰建立** - 設定使用者是允許、需要還是不允許產生 256 位元的修復金鑰。
    - **在 BitLocker 安裝精靈中隱藏修復選項** - 啟用此設定可防止使用者在開啟 BitLocker 時看到或變更修復選項。
    - **將 BitLocker 修復資訊儲存到 AD DS** - 啟用在 Active Directory 中儲存 BitLocker 修復資訊的功能。
    - **設定目標為 AD DS 的 BitLocker 修復資訊儲存** - 設定 BitLocker 修復資訊的哪些部分會儲存在 Active Directory 中。 從下列選項進行選擇：
        - **備份修復密碼和金鑰封裝**
        - **只備份修復密碼**
    - **要求先將修復資訊儲存在 AD DS 再啟用 BitLocker** - 啟用此設定可阻止使用者開啟 BitLocker，除非裝置已加入網域，且 BitLocker 修復資訊成功儲存在 Active Directory 中。
- **啟用開機前修復訊息及 URL** - 啟用此設定可設定開機前金鑰修復畫面顯示的訊息及 URL。
    - **開機前修復訊息** - 設定開機前修復訊息會向使用者顯示。 從下列選項進行選擇：
        - **使用預設修復訊息及 URL**
        - **使用空白修復訊息及 URL**
        - **使用自訂修復訊息**
        - **使用自訂修復 URL**


### <a name="bitlocker-fixed-data-drive-settings"></a>BitLocker 固定式資料磁碟機設定

- **拒絕對未受 BitLocker 保護的固定式資料磁碟機擁有寫入權限** - 啟用時，必須在所有固定式或內建的資料磁碟機中啟用 BitLocker 保護，才能進行寫入。
- **啟用固定式磁碟機修復** - 啟用此設定可控制在未提供必要的啟動資訊時，如何復原受 BitLocker 保護的固定式磁碟機。
    - **允許資料修復代理** - 如果您希望資料修復代理能夠與受 BitLocker 保護的固定式磁碟機搭配使用，請啟用此設定。
    - **使用者的修復密碼建立** - 設定使用者是允許、需要還是不允許產生 48 位數的修復密碼。  
    - **使用者的修復金鑰建立** - 設定使用者是允許、需要還是不允許產生 256 位元的修復金鑰。
    - **在 BitLocker 安裝精靈中隱藏修復選項** - 啟用此設定可防止使用者在開啟 BitLocker 時看到或變更修復選項。
    - **將 BitLocker 修復資訊儲存到 AD DS** - 啟用在 Active Directory 中儲存 BitLocker 修復資訊的功能。
    - **設定目標為 AD DS 的 BitLocker 修復資訊儲存** - 設定 BitLocker 修復資訊的哪些部分會儲存在 Active Directory 中。 從下列選項進行選擇：
        - **備份修復密碼和金鑰封裝**
        - **只備份修復密碼**
    - **要求先將修復資訊儲存在 AD DS 再啟用 BitLocker** - 啟用此設定可阻止使用者開啟 BitLocker，除非裝置已加入網域，且 BitLocker 修復資訊已成功儲存在 Active Directory 中。


### <a name="bitlocker-removable-data-drive-settings"></a>BitLocker 抽取式資料磁碟機設定

- **拒絕對未受 BitLocker 保護的抽取式資料磁碟機擁有寫入權限** - 指定是否需要抽取式存放磁碟機的 BitLocker 加密。
    - **禁止對其他組織中設定的裝置擁有寫入權限** - 指定屬於其他組織的抽取式資料磁碟機是否可以寫入。



## <a name="next-steps"></a>後續步驟

若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。


