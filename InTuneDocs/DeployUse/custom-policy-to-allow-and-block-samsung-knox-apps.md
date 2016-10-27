---
title: "允許和封鎖 KNOX 的應用程式 | Microsoft Intune"
description: "自訂設定檔來建立一份允許和封鎖 KNOX 的應用程式清單。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc8e0df-7bf3-494e-8bc4-dac59a98ab41
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c7679d624ba22b2a062ef2534a642e38a5f57fde
ms.openlocfilehash: 273627573f58e1bde4fd19c548ce87639f25ca4b



---
# 使用自訂原則來允許及封鎖 Samsung KNOX 裝置的應用程式。

使用本主題中的程序，建立 Microsoft Intune 的自訂原則，該原則會建立下列其中一項項目︰

- 無法在裝置上執行的應用程式清單。 這份清單中的應用程式會被封鎖而無法執行，即使它們在套用原則時已安裝也一樣。
- 裝置使用者可從 Google Play 市集安裝的應用程式清單。 只可以安裝您列出的應用程式。 無法從市集安裝其他應用程式。

只有執行 Samsung KNOX 的裝置可使用這些設定。

## 建立允許或封鎖的應用程式清單

1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，選擇**原則**&gt;**設定原則**&gt;**新增**。
2. 在 [建立新原則] 對話方塊中，展開 **Android**，選擇 [自訂設定]，然後選擇 [建立原則]。
3. 提供原則的名稱和選擇性描述，然後在 [OMA-URI 設定] 區段中，選擇 [新增]。
4. 在 [新增或編輯 OMA-URI 設定] 對話方塊中，指定下列各項︰在裝置上遭封鎖而無法執行的應用程式清單︰
    
    - **設定名稱。** 輸入 **PreventStartPackages**。
    - **設定描述。** 輸入選擇性描述，例如 「被封鎖而無法執行的應用程式清單」。
    -   **資料類型。** 在下拉式清單中選擇 [字串]。
    -   **OMA-URI。** 輸入 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
    -   **值。** 輸入您想要允許的應用程式套件名稱清單。 您可以使用 **; : ,** 或 **|** 作為分隔符號。 (範例︰package1;package2;)

    針對使用者在排除所有其他應用程式時，可從 Google Play 商店安裝的應用程式清單：

    - **設定名稱。** 輸入 **AllowInstallPackages**。
    - **設定描述。** 輸入選擇性描述，例如「使用者可以從 Google Play 安裝的應用程式清單」。
    - **資料類型。** 在下拉式清單中選擇 [字串]。
    - **OMA-URI。** 輸入 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
    - **值。** 輸入您想要允許的應用程式套件名稱清單。 您可以使用 **; : ,** 或 **|** 作為分隔符號。 (範例︰package1;package2;)

4. 按一下 [確定]，然後按一下 [儲存原則]。 

>[!TIP]
> 您可以藉由瀏覽至 Google Play 商店上的應用程式，找到應用程式的套件識別碼。 套件識別碼被包含在應用程式頁面的 URL 中。 例如，Microsoft Word 應用程式的套件識別碼為 **com.microsoft.office.word**。

下一次，登入每個目標裝置後，就會套用應用程式設定。


## 部署原則

1.  在 [原則]  工作區中，選取您要部署的原則，然後按一下 [管理部署] 。

2.  在 [管理部署] 對話方塊中，選取您要部署原則的一或多個群組，然後按一下 [新增]  &gt; [確定]。

 
當您選取某項已部署的原則時，您可以在原則清單下方檢視有關部署的進一步資訊。

### 請參閱
[Microsoft Intune 中的 Android 和 Samsung KNOX 設定原則設定](android-policy-settings-in-microsoft-intune.md)



<!--HONumber=Oct16_HO2-->


