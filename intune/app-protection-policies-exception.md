---
title: 應用程式的資料傳輸原則例外狀況
titleSuffix: Microsoft Intune
description: 建立 Intune 行動應用程式管理 (MAM) 資料傳輸原則的例外狀況。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d33768206c53550ec1cb34d5c1ad5e2f33e4f8c8
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>如何建立 Intune 行動應用程式管理 (MAM) 資料傳輸原則的例外狀況

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

身為系統管理員，您可以建立 Intune 行動應用程式管理 (MAM) 資料傳輸原則的例外狀況。 例外狀況可讓您明確選擇哪些未受管理的應用程式可以與受管理應用程式互相傳輸資料。 IT 必須信任您包含在例外狀況清單中的未受管理應用程式。 

>[!WARNING] 
> 您必須負責變更資料傳輸例外狀況原則。 新增項目到此原則允許未受管理的應用程式 (不由 Intune 管理的應用程式) 存取由受管理應用程式保護的資料。 對受保護資料的這種存取可能會導致資料安全性外洩。 請您只為您的組織必須使用但不支援 Intune 應用程式 (應用程式保護原則) 的應用程式新增資料傳輸例外狀況。 此外，也請只為您不認為是資料洩漏風險的應用程式新增例外狀況。

此功能適用的情況是您建立 Intune 應用程式保護原則，並將資料傳輸設定為**僅限受管理應用程式**。 當資料傳輸原則設為**僅限受管理應用程式**時，除您建立的例外狀況，資料傳輸仍僅限於受 Intune 管理的應用程式。 您可以使用通訊協定 (iOS) 或套件 (Android) 來建立限制。

您可以設定這項功能，以讓 Intune MAM 應用程式保護原則的例外狀況能**限制資料傳輸**。 此原則只有在您想要允許資料傳輸至不支援 Intune APP 的應用程式時才需要。 此原則可讓 Intune 管理的應用程式 (且將資料傳輸設定設為**僅限受管理應用程式**，以根據 URL 通訊協定 (iOS) 或套件名稱 (Android) 叫用未受管理的應用程式。 Intune 會將重要的原生應用程式新增到例外狀況的預設清單。 

## <a name="ios-data-transfer-exceptions"></a>iOS 資料傳輸例外狀況
對於以 iOS 為目標的原則，您可以依 URL 通訊協定設定資料傳輸例外狀況。 若要新增例外狀況，請檢查應用程式開發人員提供的文件，尋找支援的 URL 通訊協定的相關資訊。 如需 iOS 資料傳輸例外狀況的其他資訊，請參閱 [iOS 應用程式保護原則設定 - 資料傳輸豁免](app-protection-policy-settings-ios.md#data-transfer-exemptions)。

## <a name="android-data-transfer-exceptions"></a>Android 資料傳輸例外狀況
對於以 Android 為目標的原則，您可以依應用程式套件名稱設定資料傳輸例外狀況。 您可以檢查 **Google Play** 商店頁面，尋找您想要新增例外狀況的應用程式，以尋找應用程式套件名稱。 如需 Android 資料傳輸例外狀況的其他資訊，請參閱 [Android 應用程式保護原則設定 - 資料傳輸豁免](app-protection-policy-settings-android.md#data-transfer-exemptions)。


>[!TIP]
> 您可以藉由瀏覽至 Google Play 商店上的應用程式，找到應用程式的套件識別碼。 套件識別碼被包含在應用程式頁面的 URL 中。 例如，Microsoft Word 應用程式的套件識別碼為 **com.microsoft.office.word**。

### <a name="example"></a>範例
藉由新增 **Webex** 套件作為 MAM 資料傳輸原則的例外狀況，會允許受管理 Outlook 電子郵件訊息內的 Webex 連結直接在 Webex 應用程式中開啟。 其他未受管理應用程式中的資料傳輸仍會受到限制。

- iOS **Webex** 範例：若要豁免 **Webex** 應用程式，以允許它由 Intune 管理的應用程式叫用，您必須新增下列字串的資料傳輸例外狀況：<code>wbx</code>
    
 - iOS **地圖**範例：若要豁免 **地圖**應用程式，以允許它由 Intune 管理的應用程式叫用，您必須新增下列字串的資料傳輸例外狀況：<code>maps</code>

- Android **Webex** 範例：若要豁免 **Webex** 應用程式，以允許它由 Intune 管理的應用程式叫用，您必須新增下列字串的資料傳輸例外狀況：<code>com.cisco.webex.meetings</code>
    
- Android **SMS** 範例： 若要豁免 **SMS** 應用程式，以允許它由 Intune 管理的應用程式跨越不同傳訊應用程式和 Android 裝置來叫用，您必須新增下列字串的資料傳輸例外狀況： 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

## <a name="next-steps"></a>接下來的步驟

- [建立及部署應用程式保護原則](app-protection-policies.md)
- [iOS 應用程式保護原則設定 - 資料傳輸豁免](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Android 應用程式保護原則設定 - 資料傳輸豁免](app-protection-policy-settings-android.md#data-transfer-exemptions)
