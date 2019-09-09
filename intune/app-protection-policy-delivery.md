---
title: 了解應用程式保護原則傳遞和時間
titleSuffix: Microsoft Intune
description: 了解應用程式保護原則的不同部署時間範圍，以了解變更應該何時出現在您的終端使用者裝置上。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ec111319-7e02-434f-946b-88647726bf1a
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0dcc729eeb76dda1c2d6ddcedbedafdc7f999f0
ms.sourcegitcommit: 7484ef8006f6b81d8976c328dd704512a31872ec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70190223"
---
# <a name="understand-app-protection-policy-delivery-timing"></a>了解應用程式保護原則傳遞時間

了解應用程式保護原則的不同部署時間範圍，以了解變更應該何時出現在您的終端使用者裝置上。

## <a name="delivery-timing-summary"></a>傳遞時間摘要

應用程式保護原則傳遞取決於您使用者的授權狀態和 Intune 服務註冊。  

|    使用者狀態    |    應用程式保護行為     |    重試間隔 (請參閱備註)    |    為什麼會這樣呢？    |
|-----------------------------------------------------|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
|    租用戶未上線    |    等候下一個重試間隔。  使用者的應用程式保護不在使用中。    |    24 小時    |    當您尚未設定 Intune 租用戶時就會發生。    |
|    使用者未獲授權     |    等候下一個重試間隔。  使用者的應用程式保護不在使用中。     |    12 小時 - 不過，在 Android 裝置上，此間隔需要 Intune APP SDK 5.6.0 版或更新版本。 否則 Andriod 裝置的間隔是 24 小時。   |    當您未針對 Intune 授權使用者時就會發生。    |
|    使用者未獲指派應用程式保護原則    |    等候下一個重試間隔。  使用者的應用程式保護不在使用中。    |    12 小時        |    當您尚未指派應用程式設定給使用者時就會發生。    |
|    使用者成功註冊 Intune MAM    |    應用程式保護已針對每個原則設定套用。    更新會根據重試間隔發生    |    根據使用者負載所定義的 Intune 服務。    通常是 30 分鐘。     |    當使用者成功向 Intune 服務註冊 MAM 設定時就會發生。    |

> [!NOTE]
> 重試間隔可能需要使用中的應用程式使用才會發生，意思是應用程式已啟動並在使用中。  如果重試間隔為 24 小時，且使用者等候 48 小時才啟動應用程式，則應用程式保護用戶端將會在 48 小時內重試。

## <a name="handling-network-connectivity-issues"></a>處理網路連線問題

當使用者註冊因為網路連線問題而失敗時，會使用加快的重試間隔。  應用程式保護用戶端會以越來越長的間隔重試，直到間隔達到 60 分鐘，或成功建立連線為止。  然後，用戶端會繼續每隔 60 分鐘重試，直到成功建立連線為止。 然後，用戶端會回到根據使用者狀態的標準重試間隔。

## <a name="next-steps"></a>後續步驟

[將授權指派給使用者，讓使用者可在 Intune 中註冊裝置](licenses-assign.md)

