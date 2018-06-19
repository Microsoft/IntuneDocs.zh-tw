---
title: 選擇 iOS 裝置在 Intune 中的註冊方式
titlesuffix: Microsoft Intune
description: 在 Microsoft Intune 中設定 iOS 裝置註冊。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 01523dc4c887214794d4600219ce0b77549b4734
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31027113"
---
# <a name="enroll-ios-devices-in-intune"></a>在 Intune 中註冊 iOS 裝置

Intune 啟用 iPad 和 iPhone 的行動裝置管理 (MDM)，讓使用者存取公司的電子郵件和應用程式。

身為 Intune 管理員，您可以啟用 iOS 裝置註冊。 您可以允許使用者註冊個人擁有的裝置，又稱為「攜帶您自己的裝置」(BYOD) 註冊。 您也可以啟用公司擁有的裝置註冊。

## <a name="prerequisites-for-ios-enrollment"></a>iOS 註冊的必要條件
啟用 iOS 裝置之前，請先完成下列步驟：
- [設定 Intune](setup-steps.md) - 這些步驟會設定您的 Intune 基礎結構。 裝置註冊特別要求您[設定 MDM 授權單位](mdm-authority-set.md)。
- [取得 Apple MDM Push certificate](apple-mdm-push-certificate-get.md) - Apple 需要憑證才能管理 iOS 和 macOS 裝置。

## <a name="user-owned-ios-devices-byod"></a>使用者擁有的 iOS 裝置 (BYOD)

您可以讓使用者註冊其個人的裝置讓 Intune 管理，這稱為「攜帶您自己的裝置」或 BYOD。 當您完成必要條件及指派使用者授權之後，使用者即可從 App Store 下載 Intune 公司入口網站應用程式，並遵循應用程式中的註冊指示進行。

## <a name="company-owned-ios-devices"></a>公司擁有的 iOS 裝置
針對為使用者購買裝置的組織來說，Intune 可支援下列 iOS 公司擁有裝置的註冊方法：

- Apple 的裝置註冊計劃 (DEP)
- Apple School Manager
- Apple Configurator 設定助理註冊
- Apple Configurator 直接註冊

您也可以使用[裝置註冊管理員](device-enrollment-manager-enroll.md)帳戶，來註冊公司擁有的 iOS 裝置。

## <a name="device-enrollment-program"></a>裝置註冊方案
組織可以透過 Apple 的裝置註冊計劃 (DEP) 購買 iOS 裝置。 DEP 可以讓您在「線上」部署註冊設定檔，將裝置納入管理。 深入了解[裝置註冊計劃](device-enrollment-program-enroll-ios.md)。

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager 是針對學校提供的裝置採購暨註冊方案。 就像 DEP，您可以部署設定檔以註冊管理的裝置。 深入了解 [Apple School Manager](apple-school-manager-set-up-ios.md)。

## <a name="apple-configurator"></a>Apple Configurator
您可以使用 Apple Configurator 在 Mac 電腦上註冊 iOS 裝置。 若要準備裝置，請以 USB 連接它們並安裝註冊設定檔。 使用 Apple Configurator 註冊裝置的方法共有兩種：
- 設定助理註冊 - 將裝置重設為原廠設定，並將裝置備妥可執行設定助理，以及為裝置的新使用者安裝公司原則。
- 直接註冊 - 不會將裝置重設為原廠設定，並使用預先定義的原則來註冊裝置。 這個方法適用於無使用者親和性的裝置。

深入了解 [Apple Configurator 註冊](apple-configurator-setup-assistant-enroll-ios.md)。

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>在已註冊 DEP 或 Apple Configurator 的裝置上使用公司入口網站

已設定使用者親和性的裝置可以安裝並執行公司入口網站 App，以下載 App 及管理裝置。 使用者收到裝置之後，他們必須完成一些額外步驟，以完成設定助理並安裝公司入口網站 App。

需要有使用者親和性，才能支援下項項目︰
  - 行動應用程式管理 (MAM) 應用程式
  - 對電子郵件和公司資料進行條件式存取
  - 公司入口網站應用程式

**使用者如何註冊具有使用者親和性的屬公司擁有 iOS 裝置**
1. 當使用者將其裝置開啟時，系統會提示他們完成設定助理。 設定期間，系統會提示使用者輸入其認證。 他們必須輸入與其 Intune 中訂閱相關聯的認證 (也就是唯一的個人識別碼或 UPN)。

2. 設定期間，系統會提示使用者輸入 Apple ID。 使用者必須提供 Apple ID 以允許裝置安裝「公司入口網站」。 他們也可以在安裝完成後，從 iOS 設定功能表提供 ID。

3. 設定完成之後，該 iOS 裝置必須從 App Store 安裝公司入口網站 App。

4. 使用者現在可以使用於設定裝置時所用的 UPN 來登入公司入口網站。

5. 登入之後，系統會提示使用者註冊其裝置。 第一個步驟是識別裝置。 App 會在清單中顯示已經過公司註冊並指派給使用者 Intune 帳戶的 iOS 裝置。 使用者應該要選擇相符的裝置。

   如果此裝置尚未經過公司註冊，使用者應該選擇 [新裝置] 來繼續標準註冊流程。

6. 在下一個畫面中，使用者必須確認新裝置的序號。 使用者可以點選 [確認序號] 連結，隨即啟動使用「設定」App 來驗證序號的指示。 使用者必須在公司入口網站 App 中輸入序號的最後四個字元。

   此步驟會確認裝置是公司在 Intune 中註冊的裝置。 如果裝置上的序號不符，則可能選取了錯誤的裝置。 使用者應該返回上一個畫面，並選取不同的裝置。

7. 序號通過驗證後，公司入口網站 App 會重新導向至「公司入口網站」網站，以完成註冊。 該網站接著將會提示使用者返回 App。

8. 現在已經完成註冊。 使用者現在已可使用裝置的完整功能。

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>關於無使用者親和性之公司擁有的受管理的裝置

設定為無使用者親和性的裝置並不支援公司入口網站，且不應該安裝該 App。 [公司入口網站] 是針對有公司認證且需要存取個人化公司資源 (如電子郵件) 的使用者而設計。 註冊為無使用者親和性的裝置並非專供單一使用者登入使用。 Kiosk、銷售點 (POS)，或共用公用程式裝置，皆屬註冊為無使用者親和性的常見案例。

如果需要使用者親和性，請在註冊裝置之前確認裝置的註冊設定檔已選取 [使用者親和性]。 若要變更裝置的親和性狀態，您必須將裝置淘汰並重新註冊該裝置。

