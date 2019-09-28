---
title: 在管理中註冊組織提供的 macOS 裝置 | Microsoft Docs
description: 描述如何在 Intune 中註冊組織所購買和提供的 macOS 裝置。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0de0e676e72d46bde922fd97b651cc1a9268e45e
ms.sourcegitcommit: 6a946a055a2014e00a4ca9d71986727a4ebbc777
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71239783"
---
# <a name="enroll-your-organization-provided-macos-device-in-management"></a>在管理中註冊組織提供的 macOS 裝置

了解如何讓您的新 macOS 裝置在 Intune 中受控。  

通常公司或學校提供的裝置會在您收到之前預先設定好。 在您開啟裝置並於第一次登入之後，您的組織會將這些預先設定的設定傳送到您的裝置。 在裝置完成設定之後，您便獲得公司或學校資源的存取權。

若要開始管理設定，請開啟裝置電源，並使用公司或學校認證登入。 本文的其餘部分描述您在逐步執行設定助理時將看到的步驟和畫面。

## <a name="what-is-apple-dep"></a>什麼是 Apple DEP？

您的組織可能已透過稱為「Apple 裝置註冊計劃」  (DEP) 的某項服務來購買其裝置。 Apple DEP 可讓組織購買大量 iOS 或 macOS 裝置。 接著，組織可以在其慣用的行動裝置管理提供者 (例如 Intune) 內設定和管理這些裝置。 如果您是系統管理員，而且想要取得 Apple DEP 的詳細資訊，請參閱[使用 Apple 的裝置註冊計劃來自動註冊 macOS 裝置](https://docs.microsoft.com/intune/device-enrollment-program-enroll-macos)。  

## <a name="get-your-device-managed"></a>讓您的裝置成為受控

請完成下列步驟以在管理中註冊您的 macOS 裝置。 如果您要使用自己的裝置，而不是組織提供的裝置，請遵循[個人和自備裝置](enroll-your-device-in-intune-macos-cp.md)的步驟。  

1. 開啟 macOS 裝置的電源。
2. 選擇您的國家/地區，然後按一下 [繼續]  。  

   ![macOS 裝置設定助理 [歡迎使用] 畫面的螢幕擷取畫面，其中顯示可供選取的語言清單。](./media/macos-dep-welcome-1808.png)
3. 選擇鍵盤配置。 此清單會根據您選取的國家/地區顯示一或多個選項。 不論選取的國家/地區為何，若要查看所有版面配置選項，請按一下 [全部顯示]  。 完成後，請按一下 [繼續]  。  

   ![macOS 裝置設定助理鍵盤配置畫面的螢幕擷取畫面，其中顯示可供選取的鍵盤語言清單、未核取的 [全部顯示] 選項，以及 [上一步] 和 [繼續] 按鈕。](./media/macos-dep-keyboard-1808.png)  
4. 選取您的 Wi-Fi 網路。 您必須具有網際網路連線才能繼續設定。 如果未看到您的網路，或者您需要透過有線網路連線，請按一下 [其他網路選項]  。 完成後，請按一下 [繼續]  。  

   ![macOS 裝置設定助理 [選取您的 Wi-Fi 網路] 畫面的螢幕擷取畫面，其中顯示可供選擇的可用網路清單。 也會顯示 [其他網路選項] 按鈕、[上一步] 按鈕和 [繼續] 按鈕。](./media/macos-dep-wifi-1808.png)  
5. 連線到 Wi-Fi 後，[遠端管理]  畫面隨即出現。 遠端管理可讓組織的系統管理員使用公司所需的帳戶、設定、應用程式及網路，從遠端設定您的裝置。 請完整閱讀遠端管理說明，以協助您了解裝置受控的方式。 然後按一下 **[繼續]** 。  

   ![macOS 裝置設定助理 [遠端管理] 畫面的螢幕擷取畫面，內含說明遠端管理的文字以及取得詳細資訊的文件連結。 也會顯示 [上一步] 按鈕和 [繼續] 按鈕。](./media/macos-dep-remote-management-1-1808.png)  
6. 出現提示時，請使用您的公司或學校帳戶登入。 經過驗證之後，您的裝置會安裝管理設定檔。 設定檔會設定組織的資源，並可讓您進行存取。  
7. 閱讀 Apple 資料與隱私權圖示的相關資訊，讓您稍後在收集個人資訊時能夠識別。 然後按一下 **[繼續]** 。  

   ![macOS 裝置設定助理 [資料與隱私權] 畫面的螢幕擷取畫面，其中顯示兩個人握手的圖例，並描述 Apple 對個人資訊的使用方式。 也會顯示 [上一步] 和 [繼續] 按鈕。](./media/macos-dep-apple-data-privacy-1808.png)  
8. 註冊裝置後，您可能還需要完成其他步驟。 您看到的步驟視組織自訂設定體驗的方式而定。 它可能需要您：
    * 登入 Apple 帳戶
    * 同意條款和條件
    * 刪除電腦帳戶
    * 逐步執行快速設定
    * 設定您的 Mac  

## <a name="get-the-company-portal-app"></a>取得公司入口網站應用程式

將 macOS 版 Intune 公司入口網站應用程式下載到您的裝置上。 此應用程式可讓您在管理中監視、同步處理、新增和移除裝置，以及安裝應用程式。 下列步驟也描述如何向公司入口網站註冊您的裝置。

1. 在您的 macOS 裝置上，前往 [https://portal.manage.microsoft.com/EnrollmentRedirect.aspx](https://portal.manage.microsoft.com/EnrollmentRedirect.aspx)。
2. 使用您的公司或學校帳戶登入公司入口網站。 
3. 按一下 [取得應用程式]  以下載 macOS 版公司入口網站安裝程式。
4. 出現提示時，請開啟 .pkg 檔案並完成安裝步驟。
5. 開啟公司入口網站應用程式並使用您的公司或學校帳戶登入。
6. 找到您的裝置並按一下 [註冊]  。
7. 按一下 [繼續]   > [完成]  。 您的裝置現在應該在公司入口網站應用程式中顯示為符合規範的公司裝置。

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。
