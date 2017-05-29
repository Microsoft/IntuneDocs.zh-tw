---
title: "使用 Intune 在電信費用管理中註冊您的 iOS 裝置"
description: "了解如何將 iOS 裝置註冊至電信費用管理。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d8c6372-f2ce-4558-8886-1d7c1966699c
searchScope:
- User help
ROBOTS: 
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-enduser
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: a71b8d1a100100e204eb7e90ba0ab00573ffc5c6
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-your-ios-device-in-telecom-expense-management"></a>在電信費用管理中註冊您的 iOS 裝置

您的組織可能會使用電信費用管理軟體，以確保其資料和語音方案是在可接受的限制內使用。 當您完成裝置註冊後，系統將會提示您選取最適合該裝置的類別。

  ![iOS 裝置上 [選取最適合裝置的類別] 畫面的螢幕擷取畫面。 它會顯示一系列公司或個人註冊選項。](./media/ios-enroll-10-tem-select-best-category.png)

選取適當的選項，然後您會收到從 App Store 安裝 [__Datalert__](https://itunes.apple.com/app/datalert/id771029268?mt=8) 應用程式的通知。 Datalert 應用程式是您的組織用來測量資料使用量的方式。 如果您的組織已設定 Microsoft 公司或學校註冊選項，您便必須使用公司或學校帳戶登入。 如果此選項尚未啟用，您必須提供相關資訊 (例如您的電話號碼) 並使用代碼驗證您的裝置，以從應用程式註冊 Datalert 服務。

  ![Datalert 應用程式歡迎使用畫面的螢幕擷取畫面，此畫面提供 Datalert 如何協助您善加利用行動數據方案的簡短說明，並在之後提示您移至下一個畫面。](./media/ios-enroll-11-tem-datalert-setup.png)

## <a name="enroll-into-datalert-using-your-microsoft-work-or-school-account"></a>使用您的 Microsoft 公司或學校帳戶註冊 Datalert

> [!NOTE]
> 若要使用此方法進行註冊，您的手機上必須安裝並啟動 [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) 應用程式。

1. 選取 [使用 Microsoft 帳戶註冊]。

  ![Datalert 應用程式設定畫面的螢幕擷取畫面，此畫面在上半部提供用以註冊裝置的電話號碼欄位，並在下半部提供 [使用 Microsoft 帳戶註冊]，以針對您有 Microsoft Office 365 帳戶和 Intune 訂閱的情況。](./media/ios-enroll-11a-tem-datalert-enroll-msft-account.png)

2. 您會接收到「Datalert」想要開啟「Authenticator」的通知。 選取 [開啟]。

  ![通知使用者因應 Datalert 應用程式的要求開啟 Authenticator 應用程式之快顯的影像。](./media/ios-enroll-11b-tem-datalert-open-authenticator.png)

3. 使用您的「Microsoft 學校或公司帳戶」登入。 Datalert 安裝將會運作一段時間，然後應該就會完成。 當它完成時，請點選 [完成]。

## <a name="enroll-into-datalert-using-your-phone-number"></a>使用您的電話號碼註冊 Datalert

1. 提供您裝置的電話號碼。

  ![Datalert 應用程式要求電話號碼的螢幕擷取畫面。](./media/ios-enroll-12-tem-datalert-phone-number.png)

2. 您接著會透過 SMS 訊息收到驗證碼。 提供驗證碼，然後點選 [確定]。

  ![Datalert 應用程式要求 SMS 驗證碼的螢幕擷取畫面。](./media/ios-enroll-13-tem-datalert-sms.png)

3. 提供驗證碼之後，就會完成 Datalert 安裝。 點選 [完成]，您就可以從 Datalert 應用程式監視您的資料。

  ![Datalert 應用程式監視今天資料使用量的螢幕擷取畫面。](./media/ios-enroll-14-tem-datalert-monitoring-active.png)

一旦註冊之後，您就可以開始在 Datalert 應用程式中查看您的資料使用量。

是否仍需要協助？ 請連絡 IT 系統管理員。 如需連絡資訊，請查看[公司入口網站](http://portal.manage.microsoft.com)。

