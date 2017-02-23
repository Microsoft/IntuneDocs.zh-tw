---
title: "管理 iOS 應用程式之間的資料傳輸 |Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版：使用本主題了解如何使用 iOS 的「打開方式...」功能及行動應用程式管理原則來管理應用程式之間的資料傳輸。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 424fae862592c1ab5b4221fb5ad40a52c39f6760
ms.openlocfilehash: 8846417efd34db32d5a5c872ef438f5a0bc57e36


---

# <a name="how-to-manage-data-transfer-between-ios-apps"></a>如何管理 iOS 應用程式之間的資料傳輸 
## <a name="manage-ios-apps"></a>管理 iOS 應用程式
保護公司資料包括確定檔案傳輸僅限於您所管理的應用程式。  您可以使用下列方式管理 iOS 應用程式：

-   為應用程式設定應用程式保護原則 (我們稱之為**原則管理**的應用程式)，從而避免公司資料遺失。

-   您也可以透過 **MDM 通道**來部署和管理應用程式。  這需要在 MDM 方案中註冊裝置。 這些可以是 **受原則管理的** 應用程式或其他受管理的應用程式。

iOS 裝置適用的**開啟位置管理**功能可以限制透過 **MDM 通道**部署的應用程式之間的檔案傳輸。 「開啟位置管理」限制是在組態設定中設定，並使用 MDM 軟體部署。  當使用者安裝部署的應用程式時，就會套用您設定的限制。
##  <a name="using-app-protection-with-ios-apps"></a>對 iOS 應用程式施以應用程式保護
應用程式保護原則與 iOS 的**打開方式管理**功能一起使用，可以下列方式保護公司資料︰

-   **員工擁有但未交由任何 MDM 解決方案管理的裝置**：您可以將應用程式保護原則設定為 [Allow app to transfer data to only managed apps] (只允許應用程式將資料傳送至受管理的應用程式)。 使用者在不受原則管理的應用程式中開啟受保護的檔案時，會無法讀取檔案。

-   **Intune 管理的裝置**：對於已向 Intune 註冊的裝置，會自動允許設有應用程式保護原則之應用程式與透過 Intune 部署之其他受管理 iOS 應用程式間的資料傳輸。 若要允許設有應用程式保護原則之應用程式間的資料傳輸，請啟用 [Allow app to transfer data to only managed apps] (只允許應用程式將資料傳送至受管理的應用程式) 設定。 您可以使用**開啟位置**功能來控制透過 Intune 部署的應用程式之間的資料傳輸。   

-   **第三方 MDM 解決方案管理的裝置：**您可以使用 iOS 的**開啟位置管理**功能，將資料傳輸在限制僅限受管理的應用程式。
若要確定您使用第三方 MDM 解決方案部署的應用程式也關聯了您在 Intune 中設定的應用程式保護原則，您必須依照[設定使用者 UPN 設定](#configure-user-upn-setting)逐步解說所述，設定使用者 UPN 設定。  應用程式若是透過使用者 UPN 設定部署，便會在使用者使用其工作帳戶登入時，將應用程式保護原則套用到應用程式。

> [!IMPORTANT]
> 只有部署到協力廠商 MDM 所管理裝置的應用程式，才需要使用者 UPN 設定。  Intune 受管理裝置則不需要此設定。

## <a name="configure-user-upn-setting"></a>設定使用者 UPN 設定
協力廠商 MDM 解決方案所管理的裝置需要有此組態。 下面程序說明實作 UPN 設定之方式和所產生使用者體驗的一般流程︰


1.  在 Azure 入口網站中，[設定 iOS 平台的行動應用程式管理原則](app-protection-policies.md)。 根據公司需求設定原則設定，然後選取應該具有此原則的應用程式。

2.  使用步驟 3 和 4 中所述的設定，**透過協力廠商 MDM 解決方案**來部署應用程式和您要受管理的電子郵件設定檔。

3.  部署應用程式組態設定如下的應用程式︰key=IntuneMAMUPN, Value=<username@company.com> [example: ‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

4.  將「開啟位置管理」原則部署到已註冊的裝置。

### <a name="example-end-user-experience"></a>使用者經驗範例

1.  使用者會在裝置上安裝 Microsoft Word 應用程式。

2.  使用者會啟動受管理的原生電子郵件應用程式來存取其電子郵件。

3.  使用者嘗試從 Microsoft Word 的原生郵件中開啟文件。

4.  Word 應用程式啟動時，系統會提示使用者使用其工作帳戶登入。  出現提示時使用者輸入的此工作帳戶，應該符合您在應用程式組態設定中針對 Microsoft Word 應用程式指定的帳戶。

    > [!NOTE]
    > 使用者可以在 Word 中新增其他個人帳戶來執行個人工作，而且在個人內容中使用 Word 應用程式時，也不會受到應用程式保護原則的影響。

5.  登入成功時，會將應用程式原則設定套用至 Word 應用程式。

6.  現在，資料傳輸成功，而且文件標記為應用程式中的公司身分識別。 此外，還會將資料視為在工作環境中，並據以套用原則設定。

### <a name="see-also"></a>請參閱
[什麼是 Intune 應用程式保護原則](what-is-app-protection-policy.md)



<!--HONumber=Feb17_HO1-->


