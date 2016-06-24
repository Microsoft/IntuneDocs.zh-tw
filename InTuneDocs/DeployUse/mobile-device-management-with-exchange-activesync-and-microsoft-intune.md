---
# required metadata

title: 使用 Exchange ActiveSync 和 Microsoft Intune 的行動裝置管理 | Microsoft Intune
description:
keywords:
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Exchange ActiveSync 和 Microsoft Intune 的行動裝置管理
若要讓 Microsoft Intune 直接管理行動裝置，使用者必須對 Intune 註冊裝置。 如果使用者尚未註冊行動裝置，您可以使用 Exchange Connector 來啟用 Exchange ActiveSync (EAS) 管理。 可以使用內部部署 Exchange 伺服器和 Microsoft Office 365 上的雲端裝載 Exchange 來管理裝置。

## 行動裝置的 Exchange 存取規則 ##

Exchange 需要定義行動裝置嘗試連線到 EAS 時會發生什麼動作的一組規則。 這些規則是在 Intune 管理主控台中管理。

[行動裝置的 Exchange 存取規則](exchange-access-rules-for-mobile-devices.md)

## 安裝 Exchange Connector
Exchange Connector可讓您在 Intune 主控台中管理您的 Exchange 部署。 您必須先安裝並設定適當的 Intune 到 Exchange Connector。 根據您的 Exchange 伺服器是否為內部部署或在雲端中以服務形式裝載，選擇適當的選項︰

-   [針對內部部署 Exchange 安裝 Intune 連接器](intune-on-premises-exchange-connector.md)
-   [為託管之 Exchange Connector 設定適用的 Intune 服務](intune-service-to-service-exchange-connector.md)

## 套用 Exchange 管理之行動裝置的原則
原則設定可以透過 Intune 主控台來套用，請參閱[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。 如需特定行動服務支援之 Exchange ActiveSync 原則設定和功能的清單，請參閱 [Exchange ActiveSync 用戶端比較表](http://go.microsoft.com/fwlink/?LinkId=247270)

> 將 Intune 連線到 Microsoft Exchange 環境之後，除非 Intune 內已定義更具體的原則，否則透過 Intune 管理的所有使用者的 EAS 原則都會重設為 Microsoft Exchange Server 上目前的預設原則。

## 從行動裝置抹除公司資料
最後，如果資料不再使用中，或如果裝置遺失或失竊，您可以[抹除來自 EAS 管理的行動裝置的公司資料](wipe-for-exchange-managed-mobile-devices.md)。


<!--HONumber=May16_HO2-->


