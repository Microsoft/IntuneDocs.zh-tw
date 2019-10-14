---
title: 在 Intune 中註冊 iOS 裝置
titleSuffix: Microsoft Intune
description: 在 Microsoft Intune 中設定 iOS 裝置註冊。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c4f3424c0d9712affbbf8ba3929e825b62ce5864
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940326"
---
# <a name="enroll-ios-devices-in-intune"></a>在 Intune 中註冊 iOS 裝置

Intune 啟用 iPad 和 iPhone 的行動裝置管理 (MDM)，讓使用者安全地存取公司的電子郵件、資料和應用程式。

身為 Intune 系統管理員，您可以設定 iOS 和 iPadOS 裝置的註冊作業，以存取公司資源。 您可以允許使用者註冊個人擁有的裝置，又稱為「攜帶您自己的裝置」(BYOD) 註冊。 您也可以設定公司擁有的裝置的註冊作業。

## <a name="prerequisites-for-ios-enrollment"></a>iOS 註冊的必要條件

啟用 iOS 裝置之前，請先完成下列步驟：

- [確定您的裝置符合 Apple 裝置註冊資格](https://support.apple.com/en-us/HT204142#eligibility)。
- [設定 Intune](../fundamentals/setup-steps.md) - 這些步驟會設定您的 Intune 基礎結構。 裝置註冊特別要求您[設定 MDM 授權單位](../fundamentals/mdm-authority-set.md)。
- [取得 Apple MDM Push certificate](apple-mdm-push-certificate-get.md) - Apple 需要憑證才能管理 iOS 和 macOS 裝置。

## <a name="user-owned-ios-and-ipados-devices-byod"></a>使用者擁有的 iOS 和 iPadOS 裝置 (BYOD)

您可以讓使用者註冊其個人的裝置讓 Intune 管理，這稱為「攜帶您自己的裝置」或 BYOD。 共有三種選項可註冊使用者：
- 應用程式保護原則提供您最輕鬆的 BYOD 體驗，僅提供應用程式層級的管理。 但如果您也想要使用 6 碼複雜 PIN 來保護裝置，您可以搭配使用者註冊使用這些原則。
- 您可以將裝置註冊視為一般的 BYOD 註冊。 它也為系統管理員提供各式各樣的管理選項。
- 使用者註冊是更簡化的註冊程序，可為系統管理員提供一組裝置管理選項的子集。 這項功能目前為預覽狀態。 

當您完成必要條件及指派使用者授權之後，使用者即可從 App Store 下載 Intune 公司入口網站應用程式，並遵循應用程式中的註冊指示進行。 您可以在 iOS 裝置上自訂公司入口網站隱私權聲明，如[隱私權聲明自訂](../apps/company-portal-app.md#privacy-statement-customization)中所述。

## <a name="company-owned-ios-devices"></a>公司擁有的 iOS 裝置

針對為使用者購買裝置的組織來說，Intune 可支援下列 iOS 公司擁有裝置的註冊方法：

- Apple 的裝置註冊計劃 (DEP)
- Apple School Manager
- Apple Configurator 設定助理註冊
- Apple Configurator 直接註冊

您也可以使用[裝置註冊管理員](device-enrollment-manager-enroll.md)帳戶，來註冊公司擁有的 iOS 裝置。

## <a name="device-enrollment-program"></a>裝置註冊方案

組織可以透過 Apple 的裝置註冊計劃 (DEP) 購買 iOS 裝置。 DEP 可以讓您在「線上」部署註冊設定檔，將裝置納入管理。 如需詳細資訊，請參閱[裝置註冊計劃](device-enrollment-program-enroll-ios.md)。

## <a name="user-enrollment"></a>使用者註冊
相較於其他註冊方法，使用者註冊會提供一組管理選項子集給管理員。 如需詳細資訊，請參閱[使用者註冊支援的動作、密碼和其他選項](ios-user-enrollment-supported-actions.md)，以及[設定 iOS 和 iPadOS 使用者註冊](ios-user-enrollment.md)。

## <a name="apple-school-manager"></a>Apple School Manager

Apple School Manager 是針對學校提供的裝置採購暨註冊方案。 就像 DEP，您可以部署設定檔以註冊管理的裝置。 深入了解 [Apple School Manager](apple-school-manager-set-up-ios.md)。

## <a name="apple-configurator"></a>Apple Configurator

您可以使用 Apple Configurator 在 Mac 電腦上註冊 iOS 裝置。 若要準備裝置，請以 USB 連接它們並安裝註冊設定檔。 使用 Apple Configurator 註冊裝置的方法共有兩種：

- 設定助理註冊 - 抹除裝置，並將裝置備妥可執行設定助理，以及為裝置的新使用者安裝公司原則。
- 直接註冊 - 不會抹除裝置，並使用預先定義的原則來註冊裝置。 這個方法適用於無使用者親和性的裝置。

深入了解 [Apple Configurator 註冊](apple-configurator-enroll-ios.md)。

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>在已註冊 DEP 或 Apple Configurator 的裝置上使用公司入口網站

已設定使用者親和性的裝置可以安裝並執行公司入口網站應用程式，以下載應用程式及管理裝置。 使用者收到裝置之後，他們必須完成一些額外步驟，以完成設定助理並安裝公司入口網站 App。

需要有使用者親和性，才能支援下項項目︰

- 行動應用程式管理 (MAM) 應用程式
- 對電子郵件和公司資料進行條件式存取
- 公司入口網站應用程式

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>使用者如何註冊具有使用者親和性之公司擁有的 iOS 裝置

1. 當使用者將其裝置開啟時，系統會提示他們完成設定助理。
2. 設定後，系統會提示使用者輸入 Apple ID。 使用者必須提供 Apple ID 以允許裝置安裝公司入口網站。
3. iOS 裝置會自動安裝 App Store 的公司入口網站應用程式。
4. 使用者應啟動公司入口網站應用程式，並使用與自己 Intune 訂用帳戶相關的認證 (例如唯一個人名稱或 UPN) 來登入。
5. 登入後，註冊就告一段落。 使用者即可使用裝置的完整功能。

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>關於無使用者親和性之公司擁有的受管理的裝置

設定為無使用者親和性的裝置並不支援公司入口網站，且不應該安裝該 App。 公司入口網站專為有公司認證且需要存取個人化公司資源 (如電子郵件) 的使用者設計。 註冊為無使用者親和性的裝置並非專供單一使用者登入使用。 Kiosk、銷售點 (POS)，或共用公用程式裝置，皆屬註冊為無使用者親和性的常見案例。

如果需要使用者親和性，請在註冊裝置之前確認裝置的註冊設定檔已選取 [使用者親和性]  。 若要變更裝置的親和性狀態，您必須將裝置淘汰並重新註冊該裝置。

## <a name="see-also"></a>請參閱

[針對 Microsoft Intune 中的 iOS 裝置註冊問題進行疑難排解](https://support.microsoft.com/help/4039809) \(英文\)
