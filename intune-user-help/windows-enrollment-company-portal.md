---
title: 在 Intune 公司入口網站中註冊 Windows 裝置 | Microsoft Docs
description: 開始在公司入口網站中註冊 Windows 裝置
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9f29e2d737dfd7bef709f239d6c8506c3bb746c
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196871"
---
# <a name="windows-device-enrollment-in-intune-company-portal"></a>在 Intune 公司入口網站中註冊 Windows 裝置  

在 Intune 公司入口網站中註冊您的 Windows 裝置，以安全地存取公司及學校應用程式、電子郵件和檔案。 若您的組織需要或建議特定應用程式 (例如 Office 或 OneDrive)，您會在註冊期間收到它們，或是可在註冊後從公司入口網站取得。  

您可以透過公司入口網站「或」  應用程式註冊 Windows 10 裝置。 若您要註冊具備先前版本 Windows 的裝置，您必須透過公司入口網站註冊裝置。  

## <a name="install-company-portal-app"></a>安裝公司入口網站應用程式  
您可能已經在裝置上安裝公司入口網站應用程式。 請在您的__所有應用程式__清單中檢查您是否擁有該應用程式。  如果應用程式清單中找不到 [公司入口網站]，請遵循下列步驟來安裝。  

1. 在您的裝置上開啟 **Microsoft Store**。

2. 在 [搜尋]  欄位中，鍵入**公司入口網站**。

3. 在結果清單中，選取 [公司入口網站]   > [安裝]  。

4. 選取 [安裝]  或 [免費]  。 這兩個選項沒有任何差異；文字會根據您組織設定應用程式的方式顯示。  

## <a name="find-windows-10-version-number"></a>尋找 Windows 10 版本號碼  
不同版本的 Windows 10 裝置，註冊步驟也不相同。 下列步驟會描述如何在 Windows 10 桌面版及行動裝置版裝置上尋找版本號碼。 在您了解您的版本後，您便可以繼續進行建議的註冊步驟。  

### <a name="windows-10-desktop-devices"></a>Windows 10 Desktop 裝置  

1. 移至 [開始]  。

2. 在搜尋列中，鍵入片語「關於您的電腦」。 從結果中選取「關於您的電腦」  。  


   ![搜尋電腦的相關設定](media/searching_for_about_your_pc.png)  

3. 向下捲動至 [Windows 規格]  來尋找在您電腦上安裝的 Windows 10 **版本**。  


   ![Windows 10 Desktop 關於您的電腦](media/settings_about_pc.png)  

4. 若您的版本是  

    *  __1607 或更新版本__：請使用 [[設定]   > [帳戶]   > [存取公司或學校帳戶]  路線](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device)來註冊您的裝置。   
    * __1511 或先前版本__：請使用 [[設定]   > [帳戶]   > [您的帳戶]  路線](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device)來註冊您的裝置。  

### <a name="windows-10-mobile-devices"></a>Windows 10 Mobile 裝置       

1.  前往__所有應用程式__，然後選取__設定__應用程式。  
2.  選取 [系統]   > [關於]  。      
3.  在__裝置資訊__下方，尋找「版本」  。  
4. 若您的版本是  

    *  __1607 或更新版本__：請使用 [[設定]   > [存取公司或學校帳戶]  ](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device) 路線來註冊您的裝置。   
    * __1511 或先前版本__：請使用 [[設定]   > [帳戶]  ](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device) 路線來註冊您的裝置。  

## <a name="enroll-non-windows-10-devices"></a>註冊非 Windows 10 裝置  
使用下列文章來透過公司入口網站註冊其他支援的 Windows 裝置：   
* [Windows 8.1 或 Windows RT 8.1 裝置](enroll-your-W81-or-rt81-windows.md)  
* [Windows Phone 8.1 裝置](enroll-your-wp81-windows.md)    

## <a name="it-administrator-support"></a>IT 系統管理員支援  
若您是 IT 系統管理員並在註冊裝置期間發生問題，請參閱[針對 Microsoft Intune 中的 Windows 裝置註冊問題進行疑難排解](https://support.microsoft.com/help/4469913)。 本文列出常見錯誤、其原因，以及解決這些問題的步驟。  

## <a name="next-steps"></a>後續步驟  
現在您已了解支援裝置以及您的 Windows 10 版本號碼，您現在可以繼續前往建議的註冊文章。  
 
如需裝置管理、公司入口網站，以及在學校及公司如何使用兩者的詳細資訊，請參閱下列文章：  
* [使用受控裝置來存取公司或學校資源](use-managed-devices-to-get-work-done.md)  
* [當您在 Intune 註冊您的裝置時，會發生什麼情況](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)  
* [當我註冊裝置時，我的組織可以看到哪些資訊？](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)  

需要協助嗎？ 請連絡您公司的支援人員。 [前往公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)來尋找您組織的 IT 連絡資訊。  
