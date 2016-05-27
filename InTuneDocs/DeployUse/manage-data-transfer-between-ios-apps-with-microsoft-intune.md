---
# required metadata

title: 管理 iOS 應用程式之間的資料傳輸 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3a4515c1-b325-4ac1-9f0a-45ac27e00681

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 管理 iOS 應用程式之間的資料傳輸
## 管理 iOS 應用程式
保護公司資料包括確定檔案傳輸僅限於您所管理的應用程式。  您可以使用下列方式管理 iOS 應用程式：

-   藉由為應用程式設定 MAM 原則 (我們稱為原則管理的應用程式)，防止公司資料遺失。

-   您也可以透過 MDM 通道來部署和管理應用程式。  這需要在 MDM 方案中註冊裝置。 這些可以是 受原則管理的 應用程式或其他受管理的應用程式。

iOS 裝置適用的開啟位置管理功能可以限制透過 MDM 通道部署的應用程式之間的檔案傳輸。 「開啟位置管理」限制是在組態設定中設定，並使用 MDM 軟體部署。  當使用者安裝部署的應用程式時，就會套用您設定的限制。
##  使用 MAM 搭配 iOS 應用程式
行動應用程式管理 (MAM) 原則可搭配 iOS 開啟位置管理功能使用，以下列方式保護公司資料︰

-   未受任何 MDM 解決方案管理的員工自有裝置：您可以將 MAM 原則設定設定為 [只允許應用程式將資料傳送到受管理的應用程式]。 使用者在不受原則管理的應用程式中開啟受保護的檔案時，會無法讀取檔案。

-   Intune 管理的裝置︰針對在 Intune 中註冊的裝置，會自動允許具有 MAM 原則的應用程式之間的資料傳送與透過 Intune 部署的其他受管理 iOS 應用程式。 若要允許具有 MAM 原則的應用程式之間的資料傳送，請啟用 [只允許應用程式將資料傳送到受管理的應用程式] 設定。 您可以使用開啟位置功能來控制透過 Intune 部署的應用程式之間的資料傳輸。   

-   協力廠商 MDM 所管理的裝置的解決方案：您可以使用 iOS 的開啟位置管理功能，將資料傳輸在限制僅限受管理的應用程式。
若要確定您使用協力廠商 MDM 方案部署的應用程式也會在 Intune 中設定 MAM 原則相關聯，您必須設定的使用者 UPN 設定中所述 [使用者 UPN 設定](#configure-user-upn-setting) 逐步解說。  如果利用使用者 UPN 設定部署應用程式，則在使用者使用其工作帳戶登入時，會將 MAM 原則套用至應用程式。

> [!IMPORTANT]
> 只有部署到協力廠商 MDM 所管理裝置的應用程式，才需要使用者 UPN 設定。  Intune 受管理裝置則不需要此設定。

## 設定使用者 UPN 設定
協力廠商 MDM 解決方案所管理的裝置需要有此組態。 下面程序說明實作 UPN 設定之方式和所產生使用者體驗的一般流程︰


1.  設定 iOS 平台的行動應用程式管理原則。 根據公司需求設定原則設定，然後選取應該具有此原則的應用程式。

2.  使用步驟 3 和 4 中所述的設定，透過協力廠商 MDM 解決方案來部署應用程式和您要受管理的電子郵件設定檔。

3.  使用下列應用程式組態設定來部署這些應用程式︰索引鍵=IntuneMAMUPN、值=<username@company.com> [範例：‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

4.  將「開啟位置管理」原則部署到已註冊的裝置。

### 使用者經驗範例

1.  使用者會在裝置上安裝 Microsoft Word 應用程式。

2.  使用者會啟動受管理的原生電子郵件應用程式來存取其電子郵件。

3.  使用者嘗試從 Microsoft Word 的原生郵件中開啟文件。

4.  Word 應用程式啟動時，系統會提示使用者使用其工作帳戶登入。  出現提示時使用者輸入的此工作帳戶，應該符合您在應用程式組態設定中針對 Microsoft Word 應用程式指定的帳戶。

    > 在個人的環境中使用 Word 應用程式時，使用者可以加入其他個人帳戶至 Word，以執行其個人的工作而不會受到 MAM 原則影響。

5.  登入成功時，會將應用程式原則設定套用至 Word 應用程式。

6.  現在，資料傳輸成功，而且文件標記為應用程式中的公司身分識別。 此外，還會將資料視為在工作環境中，並據以套用原則設定。

### 請參閱
[使用行動應用程式管理原則搭配 Microsoft Intune 保護應用程式資料](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->


