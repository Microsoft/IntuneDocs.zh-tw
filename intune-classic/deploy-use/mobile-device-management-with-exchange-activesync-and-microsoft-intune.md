---
title: Exchange ActiveSync 裝置管理
description: 透過使用 Exchange Connector 的 Exchange ActiveSync (EAS) 管理，來管理行動裝置
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f5e9bd3dd2026096c323858fc7faa915895ed55d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="exchange-activesync-mobile-device-management-with-microsoft-intune"></a>搭配 Microsoft Intune 的 Exchange ActiveSync 行動裝置管理

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

若要讓 Microsoft Intune 直接管理行動裝置，裝置必須[在 Intune 中註冊](prerequisites-for-enrollment.md)。 或者，系統管理員可以啟用受限程度更高的管理解決方案，透過 Exchange Connector 來使用 Exchange ActiveSync (EAS) 管理功能。 您可以透過內部部署 Exchange 伺服器或使用 Office 365 的 Exchange Online 管理裝置。 針對每個訂用帳戶，Intune 僅支援一個任意種類的 Exchange Connector 連線。

## <a name="exchange-access-rules-for-mobile-devices"></a>行動裝置的 Exchange 存取規則 ##

Exchange 需要定義行動裝置嘗試連線到 EAS 時會發生什麼動作的一組規則。 這些規則是在 Intune 管理主控台中管理。

[行動裝置的 Exchange 存取規則](exchange-access-rules-for-mobile-devices.md)

## <a name="install-the-exchange-connector"></a>安裝 Exchange Connector
Exchange Connector可讓您在 Intune 主控台中管理您的 Exchange 部署。 您必須先安裝並設定適當的 Intune 到 Exchange Connector。 根據您的 Exchange 伺服器是內部部署或在雲端中以服務形式託管，選擇適當的選項︰

-   [為 Exchange Online 或新的 Exchange Online 專用環境設定 Intune](intune-service-to-service-exchange-connector.md)
-   [為內部部署 Exchange 伺服器及舊版 Exchange Online 專用環境安裝 Intune 連接器](intune-on-premises-exchange-connector.md)


## <a name="apply-policy-for-exchange-managed-mobile-devices"></a>套用 Exchange 管理之行動裝置的原則
Intune 主控台可用以管理 [EAS 原則設定](exchange-activesync-policy-settings-in-microsoft-intune.md)，以及[限制公司資源的存取](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)。 如需特定行動服務支援的 Exchange ActiveSync 原則設定和功能清單，請參閱 [Exchange ActiveSync Client Comparison Table](http://go.microsoft.com/fwlink/?LinkId=247270) (Exchange ActiveSync 用戶端比較表)。

> [!NOTE]
> 將 Intune 連線到 Microsoft Exchange 環境之後，除非 Intune 內已定義更具體的原則，否則透過 Intune 管理的所有使用者的 EAS 原則都會重設為 Microsoft Exchange Server 上目前的預設原則。

## <a name="wipe-company-data-from-mobile-devices"></a>從行動裝置抹除公司資料
最後，如果資料不再使用中，或如果裝置遺失或失竊，您可以[抹除來自 EAS 管理的行動裝置的公司資料](wipe-for-exchange-managed-mobile-devices.md)。
