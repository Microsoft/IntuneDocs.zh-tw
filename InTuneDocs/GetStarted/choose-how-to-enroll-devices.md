---
# required metadata

title: 選擇如何註冊行動裝置 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 06/06/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: damionw
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 選擇如何註冊行動裝置

行動裝置註冊是由 Microsoft Intune 來管理智慧型手機、平板電腦和電腦的程序。 身為系統管理員，您需要決定如何根據下列項目來註冊裝置︰

 -  擁有權 (個人與 公司擁有的)
 -  使用方式 (共用與 個人)
 -  平台 (iOS、Android、Windows Phone、Windows 電腦、Mac 電腦)

下列問題的回答可協助您判斷所管理裝置的最佳註冊方法。

## 員工攜帶自己的裝置，還是由您的組織提供裝置？

  **使用者擁有的裝置** - "BYOD” (攜帶您自己的裝置) 註冊 - 使用者可以在裝置上安裝 Intune 公司入口網站應用程式然後進行註冊，以存取公司資源 (例如電子郵件、公司入口網站、公司資料和支援)。  
  > [!div class="button"]   [BYOD 註冊 >](..deploy-use/get-ready-to-enroll-devices-in-microsoft-intune)

  **公司擁有的裝置** - 根據組織需求和所管理裝置的類型，Intune 可以透過各種方式來註冊公司擁有的裝置 (COD)。 下一個問題...

## 是否共用公司擁有的裝置，或是否有個別的使用者？

**共用公司擁有的裝置** - 這些裝置沒有單一使用者，而且通常不會設定成存取電子郵件。 範例包括使用者視需要從集區取出然後傳回的 Kiosk 裝置或工作導向裝置。 建議的註冊方法取決於裝置平台。

  - **Windows 和 Android 裝置** - *裝置註冊管理員*是 Intune 帳戶，可用來透過公司入口網站應用程式來註冊許多共用裝置。
  > [!div class="button"]   [裝置註冊管理員 >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **iOS 裝置** - 可以透過三種方式來管理共用 iOS 裝置。  **如何註冊您的共用 iOS 裝置？**

    - **Apple 的裝置註冊方案 (DEP)** - 使用註冊設定檔，可以將目標設為使用 DEP 所購買或管理的 iOS 裝置。 使用者第一次開啟裝置的電源時，裝置會下載 DEP 設定檔，並使用設定檔 DEP 進行註冊
    > [!div class="button"]     [DEP 註冊 >](../deploy-use/ios-device-enrollment-program-in-microsoft-intune)

    - **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac 電腦上執行的 Apple 應用程式。 您可以使用 USB 纜線將 iOS 裝置連接至 Mac，以在裝置上安裝註冊設定檔。 如果您可以將裝置重設為原廠預設值來進行註冊，請使用 [設定助理] 註冊。 如果您不想將裝置重設為原廠預設值，請使用 [直接註冊]。

    > [!div class="button"]     [設定助理註冊 >](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) 或[直接註冊 >](../deploy-use/ios-direct-enrollment-in-microsoft-intune)

    - **以上皆非** - 如果您無法或不想要使用 Apple DEP 或 Apple Configurator 註冊方法，請使用 Intune 的裝置註冊管理員。
    > [!div class="button"]     [DEM 註冊 >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。

**個別使用者** - 發行給個別使用者的公司擁有裝置需要追蹤為公司資產，同時允許使用者將電子郵件和資料存取為個人裝置。 建議的註冊方法取決於裝置平台。

  - **Windows 和 Android 裝置** - 匯入公司擁有之裝置的國際行動設備識別 (IMEI) 編號，以在 Intune 中將它們標記為公司擁有的裝置。 使用者接著可以安裝公司入口網站，以將他們的裝置註冊為個人裝置來存取公司資源 (例如電子郵件、應用程式和資料)。
  > [!div class="button"]   [利用 IMEI 標記 >](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  - **iOS 裝置** - 可以透過三種方式來管理共用 iOS 裝置。  **如何註冊您的共用 iOS 裝置？**

    - **Apple 的裝置註冊方案 (DEP)** - 使用註冊設定檔，可以將目標設為使用 DEP 所購買或管理的 iOS 裝置。 使用者第一次開啟裝置的電源時，裝置會下載 DEP 設定檔，並根據設定檔進行註冊。
    > [!div class="button"]     [DEP 註冊](../deploy-use/ios-device-enrollment-program-in-microsoft-intune)。

    - **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac 電腦上執行的 Apple 應用程式。 您可以使用 USB 纜線將 iOS 裝置連接至 Mac，以在裝置上安裝註冊設定檔。 如果您可以將裝置重設為原廠預設值來進行註冊，請使用 [設定助理] 註冊。

    如果您不想將裝置重設為原廠預設值，請使用 [直接註冊]。
    如果您可以將裝置重設為原廠預設值來進行註冊，請使用 [設定助理] 註冊。
    > [!div class="button"][iOS 設定助理註冊](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [!div class="button"][iOS 直接註冊](../deploy-use/ios-direct-enrollment-in-microsoft-intune)。

    - **以上皆非** - 如果您無法或不想要使用 Apple DEP 或 Apple Configurator 註冊方法，則請匯入公司擁有之裝置的國際行動設備識別 (IMEI) 編號，以在 Intune 中將它們標記為公司擁有的裝置。 使用者接著可以安裝公司入口網站，以將他們的裝置註冊為個人裝置來存取公司資源 (例如電子郵件、應用程式和資料)。 > [!div class="button"][利用 IMEI 編號標記裝置](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)


<!--HONumber=Jun16_HO1-->


