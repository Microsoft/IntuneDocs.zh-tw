---
title: 應用程式的資料傳輸原則例外狀況
titleSuffix: Microsoft Intune
description: 建立 Intune 行動應用程式管理 (MAM) 資料傳輸原則的例外狀況。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/01/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c9f6ee3d1672c375071b061b4a551f609792deb9
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238246"
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>如何建立 Intune 行動應用程式管理 (MAM) 資料傳輸原則的例外狀況

身為系統管理員，您可以建立 Intune 行動應用程式管理 (MAM) 資料傳輸原則的例外狀況。 例外狀況可讓您明確選擇哪些未受管理的應用程式可以與受管理應用程式互相傳輸資料。 您的 IT 人員必須信任您包含在例外狀況清單中的非受控應用程式。 

>[!WARNING] 
> 您必須負責變更資料傳輸例外狀況原則。 新增項目到此原則允許未受管理的應用程式 (不由 Intune 管理的應用程式) 存取由受管理應用程式保護的資料。 對受保護資料的這種存取可能會導致資料安全性外洩。 請您只為您的組織必須使用但不支援 Intune 應用程式 (應用程式保護原則) 的應用程式新增資料傳輸例外狀況。 此外，也請只為您不認為是資料洩漏風險的應用程式新增例外狀況。

在 Intune 應用程式防護原則中，將 [允許應用程式將資料傳送至其他應用程式] 設定為 [受原則管理的應用程式] 表示應用程式只能將資料傳送至由 Intune 管理的應用程式。 如果您需要允許將資料傳送到不支援 Intune 應用程式的特定應用程式，則可以使用 [選取排除的應用程式] 來為此原則建立例外狀況。 豁免允許由 Intune 管理的應用程式根據 URL 通訊協定 (iOS) 或套件名稱 (Android) 叫用非受控應用程式。 根據預設，Intune 會將重要的原生應用程式新增到此例外狀況的清單。 

> [!NOTE]
> 修改或新增至資料傳輸原則例外狀況，並不會影響其他應用程式保護原則，例如剪下、複製和貼上限制。 

## <a name="ios-data-transfer-exceptions"></a>iOS 資料傳輸例外狀況
對於以 iOS 為目標的原則，您可以依 URL 通訊協定設定資料傳輸例外狀況。 若要新增例外狀況，請檢查應用程式開發人員提供的文件，尋找支援的 URL 通訊協定的相關資訊。 如需 iOS 資料傳輸例外狀況的詳細資訊，請參閱 [iOS 應用程式防護原則設定 - 資料傳輸豁免](app-protection-policy-settings-ios.md#data-transfer-exemptions)。

> [!NOTE]
> Microsoft 並沒有以手動方式尋找用於為第三方應用程式建立應用程式例外狀況之 URL 通訊協定的方法。 

## <a name="android-data-transfer-exceptions"></a>Android 資料傳輸例外狀況
對於以 Android 為目標的原則，您可以依應用程式套件名稱設定資料傳輸例外狀況。 您可以檢查 **Google Play** 商店頁面，尋找您想要新增例外狀況的應用程式，以尋找應用程式套件名稱。 如需 Android 資料傳輸例外狀況的詳細資訊，請參閱 [Android 應用程式防護原則設定 - 資料傳輸豁免](app-protection-policy-settings-android.md#data-transfer-exemptions)。


>[!TIP]
> 您可以藉由瀏覽至 Google Play 商店上的應用程式，找到應用程式的套件識別碼。 套件識別碼被包含在應用程式頁面的 URL 中。 例如，Microsoft Word 應用程式的套件識別碼為 **com.microsoft.office.word**。

### <a name="example"></a>範例
藉由新增 **Webex** 套件作為 MAM 資料傳輸原則的例外狀況，會允許受管理 Outlook 電子郵件訊息內的 Webex 連結直接在 Webex 應用程式中開啟。 其他未受管理應用程式中的資料傳輸仍會受到限制。

- iOS **Webex** 範例： 若要豁免 **Webex** 應用程式，以允許它由 Intune 受控應用程式叫用，您必須新增下列字串的資料傳輸例外狀況：<code>wbx</code>
    
 - iOS **Maps** 範例：若要豁免原生 **Maps** 應用程式，以允許它由 Intune 受控應用程式叫用，您必須新增下列字串的資料傳輸例外狀況：<code>maps</code>

- Android **Webex** 範例： 若要豁免 **Webex** 應用程式，以允許它由 Intune 受控應用程式叫用，您必須新增下列字串的資料傳輸例外狀況：<code>com.cisco.webex.meetings</code>
    
- Android **SMS** 範例： 若要豁免原生 **SMS** 應用程式，以允許它由 Intune 受控應用程式跨越不同傳訊應用程式和 Android 裝置來叫用，您必須新增下列字串的資料傳輸例外狀況： 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

## <a name="next-steps"></a>後續步驟

- [建立及部署應用程式保護原則](app-protection-policies.md)
- [iOS 應用程式保護原則設定 - 資料傳輸豁免](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Android 應用程式保護原則設定 - 資料傳輸豁免](app-protection-policy-settings-android.md#data-transfer-exemptions)
