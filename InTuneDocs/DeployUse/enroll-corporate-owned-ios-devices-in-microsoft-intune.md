---
title: "註冊屬公司擁有的 iOS 裝置 | Microsoft Intune"
description: "使用 Apple 裝置註冊方案 (DEP) 或 Apple Configurator 來註冊公司擁有的 iOS 裝置"
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8a124eb41789053451e0c709188430b1e043d435
ms.openlocfilehash: 872be93241c84a8334e4415f00b1383da7b15a61


---

# 在 Microsoft Intune 中註冊屬公司擁有的 iOS 裝置
Microsoft Intune 支援使用 Mac 電腦上所執行的 [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) 工具，來註冊公司所擁有的 iOS 裝置。

您可以利用下列三種方式來註冊公司所註冊的 iOS 裝置：

-   **Apple Configurator** - 可以透過匯出公司註冊設定檔，然後將 iOS 裝置連線到執行 Apple Configurator 的 Mac 來註冊那些裝置。 Apple Configurator 支援兩種註冊方式：

    - **設定助理註冊** - 將裝置重設為原廠值，並準備好裝置以供裝置的新使用者進行設定。 此方法需要系統管理員使用 USB，將 iOS 裝置連接到執行 Apple Configurator 以預先註冊的 Mac 電腦。 裝置接著會傳遞至其執行設定助理程序的使用者，使用其工作或學校認證來設定裝置並完成註冊程序。 [使用 Apple Configurator 和設定助理來註冊 iOS 裝置](ios-setup-assistant-enrollment-in-microsoft-intune.md)

    - **直接註冊** – 在裝置準備期間，建立 Apple Configurator 相容的檔案以供使用。 註冊的裝置未重設為原廠值，但不具有任何使用者關係。 此方法需要系統管理員使用 USB，將 iOS 裝置連接到執行 Apple Configurator 以註冊裝置的 Mac 電腦。 [使用 Apple Configurator 直接註冊來註冊 iOS 裝置](ios-direct-enrollment-in-microsoft-intune.md)

-   **裝置註冊方案 (DEP)** – 將註冊設定檔「無線」部署到透過 Apple 的裝置註冊方案所購買的裝置。 當使用者在裝置上執行設定助理時，會在 Intune 中註冊裝置。  透過 DEP 註冊的裝置不能由使用者取消註冊。 [註冊裝置註冊方案 iOS 裝置](ios-device-enrollment-program-in-microsoft-intune.md)

## 針對使用公司入口網站之公司擁有的 iOS 裝置的使用者親和性

已設定使用者親和性的裝置可以安裝並執行公司入口網站應用程式，以下載應用程式及管理裝置。 使用者收到裝置之後，他們必須完成一些額外步驟，以完成「設定助理」並安裝公司入口網站應用程式。

如何註冊包含使用者親和性之公司擁有的 iOS 裝置
1. 當使用者將其裝置開機時，系統會提示他們完成 [設定助理]。 設定期間，系統會提示使用者輸入其認證。 他們必須輸入與其 Intune 中訂用帳戶相關聯的認證 (也就是唯一的個人識別碼或 UPN)。

2. 設定期間，系統會提示使用者輸入 Apple ID。 必須提供 Apple ID 才能讓裝置安裝 [公司入口網站]。 也可以於設定完成之後，在 iOS 設定選單中提供 Apple ID。

3. 設定完成之後，該 iOS 裝置必須從 App Store 安裝公司入口網站應用程式，例如「公司入口網站應用程式」。

4. 使用者現在即可以設定裝置時使用的 UPN 來登入 [公司入口網站]。

5. 登入之後，系統會提示使用者註冊其裝置。 第一個步驟是識別裝置。 App 會在清單中顯示已經過公司註冊並指派給使用者 Intune 帳戶的 iOS 裝置。 選擇相符的裝置。

  如果此裝置尚未經過公司註冊，請選取 [新裝置] 來繼續標準註冊流程。

6. 在下一個畫面中，使用者必須確認新裝置的序號。 使用者可以點選 [確認序號] 連結啟動 [設定] app，以確認序號。 使用者必須在 [公司入口網站] 應用程式中輸入序號的最後 4 個字元。

  此步驟會確認裝置是公司在 Intune 中註冊的裝置。 如果裝置上的序號不符，則可能選取了錯誤的裝置。 返回上一個畫面，並選取不同的裝置。

7. 序號通過驗證後，[公司入口網站] 應用程式會重新導向至 [公司入口網站] 網站以完成註冊，然後提示使用者返回 app。

8. 現在已經完成註冊。 您現在即可使用裝置所含的完整功能。

### 關於無使用者親和性之公司擁有的受管理的裝置

設定為無使用者親和性的裝置並不支援公司入口網站，且不應該安裝該應用程式。 [公司入口網站] 是針對有公司認證且需要存取個人化公司資源 (如電子郵件) 的使用者而設計。 註冊為無使用者親和性的裝置並非專供單一使用者登入使用。 Kiosk、銷售點 (POS)，或共用的工具裝置，皆屬註冊為無使用者親和性的常見案例。 如果需要使用者親和性，請在註冊裝置之前確認裝置的註冊設定檔已選取 [使用者親和性]。 若要變更裝置的親和性狀態，您必須將裝置停用並重新註冊該裝置。



### 請參閱
[準備在 Microsoft Intune 中註冊裝置](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->


