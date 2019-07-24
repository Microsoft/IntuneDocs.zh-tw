---
title: 管理 iOS 應用程式之間的資料傳輸
titleSuffix: Microsoft Intune
description: 了解如何在 Microsoft Intune 中使用行動裝置應用程式管理原則來管理應用程式之間的資料傳輸。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9a1e370b65d8bfd7e61562347323bf1455dfe55b
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68354309"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>如何使用 Microsoft Intune 管理 iOS 應用程式之間的資料傳輸

為協助保護公司資料，請限制檔案只能傳輸至您管理的應用程式。 您可以使用下列方式管理 iOS 應用程式：

- 為應用程式設定應用程式保護原則來防止公司資料遺失，我們稱為**受原則管理**的應用程式。 請參閱[您可以使用應用程式保護原則管理的所有 Intune 受控應用程式](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

- 透過 **MDM 通道**部署及管理應用程式，這需要在行動裝置管理 (MDM) 解決方案中註冊裝置。 您部署的應用程式可以是**受原則管理**的應用程式或其他受管理的應用程式。

iOS 裝置適用的**開啟位置管理**功能可以限制透過 **MDM 通道**部署的應用程式之間的檔案傳輸。 在組態設定中設定 [在管理中開啟]  限制，然後使用您的 MDM 解決方案予以部署。  當使用者安裝部署的應用程式時，就會套用您設定的限制。

## <a name="use-app-protection-with-ios-apps"></a>對 iOS 應用程式施以應用程式保護
搭配 iOS [在管理中開啟]  功能使用應用程式保護原則，可以透過下列方式保護公司資料︰

- **員工擁有但未交由任何 MDM 解決方案管理的裝置：** 您可以將應用程式防護原則設定設為 [Allow app to transfer data to only Policy Managed apps] \(只允許應用程式將資料傳送至受原則管理的應用程式\)  。 受原則管理應用程式中的「開啟於」  行為只會將其他受原則管理的應用程式呈現為共用選項。 如果使用者嘗試在原生郵件應用程式中從 OneDrive 將受原則保護的檔案作為附件傳送，該檔案將無法讀取。

- **由 MDM 解決方案管理的裝置**：針對註冊至 Intune 或協力廠商 MDM 解決方案的裝置，在具有應用程式保護原則的應用程式與透過 MDM 部署之其他受控 iOS 應用程式之間的資料共用，是由 Intune 應用程式原則和 iOS **開啟位置管理**功能所控制。 若要確認您使用 MDM 解決方案部署的應用程式也會與您的 Intune 應用程式保護原則建立關聯，請依下一節[設定使用者 UPN 設定](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm)的說明，來設定使用者 UPN 設定。 若要指定您想允許資料傳輸至其他應用程式的方式，請啟用 [將組織資料傳送至其他應用程式]  ，然後選擇您偏好的共用層級。 若要指定您想允許應用程式接收其他應用程式傳送之資料的方式，請啟用 [接收其他應用程式的資料]  ，然後選擇您偏好的接收資料層級。 如需接收和共用應用程式資料的詳細資訊，請參閱[資料重新配置設定](app-protection-policy-settings-ios.md#data-protection)。

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>設定 Microsoft Intune 或協力廠商 EMM 的使用者 UPN 設定
Intune 或協力廠商 EMM 解決方案所管理的裝置**需要**設定使用者 UPN 設定。 UPN 設定會與您從 Intune 部署的應用程式保護原則搭配運作。 下列程序為 UPN 設定進行方式及所產生使用者體驗的一般流程︰

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
> 針對 iOS 中的 Outlook 應用程式，如果您是搭配 [使用設定設計工具] 選項來部署應用程式組態原則，系統會針對該原則在幕後自動設定 IntuneMAMUPN 設定機碼。 如需詳細資料，請參閱[新的適用於 iOS 和 Android 的 Outlook 應用程式組態原則體驗 – 一般應用程式設定](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481) \(英文\) 中的＜常見問題集＞小節。 


### <a name="example-2-end-user-experience"></a>範例 2：使用者體驗

1. 使用者在裝置上安裝 Microsoft Word 應用程式。

2. 使用者啟動受管理的原生電子郵件應用程式來存取其電子郵件。

3. 使用者嘗試從 Microsoft Word 的原生郵件開啟文件。

4. 當 Word 應用程式啟動時，系統會提示使用者使用其公司帳戶登入。 使用者輸入的帳戶必須與您應用程式組態設定中為 Microsoft Word 應用程式指定的帳戶相符。

    > [!NOTE]
    > 使用者可以透過 Word 新增及使用其個人帳戶。 當使用者在工作情況之外使用 Word 時，不會套用應用程式保護原則。 

5. 登入後，應用程式保護原則設定會套用至 Word 應用程式。

6. 現在，資料傳輸成功，而且文件會標有應用程式中的公司身分識別。  該資料視為工作內容，所以會套用原則設定。 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>驗證協力廠商 EMM 的使用者 UPN 設定

在進行使用者 UPN 設定後，請驗證 iOS 應用程式是否能夠接收並遵守 Intune 應用程式保護原則。

例如，[需要應用程式 PIN]  原則設定可以輕鬆進行測試。 若原則設定等於 [是]  ，使用者應會看到提示，要求其設定或輸入 PIN 才能存取公司資料。

首先，[建立和指派應用程式保護原則](app-protection-policies.md)到 iOS 應用程式。 如需如何測試應用程式保護原則的詳細資訊，請參閱[驗證應用程式保護原則](app-protection-policies-validate.md)。


## <a name="see-also"></a>請參閱
[什麼是 Intune 應用程式保護原則](app-protection-policy.md)
