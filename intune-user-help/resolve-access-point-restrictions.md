---
title: 解決 Intune 中設定的存取點限制
description: 檢閱 Intune 存取點限制原則的 3 則常見訊息，並了解如何解決這些問題
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.openlocfilehash: a6f5fb0ae4ab5f4f5cafbba6122c0b42e4591c4b
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745112"
---
# <a name="resolve-access-point-restrictions"></a>解決存取點限制

組織可能會限制裝置存取公司資料的位置。
為了設定這些「存取點限制」，它們會指定並設定核准的網路位置。  

當您嘗試連線至無法辨識或未經核准的網路時，可能會收到下列一或多則訊息：

* 未設定存取點限制。
* 您未連線至核准的網路。
* 發生錯誤，無法強制執行存取點限制。

 下表列出每則訊息、其意義，以及再次存取工作資源的方式。

## <a name="access-point-restrictions-not-set-up"></a>未設定存取點限制  
| 公司入口網站訊息 | 此訊息的意義 | 您應該執行的動作                                                               
|------------------------|--------------------------|--------------------------|
| **未設定存取點限制 – 存取點限制處於使用中狀態，因此必須設定。** | 貴公司在您的裝置上套用了存取點限制。 此設定需要公司入口網站應用程式來驗證您裝置上的一些網路設定。 | 點選 [解析]。 公司入口網站應用程式會檢查以確定您連線至公司核准的網路。 |

## <a name="not-connected-to-an-approved-network"></a>未連線至核准的網路  

| 公司入口網站訊息 | 此訊息的意義 | 您應該執行的動作                                                                   
|------------------------|-----------------------------------|--------------------------|
| **裝置未連線至核准的網路 – 連線至核准的無線網路。** | 您已連線至未核准進行工作存取的網路。 只要您連線至此網路，就無法存取公司電子郵件、應用程式和其他受保護的公司資源。 | 連線至公司核准的網路。 然後點選 [解析] 重試。 |

## <a name="restrictions-couldnt-be-enforced"></a>無法強制執行限制  

| 公司入口網站訊息 | 此訊息的意義 | 您應該執行的動作                                                                      
|------------------------|-----------------------------------|--------------------------|
| **無法強制執行存取點限制 – 公司入口網站發生錯誤。** | Intune 無法判斷您是否連線至核准的網路。 這個錯誤可能是因為網路連線不佳、電量不足、省電模式或公司入口網站錯誤所造成。 | 確認您的網路接收狀況良好。 關閉省電模式，並確定電池續航力至少剩餘 30%。 然後點選 [解析] 重試。 

是否仍需要協助？ 建議您連絡公司支援人員。 如需特定連絡資訊，請移至[公司入口網站](https://portal.manage.microsoft.com/#HelpDeskDialog)。
