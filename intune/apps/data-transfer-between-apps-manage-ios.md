---
title: 管理 iOS 應用程式之間的資料傳輸
titleSuffix: Microsoft Intune
description: 了解如何在 Microsoft Intune 中使用行動裝置應用程式管理原則來管理應用程式之間的資料傳輸。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cdc849405b7404203faa6e86d3fed1ea8e35ec43
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414625"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>如何使用 Microsoft Intune 管理 iOS 應用程式之間的資料傳輸

為協助保護公司資料，請限制檔案只能傳輸至您管理的應用程式。 您可以使用下列方式管理 iOS 應用程式：

- 透過為應用程式設定應用程式保護原則，來保護公司或學校帳戶的組織資料。 我們稱之為*原則管理應用程式*。  請參閱[您可以使用應用程式保護原則管理的所有 Intune 受控應用程式](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

- 透過 iOS 裝置管理部署及管理應用程式，這要求您必須在行動裝置管理 (MDM) 解決方案中註冊裝置。 您部署的應用程式可以是「受原則管理」  的應用程式或其他受 iOS 管理的應用程式。

適用於已註冊之 iOS 裝置的**在管理中開啟**功能可以限制受 iOS 管理之應用程式之間的檔案傳輸。 在組態設定中設定 [在管理中開啟]  限制，然後使用您的 MDM 解決方案部署它們。  當使用者安裝部署的應用程式時，就會套用您設定的限制。

## <a name="use-app-protection-with-ios-apps"></a>對 iOS 應用程式施以應用程式保護
搭配 iOS [在管理中開啟]  功能使用應用程式保護原則，以透過下列方式保護公司資料︰

- **未由任何 MDM 解決方案管理的裝置：** 您可以設定應用程式保護原則設定以控制與其他應用程式共用資料 (透過 *Open-in* 或「共用延伸模組」  )。  若要這樣做，請將 [將組織資料傳送到其他應用程式]  設定設定為 [具 Open-In/Share 篩選且受原則管理的應用程式]  值。  受原則管理應用程式  中的「Open-in/共用」  行為只會將其他受原則管理的應用程式  呈現為共用選項。 

- **由 MDM 解決方案管理的裝置**：針對註冊至 Intune 或協力廠商 MDM 解決方案的裝置，在具有應用程式保護原則的應用程式與透過 MDM 部署之其他受控 iOS 應用程式之間的資料共用，是由 Intune 應用程式原則和 iOS **開啟位置管理**功能所控制。 若要確認您使用 MDM 解決方案部署的應用程式也會與您的 Intune 應用程式保護原則建立關聯，請依下一節[設定使用者 UPN 設定](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm)的說明，來設定使用者 UPN 設定。 若要指定您想允許資料傳輸至其他應用程式的方式，請啟用 [將組織資料傳送至其他應用程式]  ，然後選擇您偏好的共用層級。 若要指定您想允許應用程式接收其他應用程式傳送之資料的方式，請啟用 [接收其他應用程式的資料]  ，然後選擇您偏好的接收資料層級。 如需接收和共用應用程式資料的詳細資訊，請參閱[資料重新配置設定](app-protection-policy-settings-ios.md#data-protection)。

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>設定 Microsoft Intune 或協力廠商 EMM 的使用者 UPN 設定
Intune 或協力廠商 EMM 解決方案所管理的裝置**需要**設定使用者 UPN 設定，以識別已註冊的使用者帳戶。 UPN 設定會與您從 Intune 部署的應用程式保護原則搭配運作。 下列程序為 UPN 設定進行方式及所產生使用者體驗的一般流程︰

1. 在 [Azure 入口網站](https://portal.azure.com)中，針對 iOS [建立和指派應用程式保護原則](app-protection-policies.md)。 根據公司需求設定原則設定，然後選取應該具有此原則的 iOS 應用程式。

2. 使用下列通用步驟，來部署您要透過 Intune 或協力廠商 MDM 解決方案管理的應用程式及電子郵件設定檔。 *範例 1* 也涵蓋這個體驗。

3. 使用下列應用程式組態設定，將應用程式部署至受控裝置：

      **機碼** = IntuneMAMUPN, **值** = <username@company.com>

      範例：[‘IntuneMAMUPN’, ‘janellecraig@contoso.com’]
      
     > [!NOTE]
     > 在 Intune 中，應用程式組態原則註冊類型必須被設定為 [受控裝置]  。
     > 此外，應用程式也必須是從 Intune 公司入口網站 (若設為可用) 安裝，或視裝置的需求加以推送。 

4. 使用 Intune 或協力廠商 MDM 提供者，將**開啟位置管理**原則部署到已註冊的裝置。


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>範例 1：Intune 或協力廠商 MDM 主控台中的管理體驗

1. 移至 Intune 或協力廠商 MDM 提供者的管理主控台。 移至主控台區段，您可以在其中將應用程式組態設定部署到已註冊的 iOS 裝置。

2. 在 [應用程式設定] 區段中，輸入下列設定：

   **機碼** = IntuneMAMUPN, **值** = <username@company.com>

   根據您的協力廠商 MDM 提供者，金鑰/值配對的確切語法可能會不同。 下表顯示協力廠商 MDM 提供者的範例，以及應該輸入的索引鍵/值組確切值。

   |協力廠商 MDM 提供者| 設定機碼 | 數值類型 | 設定值|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | 字串 | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | 字串 | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | 字串 | ${userUPN} **或** ${userEmailAddress} |
   |Citrix 端點管理 | IntuneMAMUPN | 字串 | ${user.userprincipalname} |
   |ManageEngine Mobile Device Manager | IntuneMAMUPN | 字串 | %upn% |

> [!NOTE]  
> 針對 iOS 版 Outlook，如果您是搭配 [使用設定設計工具] 選項部署受控裝置應用程式組態原則，並啟用 [只允許公司或學校帳戶]  ，系統會針對該原則在幕後自動設定 IntuneMAMUPN 設定機碼。 如需詳細資料，請參閱[新的 iOS 與 Android 版 Outlook 應用程式組態原則體驗 – 一般應用程式設定](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481) \(英文\) 中的＜常見問題集＞小節。 


### <a name="example-2-end-user-experience"></a>範例 2：使用者體驗

使用 OS 共用從  受原則管理的應用程式*與其他應用程式共用*

1. 使用者在已註冊的 iOS 裝置上開啟 Microsoft OneDrive 應用程式，並使用其公司帳戶登入。  使用者輸入的帳戶必須與您應用程式組態設定中為 Microsoft OneDrive 應用程式指定的帳戶 UPN 相符。

2. 登入之後，您的系統管理員設定的應用程式設定會套用到 Microsoft OneDrive 中的使用者帳戶。  這包括將 [將組織資料傳送到其他應用程式]  設定設定為 [共用 OS 且受原則管理的應用程式]  值。

3. 使用者預覽公司檔案並嘗試透過 Open-in 與受 iOS 管理的應用程式共用。  

4. 資料傳輸成功，且資料現在由受 iOS 管理之應用程式中的 **Open-in 管理**保護。  Intune 應用程式不會套用到不是受原則管理之應用程式  的應用程式。

透過傳入組織資料從受 iOS 管理的應用程式與受原則管理的應用程式共用   

1. 使用者在註冊的 iOS 裝置上使用受控電子郵件設定檔開啟原生郵件應用程式。  

1. 使用者從原生郵件應用程式使用 Microsoft Word 開啟公司文件附件。

1. 當 Word 應用程式啟動時，會發生兩個體驗的其中一個：
   1. 在下列時機，資料會由 Intune APP 保護：
      - 使用者登入符合您在應用程式設定中為 Microsoft Word 應用程式指定之帳戶 UPN 的公司帳戶。 
      - 您的系統管理員已設定應用程式設定套用到 Microsoft Word 中的使用者帳戶。  這包括將 [接收其他應用程式的資料]  設定設定為 [所有包含傳入組織資料的應用程式]  值。
      - 資料傳輸成功，而且文件會標有應用程式中的公司身分識別。  Intune 應用程式保護文件的使用者動作。
   1. 在下列時機，資料**不會**由 Intune APP 保護：
      - 使用者**未**登入其公司帳戶。
      - 您的系統管理員已設定因為使用者未登入而**不會**套用到 Microsoft Word 的設定。
      - 資料傳輸成功，而且文件**不會**標有應用程式中的公司身分識別。  Intune 應用程式**不會**保護文件的使用者動作，因為它不是作用中。

    > [!NOTE]
    > 使用者可以透過 Word 新增及使用其個人帳戶。 當使用者在工作情況之外使用 Word 時，不會套用應用程式保護原則。 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>驗證協力廠商 EMM 的使用者 UPN 設定

在進行使用者 UPN 設定後，請驗證 iOS 應用程式是否能夠接收並遵守 Intune 應用程式保護原則。

例如，[需要應用程式 PIN]  原則設定可以輕鬆進行測試。 若原則設定等於 [必要]  ，使用者應會看到提示，要求其設定或輸入 PIN 才能存取公司資料。

首先，[建立和指派應用程式保護原則](app-protection-policies.md)到 iOS 應用程式。 如需如何測試應用程式保護原則的詳細資訊，請參閱[驗證應用程式保護原則](app-protection-policies-validate.md)。


## <a name="see-also"></a>請參閱
[什麼是 Intune 應用程式保護原則](app-protection-policy.md)
