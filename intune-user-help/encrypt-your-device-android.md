---
title: 加密 Android 裝置的 Intune |Microsoft Docs
description: 開啟 Android 裝置加密時由 Intune 所需的步驟
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: cfc17c60412a1cfe90693216caa69ada3d2d2c9a
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545249"
---
# <a name="encrypting-your-android-device"></a>加密 Android 裝置

裝置加密可保護檔案和資料夾免於未經授權存取您的裝置遺失或遭竊時。 開啟裝置加密之後，只擁有正確的密碼或 pin 碼的人都能夠登入您的裝置。 

您可以存取學校或公司資源之前，您的組織可能會要求您加密 Android 裝置。 根據預設，加密某些較新的 Android 裝置的立即可用。  

## <a name="turn-on-encryption"></a>開啟加密

如果公司入口網站或 Microsoft Intune 應用程式，將提示您加密您的裝置，請完成下列步驟。 

> [!Note]
> 華為、 Vivo 和 oppo 製造的裝置特定 Android 裝置無法加密。 如需詳細資訊，請參閱[這裡](your-device-appears-encrypted-but-cp-says-otherwise-android.md)。  

1. 設定裝置螢幕鎖定。  
    a. 移至 [設定]   > [Lock screen and security] \(鎖定螢幕和安全性)   > [Screen lock type] \(螢幕鎖定類型\)  。  
    b. 選取  **PIN**，**密碼**，或**模式**。  
    c. 請遵循畫面上的指示來設定您的螢幕鎖定。  

2. 請返回**鎖定螢幕和安全性**，然後選取**安全啟動**。
3. 選擇**需要 pin 碼時，裝置會開啟** > **確定**。
4. 輸入您的 PIN 以確認並加密您的裝置。
5. 開啟公司入口網站或 Microsoft Intune 的應用程式。
    * 公司入口網站使用者：選取您的裝置，然後點選 [檢查裝置設定]  。 
    * Microsoft Intune 使用者： 您必須等到頁面更新，但它會加密狀態應該變更為符合規範。  

執行 Android 4.4 及更早版本的裝置可能沒有**安全啟動**選項。 在此情況下，完成下列步驟來加密您的裝置。

1. 移至**設定** > **安全性** > **加密裝置**。 在螢幕上的標籤視 Android 裝置而有所不同。 如果您沒有看到**加密裝置**選項，請簽入：
    * **儲存體** > **儲存體加密**
    * **儲存體** > **鎖定螢幕和安全性** > **其他安全性設定** 

2. 遵循螢幕上的指示操作。 在加密期間，您的裝置可能會重新啟動數次。
3. 開啟公司入口網站或 Microsoft Intune 的應用程式。
    * 公司入口網站使用者：選取您的裝置，然後點選 [檢查裝置設定]  。  
    * Microsoft Intune 使用者： 您必須等到頁面更新，但它會加密狀態應該變更為符合規範。

## <a name="troubleshoot"></a>疑難排解  
**問題**： 您已加密您的裝置和

- 已停用 [加密] 按鈕。
- 您會看到仍需加密的訊息。
- 嘗試使用公司入口網站或 Microsoft Intune 應用程式時，您會收到錯誤。

**可以嘗試的動作**

- 請確定您的裝置已連接電源線且正在充電。  
- 請確定您已在裝置上設定 PIN 或密碼。  

是否仍需要協助？ 請連絡公司支援人員 (可查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)以取得連絡資訊)，或是撰寫電子郵件給 <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 小組</a>。  
