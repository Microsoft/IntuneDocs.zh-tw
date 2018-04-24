---
title: 抹除 Exchange 管理的行動裝置
description: Microsoft Intune 可讓您抹除或重設行動裝置，這些裝置搭配使用 Exchange ActiveSync (EAS) 和 Intune Exchange Connector 管理
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e116b620-1e12-4b5c-9905-2f7acf2ae530
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 753e5e9dac7199dff18d110808524f05aa669036
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="wipe-for-exchange-managed-mobile-devices"></a>抹除 Exchange 管理的行動裝置

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune 可讓您抹除或重設行動裝置，這些裝置搭配使用 Exchange ActiveSync (EAS) 和 Intune Exchange 連接器管理。 下表說明透過 Exchange ActiveSync 可用的抹除功能：


|      抹除類型       |              Windows 8.1 和 Windows RT 8.1              |                            iOS                             |                          Android                          |
|-------------------------|----------------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|        完整抹除        |          移除郵件帳戶及快取的郵件。           |                      重設成 XFactory。                       |                      恢復出廠預設值。                       |
|  選擇性抹除/電子郵件   |                  移除電子郵件帳戶。                  |                       不支援。                       |                      不支援。                       |
| 選擇性抹除/原則 | 移除原則強制執行，但不變更設定 | 移除原則強制執行，但不變更設定。 | 移除原則強制執行，但不變更設定。 |

