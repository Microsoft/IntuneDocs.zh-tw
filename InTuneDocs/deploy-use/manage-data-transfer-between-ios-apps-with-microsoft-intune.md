---
title: "管理 iOS 應用程式之間的資料傳輸 | Microsoft Docs"
description: "使用本主題來了解如何使用 iOS「開啟位置」功能和行動應用程式管理原則來管理應用程式之間的資料傳輸。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a4515c1-b325-4ac1-9f0a-45ac27e00681
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: c66226b7fc31f91669c4f4f0693ccbd7c679189f
ms.openlocfilehash: e71ebacec9d7b890b41e7650c8c50f42952c6326
ms.contentlocale: zh-tw
ms.lasthandoff: 03/29/2017


---

# <a name="manage-data-transfer-between-ios-apps-with-microsoft-intune"></a>使用 Microsoft Intune 管理 iOS 應用程式之間的資料傳輸

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="manage-ios-apps"></a>管理 iOS 應用程式
保護公司資料包括確定檔案傳輸僅限於您所管理的應用程式。  您可以使用下列方式管理 iOS 應用程式：

-   為應用程式設定應用程式保護原則 (我們稱之為**原則管理**的應用程式)，從而避免公司資料遺失。

-   您也可以透過 **MDM 通道**來部署和管理應用程式。  這需要在 MDM 方案中註冊裝置。 這些可以是 **受原則管理的** 應用程式或其他受管理的應用程式。

iOS 裝置適用的**開啟位置管理**功能可以限制透過 **MDM 通道**部署的應用程式之間的檔案傳輸。 「開啟位置管理」限制是在組態設定中設定，並使用 MDM 解決方案部署。  當使用者安裝部署的應用程式時，就會套用您設定的限制。

##  <a name="manage-data-transfer-between-ios-apps"></a>管理 iOS 應用程式之間的資料傳輸
應用程式保護原則與 iOS 的「開啟位置管理」功能一起使用，可以下列方式保護公司資料︰

-   **員工擁有但未交由任何 MDM 解決方案管理的裝置：**您可以將[應用程式保護原則設定](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)設為 [Allow app to transfer data to only managed apps]\(只允許應用程式將資料傳送至受管理的應用程式)。 使用者在不受原則管理的應用程式中開啟受保護的檔案時，會無法讀取檔案。

-   **Intune 管理的裝置**：對於已向 Intune 註冊的裝置，會自動允許設有應用程式保護原則之應用程式與透過 Intune 部署之其他受管理 iOS 應用程式間的資料傳輸。 若要允許設有應用程式保護原則之應用程式間的資料傳輸，請啟用 [Allow app to transfer data to only managed apps]\(只允許應用程式將資料傳送至受管理的應用程式) 設定。 您可以使用**開啟位置**功能來控制透過 Intune 部署的應用程式之間的資料傳輸。   

-   **第三方 MDM 解決方案管理的裝置：**您可以使用 iOS 的**開啟位置管理**功能，將資料傳輸在限制僅限受管理的應用程式。
若要確定您使用第三方 MDM 解決方案部署的應用程式也關聯了您在 Intune 中設定的應用程式保護原則，您必須依照[設定使用者 UPN 設定](#configure-user-upn-setting-for-third-party-emm)逐步解說所述，設定使用者 UPN 設定。  應用程式若是透過使用者 UPN 設定部署，便會在使用者使用其工作帳戶登入時，將應用程式保護原則套用到應用程式。

> [!IMPORTANT]
> 只有部署到協力廠商 MDM 所管理裝置的應用程式，才需要使用者 UPN 設定。  Intune 受管理裝置則不需要此設定。

## <a name="configure-user-upn-setting-for-third-party-emm"></a>設定協力廠商 EMM 的使用者 UPN 設定
協力廠商 EMM 解決方案所管理的裝置**需要**設定使用者 UPN 設定。 下面程序描述設定 UPN 設定之方式和所產生使用者體驗的一般流程︰


1.  在 Azure 入口網站中，[設定 iOS 平台的應用程式保護原則](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)。 根據公司需求設定原則設定，然後選取應該具有此原則的應用程式。

2.  使用下面的一般化步驟，**透過協力廠商 MDM 解決方案**來部署應用程式和您要受管理的電子郵件設定檔。 範例 1 也涵蓋這個體驗。

  1.  使用下列應用程式組態設定來部署應用程式：

      **金鑰** = IntuneMAMUPN，**值** = <username@company.com>

      範例：[‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

  2.  使用協力廠商 MDM 提供者，將「開啟位置管理」原則部署到已註冊的裝置。


### <a name="example-1-admin-experience-in-third-party-mdm-console"></a>範例 1︰協力廠商 MDM 主控台中的管理體驗

1. 移至協力廠商 MDM 提供者的管理主控台。 移至主控台區段，您可以在其中將應用程式組態設定部署到已註冊的 iOS 裝置。

2. 在 [應用程式設定] 區段中，輸入下列設定：

  **金鑰** = IntuneMAMUPN，**值** = <username@company.com>

  根據您的協力廠商 MDM 提供者，金鑰/值配對的確切語法可能會不同。 下表顯示協力廠商 MDM 提供者範例，以及應該輸入的金鑰/值配對確切值。

|協力廠商 MDM 提供者| 設定機碼 | 數值類型 | 設定值|
| ------- | ---- | ---- | ---- |
| VMware AirWatch | IntuneMAMUPN | 字串 | {UserPrincipalName}|
| MobileIron Core | IntuneMAMUPN | 字串 | $EMAIL$  **或**  $USER_UPN$ |
| MobileIron Cloud | IntuneMAMUPN | 字串 | ${userUPN} **或** ${userEmailAddress} |

### <a name="example-2-end-user-experience"></a>範例 2：使用者體驗

1.  使用者會在裝置上安裝 Microsoft Word 應用程式。

2.  使用者會啟動受管理的原生電子郵件應用程式來存取其電子郵件。

3.  使用者嘗試從 Microsoft Word 的原生郵件中開啟文件。

4.  Word 應用程式啟動時，系統會提示使用者使用其工作帳戶登入。  出現提示時使用者輸入的此工作帳戶，應該符合您在應用程式組態設定中針對 Microsoft Word 應用程式指定的帳戶。

    > [!NOTE]
    > 使用者可以在 Word 中新增其他個人帳戶來執行個人工作，而且在個人內容中使用 Word 應用程式時，也不會受到應用程式保護原則的影響。

5.  登入成功時，會將應用程式保護原則設定套用至 Word 應用程式。

6.  現在，檔案傳輸成功，而且文件標記為應用程式中的公司身分識別。 此外，還會將檔案視為在工作環境中，並據以套用原則設定。

### <a name="validate-user-upn-setting-for-third-party-emm"></a>驗證協力廠商 EMM 的使用者 UPN 設定

設定使用者 UPN 設定之後，您應該驗證 iOS 應用程式能夠接收並符合 Intune 應用程式保護原則。

例如，[Require app PIN]\(需要應用程式 PIN) 原則設定可以輕鬆地以視覺化方式在裝置上進行測試。 如果原則設定設為 [是]，則使用者應該會在嘗試存取公司資料時看到設定或輸入 PIN 的提示。

首先，[建立及部署應用程式保護原則](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)到 iOS 應用程式。 如需如何測試應用程式保護原則的詳細資訊，請參閱[驗證應用程式保護原則](validate-mobile-application-management.md)。



### <a name="see-also"></a>請參閱
[使用 Microsoft Intune 的應用程式保護原則保護應用程式資料](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

